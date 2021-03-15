---
title: "Sample Image"
date: 2021-03-14T14:49:42Z
showDate: true
draft: false
tags: ["testing"]
---

Here is a photograph of an old Porsche. It held in version control, just like the rest of the site, but using native [Git LFS][GitLFS] support. It is hosted directly on GitHub.

![1999 Porsche 996 Carrera](/posts/996_side.jpg)

## Netlify Large Media

> Netlify Large Media uses Git LFS to take advantage of the benefits of Git version tracking without bloating your repository. Your designated Large Media files are uploaded directly to our media servers while Git tracks their versions with text pointer files in the repository.

The main benefits of [the Netlify solution][NetlifyLM] appear to be:

- the avoidance of GitHub's native LFS size and bandwidth limitations; and
- a reduction of the amount of content cloned by Netlify upon build.

It was discounted in this instance, mainly because it would preclude the use of [Hugo's image processing abilities][HugoImg]. This would mean modifying templates (which rely on local image storage at build time) rather than setting up alternative online hosting.

There is also an [argument to be made][HugoDisc] for a static site to remain _truly static;_ using an external media hosting solution increases the complexity of the site and moves it away from the core static concept. It also means moving content _out_ of source control.

[GitLFS]: https://git-lfs.github.com/
[NetlifyLM]: https://docs.netlify.com/large-media/overview/
[HugoImg]: https://gohugo.io/content-management/image-processing/
[HugoDisc]: https://discourse.gohugo.io/t/hugo-101-migrating-images-from-services-like-cloudinary/20218/2
