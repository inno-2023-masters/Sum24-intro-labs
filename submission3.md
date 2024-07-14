# Lab 3

## Task 1

Command:

```
git cat-file -p  73e47a96362163df885d217f65567b4def9f4727
```

Output:

```
tree 5062f5888d41e93cec8da9b9d762f03b96016e61
parent 4aea5c959f64f8bc3860d3f806428a1aba1321cd
author Dmitriy Creed <creed@soramitsu.co.jp> 1719164403 +0300
committer Dmitriy Creed <creed@soramitsu.co.jp> 1719164403 +0300

Update lab4 Software Distribution

Signed-off-by: Dmitriy Creed <creed@soramitsu.co.jp>
```

Example with a tree hash:

![image-20240714160226818](screens/tree.png)

Example with a blob:

![image-20240714160912455](screens/blob.png)

## Task 2

### Playing with commits

![image-20240714161409935](screens/commits.png)

### Reflog output

![image-20240714161251347](screens/reflog.png)

### Recovering the reset

![image-20240714161540179](screens/recover.png)
