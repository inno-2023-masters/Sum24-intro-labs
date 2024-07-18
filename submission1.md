# Lab 1 submission

## Benefits of signing commits
Proving identity: Github allows for any user to set their name and email to what they desire in their configuration. This also will be reflected on the Github UI. This is for Github is not a security vulnerability. User A who wants to impersonate User B can't access B's private repositories for example without an access token. However, it is troublesome to guess if a commit actually came from a specific person. To address this issue, Github allows users to store SSH or GPG public keys in their account. User A will use the private key stored locally to verify (sign) the commits he/she carried out. Thus if someone is known to verify (sign) all their commits, and a new unverified one is published, it is safer to ignore that commit. Problems like this may happen in private organizations as well if a member wants to act maliciously and hide their commits under another person's identity.

## Merge Strategies

The three common Git merge strategies—Standard Merge, Squash and Merge, and Rebase and Merge—each offer some pros and cons:
1. *Standard Merge*: This strategy merges two branches by creating a merge commit that keeps the full history of changes. The downside is that it can result in a more messy history with many merge commits.

2. *Squash and Merge*: This method combines all commits from a feature branch into a single commit before merging it into the target branch. It simplifies the commit history, making it easier to navigate. However, the tradeoff is we lose the detailed history of individual changes from the feature branch, which can make understanding the development process and debugging more challenging.

3. *Rebase and Merge*: This approach reapplies the commits from a feature branch onto the base branch, creating a linear history. It produces a clean and easy-to-follow history without merge commits. However, since it rewrites commit history, it can be risky in a collaborative environment, potentially causing issues.

Standard Merge is often favored in collaborative environments because it preserves the complete history of changes, including the context and time of branch integrations. The detailed history is beneficial for understanding project evolution and resolving issues. In contrast, Squash and Merge and Rebase and Merge provide cleaner histories but at the cost of lost context and potential risks associated with rewriting history.
