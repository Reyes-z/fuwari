---
title: 为fuwari文章添加置顶功能
published: 2026-01-23
description: 为fuwari主题博客文章添加置顶功能的方法
image: ""
tags:
  - 博客
  - 博客优化
  - Fuwari
category: blog
draft: false
lang: ""
pinned: false
---
## 总览
为 `fuwari` 主题添加文章置顶功能主要需要改动三个文件，分别是:
1. **src\utils\content-utils.ts** (添加按置顶标签的文章排序方式)
2. **src\content\config.ts**（添加对 pinned 标签的 Frontmatter 的处理方式）
3. **src\components\PostCard.astro**（添加置顶文章的置顶图标显示）
## 进行修改
### 1. 修改src\utils\content-utils.ts
```js title="content-utils.ts" ins={7-9}
async function getRawSortedPosts() {
	const allBlogPosts = await getCollection("posts", ({ data }) => {
		return import.meta.env.PROD ? data.draft !== true : true;
	});

	const sorted = allBlogPosts.sort((a, b) => {
		// 首先按照置顶状态排序
		if (a.data.pinned && !b.data.pinned) return -1;
		if (!a.data.pinned && b.data.pinned) return 1;
		// 再按照发布时间排序
		const dateA = new Date(a.data.published);
		const dateB = new Date(b.data.published);
		return dateA > dateB ? -1 : 1;
	});
	return sorted;
}
```
### 2. 修改src\content\config.ts
```js title="config.ts" ins={12}
const postsCollection = defineCollection({
	schema: z.object({
		title: z.string(),
		published: z.date(),
		updated: z.date().optional(),
		draft: z.boolean().optional().default(false),
		description: z.string().optional().default(""),
		image: z.string().optional().default(""),
		tags: z.array(z.string()).optional().default([]),
		category: z.string().optional().nullable().default(""),
		lang: z.string().optional().default(""),
		pinned: z.boolean().optional().default(false),

		/* For internal use */
		prevTitle: z.string().default(""),
		prevSlug: z.string().default(""),
		nextTitle: z.string().default(""),
		nextSlug: z.string().default(""),
	}),
});
```
### 3. 修改src\components\PostCard.astro
该文件第一处修改:
```astro title="PostCard.astro" ins={14}
interface Props {
	class?: string;
	entry: CollectionEntry<"posts">;
	title: string;
	url: string;
	published: Date;
	updated?: Date;
	tags: string[];
	category: string | null;
	image: string;
	description: string;
	draft: boolean;
	style: string;
  pinned?: boolean;
}
```
该文件第二处修改:
```astro title="PostCard.astro" ins={7-9}
<a href={url}
    class="transition group w-full block font-bold mb-3 text-3xl text-90
hover:text-[var(--primary)] dark:hover:text-[var(--primary)]
active:text-[var(--title-active)] dark:active:text-[var(--title-active)]
before:w-1 before:h-5 before:rounded-md before:bg-[var(--primary)]
before:absolute before:top-[35px] before:left-[18px] before:hidden md:before:block">
    {entry.data.pinned &&
        <Icon class="inline-block text-[1.2rem] text-[var(--primary)] mr-1 align-middle translate-y-[-2px]" name="material-symbols:push-pin" />
    }
    {title}
    <Icon class="inline text-[2rem] text-[var(--primary)] md:hidden translate-y-0.5 absolute"name="material-symbols:chevron-right-rounded" ></Icon>
    <Icon class="text-[var(--primary)] text-[2rem] transition hidden md:inline absolute translate-y-0.5 opacity-0 group-hover:opacity-100 -translate-x-1 group-hover:translate-x-0" name="material-symbols:chevron-right-rounded"></Icon>
</a>
```
## 其他修改与使用
如需修改在执行 `pnpm new-post <filename>` 命令创建新文章时自动添加在 `Frontmatter` 中添加 `pinned` ，则需对 `scripts/new-post.js` 进行如下修改：
```js title="new-post.js" ins={10}
const content = `---
title: ${args[0]}
published: ${getDate()}
description: ''
image: ''
tags: []
category: ''
draft: false 
lang: ''
pinned: false 
---
`;
```

添加 `pinned` 标签后文章的 `Frontmatter` 结构如下:
```yaml
---
title: template
published: 2026-01-23
description: ''
image: ''
tags: []
category: ''
draft: true 
lang: ''
pinned: false 
---
```
将`pinned`设置为`true`和`false`来分别`启用`和`禁用`该文章置顶