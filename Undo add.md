Undo git add before commit
==========================

As git tells you:

	Use "git reset HEAD <file>..." to unstage

A nice alias to add:

	git config --global alias.unstage 'reset HEAD --'

... which means one can do `git unstage <file>`.

To undo `git add .` use `git reset`.