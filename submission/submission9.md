# Lab 9

## Task 1

1. Set Up a Basic GitHub Action from the [Quick Start Guide](https://docs.github.com/en/actions/quickstart)
    - Create a [YAML file](../.github/workflows/github-actions-demo.yml).
    - Copy the example YAML content from the guide into this file.
    - Push the changes to a new branch.
    - Review the workflow behavior.

2. Observations:
    - We’ve created an action, which appears under the name specified in `run-name`.
      ![alt text](1.png)
    - The example highlights the following features of GitHub Actions:
        - You can define when to run the action using `on: [<event>]`.
        - You can define `jobs:` to specify tasks GitHub will run.
        - Within `jobs:`, the `runs-on:` setting defines the machine environment for the job.
        - Each job includes a series of steps, which are commands executed in order.

## Task 2

1. Set Up a Manual Trigger for the Action
    - Add `workflow_dispatch` as a trigger in the YAML file:
    ```yaml
    on: [push, workflow_dispatch]
    ```
    - Now, the action can also be started manually.

2. Collect System Information
    - Create a new job specifically for gathering system metrics.
    - Result:
      ![alt text](2.png)
