---
url: /quick-look-at-github-dev
date: 2022-01-16T03:47:12.833Z
lastmod: 2022-01-16T03:47:12.859Z
tags:
  - news
title: A Quick Look at GitHub.dev
description: It turns out GitHub.dev works perfectly well for updating code on the iPad.
image: ../assets/images/package.json-—-anthony-carrick-blog-github-—-visual-studio-code-—-github.png
---
A few months ago Microsoft released [GitHub.dev](https://visualstudiomagazine.com/articles/2021/08/31/github-vs-code.aspx) - a browse-based VisualStudio Code tied to a GitHub repository. You can press “.” on the keyboard while signed into GitHub while viewing a repository (or change the URL from .com to .dev) and get a full VS Code in the web browser.

I finally tried to use it for real on my iPad while on holidays to add Google Analytics to this website. It actually works! 

# Advantages: 

* Command Palette Ctrl + P and Shift+Ctrl + P both work.
* amazing auto closing bracket feature is available
* Seems to work without issues in Safari on iPad OS

# Limitations: 

* There’s no terminal so you can’t run commands.
* Git works, but it’s “pushed” immediately which since it’s linked to GitHub directly, isn’t really a problem.
* The menu is on collaposed on the side, so it takes getting used to.

# Experience

Without the terminal I had to cheat a bit and edit package.json “by hand” to install the analytics plugin to Gatsby and I couldn’t build the site locally so I couldn’t test it without waiting for the build by Netlify. 

Interestingly the build process said the plugin wasn’t compatible with my version of Gatsby, but it actually seems to work anyway - Google Analytics is getting hits.

And without being able to run npm commands I had to look up the version of the plugin to install, whereas `npm run install` would find the latest automatically.

# In conclusion

VS Code team and GitHub probably truly intended it for quick edits or visualising a repository, rather than trying to edit a whole project like I did, but it does work. Besides, if you paid for [Codespaces](https://github.com/features/codespaces), you’d have a whole terminal and virtual machine to run commands on anyway. (Actually it’s not released yet for individuals.)

Having said all that, I’ll keep using for certain changes like simple updates to content while away from the desktop environment. (It’s also much easier with a Bluetooth or Smart Keyboard for the iPad of course.)