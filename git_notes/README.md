# Git related commands

Install git on Red Hat distribution
<pre>
yum install git
</pre>

Install git on Fedora distribution
<pre>
dnf install git
</pre>

Install git on Debian based distribution
<pre>
sudo apt-get install git
</pre>

Display Git manual
<pre>
man git
</pre>

Display Git version
<pre>
git --version
</pre>

Config git environment
<pre>
git config

Example:
git config --global user.name "karthikk"
git config --global user.email "karthik@gmail.com"
git config --global core.editor "/usr/bin/vim"
</pre>

Display git config
<pre>
git config --list
</pre>

Manual for git config
<pre>
man git -config
</pre>

Add a file to git
<pre>
git add *file-name*
git add .    -> to add all files
</pre>

Remove a file from git
<pre>
git rm *file-name*
</pre>

Command to see list of files in Staging area
<pre>
git status    > state of staged and unstaged files
git status -s > shortened output of git status
git status -v > more verbose output of git status
man git-status > manual for git status
</pre>

Commit to Git
<pre>
git commit      > this invokes a editor to add commit comments
git commit -m "Commit Message"   > in-line commit message
git commit -a -m "message"       > commit modified file in staging area
man git-commit  > manual
</pre>

Ignore certain file types
<pre>
Create .gitignore in the project
Add to repository
Edit to add file name patters to ignore

Example:
echo "build/*"  >> .gitignore

Original file that contains file patters that git will not track:
.git/info/exclude

git check-ignore *pattern*
> to verify if git ignores a particular pattern

man gitignore
> documentation of gitignore file
</pre>