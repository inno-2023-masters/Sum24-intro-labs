## Task 2: Terraform Installation and Nginx Deployment

1. **Research and Installation**:
   - Verifying the terraform installation
   ```sh
    suwilanji@SUWILANJI-PCV3:~/learn-terraform-docker-container$ terraform --version
    Terraform v1.9.0-dev
    on linux_amd64
    + provider registry.terraform.io/kreuzwerker/docker v3.0.2
    suwilanji@SUWILANJI-PCV3:~/learn-terraform-docker-container$
   ```

2. **Nginx Deployment**:
   - Step 1 : Build 
   - Initializing terraform
   ```sh
    suwilanji@SUWILANJI-PCV3:~/learn-terraform-docker-container$ terraform init
    Initializing the backend...
    Initializing provider plugins...
    - Reusing previous version of kreuzwerker/docker from the dependency lock file
    - Using previously-installed kreuzwerker/docker v3.0.2

    Terraform has been successfully initialized!

    You may now begin working with Terraform. Try running "terraform plan" to see
    any changes that are required for your infrastructure. All Terraform commands
    should now work.

    If you ever set or change modules or backend configuration for Terraform,
    rerun this command to reinitialize your working directory. If you forget, other
    commands will detect it and remind you to do so if necessary.
    suwilanji@SUWILANJI-PCV3:~/learn-terraform-docker-container$ terraform fmt
    main.tf
    suwilanji@SUWILANJI-PCV3:~/learn-terraform-docker-container$ terraform validate
    Success! The configuration is valid.

    suwilanji@SUWILANJI-PCV3:~/learn-terraform-docker-container$ terraform apply
    docker_image.nginx: Refreshing state... [id=sha256:fffffc90d343cbcb01a5032edac86db5998c536cd0a366514121a45c6723765cnginx:latest]
    docker_container.nginx: Refreshing state... [id=3d9c1651aa62a5407ce90ebc7405e8e52f84b6223f76159ce4d8930cc9baf33d]

    Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
    + create

    Terraform will perform the following actions:

    # docker_container.nginx will be created
    + resource "docker_container" "nginx" {
        + attach                                      = false
        + bridge                                      = (known after apply)
        + command                                     = (known after apply)
        + container_logs                              = (known after apply)
        + container_read_refresh_timeout_milliseconds = 15000
        + entrypoint                                  = (known after apply)
        + env                                         = (known after apply)
        + exit_code                                   = (known after apply)
        + hostname                                    = (known after apply)
        + id                                          = (known after apply)
        + image                                       = "sha256:fffffc90d343cbcb01a5032edac86db5998c536cd0a366514121a45c6723765c"
        + init                                        = (known after apply)
        + ipc_mode                                    = (known after apply)
        + log_driver                                  = (known after apply)
        + logs                                        = false
        + must_run                                    = true
        + name                                        = "tutorial"
        + network_data                                = (known after apply)
        + read_only                                   = false
        + remove_volumes                              = true
        + restart                                     = "no"
        + rm                                          = false
        + runtime                                     = (known after apply)
        + security_opts                               = (known after apply)
        + shm_size                                    = (known after apply)
        + start                                       = true
        + stdin_open                                  = false
        + stop_signal                                 = (known after apply)
        + stop_timeout                                = (known after apply)
        + tty                                         = false
        + wait                                        = false
        + wait_timeout                                = 60

        + healthcheck (known after apply)

        + labels (known after apply)

        + ports {
            + external = 8000
            + internal = 80
            + ip       = "0.0.0.0"
            + protocol = "tcp"
            }
        }

    Plan: 1 to add, 0 to change, 0 to destroy.

    Do you want to perform these actions?
    Terraform will perform the actions described above.
    Only 'yes' will be accepted to approve.

    Enter a value: yes

    docker_container.nginx: Creating...
    docker_container.nginx: Creation complete after 2s [id=92035e0586ba5119b8efce952beac4132029865171337aa75da248bdb82e7d9e]

    Apply complete! Resources: 1 added, 0 changed, 0 destroyed.
    suwilanji@SUWILANJI-PCV3:~/learn-terraform-docker-container$ terraform show
    # docker_container.nginx:
    resource "docker_container" "nginx" {
        attach                                      = false
        bridge                                      = null
        command                                     = [
            "nginx",
            "-g",
            "daemon off;",
        ]
        container_read_refresh_timeout_milliseconds = 15000
        cpu_set                                     = null
        cpu_shares                                  = 0
        domainname                                  = null
        entrypoint                                  = [
            "/docker-entrypoint.sh",
        ]
        env                                         = []
        hostname                                    = "92035e0586ba"
        id                                          = "92035e0586ba5119b8efce952beac4132029865171337aa75da248bdb82e7d9e"
        image                                       = "sha256:fffffc90d343cbcb01a5032edac86db5998c536cd0a366514121a45c6723765c"
        init                                        = false
        ipc_mode                                    = "private"
        log_driver                                  = "json-file"
        logs                                        = false
        max_retry_count                             = 0
        memory                                      = 0
        memory_swap                                 = 0
        must_run                                    = true
        name                                        = "tutorial"
        network_data                                = [
            {
                gateway                   = "172.17.0.1"
                global_ipv6_address       = null
                global_ipv6_prefix_length = 0
                ip_address                = "172.17.0.2"
                ip_prefix_length          = 16
                ipv6_gateway              = null
                mac_address               = "02:42:ac:11:00:02"
                network_name              = "bridge"
            },
        ]
        network_mode                                = "default"
        pid_mode                                    = null
        privileged                                  = false
        publish_all_ports                           = false
        read_only                                   = false
        remove_volumes                              = true
        restart                                     = "no"
        rm                                          = false
        runtime                                     = "runc"
        security_opts                               = []
        shm_size                                    = 64
        start                                       = true
        stdin_open                                  = false
        stop_signal                                 = "SIGQUIT"
        stop_timeout                                = 0
        tty                                         = false
        user                                        = null
        userns_mode                                 = null
        wait                                        = false
        wait_timeout                                = 60
        working_dir                                 = null

        ports {
            external = 8000
            internal = 80
            ip       = "0.0.0.0"
            protocol = "tcp"
        }
    }

    # docker_image.nginx:
    resource "docker_image" "nginx" {
        id           = "sha256:fffffc90d343cbcb01a5032edac86db5998c536cd0a366514121a45c6723765cnginx:latest"
        image_id     = "sha256:fffffc90d343cbcb01a5032edac86db5998c536cd0a366514121a45c6723765c"
        keep_locally = false
        name         = "nginx:latest"
        repo_digest  = "nginx@sha256:b31263533dda53e7d9762dce38da81452ec0a959a1f714859466bc4c5e9cbbae"
    }

   ```
   - Showing that the docker image is running 
   ```sh
    suwilanji@SUWILANJI-PCV3:~/learn-terraform-docker-container$ docker ps
    CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                  NAMES
    3d9c1651aa62   fffffc90d343   "/docker-entrypoint.…"   34 seconds ago   Up 28 seconds   0.0.0.0:8000->80/tcp   tutorial
    suwilanji@SUWILANJI-PCV3:~/learn-terraform-docker-container$ docker stop tutorial
    tutorial
    suwilanji@SUWILANJI-PCV3:~/learn-terraform-docker-container$ docker ps
    CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
   ```
    - Step 2 : Change
    - After updating the port from `8000` to `8080` I used `terraform apply` to apply the changes.
   ```sh
    suwilanji@SUWILANJI-PCV3:~/learn-terraform-docker-container$ terraform apply
    docker_image.nginx: Refreshing state... [id=sha256:fffffc90d343cbcb01a5032edac86db5998c536cd0a366514121a45c6723765cnginx:latest]
    docker_container.nginx: Refreshing state... [id=92035e0586ba5119b8efce952beac4132029865171337aa75da248bdb82e7d9e]

    Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
    -/+ destroy and then create replacement

    Terraform will perform the following actions:

    # docker_container.nginx must be replaced
    -/+ resource "docker_container" "nginx" {
        + bridge                                      = (known after apply)
        ~ command                                     = [
            - "nginx",
            - "-g",
            - "daemon off;",
            ] -> (known after apply)
        + container_logs                              = (known after apply)
        - cpu_shares                                  = 0 -> null
        - dns                                         = [] -> null
        - dns_opts                                    = [] -> null
        - dns_search                                  = [] -> null
        ~ entrypoint                                  = [
            - "/docker-entrypoint.sh",
            ] -> (known after apply)
        ~ env                                         = [] -> (known after apply)
        + exit_code                                   = (known after apply)
        - group_add                                   = [] -> null
        ~ hostname                                    = "92035e0586ba" -> (known after apply)
        ~ id                                          = "92035e0586ba5119b8efce952beac4132029865171337aa75da248bdb82e7d9e" -> (known after apply)
        ~ init                                        = false -> (known after apply)
        ~ ipc_mode                                    = "private" -> (known after apply)
        ~ log_driver                                  = "json-file" -> (known after apply)
        - log_opts                                    = {} -> null
        - max_retry_count                             = 0 -> null
        - memory                                      = 0 -> null
        - memory_swap                                 = 0 -> null
            name                                        = "tutorial"
        ~ network_data                                = [
            - {
                - gateway                   = "172.17.0.1"
                - global_ipv6_prefix_length = 0
                - ip_address                = "172.17.0.2"
                - ip_prefix_length          = 16
                - mac_address               = "02:42:ac:11:00:02"
                - network_name              = "bridge"
                    # (2 unchanged attributes hidden)
                },
            ] -> (known after apply)
        - network_mode                                = "default" -> null
        - privileged                                  = false -> null
        - publish_all_ports                           = false -> null
        ~ runtime                                     = "runc" -> (known after apply)
        ~ security_opts                               = [] -> (known after apply)
        ~ shm_size                                    = 64 -> (known after apply)
        ~ stop_signal                                 = "SIGQUIT" -> (known after apply)
        ~ stop_timeout                                = 0 -> (known after apply)
        - storage_opts                                = {} -> null
        - sysctls                                     = {} -> null
        - tmpfs                                       = {} -> null
            # (20 unchanged attributes hidden)

        ~ healthcheck {
            + attach                                      = (known after apply)
            + bridge                                      = (known after apply)
            + cgroupns_mode                               = (known after apply)
            + command                                     = (known after apply)
            + container_logs                              = (known after apply)
            + container_read_refresh_timeout_milliseconds = (known after apply)
            + cpu_set                                     = (known after apply)
            + cpu_shares                                  = (known after apply)
            + destroy_grace_seconds                       = (known after apply)
            + dns                                         = (known after apply)
            + dns_opts                                    = (known after apply)
            + dns_search                                  = (known after apply)
            + domainname                                  = (known after apply)
            + entrypoint                                  = (known after apply)
            + env                                         = (known after apply)
            + exit_code                                   = (known after apply)
            + gpus                                        = (known after apply)
            + group_add                                   = (known after apply)
            + hostname                                    = (known after apply)
            + id                                          = (known after apply)
            + image                                       = (known after apply)
            + init                                        = (known after apply)
            + ipc_mode                                    = (known after apply)
            + log_driver                                  = (known after apply)
            + log_opts                                    = (known after apply)
            + logs                                        = (known after apply)
            + max_retry_count                             = (known after apply)
            + memory                                      = (known after apply)
            + memory_swap                                 = (known after apply)
            + must_run                                    = (known after apply)
            + name                                        = (known after apply)
            + network_data                                = (known after apply)
            + network_mode                                = (known after apply)
            + pid_mode                                    = (known after apply)
            + privileged                                  = (known after apply)
            + publish_all_ports                           = (known after apply)
            + read_only                                   = (known after apply)
            + remove_volumes                              = (known after apply)
            + restart                                     = (known after apply)
            + rm                                          = (known after apply)
            + runtime                                     = (known after apply)
            + security_opts                               = (known after apply)
            + shm_size                                    = (known after apply)
            + start                                       = (known after apply)
            + stdin_open                                  = (known after apply)
            + stop_signal                                 = (known after apply)
            + stop_timeout                                = (known after apply)
            + storage_opts                                = (known after apply)
            + sysctls                                     = (known after apply)
            + tmpfs                                       = (known after apply)
            + tty                                         = (known after apply)
            + user                                        = (known after apply)
            + userns_mode                                 = (known after apply)
            + wait                                        = (known after apply)
            + wait_timeout                                = (known after apply)
            + working_dir                                 = (known after apply)
            } -> (known after apply)

        ~ labels {
            + attach                                      = (known after apply)
            + bridge                                      = (known after apply)
            + cgroupns_mode                               = (known after apply)
            + command                                     = (known after apply)
            + container_logs                              = (known after apply)
            + container_read_refresh_timeout_milliseconds = (known after apply)
            + cpu_set                                     = (known after apply)
            + cpu_shares                                  = (known after apply)
            + destroy_grace_seconds                       = (known after apply)
            + dns                                         = (known after apply)
            + dns_opts                                    = (known after apply)
            + dns_search                                  = (known after apply)
            + domainname                                  = (known after apply)
            + entrypoint                                  = (known after apply)
            + env                                         = (known after apply)
            + exit_code                                   = (known after apply)
            + gpus                                        = (known after apply)
            + group_add                                   = (known after apply)
            + hostname                                    = (known after apply)
            + id                                          = (known after apply)
            + image                                       = (known after apply)
            + init                                        = (known after apply)
            + ipc_mode                                    = (known after apply)
            + log_driver                                  = (known after apply)
            + log_opts                                    = (known after apply)
            + logs                                        = (known after apply)
            + max_retry_count                             = (known after apply)
            + memory                                      = (known after apply)
            + memory_swap                                 = (known after apply)
            + must_run                                    = (known after apply)
            + name                                        = (known after apply)
            + network_data                                = (known after apply)
            + network_mode                                = (known after apply)
            + pid_mode                                    = (known after apply)
            + privileged                                  = (known after apply)
            + publish_all_ports                           = (known after apply)
            + read_only                                   = (known after apply)
            + remove_volumes                              = (known after apply)
            + restart                                     = (known after apply)
            + rm                                          = (known after apply)
            + runtime                                     = (known after apply)
            + security_opts                               = (known after apply)
            + shm_size                                    = (known after apply)
            + start                                       = (known after apply)
            + stdin_open                                  = (known after apply)
            + stop_signal                                 = (known after apply)
            + stop_timeout                                = (known after apply)
            + storage_opts                                = (known after apply)
            + sysctls                                     = (known after apply)
            + tmpfs                                       = (known after apply)
            + tty                                         = (known after apply)
            + user                                        = (known after apply)
            + userns_mode                                 = (known after apply)
            + wait                                        = (known after apply)
            + wait_timeout                                = (known after apply)
            + working_dir                                 = (known after apply)
            } -> (known after apply)

        ~ ports {
            ~ external = 8000 -> 8080 # forces replacement
                # (3 unchanged attributes hidden)
            }
        }

    Plan: 1 to add, 0 to change, 1 to destroy.

    Do you want to perform these actions?
    Terraform will perform the actions described above.
    Only 'yes' will be accepted to approve.

    Enter a value: yes

    docker_container.nginx: Destroying... [id=92035e0586ba5119b8efce952beac4132029865171337aa75da248bdb82e7d9e]
    docker_container.nginx: Destruction complete after 0s
    docker_container.nginx: Creating...
    docker_container.nginx: Creation complete after 2s [id=6d7121ea7cb11e9533ef330439b9cdd52181d15bcc76cc29b349668de40752c8]

    Apply complete! Resources: 1 added, 0 changed, 1 destroyed.
   
   ```
    - Step 3 : Destroy 
   ```sh
    suwilanji@SUWILANJI-PCV3:~/learn-terraform-docker-container$ terraform destroy
    docker_image.nginx: Refreshing state... [id=sha256:fffffc90d343cbcb01a5032edac86db5998c536cd0a366514121a45c6723765cnginx:latest]
    docker_container.nginx: Refreshing state... [id=6d7121ea7cb11e9533ef330439b9cdd52181d15bcc76cc29b349668de40752c8]

    Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
    - destroy

    Terraform will perform the following actions:

    # docker_container.nginx will be destroyed
    - resource "docker_container" "nginx" {
        - attach                                      = false -> null
        - command                                     = [
            - "nginx",
            - "-g",
            - "daemon off;",
            ] -> null
        - container_read_refresh_timeout_milliseconds = 15000 -> null
        - cpu_shares                                  = 0 -> null
        - dns                                         = [] -> null
        - dns_opts                                    = [] -> null
        - dns_search                                  = [] -> null
        - entrypoint                                  = [
            - "/docker-entrypoint.sh",
            ] -> null
        - env                                         = [] -> null
        - group_add                                   = [] -> null
        - hostname                                    = "6d7121ea7cb1" -> null
        - id                                          = "6d7121ea7cb11e9533ef330439b9cdd52181d15bcc76cc29b349668de40752c8" -> null
        - image                                       = "sha256:fffffc90d343cbcb01a5032edac86db5998c536cd0a366514121a45c6723765c" -> null
        - init                                        = false -> null
        - ipc_mode                                    = "private" -> null
        - log_driver                                  = "json-file" -> null
        - log_opts                                    = {} -> null
        - logs                                        = false -> null
        - max_retry_count                             = 0 -> null
        - memory                                      = 0 -> null
        - memory_swap                                 = 0 -> null
        - must_run                                    = true -> null
        - name                                        = "tutorial" -> null
        - network_data                                = [
            - {
                - gateway                   = "172.17.0.1"
                - global_ipv6_prefix_length = 0
                - ip_address                = "172.17.0.2"
                - ip_prefix_length          = 16
                - mac_address               = "02:42:ac:11:00:02"
                - network_name              = "bridge"
                    # (2 unchanged attributes hidden)
                },
            ] -> null
        - network_mode                                = "default" -> null
        - privileged                                  = false -> null
        - publish_all_ports                           = false -> null
        - read_only                                   = false -> null
        - remove_volumes                              = true -> null
        - restart                                     = "no" -> null
        - rm                                          = false -> null
        - runtime                                     = "runc" -> null
        - security_opts                               = [] -> null
        - shm_size                                    = 64 -> null
        - start                                       = true -> null
        - stdin_open                                  = false -> null
        - stop_signal                                 = "SIGQUIT" -> null
        - stop_timeout                                = 0 -> null
        - storage_opts                                = {} -> null
        - sysctls                                     = {} -> null
        - tmpfs                                       = {} -> null
        - tty                                         = false -> null
        - wait                                        = false -> null
        - wait_timeout                                = 60 -> null
            # (7 unchanged attributes hidden)

        - ports {
            - external = 8080 -> null
            - internal = 80 -> null
            - ip       = "0.0.0.0" -> null
            - protocol = "tcp" -> null
            }
        }

    # docker_image.nginx will be destroyed
    - resource "docker_image" "nginx" {
        - id           = "sha256:fffffc90d343cbcb01a5032edac86db5998c536cd0a366514121a45c6723765cnginx:latest" -> null
        - image_id     = "sha256:fffffc90d343cbcb01a5032edac86db5998c536cd0a366514121a45c6723765c" -> null
        - keep_locally = false -> null
        - name         = "nginx:latest" -> null
        - repo_digest  = "nginx@sha256:b31263533dda53e7d9762dce38da81452ec0a959a1f714859466bc4c5e9cbbae" -> null
        }

    Plan: 0 to add, 0 to change, 2 to destroy.

    Do you really want to destroy all resources?
    Terraform will destroy all your managed infrastructure, as shown above.
    There is no undo. Only 'yes' will be accepted to confirm.

    Enter a value: yes

    docker_container.nginx: Destroying... [id=6d7121ea7cb11e9533ef330439b9cdd52181d15bcc76cc29b349668de40752c8]
    docker_container.nginx: Destruction complete after 1s
    docker_image.nginx: Destroying... [id=sha256:fffffc90d343cbcb01a5032edac86db5998c536cd0a366514121a45c6723765cnginx:latest]
    docker_image.nginx: Destruction complete after 1s

    Destroy complete! Resources: 2 destroyed.
   
   ```
   
 # Define input variables
   - First I create a variables.tf file and define a new variable. Then I update the `docker_container` resource in main.tf to use the new varable.
     ```sh
        variable "container_name" {
        description = "Value of the name for the Docker container"
        type        = string
        default     = "ExampleNginxContainer"
        }
     ```
  - I then apply the config and overide the container name.
    ```sh
    suwilanji@SUWILANJI-PCV3:~/learn-terraform-docker-container$ terraform apply -var "container_name=YetAnotherName"
    docker_image.nginx: Refreshing state... [id=sha256:fffffc90d343cbcb01a5032edac86db5998c536cd0a366514121a45c6723765cnginx:latest]
    docker_container.nginx: Refreshing state... [id=38a75fde8891c541b7daecd51df3a898da258c8357c92dc4d02422564323268f]

    Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
    -/+ destroy and then create replacement

    Terraform will perform the following actions:

    # docker_container.nginx must be replaced
    -/+ resource "docker_container" "nginx" {
        + bridge                                      = (known after apply)
        ~ command                                     = [
            - "nginx",
            - "-g",
            - "daemon off;",
            ] -> (known after apply)
        + container_logs                              = (known after apply)
        - cpu_shares                                  = 0 -> null
        - dn                                       = [] -> null
        - dns_opts                                    = [] -> null
        - dns_search                                  = [] -> null
        ~ entrypoint                                  = [
            - "/docker-entrypoint.sh",
            ] -> (known after apply)
        ~ env                                         = [] -> (known after apply)
        + exit_code                                   = (known after apply)
        - group_add                                   = [] -> null
        ~ hostname                                    = "38a75fde8891" -> (known after apply)
        ~ id                                          = "38a75fde8891c541b7daecd51df3a898da258c8357c92dc4d02422564323268f" -> (known after apply)
        ~ init                                        = false -> (known after apply)
        ~ ipc_mode                                    = "private" -> (known after apply)
        ~ log_driver                                  = "json-file" -> (known after apply)
        - log_opts                                    = {} -> null
        - max_retry_count                             = 0 -> null
        - memory                                      = 0 -> null
        - memory_swap                                 = 0 -> null
        ~ name                                        = "ExampleNginxContainer" -> "YetAnotherName" # forces replacement
        ~ network_data                                = [
            - {
                - gateway                   = "172.17.0.1"
                - global_ipv6_prefix_length = 0
                - ip_address                = "172.17.0.2"
                - ip_prefix_length          = 16
                - mac_address               = "02:42:ac:11:00:02"
                - network_name              = "bridge"
                    # (2 unchanged attributes hidden)
                },
            ] -> (known after apply)
        - network_mode                                = "default" -> null
        - privileged                                  = false -> null
        - publish_all_ports                           = false -> null
        ~ runtime                                     = "runc" -> (known after apply)
        ~ security_opts                               = [] -> (known after apply)
        ~ shm_size                                    = 64 -> (known after apply)
        ~ stop_signal                                 = "SIGQUIT" -> (known after apply)
        ~ stop_timeout                                = 0 -> (known after apply)
        - storage_opts                                = {} -> null
        - sysctls                                     = {} -> null
        - tmpfs                                       = {} -> null
            # (20 unchanged attributes hidden) 
    ```
  - After applying the configaration and overiding the name with the -var tag we can see that the container name has indeed changed to `YetAnotherName`
    ```sh
        suwilanji@SUWILANJI-PCV3:~/learn-terraform-docker-container$ docker ps
        CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                  NAMES
        cf4857aaa210   fffffc90d343   "/docker-entrypoint.…"   59 seconds ago   Up 58 seconds   0.0.0.0:8080->80/tcp   YetAnotherName
    ```