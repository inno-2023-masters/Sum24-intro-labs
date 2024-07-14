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
    - Result:
    ![alt text](1.png)

## Task 2

1. Brief summary comparing these merge strategies
    - Merge commit - creates the mearge commit that integrates all comits to the target branch and adds the m to the end of the history.
        - Pros: default approach, keeps all nessesary metadata 
        - Cons: create a banch of useless merge commits that introduce some mess to the repoitory.
    - Squash and Merge - combines all the commits into one big commit that is added to the target brunch in the end.
        - **Pros**: Clear repo in the end that show the result of the repo evolution
        - **Cons**: Deletes metadata about the authors of the commits, should not use the merged brunch us could mess up alot of things (by re-commiting the changes squashed in previous merge)
    - Rebase and Merge: rewrites the git history as if all the commits was commited to the target branch initialy
        - **Pros**: one big, clear, linear git history (used in Trunk approach which is alternative to git-flow)
        - **Cons**: easy to mess up and rewrite changes that was done after
        - Commit added to the etarget brunch witout the signature
        - Merge conflicts could not be resolved in a single commit (if 10 commits have conflicts you have to resolve the it 10 time instead of one)
2. 
![alt text](2.png)