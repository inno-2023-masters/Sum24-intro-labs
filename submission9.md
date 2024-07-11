# Task 1: Create Your First GitHub Actions Pipeline

## Step 1: Create a Workflow File:

Follow the GitHub Actions quickstart guide.

Create a directory named .github/workflows in the root of your repository.

Inside this directory, create a file named github-actions.yml with the following content

```yml
name: CI/CD configuration for lab9

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      - name: Run a one-line script
        run: echo Hello, world!
      - name: Run a multi-line script
        run: |
          echo Add other actions to build,
          echo test, and deploy your project.
```

![First Actions Build](/media/firstActionsBuild.png)

# Task 2: Gathering System Information and Manual Triggering

## Step 1: Configure a Manual Trigger
