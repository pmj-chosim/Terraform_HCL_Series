# Getting Started with Terraform Blocks: Building Azure Made Easy
## < First Chapter: What is Terraform? >

***
  

## Hello!  
# Have you ever heard of *Terraform*?  
This post will introduce you to ***Terraform***.  

### *Have you ever experienced a situation where you forgot to delete a cloud resource, and as a result, you were charged a hefty fee?* 

Thanks to ***Terraform***, I no longer worry about such issues. With ***Terraform***, you can manage your resources as code, which allows you to automatically clean up unnecessary resources.  

<br>
  
This blog post is part of a series, and more content will follow in the future.  
The goal of this series is to help you **build foundational skills for provisioning Azure services using Terraform**.  

<br>  

***
  
Here’s the table of contents for this post.  
  
### Table of Contents  
[1. What is Terraform?](#1-what-is-terraform)  
[2. Advantages of Using Terraform](#2-advantages-of-using-terraform)  
[3. What is HCL?](#3-what-is-hcl)  
[4. Common Structure of Terraform Blocks](#4-common-structure-of-terraform-blocks)  
[5. Block Types in Terraform](#5-block-types-in-terraform)

***

<br> <br>    
As you can see from the table of contents,
### This post and series covers the essential things you need to know in order to 
### use ***Terraform*** to provision services on Azure.    

<br> <br>
Let’s dive into Terraform and explore the topics step by step.    
<br>
<br>
***
## 1. What is Terraform?

***Terraform*** is a tool that helps you set up and manage your servers, networks, and other resources using code, instead of clicking through a user interface. Imagine writing a recipe for your infrastructure—when you run the code, ***Terraform*** automatically follows it to create, update, or remove the resources you need.

With ***Terraform***, you can manage resources across different cloud platforms like AWS, Azure, or Google Cloud Platform, all with the same code. This makes it easier to handle everything consistently, no matter where your resources are hosted.

Because your infrastructure is written as code, you can save it, share it, and keep track of changes. This makes it more reliable and much easier to manage in the long run.

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
The key distinction is this HCL is **declarative**. Instead of writing step-by-step instructions on *how* to create resources, you describe *what* the final infrastructure should look like.  
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

<br> 

The following content introduces the essential **blocks** to know when provisioning an Azure environment using Terraform.   
Each block plays a crucial role in Terraform configurations, and understanding them helps in using Terraform more effectively.   

Future posts will cover each block in more detail, providing additional insights as part of a series.  
  
***
  
## 4. Common Structure of Terraform Blocks    
  
Blocks in Terraform typically follow a general pattern:    
> **Not All Blocks follow this pattern

```hcl
<Block Type> <Resource Type> <Resource Name> {
  <Attribute> = <Value>
}
```

(1) **Block Type**
- Defines the role of the block.
- Examples: `resource`, `provider`, `variable`, etc.
  
(2) **Resource Type**  
- Specifies the type of resource being defined.
- Examples: `azurerm_storage_account`, `aws_s3_bucket`, `google_compute_instance`, etc.
  
(3) **Resource Name (Local Identifier)**  
- Name it as you want to name!
- provides a unique name or identifier for the resource within the configuration.
- This helps in referring to the resource elsewhere in the configuration.
- Example: `"example"` in `azurerm_storage_account "example"`.

(4) **Attributes & Values**
- Defines the properties and configurations for the resource.
- Each attribute is assigned a value that determines the resource's configuration.
- Examples:
  ```hcl
  name = "mystorageaccount"  
  location = "East US"  
  account_tier = "Standard"  
  account_replication_type = "LRS"
  ```
  
#### - Example:
```hcl
resource "azurerm_storage_account" "storageaccount1" {
  name                     = "mystorageaccount"
  location                 = "East US"
  account_tier             = "Standard"
  account_replication_type = "LRS"
}
```
> - Block Type: resource
> - Resource Type: azurerm_storage_account
> - Resource Name: storageaccount1
> - Attributes: <br>
>  name = "mystorageaccount" <br>
>  location = "East US" <br>
>  account_tier = "Standard" <br>
>  account_replication_type = "LRS"

<br>  <br>
    
***
 <br> <br>
There are various types of blocks in Terraform. 
Now, let's explore the individual blocks.  

<br>  
   
## 5. Block Types in Terraform   
  <br>
  
### (1) Provider Block 
A **Provider Block** is where you configure the services or tools that Terraform will use to manage resources. For example, when managing cloud services, you can use providers like AWS, Azure, or GCP. In addition to cloud services, you can also manage other services like DNS providers, CI/CD tools, virtualization platforms, and more. 
  
Since Azure resources will be provisioned throughout this series, the provider will consistently be set to Azure.
```hcl
provider "azurerm" {
  features {}
}
```
- Block Type: `provider`
- Resource Type: `azurerm` (Azure Resource Manager provider)
- Resource Name: Not typically required, as the provider block applies globally.
  
***Explanation:***   
> - The Provider Block typically includes settings like authentication details (API keys, credentials, etc.), region, and other provider-specific configurations.  
> - Provider Initialization: You should run `terraform init` before terraform apply to initialize the provider and download the necessary plugins.
> - `terraform init` command would be explained in next post.
 
 <br> <br>  
   
### (2) Resource Block  
A **Resource Block** is used to define and manage infrastructure resources such as virtual machines, storage accounts, and networks.  
```hcl
resource "azurerm_storage_account" "example1" {
  name                     = "mystorageaccount"
  location                 = "East US"
  account_tier             = "Standard"
  account_replication_type = "LRS"
}
```

- Block Type: `resource`
- Resource Type: `azurerm_storage_account`
- Resource Name: `example1`


***Explanation***:
  > The resource type differs depending on the Cloud Service Provider (CSP) and must be found in the provider's documentation.
  > For example, in Azure, the resource type for a storage account is azurerm_storage_account, but the name will be different in AWS or GCP.
  > Terraform uses the exact naming conventions defined by the provider, so it is crucial to reference the correct resource type according to the CSP you are using.
  
 <br> <br>  

### (3) Variable Block
A **Variable Block** is used to define variables that can be used throughout your Terraform configuration. Variables make your setup more flexible because their values can be set dynamically at runtime or passed in via the command line. It's like declaring a variable in a program, where you can set the value once and change it when needed.
```hcl
variable "region" {
  description = "The region where resources will be created"
  type        = string
  default     = "East US"
}
```
- Block Type: `variable`
- Resource Name: `region`
- Attributes: `description`, `type`, `default`

 <br> <br> 
 
### (4) Data Block
A **Data Block** is used to fetch information about existing resources that were created outside of your Terraform configuration.   
For example, it can retrieve data about a virtual machine created 3 years ago or a VNet created yesterday. You can then use this data to configure new resources or reference these existing resources in your Terraform setup.
```hcl
data "azurerm_virtual_network" "ex" {
  name                = "myvnet"
  resource_group_name = "my-resource-group"
}
```
- Block Type: `data`
- Resource Type: `azurerm_virtual_network`
- Resource Name: `ex`

 <br> <br>  
 
### (5) Module Block

 Think of a Module Block like a function in programming.

When you write a function, you don't have to rewrite the same code every time you want to perform a specific task. 
Instead, you create the function once, and then you can use (call) it whenever you need.  
  
Similarly, in Terraform, you create a module to define a set of resources (like a network, a database, etc.) once. Then, instead of writing the same configuration again in different places, you simply call the module whenever you need it.
 ```hcl
module "network_us" {
  source              = "./modules/network"
  location            = "East US"
  address_space       = ["10.0.0.0/16"]
  resource_group_name = "rg-us"
  subnet_address_prefixes = ["10.0.1.0/24"]
}
```

 
 <br> <br>  
 
### (6) Output Block
An **Output Block** is used to display specific information after Terraform finishes running, such as resource IDs or IP addresses. It's similar to how a function returns a value—the output block allows you to pass specific values (like a resource's ID or IP address) that may be required for other modules or external systems.
```hcl
output "vm_ip" {
  value = azurerm_virtual_machine.example.private_ip
}
```
- Block Type: `output`
- Resource Name: `vm_ip`
- Attributes: `value`

***Explanation:***
> In this example, output `"vm_ip"` will display the IP address of the virtual machine after Terraform finishes its execution. This value can then be used by
> other modules or systems.

<br>

***
<br> <br>


There are many more block types, but in this series, we'll dive deep into these six blocks. In the next post, let's explore each of these blocks in detail.

Thank you for reading through the post! See you in the next one~



