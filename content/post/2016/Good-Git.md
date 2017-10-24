---
title: Good Git!
date: 2016-11-22 20:26:16
tags: [git]
categories: [guide]
author: Sahil Ahuja
featured: "caveman4.jpg"
featuredalt: "Git Caveman"
featuredpath: "date"
---
## Most used (but yet unremembered) git commands

<!-- {{< figure src="/images/2016/caveman4.jpg" title="Caveman Fire" width="300px">}} -->

<!--more-->

### Push your currently detached HEAD
`git push origin HEAD:master` 


### Delete remote branches only
`git push origin --delete branch_to_delete`

### Changes in git index vs. local filesystem
{{< highlight bash >}}
git commit -m "Something terribly misguided"
git reset --soft HEAD~
<< edit files as necessary >> 
git add ... 
git commit -c ORIG_HEAD
{{< /highlight >}}
* `git reset --soft HEAD~1` doesn't remove the changes from index (i.e. `git commit` adds them again, no need to git add.).
* `git reset HEAD~1` undoes the commit, removes changes from index but keeps the changes locally (working tree)
* `git reset --hard HEAD~1` removes the changes from the filesystem (working tree) too.

#### Remove git tracked files without removing them from filesystem
`git rm --cached --force ".idea"`

## Specific Usecases

### Patch related
```bash
#To see diff for a particular commit https://stackoverflow.com/a/17563740/1233476
git diff COMMIT^ COMMIT

#To remove untracked files from working tree
git clean -n; #To check
git clean -f -d; #To delete
```

### Submodules
```bash
#to checkout already existing submodules in an existing project
git submodule update --init --recursive

#To clone a project along with its submodules
git clone --recursive <project url>

#add a submodule in a repo
`git submodule add https://github.com/<user>/rock rock` 

#remove a submodule
git submodule deinit rock

#list existing submodules
git submodule status
```

### Tags
```bash
npm version patch/minor/major #Changes packages.json and applies git tag
git push origin v1.5 (or) git push origin --tags
git tag v1.5 (lightweight tag)
git tag -a -f -m "my version 1.4" v1.6 (annotated tag)
git push --tags (or) git push upstream v2.3.3
git tag -l "v1.8.5*" (list tags)
git show v1.4
git push --delete origin tagname #For remote
git tag --delete tagname #To remove local tag
```

### More awesome references:
* How to use git: https://guides.github.com/activities/contributing-to-open-source/#contributing
* How to write git commit messages: http://chris.beams.io/posts/git-commit/
* Commit guidelines: http://contribute.jquery.org/commits-and-pull-requests/#commit-guidelines
* Git reset/revert: https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting/
* Easy git rebase: http://hackalyst.info/easy-git-rebase/
* Real git rebase: http://hackalyst.info/real-rebase/
* A few git tricks: http://prakhar.me/articles/a-few-git-tricks/
* Working with submodules: https://github.com/blog/2104-working-with-submodules , https://chrisjean.com/git-submodules-adding-using-removing-and-updating/
* Another way of using git shortcuts (without using aliases): https://medium.freecodecamp.com/bash-shortcuts-to-enhance-your-git-workflow-5107d64ea0ff#.6r30rrj9l