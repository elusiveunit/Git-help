# Commit parts of a file

[Stack Overflow question](http://stackoverflow.com/questions/1085162/how-can-i-commit-only-part-of-a-file-in-git), thanks to [cloudhead](http://stackoverflow.com/users/120146/cloudhead) and [Jonathan Day](http://stackoverflow.com/users/336905/jonathan-day)

You can do `git add -p filename`, and it'll ask you what you want to stage. You can then:

* hit `s` to split whatever change into smaller chunks. This only works if there is at least one unchanged line in the "middle" of the hunk, which is where hunk will be split
* then hit `y` to stage that chunk
	* or `n` to not stage that hunk
	* or `e` to manually edit the chunk (useful when git can't split it automatically)
* and `d` to exit or go to the next file.
* Use `?` to get the whole list of available options.

If the file is not in the repository yet, do first `git add -N filename`. Afterwards you can go on with `git add -p filename`.