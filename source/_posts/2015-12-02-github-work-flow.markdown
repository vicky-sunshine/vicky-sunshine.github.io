---
layout: post
title: "GitHub Work Flow"
date: 2015-12-02 02:45:06 +0800
comments: true
categories: tech
---

以 kiwi course 為例

## First time collaborate

1. fork kiwi to your own repo from
2. clone kiwi to local
3. let your local repo link to upstream (i.e. organization repo, kiwi)

```
git remote add upstream git@github.com:Kiwi-Learn/kiwi-scraper.git
```

## Developing new feature

every time, you want to add new feature at local, open and checkout the branch to develop,

```
git checkout -b new-feature
```

then you can start programming under the new-feature branch

## Finish Developing

when feature is done, commit first

```
git commit -m "blah blah..."
```
create/push to your own remote branch
```
git push origin new-feature
```
and then you can give kiwi a pull request after kiwi

## Sync your own repo

If the project owner agrees to merge new feature, you can,

1.sync your own repo master

```
git checkout master
git fetch upstream
git merge upstream/master
git push origin master
```
2.remove local and remote branches you just used (notice you can’t at the branch you want to delete)

- delete local branch
```
git branch -d new-feature
```
- delete remote branch
```
git push origin --delete new-feature
```
