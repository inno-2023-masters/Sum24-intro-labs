# Lab 3 : Version Control

## Task 1: Understanding Version Control Systems

- Adding a new directory and file to the repository.
```
suwil@SUWILANJI-PCV3 MINGW64 ~/Desktop/First Year Masters/Third Semester/Devops/Lab 1/Sum24-intro-labs (lab_three)
$ mkdir testFolder

suwil@SUWILANJI-PCV3 MINGW64 ~/Desktop/First Year Masters/Third Semester/Devops/Lab 1/Sum24-intro-labs (lab_three)
$ ls
index.html  lab1.md  lab2.md  lab3.md  lab4.md  lab5.md  lab6.md  README.md  testFolder/

suwil@SUWILANJI-PCV3 MINGW64 ~/Desktop/First Year Masters/Third Semester/Devops/Lab 1/Sum24-intro-labs (lab_three)
$ cd testFolder/

suwil@SUWILANJI-PCV3 MINGW64 ~/Desktop/First Year Masters/Third Semester/Devops/Lab 1/Sum24-intro-labs/testFolder (lab_three)
$ echo "hello world" > test.txt

suwil@SUWILANJI-PCV3 MINGW64 ~/Desktop/First Year Masters/Third Semester/Devops/Lab 1/Sum24-intro-labs/testFolder (lab_three)
$ ls
test.txt

suwil@SUWILANJI-PCV3 MINGW64 ~/Desktop/First Year Masters/Third Semester/Devops/Lab 1/Sum24-intro-labs (lab_three)
$ git status
On branch lab_three
Your branch is up to date with 'origin/lab_three'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        testFolder/

nothing added to commit but untracked files present (use "git add" to track)

suwil@SUWILANJI-PCV3 MINGW64 ~/Desktop/First Year Masters/Third Semester/Devops/Lab 1/Sum24-intro-labs (lab_three)
$ git add .
warning: in the working copy of 'testFolder/test.txt', LF will be replaced by CRLF the next time Git touches it

suwil@SUWILANJI-PCV3 MINGW64 ~/Desktop/First Year Masters/Third Semester/Devops/Lab 1/Sum24-intro-labs (lab_three)
$ git commit -m "add test dir"
[lab_three 7b69c0a] add test dir
 1 file changed, 1 insertion(+)
 create mode 100644 testFolder/test.txt

suwil@SUWILANJI-PCV3 MINGW64 ~/Desktop/First Year Masters/Third Semester/Devops/Lab 1/Sum24-intro-labs (lab_three)
$ git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 12 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (4/4), 563 bytes | 563.00 KiB/s, done.
Total 4 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:Suwi-inc/Sum24-intro-labs.git
   73e47a9..7b69c0a  lab_three -> lab_three

```
-  Inspecting the contents of blobs, trees, and commits.
```
suwil@SUWILANJI-PCV3 MINGW64 ~/Desktop/First Year Masters/Third Semester/Devops/Lab 1/Sum24-intro-labs (lab_three)
$ git rev-parse HEAD:testFolder/test.txt
3b18e512dba79e4c8300dd08aeb37f8e728b8dad

suwil@SUWILANJI-PCV3 MINGW64 ~/Desktop/First Year Masters/Third Semester/Devops/Lab 1/Sum24-intro-labs (lab_three)
$ git cat-file -p 3b18e512dba79e4c8300dd08aeb37f8e728b8dad
hello world
```
```
suwil@SUWILANJI-PCV3 MINGW64 ~/Desktop/First Year Masters/Third Semester/Devops/Lab 1/Sum24-intro-labs (lab_three)
$ git rev-parse HEAD:testFolder
c3b8bb102afeca86037d5b5dd89ceeb0090eae9d

suwil@SUWILANJI-PCV3 MINGW64 ~/Desktop/First Year Masters/Third Semester/Devops/Lab 1/Sum24-intro-labs (lab_three)
$ git cat-file -p c3b8bb102afeca86037d5b5dd89ceeb0090eae9d
100644 blob 3b18e512dba79e4c8300dd08aeb37f8e728b8dad    test.txt
```
```
suwil@SUWILANJI-PCV3 MINGW64 ~/Desktop/First Year Masters/Third Semester/Devops/Lab 1/Sum24-intro-labs (lab_three)
$ git cat-file -p 7b69c0a
tree c558622357846dcbd9419026c2f5db297a38b7f2
parent 73e47a96362163df885d217f65567b4def9f4727
author Suwi-inc <suwilanjisilwamba@gmail.com> 1719300383 +0300
committer Suwi-inc <suwilanjisilwamba@gmail.com> 1719300383 +0300
gpgsig -----BEGIN SSH SIGNATURE-----
 U1NIU0lHAAAAAQAAADMAAAALc3NoLWVkMjU1MTkAAAAgjC54SdeBdUFKlf8h+WLw/pARjr
 WJOobDGJrnHtL1TlEAAAADZ2l0AAAAAAAAAAZzaGE1MTIAAABTAAAAC3NzaC1lZDI1NTE5
 AAAAQD5alr9RtSzYBtXFMFjzrFjSyHv8nc5oxlaiUzxZJUuwKfk2QICjd8HJdxdIxEkGKj
 BKKSpa3OwIWtVYaC0argY=
 -----END SSH SIGNATURE-----

add test dir
```
## Task 2: Practice with Git Reset Command
