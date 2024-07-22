# Submission for Lab 9

## Task 1

I created a basic python format checker. It does so in 3 steps, first it start an image that has python, then intalls black and finally runs black to do the check. At the start it also uses `actions/checkout@v3` that copies the project files into the runner. Also this checker runs on push, meaning, it'll be triggered whenever a push is made to the repo.

You can see the file at `.github/workflows/format_checking.yml`.

![Workflow run](/Resources/workflow%20run.png)

## Task 2

### Manual trigger

The `workflow_dispatch` was added to the list of trigger events, it allows the workflow to be manually triggered, but the workflow needs to be on the main branch for it to work.

### Show system info

A set of commands for gathering system infor were called and pushed to `system-info.txt`, which at the end is printed to the console. Another possible approach would be to output this file as an artifact of the workflow run.

![Sys info](/Resources/Sys%20info.png)
