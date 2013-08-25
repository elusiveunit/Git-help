# Remove file from repo only

[Stack Overflow question](http://stackoverflow.com/questions/1143796/git-remove-a-file-from-the-repository-without-deleting-it-from-the-local-filesy), thanks to [bdonlan](http://stackoverflow.com/users/36723/bdonlan) and [Sam Tyson](http://stackoverflow.com/users/194044/sam-tyson)

To remove a file from a repository without deleting it from the local filesystem:

	git rm --cached FILE

To remove an entire folder:

	git rm -r --cached FOLDER