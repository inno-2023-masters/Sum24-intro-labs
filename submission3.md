# Understanding Version Control Systems

## Inspecting Commit Object
```
tree 21c3ee0aaea1e2a6fcdc3dd7132f9d3b5d5c921a
parent 05e887ef91a30727bf72fad35e4453be6b8cfac5
author Kamil-Sabbagh <kamil.mousa9@gmail.com> 1721326982 +0300
committer Kamil-Sabbagh <kamil.mousa9@gmail.com> 1721326982 +0300
gpgsig -----BEGIN SSH SIGNATURE-----
 U1NIU0lHAAAAAQAAADMAAAALc3NoLWVkMjU1MTkAAAAgSAiSZrUHskd4d6zBvdFKeFO7LT
 03B3Hdl2R7q/FeOCIAAAADZ2l0AAAAAAAAAAZzaGE1MTIAAABTAAAAC3NzaC1lZDI1NTE5
 AAAAQFpNo/AR0jvnsbwFAF13lxz5PU8kc3V89ACq/KH7JyT8OEIiawMXqn5PsDZfWRzscu
 dz2ygl2kBjSNJTquOXCws=
 -----END SSH SIGNATURE-----

Third commit
```

## Inspecting Tree Object
```
100644 blob ede183da8ef201e5f5737eea502edc77fd8a9bdc	README.md
100644 blob 592c392a76cb8ac6bace5c68e0ed7262254168e3	file1.txt
100644 blob 5738bc15a0416ad2624df13badfb235052777e79	index.html
100644 blob 1dba99957c3bb59d40913294b83e40d5c38b6c0b	lab1.md
100644 blob bf5553698071098c4cb429db6b14811d4316e822	lab10.md
100644 blob 1b99cc0044f93f556a0f6a599c7edf2f33f4944a	lab2.md
100644 blob 2f8463cc188ec6ca69ae7a0f98d38e132280becb	lab3.md
100644 blob d66a6867f90e48f6f44d9d80821aa1d866a24882	lab4.md
100644 blob 2ff5995a25b74c9c02a143c09a9601ce66001a9f	lab5.md
100644 blob 793bb19cd158fae333205f524eba5adc16718c58	lab6.md
100644 blob e3daa92d57248cbfb76d60de86f7b2e0da7e9a22	lab7.md
100644 blob 0a88f0778b2534da7d9208198d1f2de010ca7459	lab8.md
100644 blob 15ab5a07323c525efeda1f3ce737612852e02f2b	lab9.md
```

## Inspecting Blob Object
```
Initial content
More content
Even more content
```

# Practice with Git Reset Command

## Steps Taken to Perform Git Reset Operations
```
git reset --soft HEAD~1
git reset --hard HEAD~1
```

## Reset and Reflog Process
```
git reflog
git reset --hard 5998213
```

## Examples and Outputs
```
Reflog Hash: 5998213
```

