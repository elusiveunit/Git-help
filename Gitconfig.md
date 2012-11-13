The global .gitconfig can be viewed in an editor with `git config --global --edit`. On Windows, it's usually located in `C:\Users\<user>\.gitconfig` (Vista, 7) or `C:\Documents and Settings\<user>\.gitconfig` (XP). On *nix systems, it's located in `~/.gitconfig`.

Some settings and aliases I use:

	[user]
		name = <username>
		email = <email>
	[core]
		editor = 'C:/Program Files/Sublime Text 2/sublime_text.exe' -w
	[color]
		ui = true
	[alias]
		pum = push origin master
		st = status
		ci = commit
		cim = commit -am
		br = branch
		co = checkout
		df = diff
		dc = diff --cached
		lg = log -p
		lol = log --graph --decorate --pretty=oneline --abbrev-commit
		lola = log --graph --decorate --pretty=oneline --abbrev-commit --all
		ls = ls-files
		unstage = reset HEAD --
		uncommit = reset HEAD~1