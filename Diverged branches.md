Diverged branches
=================

[Stack Overflow question](http://stackoverflow.com/questions/2452226/master-branch-and-origin-master-have-diverged-how-to-undiverge-branches), thanks to [VonC](http://stackoverflow.com/users/6309/vonc)

> "Your branch and 'origin/master' have diverged, # and have 1 and 1 different commit(s) each, respectively."

	... o ---- o ---- A ---- B  origin/master (upstream work)
	                   \
	                    C  master (your work)

### Merge

$ git merge origin/master

This tells Git to integrate the changes from origin/master into your work and create a merge commit. The graph of history now looks like this:

	... o ---- o ---- A ---- B  origin/master (upstream work)
	                   \      \
	                    C ---- M  master (your work)

The new merge commit M has two parents, each representing one path of development that led to the content stored in the commit.

Note that the history behind M is now non-linear. We have chosen (for now) to disallow non-linear history in cmake.org/cmake.git so an attempt to push M into our repository will fail. Until this restriction is lifted, please rebase your work instead.

### Rebase

$ git rebase origin/master

This tells Git to replay commit C (your work) as if you had based it on commit B instead of A.

	... o ---- o ---- A ---- B  origin/master (upstream work)
	                          \
	                           C'  master (your work)

Commit C' is a new commit created by the git rebase command. It is different from C in two ways:

1. It has a different history: B instead of A.
2. It's content accounts for changes in both B and C: it is the same as M from the merge example.

Note that the history behind C' is still linear. We have chosen (for now) to allow only linear history in cmake.org/cmake.git.

The git pull command provides a shorthand way to fetch from origin and rebase local work on it:

	$ git pull --rebase

This combines the above fetch and rebase steps into one command.