---
title: Hexo
date: 2024-02-16 11:21:59
tags: [hexo, init]
---

## links
> Hexo: https://hexo.io/index.html

## Initialize a Hexo Blog
type the codes below one by one into your command console.
```
npm install hexo-cli -g
hexo init blog
cd blog
npm install
hexo server
```
### some issues
1. `npm install hexo-cli -g` gives me:
```
added 54 packages in 8s

14 packages are looking for funding
  run `npm fund` for details
```
2. `hexo init blog` gives me:
```
INFO  Cloning hexo-starter https://github.com/hexojs/hexo-starter.git
INFO  Install dependencies
error An unexpected error occurred: "https://registry.yarnpkg.com/hexo: connect ETIMEDOUT 104.16.0.35:443".
WARN  Failed to install dependencies. Please run 'npm install' in "E:\workspace\helloworlds\blog" folder.
```
3. `npm install` gives me:
```
npm WARN deprecated abab@2.0.6: Use your platform's native atob() and btoa() methods instead
npm WARN deprecated domexception@4.0.0: Use your platform's native DOMException instead
npm WARN deprecated cuid@2.1.8: Cuid and other k-sortable and non-cryptographic ids (Ulid, ObjectId, KSUID, all UUIDs) are all insecure. Use @paralleldrive/cuid2 instead.

added 240 packages, and audited 241 packages in 18s

28 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```

## Create a new Hexo Blog
under folder `blog`
```
hexo new "$$YOUR BLOG NAME$$"
```
you would then find your new blog under `source/_posts`, named `$$YOUR BLOG NAME$$.md`.
> NOTE: Whatever inside "$$ ... $$" is a variable.

## Edit a Hexo Blog
What you have to know before read more:
1. A Hexo blog is written by a **markdown** file.
2. A Hexo blog has several **tags**, defined in `tags: [$$TAG1$$, $$TAG2$$]`.
Edit
1. open the target markdown file under folder `source/_posts`.
2. edit `title`, `date`, `tags` if needed.
> NOTE: if you have only one tag, you can just `tag: $$TAG1$$`, or `tag: $$[TAG1]$$`, but if you have more than one tag, you must do `tags: [$$TAG1$$, $$TAG2$$, $$TAG3$$, ...]`
3. Edit the following line in markdown format.

