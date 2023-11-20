---
layout: default
title: git
parent: Cheatsheet
nav_order: 2
---

# git

## [How to squash all git commits into one](https://stackoverflow.com/questions/1657017/how-to-squash-all-git-commits-into-one)

```bash
git checkout --orphan new-main main
git commit -m "Initial commit"
git branch -M new-main main
```

## [Pretty git branch graphs](https://stackoverflow.com/questions/1057564/pretty-git-branch-graphs)

```bash
git log --all --decorate --oneline --graph
```

## [Git clone verbose output](https://stackoverflow.com/questions/26056130/git-clone-verbose-output)

```bash
git clone --verbose git@gist.github.com:89303b570cc1b3ba3e17062e28ed1ee3.git cheat-sheets
```

## [How to use git to get just the latest revision of a project](https://stackoverflow.com/questions/1209999/how-to-use-git-to-get-just-the-latest-revision-of-a-project)

```bash
git clone --depth 1 git@gist.github.com:89303b570cc1b3ba3e17062e28ed1ee3.git cheat-sheets
```

## [Skip Git commit hooks](https://stackoverflow.com/questions/7230820/skip-git-commit-hooks)

```bash
git commit --no-verify -m "commit message"
```

## [How do I delete a Git branch locally and remotely?](https://stackoverflow.com/questions/2003505/how-do-i-delete-a-git-branch-locally-and-remotely)

```bash
git push -d <remote_name> <branchname>
git branch -d <branchname>
```

## [Push git commits & tags simultaneously](https://stackoverflow.com/questions/3745135/push-git-commits-tags-simultaneously)

```bash
git push --follow-tags
```

## [How do you change the capitalization of filenames in Git?](https://stackoverflow.com/questions/10523849/how-do-you-change-the-capitalization-of-filenames-in-git)

```bash
git mv --force myfile MyFile
```

## [git reset --hard HEAD leaves untracked files behind](https://stackoverflow.com/questions/4327708/git-reset-hard-head-leaves-untracked-files-behind)

```bash
git reset --hard && git clean -df
```