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

## 📄 Example Code Snippet

```hcl
provider "aws" {
  region = "us-west-2"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
```

---

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
