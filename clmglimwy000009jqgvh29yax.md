---
title: "TerraWeek Day 2 : HCL syntax, variables, datatypes, expressions in HCL & Terraform configuration"
datePublished: Mon Sep 11 2023 18:30:00 GMT+0000 (Coordinated Universal Time)
cuid: clmglimwy000009jqgvh29yax
slug: terraweek-day-2-hcl-syntax-variables-datatypes-expressions-in-hcl-terraform-configuration
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694526652426/fcc241f3-370f-42fc-b2f8-0de9920ec7e0.png
tags: linux, aws, terraform, 90daysofdevops, terraweekchallenge

---

### Introduction to HCL

HCL stands for HashiCorp Configuration Language. HCL is designed to be both human-readable and machine-friendly, making it well-suited for writing infrastructure as code (IaC) and configuration files.

In the context of Terraform, HCL is used to write the infrastructure configuration, where you define the desired state of your infrastructure resources, their relationships, and their attributes in a clear and concise manner. HCL files typically have a `.tf` extension.

### Basic syntax of HCL

```plaintext
<block> <parameters> {
    key1 = value1             //arguments
    key2 = value2
}
```

The Terraform language syntax is built around two key syntax constructs: arguments and blocks.

### HCL blocks, parameters, and arguments

* block is a container for other content and An argument assigns a value to a particular name.
    
* The identifier before the equals sign is the argument name, and the expression after the equals sign is the argument's value.
    
    ```plaintext
    resource "local_file" "demo" {
        filename = "/roots/demo.txt"
        content = "This is sample file"
    }
    ```
    
    Here,
    
* resource = block
    
* local\_file = resource type (local : provider, file : type)
    
* “demo” = resource name
    

You need to define parameters and its corresponding arguments within blocks. Parameter specifies a resource type and arguments provide the values for those parameters. In the example above, filename and content are parameters, while "/roots/demo.txt" and "This is sample file" are their respective arguments.

### Different types of resources and data sources available in Terraform

Terraform provides two primary types of objects to interact with infrastructure: **resources** and **data sources**. These are fundamental to managing your infrastructure as code. Let's explore both:

**Resources:**

**1\. Compute Resources:**

* These resources allow you to create and manage virtual machines, containers, and other compute instances.
    
    example: `aws_instance` (EC2)
    

**2\. Networking Resources:**

* Networking resources enable you to define and manage networking components such as virtual networks, subnets, and load balancers.
    
    examples: `aws_vpc` (AWS Virtual Private Cloud)
    

**3\. Storage Resources:**

* Storage resources are used to create and manage storage solutions like databases, object storage, and disks.
    
    examples: `aws_s3_bucket` (S3 bucket)
    

**4\. Identity and Access Management (IAM) Resources:**

* IAM resources allow you to define roles, users, and permissions for controlling access to resources.
    
    examples: `aws_iam_user` (AWS IAM user)
    

**5\. Data Resources:**

* Data resources let you retrieve information from external sources, such as existing infrastructure or data sources.
    
    examples: `aws_ami` (AWS Amazon Machine Image)
    

**6\. DNS Resources:**

* DNS resources help you manage domain names and DNS records.
    
* Examples: `aws_route53_zone` (Route 53)
    

**7\. Monitoring and Logging Resources:**

* These resources allow you to set up monitoring, logging, and alerting for your infrastructure.
    
    examples: `aws_cloudwatch_alarm` (AWS CloudWatch alarm)
    

**8\. Security and Compliance Resources:**

* Security and compliance resources help you enforce security policies and compliance standards.
    
    examples: `aws_security_group` (AWS security group)
    

**Data Sources:**

1. **Provider Data Sources**: Data sources used to fetch information about resources that already exist in the provider's environment.Examples: [data.aws](http://data.aws)\_vpc (to fetch information about an existing VPC in AWS)
    
2. **External Data Sources**: Data sources that allow Terraform to query external systems or APIs for information.Examples: data.external (for running arbitrary commands and capturing their output)
    
3. **Computed Data Sources**: Data sources that provide computed or derived data within the Terraform configuration.Examples: data.template\_file (for rendering templates within Terraform)
    
4. **State Data Sources**: Data sources that allow you to access information stored in the Terraform state.Examples: data.terraform\_remote\_state (for fetching outputs from a remote state file
    

### Understand variables, data types, and expressions in HCL

* **Create a** `variables.tf` **file and define a variable**
    
    ```plaintext
    variable "fileContent" {
        default = "This is a first file created in Terraform"
    }
    ```
    
    here we have defined a variable of type string with name content and having the default value "This is a first file created in Terraform
    
* ".
    
* Let's Use the variable in a [main.tf](http://main.tf) file to create a "local\_file" resource
    
    ```plaintext
    resource "local_file" "demofile" {
        filename "/root/demo.txt"
        content = var.fileContent
    }
    ```
    
    here you can see we have used the "fileContent" variable in a resource definition to specify the content of a local file using dott(.) like structure and this method is called Interpolation **(Note: Don't use double inverted comma " "** while **interpolation)** otherwise you will end up with an error.
    
* **Execution of Infrastructure**
    
* Init -&gt; plan -&gt; apply
    
* **terraform init** : This command will scan your `.tf` files in that folder and install all the required automation things.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694538535375/b9c5c660-6e53-4a12-b8b7-229e96b4c272.png align="center")
    
* **terraform plan** : This command will create an execution plan for terraforming, the things that will be installed, the names, and the properties added.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694538582558/ef47c28e-eb2a-44df-9b5e-df3e8120596b.png align="center")
    
* **terraform apply** : The actual execution and automation happen in this command.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694538617617/055b277e-e646-4867-a878-ff47eb85c7f3.png align="center")
    

after applying all these three commands you will see a `demo.txt` file will generate automatically.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694538646418/652daf99-d63a-4d56-9c9c-fa8d566fa646.png align="center")

### Terraform configurations using HCL syntax

* **Add** `required_providers` **to your configuration, such as Docker or AWS**
    

Terraform doesn't have docker aws, and other providers preinstalled, we have to insatll them separately and to install the plugins we have to use **provider block.**

To add the required providers we should create a separate file `terraform.tf` and write a terraform block

**Step 1: Create a Terraform Configuration File**

```plaintext
terraform {
    required_providers {
        docker = {
            source  = "kreuzwerker/docker"
            version = "3.0.2"
        }    
    }
}
```

**Step 2: Initialize the Configuration**

```plaintext
terraform init
```

Terraform will identify the required providers and ensure they meet the specified version requirements. If they are not already installed, Terraform will download them.

**Step 3: Validate the Configuration**

```plaintext
terraform validate
```

This command checks your configuration file for correctness and reports any errors or warnings.

Thanks for reading😊....!

Happy learning