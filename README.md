# Terraform Interview Q&A (200 Questions)

This repository contains **200+ professional Terraform Interview Questions & Answers**, complete with examples and explanations. It is designed to help Cloud Engineers / DevOps Engineers prepare for real-world interviews.

---

## 📘 Overview

This repo covers:

* Terraform Basics
* Providers, Modules, State Management
* Workspaces & Environments
* Provisioners, Data Sources
* Loops, Conditionals, Locals
* Backend, Security, Lock Files
* Terraform Cloud / Enterprise
* AWS Examples (EC2, VPC, S3, SG, Secrets Manager)

---

## 📂 Repository Structure

```
📁 terraform-interview-questions
│
├── 📄 README.md            # Main documentation
├── 📄 QUESTIONS.md         # All 200 Q&A
├── 📁 examples             # Terraform code examples
│   ├── provider-example.tf
│   ├── ec2-example.tf
│   ├── vpc-module-example.tf
│   └── secrets-example.tf
└── 📁 diagrams             # Optional architecture diagrams
```

---

## 📄 How to Use This Repo

* Use `QUESTIONS.md` for interview preparation.
* Explore `examples/` to understand real-world Terraform configuration.
* Download, clone, or fork the repo for personal reference.

---

## 🚀 Key Terraform Topics Included

* **State Management (local & remote)**
* **IAM, EC2, VPC, SG provisioning**
* **Terraform Cloud/Enterprise usage**
* **Conditional logic, loops & dynamic blocks**
* **Importing existing infra**
* **Secrets handling & encryption**
* **Backend configuration (S3, Consul, Remote)**

---

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

(Commands and short answers cover `terraform plan`, `apply`, `destroy`, variables, outputs, workspaces, remote state, import, data sources, provisioners, secrets management, backend configuration, conditionals, validate, fmt, count vs for_each, loops, locals, taint, module versioning, Terraform Registry, dry run, terraform state and rename, workspace usage, debugging, local vs remote backends, provider versioning, refresh, graph generation, lifecycle blocks.)

*The full set of Q&A 11–40 is included in the QUESTIONS.md file inside the repo.*

---

## Advanced Topics (41–100)

(Lifecycle blocks, ignore_changes, import, module outputs, dynamic blocks, maps, count parameter, Terraform Cloud/Enterprise, backends, formatting, lock files, workspaces, secrets, console, data sources, state mv, conditionals, taint, provider versioning, refresh, graphing and validation.)

*The full set of Q&A 41–100 is included in the QUESTIONS.md file inside the repo.*

---

## Remaining Questions (101–200)

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


## ⭐ Contribution

Feel free to contribute:

* Add more interview questions
* Add Terraform examples
* Improve formatting or fix typos

---

## 🙌 Support

If this repository helps in your interview preparation, **star the repo ⭐** and share it with others!

---

## 🔗 Connect

For more DevOps & AWS content, subscribe to:
**Tech with Burhan (YouTube)** 🎥

---

## 📄 LICENSE

This project is open-source and available under the MIT License.
