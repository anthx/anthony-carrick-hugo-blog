---
title: "New Blogging Platform using Hugo"
tags: ["Technology"]
description: I've moved this blog to Hugo and Netlify
date: 2022-12-01
lastmod: 2022-12-01
---

I’ve migrated this blog on Hugo and Netlify because my chosen Gatsby theme wasn't updated for the latest version of Gatsby and with other NPM updates all became unmaintainable. 

It's taken about 2 - 3 evenings to rebuild it in Hugo, because Hugo already uses Markdown for it's content. So I just needed to rearrange the front matter (article metadata) and create the new site. Still Netlify makes it quite easy.

Following [Hugo](https://gohugo.io/documentation/) and [Jimmy Cai's](https://stack.jimmycai.com/) directions were good. The directory structure of the content was different, but well documented so I just copy it in and rename the folders. Use VS Code to find and replace the Front Matter codes where they differ.

YouTube embeds weren't working because of Hugo's Markdown renderer turns HTML off. So I could either just turn it on again in a config, or add a Hugo Shortcode following [Igor Baiborodine's YouTube Hugo directions](https://www.kiroule.com/article/use-video-embeds-in-hugo-theme/#enhanced-youtube-shortcode). 

I could bring in Netflify CMS again too and it even works locally this time. I couldn't get it work locally on Gatsby for some reason.

It also builds on Netlify _a lot_ faster since it's Go and not Node so being able to publish it and see it should be more pleasant. 

And with only dependencies on Hugo and the theme, I can maintain it longer and easier even if they go away. Plus just due to the way they work, it feels easier to customise.