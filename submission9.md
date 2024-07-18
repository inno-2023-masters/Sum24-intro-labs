# Task 1

### yaml configuration of workflow

![](/screens/conf.png)

### Workflow

![](/screens/workflow.png)

### Jobs

![](/screens/jobs.png)

# Task 2

## Manul Triggering

### Before


![](/screens/workflow.png)

### new yaml configuration
```yaml
name: GitHub Actions Manual
run-name: ${{ github.actor }} is testing out GitHub Actions 🚀
on: 
    workflow_dispatch:
jobs:
```

### After
![](/screens/2workflow.png)
![](/screens/6wf.png)

## System information

![](/screens/sysinfo.png)


