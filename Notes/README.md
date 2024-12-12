
# 📘 Terraform Notes, Common Code, and Industry Practices

Welcome to the **Terraform Knowledge Hub**! 🌟  
Explore beginner-friendly notes, frequently used Terraform code snippets, and best practices followed in the industry. 🚀  

![Terraform use case diagram](terraform-architecture-diagram.png)

---

## 📖 Terraform Notes  

### 🌐 What is Terraform?  
- **Terraform** is an open-source Infrastructure as Code (IaC) tool by HashiCorp.  
- It allows you to **define and provision infrastructure** using configuration files.  

### ⚙️ Key Features  
- **Declarative Syntax**: You describe the desired end state, and Terraform figures out the steps to achieve it.  
- **Provider Support**: Works with multiple cloud providers (AWS, Azure, GCP, etc.).  
- **State Management**: Tracks infrastructure state with a state file.  

### 🧩 Core Concepts  
- **Provider**: Connects Terraform with cloud providers (e.g., AWS, Azure).  
- **Resources**: The infrastructure objects (e.g., EC2, S3) you define.  
- **Modules**: Reusable Terraform code blocks.  
- **State File**: Stores the current state of your infrastructure.  

---

## 🛠️ Common Terraform Code Examples  

### Example 1: Provision an AWS EC2 Instance  
```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-12345678"
  instance_type = "t2.micro"

  tags = {
    Name = "ExampleInstance"
  }
}
```  

### Example 2: Create an S3 Bucket  
```hcl
resource "aws_s3_bucket" "example" {
  bucket = "my-example-bucket"
  acl    = "private"
}
```  

### Example 3: Use Variables and Outputs  
```hcl
variable "instance_type" {
  default = "t2.micro"
}

resource "aws_instance" "example" {
  instance_type = var.instance_type
  ami           = "ami-12345678"
}

output "instance_id" {
  value = aws_instance.example.id
}
```  

### Example 4: Use a Module  
```hcl
module "vpc" {
  source  = "terraform-aws-modules/vpc/aws"
  version = "3.0.0"

  name = "my-vpc"
  cidr = "10.0.0.0/16"
}
```  

### Example 5: Create a Security Group  
```hcl
resource "aws_security_group" "example" {
  name        = "example-sg"
  description = "Allow SSH and HTTP"

  ingress {
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }

  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
}
```  

---

## 🏆 Industry Best Practices  

### ✅ Code Practices  
- Use **variables.tf** for all variables and **outputs.tf** for outputs.  
- Keep your code modular by using **modules**.  
- Follow consistent naming conventions.  

### 🔒 Security  
- Never hardcode sensitive information (use environment variables or secret managers).  
- Restrict access using fine-grained security policies.  

### 📂 Project Structure  
```
├── main.tf  
├── variables.tf  
├── outputs.tf  
├── modules/  
│   ├── vpc/  
│   ├── ec2/  
│   └── s3/  
```  

### 🌐 State Management  
- Use **remote state** for team collaboration (e.g., AWS S3 backend).  
- Enable **state locking** to prevent simultaneous changes.  

### 🛠️ Automation  
- Integrate Terraform with CI/CD pipelines.  
- Use **terraform fmt** and **terraform validate** in pre-commit hooks.  

---

## 📝 Additional Resources  
- [Official Terraform Documentation](https://www.terraform.io/docs)  
- [Terraform Registry](https://registry.terraform.io/) for community modules  
- [Best Practices for Terraform](https://learn.hashicorp.com/collections/terraform/best-practices)  

---

Happy Terraforming! 🚀✨  
