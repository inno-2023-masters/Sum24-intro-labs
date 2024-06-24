# Lab 3: Version Control
## Anton Buguev, a.buguev@innopolis.university, M23-RO-01

### Task 1. Understanding Version Control Systems.
1. Check info about commits:
```sh
git log
```
Result:
```sh
commit 185111351c7203cea469a70ab53923f477e76593 (HEAD -> lab3_solution, origin/lab3_solution)
Author: Anton <albugg2001@gmail.com>
Date:   Mon Jun 24 22:02:40 2024 +0300

    Create submission file
```
2. Copy commit hash and run

```sh
git cat-file -p 185111351c7203cea469a70ab53923f477e76593
```
Rsult:

```sh
tree 14ecc679ef9772e3025a4a1afbf5fcbc888ccbb0
parent 73e47a96362163df885d217f65567b4def9f4727
author Anton <albugg2001@gmail.com> 1719255760 +0300
committer Anton <albugg2001@gmail.com> 1719255760 +0300
gpgsig -----BEGIN SSH SIGNATURE-----
<SSH SIGNATURE>
-----END SSH SIGNATURE-----

Create submission file
```
3. Copy tree hash and run
```sh
git cat-file -p 14ecc679ef9772e3025a4a1afbf5fcbc888ccbb0
```
Result:
```sh
100644 blob ede183da8ef201e5f5737eea502edc77fd8a9bdc	README.md
100644 blob 5738bc15a0416ad2624df13badfb235052777e79	index.html
100644 blob c54a520ec380d5cc77c55f2e40fe921fc5580de5	lab1.md
100644 blob 1b99cc0044f93f556a0f6a599c7edf2f33f4944a	lab2.md
100644 blob 2f8463cc188ec6ca69ae7a0f98d38e132280becb	lab3.md
100644 blob d66a6867f90e48f6f44d9d80821aa1d866a24882	lab4.md
100644 blob 2ff5995a25b74c9c02a143c09a9601ce66001a9f	lab5.md
100644 blob 793bb19cd158fae333205f524eba5adc16718c58	lab6.md
100644 blob 51c4a9ee2271d822dc1b6843a7c20051ee767760	submission3.md
```
4. Copy blob hash and run
```sh
git cat-file -p 51c4a9ee2271d822dc1b6843a7c20051ee767760
```
Result:
```sh
# Lab 3: Version Control
## Anton Buguev, a.buguev@innopolis.university, M23-RO-01

### Task 1. Understanding Version Control Systems.
```
