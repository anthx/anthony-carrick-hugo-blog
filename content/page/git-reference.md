---
title: Git Stuff
url: "/git-reference"
description: Stuff it's easy to forget about Git
menu:
    main: 
        weight: -90
        params:
            icon: brand-git
toc: false
---

## Git Quick Reference
## I've put work on the wrong branch!

I accidentally did work on Branch A, but it should be on Branch B:

```
git checkout <branch-B>  
git cherry-pick <commit ID>  
git cherry-pick <commit ID>  
```

Git will grab the commit from the original branch and replay it onto the new branch, so you'll have new commit IDs.

## I've accidentally committed something, but don't want to delete the working copy

```
git rm --cached mylogfile.log
```

and for a single directory:

```
git rm --cached -r mydirectory
```

## Update branch from master to get new changes

```
git merge origin/master
```

Seems to automatically fetch because of the reference to origin.

To avoid the extra commit (if you don't mind lying about the history):

```
git fetch  
git rebase origin/master
```

## Clean up branches on my PC but not on Origin

```
git checkout master  
git pull  
git fetch --prune -n --dry-run  
```

Then in PowerShell:

```
git branch --list --format "%(if:equals=[gone])%(upstream:track)%(then)%(refname:short)%(end)" | ? { $_ -ne "" } | % { git branch -D $_ }
```

See [Xenoinc's Guide](https://github.com/xenoinc/CodeDevOps/blob/c33f2f8107601a4a16fde03d493ba61b5d895f1c/docs/GitCleanup.md)