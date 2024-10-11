# Terraform-EC2-Instance-and-AMI-Creation
Purpose:  In this mini project, you will use Terraform to automate the creation of an EC2 instance on AWS and then create an Ami Machine Image (AMI) from that instance.

## Step 1: Create a Project Directory
Open a terminal and create a new directory for your Terraform project.

```bash
mkdir terraform-ec2-ami
```

## Step 2: Change into the Project Directory
Navigate into the newly created directory.

```bash
cd terraform-ec2-ami
```

## Step 3: Create a Terraform Configuration File
Use a text editor like `nano` to create the main configuration file.

```bash
nano main.tf
```

## Step 4: Add the Terraform Configuration

Copy and paste the following configuration into your `main.tf` file:

```hcl
provider "aws" {
  region = "us-east-1"  # Change this to your desired AWS region
}

resource "aws_instance" "example_instance" {
  ami           = "ami-0c55b159cbfafe1f0"  # Specify your desired AMI ID
  instance_type = "t2.micro"
  key_name      = "your-key-pair"  # Specify your key pair name

  # Add other necessary configuration for your instance (e.g., subnet, security group, etc.)
}

resource "aws_ami" "example_ami" {
  name        = "example-ami"
  description = "Example AMI created with Terraform"
  instance_id = aws_instance.example_instance.id

  # Add any additional settings or configuration for your AMI
}
```

Save the file after pasting the code (`Ctrl + O`, then `Ctrl + X` in `nano`).

## Step 5: Initialize the Terraform Project
Initialize your project to download the necessary provider plugins.

```bash
terraform init
```

## Step 6: Apply the Terraform Configuration
Run the following command to create your resources:

```bash
terraform apply
```

Terraform will prompt you to confirm. Type `yes` to proceed.

## Step 7: Modify the Configuration (Optional)
You can experiment by changing the configuration. For example:
- Modify the `instance_type` from `t2.micro` to `t2.small`.
- Add additional resources, like a security group, or change the region.

After making changes, apply the configuration again:

```bash
terraform apply
```

## Step 8: Document Your Observations
While working on this project, note your observations:
- Did the EC2 instance and AMI get created successfully?
- Were there any errors during `terraform apply`?
- Any changes or updates you applied afterward?

Challenges you might face could include:
- Issues with region-specific AMIs.
- Incorrect key pair name.
- Security group or network configuration problems.

Make sure to keep track of these challenges and how you resolved them.

## Conclusion
This guide walks you through creating an EC2 instance and AMI using Terraform. By experimenting with the configuration, you can better understand Terraform's capabilities.
```

Let me know if you need any further adjustments!
