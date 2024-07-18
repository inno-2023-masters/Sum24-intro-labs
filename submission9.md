# Task 1: Create Your First GitHub Actions Pipeline

## Step 1: Follow the Official GitHub Actions Quickstart Guide

**Observations and Key Concepts:**
- **GitHub Actions:** A tool to automate software workflows directly from your GitHub repository.
- **Workflows:** Defined by YAML files located in the `.github/workflows` directory.
- **Jobs:** A workflow is composed of one or more jobs, which run in parallel by default.
- **Steps:** Jobs consist of multiple steps, which can run commands or actions.

**Steps Followed:**
1. **Create a New Repository:**
   - Created a repository named `github-actions-demo`.
   
2. **Create Workflow File:**
   - Created a `.github/workflows` directory.
   - Added a YAML file named `main.yml` with the following content:
     ```yaml
     name: CI

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

3. **Push Changes and Observe Workflow:**
   - Pushed changes to GitHub.
   - Observed that the workflow ran automatically upon the push.

**Workflow Execution Output:**
- Workflow ran successfully.
- Output observed in the Actions tab showed the steps executed with logs for each command.

**Errors Encountered:**
- No errors were encountered.

# Task 2: Gathering System Information and Manual Triggering

## Step 1: Configure a Manual Trigger

**Changes Made:**
- Modified the workflow file to add a manual trigger using the `workflow_dispatch` event.
  ```yaml
  name: CI

  on:
    push:
    workflow_dispatch:

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

#### Step 2: Gather System Information

**Changes Made:**
- Added steps to gather system information about the runner, hardware specifications, and OS details.
  ```yaml
  name: CI

  on:
    push:
    workflow_dispatch:

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
      - name: Gather system information
        run: |
          echo "Gathering system information..."
          uname -a
          lscpu
          cat /etc/os-release
  ```

**Gathered System Information:**
- **Kernel Information:** Output from `uname -a`.
- **CPU Information:** Output from `lscpu`.
- **OS Information:** Output from `cat /etc/os-release`.

