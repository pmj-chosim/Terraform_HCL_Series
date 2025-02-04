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

HCL is the primary language of Terraform, enabling you to define and manage infrastructure using declarative syntax.  

> ### What is declarative syntax?  
> Declarative syntax allows you to describe the desired state of infrastructure rather than specifying step-by-step procedures to create it.  
> 
> Additionally, HCL plays a crucial role in managing infrastructure as code, making the process more efficient and maintainable.  

***
