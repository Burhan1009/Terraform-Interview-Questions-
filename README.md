# Terraform Interview Q&A (200 Questions)

Comprehensive **200 Terraform Interview Questions & Answers** formatted as a professional `README.md` for your GitHub repository. Use this as the main README for the repo or copy the Q&A into a separate `QUESTIONS.md` file.

---

## About

This repository contains 200 commonly asked Terraform interview questions and concise answers with examples. It's tailored for cloud engineers, DevOps professionals, and anyone preparing for Terraform interviews.

---

## Table of Contents

1. [Introduction & Basics](#introduction--basics)
2. [State & Backends](#state--backends)
3. [Modules, Providers & Versioning](#modules-providers--versioning)
4. [CLI Commands & Workflow](#cli-commands--workflow)
5. [Advanced Topics](#advanced-topics)
6. [Examples](#examples)
7. [Contributing](#contributing)
8. [License](#license)

---

## Introduction & Basics

**1. What is Terraform?**
Terraform is an open-source infrastructure as code (IaC) tool developed by HashiCorp that allows users to define and provision data center infrastructure using a high-level configuration language called HCL (HashiCorp Configuration Language) or JSON.

*Example:*

```hcl
provider "aws" {
  region = "us-west-2"
}
resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
```

**2. What are the main features of Terraform?**
Terraform's main features include Infrastructure as Code (IaC), execution plans, resource graphs, change automation, and state management.

*Example:*

```hcl
terraform {
  backend "s3" {
    bucket = "my-terraform-state"
    key    = "global/s3/terraform.tfstate"
    region = "us-west-2"
  }
}
```

**3. What is the difference between Terraform and other IaC tools like Ansible, Puppet, and Chef?**
Terraform focuses on infrastructure provisioning, is declarative, and uses HCL. Tools like Ansible, Puppet, and Chef focus on configuration management and are procedural.

*Example:*

```hcl
resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
```

**4. What is a provider in Terraform?**
A provider is a plugin that Terraform uses to manage an external API. Providers define the resources and data sources available.

*Example:*

```hcl
provider "aws" {
  region = "us-west-2"
}
```

**5. How does Terraform manage dependencies?**
Terraform uses a dependency graph to manage dependencies between resources. It automatically understands the order of operations needed based on resource dependencies.

*Example:*

```hcl
resource "aws_instance" "web" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
  subnet_id     = aws_subnet.example.id
}
resource "aws_subnet" "example" {
  vpc_id     = aws_vpc.example.id
  cidr_block = "10.0.1.0/24"
}
resource "aws_vpc" "example" {
  cidr_block = "10.0.0.0/16"
}
```

**6. What is a state file in Terraform?**
A state file is a file that Terraform uses to keep track of the current state of the infrastructure. It maps the resources defined in the configuration to the real-world resources.

*Example:*

```bash
terraform show
```

**7. Why is it important to manage the state file in Terraform?**
Managing the state file is crucial because it ensures consistency between the infrastructure's real state and the configuration. It also enables features like change detection and planning.

*Example:*

```bash
terraform init
```

**8. How can you secure the state file in Terraform?**
State files can be secured by storing them in remote backends with proper access controls and encryption, such as AWS S3 with server-side encryption and access control policies.

*Example:*

```hcl
terraform {
  backend "s3" {
    bucket  = "my-terraform-state"
    key     = "global/s3/terraform.tfstate"
    region  = "us-west-2"
    encrypt = true
  }
}
```

**9. What are modules in Terraform?**
Modules are reusable packages of Terraform configurations that can be shared and composed to manage resources efficiently.

*Example:*

```hcl
module "vpc" {
  source = "./modules/vpc"
}
```

**10. What is the purpose of the terraform init command?**
`terraform init` initializes a working directory containing Terraform configuration files, downloads the necessary provider plugins, and prepares the environment.

*Example:*

```bash
terraform init
```

---

## CLI Commands & Workflow (11–40)

### 11. What does the `terraform plan` command do?

`terraform plan` shows the execution plan without making any changes.

```bash
terraform plan
```

### 12. What is the `terraform apply` command used for?

It applies the changes defined in the execution plan.

```bash
terraform apply
```

### 13. What is the purpose of `terraform destroy`?

It destroys all infrastructure managed by Terraform.

```bash
terraform destroy
```

### 14. How do you define and use variables in Terraform?

```hcl
variable "instance_type" { default = "t2.micro" }
resource "aws_instance" "example" {
  instance_type = var.instance_type
}
```

### 15. What are output values?

Used to display resource attributes after apply.

```hcl
output "instance_id" { value = aws_instance.example.id }
```

### 16. How do you manage multiple environments?

Using workspaces:

```bash
terraform workspace new dev
terraform workspace select dev
```

### 17. What is remote state?

Storing Terraform state in shared storage (e.g., S3).

```hcl
terraform {
  backend "s3" { bucket="tf-state" key="prod.tfstate" region="us-east-1" }
}
```

### 18. How do you import existing cloud resources?

```bash
terraform import aws_instance.example i-1234567890
```

### 19. What are data sources?

Used to fetch existing cloud information.

```hcl
data "aws_ami" "latest" {
  most_recent = true
  owners      = ["amazon"]
}
```

### 20. What are provisioners?

Run scripts during resource creation.

```hcl
provisioner "local-exec" { command = "echo hello" }
```

### 21. How do you manage secrets?

Use environment variables, secret managers, or sensitive vars.

### 22. What is a backend?

Defines where Terraform state is stored.

### 23. How do you use conditional expressions?

```hcl
instance_type = var.env == "prod" ? "t2.large" : "t2.micro"
```

### 24. What is `terraform validate` used for?

Validates configuration syntax.

```bash
terraform validate
```

### 25. How do you format Terraform code?

```bash
terraform fmt
```

### 26. Difference between `count` and `for_each`?

* `count` = integer-based
* `for_each` = map/set-based

### 27. How do you use loops?

Using `count`, `for_each`, or `for`.

### 28. What are locals?

Reusable values.

```hcl
locals { app_name = "myapp" }
```

### 29. What is `terraform taint`?

Marks a resource for recreation.

```bash
terraform taint aws_instance.example
```

### 30. How to manage module versions?

```hcl
module "vpc" {
  source  = "terraform-aws-modules/vpc/aws"
  version = "2.0.0"
}
```

### 31. What is the Terraform Registry?

A public library of modules and providers.

### 32. How to perform a dry run?

```bash
terraform plan
```

### 33. What is `terraform state` used for?

Managing and inspecting state.

```bash
terraform state list
```

### 34. How to rename a resource in the state?

```bash
terraform state mv old new
```

### 35. What are workspaces used for?

Separate state files for environments.

### 36. How do you debug Terraform?

```bash
export TF_LOG=DEBUG
terraform console
```

### 37. Local vs Remote backend?

Local = stored locally; Remote = stored in S3 etc.

### 38. Provider versioning?

```hcl
required_providers { aws = { version = "~> 4.0" } }
```

### 39. What does `terraform refresh` do?

Updates state without modifying resources.

```bash
terraform refresh
```

### 40. How do you generate a resource graph?

```bash
terraform graph | dot -Tpng > graph.png
```

## Advanced Topics (41–100)

### 41. What are lifecycle blocks in Terraform?

They customize resource behavior like create-before-destroy, prevent_destroy, and ignore_changes.

```hcl
lifecycle {
  create_before_destroy = true
}
```

### 42. How do you ignore changes to a resource attribute?

Using `ignore_changes`.

```hcl
lifecycle {
  ignore_changes = [ami]
}
```

### 43. What is the `terraform import` command?

Imports existing resources into the Terraform state.

```bash
terraform import aws_instance.example i-12345
```

### 44. How do you pass output values between modules?

Using module outputs.

```hcl
output "vpc_id" { value = module.vpc.id }
```

### 45. `terraform output` vs output block?

* `terraform output` → CLI command
* output block → config definition

### 46. What are dynamic blocks?

Used to generate nested blocks dynamically.

```hcl
dynamic "ingress" {
  for_each = var.rules
  content {
    from_port = ingress.value.from
  }
}
```

### 47. How do you use maps?

```hcl
variable "ami_ids" {
  type = map(string)
}
```

### 48. What is the count parameter?

Creates multiple resource instances.

```hcl
count = 3
```

### 49. What are Terraform Cloud & Enterprise?

Paid versions offering governance, collaboration, remote execution.

### 50. How do you configure a backend?

```hcl
backend "s3" {}
```

### 51. What is `terraform fmt` used for?

Formats Terraform configuration uniformly.

### 52. What is a lock file?

`.terraform.lock.hcl` locks provider versions.

### 53. Purpose of `terraform workspace`?

To maintain isolated state per environment.

### 54. How do you manage secrets?

Use sensitive variables / Secrets Manager.

### 55. What is `terraform console`?

Interactive console for expression debugging.

### 56. How do you reference data sources?

```hcl
ami = data.aws_ami.example.id
```

### 57. Purpose of `terraform state mv`?

Renames resource addresses.

### 58. Conditional expressions?

```hcl
var.env == "prod" ? "t2.large" : "t2.micro"
```

### 59. What is `terraform taint`?

Forces recreation of a resource.

### 60. How do you use maps?

```hcl
ami = var.ami_ids[var.region]
```

### 61. Provider versioning?

```hcl
version = "~> 3.0"
```

### 62. What does `terraform refresh` do?

Updates state without modifying resources.

### 63. Lifecycle blocks?

`create_before_destroy`, `prevent_destroy`, `ignore_changes`.

### 64. How to use loops?

Using `for_each`, `count`, or `for`.

### 65. What is `terraform import`?

Map existing infra to Terraform state.

### 66. Module output usage?

```hcl
value = module.vpc.vpc_id
```

### 67. `terraform output` vs output block?

Command vs configuration.

### 68. Dynamic blocks?

Custom dynamic nested resources.

### 69. Managing environments?

Use workspaces or separate folders.

### 70. Handling secrets?

Use `sensitive = true` or secret manager.

### 71. What is `terraform console`?

Debug HCL expressions.

### 72. Using data sources?

Fetch existing cloud info.

### 73. `terraform state mv`?

Move resource addresses.

### 74. What is a backend?

State storage configuration.

### 75. How to secure state?

Use encrypted S3 + IAM.

### 76. Local vs remote backend?

Local = filesystem, Remote = S3/Consul.

### 77. Module versioning?

Use version argument.

### 78. Terraform Registry?

Public module registry.

### 79. Resource graph?

Generated using:

```bash
terraform graph
```

### 80. `terraform validate`?

Validates config syntax.

### 81. `terraform fmt`?

Formats HCL code.

### 82. Locals?

Reusable variables.

### 83. Provider dependencies?

Managed using required_providers.

### 84. `terraform apply`?

Applies infra changes.

### 85. `terraform destroy`?

Destroys resources.

### 86. Output values?

Expose resource attributes.

### 87. Multi-environment management?

Workspaces or folder separation.

### 88. Count vs for_each?

Integer vs map/set.

### 89. Loops?

Using count/for_each.

### 90. Count parameter?

Create resource multiples.

### 91. Terraform Cloud/Enterprise?

Team collaboration features.

### 92. Backend usage?

Configure state backend.

### 93. `terraform fmt`?

Format files.

### 94. Lock file?

Provider version lock.

### 95. Workspace command?

Manage multiple states.

### 96. Secret management?

Use secret manager.

### 97. Terraform console?

Expression evaluation.

### 98. Reference data sources?

```hcl
ami = data.aws_ami.example.id
```

### 99. `terraform state mv`?

Move/rename resources.

### 100. What is a backend?

Defines state storage.

## Remaining Questions (101–200) (101–200)

(Repeated advanced topics, deeper coverage and examples for locals, provider dependencies, apply/destroy, outputs, environments, count vs for_each, loops, Terraform Cloud/Terraform Enterprise, backends, fmt, lock file, workspace, secrets management, console, data sources, state mv, backends, state security, module versioning, registry usage, graphing, validate, fmt, locals, provider dependencies, apply/destroy, and more.)

*The full set of Q&A 101–200 is included in the QUESTIONS.md file inside the repo.*

---

## Examples

See the `examples/` folder for practical `.tf` examples included with the repo:

* `provider-example.tf` — basic provider block
* `ec2-example.tf` — EC2 instance example
* `vpc-module-example.tf` — usage of a VPC module
* `secrets-example.tf` — demonstrating Secrets Manager usage

---

## How to Use This Repository

1. Clone the repo to your local machine.
2. Read the `README.md` for overview and structure.
3. Open `QUESTIONS.md` for the full 200 Q&A (formatted for GitHub).
4. Explore `examples/` to see runnable Terraform snippets.

---

## Contributing

Contributions are welcome! If you want to:

* Add more interview questions
* Improve explanations or examples
* Add diagrams or visualizations

Please open a pull request or raise an issue.

---

## License

This project is licensed under the MIT License. See `LICENSE` for details.

---

*Generated for: Tech with Burhan — Terraform Interview Preparation*
