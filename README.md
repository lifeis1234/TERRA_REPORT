# TERRA_REPORT 1번
## 설치 terraform init
ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/04-Provisioner_files$ terraform init

Initializing the backend...

Initializing provider plugins...

The following providers do not have any version constraints in configuration,
so the latest version was installed.

To prevent automatic upgrades to new major versions that may contain breaking
changes, it is recommended to add version = "..." constraints to the
corresponding provider blocks in configuration, with the constraint strings
suggested below.

* provider.aws: version = "~> 2.61"

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.

## terraform plan

ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/04-Provisioner_files$ terraform plan
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
      + tags                         = {
          + "Name" = "My Instance"
        }
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

ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/04-Provisioner_files$ terraform apply -auto-approve
aws_key_pair.mykey: Creating...
aws_key_pair.mykey: Creation complete after 0s [id=mykey]
aws_instance.example: Creating...
aws_instance.example: Still creating... [10s elapsed]
aws_instance.example: Still creating... [20s elapsed]
aws_instance.example: Creation complete after 22s [id=i-0a880852b44a6d3ad]

Apply complete! Resources: 2 added, 0 changed, 0 destroyed.


# Apply terraform init
ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/04-Provisioner_files$ terraform apply -auto-approve
aws_key_pair.mykey: Refreshing state... [id=mykey]
aws_instance.example: Refreshing state... [id=i-0a880852b44a6d3ad]

Apply complete! Resources: 0 added, 0 changed, 0 destroyed.
ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/04-Provisioner_files$

# Destroy terraform destroy
ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/04-Provisioner_files$ terraform destroy
aws_key_pair.mykey: Refreshing state... [id=mykey]
aws_instance.example: Refreshing state... [id=i-0a880852b44a6d3ad]

An execution plan has been generated and is shown below.
Resource actions are indicated with the following symbols:
  - destroy

Terraform will perform the following actions:

  # aws_instance.example will be destroyed
  - resource "aws_instance" "example" {
      - ami                          = "ami-00edfb46b107f643c" -> null
      - arn                          = "arn:aws:ec2:ap-northeast-2:918903027633:instance/i-0a880852b44a6d3ad" -> null
      - associate_public_ip_address  = true -> null
      - availability_zone            = "ap-northeast-2c" -> null
      - cpu_core_count               = 1 -> null
      - cpu_threads_per_core         = 1 -> null
      - disable_api_termination      = false -> null
      - ebs_optimized                = false -> null
      - get_password_data            = false -> null
      - hibernation                  = false -> null
      - id                           = "i-0a880852b44a6d3ad" -> null
      - instance_state               = "running" -> null
      - instance_type                = "t2.micro" -> null
      - ipv6_address_count           = 0 -> null
      - ipv6_addresses               = [] -> null
      - key_name                     = "mykey" -> null
      - monitoring                   = false -> null
      - primary_network_interface_id = "eni-05c0fb884878b5e94" -> null
      - private_dns                  = "ip-172-31-47-28.ap-northeast-2.compute.internal" -> null
      - private_ip                   = "172.31.47.28" -> null
      - public_dns                   = "ec2-13-209-17-232.ap-northeast-2.compute.amazonaws.com" -> null
      - public_ip                    = "13.209.17.232" -> null
      - security_groups              = [
          - "default",
        ] -> null
      - source_dest_check            = true -> null
      - subnet_id                    = "subnet-012deb4b1be3f3b3d" -> null
      - tags                         = {
          - "Name" = "My Instance"
        } -> null
      - tenancy                      = "default" -> null
      - volume_tags                  = {} -> null
      - vpc_security_group_ids       = [
          - "sg-0ddcdfc0d37a8630c",
        ] -> null

      - credit_specification {
          - cpu_credits = "standard" -> null
        }

      - metadata_options {
          - http_endpoint               = "enabled" -> null
          - http_put_response_hop_limit = 1 -> null
          - http_tokens                 = "optional" -> null
        }

      - root_block_device {
          - delete_on_termination = true -> null
          - device_name           = "/dev/sda1" -> null
          - encrypted             = false -> null
          - iops                  = 100 -> null
          - volume_id             = "vol-027fd581111283b54" -> null
          - volume_size           = 8 -> null
          - volume_type           = "gp2" -> null
        }
    }

  # aws_key_pair.mykey will be destroyed
  - resource "aws_key_pair" "mykey" {
      - fingerprint = "3e:a6:f9:e6:4e:ef:7b:7e:8f:e6:22:a4:c7:4b:de:90" -> null
      - id          = "mykey" -> null
      - key_name    = "mykey" -> null
      - key_pair_id = "key-0f1c955e2d1ec57f9" -> null
      - public_key  = "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDVb46/FxCPpvDaOfcTht71kwALGdt4r6rQPQXvXy0RYs/1q+CYE+yPi2BRvuDf2eylbChGon8PL3jihs30uMZmEvhX6i+mqvI06MloGlLMrwo6ev8/sX4puR5TAa+F1hy8NTDJjI0Hm/enQIjJD9On2f/8XV9kBZf4Q87aUVL5jLrcWIgIhC1cfEMqH3aD1WALmIu7ueNAh/YiM3+FgmNXPZfGs6iZzoAvsq4y11A79H20S/w9C1TKskIG3ytpASBEE9Ieec25qPvE2Ip71N8Wo/R6I3K0ToWGcnNBi0gs4MW5soN/l9A4K3OF5MFQAre4iLqQl0I2AObjhQNyd33F ubuntu@u1" -> null
      - tags        = {} -> null
    }

Plan: 0 to add, 0 to change, 2 to destroy.

Do you really want to destroy all resources?
  Terraform will destroy all your managed infrastructure, as shown above.
  There is no undo. Only 'yes' will be accepted to confirm.

  Enter a value: yes

aws_instance.example: Destroying... [id=i-0a880852b44a6d3ad]
aws_instance.example: Still destroying... [id=i-0a880852b44a6d3ad, 10s elapsed]
aws_instance.example: Still destroying... [id=i-0a880852b44a6d3ad, 20s elapsed]
aws_instance.example: Still destroying... [id=i-0a880852b44a6d3ad, 30s elapsed]
aws_instance.example: Destruction complete after 30s
aws_key_pair.mykey: Destroying... [id=mykey]
aws_key_pair.mykey: Destruction complete after 0s

Destroy complete! Resources: 2 destroyed.

# TERRA_REPORT 2번

## 설치 terraform init
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

## terraform apply
ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/04-Provisioner_files$ terraform plan
Refreshing Terraform state in-memory prior to plan...
The refreshed state will be used to calculate this plan, but will not be
persisted to local or remote state storage.


Error: Error in function call

  on instance.tf line 3, in resource "aws_key_pair" "mykey":
   3:   public_key = file(var.PATH_TO_PUBLIC_KEY)
    |----------------
    | var.PATH_TO_PUBLIC_KEY is "~/mykey1.pub"

Call to function "file" failed: no file exists at /home/ubuntu/mykey1.pub.


## terraform destroy
