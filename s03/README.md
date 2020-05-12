# TERRA_REPORT 3번
## 순서 terraform init , terraform plan , terraform apply , 원격접속
## Error발생한 부분: 1번 문제를 푼 후에  avality zone을 변경하지 않아서 발생
## 설치 terraform init
uubuntu@u1:/mnt/hgfs/Desktop/terraform-course/05-Provisioner_Script$ terraform init

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

  # aws_instance.example[0] will be created
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

  # aws_instance.example[1] will be created
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

  # aws_instance.example[2] will be created
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

  # aws_instance.example[3] will be created
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

Plan: 5 to add, 0 to change, 0 to destroy.

------------------------------------------------------------------------

Note: You didn't specify an "-out" parameter to save this plan, so Terraform
can't guarantee that exactly these actions will be performed if
"terraform apply" is subsequently run.

## terraform apply
ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/05-Provisioner_Script$ terraform apply -auto-approve
aws_key_pair.mykey: Creating...
aws_vpc.main: Creating...
aws_key_pair.mykey: Creation complete after 3s [id=mykey]
aws_instance.example[2]: Creating...
aws_instance.example[1]: Creating...
aws_instance.example[0]: Creating...
aws_vpc.main: Still creating... [10s elapsed]
aws_instance.example[2]: Still creating... [10s elapsed]
aws_instance.example[1]: Still creating... [10s elapsed]
aws_instance.example[0]: Still creating... [10s elapsed]
aws_vpc.main: Still creating... [20s elapsed]
aws_instance.example[2]: Still creating... [20s elapsed]
aws_instance.example[1]: Still creating... [20s elapsed]
aws_instance.example[0]: Still creating... [20s elapsed]
aws_vpc.main: Creation complete after 25s [id=vpc-0f813c121c81213fa]
aws_internet_gateway.main-gw: Creating...
aws_subnet.main-private-1: Creating...
aws_subnet.main-private-3: Creating...
aws_subnet.main-private-2: Creating...
aws_subnet.main-public-3: Creating...
aws_subnet.main-public-1: Creating...
aws_subnet.main-public-2: Creating...
aws_instance.example[1]: Provisioning with 'file'...
aws_subnet.main-private-3: Creation complete after 7s [id=subnet-0efce09a5022cabbd]
aws_subnet.main-private-2: Creation complete after 7s [id=subnet-0a69646d932713f29]
aws_subnet.main-private-1: Creation complete after 8s [id=subnet-003615c6ad029629b]
aws_instance.example[2]: Still creating... [30s elapsed]
aws_instance.example[1]: Still creating... [30s elapsed]
aws_instance.example[0]: Still creating... [30s elapsed]
aws_subnet.main-public-2: Creation complete after 8s [id=subnet-047d1edf40e291f2b]
aws_subnet.main-public-1: Creation complete after 8s [id=subnet-0f8d099d0a0507410]
aws_subnet.main-public-3: Creation complete after 9s [id=subnet-0e14b68d8a34b975e]
aws_internet_gateway.main-gw: Still creating... [10s elapsed]
aws_internet_gateway.main-gw: Creation complete after 10s [id=igw-0edba9462bace0cbe]
aws_route_table.main-public: Creating...
aws_instance.example[1]: Provisioning with 'remote-exec'...
aws_instance.example[1] (remote-exec): Connecting to remote host via SSH...
aws_instance.example[1] (remote-exec):   Host: 3.250.54.255
aws_instance.example[1] (remote-exec):   User: ubuntu
aws_instance.example[1] (remote-exec):   Password: false
aws_instance.example[1] (remote-exec):   Private key: true
aws_instance.example[1] (remote-exec):   Certificate: false
aws_instance.example[1] (remote-exec):   SSH Agent: false
aws_instance.example[1] (remote-exec):   Checking Host Key: false
aws_instance.example[1] (remote-exec): Connected!
aws_instance.example[0]: Provisioning with 'file'...
aws_instance.example[2]: Still creating... [40s elapsed]
aws_instance.example[0]: Still creating... [40s elapsed]
aws_instance.example[1]: Still creating... [40s elapsed]
aws_route_table.main-public: Creation complete after 9s [id=rtb-0c27dd9bf0939573e]
aws_route_table_association.main-public-3-a: Creating...
aws_route_table_association.main-public-2-a: Creating...
aws_route_table_association.main-public-1-a: Creating...
aws_route_table_association.main-public-3-a: Creation complete after 2s [id=rtbassoc-053a04fc9311e8014]
aws_route_table_association.main-public-2-a: Creation complete after 2s [id=rtbassoc-0cac41fe38bdd05ad]
aws_route_table_association.main-public-1-a: Creation complete after 2s [id=rtbassoc-0b577b4ff1266be2c]
aws_instance.example[2]: Provisioning with 'file'...
aws_instance.example[0]: Provisioning with 'remote-exec'...
aws_instance.example[0] (remote-exec): Connecting to remote host via SSH...
aws_instance.example[0] (remote-exec):   Host: 54.77.43.202
aws_instance.example[0] (remote-exec):   User: ubuntu
aws_instance.example[0] (remote-exec):   Password: false
aws_instance.example[0] (remote-exec):   Private key: true
aws_instance.example[0] (remote-exec):   Certificate: false
aws_instance.example[0] (remote-exec):   SSH Agent: false
aws_instance.example[0] (remote-exec):   Checking Host Key: false
aws_instance.example[2]: Still creating... [50s elapsed]
aws_instance.example[1]: Still creating... [50s elapsed]
aws_instance.example[0]: Still creating... [50s elapsed]
aws_instance.example[2]: Provisioning with 'remote-exec'...
aws_instance.example[2] (remote-exec): Connecting to remote host via SSH...
aws_instance.example[2] (remote-exec):   Host: 3.250.70.112
aws_instance.example[2] (remote-exec):   User: ubuntu
aws_instance.example[2] (remote-exec):   Password: false
aws_instance.example[2] (remote-exec):   Private key: true
aws_instance.example[2] (remote-exec):   Certificate: false
aws_instance.example[2] (remote-exec):   SSH Agent: false
aws_instance.example[2] (remote-exec):   Checking Host Key: false
aws_instance.example[0] (remote-exec): Connected!
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal InRelease [265 kB]
aws_instance.example[1] (remote-exec): 0% [1 InRelease 0 B/265 kB 0%] [Connect
aws_instance.example[1] (remote-exec): 0% [Connecting to security.ubuntu.com (
aws_instance.example[1] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]

aws_instance.example[1] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]
aws_instance.example[1] (remote-exec): 0% [Waiting for headers]
aws_instance.example[1] (remote-exec): Get:4 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]
aws_instance.example[1] (remote-exec): 0% [4 InRelease 2585 B/107 kB 2%]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 Packages [970 kB]
aws_instance.example[1] (remote-exec): 0% [5 Packages 49.8 kB/970 kB 5%]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main Translation-en [506 kB]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en 127 kB/506 kB 25%]
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B] [6 Translatio
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 c-n-f Metadata [29.5 kB]
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B] [7 Commands-a
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 Packages [8628 kB]
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B] [8 Packages 0
aws_instance.example[1] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe Translation-en [5124 kB]
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B] [9 Translatio
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B] [9 Translatio
aws_instance.example[1] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 c-n-f Metadata [265 kB]
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B] [10 Commands-
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages [144 kB]
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B] [11 Packages
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse Translation-en [104 kB]
aws_instance.example[1] (remote-exec): 0% [12 Translation-en 0 B/104 kB 0%]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 c-n-f Metadata [9136 B]
aws_instance.example[1] (remote-exec): 0% [13 Commands-amd64 0 B/9136 B 0%]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [84.4 kB]
aws_instance.example[1] (remote-exec): 0% [14 Packages 0 B/84.4 kB 0%]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main Translation-en [30.2 kB]
aws_instance.example[1] (remote-exec): 0% [15 Translation-en 0 B/30.2 kB 0%]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [1940 B]
aws_instance.example[1] (remote-exec): 0% [16 Commands-amd64 0 B/1940 B 0%]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [4180 B]
aws_instance.example[1] (remote-exec): 0% [17 Packages 0 B/4180 B 0%]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): Get:18 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en [1360 B]
aws_instance.example[1] (remote-exec): 0% [18 Translation-en 0 B/1360 B 0%]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): Get:19 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [27.2 kB]
aws_instance.example[1] (remote-exec): 0% [19 Packages 0 B/27.2 kB 0%]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [Waitin
aws_instance.example[1] (remote-exec): Get:20 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe Translation-en [13.3 kB]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [20 Tra
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Get:21 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [1132 B]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [21 Com
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Get:22 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [22 Com
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): 0% [7 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:23 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/main amd64 c-n-f Metadata [112 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:24 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/restricted amd64 c-n-f Metadata [116 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[1] (remote-exec): Get:25 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages [2792 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[1] (remote-exec): Get:26 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe Translation-en [1280 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[1] (remote-exec): Get:27 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 c-n-f Metadata [188 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[1] (remote-exec): Get:28 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): 92% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:29 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [50.1 kB]
aws_instance.example[1] (remote-exec): 92% [8 Packages store 0 B] [29 Packages
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:30 http://security.ubuntu.com/ubuntu focal-security/main Translation-en [18.5 kB]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B] [30 Translat
aws_instance.example[1] (remote-exec): Get:31 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [1352 B]
aws_instance.example[1] (remote-exec): Get:32 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages [4180 B]
aws_instance.example[1] (remote-exec): Get:33 http://security.ubuntu.com/ubuntu focal-security/restricted Translation-en [1360 B]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B] [33 Translat
aws_instance.example[1] (remote-exec): Get:34 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [7548 B]
aws_instance.example[1] (remote-exec): Get:35 http://security.ubuntu.com/ubuntu focal-security/universe Translation-en [5636 B]
aws_instance.example[1] (remote-exec): Get:36 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [608 B]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B] [Waiting for
aws_instance.example[1] (remote-exec): Get:37 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): Connected!
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): 93% [Working]
aws_instance.example[1] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 93% [Working]
aws_instance.example[1] (remote-exec): 93% [10 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 94% [Working]
aws_instance.example[1] (remote-exec): 94% [11 Packages store 0 B]
aws_instance.example[1] (remote-exec): 94% [Working]
aws_instance.example[1] (remote-exec): 94% [12 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 94% [Working]
aws_instance.example[1] (remote-exec): 94% [13 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 94% [Working]
aws_instance.example[1] (remote-exec): 94% [14 Packages store 0 B]
aws_instance.example[1] (remote-exec): 95% [Working]
aws_instance.example[1] (remote-exec): 95% [15 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 95% [Working]
aws_instance.example[1] (remote-exec): 95% [16 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 95% [Working]
aws_instance.example[1] (remote-exec): 95% [17 Packages store 0 B]
aws_instance.example[1] (remote-exec): 95% [Working]
aws_instance.example[1] (remote-exec): 95% [18 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 95% [Working]
aws_instance.example[1] (remote-exec): 95% [19 Packages store 0 B]
aws_instance.example[1] (remote-exec): 96% [Working]
aws_instance.example[1] (remote-exec): 96% [20 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 96% [Working]
aws_instance.example[1] (remote-exec): 96% [21 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 96% [Working]
aws_instance.example[1] (remote-exec): 96% [22 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 96% [Working]
aws_instance.example[1] (remote-exec): 96% [23 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 97% [Working]
aws_instance.example[1] (remote-exec): 97% [24 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 97% [Working]
aws_instance.example[1] (remote-exec): 97% [25 Packages store 0 B]
aws_instance.example[1] (remote-exec): 97% [Working]
aws_instance.example[1] (remote-exec): 97% [26 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 97% [Working]
aws_instance.example[1] (remote-exec): 97% [27 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 98% [Working]
aws_instance.example[1] (remote-exec): 98% [28 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 98% [Working]
aws_instance.example[1] (remote-exec): 98% [29 Packages store 0 B]
aws_instance.example[1] (remote-exec): 98% [Working]
aws_instance.example[1] (remote-exec): 98% [30 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 98% [Working]
aws_instance.example[1] (remote-exec): 98% [31 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 99% [Working]
aws_instance.example[1] (remote-exec): 99% [32 Packages store 0 B]
aws_instance.example[1] (remote-exec): 99% [Working]
aws_instance.example[1] (remote-exec): 99% [33 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 99% [Working]
aws_instance.example[1] (remote-exec): 99% [34 Packages store 0 B]
aws_instance.example[1] (remote-exec): 99% [Working]
aws_instance.example[1] (remote-exec): 99% [35 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 100% [Working]
aws_instance.example[1] (remote-exec): 100% [36 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 100% [Working]
aws_instance.example[1] (remote-exec): 100% [37 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 100% [Working]
aws_instance.example[1] (remote-exec): Fetched 16.6 MB in 3s (6061 kB/s)
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal InRelease [265 kB]
aws_instance.example[0] (remote-exec): 0% [1 InRelease 0 B/265 kB 0%] [Connect
aws_instance.example[0] (remote-exec): 0% [Connecting to security.ubuntu.com (
aws_instance.example[0] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]

aws_instance.example[0] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]
aws_instance.example[0] (remote-exec): 0% [Connecting to security.ubuntu.com (
aws_instance.example[0] (remote-exec): 0% [Waiting for headers]
aws_instance.example[0] (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 Packages [970 kB]
aws_instance.example[0] (remote-exec): 0% [4 Packages 87.5 kB/970 kB 9%] [Wait
aws_instance.example[0] (remote-exec): 0% [Waiting for headers]
aws_instance.example[0] (remote-exec): Get:5 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]
aws_instance.example[0] (remote-exec): 0% [5 InRelease 2585 B/107 kB 2%]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main Translation-en [506 kB]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [6 Translatio
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [5 InRelease
aws_instance.example[0] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 c-n-f Metadata [29.5 kB]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [7 Commands-a
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [5 InRelease
aws_instance.example[0] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 Packages [8628 kB]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [8 Packages 0
aws_instance.example[0] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe Translation-en [5124 kB]
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [9 Translatio
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [9 Translatio
aws_instance.example[0] (remote-exec): 0% [4 Packages store 0 B] [9 Translatio
aws_instance.example[0] (remote-exec): 0% [9 Translation-en 5124 kB/5124 kB 10
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B] [9 Tran
aws_instance.example[0] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 c-n-f Metadata [265 kB]
aws_instance.example[0] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages [144 kB]
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B] [11 Pac
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse Translation-en [104 kB]
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B] [12 Tra
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 c-n-f Metadata [9136 B]
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B] [13 Com
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [84.4 kB]
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B] [14 Pac
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main Translation-en [30.2 kB]
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B] [15 Tra
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [1940 B]
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B] [16 Com
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [4180 B]
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B] [17 Pac
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:18 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en [1360 B]
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B] [18 Tra
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:19 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [27.2 kB]
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B] [19 Pac
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:20 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe Translation-en [13.3 kB]
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B] [20 Tra
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:21 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [1132 B]
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B] [21 Com
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:22 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B] [22 Com
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): 0% [7 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:23 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/main amd64 c-n-f Metadata [112 B]
aws_instance.example[0] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:24 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/restricted amd64 c-n-f Metadata [116 B]
aws_instance.example[0] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:25 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages [2792 B]
aws_instance.example[0] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:26 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe Translation-en [1280 B]
aws_instance.example[0] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:27 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 c-n-f Metadata [188 B]
aws_instance.example[0] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:28 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[0] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): 92% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:29 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [50.1 kB]
aws_instance.example[0] (remote-exec): 92% [8 Packages store 0 B] [29 Packages
aws_instance.example[0] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:30 http://security.ubuntu.com/ubuntu focal-security/main Translation-en [18.5 kB]
aws_instance.example[0] (remote-exec): 93% [8 Packages store 0 B] [30 Translat
aws_instance.example[0] (remote-exec): Get:31 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [1352 B]
aws_instance.example[0] (remote-exec): 93% [8 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:32 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages [4180 B]
aws_instance.example[0] (remote-exec): 93% [8 Packages store 0 B] [32 Packages
aws_instance.example[0] (remote-exec): Get:33 http://security.ubuntu.com/ubuntu focal-security/restricted Translation-en [1360 B]
aws_instance.example[0] (remote-exec): 93% [8 Packages store 0 B] [33 Translat
aws_instance.example[0] (remote-exec): Get:34 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [7548 B]
aws_instance.example[0] (remote-exec): 93% [8 Packages store 0 B] [34 Packages
aws_instance.example[0] (remote-exec): Get:35 http://security.ubuntu.com/ubuntu focal-security/universe Translation-en [5636 B]
aws_instance.example[0] (remote-exec): 93% [8 Packages store 0 B] [35 Translat
aws_instance.example[0] (remote-exec): Get:36 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [608 B]
aws_instance.example[0] (remote-exec): 93% [8 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:37 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal InRelease [265 kB]
aws_instance.example[0] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): Reading package lists... 0%
aws_instance.example[1] (remote-exec): Reading package lists... 0%
aws_instance.example[1] (remote-exec): Reading package lists... 0%
aws_instance.example[1] (remote-exec): Reading package lists... 6%
aws_instance.example[1] (remote-exec): Reading package lists... 6%
aws_instance.example[1] (remote-exec): Reading package lists... 9%
aws_instance.example[1] (remote-exec): Reading package lists... 9%
aws_instance.example[1] (remote-exec): Reading package lists... 10%
aws_instance.example[1] (remote-exec): Reading package lists... 10%
aws_instance.example[1] (remote-exec): Reading package lists... 10%
aws_instance.example[2] (remote-exec): 0% [1 InRelease 0 B/265 kB 0%] [Connect
aws_instance.example[2] (remote-exec): 0% [Waiting for headers]
aws_instance.example[2] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]

aws_instance.example[2] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]
aws_instance.example[2] (remote-exec): Get:4 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]
aws_instance.example[2] (remote-exec): 0% [3 InRelease 98.3 kB/98.3 kB 100%] [
aws_instance.example[2] (remote-exec): 0% [4 InRelease 2585 B/107 kB 2%]
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 Packages [970 kB]
aws_instance.example[2] (remote-exec): 0% [5 Packages 25.9 kB/970 kB 3%]
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main Translation-en [506 kB]
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [6 Translatio
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 c-n-f Metadata [29.5 kB]
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [7 Commands-a
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 Packages [8628 kB]
aws_instance.example[1] (remote-exec): Reading package lists... 10%
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [8 Packages 0
aws_instance.example[2] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe Translation-en [5124 kB]
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [9 Translatio
aws_instance.example[0] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [9 Translatio
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 c-n-f Metadata [265 kB]
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [10 Commands-
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages [144 kB]
aws_instance.example[1] (remote-exec): Reading package lists... 66%
aws_instance.example[1] (remote-exec): Reading package lists... 66%
aws_instance.example[1] (remote-exec): Reading package lists... 96%
aws_instance.example[1] (remote-exec): Reading package lists... 96%
aws_instance.example[1] (remote-exec): Reading package lists... 97%
aws_instance.example[1] (remote-exec): Reading package lists... 97%
aws_instance.example[1] (remote-exec): Reading package lists... 97%
aws_instance.example[1] (remote-exec): Reading package lists... 97%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [11 Packages
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse Translation-en [104 kB]
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... Done
aws_instance.example[1] (remote-exec): Reading package lists... 0%
aws_instance.example[1] (remote-exec): Reading package lists... 100%
aws_instance.example[1] (remote-exec): Reading package lists... Done

aws_instance.example[2] (remote-exec): 0% [12 Translation-en 0 B/104 kB 0%]
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 c-n-f Metadata [9136 B]
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B] [13 Com
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [84.4 kB]
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B] [14 Pac
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main Translation-en [30.2 kB]
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B] [15 Tra
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [1940 B]
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B] [16 Com
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [4180 B]
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B] [17 Pac
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): Get:18 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en [1360 B]
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B] [18 Tra
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): Get:19 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [27.2 kB]
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B] [19 Pac
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): Get:20 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe Translation-en [13.3 kB]
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B] [20 Tra
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): Get:21 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [1132 B]
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B] [21 Com
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): Get:22 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[0] (remote-exec): 93% [Working]
aws_instance.example[0] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Building dependency tree... 0%
aws_instance.example[1] (remote-exec): Building dependency tree... 0%
aws_instance.example[1] (remote-exec): Building dependency tree... 50%
aws_instance.example[1] (remote-exec): Building dependency tree... 50%
aws_instance.example[1] (remote-exec): Building dependency tree
aws_instance.example[1] (remote-exec): Reading state information... 0%
aws_instance.example[1] (remote-exec): Reading state information... 0%
aws_instance.example[1] (remote-exec): Reading state information... Done
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B] [22 Com
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): 0% [7 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:23 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/main amd64 c-n-f Metadata [112 B]
aws_instance.example[2] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:24 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/restricted amd64 c-n-f Metadata [116 B]
aws_instance.example[2] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:25 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages [2792 B]
aws_instance.example[2] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:26 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe Translation-en [1280 B]
aws_instance.example[2] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:27 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 c-n-f Metadata [188 B]
aws_instance.example[2] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:28 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[2] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): The following additional packages will be installed:
aws_instance.example[1] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[1] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[1] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[1] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[1] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[1] (remote-exec):   libnginx-mod-mail
aws_instance.example[1] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[1] (remote-exec):   libwebp6 libxpm4 nginx-common
aws_instance.example[1] (remote-exec):   nginx-core
aws_instance.example[1] (remote-exec): Suggested packages:
aws_instance.example[1] (remote-exec):   libgd-tools fcgiwrap nginx-doc
aws_instance.example[1] (remote-exec):   ssl-cert
aws_instance.example[1] (remote-exec): The following NEW packages will be installed:
aws_instance.example[1] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[1] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[1] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[1] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[1] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[1] (remote-exec):   libnginx-mod-mail
aws_instance.example[1] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[1] (remote-exec):   libwebp6 libxpm4 nginx nginx-common
aws_instance.example[1] (remote-exec):   nginx-core
aws_instance.example[1] (remote-exec): 0 upgraded, 17 newly installed, 0 to remove and 21 not upgraded.
aws_instance.example[1] (remote-exec): Need to get 2431 kB of archives.
aws_instance.example[1] (remote-exec): After this operation, 7891 kB of additional disk space will be used.
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fonts-dejavu-core all 2.37-1 [1041 kB]
aws_instance.example[1] (remote-exec): 0% [1 fonts-dejavu-core 0 B/1041 kB 0%]
aws_instance.example[1] (remote-exec): 35% [Working]
aws_instance.example[1] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fontconfig-config all 2.13.1-2ubuntu3 [28.8 kB]
aws_instance.example[1] (remote-exec): 35% [2 fontconfig-config 0 B/28.8 kB 0%
aws_instance.example[1] (remote-exec): 38% [Working]
aws_instance.example[1] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libfontconfig1 amd64 2.13.1-2ubuntu3 [114 kB]
aws_instance.example[1] (remote-exec): 38% [3 libfontconfig1 0 B/114 kB 0%]
aws_instance.example[1] (remote-exec): 42% [Working]
aws_instance.example[1] (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg-turbo8 amd64 2.0.3-0ubuntu1 [118 kB]
aws_instance.example[1] (remote-exec): 42% [4 libjpeg-turbo8 0 B/118 kB 0%]
aws_instance.example[1] (remote-exec): 48% [Working]
aws_instance.example[1] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg8 amd64 8c-2ubuntu8 [2194 B]
aws_instance.example[1] (remote-exec): 48% [5 libjpeg8 0 B/2194 B 0%]
aws_instance.example[1] (remote-exec): 49% [Working]
aws_instance.example[1] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjbig0 amd64 2.1-3.1build1 [26.7 kB]
aws_instance.example[1] (remote-exec): 49% [6 libjbig0 0 B/26.7 kB 0%]
aws_instance.example[1] (remote-exec): 51% [Working]
aws_instance.example[1] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libwebp6 amd64 0.6.1-2 [185 kB]
aws_instance.example[1] (remote-exec): 51% [7 libwebp6 0 B/185 kB 0%]
aws_instance.example[1] (remote-exec): 58% [Working]
aws_instance.example[1] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libtiff5 amd64 4.1.0+git191117-2build1 [161 kB]
aws_instance.example[1] (remote-exec): 58% [8 libtiff5 0 B/161 kB 0%]
aws_instance.example[1] (remote-exec): 65% [Working]
aws_instance.example[1] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libxpm4 amd64 1:3.5.12-1 [34.0 kB]
aws_instance.example[1] (remote-exec): 65% [9 libxpm4 0 B/34.0 kB 0%]
aws_instance.example[1] (remote-exec): 67% [Working]
aws_instance.example[1] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libgd3 amd64 2.2.5-5.2ubuntu2 [118 kB]
aws_instance.example[1] (remote-exec): 67% [10 libgd3 0 B/118 kB 0%]
aws_instance.example[1] (remote-exec): 72% [Working]
aws_instance.example[1] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-common all 1.17.10-0ubuntu1 [37.3 kB]
aws_instance.example[1] (remote-exec): 72% [11 nginx-common 0 B/37.3 kB 0%]
aws_instance.example[1] (remote-exec): 74% [Working]
aws_instance.example[1] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-image-filter amd64 1.17.10-0ubuntu1 [14.3 kB]
aws_instance.example[1] (remote-exec): 74% [12 libnginx-mod-http-image-filter
aws_instance.example[1] (remote-exec): 76% [Working]
aws_instance.example[1] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-xslt-filter amd64 1.17.10-0ubuntu1 [12.5 kB]
aws_instance.example[1] (remote-exec): 76% [13 libnginx-mod-http-xslt-filter 0
aws_instance.example[1] (remote-exec): 78% [Working]
aws_instance.example[1] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-mail amd64 1.17.10-0ubuntu1 [42.3 kB]
aws_instance.example[1] (remote-exec): 78% [14 libnginx-mod-mail 0 B/42.3 kB 0
aws_instance.example[1] (remote-exec): 80% [Working]
aws_instance.example[1] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-stream amd64 1.17.10-0ubuntu1 [66.9 kB]
aws_instance.example[1] (remote-exec): 80% [15 libnginx-mod-stream 0 B/66.9 kB
aws_instance.example[1] (remote-exec): 84% [Working]
aws_instance.example[1] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-core amd64 1.17.10-0ubuntu1 [425 kB]
aws_instance.example[1] (remote-exec): 84% [16 nginx-core 0 B/425 kB 0%]
aws_instance.example[1] (remote-exec): 99% [Working]
aws_instance.example[1] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx all 1.17.10-0ubuntu1 [3616 B]
aws_instance.example[1] (remote-exec): 99% [17 nginx 0 B/3616 B 0%]
aws_instance.example[1] (remote-exec): 100% [Working]
aws_instance.example[1] (remote-exec): Fetched 2431 kB in 0s (37.1 MB/s)
aws_instance.example[2] (remote-exec): 92% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:29 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [50.1 kB]
aws_instance.example[2] (remote-exec): 92% [8 Packages store 0 B] [29 Packages
aws_instance.example[2] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:30 http://security.ubuntu.com/ubuntu focal-security/main Translation-en [18.5 kB]
aws_instance.example[2] (remote-exec): 93% [8 Packages store 0 B] [30 Translat
aws_instance.example[2] (remote-exec): Get:31 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [1352 B]
aws_instance.example[2] (remote-exec): Get:32 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages [4180 B]
aws_instance.example[2] (remote-exec): 93% [8 Packages store 0 B] [32 Packages
aws_instance.example[2] (remote-exec): 93% [8 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:33 http://security.ubuntu.com/ubuntu focal-security/restricted Translation-en [1360 B]
aws_instance.example[2] (remote-exec): Get:34 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [7548 B]
aws_instance.example[2] (remote-exec): Get:35 http://security.ubuntu.com/ubuntu focal-security/universe Translation-en [5636 B]
aws_instance.example[2] (remote-exec): Get:36 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [608 B]
aws_instance.example[2] (remote-exec): Get:37 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[2] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Preconfiguring packages ...
aws_instance.example[2]: Still creating... [1m0s elapsed]
aws_instance.example[0]: Still creating... [1m0s elapsed]
aws_instance.example[1]: Still creating... [1m0s elapsed]
aws_instance.example[0] (remote-exec): 93% [Working]
aws_instance.example[0] (remote-exec): 93% [10 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 94% [Working]
aws_instance.example[0] (remote-exec): 94% [11 Packages store 0 B]
aws_instance.example[0] (remote-exec): 94% [Working]
aws_instance.example[0] (remote-exec): 94% [12 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 94% [Working]
aws_instance.example[0] (remote-exec): 94% [13 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 94% [Working]
aws_instance.example[0] (remote-exec): 94% [14 Packages store 0 B]
aws_instance.example[0] (remote-exec): 95% [Working]
aws_instance.example[0] (remote-exec): 95% [15 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 95% [Working]
aws_instance.example[0] (remote-exec): 95% [16 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 95% [Working]
aws_instance.example[0] (remote-exec): 95% [17 Packages store 0 B]
aws_instance.example[0] (remote-exec): 95% [Working]
aws_instance.example[0] (remote-exec): 95% [18 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 95% [Working]
aws_instance.example[0] (remote-exec): 95% [19 Packages store 0 B]
aws_instance.example[0] (remote-exec): 96% [Working]
aws_instance.example[0] (remote-exec): 96% [20 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 96% [Working]
aws_instance.example[0] (remote-exec): 96% [21 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 96% [Working]
aws_instance.example[0] (remote-exec): 96% [22 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 96% [Working]
aws_instance.example[0] (remote-exec): 96% [23 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 97% [Working]
aws_instance.example[0] (remote-exec): 97% [24 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 97% [Working]
aws_instance.example[0] (remote-exec): 97% [25 Packages store 0 B]
aws_instance.example[0] (remote-exec): 97% [Working]
aws_instance.example[0] (remote-exec): 97% [26 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 97% [Working]
aws_instance.example[0] (remote-exec): 97% [27 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 98% [Working]
aws_instance.example[0] (remote-exec): 98% [28 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 98% [Working]
aws_instance.example[0] (remote-exec): 98% [29 Packages store 0 B]
aws_instance.example[0] (remote-exec): 98% [Working]
aws_instance.example[0] (remote-exec): 98% [30 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 98% [Working]
aws_instance.example[0] (remote-exec): 98% [31 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 99% [Working]
aws_instance.example[0] (remote-exec): 99% [32 Packages store 0 B]
aws_instance.example[0] (remote-exec): 99% [Working]
aws_instance.example[0] (remote-exec): 99% [33 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 99% [Working]
aws_instance.example[0] (remote-exec): 99% [34 Packages store 0 B]
aws_instance.example[0] (remote-exec): 99% [Working]
aws_instance.example[0] (remote-exec): 99% [35 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 100% [Working]
aws_instance.example[0] (remote-exec): 100% [36 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 100% [Working]
aws_instance.example[0] (remote-exec): 100% [37 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 100% [Working]
aws_instance.example[0] (remote-exec): Fetched 16.6 MB in 3s (5722 kB/s)
aws_instance.example[1] (remote-exec): Selecting previously unselected package fonts-dejavu-core.
aws_instance.example[2] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): (Reading database ...
aws_instance.example[1] (remote-exec): (Reading database ... 5%
aws_instance.example[1] (remote-exec): (Reading database ... 10%
aws_instance.example[1] (remote-exec): (Reading database ... 15%
aws_instance.example[1] (remote-exec): (Reading database ... 20%
aws_instance.example[1] (remote-exec): (Reading database ... 25%
aws_instance.example[1] (remote-exec): (Reading database ... 30%
aws_instance.example[1] (remote-exec): (Reading database ... 35%
aws_instance.example[1] (remote-exec): (Reading database ... 40%
aws_instance.example[1] (remote-exec): (Reading database ... 45%
aws_instance.example[1] (remote-exec): (Reading database ... 50%
aws_instance.example[1] (remote-exec): (Reading database ... 55%
aws_instance.example[1] (remote-exec): (Reading database ... 60%
aws_instance.example[1] (remote-exec): (Reading database ... 65%
aws_instance.example[1] (remote-exec): (Reading database ... 70%
aws_instance.example[1] (remote-exec): (Reading database ... 75%
aws_instance.example[1] (remote-exec): (Reading database ... 80%
aws_instance.example[1] (remote-exec): (Reading database ... 85%
aws_instance.example[1] (remote-exec): (Reading database ... 90%
aws_instance.example[1] (remote-exec): (Reading database ... 95%
aws_instance.example[1] (remote-exec): (Reading database ... 100%
aws_instance.example[1] (remote-exec): (Reading database ... 59604 files and directories currently installed.)
aws_instance.example[1] (remote-exec): Preparing to unpack .../00-fonts-dejavu-core_2.37-1_all.deb ...
aws_instance.example[1] (remote-exec): Unpacking fonts-dejavu-core (2.37-1) ...
aws_instance.example[2] (remote-exec): 93% [Working]
aws_instance.example[2] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Selecting previously unselected package fontconfig-config.
aws_instance.example[1] (remote-exec): Preparing to unpack .../01-fontconfig-config_2.13.1-2ubuntu3_all.deb ...
aws_instance.example[1] (remote-exec): Unpacking fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libfontconfig1:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../02-libfontconfig1_2.13.1-2ubuntu3_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libjpeg-turbo8:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../03-libjpeg-turbo8_2.0.3-0ubuntu1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libjpeg8:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../04-libjpeg8_8c-2ubuntu8_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libjbig0:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../05-libjbig0_2.1-3.1build1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libwebp6:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../06-libwebp6_0.6.1-2_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libtiff5:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../07-libtiff5_4.1.0+git191117-2build1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libxpm4:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../08-libxpm4_1%3a3.5.12-1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[2] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Selecting previously unselected package libgd3:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../09-libgd3_2.2.5-5.2ubuntu2_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package nginx-common.
aws_instance.example[1] (remote-exec): Preparing to unpack .../10-nginx-common_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[1] (remote-exec): Unpacking nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libnginx-mod-http-image-filter.
aws_instance.example[1] (remote-exec): Preparing to unpack .../11-libnginx-mod-http-image-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): 93% [Working]
aws_instance.example[2] (remote-exec): 93% [10 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 94% [Working]
aws_instance.example[2] (remote-exec): 94% [11 Packages store 0 B]
aws_instance.example[2] (remote-exec): 94% [Working]
aws_instance.example[2] (remote-exec): 94% [12 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 94% [Working]
aws_instance.example[2] (remote-exec): 94% [13 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 94% [Working]
aws_instance.example[2] (remote-exec): 94% [14 Packages store 0 B]
aws_instance.example[2] (remote-exec): 95% [Working]
aws_instance.example[2] (remote-exec): 95% [15 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 95% [Working]
aws_instance.example[2] (remote-exec): 95% [16 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 95% [Working]
aws_instance.example[2] (remote-exec): 95% [17 Packages store 0 B]
aws_instance.example[2] (remote-exec): 95% [Working]
aws_instance.example[2] (remote-exec): 95% [18 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 95% [Working]
aws_instance.example[2] (remote-exec): 95% [19 Packages store 0 B]
aws_instance.example[2] (remote-exec): 96% [Working]
aws_instance.example[2] (remote-exec): 96% [20 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 96% [Working]
aws_instance.example[2] (remote-exec): 96% [21 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 96% [Working]
aws_instance.example[2] (remote-exec): 96% [22 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 96% [Working]
aws_instance.example[2] (remote-exec): 96% [23 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 97% [Working]
aws_instance.example[2] (remote-exec): 97% [24 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 97% [Working]
aws_instance.example[2] (remote-exec): 97% [25 Packages store 0 B]
aws_instance.example[2] (remote-exec): 97% [Working]
aws_instance.example[2] (remote-exec): 97% [26 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 97% [Working]
aws_instance.example[2] (remote-exec): 97% [27 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 98% [Working]
aws_instance.example[2] (remote-exec): 98% [28 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 98% [Working]
aws_instance.example[2] (remote-exec): 98% [29 Packages store 0 B]
aws_instance.example[2] (remote-exec): 98% [Working]
aws_instance.example[2] (remote-exec): 98% [30 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 98% [Working]
aws_instance.example[2] (remote-exec): 98% [31 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 99% [Working]
aws_instance.example[2] (remote-exec): 99% [32 Packages store 0 B]
aws_instance.example[2] (remote-exec): 99% [Working]
aws_instance.example[2] (remote-exec): 99% [33 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 99% [Working]
aws_instance.example[2] (remote-exec): 99% [34 Packages store 0 B]
aws_instance.example[2] (remote-exec): 99% [Working]
aws_instance.example[2] (remote-exec): 99% [35 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 100% [Working]
aws_instance.example[2] (remote-exec): 100% [36 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 100% [Working]
aws_instance.example[2] (remote-exec): 100% [37 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 100% [Working]
aws_instance.example[2] (remote-exec): Fetched 16.6 MB in 3s (5869 kB/s)
aws_instance.example[1] (remote-exec): Selecting previously unselected package libnginx-mod-http-xslt-filter.
aws_instance.example[1] (remote-exec): Preparing to unpack .../12-libnginx-mod-http-xslt-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libnginx-mod-mail.
aws_instance.example[1] (remote-exec): Preparing to unpack .../13-libnginx-mod-mail_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libnginx-mod-stream.
aws_instance.example[1] (remote-exec): Preparing to unpack .../14-libnginx-mod-stream_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package nginx-core.
aws_instance.example[1] (remote-exec): Preparing to unpack .../15-nginx-core_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package nginx.
aws_instance.example[1] (remote-exec): Preparing to unpack .../16-nginx_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[1] (remote-exec): Unpacking nginx (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[1] (remote-exec): Setting up nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /lib/systemd/system/nginx.service.
aws_instance.example[1] (remote-exec): Setting up libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[1] (remote-exec): Setting up libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[1] (remote-exec): Setting up fonts-dejavu-core (2.37-1) ...
aws_instance.example[1] (remote-exec): Setting up libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[1] (remote-exec): Setting up libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[1] (remote-exec): Setting up libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[1] (remote-exec): Setting up libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[1] (remote-exec): Setting up libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[1] (remote-exec): Setting up libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up nginx (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Processing triggers for ufw (0.36-6) ...
aws_instance.example[1] (remote-exec): Processing triggers for systemd (245.4-4ubuntu3) ...
aws_instance.example[1] (remote-exec): Processing triggers for man-db (2.9.1-1) ...
aws_instance.example[0] (remote-exec): Reading package lists... 0%
aws_instance.example[0] (remote-exec): Reading package lists... 0%
aws_instance.example[0] (remote-exec): Reading package lists... 0%
aws_instance.example[0] (remote-exec): Reading package lists... 6%
aws_instance.example[0] (remote-exec): Reading package lists... 6%
aws_instance.example[0] (remote-exec): Reading package lists... 9%
aws_instance.example[0] (remote-exec): Reading package lists... 9%
aws_instance.example[0] (remote-exec): Reading package lists... 10%
aws_instance.example[0] (remote-exec): Reading package lists... 10%
aws_instance.example[0] (remote-exec): Reading package lists... 10%
aws_instance.example[1] (remote-exec): Processing triggers for libc-bin (2.31-0ubuntu9) ...
aws_instance.example[0] (remote-exec): Reading package lists... 10%
aws_instance.example[0] (remote-exec): Reading package lists... 66%
aws_instance.example[0] (remote-exec): Reading package lists... 66%
aws_instance.example[0] (remote-exec): Reading package lists... 96%
aws_instance.example[0] (remote-exec): Reading package lists... 96%
aws_instance.example[0] (remote-exec): Reading package lists... 97%
aws_instance.example[0] (remote-exec): Reading package lists... 97%
aws_instance.example[0] (remote-exec): Reading package lists... 97%
aws_instance.example[0] (remote-exec): Reading package lists... 97%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... 99%
aws_instance.example[0] (remote-exec): Reading package lists... Done
aws_instance.example[0] (remote-exec): Reading package lists... 0%
aws_instance.example[0] (remote-exec): Reading package lists... 100%
aws_instance.example[0] (remote-exec): Reading package lists... Done
aws_instance.example[0] (remote-exec): Building dependency tree... 0%
aws_instance.example[0] (remote-exec): Building dependency tree... 0%
aws_instance.example[0] (remote-exec): Building dependency tree... 50%
aws_instance.example[0] (remote-exec): Building dependency tree... 50%
aws_instance.example[0] (remote-exec): Building dependency tree
aws_instance.example[0] (remote-exec): Reading state information... 0%
aws_instance.example[0] (remote-exec): Reading state information... 0%
aws_instance.example[0] (remote-exec): Reading state information... Done
aws_instance.example[0] (remote-exec): The following additional packages will be installed:
aws_instance.example[0] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[0] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[0] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[0] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[0] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[0] (remote-exec):   libnginx-mod-mail
aws_instance.example[0] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[0] (remote-exec):   libwebp6 libxpm4 nginx-common
aws_instance.example[0] (remote-exec):   nginx-core
aws_instance.example[0] (remote-exec): Suggested packages:
aws_instance.example[0] (remote-exec):   libgd-tools fcgiwrap nginx-doc
aws_instance.example[0] (remote-exec):   ssl-cert
aws_instance.example[0] (remote-exec): The following NEW packages will be installed:
aws_instance.example[0] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[0] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[0] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[0] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[0] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[0] (remote-exec):   libnginx-mod-mail
aws_instance.example[0] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[0] (remote-exec):   libwebp6 libxpm4 nginx nginx-common
aws_instance.example[0] (remote-exec):   nginx-core
aws_instance.example[0] (remote-exec): 0 upgraded, 17 newly installed, 0 to remove and 21 not upgraded.
aws_instance.example[0] (remote-exec): Need to get 2431 kB of archives.
aws_instance.example[0] (remote-exec): After this operation, 7891 kB of additional disk space will be used.
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fonts-dejavu-core all 2.37-1 [1041 kB]
aws_instance.example[0] (remote-exec): 0% [1 fonts-dejavu-core 0 B/1041 kB 0%]
aws_instance.example[0] (remote-exec): 35% [Working]
aws_instance.example[0] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fontconfig-config all 2.13.1-2ubuntu3 [28.8 kB]
aws_instance.example[0] (remote-exec): 35% [2 fontconfig-config 0 B/28.8 kB 0%
aws_instance.example[0] (remote-exec): 38% [Working]
aws_instance.example[0] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libfontconfig1 amd64 2.13.1-2ubuntu3 [114 kB]
aws_instance.example[0] (remote-exec): 38% [3 libfontconfig1 0 B/114 kB 0%]
aws_instance.example[0] (remote-exec): 42% [Working]
aws_instance.example[0] (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg-turbo8 amd64 2.0.3-0ubuntu1 [118 kB]
aws_instance.example[0] (remote-exec): 42% [4 libjpeg-turbo8 0 B/118 kB 0%]
aws_instance.example[0] (remote-exec): 48% [Working]
aws_instance.example[0] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg8 amd64 8c-2ubuntu8 [2194 B]
aws_instance.example[0] (remote-exec): 48% [5 libjpeg8 0 B/2194 B 0%]
aws_instance.example[0] (remote-exec): 49% [Working]
aws_instance.example[0] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjbig0 amd64 2.1-3.1build1 [26.7 kB]
aws_instance.example[0] (remote-exec): 49% [6 libjbig0 0 B/26.7 kB 0%]
aws_instance.example[0] (remote-exec): 51% [Working]
aws_instance.example[0] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libwebp6 amd64 0.6.1-2 [185 kB]
aws_instance.example[0] (remote-exec): 51% [7 libwebp6 0 B/185 kB 0%]
aws_instance.example[0] (remote-exec): 58% [Working]
aws_instance.example[0] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libtiff5 amd64 4.1.0+git191117-2build1 [161 kB]
aws_instance.example[0] (remote-exec): 58% [8 libtiff5 0 B/161 kB 0%]
aws_instance.example[0] (remote-exec): 65% [Working]
aws_instance.example[0] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libxpm4 amd64 1:3.5.12-1 [34.0 kB]
aws_instance.example[0] (remote-exec): 65% [9 libxpm4 0 B/34.0 kB 0%]
aws_instance.example[0] (remote-exec): 67% [Working]
aws_instance.example[0] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libgd3 amd64 2.2.5-5.2ubuntu2 [118 kB]
aws_instance.example[0] (remote-exec): 67% [10 libgd3 0 B/118 kB 0%]
aws_instance.example[0] (remote-exec): 72% [Working]
aws_instance.example[0] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-common all 1.17.10-0ubuntu1 [37.3 kB]
aws_instance.example[0] (remote-exec): 72% [11 nginx-common 0 B/37.3 kB 0%]
aws_instance.example[0] (remote-exec): 74% [Working]
aws_instance.example[0] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-image-filter amd64 1.17.10-0ubuntu1 [14.3 kB]
aws_instance.example[0] (remote-exec): 74% [12 libnginx-mod-http-image-filter
aws_instance.example[0] (remote-exec): 76% [Working]
aws_instance.example[0] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-xslt-filter amd64 1.17.10-0ubuntu1 [12.5 kB]
aws_instance.example[0] (remote-exec): 76% [13 libnginx-mod-http-xslt-filter 0
aws_instance.example[0] (remote-exec): 78% [Working]
aws_instance.example[0] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-mail amd64 1.17.10-0ubuntu1 [42.3 kB]
aws_instance.example[0] (remote-exec): 78% [14 libnginx-mod-mail 0 B/42.3 kB 0
aws_instance.example[0] (remote-exec): 80% [Working]
aws_instance.example[0] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-stream amd64 1.17.10-0ubuntu1 [66.9 kB]
aws_instance.example[0] (remote-exec): 80% [15 libnginx-mod-stream 0 B/66.9 kB
aws_instance.example[0] (remote-exec): 84% [Working]
aws_instance.example[0] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-core amd64 1.17.10-0ubuntu1 [425 kB]
aws_instance.example[0] (remote-exec): 84% [16 nginx-core 0 B/425 kB 0%]
aws_instance.example[0] (remote-exec): 99% [Working]
aws_instance.example[0] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx all 1.17.10-0ubuntu1 [3616 B]
aws_instance.example[0] (remote-exec): 99% [17 nginx 0 B/3616 B 0%]
aws_instance.example[0] (remote-exec): 100% [Working]
aws_instance.example[0] (remote-exec): Fetched 2431 kB in 0s (39.9 MB/s)
aws_instance.example[2] (remote-exec): Reading package lists... 0%
aws_instance.example[2] (remote-exec): Reading package lists... 0%
aws_instance.example[2] (remote-exec): Reading package lists... 0%
aws_instance.example[2] (remote-exec): Reading package lists... 6%
aws_instance.example[2] (remote-exec): Reading package lists... 6%
aws_instance.example[2] (remote-exec): Reading package lists... 9%
aws_instance.example[2] (remote-exec): Reading package lists... 9%
aws_instance.example[2] (remote-exec): Reading package lists... 10%
aws_instance.example[2] (remote-exec): Reading package lists... 10%
aws_instance.example[2] (remote-exec): Reading package lists... 10%
aws_instance.example[0] (remote-exec): Preconfiguring packages ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package fonts-dejavu-core.
aws_instance.example[2] (remote-exec): Reading package lists... 10%
aws_instance.example[0] (remote-exec): (Reading database ...
aws_instance.example[0] (remote-exec): (Reading database ... 5%
aws_instance.example[0] (remote-exec): (Reading database ... 10%
aws_instance.example[0] (remote-exec): (Reading database ... 15%
aws_instance.example[0] (remote-exec): (Reading database ... 20%
aws_instance.example[0] (remote-exec): (Reading database ... 25%
aws_instance.example[0] (remote-exec): (Reading database ... 30%
aws_instance.example[0] (remote-exec): (Reading database ... 35%
aws_instance.example[0] (remote-exec): (Reading database ... 40%
aws_instance.example[0] (remote-exec): (Reading database ... 45%
aws_instance.example[0] (remote-exec): (Reading database ... 50%
aws_instance.example[0] (remote-exec): (Reading database ... 55%
aws_instance.example[0] (remote-exec): (Reading database ... 60%
aws_instance.example[0] (remote-exec): (Reading database ... 65%
aws_instance.example[0] (remote-exec): (Reading database ... 70%
aws_instance.example[0] (remote-exec): (Reading database ... 75%
aws_instance.example[0] (remote-exec): (Reading database ... 80%
aws_instance.example[0] (remote-exec): (Reading database ... 85%
aws_instance.example[0] (remote-exec): (Reading database ... 90%
aws_instance.example[0] (remote-exec): (Reading database ... 95%
aws_instance.example[0] (remote-exec): (Reading database ... 100%
aws_instance.example[0] (remote-exec): (Reading database ... 59604 files and directories currently installed.)
aws_instance.example[0] (remote-exec): Preparing to unpack .../00-fonts-dejavu-core_2.37-1_all.deb ...
aws_instance.example[0] (remote-exec): Unpacking fonts-dejavu-core (2.37-1) ...
aws_instance.example[2] (remote-exec): Reading package lists... 66%
aws_instance.example[2] (remote-exec): Reading package lists... 66%
aws_instance.example[2] (remote-exec): Reading package lists... 96%
aws_instance.example[2] (remote-exec): Reading package lists... 96%
aws_instance.example[2] (remote-exec): Reading package lists... 97%
aws_instance.example[2] (remote-exec): Reading package lists... 97%
aws_instance.example[2] (remote-exec): Reading package lists... 97%
aws_instance.example[2] (remote-exec): Reading package lists... 97%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[0] (remote-exec): Selecting previously unselected package fontconfig-config.
aws_instance.example[0] (remote-exec): Preparing to unpack .../01-fontconfig-config_2.13.1-2ubuntu3_all.deb ...
aws_instance.example[0] (remote-exec): Unpacking fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 98%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... 99%
aws_instance.example[2] (remote-exec): Reading package lists... Done
aws_instance.example[2] (remote-exec): Reading package lists... 0%
aws_instance.example[2] (remote-exec): Reading package lists... 100%
aws_instance.example[2] (remote-exec): Reading package lists... Done
aws_instance.example[0] (remote-exec): Selecting previously unselected package libfontconfig1:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../02-libfontconfig1_2.13.1-2ubuntu3_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libjpeg-turbo8:amd64.
aws_instance.example[2] (remote-exec): Building dependency tree... 0%
aws_instance.example[2] (remote-exec): Building dependency tree... 0%
aws_instance.example[2] (remote-exec): Building dependency tree... 50%
aws_instance.example[2] (remote-exec): Building dependency tree... 50%
aws_instance.example[0] (remote-exec): Preparing to unpack .../03-libjpeg-turbo8_2.0.3-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Building dependency tree
aws_instance.example[2] (remote-exec): Reading state information... 0%
aws_instance.example[2] (remote-exec): Reading state information... 0%
aws_instance.example[2] (remote-exec): Reading state information... Done
aws_instance.example[0] (remote-exec): Selecting previously unselected package libjpeg8:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../04-libjpeg8_8c-2ubuntu8_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libjbig0:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../05-libjbig0_2.1-3.1build1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libwebp6:amd64.
aws_instance.example[2] (remote-exec): The following additional packages will be installed:
aws_instance.example[2] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[2] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[2] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[2] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[2] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[2] (remote-exec):   libnginx-mod-mail
aws_instance.example[2] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[2] (remote-exec):   libwebp6 libxpm4 nginx-common
aws_instance.example[2] (remote-exec):   nginx-core
aws_instance.example[2] (remote-exec): Suggested packages:
aws_instance.example[2] (remote-exec):   libgd-tools fcgiwrap nginx-doc
aws_instance.example[2] (remote-exec):   ssl-cert
aws_instance.example[0] (remote-exec): Preparing to unpack .../06-libwebp6_0.6.1-2_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[2] (remote-exec): The following NEW packages will be installed:
aws_instance.example[2] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[2] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[2] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[2] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[2] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[2] (remote-exec):   libnginx-mod-mail
aws_instance.example[2] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[2] (remote-exec):   libwebp6 libxpm4 nginx nginx-common
aws_instance.example[0] (remote-exec): Selecting previously unselected package libtiff5:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../07-libtiff5_4.1.0+git191117-2build1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libxpm4:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../08-libxpm4_1%3a3.5.12-1_amd64.deb ...
aws_instance.example[2] (remote-exec):   nginx-core
aws_instance.example[2] (remote-exec): 0 upgraded, 17 newly installed, 0 to remove and 21 not upgraded.
aws_instance.example[2] (remote-exec): Need to get 2431 kB of archives.
aws_instance.example[2] (remote-exec): After this operation, 7891 kB of additional disk space will be used.
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fonts-dejavu-core all 2.37-1 [1041 kB]
aws_instance.example[2] (remote-exec): 0% [1 fonts-dejavu-core 0 B/1041 kB 0%]
aws_instance.example[2] (remote-exec): 35% [Working]
aws_instance.example[2] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fontconfig-config all 2.13.1-2ubuntu3 [28.8 kB]
aws_instance.example[0] (remote-exec): Unpacking libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[2] (remote-exec): 35% [2 fontconfig-config 0 B/28.8 kB 0%
aws_instance.example[2] (remote-exec): 38% [Working]
aws_instance.example[2] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libfontconfig1 amd64 2.13.1-2ubuntu3 [114 kB]
aws_instance.example[2] (remote-exec): 38% [3 libfontconfig1 0 B/114 kB 0%]
aws_instance.example[2] (remote-exec): 42% [Working]
aws_instance.example[2] (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg-turbo8 amd64 2.0.3-0ubuntu1 [118 kB]
aws_instance.example[2] (remote-exec): 42% [4 libjpeg-turbo8 0 B/118 kB 0%]
aws_instance.example[2] (remote-exec): 48% [Working]
aws_instance.example[2] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg8 amd64 8c-2ubuntu8 [2194 B]
aws_instance.example[2] (remote-exec): 48% [5 libjpeg8 0 B/2194 B 0%]
aws_instance.example[2] (remote-exec): 49% [Working]
aws_instance.example[2] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjbig0 amd64 2.1-3.1build1 [26.7 kB]
aws_instance.example[2] (remote-exec): 49% [6 libjbig0 0 B/26.7 kB 0%]
aws_instance.example[2] (remote-exec): 51% [Working]
aws_instance.example[2] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libwebp6 amd64 0.6.1-2 [185 kB]
aws_instance.example[2] (remote-exec): 51% [7 libwebp6 0 B/185 kB 0%]
aws_instance.example[2] (remote-exec): 58% [Working]
aws_instance.example[2] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libtiff5 amd64 4.1.0+git191117-2build1 [161 kB]
aws_instance.example[2] (remote-exec): 58% [8 libtiff5 0 B/161 kB 0%]
aws_instance.example[2] (remote-exec): 65% [Working]
aws_instance.example[2] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libxpm4 amd64 1:3.5.12-1 [34.0 kB]
aws_instance.example[2] (remote-exec): 65% [9 libxpm4 0 B/34.0 kB 0%]
aws_instance.example[2] (remote-exec): 67% [Working]
aws_instance.example[2] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libgd3 amd64 2.2.5-5.2ubuntu2 [118 kB]
aws_instance.example[2] (remote-exec): 67% [10 libgd3 0 B/118 kB 0%]
aws_instance.example[2] (remote-exec): 72% [Working]
aws_instance.example[2] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-common all 1.17.10-0ubuntu1 [37.3 kB]
aws_instance.example[2] (remote-exec): 72% [11 nginx-common 0 B/37.3 kB 0%]
aws_instance.example[2] (remote-exec): 74% [Working]
aws_instance.example[2] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-image-filter amd64 1.17.10-0ubuntu1 [14.3 kB]
aws_instance.example[2] (remote-exec): 74% [12 libnginx-mod-http-image-filter
aws_instance.example[2] (remote-exec): 76% [Working]
aws_instance.example[2] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-xslt-filter amd64 1.17.10-0ubuntu1 [12.5 kB]
aws_instance.example[2] (remote-exec): 76% [13 libnginx-mod-http-xslt-filter 0
aws_instance.example[2] (remote-exec): 78% [Working]
aws_instance.example[2] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-mail amd64 1.17.10-0ubuntu1 [42.3 kB]
aws_instance.example[2] (remote-exec): 78% [14 libnginx-mod-mail 0 B/42.3 kB 0
aws_instance.example[2] (remote-exec): 80% [Working]
aws_instance.example[2] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-stream amd64 1.17.10-0ubuntu1 [66.9 kB]
aws_instance.example[2] (remote-exec): 80% [15 libnginx-mod-stream 0 B/66.9 kB
aws_instance.example[2] (remote-exec): 84% [Working]
aws_instance.example[2] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-core amd64 1.17.10-0ubuntu1 [425 kB]
aws_instance.example[2] (remote-exec): 84% [16 nginx-core 0 B/425 kB 0%]
aws_instance.example[2] (remote-exec): 99% [Working]
aws_instance.example[2] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx all 1.17.10-0ubuntu1 [3616 B]
aws_instance.example[2] (remote-exec): 99% [17 nginx 0 B/3616 B 0%]
aws_instance.example[2] (remote-exec): 100% [Working]
aws_instance.example[2] (remote-exec): Fetched 2431 kB in 0s (29.2 MB/s)
aws_instance.example[0] (remote-exec): Selecting previously unselected package libgd3:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../09-libgd3_2.2.5-5.2ubuntu2_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package nginx-common.
aws_instance.example[0] (remote-exec): Preparing to unpack .../10-nginx-common_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[0] (remote-exec): Unpacking nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libnginx-mod-http-image-filter.
aws_instance.example[0] (remote-exec): Preparing to unpack .../11-libnginx-mod-http-image-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Preconfiguring packages ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libnginx-mod-http-xslt-filter.
aws_instance.example[0] (remote-exec): Preparing to unpack .../12-libnginx-mod-http-xslt-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libnginx-mod-mail.
aws_instance.example[0] (remote-exec): Preparing to unpack .../13-libnginx-mod-mail_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package fonts-dejavu-core.
aws_instance.example[0] (remote-exec): Selecting previously unselected package libnginx-mod-stream.
aws_instance.example[0] (remote-exec): Preparing to unpack .../14-libnginx-mod-stream_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package nginx-core.
aws_instance.example[0] (remote-exec): Preparing to unpack .../15-nginx-core_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package nginx.
aws_instance.example[0] (remote-exec): Preparing to unpack .../16-nginx_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[0] (remote-exec): Unpacking nginx (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[2] (remote-exec): (Reading database ...
aws_instance.example[2] (remote-exec): (Reading database ... 5%
aws_instance.example[2] (remote-exec): (Reading database ... 10%
aws_instance.example[2] (remote-exec): (Reading database ... 15%
aws_instance.example[2] (remote-exec): (Reading database ... 20%
aws_instance.example[2] (remote-exec): (Reading database ... 25%
aws_instance.example[2] (remote-exec): (Reading database ... 30%
aws_instance.example[2] (remote-exec): (Reading database ... 35%
aws_instance.example[2] (remote-exec): (Reading database ... 40%
aws_instance.example[2] (remote-exec): (Reading database ... 45%
aws_instance.example[2] (remote-exec): (Reading database ... 50%
aws_instance.example[2] (remote-exec): (Reading database ... 55%
aws_instance.example[2] (remote-exec): (Reading database ... 60%
aws_instance.example[2] (remote-exec): (Reading database ... 65%
aws_instance.example[2] (remote-exec): (Reading database ... 70%
aws_instance.example[2] (remote-exec): (Reading database ... 75%
aws_instance.example[2] (remote-exec): (Reading database ... 80%
aws_instance.example[2] (remote-exec): (Reading database ... 85%
aws_instance.example[2] (remote-exec): (Reading database ... 90%
aws_instance.example[2] (remote-exec): (Reading database ... 95%
aws_instance.example[2] (remote-exec): (Reading database ... 100%
aws_instance.example[2] (remote-exec): (Reading database ... 59604 files and directories currently installed.)
aws_instance.example[0] (remote-exec): Setting up nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Preparing to unpack .../00-fonts-dejavu-core_2.37-1_all.deb ...
aws_instance.example[2] (remote-exec): Unpacking fonts-dejavu-core (2.37-1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package fontconfig-config.
aws_instance.example[2] (remote-exec): Preparing to unpack .../01-fontconfig-config_2.13.1-2ubuntu3_all.deb ...
aws_instance.example[2] (remote-exec): Unpacking fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libfontconfig1:amd64.
aws_instance.example[2] (remote-exec): Preparing to unpack .../02-libfontconfig1_2.13.1-2ubuntu3_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libjpeg-turbo8:amd64.
aws_instance.example[2] (remote-exec): Preparing to unpack .../03-libjpeg-turbo8_2.0.3-0ubuntu1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libjpeg8:amd64.
aws_instance.example[2] (remote-exec): Preparing to unpack .../04-libjpeg8_8c-2ubuntu8_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[0] (remote-exec): Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /lib/systemd/system/nginx.service.
aws_instance.example[2] (remote-exec): Selecting previously unselected package libjbig0:amd64.
aws_instance.example[2] (remote-exec): Preparing to unpack .../05-libjbig0_2.1-3.1build1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libwebp6:amd64.
aws_instance.example[2] (remote-exec): Preparing to unpack .../06-libwebp6_0.6.1-2_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libtiff5:amd64.
aws_instance.example[2] (remote-exec): Preparing to unpack .../07-libtiff5_4.1.0+git191117-2build1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libxpm4:amd64.
aws_instance.example[2] (remote-exec): Preparing to unpack .../08-libxpm4_1%3a3.5.12-1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libgd3:amd64.
aws_instance.example[2] (remote-exec): Preparing to unpack .../09-libgd3_2.2.5-5.2ubuntu2_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package nginx-common.
aws_instance.example[2] (remote-exec): Preparing to unpack .../10-nginx-common_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[2] (remote-exec): Unpacking nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libnginx-mod-http-image-filter.
aws_instance.example[2] (remote-exec): Preparing to unpack .../11-libnginx-mod-http-image-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libnginx-mod-http-xslt-filter.
aws_instance.example[2] (remote-exec): Preparing to unpack .../12-libnginx-mod-http-xslt-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libnginx-mod-mail.
aws_instance.example[2] (remote-exec): Preparing to unpack .../13-libnginx-mod-mail_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package libnginx-mod-stream.
aws_instance.example[2] (remote-exec): Preparing to unpack .../14-libnginx-mod-stream_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[0] (remote-exec): Setting up libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package nginx-core.
aws_instance.example[0] (remote-exec): Setting up libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[2] (remote-exec): Preparing to unpack .../15-nginx-core_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up fonts-dejavu-core (2.37-1) ...
aws_instance.example[0] (remote-exec): Setting up libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package nginx.
aws_instance.example[0] (remote-exec): Setting up libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[2] (remote-exec): Preparing to unpack .../16-nginx_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[0] (remote-exec): Setting up libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Unpacking nginx (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Setting up libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[2] (remote-exec): Setting up nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[0] (remote-exec): Setting up libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[0] (remote-exec): Setting up libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[0] (remote-exec): Setting up libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /lib/systemd/system/nginx.service.
aws_instance.example[1]: Creation complete after 1m15s [id=i-03d0a980ff4cd14c1]
aws_instance.example[0] (remote-exec): Setting up nginx (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Processing triggers for ufw (0.36-6) ...
aws_instance.example[0] (remote-exec): Processing triggers for systemd (245.4-4ubuntu3) ...
aws_instance.example[2] (remote-exec): Setting up libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[2] (remote-exec): Setting up libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Setting up libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[2] (remote-exec): Setting up fonts-dejavu-core (2.37-1) ...
aws_instance.example[2] (remote-exec): Setting up libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Processing triggers for man-db (2.9.1-1) ...
aws_instance.example[2] (remote-exec): Setting up libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[2] (remote-exec): Setting up libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Setting up fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Setting up libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Setting up libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[0] (remote-exec): Processing triggers for libc-bin (2.31-0ubuntu9) ...
aws_instance.example[2] (remote-exec): Setting up libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Setting up libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[2] (remote-exec): Setting up libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Setting up nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[2]: Still creating... [1m17s elapsed]
aws_instance.example[0]: Still creating... [1m17s elapsed]
aws_instance.example[2] (remote-exec): Setting up nginx (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Processing triggers for ufw (0.36-6) ...
aws_instance.example[2] (remote-exec): Processing triggers for systemd (245.4-4ubuntu3) ...
aws_instance.example[2] (remote-exec): Processing triggers for man-db (2.9.1-1) ...
aws_instance.example[2] (remote-exec): Processing triggers for libc-bin (2.31-0ubuntu9) ...
aws_instance.example[0]: Creation complete after 1m21s [id=i-0ae34fafd3fd7dcb3]
aws_instance.example[2]: Creation complete after 1m22s [id=i-0e7f9686281be8f51]

Apply complete! Resources: 16 added, 0 changed, 0 destroyed.



## Remote login

ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/05-Provisioner_Script$ ssh -i ~/mykey ubuntu@54.77.43.202
Warning: Permanently added '54.77.43.202' (ECDSA) to the list of known hosts.
Welcome to Ubuntu 20.04 LTS (GNU/Linux 5.4.0-1009-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Tue May 12 10:12:37 UTC 2020

  System load:  0.02              Processes:             108
  Usage of /:   18.2% of 7.69GB   Users logged in:       0
  Memory usage: 19%               IPv4 address for eth0: 172.31.44.70
  Swap usage:   0%


19 updates can be installed immediately.
10 of these updates are security updates.
To see these additional updates run: apt list --upgradable


Last login: Tue May 12 10:08:27 2020 from 121.190.44.177

# Terraform Destroy

aws_vpc.main will be destroyed
 - resource "aws_vpc" "main" {
     - arn                              = "arn:aws:ec2:eu-west-1:918903027633:vpc/vpc-0f813c121c81213fa" -> null
     - assign_generated_ipv6_cidr_block = false -> null
     - cidr_block                       = "10.0.0.0/16" -> null
     - default_network_acl_id           = "acl-03fac9d57d4a3f11d" -> null
     - default_route_table_id           = "rtb-040f8bc07a4965ac0" -> null
     - default_security_group_id        = "sg-0c15b1e27c57f60fa" -> null
     - dhcp_options_id                  = "dopt-041e34b648824bf7f" -> null
     - enable_classiclink               = false -> null
     - enable_classiclink_dns_support   = false -> null
     - enable_dns_hostnames             = true -> null
     - enable_dns_support               = true -> null
     - id                               = "vpc-0f813c121c81213fa" -> null
     - instance_tenancy                 = "default" -> null
     - main_route_table_id              = "rtb-040f8bc07a4965ac0" -> null
     - owner_id                         = "918903027633" -> null
     - tags                             = {
         - "Name" = "main"
       } -> null
   }

Plan: 0 to add, 0 to change, 16 to destroy.

Do you really want to destroy all resources?
 Terraform will destroy all your managed infrastructure, as shown above.
 There is no undo. Only 'yes' will be accepted to confirm.

 Enter a value: yes

aws_instance.example[2]: Destroying... [id=i-0e7f9686281be8f51]
aws_subnet.main-private-3: Destroying... [id=subnet-0efce09a5022cabbd]
aws_route_table_association.main-public-2-a: Destroying... [id=rtbassoc-0cac41fe38bdd05ad]
aws_subnet.main-private-1: Destroying... [id=subnet-003615c6ad029629b]
aws_route_table_association.main-public-3-a: Destroying... [id=rtbassoc-053a04fc9311e8014]
aws_instance.example[1]: Destroying... [id=i-03d0a980ff4cd14c1]
aws_subnet.main-private-2: Destroying... [id=subnet-0a69646d932713f29]
aws_instance.example[0]: Destroying... [id=i-0ae34fafd3fd7dcb3]
aws_route_table_association.main-public-1-a: Destroying... [id=rtbassoc-0b577b4ff1266be2c]
aws_route_table_association.main-public-3-a: Destruction complete after 2s
aws_subnet.main-public-3: Destroying... [id=subnet-0e14b68d8a34b975e]
aws_route_table_association.main-public-1-a: Destruction complete after 2s
aws_subnet.main-public-1: Destroying... [id=subnet-0f8d099d0a0507410]
aws_route_table_association.main-public-2-a: Destruction complete after 2s
aws_subnet.main-public-2: Destroying... [id=subnet-047d1edf40e291f2b]
aws_route_table.main-public: Destroying... [id=rtb-0c27dd9bf0939573e]
aws_subnet.main-private-1: Destruction complete after 4s
aws_subnet.main-private-3: Destruction complete after 4s
aws_subnet.main-private-2: Destruction complete after 4s
aws_subnet.main-public-1: Destruction complete after 3s
aws_subnet.main-public-3: Destruction complete after 3s
aws_subnet.main-public-2: Destruction complete after 3s
aws_route_table.main-public: Destruction complete after 5s
aws_internet_gateway.main-gw: Destroying... [id=igw-0edba9462bace0cbe]
aws_instance.example[2]: Still destroying... [id=i-0e7f9686281be8f51, 10s elapsed]
aws_instance.example[0]: Still destroying... [id=i-0ae34fafd3fd7dcb3, 10s elapsed]
aws_instance.example[1]: Still destroying... [id=i-03d0a980ff4cd14c1, 10s elapsed]
aws_internet_gateway.main-gw: Still destroying... [id=igw-0edba9462bace0cbe, 10s elapsed]
aws_internet_gateway.main-gw: Destruction complete after 13s
aws_vpc.main: Destroying... [id=vpc-0f813c121c81213fa]
aws_instance.example[2]: Still destroying... [id=i-0e7f9686281be8f51, 20s elapsed]
aws_instance.example[1]: Still destroying... [id=i-03d0a980ff4cd14c1, 20s elapsed]
aws_instance.example[0]: Still destroying... [id=i-0ae34fafd3fd7dcb3, 20s elapsed]
aws_vpc.main: Destruction complete after 2s
aws_instance.example[0]: Destruction complete after 26s
aws_instance.example[1]: Destruction complete after 26s
aws_instance.example[2]: Destruction complete after 26s
aws_key_pair.mykey: Destroying... [id=mykey]
aws_key_pair.mykey: Destruction complete after 3s
