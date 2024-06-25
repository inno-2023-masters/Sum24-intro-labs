### Task 1. Understanding Version Control Systems.
```Git Log``` to find commit hash
```sh
commit 87128d69d3f3606d005a2b591e625f86a92fc0ad (HEAD -> lab-3)
Author: AppleWolf <Stealth102@yandex.ru>

Date:   Tue Jun 25 14:04:38 2024 +0300

    Create submission file
```
```git cat-file -p 87128d69d3f3606d005a2b591e625f86a92fc0ad``` to inspect the contents of commit

```sh
tree c0c781579a11bf8df1020a3029255ee4509d2738
parent 73e47a96362163df885d217f65567b4def9f4727
author AppleWolf <Stealth102@yandex.ru> 1719313478 +0300
committer AppleWolf <Stealth102@yandex.ru> 171931347 +0300
```
```git cat-file -p c0c781579a11bf8df1020a3029255ee4509d2738``` to inspect the contents of tree
```sh
100644 blob ede183da8ef201e5f5737eea502edc77fd8a9bdc    README.md
100644 blob 5738bc15a0416ad2624df13badfb235052777e79    index.html
100644 blob c54a520ec380d5cc77c55f2e40fe921fc5580de5    lab1.md
100644 blob 1b99cc0044f93f556a0f6a599c7edf2f33f4944a    lab2.md
100644 blob 2f8463cc188ec6ca69ae7a0f98d38e132280becb    lab3.md
100644 blob d66a6867f90e48f6f44d9d80821aa1d866a24882    lab4.md
100644 blob 2ff5995a25b74c9c02a143c09a9601ce66001a9f    lab5.md
100644 blob 793bb19cd158fae333205f524eba5adc16718c58    lab6.md
100644 blob 955f5b75215bcc6f01f5c79461c27c2d0cb04414    submission3.md
```
```git cat-file -p 955f5b75215bcc6f01f5c79461c27c2d0cb04414``` to inspect the contents of blob
```sh
    ### Task 1. Understanding Version Control Systems.
```