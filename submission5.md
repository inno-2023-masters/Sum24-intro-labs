# GitOps & SRE Lab

## Task 1: Key Metrics for SRE and SLAs

![IOstart](/media/iostat.png)

du -a /var | sort -n -r | head -n 3
->
3201352 /var
2528688 /var/lib
2294788 /var/lib/snapd

df -h /var
->
Filesystem Size Used Avail Use% Mounted on
/dev/nvme0n1p6 146G 14G 124G 10% /

## Task 2: Terraform Installation and Nginx Deployment

Configuration and steps described in `TerraformAndNginx.md` in the `lab5` folder.
