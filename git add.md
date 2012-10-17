Difference of "git add -A" and "git add ."
==========================================

[Stack Overflow question](http://stackoverflow.com/questions/572549/difference-of-git-add-a-and-git-add), thanks to [Charles Bailey](http://stackoverflow.com/users/19563/charles-bailey)

`git add -A` is equivalent to `git add .; git add -u`.

The important point about `git add .` is that it looks at the working tree and adds all those paths to the staged changes if they are either changed or are new and not ignored, it does not stage any 'rm' actions.

`git add -u` looks at all the currently tracked files and stages the changes to those files if they are different or if they have been removed. It does not add any new files, it only stages changes to already tracked files.

`git add -A` is a handy shortcut for doing both.

Summary:

- `git add .` stages new and modified, **not deleted**
- `git add -u` stages modified and deleted, **not new**
- `git add -A` do both `.` and `-u`, stages **all**