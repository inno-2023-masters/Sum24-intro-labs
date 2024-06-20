# Lab 3

## Task 1
To find the hash of the latest commit I executed the log command:
```
$ git log -1

commit 5a2182e7e6a5b18fc3fe72a23e06bdfa4abb7b86 (HEAD -> Lab3)
Author: Elizaveta Kovanova <e.kovanov@innopolis.university>
Date:   Thu Jun 20 14:27:20 2024 +0300
```

### Output with commit hash
With the obtained hash I can see the output of the commit_hash cat-file command:
```
$ git cat-file -p 5a2182e7e6a5b18fc3fe72a23e06bdfa4abb7b86

tree 427fb2622172550b185ebd0c934e1a181390c713
parent 2c1fffa277473ab4582e95e3d7de189813b0e486
author Elizaveta Kovanova <e.kovanov@innopolis.university> 1718882840 +0300
committer Elizaveta Kovanova <e.kovanov@innopolis.university> 1718882840 +0300
gpgsig -----BEGIN SSH SIGNATURE-----
 ...
 <redacted SSH signature>
 ...
 -----END SSH SIGNATURE-----

```

### Output with tree hash
The commit contents include the tree hash. To see the tree it references execute:
```
$ git cat-file -p 427fb2622172550b185ebd0c934e1a181390c713

100644 blob ede183da8ef201e5f5737eea502edc77fd8a9bdc	README.md
100644 blob 5738bc15a0416ad2624df13badfb235052777e79	index.html
100644 blob c54a520ec380d5cc77c55f2e40fe921fc5580de5	lab1.md
100644 blob 1b99cc0044f93f556a0f6a599c7edf2f33f4944a	lab2.md
100644 blob 2f8463cc188ec6ca69ae7a0f98d38e132280becb	lab3.md
100644 blob ee2e111d04704f3b786d6de30381034edc0fefb6	lab4.md
100644 blob cc510bdf575297a13cfb6a509601de1fb800bee0	submission3.md

```

### Output with blob hash
To see the actual blob, select the hash for the recent commit in submission3.md file:
```
$ git cat-file -p cc510bdf575297a13cfb6a509601de1fb800bee0

# Lab 3

## Task 1

### Output with blob hash

### Output with tree hash

### Output with commit hash


## Task 2
```

## Task 2

### Steps taken in Git reset operations and command outputs

* Series of commits and their respective outputs:
```
$ echo "First commit" > file.txt
$ git add file.txt 
$ git commit -m "First commit"

[git-reset-practice 68bcbf6] First commit
 1 file changed, 1 insertion(+)
 create mode 100644 file.txt
```
```
$ echo "Second commit" >> file.txt
$ git add file.txt 
$ git commit -m "Second commit"

[git-reset-practice e2fb067] Second commit
 1 file changed, 1 insertion(+)

```
```
$ echo "Third commit" >> file.txt
$ git add file.txt 
$ git commit -m "Third commit"

[git-reset-practice e817840] Third commit
 1 file changed, 1 insertion(+)

```

### Reset and reflog process