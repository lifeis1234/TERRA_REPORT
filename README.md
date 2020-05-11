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
