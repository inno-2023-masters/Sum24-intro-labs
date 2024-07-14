# Lab1 

## Task 1

1. Brief summary explaining the benefits of signing commits.
    - The main idea of siggning the commits is the same as signing anything - it is done to enshure the source of data (in this case the source of the commits). It is a way to enshure the author of hanges is legitamate ensuring the security and integrity
2. Make signed commit
    - Gen keys `ssh-keygen -t ed25519 -C "<e-mail>"`
    - Add private key to repo
    ```bash
    git config user.signingkey ~/.ssh/id_ed25519
    git config commit.gpgSign true
    git config gpg.format ssh
    ```
    - Commit `git add . && git commit -S -m 'Remake keys with actual email'`
    - Push `git push origin master`