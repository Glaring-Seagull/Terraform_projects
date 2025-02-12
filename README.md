# Simple AWS Webpage with Terraform

This project uses Terraform to deploy a simple AWS infrastructure that hosts a web server. The infrastructure includes a VPC, subnet, internet gateway, route table, security group, network interface, elastic IP, and an EC2 instance with Apache2 installed.

## Prerequisites

- [Terraform](https://www.terraform.io/downloads.html) installed
- AWS account with appropriate permissions
- AWS access key and secret key

## Setup

1. **Clone the repository**:

   ```sh
   git clone https://github.com/Glaring-Seagull/Terraform_projects.git
   cd Terraform_projects/Simple_AWS_webpage
   ```

2. **Create a vars.tf file**:

   Create a file named vars.tf and add the following content:

   ```hcl
   variable "aws_access_key" {
     description = "Put your AWS access key here..."
     type = string
     sensitive = true
   }

   variable "aws_secret_key" {
     description = "Put your AWS secret key here..."
     type = string
     sensitive = true
   }
   ```

3. **Configure AWS credentials**:

   Use your AWS access key and secret key in the vars.tf file.

4. **Initialize Terraform**:

   Initialize the Terraform working directory:

   ```sh
   terraform init
   ```

5. **Plan the deployment**:

   Generate and show an execution plan:

   ```sh
   terraform plan
   ```

6. **Apply the deployment**:

   Apply the changes required to reach the desired state of the configuration:

   ```sh
   terraform apply
   ```

   Type `yes` to confirm the deployment.

## Outputs

After the deployment is complete, Terraform will output the public IP address of the web server:

```sh
output "server_public_ip" {
  value = aws_eip.one.public_ip
}
```

You can use this IP address to access the web server in your browser.

## Clean Up

To destroy the infrastructure created by this Terraform configuration, run:

```sh
terraform destroy
```

Type `yes` to confirm the destruction.

## Notes
- Ensure that your AWS credentials are not hardcoded in the `main.tf` file for security reasons. Use environment variables or AWS credentials file as an alternative.
- The `ami` used in `aws_instance` is specific to the `us-east-1` region. Modify it based on your region availability.
- Update the `key_name` in `aws_instance` to match your AWS key pair name.

This README provides a step-by-step guide to deploy and manage a simple AWS infrastructure using Terraform, and is for demontration purposes only. For more information, refer to the [Terraform documentation](https://www.terraform.io/docs/index.html).
