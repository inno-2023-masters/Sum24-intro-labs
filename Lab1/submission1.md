# Lab 1: Introduction to DevOps with Git

## Task 1: SSH Commit Signature Verification

**Objective**: Understand the importance of commit signing using SSH keys and set up commit signature verification.

1. **Explore the Importance of Signed Commits**:
   - **Research**: Learn why commit signing is crucial for verifying the integrity and authenticity of commits.
     - Commits are made to the different project of different size, value and importancy. For some local projects of one person or small group commit signing might be redundant and will only lead to spending unnecessary time on useless work.  
       On the other hand, there are some middle size teams and projects. In this case signing is suggested to divide responsibility for the made changes on certain people, who were making commits. With commit signing it is almost impossible (I don't like using "completely impossible" in the context of IT, since each year people prove that nothing is fully safe) to say, that someone changed their commits, even if they were made a long time ago.  
       The third case is the projects of huge size (like Linux kernel) projects or projects of high responsibility (autopilot for planes), where even a small mistake can lead to huge fails or critical backdoors. In this case only a small group of users can commit or appove commits into high-secured branches. In this case signiture of commits is necessary for the safety reasons.

2. **Set Up SSH Commit Signing**:
   - **Option 2: Generate a New SSH Key (Recommended: ed25519 Format)**:
     - Generate a new SSH key pair using the ed25519 format.

       ```sh
       ssh-keygen -t ed25519 -C "your_email@example.com"
       ```

     - Add the public key to your GitHub account.
       - [GitHub Guide to Adding SSH Key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

   - Configure Git to use your new SSH key for signing commits.

     ```sh
     git config --global user.signingkey <YOUR_SSH_KEY>
     git config --global commit.gpgSign true
     git config --global gpg.format ssh
     ```

3. **Make a Signed Commit**:
   - Create and sign a commit.

     ```sh
     git commit -S -m "Your signed commit message"
     ```

   - Push the commit with your submission1.md file.

## Task 2: Merge Strategies in Git

**Objective**: Research the differences between merge strategies in Git and modify repository settings to allow only the standard merge strategy.

1. **Research Merge Strategies**:
   - **Standard Merge**: Combines two branches by creating a merge commit. 
     - Pros:  
       - Saves full history of commits and their relationships. It makes history more understandable.  
     - Cons:
       - Since we save the full history plus some additional merge commits, the log might be huge, making it harder to follow.
   - **Squash and Merge**: Combines all commits from a feature branch into a single commit before merging.  
     - Pros:
       - More compressed history.
     - Cons:
       - Losing the connection to the feature branch.
   - **Rebase and Merge**: Reapplies commits from a feature branch onto the base branch.
     - Pros:
       - Produces very straightforward and simple history with no extra commits.
     - Cons:
       - It rewrites the history, which is not good. Also requires forced push, which is simply dangerous.
   - **Summary**: Standard merge is prefered in collaborative environments since it saves all the history, which is crucial.

2. **Modify Repository Settings**:
   - **Disable Squash and Rebase Merge**:
     - Go to the Settings page of your forked repository on GitHub.
     - Navigate to the "Options" section.

   - Status: Done