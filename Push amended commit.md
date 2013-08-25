# Push amended commit

For when you immediately realize you need to adjust your last pushed commit.

In general, this **shouldn't be done**! If anyone pulled between the changes, there can be difficulties since `--force` can cause the remote repository to lose commits.

In the case of single-person projects, or when there are definitely no pulls, it's quite simple:

	git commit --amend
	git push --force (or just -f) (origin master)

As an alternative to --amend, one can use `git reset --soft HEAD~1` and then redo the commit with a new message.