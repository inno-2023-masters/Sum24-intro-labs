# DevOps Lab 1

## Task 1: SSH Commit Signature Verification

Benefits of signing commits include:

- Integrity: Signing commits help improve the integrity of the commits proving that the changes come from the expected source
- Identity Protection: Since it is easy to [impersonate a user](https://mikegerwitz.com/papers/git-horror-story.html), signed commits can help identify commit forgeries.
- Commit Policies: GitHub and other distributed VCS support rules and policies to accept/reject signed and unsigned commits. This can increase the security of the codebase.
