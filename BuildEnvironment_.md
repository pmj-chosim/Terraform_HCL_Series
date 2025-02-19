테라폼 환경을 설치해 보자.

운영체제에 알맞게 설치를 해라. Windows와 Linux, macOS에 설치하는 방법을 제공한다.

<br>

## Windows

#### 1. Terraform 다운로드

Terraform 설치 파일은 HashiCorp 공식 사이트에서 다운로드할 수 있습니다.

🔗 [Terraform 다운로드 페이지](https://developer.hashicorp.com/terraform/install)

#### 다운로드 방법

1. 위의 링크를 클릭하여 다운로드 페이지로 이동합니다.

1. 좌측 배너에서 Windows를 클릭합니다.

1. 64bit 컴퓨터인 경우 `AMD64`를 선택하여 다운로드합니다. (대부분의 컴퓨터는 64bit) 
    >  32bit 컴퓨터인 경우 `386`을 선택합니다.

1. 다운로드된 ZIP 파일을 확인합니다.
   - 다운로드 폴더에서 terraform_버전_windows_amd64.zip과 같은 이름의 파일을 찾습니다.

1. ZIP 파일의 압축을 해제합니다.
   - Windows 기본 제공 기능으로 압축을 풀거나, 7-Zip, WinRAR 같은 프로그램을 사용할 수도 있습니다.
   - 압축을 푼 후, terraform.exe 파일이 생성됩니다.

1. `terraform.exe` 파일을 적절한 경로에 이동시킵니다.
   - `C:\terraform` 또는 `C:\Program Files\Terraform` 같은 폴더를 만든 후, `terraform.exe`를 이동시킵니다.
  
1. 환경 변수를 설정하여 Terraform을 시스템 전역에서 실행 가능하게 만듭니다.

    (1) **환경 변수 창 열기**  
       - Windows 검색에서 **"시스템 환경 변수 편집"** 입력 후 실행  
       - `"고급"` 탭에서 `"환경 변수"` 클릭  
    
    (2️) **Path 변수 수정**  
       - `"시스템 변수"` 목록에서 `"Path"` 선택 후 `"편집"` 클릭  
       - `"새로 만들기"` 버튼을 누르고 Terraform이 있는 폴더 경로 입력 (예: `C:\terraform`)  
    


<br>

## Linux  
  
패키지 매니저를 사용해 쉽게 다운 받을 수 있다. 사용 중인 Linux 배포판에 맞는 명령어를 복사하여 Terraform을 설치하세요.
  
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

패키지 매니저를 사용해 쉽게 다운 받을 수 있다. 명령어를 복사하여 Terraform을 설치하세요.

```hcl
brew tap hashicorp/tap
brew install hashicorp/tap/terraform
```
