# Mastering-Git

Learning materials / tutorials to master git.

```
git status

git status --short
git status -s

git branch

git branch --all

git switch -c newbranch

git checkout branch

git checkout sdfdfsd -> Creates detached HEAD

# Discard changes in the working directory
git checkout -- <filename>

# Discard changes and checkout recently commited change
git checkout HEAD <filename>

git add remote origin URL
git add remote upstream URL

git add .

git push origin master
git push <remote name> <branch name>

git remote

# Delete from git and local - just shows warning
git rm <filename>
# Do not delete locally
git rm --cached <filename>
# Delete from git and local force
git rm -f <filename>

# Rename file(s)
git mv <filename> <new-filename>

# Other method
mv <filename> <new-filename>
git add <new-filename>
git add <filename>
# Git finds that this file is renamed

# Show commit details
git show <commithash>

# Show commit details of commit pointed by branch tip
git show <branchname>

# Show commit details of commit pointed by HEAD
git show HEAD

# Show commit details parent commit of the HEAD
git show HEAD^
# 2 commits older or parent of parent of HEAD
git show HEAD^^
# Another way
git show HEAD~2
# Pick one of the multiple parents
git show HEAD~2^2

# Show the commit one month ago
git show HEAD@{"1 month ago"}
```

```
$ git add employees.txt

$ git commit -m "adding employees file"
[master 9efad90] adding employees file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 employees.txt

$  git diff --staged

diff --git a/employees.txt b/employees.txt
index e69de29..552ad38 100644
--- a/employees.txt
+++ b/employees.txt
@@ -0,0 +1 @@
+Tamilmozhi | 9884622349

tgunasekar@tgunasekar-inl MINGW64 /d/git/Mastering-Git (master)
$ git diff --staged
diff --git a/vendors.txt b/vendors.txt
new file mode 100644
index 0000000..e69de29


$ git diff --staged
diff --git a/vendors.txt b/vendors.txt
new file mode 100644
index 0000000..552ad38
--- /dev/null
+++ b/vendors.txt
@@ -0,0 +1 @@
+Tamilmozhi | 9884622349

```

sha1 hash
EMPTY File hash: e69de29 !? (/dev/null)

## Git Log

```
git log

# Show only recent 3 logs
git log -3

# Show only one line per log
git log --oneline

# Show log with stat, no of changes in each file
git log --stat

# Show log with diff
git log --patch

# Show as graph
git log --graph --decorate --oneline

# Grep in log history
git log --grep <search term> --oneline

# Log of commits between 2 branches
# both .. and ... works
git log branch1..branch2 --oneline

# Group logs by user
git shortlog
```

## Git commit

Ref: [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/)

### The seven rules of a great Git commit message

1. Separate subject from body with a blank line
2. Limit the subject line to 50 characters
3. Capitalize the subject line
4. Do not end the subject line with a period
5. Use the imperative mood in the subject line
6. Wrap the body at 72 characters
7. Use the body to explain what and why vs. how

GitHub’s UI warns if you go past the 50 character limit and will truncate any subject line longer than 72 characters with an ellipsis
So shoot for 50 characters, but consider 72 the hard limit.

**A properly formed Git commit subject line should always be able to complete the following sentence:**

If applied, this commit will your subject line here
For example:

- If applied, this commit will _**refactor subsystem X for readability**_
- If applied, this commit will _**update getting started documentation**_
- If applied, this commit will _**remove deprecated methods**_
- If applied, this commit will _**release version 1.0.0**_
- If applied, this commit will _**merge pull request #123 from user/branch**_

Notice how this doesn’t work for the other non-imperative(indicative) forms:

- If applied, this commit will _**fixed bug with Y**_
- If applied, this commit will _**changing behavior of X**_
- If applied, this commit will _**more fixes for broken stuff**_
- If applied, this commit will _**sweet new API methods**_

> leave out details about how a change has been made. Code is generally self-explanatory in this regard (and if the code is so complex that it needs to be explained in prose, that’s what source comments are for).

> Just focus on making clear the reasons why you made the change in the first place—the way things worked before the change (and what was wrong with that), the way they work now, and why you decided to solve it the way you did.

> The future maintainer that thanks you may be yourself!

```
# add all tracked files to the staging area and commits them in one step
git commit -a -m

# commit any files that have already been added to the staging area
git commit -m " "

# Merge the staged changes with earlier commit
git commit --amend
```

Details of recent commit

```
vi .git/COMMIT_EDITMSG
```

## Git Stash

Move the content of working area to stash and checkout latest commit from repo.
Starting with => stash@{0}

```
git add .
git stash

# Stash all the files
git stash --include-untracked

# Restore the recent stash but not clear it
git stash apply

# Clear stash
git stash clear

git stash list
git stash show
git stash pop
```

## Git Merge

```
git merge new_branch
# > Merge made by the 'recursive' strategy
```

## Git Reset

```
# Reset commit and move back to staging area
git reset --soft <commitHash>

# Reset branch to commit and updates staging area and working directory
git reset --hard <commitHash>

# Default reset is --mixed, move changes back to working directory !?
git reset <commitHash>
git reset --mixed <commitHash>

# Move to trash, deletes working directory and staging are content also.
git reset --trash <commitHash>

# Restore particular file from recent commit
git reset HEAD <filename>
```

## Plumbing Commands

```
git hash-object

# Read the content to hash from standard input
echo 'hello' | git hash-object --stdin

# Store it in git under .git/objects/xx/x...xx
echo 'hello' | git hash-object --stdin -w

# Print the type of hash file
git cat-file <file hash> -t
blob

# Pretty print the hash file
git cat-file <file hash> -p

# Count number of objects
git count-objects

git show-ref <branchname>
git show-ref master
```

## Git diff

```
git diff --staged
- Metadata : file version hash and file mode identifier
- Change Markers
- Chunk header
- Chunk changes

git diff --stage --no-renames

# Diff between HEAD and 2 commits before HEAD
git diff HEAD HEAD~2
```

## Git Rebase

```
# Interactive rebase, apply only on local commits.
git rebase --interactive
git rebase -i

```

## Git Reflog

```
git reflog HEAD

git reflog refs/heads/master
```

## Git Revert

```
git revert <commit hash>
git revert HEAD
```

## Git blame

```
# Show each line of the file along with the commit in which it was added
# ^ denote first commit
git blame <filename>
```

## New Commands

```
git filter-branch
git rerere
git cherry-pick
git bisect
```
