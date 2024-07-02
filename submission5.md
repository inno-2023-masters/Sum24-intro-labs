# Lab 5 : GitOps & SRE Lab

## Task 1: Key Metrics for SRE and SLAs

1. **Monitor System Resources**:
   - Using `htop` and `isostat` we can see here the three applicaitions/processes that are taking up the most CPU and memory.
    ![alt text](images/one.png)

   - Here we can see that `google chrome` has the most I/O usage.
    ![alt text](images/one-io.png)

   - `iostat` shows my system's storage I/O statistics.
    ![alt text](images/one-iostat.png)
 
2. **Disk Space Management**:
   - The 3 largest /directories in the `/var` directory.

      ![alt text](images/two.png)
    
      ![alt text](images/two-du.png)
    
## Task 2: Terraform Installation and Nginx Deployment
- Solution in `TerraformAndNginx.md`.