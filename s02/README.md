# TERRA_REPORT 2번

## 설치 terraform init
uubuntu@u1:/mnt/hgfs/Desktop/terraform-course/04-Provisioner_files$ terraform init

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
      + ami                          = "ami-0dad359ff462124ca"
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
      + public_key  = "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDVb46/FxCPpvDaOfcTht71kwALGdt4r6rQPQXvXy0RYs/1q+CYE+yPi2BRvuDf2eylbChGon8PL3jihs3mEvhX6i+mqvI06MloGlLMrwo6ev8/sX4puR5TAa+F1hy8NTDJjI0Hm/enQIjJD9On2f/8XV9kBZf4Q87aUVL5jLrcWIgIhC1cfEMqH3aD1WALmIu7ueNAh/YiM3+FgmNXPZfGs6iZzoAvs1A79H20S/w9C1TKskIG3ytpASBEE9Ieec25qPvE2Ip71N8Wo/R6I3K0ToWGcnNBi0gs4MW5soN/l9A4K3OF5MFQAre4iLqQl0I2AObjhQNyd33F ubuntu@u1"
    }

Plan: 2 to add, 0 to change, 0 to destroy.

------------------------------------------------------------------------

Note: You didn't specify an "-out" parameter to save this plan, so Terraform
can't guarantee that exactly these actions will be performed if
"terraform apply" is subsequently run.



## terraform apply
ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/05-Provisioner_Script$ terraform apply -auto-approve
aws_subnet.main-private-3: Refreshing state... [id=subnet-0290c176297c95bd1]
aws_subnet.main-public-2: Refreshing state... [id=subnet-0b2986d3f4fab1ee7]
aws_route_table_association.main-public-2-a: Refreshing state... [id=rtbassoc-0822b1dbc1a0e6ea3]
aws_route_table_association.main-public-1-a: Refreshing state... [id=rtbassoc-095e1be87b14c0fdb]
aws_subnet.main-private-1: Refreshing state... [id=subnet-094c1ac6012ac4f50]
aws_internet_gateway.main-gw: Refreshing state... [id=igw-0ff81657f1a4f1432]
aws_subnet.main-private-2: Refreshing state... [id=subnet-09b6362bcf5b9d3db]
aws_subnet.main-public-3: Refreshing state... [id=subnet-00ce79bf3224e69f2]
aws_vpc.main: Refreshing state... [id=vpc-0533b36027d067f57]
aws_route_table.main-public: Refreshing state... [id=rtb-05f6e1ec690a53581]
aws_route_table_association.main-public-3-a: Refreshing state... [id=rtbassoc-0b658a0ea94a63b4f]
aws_subnet.main-public-1: Refreshing state... [id=subnet-0b7f7cd48cb07d7f7]
aws_route_table_association.main-public-2-a: Destroying... [id=rtbassoc-0822b1dbc1a0e6ea3]
aws_subnet.main-private-1: Destroying... [id=subnet-094c1ac6012ac4f50]
aws_subnet.main-private-2: Destroying... [id=subnet-09b6362bcf5b9d3db]
aws_route_table_association.main-public-3-a: Destroying... [id=rtbassoc-0b658a0ea94a63b4f]
aws_subnet.main-private-3: Destroying... [id=subnet-0290c176297c95bd1]
aws_route_table_association.main-public-1-a: Destroying... [id=rtbassoc-095e1be87b14c0fdb]
aws_key_pair.mykey: Creating...
aws_route_table_association.main-public-3-a: Destruction complete after 2s
aws_subnet.main-public-3: Destroying... [id=subnet-00ce79bf3224e69f2]
aws_route_table_association.main-public-2-a: Destruction complete after 2s
aws_subnet.main-public-2: Destroying... [id=subnet-0b2986d3f4fab1ee7]
aws_route_table_association.main-public-1-a: Destruction complete after 2s
aws_subnet.main-public-1: Destroying... [id=subnet-0b7f7cd48cb07d7f7]
aws_route_table.main-public: Destroying... [id=rtb-05f6e1ec690a53581]
aws_key_pair.mykey: Creation complete after 3s [id=mykey]
aws_instance.example[2]: Creating...
aws_instance.example[3]: Creating...
aws_instance.example[0]: Creating...
aws_subnet.main-private-1: Destruction complete after 3s
aws_instance.example[1]: Creating...
aws_subnet.main-private-3: Destruction complete after 4s
aws_subnet.main-private-2: Destruction complete after 4s
aws_subnet.main-public-3: Destruction complete after 3s
aws_subnet.main-public-1: Destruction complete after 3s
aws_subnet.main-public-2: Destruction complete after 3s
aws_route_table.main-public: Destruction complete after 7s
aws_internet_gateway.main-gw: Destroying... [id=igw-0ff81657f1a4f1432]
aws_instance.example[2]: Still creating... [12s elapsed]
aws_instance.example[3]: Still creating... [12s elapsed]
aws_instance.example[0]: Still creating... [12s elapsed]
aws_instance.example[1]: Still creating... [13s elapsed]
aws_internet_gateway.main-gw: Still destroying... [id=igw-0ff81657f1a4f1432, 10s elapsed]
aws_internet_gateway.main-gw: Destruction complete after 13s
aws_vpc.main: Destroying... [id=vpc-0533b36027d067f57]
aws_vpc.main: Destruction complete after 1s
aws_instance.example[0]: Still creating... [23s elapsed]
aws_instance.example[3]: Still creating... [23s elapsed]
aws_instance.example[2]: Still creating... [23s elapsed]
aws_instance.example[1]: Still creating... [23s elapsed]
aws_instance.example[0]: Still creating... [33s elapsed]
aws_instance.example[3]: Still creating... [33s elapsed]
aws_instance.example[2]: Still creating... [33s elapsed]
aws_instance.example[1]: Still creating... [33s elapsed]
aws_instance.example[1]: Provisioning with 'file'...
aws_instance.example[2]: Provisioning with 'file'...
aws_instance.example[0]: Provisioning with 'file'...
aws_instance.example[3]: Provisioning with 'file'...
aws_instance.example[2]: Still creating... [45s elapsed]
aws_instance.example[3]: Still creating... [45s elapsed]
aws_instance.example[0]: Still creating... [45s elapsed]
aws_instance.example[1]: Still creating... [45s elapsed]
aws_instance.example[1]: Provisioning with 'remote-exec'...
aws_instance.example[2]: Provisioning with 'remote-exec'...
aws_instance.example[1] (remote-exec): Connecting to remote host via SSH...
aws_instance.example[1] (remote-exec):   Host: 34.249.8.171
aws_instance.example[1] (remote-exec):   User: ubuntu
aws_instance.example[1] (remote-exec):   Password: false
aws_instance.example[1] (remote-exec):   Private key: true
aws_instance.example[1] (remote-exec):   Certificate: false
aws_instance.example[1] (remote-exec):   SSH Agent: false
aws_instance.example[1] (remote-exec):   Checking Host Key: false
aws_instance.example[2] (remote-exec): Connecting to remote host via SSH...
aws_instance.example[2] (remote-exec):   Host: 52.18.223.114
aws_instance.example[2] (remote-exec):   User: ubuntu
aws_instance.example[2] (remote-exec):   Password: false
aws_instance.example[2] (remote-exec):   Private key: true
aws_instance.example[2] (remote-exec):   Certificate: false
aws_instance.example[2] (remote-exec):   SSH Agent: false
aws_instance.example[2] (remote-exec):   Checking Host Key: false
aws_instance.example[0]: Provisioning with 'remote-exec'...
aws_instance.example[0] (remote-exec): Connecting to remote host via SSH...
aws_instance.example[0] (remote-exec):   Host: 54.246.189.253
aws_instance.example[0] (remote-exec):   User: ubuntu
aws_instance.example[0] (remote-exec):   Password: false
aws_instance.example[0] (remote-exec):   Private key: true
aws_instance.example[0] (remote-exec):   Certificate: false
aws_instance.example[0] (remote-exec):   SSH Agent: false
aws_instance.example[0] (remote-exec):   Checking Host Key: false
aws_instance.example[3]: Provisioning with 'remote-exec'...
aws_instance.example[3] (remote-exec): Connecting to remote host via SSH...
aws_instance.example[3] (remote-exec):   Host: 54.154.225.131
aws_instance.example[3] (remote-exec):   User: ubuntu
aws_instance.example[3] (remote-exec):   Password: false
aws_instance.example[3] (remote-exec):   Private key: true
aws_instance.example[3] (remote-exec):   Certificate: false
aws_instance.example[3] (remote-exec):   SSH Agent: false
aws_instance.example[3] (remote-exec):   Checking Host Key: false
aws_instance.example[1] (remote-exec): Connected!
aws_instance.example[2] (remote-exec): Connected!
aws_instance.example[0] (remote-exec): Connected!
aws_instance.example[3] (remote-exec): Connected!
aws_instance.example[3]: Still creating... [55s elapsed]
aws_instance.example[2]: Still creating... [55s elapsed]
aws_instance.example[0]: Still creating... [55s elapsed]
aws_instance.example[1]: Still creating... [55s elapsed]
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal InRelease [265 kB]
aws_instance.example[0] (remote-exec): 0% [1 InRelease 0 B/265 kB 0%] [Connect
aws_instance.example[0] (remote-exec): 0% [Connecting to security.ubuntu.com (
aws_instance.example[0] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]

aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal InRelease [265 kB]
aws_instance.example[1] (remote-exec): 0% [1 InRelease 0 B/265 kB 0%] [Connect
aws_instance.example[1] (remote-exec): 0% [Connecting to security.ubuntu.com (
aws_instance.example[1] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]
aws_instance.example[0] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]
aws_instance.example[0] (remote-exec): 0% [Waiting for headers]
aws_instance.example[0] (remote-exec): Get:4 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]
aws_instance.example[0] (remote-exec): 0% [4 InRelease 2586 B/107 kB 2%]
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 Packages [970 kB]
aws_instance.example[0] (remote-exec): 0% [5 Packages 31.0 kB/970 kB 3%]
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main Translation-en [506 kB]
aws_instance.example[0] (remote-exec): 0% [6 Translation-en 26.6 kB/506 kB 5%]
aws_instance.example[0] (remote-exec): 0% [5 Packages store 0 B] [6 Translatio
aws_instance.example[0] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 c-n-f Metadata [29.5 kB]
aws_instance.example[0] (remote-exec): 0% [5 Packages store 0 B] [7 Commands-a
aws_instance.example[0] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 Packages [8628 kB]

aws_instance.example[0] (remote-exec): 0% [5 Packages store 0 B] [8 Packages 0
aws_instance.example[0] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe Translation-en [5124 kB]
aws_instance.example[1] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]
aws_instance.example[1] (remote-exec): 0% [Waiting for headers]
aws_instance.example[1] (remote-exec): Get:4 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]
aws_instance.example[1] (remote-exec): 0% [4 InRelease 2586 B/107 kB 2%]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 Packages [970 kB]
aws_instance.example[1] (remote-exec): 0% [5 Packages 26.6 kB/970 kB 3%]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B] [Waiting for
aws_instance.example[1] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main Translation-en [506 kB]
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B] [6 Translatio
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 c-n-f Metadata [29.5 kB]
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B] [7 Commands-a
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 Packages [8628 kB]
aws_instance.example[0] (remote-exec): 0% [5 Packages store 0 B] [9 Translatio
aws_instance.example[0] (remote-exec): 0% [5 Packages store 0 B] [9 Translatio
aws_instance.example[0] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 c-n-f Metadata [265 kB]
aws_instance.example[0] (remote-exec): 0% [5 Packages store 0 B] [10 Commands-
aws_instance.example[0] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages [144 kB]
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B] [11 Pac
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse Translation-en [104 kB]
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B] [8 Packages 0
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
aws_instance.example[0] (remote-exec): Get:21 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [1132
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B] [21 Com
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): Get:22 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 c-n-f Metadata [11
aws_instance.example[1] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe Translation-en [5124 kB]
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B] [9 Translatio
aws_instance.example[1] (remote-exec): 0% [5 Packages store 0 B] [9 Translatio
aws_instance.example[1] (remote-exec): 0% [9 Translation-en 5124 kB/5124 kB 10
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [9 Tran
aws_instance.example[1] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 c-n-f Metadata [265 kB]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [10 Com
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages [144 kB]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [11 Pac
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse Translation-en [104 kB]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [12 Tra
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 c-n-f Metadata [9136 B]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [13 Com
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [84.4 kB]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [14 Pac
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main Translation-en [30.2 kB]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [15 Tra
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [1940 B]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [16 Com
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [4180 B]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [17 Pac
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Get:18 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en [1360 B]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [18 Tra
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Get:19 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [27.2 kB]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [19 Pac
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Get:20 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe Translation-en [13.3 kB]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [20 Tra
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Get:21 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [1132
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [21 Com
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Get:22 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 c-n-f Metadata [11
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B] [22 Com
aws_instance.example[0] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): 0% [7 Commands-amd64 store 0 B]
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:23 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/main amd64 c-n-f Metadata [112 B]
aws_instance.example[0] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:24 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/restricted amd64 c-n-f Metadata [B]
aws_instance.example[0] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:25 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages [2792 B]
aws_instance.example[0] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:26 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe Translation-en [1280 B]
aws_instance.example[0] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:27 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 c-n-f Metadata [18
aws_instance.example[0] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:28 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/multiverse amd64 c-n-f Metadata [B]
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B] [22 Com
aws_instance.example[1] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): 0% [7 Commands-amd64 store 0 B]
aws_instance.example[1] (remote-exec): 0% [Working]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:23 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/main amd64 c-n-f Metadata [112 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:24 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/restricted amd64 c-n-f Metadata [B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[1] (remote-exec): Get:25 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages [2792 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[1] (remote-exec): Get:26 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe Translation-en [1280 B]
aws_instance.example[1] (remote-exec): Get:27 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 c-n-f Metadata [18
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[1] (remote-exec): Get:28 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/multiverse amd64 c-n-f Metadata [B]
aws_instance.example[0] (remote-exec): 92% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:29 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [50.1 kB]
aws_instance.example[0] (remote-exec): 92% [8 Packages store 0 B] [29 Packages
aws_instance.example[0] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): Get:30 http://security.ubuntu.com/ubuntu focal-security/main Translation-en [18.5 kB]
aws_instance.example[0] (remote-exec): 93% [8 Packages store 0 B] [30 Translat
aws_instance.example[0] (remote-exec): Get:31 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [1352 B]
aws_instance.example[0] (remote-exec): Get:32 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages [4180 B]
aws_instance.example[0] (remote-exec): 93% [8 Packages store 0 B] [32 Packages
aws_instance.example[0] (remote-exec): Get:33 http://security.ubuntu.com/ubuntu focal-security/restricted Translation-en [1360 B]
aws_instance.example[0] (remote-exec): Get:34 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [7548 B]
aws_instance.example[0] (remote-exec): 93% [8 Packages store 0 B] [Waiting for
aws_instance.example[0] (remote-exec): Get:35 http://security.ubuntu.com/ubuntu focal-security/universe Translation-en [5636 B]
aws_instance.example[0] (remote-exec): Get:36 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [608 B]
aws_instance.example[0] (remote-exec): Get:37 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[1] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): 92% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:29 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [50.1 kB]
aws_instance.example[1] (remote-exec): 92% [8 Packages store 0 B] [29 Packages
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): Get:30 http://security.ubuntu.com/ubuntu focal-security/main Translation-en [18.5 kB]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B] [30 Translat
aws_instance.example[1] (remote-exec): Get:31 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [1352 B]
aws_instance.example[1] (remote-exec): Get:32 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages [4180 B]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B] [32 Packages
aws_instance.example[1] (remote-exec): Get:33 http://security.ubuntu.com/ubuntu focal-security/restricted Translation-en [1360 B]
aws_instance.example[1] (remote-exec): Get:34 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [7548 B]
aws_instance.example[1] (remote-exec): Get:35 http://security.ubuntu.com/ubuntu focal-security/universe Translation-en [5636 B]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B] [35 Translat
aws_instance.example[1] (remote-exec): Get:36 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [608 B]
aws_instance.example[1] (remote-exec): Get:37 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): 93% [Working]
aws_instance.example[0] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): 93% [Working]
aws_instance.example[1] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[0] (remote-exec): 93% [9 Translation-en store 0 B]
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
aws_instance.example[0] (remote-exec): Fetched 16.6 MB in 3s (5920 kB/s)
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
aws_instance.example[1] (remote-exec): Fetched 16.6 MB in 3s (5903 kB/s)
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal InRelease [265 kB]
aws_instance.example[2] (remote-exec): 0% [1 InRelease 0 B/265 kB 0%] [Connect
aws_instance.example[2] (remote-exec): 0% [Waiting for headers]
aws_instance.example[2] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]
aws_instance.example[2] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]
aws_instance.example[2] (remote-exec): Get:4 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]
aws_instance.example[2] (remote-exec): 0% [4 InRelease 8378 B/107 kB 8%]
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
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [8 Packages 0
aws_instance.example[2] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe Translation-en [5124 kB]
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [9 Translatio
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [9 Translatio
aws_instance.example[2] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 c-n-f Metadata [265 kB]
aws_instance.example[2] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages [144 kB]
aws_instance.example[2] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse Translation-en [104 kB]
aws_instance.example[2] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 c-n-f Metadata [9136 B]
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [84.4 kB]
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [14 Packages
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main Translation-en [30.2 kB]
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [15 Translati
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [1940 B]
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [16 Commands-
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [4180 B]
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [17 Packages
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:18 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en [1360 B]
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [18 Translati
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:19 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [27.2 kB]
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [19 Packages
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:20 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe Translation-en [13.3 kB]
aws_instance.example[2] (remote-exec): 0% [5 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:21 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [1132
aws_instance.example[2] (remote-exec): 0% [5 Packages store 5827 kB] [Waiting
aws_instance.example[2] (remote-exec): 0% [Waiting for headers]
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B] [Waitin
aws_instance.example[2] (remote-exec): Get:22 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 c-n-f Metadata [11
aws_instance.example[2] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): 0% [7 Commands-amd64 store 0 B]
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:23 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/main amd64 c-n-f Metadata [112 B]
aws_instance.example[2] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:24 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/restricted amd64 c-n-f Metadata [B]
aws_instance.example[2] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:25 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages [2792 B]
aws_instance.example[2] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:26 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe Translation-en [1280 B]
aws_instance.example[2] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:27 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 c-n-f Metadata [18
aws_instance.example[2] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[2] (remote-exec): Get:28 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/multiverse amd64 c-n-f Metadata [B]
aws_instance.example[2] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): 92% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:29 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [50.1 kB]
aws_instance.example[2] (remote-exec): 92% [8 Packages store 0 B] [29 Packages
aws_instance.example[2] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): Get:30 http://security.ubuntu.com/ubuntu focal-security/main Translation-en [18.5 kB]
aws_instance.example[2] (remote-exec): 93% [8 Packages store 0 B] [30 Translat
aws_instance.example[2] (remote-exec): Get:31 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [1352 B]
aws_instance.example[2] (remote-exec): Get:32 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages [4180 B]
aws_instance.example[2] (remote-exec): Get:33 http://security.ubuntu.com/ubuntu focal-security/restricted Translation-en [1360 B]
aws_instance.example[2] (remote-exec): 93% [8 Packages store 0 B] [33 Translat
aws_instance.example[2] (remote-exec): Get:34 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [7548 B]
aws_instance.example[2] (remote-exec): Get:35 http://security.ubuntu.com/ubuntu focal-security/universe Translation-en [5636 B]
aws_instance.example[2] (remote-exec): Get:36 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [608 B]
aws_instance.example[2] (remote-exec): Get:37 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[2]: Still creating... [1m5s elapsed]
aws_instance.example[3]: Still creating... [1m5s elapsed]
aws_instance.example[0]: Still creating... [1m5s elapsed]
aws_instance.example[1]: Still creating... [1m5s elapsed]
aws_instance.example[2] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[2] (remote-exec): 93% [Working]
aws_instance.example[2] (remote-exec): 93% [9 Translation-en store 0 B]
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
aws_instance.example[0] (remote-exec): Reading package lists... 10%
aws_instance.example[2] (remote-exec): 93% [9 Translation-en store 0 B]
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
aws_instance.example[2] (remote-exec): Fetched 16.6 MB in 3s (5910 kB/s)
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
aws_instance.example[1] (remote-exec): Reading package lists... 10%
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
aws_instance.example[3] (remote-exec): 0% [Working]
aws_instance.example[3] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal InRelease [265 kB]
aws_instance.example[3] (remote-exec): 0% [1 InRelease 0 B/265 kB 0%] [Connect
aws_instance.example[3] (remote-exec): 0% [Waiting for headers]
aws_instance.example[3] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]
aws_instance.example[0] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[0] (remote-exec):   libwebp6 libxpm4 nginx nginx-common
aws_instance.example[0] (remote-exec):   nginx-core
aws_instance.example[0] (remote-exec): 0 upgraded, 17 newly installed, 0 to remove and 21 not upgraded.
aws_instance.example[0] (remote-exec): Need to get 2431 kB of archives.
aws_instance.example[0] (remote-exec): After this operation, 7891 kB of additional disk space will be used.
aws_instance.example[0] (remote-exec): 0% [Working]
aws_instance.example[0] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fonts-dejavu-core all 2.37-1 [104]
aws_instance.example[0] (remote-exec): 0% [1 fonts-dejavu-core 0 B/1041 kB 0%]
aws_instance.example[0] (remote-exec): 35% [Working]
aws_instance.example[0] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fontconfig-config all 2.13.1-2ubu [28.8 kB]
aws_instance.example[0] (remote-exec): 35% [2 fontconfig-config 0 B/28.8 kB 0%
aws_instance.example[0] (remote-exec): 38% [Working]
aws_instance.example[0] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libfontconfig1 amd64 2.13.1-2ubun[114 kB]
aws_instance.example[0] (remote-exec): 38% [3 libfontconfig1 0 B/114 kB 0%]
aws_instance.example[0] (remote-exec): 42% [Working]
aws_instance.example[0] (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg-turbo8 amd64 2.0.3-0ubunt118 kB]
aws_instance.example[0] (remote-exec): 42% [4 libjpeg-turbo8 0 B/118 kB 0%]
aws_instance.example[0] (remote-exec): 48% [Working]
aws_instance.example[0] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg8 amd64 8c-2ubuntu8 [2194
aws_instance.example[0] (remote-exec): 48% [5 libjpeg8 0 B/2194 B 0%]
aws_instance.example[0] (remote-exec): 49% [Working]
aws_instance.example[0] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjbig0 amd64 2.1-3.1build1 [26.]
aws_instance.example[0] (remote-exec): 49% [6 libjbig0 0 B/26.7 kB 0%]
aws_instance.example[0] (remote-exec): 51% [Working]
aws_instance.example[0] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libwebp6 amd64 0.6.1-2 [185 kB]
aws_instance.example[0] (remote-exec): 51% [7 libwebp6 0 B/185 kB 0%]
aws_instance.example[0] (remote-exec): 58% [Working]
aws_instance.example[0] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libtiff5 amd64 4.1.0+git191117-2b1 [161 kB]
aws_instance.example[0] (remote-exec): 58% [8 libtiff5 0 B/161 kB 0%]
aws_instance.example[0] (remote-exec): 65% [Working]
aws_instance.example[0] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libxpm4 amd64 1:3.5.12-1 [34.0 kB
aws_instance.example[0] (remote-exec): 65% [9 libxpm4 0 B/34.0 kB 0%]
aws_instance.example[0] (remote-exec): 67% [Working]
aws_instance.example[0] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libgd3 amd64 2.2.5-5.2ubuntu2 [1B]
aws_instance.example[0] (remote-exec): 67% [10 libgd3 0 B/118 kB 0%]
aws_instance.example[0] (remote-exec): 72% [Working]
aws_instance.example[1] (remote-exec): Reading package lists... 66%
aws_instance.example[1] (remote-exec): Reading package lists... 66%
aws_instance.example[0] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-common all 1.17.10-0ubuntu7.3 kB]
aws_instance.example[0] (remote-exec): 72% [11 nginx-common 0 B/37.3 kB 0%]
aws_instance.example[0] (remote-exec): 74% [Working]
aws_instance.example[0] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-image-filter a 1.17.10-0ubuntu1 [14.3 kB]
aws_instance.example[0] (remote-exec): 74% [12 libnginx-mod-http-image-filter
aws_instance.example[0] (remote-exec): 76% [Working]
aws_instance.example[0] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-xslt-filter am1.17.10-0ubuntu1 [12.5 kB]
aws_instance.example[0] (remote-exec): 76% [13 libnginx-mod-http-xslt-filter 0
aws_instance.example[0] (remote-exec): 78% [Working]
aws_instance.example[0] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-mail amd64 1.17.10-ntu1 [42.3 kB]
aws_instance.example[0] (remote-exec): 78% [14 libnginx-mod-mail 0 B/42.3 kB 0
aws_instance.example[0] (remote-exec): 80% [Working]
aws_instance.example[0] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-stream amd64 1.17.1buntu1 [66.9 kB]
aws_instance.example[0] (remote-exec): 80% [15 libnginx-mod-stream 0 B/66.9 kB
aws_instance.example[0] (remote-exec): 84% [Working]
aws_instance.example[0] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-core amd64 1.17.10-0ubuntu25 kB]
aws_instance.example[0] (remote-exec): 84% [16 nginx-core 0 B/425 kB 0%]
aws_instance.example[0] (remote-exec): 99% [Working]
aws_instance.example[0] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx all 1.17.10-0ubuntu1 [3616
aws_instance.example[0] (remote-exec): 99% [17 nginx 0 B/3616 B 0%]
aws_instance.example[0] (remote-exec): 100% [Working]
aws_instance.example[0] (remote-exec): Fetched 2431 kB in 0s (27.9 MB/s)
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
aws_instance.example[3] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]
aws_instance.example[3] (remote-exec): Get:4 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]
aws_instance.example[3] (remote-exec): 0% [3 InRelease 58.7 kB/98.3 kB 60%] [4
aws_instance.example[3] (remote-exec): 0% [4 InRelease 2586 B/107 kB 2%]
aws_instance.example[3] (remote-exec): 0% [Working]
aws_instance.example[3] (remote-exec): 0% [Working]
aws_instance.example[3] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 Packages [970 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages 47.6 kB/970 kB 5%]
aws_instance.example[3] (remote-exec): 0% [Working]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [Waiting for
aws_instance.example[3] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main Translation-en [506 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [6 Translatio
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 c-n-f Metadata [29.5 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [7 Commands-a
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 Packages [8628 kB]
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 98%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
aws_instance.example[1] (remote-exec): Reading package lists... 99%
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
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [8 Packages 0
aws_instance.example[3] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe Translation-en [5124 kB]
aws_instance.example[0] (remote-exec): Preconfiguring packages ...
aws_instance.example[1] (remote-exec): Building dependency tree... 0%
aws_instance.example[1] (remote-exec): Building dependency tree... 0%
aws_instance.example[1] (remote-exec): Building dependency tree... 50%
aws_instance.example[1] (remote-exec): Building dependency tree... 50%
aws_instance.example[1] (remote-exec): Building dependency tree
aws_instance.example[1] (remote-exec): Reading state information... 0%
aws_instance.example[1] (remote-exec): Reading state information... 0%
aws_instance.example[1] (remote-exec): Reading state information... Done
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [9 Translatio
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/universe amd64 c-n-f Metadata [265 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [10 Commands-
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages [144 kB]
aws_instance.example[0] (remote-exec): Selecting previously unselected package fonts-dejavu-core.
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [11 Packages
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse Translation-en [104 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [12 Translati
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/multiverse amd64 c-n-f Metadata [9136 B]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [13 Commands-
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [84.4 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [14 Packages
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main Translation-en [30.2 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [15 Translati
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [Waiting for
aws_instance.example[3] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [1940 B]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [Waiting for
aws_instance.example[3] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [4180 B]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [Waiting for
aws_instance.example[3] (remote-exec): Get:18 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en [1360 B]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [Waiting for
aws_instance.example[3] (remote-exec): Get:19 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [27.2 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [Waiting for
aws_instance.example[3] (remote-exec): Get:20 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe Translation-en [13.3 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [Waiting for
aws_instance.example[3] (remote-exec): Get:21 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [1132
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B] [Waiting for
aws_instance.example[3] (remote-exec): Get:22 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 c-n-f Metadata [11
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
aws_instance.example[1] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fonts-dejavu-core all 2.37-1 [104]
aws_instance.example[1] (remote-exec): 0% [1 fonts-dejavu-core 0 B/1041 kB 0%]
aws_instance.example[1] (remote-exec): 35% [Working]
aws_instance.example[1] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fontconfig-config all 2.13.1-2ubu [28.8 kB]
aws_instance.example[1] (remote-exec): 35% [2 fontconfig-config 0 B/28.8 kB 0%
aws_instance.example[1] (remote-exec): 38% [Working]
aws_instance.example[1] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libfontconfig1 amd64 2.13.1-2ubun[114 kB]
aws_instance.example[1] (remote-exec): 38% [3 libfontconfig1 0 B/114 kB 0%]
aws_instance.example[1] (remote-exec): 42% [Working]
aws_instance.example[1] (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg-turbo8 amd64 2.0.3-0ubunt118 kB]
aws_instance.example[1] (remote-exec): 42% [4 libjpeg-turbo8 0 B/118 kB 0%]
aws_instance.example[1] (remote-exec): 48% [Working]
aws_instance.example[1] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg8 amd64 8c-2ubuntu8 [2194
aws_instance.example[1] (remote-exec): 48% [5 libjpeg8 0 B/2194 B 0%]
aws_instance.example[1] (remote-exec): 49% [Working]
aws_instance.example[1] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjbig0 amd64 2.1-3.1build1 [26.]
aws_instance.example[1] (remote-exec): 49% [6 libjbig0 0 B/26.7 kB 0%]
aws_instance.example[1] (remote-exec): 51% [Working]
aws_instance.example[1] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libwebp6 amd64 0.6.1-2 [185 kB]
aws_instance.example[3] (remote-exec): 0% [5 Packages store 0 B]
aws_instance.example[3] (remote-exec): 0% [Working]
aws_instance.example[3] (remote-exec): 0% [6 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 0% [Working]
aws_instance.example[3] (remote-exec): 0% [7 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 0% [Working]
aws_instance.example[3] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[3] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:23 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/main amd64 c-n-f Metadata [112 B]
aws_instance.example[3] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:24 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/restricted amd64 c-n-f Metadata [B]
aws_instance.example[3] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[3] (remote-exec): Get:25 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages [2792 B]
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
aws_instance.example[3] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[3] (remote-exec): Get:26 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe Translation-en [1280 B]
aws_instance.example[3] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[3] (remote-exec): Get:27 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/universe amd64 c-n-f Metadata [18
aws_instance.example[0] (remote-exec): Preparing to unpack .../00-fonts-dejavu-core_2.37-1_all.deb ...
aws_instance.example[3] (remote-exec): 0% [8 Packages store 0 B] [Waiting for
aws_instance.example[3] (remote-exec): Get:28 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal-backports/multiverse amd64 c-n-f Metadata [B]
aws_instance.example[0] (remote-exec): Unpacking fonts-dejavu-core (2.37-1) ...
aws_instance.example[1] (remote-exec): 51% [7 libwebp6 0 B/185 kB 0%]
aws_instance.example[3] (remote-exec): 0% [8 Packages store 0 B]
aws_instance.example[1] (remote-exec): 58% [Working]
aws_instance.example[1] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libtiff5 amd64 4.1.0+git191117-2b1 [161 kB]
aws_instance.example[1] (remote-exec): 58% [8 libtiff5 0 B/161 kB 0%]
aws_instance.example[1] (remote-exec): 65% [Working]
aws_instance.example[1] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libxpm4 amd64 1:3.5.12-1 [34.0 kB
aws_instance.example[1] (remote-exec): 65% [9 libxpm4 0 B/34.0 kB 0%]
aws_instance.example[1] (remote-exec): 67% [Working]
aws_instance.example[1] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libgd3 amd64 2.2.5-5.2ubuntu2 [1B]
aws_instance.example[1] (remote-exec): 67% [10 libgd3 0 B/118 kB 0%]
aws_instance.example[1] (remote-exec): 72% [Working]
aws_instance.example[1] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-common all 1.17.10-0ubuntu7.3 kB]
aws_instance.example[1] (remote-exec): 72% [11 nginx-common 0 B/37.3 kB 0%]
aws_instance.example[1] (remote-exec): 74% [Working]
aws_instance.example[1] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-image-filter a 1.17.10-0ubuntu1 [14.3 kB]
aws_instance.example[1] (remote-exec): 74% [12 libnginx-mod-http-image-filter
aws_instance.example[1] (remote-exec): 76% [Working]
aws_instance.example[1] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-xslt-filter am1.17.10-0ubuntu1 [12.5 kB]
aws_instance.example[1] (remote-exec): 76% [13 libnginx-mod-http-xslt-filter 0
aws_instance.example[1] (remote-exec): 78% [Working]
aws_instance.example[1] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-mail amd64 1.17.10-ntu1 [42.3 kB]
aws_instance.example[1] (remote-exec): 78% [14 libnginx-mod-mail 0 B/42.3 kB 0
aws_instance.example[1] (remote-exec): 80% [Working]
aws_instance.example[1] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-stream amd64 1.17.1buntu1 [66.9 kB]
aws_instance.example[1] (remote-exec): 80% [15 libnginx-mod-stream 0 B/66.9 kB
aws_instance.example[1] (remote-exec): 84% [Working]
aws_instance.example[1] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-core amd64 1.17.10-0ubuntu25 kB]
aws_instance.example[1] (remote-exec): 84% [16 nginx-core 0 B/425 kB 0%]
aws_instance.example[1] (remote-exec): 99% [Working]
aws_instance.example[1] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx all 1.17.10-0ubuntu1 [3616
aws_instance.example[1] (remote-exec): 99% [17 nginx 0 B/3616 B 0%]
aws_instance.example[1] (remote-exec): 100% [Working]
aws_instance.example[1] (remote-exec): Fetched 2431 kB in 0s (35.7 MB/s)
aws_instance.example[0] (remote-exec): Selecting previously unselected package fontconfig-config.
aws_instance.example[0] (remote-exec): Preparing to unpack .../01-fontconfig-config_2.13.1-2ubuntu3_all.deb ...
aws_instance.example[0] (remote-exec): Unpacking fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libfontconfig1:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../02-libfontconfig1_2.13.1-2ubuntu3_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[3] (remote-exec): 92% [8 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:29 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [50.1 kB]
aws_instance.example[3] (remote-exec): 92% [8 Packages store 0 B] [29 Packages
aws_instance.example[3] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[3] (remote-exec): Get:30 http://security.ubuntu.com/ubuntu focal-security/main Translation-en [18.5 kB]
aws_instance.example[3] (remote-exec): 93% [8 Packages store 0 B] [30 Translat
aws_instance.example[3] (remote-exec): Get:31 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [1352 B]
aws_instance.example[3] (remote-exec): Get:32 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages [4180 B]
aws_instance.example[3] (remote-exec): Get:33 http://security.ubuntu.com/ubuntu focal-security/restricted Translation-en [1360 B]
aws_instance.example[3] (remote-exec): 93% [8 Packages store 0 B] [33 Translat
aws_instance.example[3] (remote-exec): Get:34 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [7548 B]
aws_instance.example[3] (remote-exec): Get:35 http://security.ubuntu.com/ubuntu focal-security/universe Translation-en [5636 B]
aws_instance.example[3] (remote-exec): Get:36 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [608 B]
aws_instance.example[3] (remote-exec): Get:37 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 c-n-f Metadata [116 B]
aws_instance.example[1] (remote-exec): Preconfiguring packages ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libjpeg-turbo8:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../03-libjpeg-turbo8_2.0.3-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libjpeg8:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../04-libjpeg8_8c-2ubuntu8_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[3] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): Selecting previously unselected package libjbig0:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../05-libjbig0_2.1-3.1build1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libwebp6:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../06-libwebp6_0.6.1-2_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libtiff5:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../07-libtiff5_4.1.0+git191117-2build1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package fonts-dejavu-core.
aws_instance.example[0] (remote-exec): Selecting previously unselected package libxpm4:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../08-libxpm4_1%3a3.5.12-1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libgd3:amd64.
aws_instance.example[0] (remote-exec): Preparing to unpack .../09-libgd3_2.2.5-5.2ubuntu2_amd64.deb ...
aws_instance.example[1] (remote-exec): (Reading database ...
aws_instance.example[0] (remote-exec): Unpacking libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package nginx-common.
aws_instance.example[0] (remote-exec): Preparing to unpack .../10-nginx-common_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[0] (remote-exec): Unpacking nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libnginx-mod-http-image-filter.
aws_instance.example[0] (remote-exec): Preparing to unpack .../11-libnginx-mod-http-image-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libnginx-mod-http-xslt-filter.
aws_instance.example[0] (remote-exec): Preparing to unpack .../12-libnginx-mod-http-xslt-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): 93% [8 Packages store 0 B]
aws_instance.example[0] (remote-exec): Selecting previously unselected package libnginx-mod-mail.
aws_instance.example[0] (remote-exec): Preparing to unpack .../13-libnginx-mod-mail_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package libnginx-mod-stream.
aws_instance.example[0] (remote-exec): Preparing to unpack .../14-libnginx-mod-stream_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Selecting previously unselected package nginx-core.
aws_instance.example[0] (remote-exec): Preparing to unpack .../15-nginx-core_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[0] (remote-exec): Unpacking nginx-core (1.17.10-0ubuntu1) ...
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
aws_instance.example[0] (remote-exec): Selecting previously unselected package nginx.
aws_instance.example[0] (remote-exec): Preparing to unpack .../16-nginx_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[0] (remote-exec): Unpacking nginx (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[0] (remote-exec): Setting up nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package fontconfig-config.
aws_instance.example[1] (remote-exec): Preparing to unpack .../01-fontconfig-config_2.13.1-2ubuntu3_all.deb ...
aws_instance.example[1] (remote-exec): Unpacking fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[3] (remote-exec): 93% [Working]
aws_instance.example[3] (remote-exec): 93% [9 Translation-en store 0 B]
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
aws_instance.example[0] (remote-exec): Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /lib/systemd/system/nginx.sce.
aws_instance.example[1] (remote-exec): Selecting previously unselected package libtiff5:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../07-libtiff5_4.1.0+git191117-2build1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libxpm4:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../08-libxpm4_1%3a3.5.12-1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libgd3:amd64.
aws_instance.example[1] (remote-exec): Preparing to unpack .../09-libgd3_2.2.5-5.2ubuntu2_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package nginx-common.
aws_instance.example[1] (remote-exec): Preparing to unpack .../10-nginx-common_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[3] (remote-exec): 93% [9 Translation-en store 0 B]
aws_instance.example[1] (remote-exec): Unpacking nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Selecting previously unselected package libnginx-mod-http-image-filter.
aws_instance.example[1] (remote-exec): Preparing to unpack .../11-libnginx-mod-http-image-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[1] (remote-exec): Unpacking libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
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
aws_instance.example[3] (remote-exec): 93% [Working]
aws_instance.example[3] (remote-exec): 93% [10 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 94% [Working]
aws_instance.example[3] (remote-exec): 94% [11 Packages store 0 B]
aws_instance.example[3] (remote-exec): 94% [Working]
aws_instance.example[3] (remote-exec): 94% [12 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 94% [Working]
aws_instance.example[3] (remote-exec): 94% [13 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 94% [Working]
aws_instance.example[3] (remote-exec): 94% [14 Packages store 0 B]
aws_instance.example[3] (remote-exec): 95% [Working]
aws_instance.example[3] (remote-exec): 95% [15 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 95% [Working]
aws_instance.example[3] (remote-exec): 95% [16 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 95% [Working]
aws_instance.example[3] (remote-exec): 95% [17 Packages store 0 B]
aws_instance.example[3] (remote-exec): 95% [Working]
aws_instance.example[3] (remote-exec): 95% [18 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 95% [Working]
aws_instance.example[3] (remote-exec): 95% [19 Packages store 0 B]
aws_instance.example[3] (remote-exec): 96% [Working]
aws_instance.example[3] (remote-exec): 96% [20 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 96% [Working]
aws_instance.example[3] (remote-exec): 96% [21 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 96% [Working]
aws_instance.example[3] (remote-exec): 96% [22 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 96% [Working]
aws_instance.example[3] (remote-exec): 96% [23 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 97% [Working]
aws_instance.example[3] (remote-exec): 97% [24 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 97% [Working]
aws_instance.example[3] (remote-exec): 97% [25 Packages store 0 B]
aws_instance.example[3] (remote-exec): 97% [Working]
aws_instance.example[3] (remote-exec): 97% [26 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 97% [Working]
aws_instance.example[3] (remote-exec): 97% [27 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 98% [Working]
aws_instance.example[3] (remote-exec): 98% [28 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 98% [Working]
aws_instance.example[3] (remote-exec): 98% [29 Packages store 0 B]
aws_instance.example[3] (remote-exec): 98% [Working]
aws_instance.example[3] (remote-exec): 98% [30 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 98% [Working]
aws_instance.example[3] (remote-exec): 98% [31 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 99% [Working]
aws_instance.example[3] (remote-exec): 99% [32 Packages store 0 B]
aws_instance.example[3] (remote-exec): 99% [Working]
aws_instance.example[3] (remote-exec): 99% [33 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 99% [Working]
aws_instance.example[3] (remote-exec): 99% [34 Packages store 0 B]
aws_instance.example[3] (remote-exec): 99% [Working]
aws_instance.example[3] (remote-exec): 99% [35 Translation-en store 0 B]
aws_instance.example[3] (remote-exec): 100% [Working]
aws_instance.example[3] (remote-exec): 100% [36 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 100% [Working]
aws_instance.example[3] (remote-exec): 100% [37 Commands-amd64 store 0 B]
aws_instance.example[3] (remote-exec): 100% [Working]
aws_instance.example[3] (remote-exec): Fetched 16.6 MB in 3s (5938 kB/s)
aws_instance.example[1] (remote-exec): Selecting previously unselected package nginx.
aws_instance.example[1] (remote-exec): Preparing to unpack .../16-nginx_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[1] (remote-exec): Unpacking nginx (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[0] (remote-exec): Setting up libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[0] (remote-exec): Setting up libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[1] (remote-exec): Setting up nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up fonts-dejavu-core (2.37-1) ...
aws_instance.example[0] (remote-exec): Setting up libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[0] (remote-exec): Setting up libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[0] (remote-exec): Setting up libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[0] (remote-exec): Setting up libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[0] (remote-exec): Setting up libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[1] (remote-exec): Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /lib/systemd/system/nginx.sce.
aws_instance.example[0] (remote-exec): Setting up libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Setting up nginx (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Processing triggers for ufw (0.36-6) ...
aws_instance.example[0] (remote-exec): Processing triggers for systemd (245.4-4ubuntu3) ...
aws_instance.example[2] (remote-exec): Reading package lists... 0%
aws_instance.example[2] (remote-exec): Reading package lists... 0%
aws_instance.example[2] (remote-exec): Reading package lists... 0%
aws_instance.example[2] (remote-exec): Reading package lists... 6%
aws_instance.example[2] (remote-exec): Reading package lists... 6%
aws_instance.example[2] (remote-exec): Reading package lists... 9%
aws_instance.example[2] (remote-exec): Reading package lists... 9%
aws_instance.example[2] (remote-exec): Reading package lists... 10%
aws_instance.example[2] (remote-exec): Reading package lists... 10%
aws_instance.example[1] (remote-exec): Setting up libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[1] (remote-exec): Setting up libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[1] (remote-exec): Setting up fonts-dejavu-core (2.37-1) ...
aws_instance.example[1] (remote-exec): Setting up libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[1] (remote-exec): Setting up libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Reading package lists... 10%
aws_instance.example[2] (remote-exec): Reading package lists... 10%
aws_instance.example[0] (remote-exec): Processing triggers for man-db (2.9.1-1) ...
aws_instance.example[1] (remote-exec): Setting up libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[1] (remote-exec): Setting up libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[1] (remote-exec): Setting up libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[1] (remote-exec): Setting up libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Setting up nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[0] (remote-exec): Processing triggers for libc-bin (2.31-0ubuntu9) ...
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
aws_instance.example[2] (remote-exec): Building dependency tree... 0%
aws_instance.example[2] (remote-exec): Building dependency tree... 0%
aws_instance.example[2] (remote-exec): Building dependency tree... 50%
aws_instance.example[2] (remote-exec): Building dependency tree... 50%
aws_instance.example[2] (remote-exec): Building dependency tree
aws_instance.example[2] (remote-exec): Reading state information... 0%
aws_instance.example[2] (remote-exec): Reading state information... 0%
aws_instance.example[2] (remote-exec): Reading state information... Done
aws_instance.example[1] (remote-exec): Setting up nginx (1.17.10-0ubuntu1) ...
aws_instance.example[1] (remote-exec): Processing triggers for ufw (0.36-6) ...
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
aws_instance.example[1] (remote-exec): Processing triggers for systemd (245.4-4ubuntu3) ...
aws_instance.example[2] (remote-exec): The following NEW packages will be installed:
aws_instance.example[2] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[2] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[2] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[2] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[2] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[2] (remote-exec):   libnginx-mod-mail
aws_instance.example[2] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[2] (remote-exec):   libwebp6 libxpm4 nginx nginx-common
aws_instance.example[2] (remote-exec):   nginx-core
aws_instance.example[2] (remote-exec): 0 upgraded, 17 newly installed, 0 to remove and 21 not upgraded.
aws_instance.example[2] (remote-exec): Need to get 2431 kB of archives.
aws_instance.example[2] (remote-exec): After this operation, 7891 kB of additional disk space will be used.
aws_instance.example[2] (remote-exec): 0% [Working]
aws_instance.example[2] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fonts-dejavu-core all 2.37-1 [104]
aws_instance.example[2] (remote-exec): 0% [1 fonts-dejavu-core 0 B/1041 kB 0%]
aws_instance.example[2] (remote-exec): 35% [Working]
aws_instance.example[2] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fontconfig-config all 2.13.1-2ubu [28.8 kB]
aws_instance.example[2] (remote-exec): 35% [2 fontconfig-config 0 B/28.8 kB 0%
aws_instance.example[2] (remote-exec): 38% [Working]
aws_instance.example[2] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libfontconfig1 amd64 2.13.1-2ubun[114 kB]
aws_instance.example[2] (remote-exec): 38% [3 libfontconfig1 0 B/114 kB 0%]
aws_instance.example[2] (remote-exec): 42% [Working]
aws_instance.example[2] (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg-turbo8 amd64 2.0.3-0ubunt118 kB]
aws_instance.example[2] (remote-exec): 42% [4 libjpeg-turbo8 0 B/118 kB 0%]
aws_instance.example[2] (remote-exec): 48% [Working]
aws_instance.example[2] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg8 amd64 8c-2ubuntu8 [2194
aws_instance.example[2] (remote-exec): 48% [5 libjpeg8 0 B/2194 B 0%]
aws_instance.example[2] (remote-exec): 49% [Working]
aws_instance.example[2] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjbig0 amd64 2.1-3.1build1 [26.]
aws_instance.example[2] (remote-exec): 49% [6 libjbig0 0 B/26.7 kB 0%]
aws_instance.example[2] (remote-exec): 51% [Working]
aws_instance.example[2] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libwebp6 amd64 0.6.1-2 [185 kB]
aws_instance.example[2] (remote-exec): 51% [7 libwebp6 0 B/185 kB 0%]
aws_instance.example[2] (remote-exec): 58% [Working]
aws_instance.example[2] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libtiff5 amd64 4.1.0+git191117-2b1 [161 kB]
aws_instance.example[2] (remote-exec): 58% [8 libtiff5 0 B/161 kB 0%]
aws_instance.example[2] (remote-exec): 65% [Working]
aws_instance.example[2] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libxpm4 amd64 1:3.5.12-1 [34.0 kB
aws_instance.example[2] (remote-exec): 65% [9 libxpm4 0 B/34.0 kB 0%]
aws_instance.example[2] (remote-exec): 67% [Working]
aws_instance.example[2] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libgd3 amd64 2.2.5-5.2ubuntu2 [1B]
aws_instance.example[2] (remote-exec): 67% [10 libgd3 0 B/118 kB 0%]
aws_instance.example[2] (remote-exec): 72% [Working]
aws_instance.example[2] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-common all 1.17.10-0ubuntu7.3 kB]
aws_instance.example[2] (remote-exec): 72% [11 nginx-common 0 B/37.3 kB 0%]
aws_instance.example[2] (remote-exec): 74% [Working]
aws_instance.example[2] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-image-filter a 1.17.10-0ubuntu1 [14.3 kB]
aws_instance.example[2] (remote-exec): 74% [12 libnginx-mod-http-image-filter
aws_instance.example[2] (remote-exec): 76% [Working]
aws_instance.example[2] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-xslt-filter am1.17.10-0ubuntu1 [12.5 kB]
aws_instance.example[2] (remote-exec): 76% [13 libnginx-mod-http-xslt-filter 0
aws_instance.example[2] (remote-exec): 78% [Working]
aws_instance.example[2] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-mail amd64 1.17.10-ntu1 [42.3 kB]
aws_instance.example[2] (remote-exec): 78% [14 libnginx-mod-mail 0 B/42.3 kB 0
aws_instance.example[2] (remote-exec): 80% [Working]
aws_instance.example[2] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-stream amd64 1.17.1buntu1 [66.9 kB]
aws_instance.example[2] (remote-exec): 80% [15 libnginx-mod-stream 0 B/66.9 kB
aws_instance.example[2] (remote-exec): 84% [Working]
aws_instance.example[2] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-core amd64 1.17.10-0ubuntu25 kB]
aws_instance.example[2] (remote-exec): 84% [16 nginx-core 0 B/425 kB 0%]
aws_instance.example[2] (remote-exec): 99% [Working]
aws_instance.example[2] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx all 1.17.10-0ubuntu1 [3616
aws_instance.example[2] (remote-exec): 99% [17 nginx 0 B/3616 B 0%]
aws_instance.example[2] (remote-exec): 100% [Working]
aws_instance.example[2] (remote-exec): Fetched 2431 kB in 0s (34.6 MB/s)
aws_instance.example[1] (remote-exec): Processing triggers for man-db (2.9.1-1) ...
aws_instance.example[2] (remote-exec): Preconfiguring packages ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package fonts-dejavu-core.
aws_instance.example[1] (remote-exec): Processing triggers for libc-bin (2.31-0ubuntu9) ...
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
aws_instance.example[2] (remote-exec): Selecting previously unselected package nginx-core.
aws_instance.example[2] (remote-exec): Preparing to unpack .../15-nginx-core_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[2] (remote-exec): Unpacking nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Selecting previously unselected package nginx.
aws_instance.example[2] (remote-exec): Preparing to unpack .../16-nginx_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[2] (remote-exec): Unpacking nginx (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Setting up libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[2] (remote-exec): Setting up nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Reading package lists... 0%
aws_instance.example[3] (remote-exec): Reading package lists... 0%
aws_instance.example[3] (remote-exec): Reading package lists... 0%
aws_instance.example[3] (remote-exec): Reading package lists... 6%
aws_instance.example[3] (remote-exec): Reading package lists... 6%
aws_instance.example[3] (remote-exec): Reading package lists... 9%
aws_instance.example[3] (remote-exec): Reading package lists... 9%
aws_instance.example[3] (remote-exec): Reading package lists... 10%
aws_instance.example[3] (remote-exec): Reading package lists... 10%
aws_instance.example[3] (remote-exec): Reading package lists... 10%
aws_instance.example[2] (remote-exec): Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /lib/systemd/system/nginx.sce.
aws_instance.example[3] (remote-exec): Reading package lists... 10%
aws_instance.example[3] (remote-exec): Reading package lists... 66%
aws_instance.example[3] (remote-exec): Reading package lists... 66%
aws_instance.example[3] (remote-exec): Reading package lists... 96%
aws_instance.example[3] (remote-exec): Reading package lists... 96%
aws_instance.example[3] (remote-exec): Reading package lists... 97%
aws_instance.example[3] (remote-exec): Reading package lists... 97%
aws_instance.example[3] (remote-exec): Reading package lists... 97%
aws_instance.example[3] (remote-exec): Reading package lists... 97%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 98%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... 99%
aws_instance.example[3] (remote-exec): Reading package lists... Done
aws_instance.example[3] (remote-exec): Reading package lists... 0%
aws_instance.example[3] (remote-exec): Reading package lists... 100%
aws_instance.example[3] (remote-exec): Reading package lists... Done
aws_instance.example[3] (remote-exec): Building dependency tree... 0%
aws_instance.example[3] (remote-exec): Building dependency tree... 0%
aws_instance.example[3] (remote-exec): Building dependency tree... 50%
aws_instance.example[3] (remote-exec): Building dependency tree... 50%
aws_instance.example[3] (remote-exec): Building dependency tree
aws_instance.example[2] (remote-exec): Setting up libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[2] (remote-exec): Setting up libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Setting up libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[2] (remote-exec): Setting up fonts-dejavu-core (2.37-1) ...
aws_instance.example[3] (remote-exec): Reading state information... 0%
aws_instance.example[3] (remote-exec): Reading state information... 0%
aws_instance.example[3] (remote-exec): Reading state information... Done
aws_instance.example[2] (remote-exec): Setting up libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Setting up libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[2] (remote-exec): Setting up libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Setting up fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Setting up libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): The following additional packages will be installed:
aws_instance.example[3] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[3] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[3] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[3] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[3] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[3] (remote-exec):   libnginx-mod-mail
aws_instance.example[3] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[3] (remote-exec):   libwebp6 libxpm4 nginx-common
aws_instance.example[3] (remote-exec):   nginx-core
aws_instance.example[3] (remote-exec): Suggested packages:
aws_instance.example[3] (remote-exec):   libgd-tools fcgiwrap nginx-doc
aws_instance.example[3] (remote-exec):   ssl-cert
aws_instance.example[3] (remote-exec): The following NEW packages will be installed:
aws_instance.example[3] (remote-exec):   fontconfig-config fonts-dejavu-core
aws_instance.example[3] (remote-exec):   libfontconfig1 libgd3 libjbig0
aws_instance.example[3] (remote-exec):   libjpeg-turbo8 libjpeg8
aws_instance.example[3] (remote-exec):   libnginx-mod-http-image-filter
aws_instance.example[3] (remote-exec):   libnginx-mod-http-xslt-filter
aws_instance.example[3] (remote-exec):   libnginx-mod-mail
aws_instance.example[3] (remote-exec):   libnginx-mod-stream libtiff5
aws_instance.example[3] (remote-exec):   libwebp6 libxpm4 nginx nginx-common
aws_instance.example[3] (remote-exec):   nginx-core
aws_instance.example[3] (remote-exec): 0 upgraded, 17 newly installed, 0 to remove and 21 not upgraded.
aws_instance.example[3] (remote-exec): Need to get 2431 kB of archives.
aws_instance.example[3] (remote-exec): After this operation, 7891 kB of additional disk space will be used.
aws_instance.example[3] (remote-exec): 0% [Working]
aws_instance.example[3] (remote-exec): Get:1 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fonts-dejavu-core all 2.37-1 [104]
aws_instance.example[3] (remote-exec): 0% [1 fonts-dejavu-core 0 B/1041 kB 0%]
aws_instance.example[3] (remote-exec): 35% [Working]
aws_instance.example[3] (remote-exec): Get:2 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 fontconfig-config all 2.13.1-2ubu [28.8 kB]
aws_instance.example[3] (remote-exec): 35% [2 fontconfig-config 0 B/28.8 kB 0%
aws_instance.example[3] (remote-exec): 38% [Working]
aws_instance.example[3] (remote-exec): Get:3 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libfontconfig1 amd64 2.13.1-2ubun[114 kB]
aws_instance.example[3] (remote-exec): 38% [3 libfontconfig1 0 B/114 kB 0%]
aws_instance.example[3] (remote-exec): 42% [Working]
aws_instance.example[3] (remote-exec): Get:4 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg-turbo8 amd64 2.0.3-0ubunt118 kB]
aws_instance.example[3] (remote-exec): 42% [4 libjpeg-turbo8 0 B/118 kB 0%]
aws_instance.example[3] (remote-exec): 48% [Working]
aws_instance.example[3] (remote-exec): Get:5 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjpeg8 amd64 8c-2ubuntu8 [2194
aws_instance.example[3] (remote-exec): 48% [5 libjpeg8 0 B/2194 B 0%]
aws_instance.example[3] (remote-exec): 49% [Working]
aws_instance.example[3] (remote-exec): Get:6 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libjbig0 amd64 2.1-3.1build1 [26.]
aws_instance.example[3] (remote-exec): 49% [6 libjbig0 0 B/26.7 kB 0%]
aws_instance.example[3] (remote-exec): 51% [Working]
aws_instance.example[3] (remote-exec): Get:7 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libwebp6 amd64 0.6.1-2 [185 kB]
aws_instance.example[3] (remote-exec): 51% [7 libwebp6 0 B/185 kB 0%]
aws_instance.example[3] (remote-exec): 58% [Working]
aws_instance.example[3] (remote-exec): Get:8 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libtiff5 amd64 4.1.0+git191117-2b1 [161 kB]
aws_instance.example[3] (remote-exec): 58% [8 libtiff5 0 B/161 kB 0%]
aws_instance.example[3] (remote-exec): 65% [Working]
aws_instance.example[3] (remote-exec): Get:9 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libxpm4 amd64 1:3.5.12-1 [34.0 kB
aws_instance.example[3] (remote-exec): 65% [9 libxpm4 0 B/34.0 kB 0%]
aws_instance.example[3] (remote-exec): 67% [Working]
aws_instance.example[3] (remote-exec): Get:10 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libgd3 amd64 2.2.5-5.2ubuntu2 [1B]
aws_instance.example[3] (remote-exec): 67% [10 libgd3 0 B/118 kB 0%]
aws_instance.example[3] (remote-exec): 72% [Working]
aws_instance.example[3] (remote-exec): Get:11 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-common all 1.17.10-0ubuntu7.3 kB]
aws_instance.example[3] (remote-exec): 72% [11 nginx-common 0 B/37.3 kB 0%]
aws_instance.example[3] (remote-exec): 74% [Working]
aws_instance.example[3] (remote-exec): Get:12 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-image-filter a 1.17.10-0ubuntu1 [14.3 kB]
aws_instance.example[3] (remote-exec): 74% [12 libnginx-mod-http-image-filter
aws_instance.example[3] (remote-exec): 76% [Working]
aws_instance.example[3] (remote-exec): Get:13 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-http-xslt-filter am1.17.10-0ubuntu1 [12.5 kB]
aws_instance.example[3] (remote-exec): 76% [13 libnginx-mod-http-xslt-filter 0
aws_instance.example[3] (remote-exec): 78% [Working]
aws_instance.example[3] (remote-exec): Get:14 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-mail amd64 1.17.10-ntu1 [42.3 kB]
aws_instance.example[3] (remote-exec): 78% [14 libnginx-mod-mail 0 B/42.3 kB 0
aws_instance.example[3] (remote-exec): 80% [Working]
aws_instance.example[3] (remote-exec): Get:15 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 libnginx-mod-stream amd64 1.17.1buntu1 [66.9 kB]
aws_instance.example[3] (remote-exec): 80% [15 libnginx-mod-stream 0 B/66.9 kB
aws_instance.example[3] (remote-exec): 84% [Working]
aws_instance.example[3] (remote-exec): Get:16 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx-core amd64 1.17.10-0ubuntu25 kB]
aws_instance.example[3] (remote-exec): 84% [16 nginx-core 0 B/425 kB 0%]
aws_instance.example[3] (remote-exec): 99% [Working]
aws_instance.example[3] (remote-exec): Get:17 http://eu-west-1.ec2.archive.ubuntu.com/ubuntu focal/main amd64 nginx all 1.17.10-0ubuntu1 [3616
aws_instance.example[3] (remote-exec): 99% [17 nginx 0 B/3616 B 0%]
aws_instance.example[3] (remote-exec): 100% [Working]
aws_instance.example[3] (remote-exec): Fetched 2431 kB in 0s (28.6 MB/s)
aws_instance.example[2] (remote-exec): Setting up libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[2] (remote-exec): Setting up libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[2] (remote-exec): Setting up libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[2] (remote-exec): Setting up libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Setting up nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Preconfiguring packages ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package fonts-dejavu-core.
aws_instance.example[3]: Still creating... [1m17s elapsed]
aws_instance.example[0]: Still creating... [1m17s elapsed]
aws_instance.example[2]: Still creating... [1m17s elapsed]
aws_instance.example[1]: Still creating... [1m17s elapsed]
aws_instance.example[2] (remote-exec): Setting up nginx (1.17.10-0ubuntu1) ...
aws_instance.example[2] (remote-exec): Processing triggers for ufw (0.36-6) ...
aws_instance.example[2] (remote-exec): Processing triggers for systemd (245.4-4ubuntu3) ...
aws_instance.example[3] (remote-exec): (Reading database ...
aws_instance.example[3] (remote-exec): (Reading database ... 5%
aws_instance.example[3] (remote-exec): (Reading database ... 10%
aws_instance.example[3] (remote-exec): (Reading database ... 15%
aws_instance.example[3] (remote-exec): (Reading database ... 20%
aws_instance.example[3] (remote-exec): (Reading database ... 25%
aws_instance.example[3] (remote-exec): (Reading database ... 30%
aws_instance.example[3] (remote-exec): (Reading database ... 35%
aws_instance.example[3] (remote-exec): (Reading database ... 40%
aws_instance.example[3] (remote-exec): (Reading database ... 45%
aws_instance.example[3] (remote-exec): (Reading database ... 50%
aws_instance.example[3] (remote-exec): (Reading database ... 55%
aws_instance.example[3] (remote-exec): (Reading database ... 60%
aws_instance.example[3] (remote-exec): (Reading database ... 65%
aws_instance.example[3] (remote-exec): (Reading database ... 70%
aws_instance.example[3] (remote-exec): (Reading database ... 75%
aws_instance.example[3] (remote-exec): (Reading database ... 80%
aws_instance.example[3] (remote-exec): (Reading database ... 85%
aws_instance.example[3] (remote-exec): (Reading database ... 90%
aws_instance.example[3] (remote-exec): (Reading database ... 95%
aws_instance.example[3] (remote-exec): (Reading database ... 100%
aws_instance.example[3] (remote-exec): (Reading database ... 59604 files and directories currently installed.)
aws_instance.example[3] (remote-exec): Preparing to unpack .../00-fonts-dejavu-core_2.37-1_all.deb ...
aws_instance.example[3] (remote-exec): Unpacking fonts-dejavu-core (2.37-1) ...
aws_instance.example[2] (remote-exec): Processing triggers for man-db (2.9.1-1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package fontconfig-config.
aws_instance.example[3] (remote-exec): Preparing to unpack .../01-fontconfig-config_2.13.1-2ubuntu3_all.deb ...
aws_instance.example[3] (remote-exec): Unpacking fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libfontconfig1:amd64.
aws_instance.example[3] (remote-exec): Preparing to unpack .../02-libfontconfig1_2.13.1-2ubuntu3_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[0]: Creation complete after 1m17s [id=i-07f36f7ba812c4e0e]
aws_instance.example[3] (remote-exec): Selecting previously unselected package libjpeg-turbo8:amd64.
aws_instance.example[3] (remote-exec): Preparing to unpack .../03-libjpeg-turbo8_2.0.3-0ubuntu1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libjpeg8:amd64.
aws_instance.example[2] (remote-exec): Processing triggers for libc-bin (2.31-0ubuntu9) ...
aws_instance.example[3] (remote-exec): Preparing to unpack .../04-libjpeg8_8c-2ubuntu8_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libjbig0:amd64.
aws_instance.example[3] (remote-exec): Preparing to unpack .../05-libjbig0_2.1-3.1build1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libwebp6:amd64.
aws_instance.example[3] (remote-exec): Preparing to unpack .../06-libwebp6_0.6.1-2_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libtiff5:amd64.
aws_instance.example[3] (remote-exec): Preparing to unpack .../07-libtiff5_4.1.0+git191117-2build1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libxpm4:amd64.
aws_instance.example[3] (remote-exec): Preparing to unpack .../08-libxpm4_1%3a3.5.12-1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libgd3:amd64.
aws_instance.example[3] (remote-exec): Preparing to unpack .../09-libgd3_2.2.5-5.2ubuntu2_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package nginx-common.
aws_instance.example[3] (remote-exec): Preparing to unpack .../10-nginx-common_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[3] (remote-exec): Unpacking nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libnginx-mod-http-image-filter.
aws_instance.example[3] (remote-exec): Preparing to unpack .../11-libnginx-mod-http-image-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[1]: Creation complete after 1m18s [id=i-0c782e5cfc61b6f58]
aws_instance.example[3] (remote-exec): Selecting previously unselected package libnginx-mod-http-xslt-filter.
aws_instance.example[3] (remote-exec): Preparing to unpack .../12-libnginx-mod-http-xslt-filter_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libnginx-mod-mail.
aws_instance.example[3] (remote-exec): Preparing to unpack .../13-libnginx-mod-mail_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package libnginx-mod-stream.
aws_instance.example[3] (remote-exec): Preparing to unpack .../14-libnginx-mod-stream_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package nginx-core.
aws_instance.example[3] (remote-exec): Preparing to unpack .../15-nginx-core_1.17.10-0ubuntu1_amd64.deb ...
aws_instance.example[3] (remote-exec): Unpacking nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Selecting previously unselected package nginx.
aws_instance.example[3] (remote-exec): Preparing to unpack .../16-nginx_1.17.10-0ubuntu1_all.deb ...
aws_instance.example[3] (remote-exec): Unpacking nginx (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Setting up libxpm4:amd64 (1:3.5.12-1) ...
aws_instance.example[3] (remote-exec): Setting up nginx-common (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service → /lib/systemd/system/nginx.sce.
aws_instance.example[3] (remote-exec): Setting up libjbig0:amd64 (2.1-3.1build1) ...
aws_instance.example[3] (remote-exec): Setting up libnginx-mod-http-xslt-filter (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Setting up libwebp6:amd64 (0.6.1-2) ...
aws_instance.example[3] (remote-exec): Setting up fonts-dejavu-core (2.37-1) ...
aws_instance.example[3] (remote-exec): Setting up libjpeg-turbo8:amd64 (2.0.3-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Setting up libjpeg8:amd64 (8c-2ubuntu8) ...
aws_instance.example[3] (remote-exec): Setting up libnginx-mod-mail (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Setting up fontconfig-config (2.13.1-2ubuntu3) ...
aws_instance.example[3] (remote-exec): Setting up libnginx-mod-stream (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Setting up libtiff5:amd64 (4.1.0+git191117-2build1) ...
aws_instance.example[3] (remote-exec): Setting up libfontconfig1:amd64 (2.13.1-2ubuntu3) ...
aws_instance.example[3] (remote-exec): Setting up libgd3:amd64 (2.2.5-5.2ubuntu2) ...
aws_instance.example[3] (remote-exec): Setting up libnginx-mod-http-image-filter (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Setting up nginx-core (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Setting up nginx (1.17.10-0ubuntu1) ...
aws_instance.example[3] (remote-exec): Processing triggers for ufw (0.36-6) ...
aws_instance.example[3] (remote-exec): Processing triggers for systemd (245.4-4ubuntu3) ...
aws_instance.example[3] (remote-exec): Processing triggers for man-db (2.9.1-1) ...
aws_instance.example[3] (remote-exec): Processing triggers for libc-bin (2.31-0ubuntu9) ...
aws_instance.example[2]: Creation complete after 1m21s [id=i-060c4d9cfd48d3b84]
aws_instance.example[3]: Creation complete after 1m25s [id=i-0e0c1ed560fdce84f]

Apply complete! Resources: 5 added, 0 changed, 12 destroyed.


## Remote login
ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/05-Provisioner_Script$ ssh -i ~/mykey ubuntu@52.18.223.114
Warning: Permanently added '52.18.223.114' (ECDSA) to the list of known hosts.
Welcome to Ubuntu 20.04 LTS (GNU/Linux 5.4.0-1009-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Tue May 12 09:55:02 UTC 2020

  System load:  0.25              Processes:             105
  Usage of /:   18.2% of 7.69GB   Users logged in:       0
  Memory usage: 20%               IPv4 address for eth0: 172.31.44.178
  Swap usage:   0%


19 updates can be installed immediately.
10 of these updates are security updates.
To see these additional updates run: apt list --upgradable


Last login: Tue May 12 09:53:02 2020 from 121.190.44.177


## terraform destroy
ubuntu@u1:/mnt/hgfs/Desktop/terraform-course/05-Provisioner_Script$ terraform destroy -auto-approve
aws_key_pair.mykey: Refreshing state... [id=mykey]
aws_instance.example[1]: Refreshing state... [id=i-0c782e5cfc61b6f58]
aws_instance.example[3]: Refreshing state... [id=i-0e0c1ed560fdce84f]
aws_instance.example[0]: Refreshing state... [id=i-07f36f7ba812c4e0e]
aws_instance.example[2]: Refreshing state... [id=i-060c4d9cfd48d3b84]
aws_instance.example[2]: Destroying... [id=i-060c4d9cfd48d3b84]
aws_instance.example[3]: Destroying... [id=i-0e0c1ed560fdce84f]
aws_instance.example[1]: Destroying... [id=i-0c782e5cfc61b6f58]
aws_instance.example[0]: Destroying... [id=i-07f36f7ba812c4e0e]
aws_instance.example[3]: Still destroying... [id=i-0e0c1ed560fdce84f, 10s elapsed]
aws_instance.example[2]: Still destroying... [id=i-060c4d9cfd48d3b84, 10s elapsed]
aws_instance.example[1]: Still destroying... [id=i-0c782e5cfc61b6f58, 10s elapsed]
aws_instance.example[0]: Still destroying... [id=i-07f36f7ba812c4e0e, 10s elapsed]
aws_instance.example[3]: Still destroying... [id=i-0e0c1ed560fdce84f, 20s elapsed]
aws_instance.example[2]: Still destroying... [id=i-060c4d9cfd48d3b84, 20s elapsed]
aws_instance.example[1]: Still destroying... [id=i-0c782e5cfc61b6f58, 20s elapsed]
aws_instance.example[0]: Still destroying... [id=i-07f36f7ba812c4e0e, 20s elapsed]
aws_instance.example[2]: Destruction complete after 27s
aws_instance.example[1]: Destruction complete after 27s
aws_instance.example[3]: Destruction complete after 27s
aws_instance.example[0]: Still destroying... [id=i-07f36f7ba812c4e0e, 32s elapsed]
aws_instance.example[0]: Destruction complete after 39s
aws_key_pair.mykey: Destroying... [id=mykey]
aws_key_pair.mykey: Destruction complete after 1s

Destroy complete! Resources: 5 destroyed.
