테라폼 환경을 설치해 보자.

운영체제에 알맞게 설치를 해라. Windows와 Lunux에 설치하는 방법을 제공한다.

## Windows

#### 1. Terraform 다운로드

Terraform 설치 파일은 HashiCorp 공식 사이트에서 다운로드할 수 있습니다.

🔗 [Terraform 다운로드 페이지](https://developer.hashicorp.com/terraform/install)

#### 다운로드 방법

1. 위의 링크를 클릭하여 다운로드 페이지로 이동합니다.

1. 좌측 배너에서 Windows를 클릭합니다.

1. 64bit 컴퓨터인 경우 AMD64를 선택하여 다운로드합니다. (대부분의 컴퓨터는 64bit)
   32bit 컴퓨터인 경우 386을 선택합니다.

1. 다운로드된 ZIP 파일을 확인합니다.



## Linux  
  
#### Ubuntu/Debian Linux  
```hcl
wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform
```

   
