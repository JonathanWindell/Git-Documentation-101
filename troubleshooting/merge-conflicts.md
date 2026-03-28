# Git Merge Conflicts

## 1. Introduction: How to Fix Merge Conflicts. 
Sometimes when merging two branches that have made changes to the same file git can't know which one is correct and a merge conflict will arise. You will then manually have to cherry pick the parts of the different files that you want to keep or choose either version to keep. 

## 2. Tutorial: How to Fix Merge Conflicts
When fixing a merge conflict it's important to know what to keep and what do discard. Often the one who's trying the merge has to take the responsibility as to figure out which parts to keep or file. To avoid merging any conflicts in to the main branch you need to know how merging, rebasing and squashing works which you can read about here. 

- [Merging](https://github.com/JonathanWindell/Git-Documentation-101/blob/main/examples/merging.md)
- [Rebasing](https://github.com/JonathanWindell/Git-Documentation-101/blob/main/examples/rebasing.md)
- [Squashing](https://github.com/JonathanWindell/Git-Documentation-101/blob/main/examples/squashing.md)
- [Git Official Documentation](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)

**Example:**
```git
$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")

Unmerged paths:
  (use "git add <file>..." to mark resolution)

    both modified:      index.html

no changes added to commit (use "git add" and/or "git commit -a")
```
This is an example where a merge can't be performed until the conflicts have been solved. Git will write what files have merge conflicts and it's up to you to fix them.

**Example:**
```git
<<<<<<< HEAD:index.html
<div id="footer">contact : email.support@github.com</div>
=======
<div id="footer">
 please contact us at support@github.com
</div>
>>>>>>> featureFooter:index.html
```

This example shows how there are two confliciting versions between your feature file and the `HEAD` which describes the `main` branch. You have to choose either version of the code and then remove the following lines. 

- `<<<<<<< HEAD:index.html`
- `=======` 
- `>>>>>>> featureFooter:index.html`. 

When this is done you can add the file using `git add` and fulfill the merge. 

| Command | Action |
| ------- | ------ |
| git log --merge | Lists commit causing the conflict on both branches |
| git mergetool | Launches a configured merge tool (e.g. vimdiff, VS Code) for visual resolution. |