# TERRA_REPORT 1번
## 설치 terraform init
ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/05-Provisioner_Script$ terraform init

Initializing the backend...

Initializing provider plugins...

The following providers do not have any version constraints in configuration,
so the latest version was installed.

To prevent automatic upgrades to new major versions that may contain breaking
changes, it is recommended to add version = "..." constraints to the
corresponding provider blocks in configuration, with the constraint strings
suggested below.

* provider.aws: version = "~> 2.60"

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.


## terraform plan

ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/05-Provisioner_Script$ terraform plan
Refreshing Terraform state in-memory prior to plan...
The refreshed state will be used to calculate this plan, but will not be
persisted to local or remote state storage.


------------------------------------------------------------------------

An execution plan has been generated and is shown below.
Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # aws_instance.example will be created
  + resource "aws_instance" "example" {
      + ami                          = "ami-00edfb46b107f643c"
      + arn                          = (known after apply)
      + associate_public_ip_address  = (known after apply)
      + availability_zone            = (known after apply)
      + cpu_core_count               = (known after apply)
      + cpu_threads_per_core         = (known after apply)
      + get_password_data            = false
      + host_id                      = (known after apply)
      + id                           = (known after apply)
      + instance_state               = (known after apply)
      + instance_type                = "t2.micro"
      + ipv6_address_count           = (known after apply)
      + ipv6_addresses               = (known after apply)
      + key_name                     = "mykey"
      + network_interface_id         = (known after apply)
      + outpost_arn                  = (known after apply)
      + password_data                = (known after apply)
      + placement_group              = (known after apply)
      + primary_network_interface_id = (known after apply)
      + private_dns                  = (known after apply)
      + private_ip                   = (known after apply)
      + public_dns                   = (known after apply)
      + public_ip                    = (known after apply)
      + security_groups              = (known after apply)
      + source_dest_check            = true
      + subnet_id                    = (known after apply)
      + tenancy                      = (known after apply)
      + volume_tags                  = (known after apply)
      + vpc_security_group_ids       = (known after apply)

      + ebs_block_device {
          + delete_on_termination = (known after apply)
          + device_name           = (known after apply)
          + encrypted             = (known after apply)
          + iops                  = (known after apply)
          + kms_key_id            = (known after apply)
          + snapshot_id           = (known after apply)
          + volume_id             = (known after apply)
          + volume_size           = (known after apply)
          + volume_type           = (known after apply)
        }

      + ephemeral_block_device {
          + device_name  = (known after apply)
          + no_device    = (known after apply)
          + virtual_name = (known after apply)
        }

      + metadata_options {
          + http_endpoint               = (known after apply)
          + http_put_response_hop_limit = (known after apply)
          + http_tokens                 = (known after apply)
        }

      + network_interface {
          + delete_on_termination = (known after apply)
          + device_index          = (known after apply)
          + network_interface_id  = (known after apply)
        }

      + root_block_device {
          + delete_on_termination = (known after apply)
          + device_name           = (known after apply)
          + encrypted             = (known after apply)
          + iops                  = (known after apply)
          + kms_key_id            = (known after apply)
          + volume_id             = (known after apply)
          + volume_size           = (known after apply)
          + volume_type           = (known after apply)
        }
    }

  # aws_key_pair.mykey will be created
  + resource "aws_key_pair" "mykey" {
      + fingerprint = (known after apply)
      + id          = (known after apply)
      + key_name    = "mykey"
      + key_pair_id = (known after apply)
      + public_key  = "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDVb46/FxCPpvDaOfcTht71kwALGdt4r6rQPQXvXy0RYs/1q+CYE+yPi2BRvuDf2eylbChGon8PL3jihs30uMZmEvhX6i+mqvI06MloGlLMrwo6ev8/sX4puR5TAa+F1hy8NTDJjI0Hm/enQIjJD9On2f/8XV9kBZf4Q87aUVL5jLrcWIgIhC1cfEMqH3aD1WALmIu7ueNAh/YiM3+FgmNXPZfGs6iZzoAvsq4y11A79H20S/w9C1TKskIG3ytpASBEE9Ieec25qPvE2Ip71N8Wo/R6I3K0ToWGcnNBi0gs4MW5soN/l9A4K3OF5MFQAre4iLqQl0I2AObjhQNyd33F ubuntu@u1"
    }

Plan: 2 to add, 0 to change, 0 to destroy.

------------------------------------------------------------------------

Note: You didn't specify an "-out" parameter to save this plan, so Terraform
can't guarantee that exactly these actions will be performed if
"terraform apply" is subsequently run.


# Apply terraform apply
ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/05-Provisioner_Script$ terraform apply -auto-approve
aws_key_pair.mykey: Creating...
aws_key_pair.mykey: Creation complete after 1s [id=mykey]
aws_instance.example: Creating...
aws_instance.example: Still creating... [10s elapsed]
aws_instance.example: Still creating... [20s elapsed]
aws_instance.example: Provisioning with 'file'...
aws_instance.example: Still creating... [30s elapsed]
aws_instance.example: Provisioning with 'remote-exec'...
aws_instance.example (remote-exec): Connecting to remote host via SSH...
aws_instance.example (remote-exec):   Host: 13.124.33.52
aws_instance.example (remote-exec):   User: ubuntu
aws_instance.example (remote-exec):   Password: false
aws_instance.example (remote-exec):   Private key: true
aws_instance.example (remote-exec):   Certificate: false
aws_instance.example (remote-exec):   SSH Agent: false
aws_instance.example (remote-exec):   Checking Host Key: false
aws_instance.example (remote-exec): Connected!
aws_instance.example: Still creating... [40s elapsed]
aws_instance.example (remote-exec): 0% [Working]
aws_instance.example (remote-exec): Hit:1 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic InRelease
aws_instance.example (remote-exec): 0% [Connecting to security.ubuntu.com (
aws_instance.example (remote-exec): Get:2 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
aws_instance.example (remote-exec): 0% [Waiting for headers] [Connecting to
aws_instance.example (remote-exec): Get:3 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
aws_instance.example (remote-exec): 0% [3 InRelease 31.6 kB/74.6 kB 42%] [C
aws_instance.example (remote-exec): 0% [Connecting to security.ubuntu.com (
aws_instance.example (remote-exec): 0% [1 InRelease gpgv 242 kB] [Connectin
aws_instance.example (remote-exec): 0% [Connecting to security.ubuntu.com (
aws_instance.example (remote-exec): 0% [2 InRelease gpgv 88.7 kB] [Waiting
aws_instance.example (remote-exec): Get:4 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages [8570 kB]
aws_instance.example (remote-exec): 0% [2 InRelease gpgv 88.7 kB] [4 Packag
aws_instance.example (remote-exec): 0% [2 InRelease gpgv 88.7 kB] [Waiting
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [2 InRelease
aws_instance.example (remote-exec): Get:5 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic/universe Translation-en [4941 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [2 InRelease
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [5 Translatio
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): Get:6 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages [151 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): Get:7 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic/multiverse Translation-en [108 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): Get:8 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [932 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): Get:9 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): Get:10 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/main Translation-en [318 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): Get:11 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/restricted amd64 Packages [50.1 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): Get:12 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/restricted Translation-en [12.6 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): Get:13 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [1068 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): Get:14 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/universe Translation-en [332 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): Get:15 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 Packages [15.5 kB]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): Get:16 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/multiverse Translation-en [6352 B]
aws_instance.example: Still creating... [51s elapsed]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [3 InRelease
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [9 InRelease
aws_instance.example (remote-exec): Get:17 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-backports/main amd64 Packages [7516 B]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [9 InRelease
aws_instance.example (remote-exec): Get:18 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-backports/main Translation-en [4764 B]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [Waiting for
aws_instance.example (remote-exec): Get:19 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 Packages [7484 B]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [Waiting for
aws_instance.example (remote-exec): Get:20 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-backports/universe Translation-en [4436 B]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [9 InRelease
aws_instance.example (remote-exec): 0% [4 Packages store 0 B]
aws_instance.example (remote-exec): 0% [4 Packages store 0 B] [9 InRelease
aws_instance.example (remote-exec): 86% [4 Packages store 0 B]
aws_instance.example (remote-exec): Get:21 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [707 kB]
aws_instance.example (remote-exec): 86% [4 Packages store 0 B] [21 Packages
aws_instance.example (remote-exec): 87% [21 Packages 91.2 kB/707 kB 13%]
aws_instance.example (remote-exec): 87% [5 Translation-en store 0 B] [21 Pa
aws_instance.example (remote-exec): 88% [5 Translation-en store 0 B] [21 Pa
aws_instance.example (remote-exec): 90% [21 Packages 653 kB/707 kB 92%]
aws_instance.example (remote-exec): 90% [6 Packages store 0 B] [21 Packages
aws_instance.example (remote-exec): 90% [21 Packages 701 kB/707 kB 99%]
aws_instance.example (remote-exec): 90% [7 Translation-en store 0 B] [21 Pa
aws_instance.example (remote-exec): 90% [7 Translation-en store 0 B]
aws_instance.example (remote-exec): 90% [Waiting for headers]
aws_instance.example (remote-exec): 90% [8 Packages store 0 B] [Waiting for
aws_instance.example (remote-exec): 90% [Waiting for headers]
aws_instance.example (remote-exec): 90% [10 Translation-en store 0 B] [Wait
aws_instance.example (remote-exec): Get:22 http://security.ubuntu.com/ubuntu bionic-security/main Translation-en [224 kB]
aws_instance.example (remote-exec): 90% [10 Translation-en store 0 B] [22 T
aws_instance.example (remote-exec): 91% [22 Translation-en 145 kB/224 kB 65
aws_instance.example (remote-exec): 91% [11 Packages store 0 B] [22 Transla
aws_instance.example (remote-exec): 92% [22 Translation-en 198 kB/224 kB 88
aws_instance.example (remote-exec): 92% [12 Translation-en store 0 B] [22 T
aws_instance.example (remote-exec): 92% [22 Translation-en 218 kB/224 kB 97
aws_instance.example (remote-exec): 92% [13 Packages store 0 B] [22 Transla
aws_instance.example (remote-exec): 92% [13 Packages store 0 B] [Waiting fo
aws_instance.example (remote-exec): Get:23 http://security.ubuntu.com/ubuntu bionic-security/restricted amd64 Packages [40.3 kB]
aws_instance.example (remote-exec): 92% [13 Packages store 0 B] [23 Package
aws_instance.example (remote-exec): Get:24 http://security.ubuntu.com/ubuntu bionic-security/restricted Translation-en [10.2 kB]
aws_instance.example (remote-exec): 92% [13 Packages store 0 B] [24 Transla
aws_instance.example (remote-exec): Get:25 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [660 kB]
aws_instance.example (remote-exec): 92% [13 Packages store 0 B] [25 Package
aws_instance.example (remote-exec): 95% [25 Packages 621 kB/660 kB 94%]
aws_instance.example (remote-exec): 95% [14 Translation-en store 0 B] [25 P
aws_instance.example (remote-exec): Get:26 http://security.ubuntu.com/ubuntu bionic-security/universe Translation-en [219 kB]
aws_instance.example (remote-exec): 95% [14 Translation-en store 0 B] [26 T
aws_instance.example (remote-exec): Get:27 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 Packages [7392 B]
aws_instance.example (remote-exec): 96% [14 Translation-en store 0 B] [27 P
aws_instance.example (remote-exec): 96% [14 Translation-en store 0 B] [Wait
aws_instance.example (remote-exec): Get:28 http://security.ubuntu.com/ubuntu bionic-security/multiverse Translation-en [2788 B]
aws_instance.example (remote-exec): 96% [14 Translation-en store 0 B] [28 T
aws_instance.example (remote-exec): 96% [14 Translation-en store 0 B]
aws_instance.example (remote-exec): 97% [Working]
aws_instance.example (remote-exec): 97% [15 Packages store 0 B]
aws_instance.example (remote-exec): 97% [Working]
aws_instance.example (remote-exec): 97% [16 Translation-en store 0 B]
aws_instance.example (remote-exec): 97% [Working]
aws_instance.example (remote-exec): 97% [17 Packages store 0 B]
aws_instance.example (remote-exec): 97% [Working]
aws_instance.example (remote-exec): 97% [18 Translation-en store 0 B]
aws_instance.example (remote-exec): 98% [Working]
aws_instance.example (remote-exec): 98% [19 Packages store 0 B]
aws_instance.example (remote-exec): 98% [Working]
aws_instance.example (remote-exec): 98% [20 Translation-en store 0 B]
aws_instance.example (remote-exec): 98% [Working]
aws_instance.example (remote-exec): 98% [21 Packages store 0 B]
aws_instance.example (remote-exec): 98% [Working]
aws_instance.example (remote-exec): 98% [22 Translation-en store 0 B]
aws_instance.example (remote-exec): 99% [Working]
aws_instance.example (remote-exec): 99% [23 Packages store 0 B]
aws_instance.example (remote-exec): 99% [Working]
aws_instance.example (remote-exec): 99% [24 Translation-en store 0 B]
aws_instance.example (remote-exec): 99% [Working]
aws_instance.example (remote-exec): 99% [25 Packages store 0 B]
aws_instance.example (remote-exec): 99% [Working]
aws_instance.example (remote-exec): 99% [26 Translation-en store 0 B]
aws_instance.example (remote-exec): 100% [Working]
aws_instance.example (remote-exec): 100% [27 Packages store 0 B]
aws_instance.example (remote-exec): 100% [Working]
aws_instance.example (remote-exec): 100% [28 Translation-en store 0 B]
aws_instance.example (remote-exec): 100% [Working]
aws_instance.example (remote-exec): Fetched 18.7 MB in 4s (4851 kB/s)
aws_instance.example (remote-exec): Reading package lists... 0%
aws_instance.example (remote-exec): Reading package lists... 0%
aws_instance.example (remote-exec): Reading package lists... 0%
aws_instance.example (remote-exec): Reading package lists... 4%
aws_instance.example (remote-exec): Reading package lists... 4%
aws_instance.example (remote-exec): Reading package lists... 7%
aws_instance.example (remote-exec): Reading package lists... 7%
aws_instance.example (remote-exec): Reading package lists... 7%
aws_instance.example (remote-exec): Reading package lists... 7%
aws_instance.example (remote-exec): Reading package lists... 7%
aws_instance.example (remote-exec): Reading package lists... 7%
aws_instance.example (remote-exec): Reading package lists... 46%
aws_instance.example (remote-exec): Reading package lists... 46%
aws_instance.example (remote-exec): Reading package lists... 66%
aws_instance.example (remote-exec): Reading package lists... 66%
aws_instance.example (remote-exec): Reading package lists... 67%
aws_instance.example (remote-exec): Reading package lists... 67%
aws_instance.example (remote-exec): Reading package lists... 67%
aws_instance.example (remote-exec): Reading package lists... 67%
aws_instance.example (remote-exec): Reading package lists... 72%
aws_instance.example (remote-exec): Reading package lists... 73%
aws_instance.example (remote-exec): Reading package lists... 73%
aws_instance.example (remote-exec): Reading package lists... 76%
aws_instance.example (remote-exec): Reading package lists... 76%
aws_instance.example (remote-exec): Reading package lists... 77%
aws_instance.example (remote-exec): Reading package lists... 77%
aws_instance.example (remote-exec): Reading package lists... 77%
aws_instance.example (remote-exec): Reading package lists... 77%
aws_instance.example (remote-exec): Reading package lists... 83%
aws_instance.example (remote-exec): Reading package lists... 83%
aws_instance.example (remote-exec): Reading package lists... 86%
aws_instance.example (remote-exec): Reading package lists... 86%
aws_instance.example (remote-exec): Reading package lists... 86%
aws_instance.example (remote-exec): Reading package lists... 86%
aws_instance.example (remote-exec): Reading package lists... 86%
aws_instance.example (remote-exec): Reading package lists... 86%
aws_instance.example (remote-exec): Reading package lists... 86%
aws_instance.example (remote-exec): Reading package lists... 86%
aws_instance.example (remote-exec): Reading package lists... 86%
aws_instance.example (remote-exec): Reading package lists... 86%
aws_instance.example (remote-exec): Reading package lists... 86%
aws_instance.example (remote-exec): Reading package lists... 86%
aws_instance.example (remote-exec): Reading package lists... 86%
aws_instance.example (remote-exec): Reading package lists... 86%
aws_instance.example (remote-exec): Reading package lists... 90%
aws_instance.example (remote-exec): Reading package lists... 90%
aws_instance.example (remote-exec): Reading package lists... 93%
aws_instance.example (remote-exec): Reading package lists... 93%
aws_instance.example (remote-exec): Reading package lists... 93%
aws_instance.example (remote-exec): Reading package lists... 93%
aws_instance.example (remote-exec): Reading package lists... 94%
aws_instance.example (remote-exec): Reading package lists... 94%
aws_instance.example (remote-exec): Reading package lists... 97%
aws_instance.example (remote-exec): Reading package lists... 97%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... 99%
aws_instance.example (remote-exec): Reading package lists... Done
aws_instance.example (remote-exec): Reading package lists... 0%
aws_instance.example (remote-exec): Reading package lists... 100%
aws_instance.example (remote-exec): Reading package lists... Done
aws_instance.example (remote-exec): Building dependency tree... 0%
aws_instance.example (remote-exec): Building dependency tree... 0%
aws_instance.example (remote-exec): Building dependency tree... 50%
aws_instance.example (remote-exec): Building dependency tree... 50%
aws_instance.example (remote-exec): Building dependency tree
aws_instance.example (remote-exec): Reading state information... 0%
aws_instance.example (remote-exec): Reading state information... 0%
aws_instance.example (remote-exec): Reading state information... Done
aws_instance.example (remote-exec): The following additional packages will be installed:
aws_instance.example (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example (remote-exec):   libnginx-mod-http-geoip
aws_instance.example (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example (remote-exec):   libnginx-mod-mail
aws_instance.example (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example (remote-exec):   libwebp6 libxpm4 nginx-common
aws_instance.example (remote-exec):   nginx-core
aws_instance.example (remote-exec): Suggested packages:
aws_instance.example (remote-exec):   libgd-tools fcgiwrap nginx-doc
aws_instance.example (remote-exec):   ssl-cert
aws_instance.example (remote-exec): The following NEW packages will be installed:
aws_instance.example (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example (remote-exec):   libnginx-mod-http-geoip
aws_instance.example (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example (remote-exec):   libnginx-mod-mail
aws_instance.example (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example (remote-exec):   libwebp6 libxpm4 nginx nginx-common
aws_instance.example (remote-exec):   nginx-core
aws_instance.example (remote-exec): 0 upgraded, 18 newly installed, 0 to remove and 20 not upgraded.
aws_instance.example (remote-exec): Need to get 2462 kB of archives.
aws_instance.example (remote-exec): After this operation, 8210 kB of additional disk space will be used.
aws_instance.example (remote-exec): 0% [Working]
aws_instance.example (remote-exec): Get:1 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libjpeg-turbo8 amd64 1.5.2-0ubuntu5.18.04.3 [110 kB]
aws_instance.example (remote-exec): 0% [1 libjpeg-turbo8 0 B/110 kB 0%]
aws_instance.example (remote-exec): 5% [Working]
aws_instance.example (remote-exec): Get:2 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic/main amd64 fonts-dejavu-core all 2.37-1 [1041 kB]
aws_instance.example (remote-exec): 5% [2 fonts-dejavu-core 0 B/1041 kB 0%]
aws_instance.example (remote-exec): 40% [Working]
aws_instance.example (remote-exec): Get:3 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic/main amd64 fontconfig-config all 2.12.6-0ubuntu2 [55.8 kB]
aws_instance.example (remote-exec): 40% [3 fontconfig-config 0 B/55.8 kB 0%
aws_instance.example (remote-exec): 43% [Working]
aws_instance.example (remote-exec): Get:4 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic/main amd64 libfontconfig1 amd64 2.12.6-0ubuntu2 [137 kB]
aws_instance.example (remote-exec): 43% [4 libfontconfig1 0 B/137 kB 0%]
aws_instance.example (remote-exec): 48% [Working]
aws_instance.example (remote-exec): Get:5 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic/main amd64 libjpeg8 amd64 8c-2ubuntu8 [2194 B]
aws_instance.example (remote-exec): 48% [5 libjpeg8 0 B/2194 B 0%]
aws_instance.example (remote-exec): 49% [Working]
aws_instance.example (remote-exec): Get:6 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic/main amd64 libjbig0 amd64 2.1-3.1build1 [26.7 kB]
aws_instance.example (remote-exec): 49% [6 libjbig0 0 B/26.7 kB 0%]
aws_instance.example (remote-exec): 51% [Working]
aws_instance.example (remote-exec): Get:7 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libtiff5 amd64 4.0.9-5ubuntu0.3 [153 kB]
aws_instance.example (remote-exec): 51% [7 libtiff5 0 B/153 kB 0%]
aws_instance.example (remote-exec): 57% [Working]
aws_instance.example (remote-exec): Get:8 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic/main amd64 libwebp6 amd64 0.6.1-2 [185 kB]
aws_instance.example (remote-exec): 57% [8 libwebp6 0 B/185 kB 0%]
aws_instance.example (remote-exec): 64% [Working]
aws_instance.example (remote-exec): Get:9 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic/main amd64 libxpm4 amd64 1:3.5.12-1 [34.0 kB]
aws_instance.example (remote-exec): 64% [9 libxpm4 0 B/34.0 kB 0%]
aws_instance.example (remote-exec): 67% [Working]
aws_instance.example (remote-exec): Get:10 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libgd3 amd64 2.2.5-4ubuntu0.4 [119 kB]
aws_instance.example (remote-exec): 67% [10 libgd3 0 B/119 kB 0%]
aws_instance.example (remote-exec): 72% [Working]
aws_instance.example (remote-exec): Get:11 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/main amd64 nginx-common all 1.14.0-0ubuntu1.7 [37.4 kB]
aws_instance.example (remote-exec): 72% [11 nginx-common 0 B/37.4 kB 0%]
aws_instance.example (remote-exec): 74% [Working]
aws_instance.example (remote-exec): Get:12 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libnginx-mod-http-geoip amd64 1.14.0-0ubuntu1.7 [11.2 kB]
aws_instance.example (remote-exec): 74% [12 libnginx-mod-http-geoip 0 B/11.
aws_instance.example (remote-exec): 75% [Working]
aws_instance.example (remote-exec): Get:13 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libnginx-mod-http-image-filter amd64 1.14.0-0ubuntu1.7 [14.6 kB]
aws_instance.example (remote-exec): 75% [13 libnginx-mod-http-image-filter
aws_instance.example (remote-exec): 77% [Working]
aws_instance.example (remote-exec): Get:14 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libnginx-mod-http-xslt-filter amd64 1.14.0-0ubuntu1.7 [13.0 kB]
aws_instance.example (remote-exec): 77% [14 libnginx-mod-http-xslt-filter 0
aws_instance.example (remote-exec): 79% [Working]
aws_instance.example (remote-exec): Get:15 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libnginx-mod-mail amd64 1.14.0-0ubuntu1.7 [41.8 kB]
aws_instance.example (remote-exec): 79% [15 libnginx-mod-mail 0 B/41.8 kB 0
aws_instance.example (remote-exec): 81% [Working]
aws_instance.example (remote-exec): Get:16 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libnginx-mod-stream amd64 1.14.0-0ubuntu1.7 [63.7 kB]
aws_instance.example (remote-exec): 81% [16 libnginx-mod-stream 0 B/63.7 kB
aws_instance.example (remote-exec): 84% [Working]
aws_instance.example (remote-exec): Get:17 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/main amd64 nginx-core amd64 1.14.0-0ubuntu1.7 [413 kB]
aws_instance.example (remote-exec): 84% [17 nginx-core 0 B/413 kB 0%]
aws_instance.example (remote-exec): 99% [Working]
aws_instance.example (remote-exec): Get:18 http://ap-northeast-2.ec2.archive.ubuntu.com/ubuntu bionic-updates/main amd64 nginx all 1.14.0-0ubuntu1.7 [3596 B]
aws_instance.example (remote-exec): 99% [18 nginx 0 B/3596 B 0%]
aws_instance.example (remote-exec): 100% [Working]
aws_instance.example (remote-exec): Fetched 2462 kB in 0s (27.0 MB/s)
aws_instance.example (remote-exec): Preconfiguring packages ...
aws_instance.example (remote-exec): Selecting previously unselected package libjpeg-turbo8:amd64.
aws_instance.example (remote-exec): (Reading database ...
aws_instance.example (remote-exec): (Reading database ... 5%
aws_instance.example (remote-exec): (Reading database ... 10%
aws_instance.example (remote-exec): (Reading database ... 15%
aws_instance.example (remote-exec): (Reading database ... 20%
aws_instance.example (remote-exec): (Reading database ... 25%
aws_instance.example (remote-exec): (Reading database ... 30%
aws_instance.example (remote-exec): (Reading database ... 35%
aws_instance.example (remote-exec): (Reading database ... 40%
aws_instance.example (remote-exec): (Reading database ... 45%
aws_instance.example (remote-exec): (Reading database ... 50%
aws_instance.example (remote-exec): (Reading database ... 55%
aws_instance.example (remote-exec): (Reading database ... 60%
aws_instance.example (remote-exec): (Reading database ... 65%
aws_instance.example (remote-exec): (Reading database ... 70%
aws_instance.example (remote-exec): (Reading database ... 75%
aws_instance.example (remote-exec): (Reading database ... 80%
aws_instance.example (remote-exec): (Reading database ... 85%
aws_instance.example (remote-exec): (Reading database ... 90%
aws_instance.example (remote-exec): (Reading database ... 95%
aws_instance.example (remote-exec): (Reading database ... 100%
aws_instance.example (remote-exec): (Reading database ... 56588 files and directories currently installed.)
aws_instance.example (remote-exec): Preparing to unpack .../00-libjpeg-turbo8_1.5.2-0ubuntu5.18.04.3_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libjpeg-turbo8:amd64 (1.5.2-0ubuntu5.18.04.3) ...
aws_instance.example (remote-exec): Selecting previously unselected package fonts-dejavu-core.
aws_instance.example (remote-exec): Preparing to unpack .../01-fonts-dejavu-core_2.37-1_all.deb ...
aws_instance.example (remote-exec): Unpacking fonts-dejavu-core (2.37-1) ...
aws_instance.example (remote-exec): Selecting previously unselected package fontconfig-config.
aws_instance.example (remote-exec): Preparing to unpack .../02-fontconfig-config_2.12.6-0ubuntu2_all.deb ...
aws_instance.example (remote-exec): Unpacking fontconfig-config (2.12.6-0ubuntu2) ...
aws_instance.example (remote-exec): Selecting previously unselected package libfontconfig1:amd64.
aws_instance.example (remote-exec): Preparing to unpack .../03-libfontconfig1_2.12.6-0ubuntu2_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libfontconfig1:amd64 (2.12.6-0ubuntu2) ...
aws_instance.example (remote-exec): Selecting previously unselected package libjpeg8:amd64.
aws_instance.example (remote-exec): Preparing to unpack .../04-libjpeg8_8c-2ubuntu8_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example (remote-exec): Selecting previously unselected package libjbig0:amd64.
aws_instance.example (remote-exec): Preparing to unpack .../05-libjbig0_2.1-3.1build1_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example (remote-exec): Selecting previously unselected package libtiff5:amd64.
aws_instance.example (remote-exec): Preparing to unpack .../06-libtiff5_4.0.9-5ubuntu0.3_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libtiff5:amd64 (4.0.9-5ubuntu0.3) ...
aws_instance.example (remote-exec): Selecting previously unselected package libwebp6:amd64.
aws_instance.example (remote-exec): Preparing to unpack .../07-libwebp6_0.6.1-2_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libwebp6:amd64 (0.6.1-2) ...
aws_instance.example (remote-exec): Selecting previously unselected package libxpm4:amd64.
aws_instance.example (remote-exec): Preparing to unpack .../08-libxpm4_1%3a3.5.12-1_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example (remote-exec): Selecting previously unselected package libgd3:amd64.
aws_instance.example (remote-exec): Preparing to unpack .../09-libgd3_2.2.5-4ubuntu0.4_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libgd3:amd64 (2.2.5-4ubuntu0.4) ...
aws_instance.example (remote-exec): Selecting previously unselected package nginx-common.
aws_instance.example (remote-exec): Preparing to unpack .../10-nginx-common_1.14.0-0ubuntu1.7_all.deb ...
aws_instance.example (remote-exec): Unpacking nginx-common (1.14.0-0ubuntu1.7) ...
aws_instance.example (remote-exec): Selecting previously unselected package libnginx-mod-http-geoip.
aws_instance.example (remote-exec): Preparing to unpack .../11-libnginx-mod-http-geoip_1.14.0-0ubuntu1.7_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libnginx-mod-http-geoip (1.14.0-0ubuntu1.7) ...
aws_instance.example (remote-exec): Selecting previously unselected package libnginx-mod-http-image-filter.
aws_instance.example (remote-exec): Preparing to unpack .../12-libnginx-mod-http-image-filter_1.14.0-0ubuntu1.7_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libnginx-mod-http-image-filter (1.14.0-0ubuntu1.7) ...
aws_instance.example (remote-exec): Selecting previously unselected package libnginx-mod-http-xslt-filter.
aws_instance.example (remote-exec): Preparing to unpack .../13-libnginx-mod-http-xslt-filter_1.14.0-0ubuntu1.7_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libnginx-mod-http-xslt-filter (1.14.0-0ubuntu1.7) ...
aws_instance.example (remote-exec): Selecting previously unselected package libnginx-mod-mail.
aws_instance.example (remote-exec): Preparing to unpack .../14-libnginx-mod-mail_1.14.0-0ubuntu1.7_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libnginx-mod-mail (1.14.0-0ubuntu1.7) ...
aws_instance.example (remote-exec): Selecting previously unselected package libnginx-mod-stream.
aws_instance.example (remote-exec): Preparing to unpack .../15-libnginx-mod-stream_1.14.0-0ubuntu1.7_amd64.deb ...
aws_instance.example (remote-exec): Unpacking libnginx-mod-stream (1.14.0-0ubuntu1.7) ...
aws_instance.example (remote-exec): Selecting previously unselected package nginx-core.
aws_instance.example (remote-exec): Preparing to unpack .../16-nginx-core_1.14.0-0ubuntu1.7_amd64.deb ...
aws_instance.example (remote-exec): Unpacking nginx-core (1.14.0-0ubuntu1.7) ...
aws_instance.example (remote-exec): Selecting previously unselected package nginx.
aws_instance.example (remote-exec): Preparing to unpack .../17-nginx_1.14.0-0ubuntu1.7_all.deb ...
aws_instance.example (remote-exec): Unpacking nginx (1.14.0-0ubuntu1.7) ...
aws_instance.example (remote-exec): Setting up libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example (remote-exec): Setting up fonts-dejavu-core (2.37-1) ...
aws_instance.example (remote-exec): Setting up nginx-common (1.14.0-0ubuntu1.7) ...
aws_instance.example: Still creating... [1m1s elapsed]
aws_instance.example (remote-exec): Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /lib/systemd/system/nginx.service.
aws_instance.example (remote-exec): Setting up libjpeg-turbo8:amd64 (1.5.2-0ubuntu5.18.04.3) ...
aws_instance.example (remote-exec): Setting up libnginx-mod-mail (1.14.0-0ubuntu1.7) ...
aws_instance.example (remote-exec): Setting up libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example (remote-exec): Setting up libnginx-mod-http-xslt-filter (1.14.0-0ubuntu1.7) ...
aws_instance.example (remote-exec): Setting up libnginx-mod-http-geoip (1.14.0-0ubuntu1.7) ...
aws_instance.example (remote-exec): Setting up libwebp6:amd64 (0.6.1-2) ...
aws_instance.example (remote-exec): Setting up libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example (remote-exec): Setting up fontconfig-config (2.12.6-0ubuntu2) ...
aws_instance.example (remote-exec): Setting up libnginx-mod-stream (1.14.0-0ubuntu1.7) ...
aws_instance.example (remote-exec): Setting up libtiff5:amd64 (4.0.9-5ubuntu0.3) ...
aws_instance.example (remote-exec): Setting up libfontconfig1:amd64 (2.12.6-0ubuntu2) ...
aws_instance.example (remote-exec): Setting up libgd3:amd64 (2.2.5-4ubuntu0.4) ...
aws_instance.example (remote-exec): Setting up libnginx-mod-http-image-filter (1.14.0-0ubuntu1.7) ...
aws_instance.example (remote-exec): Setting up nginx-core (1.14.0-0ubuntu1.7) ...
aws_instance.example (remote-exec): Setting up nginx (1.14.0-0ubuntu1.7) ...
aws_instance.example (remote-exec): Processing triggers for systemd (237-3ubuntu10.39) ...
aws_instance.example (remote-exec): Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
aws_instance.example (remote-exec): Processing triggers for ufw (0.36-0ubuntu0.18.04.1) ...
aws_instance.example (remote-exec): Processing triggers for ureadahead (0.100.0-21) ...
aws_instance.example (remote-exec): Processing triggers for libc-bin (2.27-3ubuntu1) ...
aws_instance.example: Creation complete after 1m6s [id=i-03446810cc801011f]

Apply complete! Resources: 2 added, 0 changed, 0 destroyed.


# Remote login
ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/05-Provisioner_Script$ ssh -i ~/mykey ubuntu@13.124.33.52
Warning: Permanently added '13.124.33.52' (ECDSA) to the list of known hosts.
Welcome to Ubuntu 18.04.4 LTS (GNU/Linux 4.15.0-1065-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Mon May 11 10:36:41 UTC 2020

  System load:  0.03              Processes:           91
  Usage of /:   16.0% of 7.69GB   Users logged in:     0
  Memory usage: 16%               IP address for eth0: 172.31.44.153
  Swap usage:   0%


24 packages can be updated.
16 updates are security updates.


Last login: Mon May 11 10:33:04 2020 from 59.13.4.75



# Destroy terraform destroy
ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/05-Provisioner_Script$ terraform destroy -auto-approve
aws_key_pair.mykey: Refreshing state... [id=mykey]
aws_instance.example: Refreshing state... [id=i-03446810cc801011f]
aws_instance.example: Destroying... [id=i-03446810cc801011f]
aws_instance.example: Still destroying... [id=i-03446810cc801011f, 10s elapsed]
aws_instance.example: Still destroying... [id=i-03446810cc801011f, 21s elapsed]
aws_instance.example: Still destroying... [id=i-03446810cc801011f, 31s elapsed]
aws_instance.example: Destruction complete after 31s
aws_key_pair.mykey: Destroying... [id=mykey]
aws_key_pair.mykey: Destruction complete after 0s

Destroy complete! Resources: 2 destroyed.


# TERRA_REPORT 2번

## 설치 terraform init


## terraform plan



## terraform apply

## Remote login



## terraform destroy
