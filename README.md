# AWS S3 Bucket creation using Terraform

In this we are going to provishion the AWS s3 bucket using Hashicorp's Terraform (0.12)

Reference: https://www.terraform.io/docs/providers/aws/index.html

## What is Terraform 

Terraform is a tool designed to help you automate your cloud infrastructure. It allows you to create your infrastructure as code, using a high-level configuration language called HCL.

It is developed by HashiCorp, open-source, and licensed under Mozilla Public License 2.0.

## Installation Procedure

Download the terraform binary file https://www.terraform.io/downloads.html

Download the terraform zip archive and unzip it in a suitable location. Once you have unzipped the terraform, update PATH environment variable pointing to terraform. Since, the folder /usr/local/bin is already set to PATH environment variable, we don't need to set it again. If you are using any other location, then specify it in the PATH environment variable either in .bash_profile or in /etc/profile.

Note: I have build this environment using Amazon Linux 2, Terraform 0.12 and Visual Code.

> Commandline 

```
[root@shazakz ~]# cd /usr/local/src
[root@shazakz src]# wget https://releases.hashicorp.com/terraform/0.12.24/terraform_0.12.24_linux_amd64.zip
[root@shazakz src]# unzip terraform_0.12.24_linux_amd64.zip
[root@shazakz src]# mv terraform /usr/local/bin/
```
If you have opted for a different custom path rather than the default path, use this commad to add the custom path.

```
export PATH=$PATH:/terraform-path/
```
Verify the installation of terraform with the following command.

```
[root@shazakz src]# terraform
Usage: terraform [--version] [--help] <command> [args]
The available commands for execution are listed below.
The most common, useful commands are shown first, followed by
less common or more advanced commands. If you're just getting
started with Terraform, stick with the common commands. For the
other commands, please read the help and docs before usage.

Common commands:
apply               Builds or changes infrastructure
console            Interactive console for Terraform interpolations
destroy            Destroy Terraform-managed infrastructure
fmt                  Rewrites config files to canonical format
get                  Download and install modules for the configuration
graph              Create a visual graph of Terraform resources
import             Import existing infrastructure into Terraform
init                  Initializes Terraform configuration from a module
output             Read an output from a state file
plan                Generate and show an execution plan
push               Upload this Terraform module to Atlas to run
refresh            Update local state file against real resources
remote            Configure remote state storage
show               Inspect Terraform state or plan
taint                Manually mark a resource for recreation
untaint             Manually unmark a resource as tainted
validate           Validates the Terraform files
version            Prints the Terraform version

All other commands:
debug              Debug output management (experimental)
state                Advanced state management
```
## AWS Configurations

Create an user for the Terraform and a test user.

* Terraform user must have IAM access and S3 access accordigly. Also need access credentials (access key & secret key).
* test user don't need any permission.

## Terraform files and uses

Here, I have created 3 files.

1. main-latest.tf
2. variables.tf
3. bucket-policy.json

> main-latest.tf: This file contains main terraform configuration script.

> variables.tf: This file have the variables that we used instead of giving hard-code in the main file.

> bucket-policy.json: Encapsulated with the AWS s3 bucket policy, which give access to a test user on the bucket.

