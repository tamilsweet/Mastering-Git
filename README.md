# Mastering-Git

Learning materials / tutorials to master git.

```
git status

git status --short
git status -s

git log

git switch -c newbranch

git checkout branch

git checkout sdfdfsd -> Creates detached HEAD

git add remote origin URL
git add remote upstream URL

git diff --staged
- Metadata : file version hash and file mode identifier
- Change Markers
- Chunk header
- Chunk changes

git diff --stage --no-renames

git add .

git commit -a -m
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

EMPTY File hash: e69de29 !? (/dev/null)
