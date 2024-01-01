## 12 - Infrastructure as Code with Terraform

Infrastructure as Code (IaC) with Terraform is a powerful approach to automate and manage infrastructure. Here's a simplified explanation and key points:

### What is Terraform?

Terraform is a tool for automating and managing infrastructure. It allows you to define the infrastructure you want in a file, and then apply it. Terraform will create, update, or destroy the infrastructure as needed.

### How Terraform Works:

1. **Definition File:**
   - You write a configuration file (e.g., `main.tf`) where you specify the desired infrastructure.

2. **Apply Changes:**
   - Run `terraform apply` to apply the configuration. Terraform will create the infrastructure as defined in the file.

3. **State Management:**
   - Terraform keeps track of the state of the infrastructure in a state file (`terraform.tfstate`). This file stores the current state of your resources.

4. **Changes and Updates:**
   - When you want to make changes, update the configuration file and re-run `terraform apply`. Terraform will figure out the changes needed and apply them.

### Advantages of Terraform:

- **Version Control:**
  - Infrastructure changes are tracked, providing a history of changes (Infrastructure as Code).

- **Replication:**
  - Easily replicate infrastructure for different environments (dev, staging, production).

- **Cleanup:**
  - Simple cleanup with a single command (`terraform destroy`).

- **Collaboration:**
  - Facilitates team collaboration by providing visibility into created infrastructure and easy modifications.

### Connecting to Platform Provider:

- Terraform connects to the platform provider (e.g., AWS) using the provider's API.
- For AWS, Terraform can deploy resources like EC2 servers using the AWS provider.

### Key Terraform Files:

- `main.tf`: Contains the main Terraform configuration.
- `variables.tf`: Defines variables used in the configuration.
- `outputs.tf`: Specifies outputs that should be exposed.
- `providers.tf`: Lists all providers used.
- `terraform.tfvars`: Contains variable values.
- `terraform.tfstate`: Stores the state of the infrastructure.
- `terraform.tfstate.backup`: Backup of the state file.
- `.terraform`: Directory containing plugins and providers.

### Important Terraform Commands:

- `terraform refresh`
- `terraform plan`
- `terraform apply`
- `terraform destroy`

### Modules/Providers:

- Modules and providers are plugins used by Terraform to connect to platforms.
- Examples include the AWS provider for AWS resources.
- Modules help organize and reuse configurations.

### Types of Resources:

- **Resource:** Used to create new infrastructure.
- **Data:** Used to query existing resources.

### Variables:

- Variables can be defined in `terraform.tfvars`.
- Can be set via command line (`-var` flag) or environment variables (`TF_VAR_`).
- Default values can be set in `variables.tf`.

### Provisioners:

- Used to execute commands after resource creation.
- Examples: "remote-exec" for running scripts on remote servers.

### Modules:

- Logical units grouping multiple resources.
- Reusable configurations with inputs and outputs.

### Remote State:

- Terraform can write data to a remote data store for team collaboration.
- Best practices include setting up remote storage backend (e.g., S3).

### Best Practices:

- Change state using Terraform commands only.
- Use remote storage backend for team sharing.
- Enable state locking to avoid conflicts.
- Backup state file and enable versioning.
- Use separate states for different environments.
- Host Terraform scripts in a Git repository.
- Use continuous integration (CI) for Terraform code.
- Apply infrastructure changes only through a continuous deployment (CD) pipeline.

### Declarative Nature:

- Terraform is declarative, defining the end result, and Terraform figures out how to achieve it.

### Terraform vs. Ansible:

- Terraform is mainly for infrastructure provisioning.
- Ansible is a configuration management tool.

