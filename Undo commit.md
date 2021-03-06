# Undo last Git commit

[Stack Overflow question](http://stackoverflow.com/questions/927358/undo-last-git-commit), thanks to [Kyralessa](http://stackoverflow.com/users/5486/kyralessa)

Say you have this, where C is your HEAD and (F) is the state of your files.

	             (F)
	A ---- B ---- C
	       |
	     master

If you want to **nuke commit C and never see it again**. You do this:

	git reset --hard HEAD~1

The result is:

	      (F)
	A ---- B
	       |
	     master

Now B is the HEAD. Because you used `--hard`, your files are reset to their state at commit B.

Ah, but suppose commit C wasn't a disaster, but just a bit off. You want to undo the commit but keep your changes for a bit of editing before you do a better commit. Starting again from the first point, you can do this, leaving off the --hard:

	git reset HEAD~1

In this case the result is:

	             (F)
	A ---- B ---- C
	       |
	     master


In both cases, HEAD is just a pointer to the latest commit. When you do a `git reset HEAD~1`, you tell Git to move the HEAD pointer back one commit. But (unless you use `--hard`) you leave your files as they were. So now `git status` shows the changes you had checked into C. You haven't lost a thing!

For the lightest touch, you can even undo your commit but leave your files and your index:

	git reset --soft HEAD~1

This not only leaves your files alone, it even leaves your index alone. When you do `git status`, you'll see that the same files are in the index as before. In fact, right after this command, you could do `git commit` and you'd be redoing the same commit you just had.

One more thing: Suppose you destroy a commit as in the first example, but then discover you needed it after all? Tough luck, right?

Nope, there's still a way to get it back. Type `git reflog` and you'll see a list of (partial) commit shas that you've moved around in. Find the commit you destroyed, and do this:

	git checkout -b someNewBranchName shaYouDestroyed

You've now resurrected that commit. Commits don't actually get destroyed in Git for some 90 days, so you can usually go back and rescue one you didn't mean to get rid of.

Undo older commit
-----------------

This can be done with the `git revert` command, which reverts the changes that the specified commits introduce, by making new commits. This requires your working tree to be clean (no modifications from the HEAD commit).  [Documentation](http://git-scm.com/docs/git-revert)

	git revert f1a3098f 2c67ee75

When reverting several commits, the `--no-commit` (or just `-n`) flag can be useful. This applies the revert changes without making the commits, so you don't end up with a long list of revert commits. This also means the index does not have to match the HEAD commit.