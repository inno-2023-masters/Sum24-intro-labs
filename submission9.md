# CI/CD Lab - GitHub Actions

## Task 1: Create Your First GitHub Actions Pipeline

### Observations, Key Concepts, and Steps Followed

#### Reading the Official Guide
I followed the official GitHub Actions [quickstart guide](https://docs.github.com/en/actions/quickstart). 

#### Creating the Workflow File
I created a `.github/workflows` directory in my repository and added a new file named `github-actions-demo.yml`. I copied the provided YAML content into this file and committed the changes to my branch.
```
name: GitHub Actions Demo
run-name: ${{ github.actor }} is testing out GitHub Actions 🚀
on: [push]
jobs:
  Explore-GitHub-Actions:
    runs-on: ubuntu-latest
    steps:
      - run: echo "🎉 The job was automatically triggered by a ${{ github.event_name }} event."
      - run: echo "🐧 This job is now running on a ${{ runner.os }} server hosted by GitHub!"
      - run: echo "🔎 The name of your branch is ${{ github.ref }} and your repository is ${{ github.repository }}."
      - name: Check out repository code
        uses: actions/checkout@v4
      - run: echo "💡 The ${{ github.repository }} repository has been cloned to the runner."
      - run: echo "🖥️ The workflow is now ready to test your code on the runner."
      - name: List files in the repository
        run: |
          ls ${{ github.workspace }}
      - run: echo "🍏 This job's status is ${{ job.status }}."

```

#### Observing the Workflow Execution
After pushing the changes, I navigated to the "Actions" tab in my repository. I selected the "GitHub Actions Demo" workflow and observed its execution. The workflow ran successfully, displaying logs for each step, including messages about the event trigger, runner OS, repository details, and job status.

### Workflow Execution Output and Observations
The workflow ran without errors. Key outputs included:
- Confirmation of the push event trigger.
- Details about the runner's operating system (Ubuntu).
- Information about the branch and repository.
- A list of files in the repository.

![](.\images\githubActions.png)
No errors were encountered during the execution.

# Task 2: Gathering System Information and Manual Triggering

## Configuring a Manual Trigger

I extended the existing GitHub Actions workflow by adding a manual trigger yaml file. This allows the workflow to be triggered manually in addition to being triggered by a push event. The updated `on` section of the YAML file is as follows:

`yaml
on:
push:
workflow_dispatch:
`

### Changes Made to the Workflow File
- Added `workflow_dispatch` to the `on` section to enable manual triggering.

## Gathering System Information

To gather system information, I added a file called `system-specs.yml` to the workflow folder

### System Spec Workflow Steps
```
name: GitHub Actions Demo
run-name: ${{ github.actor }} is testing out GitHub Actions 🚀
on: [push]
jobs:
  Explore-GitHub-Actions:
    runs-on: ubuntu-latest
    steps:
      - run: echo "🎉 The job was triggered by a ${{ github.event_name }} event."
      - run: echo "🐧 This job is now running on a ${{ runner.os }} server hosted by GitHub!"
      - run: echo "🔎 The name of your branch is ${{ github.ref }} and your repository is ${{ github.repository }}."
      - name: Check out repository code
        uses: actions/checkout@v4
      - run: echo "💡 The ${{ github.repository }} repository has been cloned to the runner."
      - run: echo "🖥️ The workflow is now ready to test your code on the runner."
      - name: Gather system information
        run: |
          echo "Gathering system information..."
          echo "OS Information:"
          uname -a
          echo "CPU Information:"
          lscpu
          echo "Memory Information:"
          free -h
          echo "Disk Space Information:"
          df -h
      - name: List files in the repository
        run: |
          ls ${{ github.workspace }}
      - run: echo "🍏 This job's status is ${{ job.status }}."
```



### Documentation of Gathered Information

The gathered system information includes:
- **Operating System**: Details provided by the `uname -a` command.
- **Runner OS**: Operating system of the runner 
- **Architecture**: System architecture
- **Memory Information**
- **Disk Space**
- **Number of CPUs**: CPU count of the runner.


![](.\images\systemSpecs.png)

