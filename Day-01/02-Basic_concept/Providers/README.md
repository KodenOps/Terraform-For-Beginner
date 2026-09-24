# What the hell is **Provider**
So, Terraform allows you to write .tf commands to provision and manage cloud infra/services. These are two environments that are built by different companies and technologies. Provider here does one thing which is to Interprete/Translate the .tf commands into commands that the cloud providers could understand.

                  Terraform
                     │
              .tf configuration
                     │
                     ▼
               Terraform Core
                     │
              "I need to create
               an AWS VPC"
                     │
                     ▼
              AWS Provider
                     │
        translates Terraform's
        resource operations into
        AWS API calls
                     │
                     ▼
                AWS APIs
                     │
                     ▼
             AWS infrastructure


## First Provider
Below is a sample AWS provider snippet.

```hcl

terraform {
  required_version = ">= 1.10.0"

  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 6.0"
    }
  }
}

# Configure the AWS Provider
provider "aws" {
  region = "us-east-1"
}

# Create a VPC
resource "aws_vpc" "example" {
  cidr_block = "10.0.0.0/16"
}

```

### Versions
There are two versions line in the snippet. One, is the version of the AWS provider itself and the second is the Terraform version constraint for the terraform to run.

If the installed version of Terraform `terraform -version` on your system is `1.8.2` and you specify the `required_version = ">= 1.10.0"`, this will fail to run because the constraint in your document is that the terraform manifest must run on a version above or equal to 1.10.0

#### Operators
- `>`: regular greater than operator
- `<`: regular less than operator
- `=`: equal to operator
- `>=`: greater or equal to operator
- `<=`: Less or equal to operator
- `~>`: this is the pessimistic operator. If used for version like `1.6.0`, it means versions above 1.6.0 (1.6.1, 1.6.2,.....1.6.9999) but can never permit version `1.7.0`
- `~<`: same as above but here less