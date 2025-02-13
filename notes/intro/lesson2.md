### Setting Up Your First Terraform Project

- **Project File Creation**

  - A file named `main.tf` is created to hold the Terraform code.

- **Purpose of the Project**

  - The code in `main.tf` will create an AWS S3 bucket.
  - The bucket's name is formatted as `<yourname>-first-bucket`.
  - The bucket is created in the `us-east-2` region.

- **Structure of the Terraform Code**

  - **Provider Block**
    - Declares the AWS provider using the `provider` keyword.
    - Specifies the provider (AWS) and configures parameters like the region.
    - Example configuration sets `region = "us-east-2"`.
  - **Resource Block**
    - Defines the infrastructure element to be created, in this case, an S3 bucket.
    - Uses the `resource` keyword with the resource type `"aws_s3_bucket"`.
    - Provides a unique identifier for the resource (e.g., `"first_bucket"`).
    - Sets parameters for the resource, such as the bucket name.

- **Key Points**

  - Terraform code is highly readable and declarative, making it clear what infrastructure will be created.
  - The separation into provider and resource blocks helps organize configuration:
    - The provider block handles external service configuration.
    - The resource block defines specific infrastructure elements.

### Creating Your First Infrastructure with Terraform

- **Terraform Initialization**

  - Start by initializing the Terraform project using `terraform init`.
  - Requires environment variables:
    - `access_key_id` (e.g., )
    - `secret_access_key` (e.g., )
  - Ensure you have an AWS account set up before proceeding.

- **Executing Terraform Apply**

  - Running `terraform apply` prompts Terraform to compare your code with the current AWS infrastructure.
  - Terraform generates a plan showing that it will create an S3 bucket if it doesn't exist.
  - The process pauses, awaiting confirmation (`yes`) to proceed.
  - On successful application, you'll see output indicating:\
    `Apply complete! Resources: 1 added, 0 changed, 0 destroyed.`

- **Verification and Drift Detection**

  - Check the AWS Console (S3 section) to confirm the S3 bucket has been created.
  - If you manually delete the bucket from AWS and run `terraform apply` again:
    - Terraform detects the drift and plans to recreate the bucket.
  - Running `terraform apply` when the bucket exists results in:\
    `Apply complete! Resources: 0 added, 0 changed, 0 destroyed.`\
    indicating the current state matches the configuration.

- **Destroying the Infrastructure**

  - Use `terraform destroy` to remove the created infrastructure.
  - Terraform shows a destruction plan and awaits confirmation (`yes`).
  - On completion, you see:\
    `Destroy complete! Resources: 1 destroyed.`
  - Confirm in the AWS Console that the S3 bucket has been removed.

- **Key Takeaways**

  - Terraform's plan feature allows you to preview changes before applying them.
  - The tool automatically detects and reconciles differences between the code and the actual infrastructure state.
  - Always run `terraform destroy` after testing to avoid unwanted AWS charges.
