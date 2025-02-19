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

프로바이더 블록은 <Block Type> <Resource Name? Type?> 이렇게 생겼어.
그리고 Block Type은 <provider>로 고정이고 resource name은 너가 사용할 csp에 해당하는 걸 적으면 돼.
우리는 이 시리즈 내내 azure를 csp로 사용할 거잖아?
그래서 우리는 이 포스트 끝까지 계속 resource name으로 azurerm을 쓸거야.
그래서 에저에 인프라를 프로비저닝할거라면 <provider> <azurerm>을 꼭 사용해야해.


```hcl
provider "azurerm"{
  features {}

  subscription_id = "00000000-0000-0000-0000-000000000000"
  tenant_id       = "11111111-1111-1111-1111-111111111111"
}
```
이런식으로 provider 블록을 작성해서 사용해.

- The `features` block is required but can be left empty. It is used to enable specific features in the Azure provider.
- The `subscription_id` is the unique identifier for your Azure subscription. This is mandatory unless you're using other authentication methods that automatically retrieve it.
- The `tenant_id` refers to your Azure Active Directory (AAD) tenant. This is optional in some cases, but if you have multiple tenants, specifying it ensures the correct one is used.

