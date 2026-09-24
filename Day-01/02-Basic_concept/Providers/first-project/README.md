# Your first project
In this short task, you will deploy a VPC on AWS. This means the following:
- You will need to be able to reach your AWS account via CLI
- YOu will need to create the `main.tf` file containing your provider and resources blocks
- finally, you'll run your `terraform` commands

## Connecting to AWS via CLI
- Create an IAM user with the right permission (permission to be able to create VPC alone)
- Create a Access Key for the user (if you won't have access to GUI while logging in)
- install `aws cli`
- After installation, run `aws login`, confirm the `REGION` by pressing `ENTER`.
- This will trigger your browser to initiate login. If no GUI is possible, paste your ID and Key from the Access Key you created earlier


## Setting Up the Main.tf
This has already been provided in the folder. This is just a simple manifest.

```hcl

terraform {
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
resource "aws_vpc" "main" {
  cidr_block       = "10.0.0.0/16"
  instance_tenancy = "default"

  tags = {
    Name = "testing"
  }
}


```
## Run `Terraform` command
Now that everything is ready for use, run the following

1. Initiate the terraform to download the `provider`

```shell
terraform init
```

This will also initiate the following:
- Initializes the backend
- Creates/updates .terraform/
- Creates/updates .terraform.lock.hcl

2. Check if your manifest is correct

```shell

terraform validate

```

3. Dry-run your manifest (main.tf)
```shell

terraform plan

```

4. Finally, deploy your VPC

```shell

terraform apply

```

5. After confirming the deployment and done with everything, you can delete using:

```shell

terraform destroy

```