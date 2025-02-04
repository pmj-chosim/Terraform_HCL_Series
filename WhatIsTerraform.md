## Hello!  
# Have you ever heard of *Terraform*?  
This post will introduce you to ***Terraform***.  

### *Have you ever experienced a situation where you forgot to delete a cloud resource, and as a result, you were charged a hefty fee?* 

Thanks to ***Terraform***, I no longer worry about such issues. With ***Terraform***, you can manage your resources as code, which allows you to automatically clean up unnecessary resources.  

<br>
  
This blog post is part of a series, and more content will follow in the future.  
The goal of this series is to help you **build foundational skills for provisioning Azure services using Terraform**.  

<br> 
  
Here’s the table of contents.  
  
### Table of Contents  
~~
  


<br> <br>    
As you can see from the table of contents,
### This post covers the essential things you need to know in order to 
### use ***Terraform*** to provision services on Azure.    

<br> <br>
Let’s dive into Terraform and explore the topics step by step.    
<br>
<br>
***
## 1. What is Terraform?

***Terraform*** is a tool for managing infrastructure as code (IaC: Infrastructure as Code).  
By using ***Terraform***, you can define and automate the deployment, updates, and versioning of infrastructure as code.  
Additionally, it offers the advantage of managing resources consistently across various cloud service providers (such as AWS, Azure, Google Cloud, etc.).

***Terraform*** enables infrastructure to be codified, making it reproducible, version-controlled, and facilitating efficient collaboration. Furthermore, software development processes, such as code reviews, can be applied to infrastructure management as well.

***
  
## 2. Advantages of Using Terraform  

Using Terraform instead of creating Azure infrastructure via the UI offers several benefits.  

For example:  

- **Consistency**: When configuring resources manually via the UI, mistakes can occur. With Terraform, you can repeatedly deploy the same configuration defined in code, preventing misconfigurations or omissions.  
- **Version Control**: Terraform code can be stored in a version control system like Git. This allows you to track changes and collaborate with team members efficiently.  
- **Automation**: It reduces the hassle of manually creating and updating resources. Terraform automatically tracks and manages all changes.  

***
To provision infrastructure on Azure using Terraform, there is one essential thing you need to learn:  
You must understand **HCL (HashiCorp Configuration Language)**.

## 3. What is HCL?  

HCL (HashiCorp Configuration Language) is the primary language of Terraform, allowing you to define and manage infrastructure using **declarative syntax**.  

### - Why use HCL?  
With HCL, you can automatically provision Azure resources without using the UI. Instead of manually configuring each resource, you define the desired state in code, and Terraform ensures that the infrastructure matches your configuration.  

### - How is HCL different from other programming languages?  
  
(1) **Declarative**  
While HCL is classified as a programming language, it differs from traditional languages like Python or Java.  
The key distinction is that HCL is **declarative**. Instead of writing step-by-step instructions on *how* to create resources, you describe *what* the final infrastructure should look like.  
Terraform then automatically manages resource states and applies necessary changes to match the desired configuration.   

(2) **Block-Based**  
Additionally, HCL is **block-based**, making it easy to structure and organize infrastructure definitions.  

> ## What is a block?  
> Think of **blocks** in HCL like **building blocks in LEGO**. Each block serves a specific function, and by stacking different blocks together, you can build a complete infrastructure—just like assembling LEGO pieces to create a structure.  
> 
> Each block consists of a **type** (e.g., `resource`, `provider`) and a **configuration** that defines its details.  
>
> For example:  
> - A **resource** block is like an individual LEGO piece that represents a cloud resource (e.g., a virtual machine, database, or storage account).  
> - A **provider** block is like the foundation that connects Terraform to a specific cloud service (e.g., Azure, AWS).   

<br>
  
### - Similarities with other programming languages  
Despite its differences, HCL shares some common programming concepts, such as:  
- **Conditional statements** (if-else logic)  
- **Loops** (iteration over lists or maps)  
- **Variables** for dynamic configuration  

<br>
These features make HCL flexible and reusable, helping developers efficiently manage infrastructure as code.  
<br> <br>  

***
  
This post introduces the essential **blocks** to know when provisioning an Azure environment using Terraform. Each block plays a crucial role in Terraform configurations, and understanding them helps in using Terraform more effectively.  

Future posts will cover each block in more detail, providing additional insights as part of a series.
