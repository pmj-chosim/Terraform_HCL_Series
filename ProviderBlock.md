안녕~ 또 만나서 반가워!!  
이번 시간은 provider block에 대해 알아 볼 거야.  
provider block에 대해 알아 보고, azure에 리소스 그룹을 provider block을 사용해서 만들어 볼 거야.  
  
지난 시간에 terraform 환경 set up을 했었지?  
오늘은 visual studio code에서 바로 terraform을 사용해 볼꺼야.  
  
visual studio code가 없다면   
[Viusal Studio Code Install](https://code.visualstudio.com/download)   
위에서 다운 받을 수 있어.  
  
없다면, 설치하고 오늘 이 포스트와 함께 provider 블록에 대해 알아본 다음, 사용까지 해보자!  
  
***
1. 먼저 프로바이더 블록이 뭔지 다시 회상해보자!



2. 프로바이더 블록은 어떻게 생겼을까?

이 시리즈의 맨 처음 포스트에서 terraform 블록들의 공통적인 구조를 얘기했었지/
  
 - Common Structure of Terraform Blocks
Blocks in Terraform typically follow a general pattern:

**Not All Blocks follow this pattern

<Block Type> <Resource Type> <Resource Name> {
  <Attribute> = <Value>
}

모든 블록이 저렇게 생긴 건 아니라고 했잖아. 프로바이더 블록이 저렇게 생기지 않았어.

The provider block follows the structure: `<Block Type> <Provider Type>`.  

- The **Block Type** is always `provider`.  
- The **Provider Type** specifies which cloud service provider (CSP) you are using.  

Since we'll be using **Azure** as our CSP throughout this series, we'll consistently use `azurerm` as the provider type.  

So, whenever you provision infrastructure on Azure using Terraform, you must use the following format:

```terraform
provider "azurerm" {
  features {}
}
```
그렇긴 한데.. 우리는 정보를 더 추가해서 계속 사용할 거야. 다음 형태로 사용할 거란 말이지. 

```hcl
provider "azurerm"{
  features {}

  subscription_id = "00000000-0000-0000-0000-000000000000"
  tenant_id       = "11111111-1111-1111-1111-111111111111"
}
```
지금, 새로 추가된 게 있지?

- The `features` block is required but can be left empty. It is used to enable specific features in the Azure provider.
- The `subscription_id` is the unique identifier for your Azure subscription. This is mandatory unless you're using other authentication methods that automatically retrieve it.
- The `tenant_id` refers to your Azure Active Directory (AAD) tenant. This is optional in some cases, but if you have multiple tenants, specifying it ensures the correct one is used.

우리는 subcription_id 정보를 추가적으로 넣어서 매번 사용할거야.
subcription_id에 뭐 적어야 하는지는 조금 있다가 같이 살펴보자.


3. 세 번째로는 visual studio code에서 terraform을 사용할 수 있게 환경을 만드는 거야!
어렵진 않고, 폴더랑 파일을 만들어 볼거야.

visual studio code를 열고, 너가 작업하고 싶은 폴더를 만들어. 이름은 상관없어. 그 다음 폴더 안에 main.tf라는 파일을 만들어 보자.
> main.tf는 ~~~다.

terraform을 사용하려면, 꼭 필수적으로 작성해야 하는 코드가 있거든?
terrafom의 버전을 명시해서 우째저쨰 하겠다는 코드야.

```hcl
terraform{
    required_version=">=1.0.0"
    required_providers{
        local={
            source="hashicorp/local"
            version=">= 2.0.0"
        }
    }
}
```
요런 코드지.
> `requried_version`은 ~~다
> `required_providers`는 ~다
>  `required_providers` 안에는 사용할 프로바이더가 명시가 되어야 해.

저 코드는 로컬 컴퓨터에 리소스를 프로비전하겠다는 코드야. 그런데 우리는 azure에 프로비전할 거잖아?

그래서 우리는
```hcl
terraform {
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
      version = "=4.1.0"
    }
  }
}
```
요 코드를 `main.tf`에 써줘야해.  
  
여기서 `4.1.0`은 azure~~의 버전이야. 내가 블로그를 가능하면 업데이트하려 노력하겠지만, 버전 오류가 혹시 발생한다면
[Terraform Guide](https://registry.tf-registry-prod-use1.terraform.io/providers/hashicorp/azurerm/latest/docs/guides/azure_cli)
여기서 지원 버전이 뭔지 확인한 다음, 해당 버전으로 작성하면 돼.
  

4. 이제 azure를 프로비전 해볼까?
 먼저  아까 1~3번 내용에서 다뤘던 거를 정리해 보자!
terraform으로 azure에 프로비전 하기 위해서는 필수적인 게 2가지 있다.
그것은 바로
```hcl
# 첫 번째로 필수적인 것.
terraform {
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
      version = "=4.1.0"
    }
  }
}

# 두 번째로 필수적인 것
provider "azurerm"{
  features {}

  subscription_id = "00000000-0000-0000-0000-000000000000"
}
```
요 블록을 써주는 거야.
이걸 vscode에서 main.tf에 적어줘.

그 다음, 내 subscription_id로 내용을 바꿔줘.

[Azure Portal](https://portal.azure.com/)에 접속해 로그인하고, 맨 위에 있는 배너를 살펴 봐바. copliot 버튼 옆에 있는 버튼있지? cloud shell 버튼을 눌러봐.
![image](https://github.com/user-attachments/assets/9aa8976b-1889-41b3-b453-fb0eb3ea4604)  
그 다음 조금 기다리면, 다음과 유사한 화면이 보일거야.
  
  ![image](https://github.com/user-attachments/assets/af521d6e-49d9-4c68-b098-71d3a02783b5)

여기에 명령어를 하나 입력하자.  
```bash
az account show --output table
```
입력하면 구독 정보들을 확인할 수 있어.

![image](https://github.com/user-attachments/assets/b8e33778-82a5-4edc-a077-28a83db5f499)  

너가 사용할 구독의 id를 복사하면 돼. 복사해서 아까 main.tf의 provider의 subscription_id 부분에 붙여 넣어 주면 된다.

![image](https://github.com/user-attachments/assets/4b46ae3a-8088-42ec-b4c3-d73667782607)  

이런식으로 너가 잘 했을 것 같아.  

그러면 이제 이거를 실행해보자.  


5. terraform 명령어들???

terraform init
terraform plan
terraform apply 설명


그리고 visual studio code의 터미널을 열고, 터미널 경로가 main.tf가 속한 폴더 경로인지 확인해줘. main.tf가 속한 폴더 경로가 아니라면
해당 경로로 이동해줘. 
![image](https://github.com/user-attachments/assets/7082cb9c-f316-45c8-a2b8-5fc2e09a6247)

거기서 terraform init을 가장 먼저 해주면 돼.  
![image](https://github.com/user-attachments/assets/b944fdab-6a77-48fb-ad51-565f7eb0faca)  
위 사진처럼 새로운 게 생길거야.
>.terraform은 ~다
>.terraform.lock.hcl은 뭐뭐다


그 다음 terraform plan을 해보자.
![image](https://github.com/user-attachments/assets/a37bca3b-6b4d-4d3c-a6eb-a1be3c66da3f)

이런식으로 뜨면 잘 수행되고 있는 거야.
no changes로 뜨지? 이거는 우리가 아직 아무 것도 프로비전하지 않아서야.

그 다음 terraform apply를 해보자.
![image](https://github.com/user-attachments/assets/b15d87cd-9dd2-44ed-a0f5-8f887d96ab74)

Apply complete가 뜨면 성공이야! 
근데 프로비저닝된 게 없어서 잘 됐는지 나는 잘 와닿지 않더라고.
그래서 우리 리소스 그룹을 하나 프로비저닝 해보면서
잘 됐는지 가시적으로 확인해보자!

```hcl
resource "azurerm_resource_group" "example" {
  name     = "example-2"
  location = "West Europe"
}
```
main.tf에 이 코드를 추가해줘.
![image](https://github.com/user-attachments/assets/17673283-78c7-4b7a-874c-256eb75e8e91)  

저장을 한 다음, 다시 터미널에 `terraform plan`을 입력해보자.
![image](https://github.com/user-attachments/assets/4b569e6f-bd58-4eb9-9519-a5c6ce8c8c04)  

이대로 만들어도 문제 없다 하니,
`terraform aplly`를 적용해 만들어 보자.  
![image](https://github.com/user-attachments/assets/41c91879-8423-4e66-824d-c8363963529b)  

yes를 입력해주고  
![image](https://github.com/user-attachments/assets/79b31cfc-4ae4-4ec6-8e4f-8cdc2f51554d)  
기다리면, 생성이 될거야.  
azure portal에서도 만들어 졌는지 확인해 보자.  
![image](https://github.com/user-attachments/assets/490888d8-e1e8-4267-a01f-a957da9ecad7)  
azure portal에서 resource groups을 클릭해봐.


![image](https://github.com/user-attachments/assets/002414a9-07a9-4b57-ba9f-203dbd494ac3)  

example-2가 잘 생성돼 있네!!

축하해!!!

Azure에 프로비전을 완료했어!!

***
다음 포스트에서는  ~~를 알아보자.
다음 포스트에서 꼭 다시 만나 ~~

