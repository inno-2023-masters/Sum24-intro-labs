![alt text](image.png)

![alt text](image-1.png)


## Observations and Key Concepts

In this task, we extended our GitHub Actions workflow to include a manual trigger and gather system information. The key concepts involved were:

- Adding a manual trigger (`workflow_dispatch`) to our existing workflow.
- Gathering system information such as runner details, hardware specifications, memory, and disk usage.

## Steps Followed

1. **Configured a Manual Trigger:**
   - Added `workflow_dispatch` to the `on` section of the workflow file to enable manual triggering.

2. **Gathered System Information:**
   - Included steps in the workflow to gather and document system information such as runner info, hardware specifications, memory, and disk usage.

## Changes Made to Workflow File

The workflow file (`.github/workflows/test.yml`) was modified to include:

- A manual trigger.
- Steps to gather system information.