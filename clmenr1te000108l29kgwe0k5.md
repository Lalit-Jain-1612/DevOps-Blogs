---
title: "TerraWeek -7 days challenge -Day 1 : Introduction to Terraform and Terraform Basics"
seoTitle: "Introduction to Terraform"
datePublished: Sun Sep 10 2023 18:30:00 GMT+0000 (Coordinated Universal Time)
cuid: clmenr1te000108l29kgwe0k5
slug: terraweek-7-days-challenge-day-1-introduction-to-terraform-and-terraform-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694413573243/7861a779-3677-44e2-8799-1bdc58eee8c2.png
tags: linux, aws, devops, terraform, 90daysofdevops

---

Hi Techies,

Here we are with the new challenge "Terraweek 7 days challenge" to learn Terraform which helps in provisioning the infrastructure.

Over the next 7 days, we'll go on a journey together to learn about Terraform from basics to advanced. Get set for an adventure into Terraform! In our upcoming blog series, we're starting a deep dive into this amazing tool that helps manage computer stuff.

### Introduction of IaC

Infrastructure as code (IaC) tools allow you to manage infrastructure with configuration files rather than through a graphical user interface. IaC allows you to build, change, and manage your infrastructure in a safe, consistent, and repeatable way by defining resource configurations you can version, reuse, and share.

### What is Terraform and how can it help you manage infrastructure as code?

Terraform is HashiCorp's infrastructure as a code tool. It lets you define resources and infrastructure in human-readable, declarative configuration files and manages your infrastructure's lifecycle.

It helps you create, change, and delete your digital stuff (like servers and databases) using code that's why it is called Infrastructure as a code(IaC) service. It's a super handy tool to make your tech world easier to control.

### Why do we need Terraform and how does it simplify infrastructure provisioning?

Earlier to manage the on premise infrastructure was very complicated task. The time taken to launch the instance was too long (**slow deployment**) and it was a very **expensive** operation because for managing every task we had to have different groups(like Field Engineers, System/NW administrators etc..) inside Infrastructure Team as you can see in below ScreenShot. we had a **limited automation** and there was a chance of **human error** too, because of that we started using **Terraform (Infrastructure as a code)** and now just one DevOps engineer can automate the entire task of infrastructure provisioning.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694418028534/599d1801-7110-4673-aa57-548720afa64b.png align="center")

Using Terraform has several advantages that simplifies your infrastructure provisioning over manually managing:

* Terraform can manage infrastructure on multiple cloud platforms.
    
* The human-readable configuration language helps you write infrastructure code quickly.
    
* Terraform's state allows you to track resource changes throughout your deployments.
    
* You can commit your configurations to version control to safely collaborate on infrastructure.
    

### How can you install Terraform and set up the environment for AWS, Azure, or GCP?

following are commands to install Terraform for Linux.

```plaintext
sudo apt-get update && sudo apt-get install -y gnupg software-properties-common

wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg

gpg --no-default-keyring \ --keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg \ --fingerprint

echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

sudo apt update 

sudo apt install terraform
```

If you want to install Terraform in other OS then you can refer -&gt; [Terraform Installation Guide](https://developer.hashicorp.com/terraform/downloads).

### 5 crucial terminologies of Terraform with example

**Resource**: Resources represent the components of your infrastructure that Terraform manages example: servers(EC2), databases(dynamoDB), storage(S3).

**Provider**: A provider is a plugin that Terraform uses to interact with a specific cloud or service. example: AWS, Azure, or Google Cloud.

**Module**: Modules allow you to organize and reuse Terraform configurations. They are like building blocks that encapsulate a set of resources and their configurations. example: Creating a module to provision a VPC and subnets.

**Variable**: Variables are placeholders for values that you can pass into your Terraform configurations, making them flexible and reusable. example:

```plaintext
variable "aws_region" {
  description = "The AWS region to deploy resources."
  default     = "us-west-2"
}
```

**State**: State is useful to keep a record of why and how infrastructure was created at the first place. It is Used to improve performance, dependency management, etc

In the next blog post we will be learning about HCL language, syntax, and writing Terraform configurations using HCL syntax. [Reference video](https://www.youtube.com/watch?v=965CaSveIEI)

Thanks for reading😊...!

Happy Learning😄