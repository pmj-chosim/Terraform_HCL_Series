### Hello Everyone! 
### I'm really glad to see you again 😁
## Today, we will set up the environment for using Terraform.

Last time, we covered "what Terraform is" and "what this series is about".  
  
In this post, we’ll focus on installing Terraform on your operating system, with installation methods provided for `Windows`, `Linux`, and `macOS`.

***
<br>

The process of setting up the Terraform environment can be divided into two main steps.  
First, you'll need to download Terraform according to your operating system. Then, we’ll verify that Terraform has been downloaded correctly.  
  
Let’s start with the download. Follow the guide that matches your operating system.  

▶️[Windows Terraform Installation Guide](#Windows)  
▶️[Linux Terraform Installation Guide](#Linux)  
▶️[macOS Terraform Installation Guide](#macOS)  

<br>
 
***

## Windows

#### [1] Terraform Download

You can download the Terraform installation file from HashiCorp's official website.  

🔗 [Terraform Download Page](https://developer.hashicorp.com/terraform/install)

#### [2] Installation Instructions

1. Click the link above to go to the download page.  

1. In the left sidebar, click on  `Windows`.

1. If you're using a 64-bit computer, select `AMD64` to download. (Most computers are 64-bit)
    >  If you're using a 32-bit computer, select `386`.

1. Check your Downloads folder for the ZIP file.
   - You should find a file named something like `terraform_version_windows_amd64.zip`.

1. Extract the ZIP file.
   - You can use the built-in Windows extraction tool or third-party programs like 7-Zip or WinRAR.
   - After extracting, the `terraform.exe` file will be created.

1. Move the `terraform.exe` file to an appropriate directory.
   - Create a folder like `C:\terraform` or `C:\Program Files\Terraform`, then move the `terraform.exe` file there.
  
1. Set up environment variables to make Terraform globally executable.

    (1) **Open Environment Variables**  
       - Type **"Edit the system environment variables"** in the Windows search bar and press Enter.  
       - Under the **"Advanced"** tab, click **"Environment Variables"**.  

    (2) **Edit the Path variable**  
       - In the **"System variables"** section, select **"Path"** and click **"Edit"**.  
       - Click **"New"**, then add the path to the folder where you placed `terraform.exe` (e.g., `C:\terraform` or `C:\Program Files\Terraform`).
   
    


<br>

## Linux  
  
You can easily install Terraform using a package manager. Just copy the command for your specific Linux distribution to get started.
  
#### - Ubuntu/Debian
```hcl
wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform
```
  
#### - CentOS/RHEL 
```hcl
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo
sudo yum -y install terraform
``` 

#### - Fedora  
```hcl
sudo dnf install -y dnf-plugins-core
sudo dnf config-manager addrepo --from-repofile=https://rpm.releases.hashicorp.com/fedora/hashicorp.repo
sudo dnf -y install terraform
```

#### - Amazon Linux
```hcl
sudo yum install -y yum-utils shadow-utils
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
sudo yum -y install terraform
```

#### - Homebrew
```hcl
brew tap hashicorp/tap
brew install hashicorp/tap/terraform
```
<br>


## macOS

You can easily download Terraform using a package manager. Copy the command and install Terraform. 

```hcl
brew tap hashicorp/tap
brew install hashicorp/tap/terraform
```
