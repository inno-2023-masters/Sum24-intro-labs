# Lab 9

## Task 1

I followed the instruction and got the following result:
![alt text](image.png)

### Document for Implementing GitHub Actions Workflow

#### Step 1: Create a Workflow File

1. Navigate to your repository on GitHub.com.
2. If the .github/workflows directory exists:
   - Go to the .github/workflows directory on GitHub.
   - Click on "Add file" and then select "Create new file."
   - Name the file github-actions-demo.yml.
3. If the .github/workflows directory doesn't exist:
   - Go to the main page of your repository on GitHub.
   - Click on "Add file" and then select "Create new file."
   - Name the file .github/workflows/github-actions-demo.yml.
   - This creates the .github and workflows directories along with the github-actions-demo.yml file.

#### Step 2: Add YAML Contents to github-actions-demo.yml

Copy and paste the following YAML contents into the github-actions-demo.yml file:

```yml
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
      - run: echo "🖥 The workflow is now ready to test your code on the runner."
      - name: List files in the repository
        run: |
          ls ${{ github.workspace }}
      - run: echo "🍏 This job's status is ${{ job.status }}."
```

#### Step 3: Commit Changes

1. Click on "Commit changes."
2. In the "Propose changes" dialog, select either to commit to the default branch or create a new branch and start a pull request.
3. Click on "Commit changes" or "Propose changes."

#### Conclusion

By following these steps, I have successfully created a GitHub Actions workflow file in my repository. This workflow will be triggered on a push event and execute the defined steps.

## Task 2

I set up manual triggering:
![alt text](image-1.png)

the modified yml:

```yml
name: GitHub Actions Demo
run-name: ${{ github.actor }} is testing out GitHub Actions 🚀
on:
  workflow_dispatch:
jobs:
  print-tag:
    runs-on: ubuntu-latest
    if:  ${{ inputs.print_tags }} 
    steps:
      - name: Print the input tag to STDOUT
        run: echo  The tags are ${{ inputs.tags }} 
```

### After the modification:

**Manually Trigger the Workflow Instruction**:
   - Go to your GitHub repository where you added the GitHub Actions workflow.
   - Click on the "Actions" tab at the top of the repository.
   - In the left sidebar, you should see your workflow listed under "All workflows."
   - Click on the workflow name to open it.
   - On the top right corner, you should see a "Run workflow" button. Click on it.
   - You will be prompted to enter any input required by your workflow, if applicable.
   - Click the green "Run workflow" button to manually trigger the workflow.