## Task 1
The output of the command using blobs hashes, commits hashes, and tree hashes:
```
git cat-file -p
```

The repository file tree at this point is: 
```
➜  new_repo git:(main) tree .
.
├── main.py
├── readme
└── src
    ├── __init__.py
    └── feat.py

2 directories, 4 files
```


1. Blob hash:

    ```
    ➜  new_repo git:(main) git cat-file -p dc0994d12ebe8d55b33231da587c693d386fe47e


    if __name__ == '__main__':
        print("main is being executed")
    ```


2. Commit hash:
    ```
    ➜  new_repo git:(main) git cat-file -p a14a8419ec0317d293e564e0e31771a745fdb49e
    tree 78298a6addacead097db808f58a9eabefba1c3bd
    parent 5252335e1d7b962a767eb71462a02c9addfab6b9
    author Mohammad Shahin <pr.hash2001@gmail.com> 1721308157 +0300
    committer Mohammad Shahin <pr.hash2001@gmail.com> 1721308157 +0300
    gpgsig -----BEGIN SSH SIGNATURE-----
    U1NIU0lHAAAAAQAAADMAAAALc3NoLWVkMjU1MTkAAAAgz+g8zXqfdMd66naVtfTOexz+2o
    0ppn7fQH1b+/43S0wAAAADZ2l0AAAAAAAAAAZzaGE1MTIAAABTAAAAC3NzaC1lZDI1NTE5
    AAAAQFj2HxfP9BBSy3XsnIS3qA4s4iMunaDssVrvWYuX3HPMyJitsZshmaQzx6Kw7bTq5S
    cOfaohAy5rkQdDiHj0OAM=
    -----END SSH SIGNATURE-----

    add src dir
    ```

3. Tree hash:
    ```
    ➜  new_repo git:(main) git cat-file -p e81d494d0b6a0eb877a57ae4eb5244fba7f3a666
    100644 blob e69de29bb2d1d6434b8b29ae775ad8c2e48c5391    __init__.py
    100644 blob e69de29bb2d1d6434b8b29ae775ad8c2e48c5391    feat.py
    ```

## Task 2

First, the series of commits were created in the branch. The commits are [First commit, Second commit, Third commit]. Then the two types of reset were done.

1. Soft reset:
The command below moves the head one commit back, but keeps the file changes of the last commit as staged changes. This makes recovering possible in two ways; we can either re-commit the staged file, or use `git reflog`.

```
➜  git reset --soft HEAD~1
```

This made us at commit "Second commit" with "Third commit"'s file changes kept stages.

```
➜  new_repo git:(git-reset-practice) ✗ git reflog
➜  new_repo git:(git-reset-practice) ✗ git reset HEAD@{1} --hard
```

```
➜  git reflog

545cb6f (HEAD -> git-reset-practice) HEAD@{0}: reset: moving to HEAD@{1}
7dae848 HEAD@{1}: reset: moving to HEAD~1
545cb6f (HEAD -> git-reset-practice) HEAD@{2}: commit: Third commit
7dae848 HEAD@{3}: commit: Second commit
0c87b81 HEAD@{4}: commit: First commit
a14a841 (main) HEAD@{5}: checkout: moving from main to git-reset-practice
a14a841 (main) HEAD@{6}: commit: add src dir
5252335 HEAD@{7}: commit: add main file
39ac9c6 HEAD@{8}: commit (initial): init
```

```
➜  git reset HEAD@{1} --hard
```

This brought the head back to "Third commit".

We can list the last three commits:

```
➜  git log -n 3
commit 545cb6f3919e6c0a24904fe1b4b2d5e5252814a2 (HEAD -> git-reset-practice)
Author: Mohammad Shahin <pr.hash2001@gmail.com>
Date:   Thu Jul 18 18:12:31 2024 +0300

    Third commit

commit 7dae848c21c70679a023b3edcf4dbc76b42d1602
Author: Mohammad Shahin <pr.hash2001@gmail.com>
Date:   Thu Jul 18 18:12:22 2024 +0300

    Second commit

commit 0c87b81afae125c9187a943958cd17f6b3751b72
Author: Mohammad Shahin <pr.hash2001@gmail.com>
Date:   Thu Jul 18 18:11:57 2024 +0300

    First commit
```

2. Hard reset:

The command below moves the head one commit back, but completely removes the changes associated with the last commit. 

```
git reset --hard HEAD~1
```

`file.txt` now contains only the following. The "Third commit" text was deleted: 

```
First commit
Second commit
```

Now we run: 

```
➜  git reflog
7dae848 (HEAD -> git-reset-practice) HEAD@{0}: reset: moving to HEAD~1
545cb6f HEAD@{1}: reset: moving to HEAD@{1}
7dae848 (HEAD -> git-reset-practice) HEAD@{2}: reset: moving to HEAD~1
545cb6f HEAD@{3}: commit: Third commit
7dae848 (HEAD -> git-reset-practice) HEAD@{4}: commit: Second commit
0c87b81 HEAD@{5}: commit: First commit
a14a841 (main) HEAD@{6}: checkout: moving from main to git-reset-practice
a14a841 (main) HEAD@{7}: commit: add src dir
5252335 HEAD@{8}: commit: add main file
39ac9c6 HEAD@{9}: commit (initial): init
```

Next we run:

```
git reset HEAD@{1} --hard
```

And the changes are back (and committed).
