# Broker ECR 통합을 위한 컨테이너 레지스트리 에이전트 설정하기

## Broker ECR 통합을 위한 용어 및 다이어그램

Elastic 컨테이너 레지스트리에서 브로커링된 통신은 다른 컨테이너 레지스트리와 동일합니다. 그러나 ECR에는 에이전트에서 IAM(식별 및 액세스 관리) 역할 또는 사용자를 설정해야 하는 특별한 인증 메커니즘이 있습니다.

**컨테이너 레지스트리 에이전트 IAM** 역할 또는 **IAM 사용자**는 컨테이너 레지스트리 에이전트에서 ECR에 액세스할 수 있는 역할을 맡는 데 사용됩니다.

**Snyk ECR 서비스 역할**은 ECR에 대한 액세스 권한이 있는 **IAM 역할**이며 컨테이너 레지스트리 에이전트 IAM 역할 또는 IAM 사용자가 ECR에 대한 읽기 전용 액세스 권한을 갖도록 가정합니다. Snyk ECR 서비스 역할 ARN은 ECR이 실행되는 지역과 함께 Broker 클라이언트에 제공되며, 이를 맡게 될 컨테이너 레지스트리 에이전트에 전달됩니다.

여러 계정에 컨테이너 레지스트리 에이전트와 통신해야 하는 여러 ECR이 있는 경우, 각 ECR에 대해 Broker 클라이언트를 설정해야 합니다.

다음은 브로커 ECR 통합을 위한 아키텍처를 보여줍니다. 다이어그램의 구성 요소 설정에 대한 자세한 내용은 다음 단계를 참조하세요.

<figure><img src="../../../.gitbook/assets/Broker-CRA-architecture-diagram.png" alt="Architecture of the brokered ECR integration"><figcaption><p>브로커 ECR 통합의 아키텍처</p></figcaption></figure>

## 브로커 ECR 통합을 위한 단계 요약

다음 단계에 따라 서로 다른 계정에 있는 ECR 리포지토리에 액세스할 수 있는 단일 컨테이너 레지스트리 에이전트 인스턴스를 설정하세요.

1. **이 단계는 한 번만 실행하세요.** 역할을 맡을 수 있는 권한이 있는 컨테이너 레지스트리 에이전트 IAM 역할 또는 IAM 사용자를 만듭니다. IAM 역할 또는 IAM 사용자를 사용하여 컨테이너 레지스트리 에이전트를 실행합니다. **각 ECR 계정에 대해 별도의 Broker 인스턴스를 사용하여 각 ECR 계정에 대해 다음 단계를 실행합니다.**
2. ECR이 있는 AWS 계정에서 ECR에 대한 읽기 권한이 있는 Snyk ECR 서비스 역할을 생성하고 이 역할은 이전 단계에서 생성한 특정 컨테이너 레지스트리 에이전트 IAM 역할 또는 IAM 사용자만 맡도록 제한합니다.
3. 컨테이너 레지스트리 에이전트 IAM 역할 또는 IAM 사용자가 Snyk ECR 서비스 역할만 맡을 수 있도록 제한합니다.
4. Broker 클라이언트에 Snyk ECR 서비스 역할의 역할 아마존 리소스 이름(ARN)을 제공합니다. Broker 클라이언트는 이 역할 ARN을 컨테이너 레지스트리 에이전트에 전달하고, 컨테이너 레지스트리 에이전트는 이 역할이 ECR에 액세스하는 것으로 간주합니다.

## 1단계: IAM 사용자 또는 IAM 역할로 컨테이너 레지스트리 에이전트 실행하기

이 단계에서는 컨테이너 레지스트리 에이전트에서 사용할 IAM 역할 또는 IAM 사용자를 생성합니다. [AWS 문서](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-credentials-node.html)에 설명된 방법을 통해 컨테이너 레지스트리 에이전트에 IAM 역할 또는 IAM 사용자를 제공할 수 있습니다.

다음 예에서는 다음 방법 중 하나를 사용하여 IAM 역할 또는 IAM 사용자를 제공하는 방법을 설명합니다:

* **예제** **a**: 전용 EC2 역할을 생성하고 컨테이너 레지스트리 에이전트 이미지를 실행하는 EC2 인스턴스에 AWS IAM(ID 및 액세스 관리) 역할의 자격 증명을 로드합니다.
* **예제 b**: 전용 사용자를 만들고 환경 변수를 통해 자격 증명을 제공합니다.

Amazon ECS 작업에서 전용 역할을 제공할 수도 있습니다. 자세한 내용은 [AWS 문서](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-iam-roles.html)를 참조하세요.

### 예제 a: 전용 EC2 서비스 역할을 생성하고 Amazon EC2용 AWS IAM(신원 및 액세스 관리) 역할에서 자격 증명 로드하기

#### 1단계: 역할 만들기

1. [AWS](https://console.aws.amazon.com/iam/home?#/policies) 로 이동하여 IAM 서비스를 사용하여 AWS 관리 콘솔에 로그인하고 **역할(role)** 페이지로 이동합니다.
2. **역할 만들기(create a role)**&#xB97C; 선택합니다.
3. **신뢰할 수 있는 엔티티 유형**에 대해 **AWS** 서비스를 선택합니다.
4. **사용 사례(use case)**&#xB85C; **EC2**를 선택합니다.
5. 권한 및 태그를 사용하여 다음으로 이동을 선택합니다.
6. 역할 이름을 검토하고 입력합니다:**SnykCraEc2Role**.
7. 역할을 만듭니다.
8.  역할의 **요약(Summary)** 페이지에서 나중에 사용할 수 있도록 **인스턴스 프로필 ARN(Instance Profile ARN)**&#xC744; 복사합니다.\
    예: `arn:aws:iam::aws-account:instance-profile` 또는`SnykCraEc2Role`\
    또한 **Role ARN**을 복사합니다.

    예: `arn:aws:iam::aws-account:role` 또는`SnykCraEc2Role`

#### 2단계: EC2 역할이 다른 역할을 맡을 수 있도록 허용하는 정책 만들기

1. 새로 만든 역할 페이지의 **권한(Permissions)** 탭에서 **인라인 정책(Inline policy)**&#xC744; 만듭니다.
2. **Service**에서 **STS**를 선택합니다.
3. **작업(Actions)**&#xC5D0;서 **쓰기(Write)** → **역할 가정하기(AssumeRole)**&#xB97C; 선택합니다.
4. **리소스(Resources)**&#xC5D0;서 **모든 리소스(All resources)**&#xB97C; 선택합니다(이후 단계에서 리소스를 강화합니다).
5.  **JSON** 탭에서 정책에 다음이 포함되어 있는지 확인합니다:

    ```
    {
      Version: 2012-10-17,
      Statement: [
        {
          Sid: SnykCraAssumeRolePolicy,
          Effect: Allow,
          Action: sts:AssumeRole,
          Resource: *
        }
      ]
    }
    ```
6. 정책을 검토하고 정책 이름(**SnykCraAssumeRolePolicy**)을 입력합니다.
7. 정책 생성을 선택합니다.

#### 3단계: 컨테이너 레지스트리 에이전트를 실행하는 EC2 머신에 역할 연결하기

1. **EC2 관리 콘솔(EC2 Management Console)**&#xB85C; 이동하여 컨테이너 레지스트리 에이전트 컨테이너를 실행하는 인스턴스를 선택합니다.
2. **작업(Actions) → 보안(Security) → IAM 역할 수정(Modify IAM Role)**&#xC744; 선택합니다.
3. **IAM 역할(IAM role)** 드롭다운 목록에서 첫 번째 단계에서 생성한 IAM 역할의 인스턴스 프로파일을 선택합니다. \
   예: `arn:aws:iam::aws-accoun:instance-profile` 또는`SnykCraEc2Role`
4. 그런 다음 **저장(Save)**&#xD569;니다.

EC2 머신에서 컨테이너 레지스트리 에이전트 이미지를 실행하는 경우, 연결된 역할의 자격 증명이 실행 중인 컨테이너 레지스트리 에이전트에 의해 자동으로 선택됩니다. 따라서 추가 단계가 필요하지 않습니다. 자세한 내용은 [Amazon 문서](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html#instance-metadata-security-credentials)를 참조하세요.

### 예제 b: 환경 변수를 통해 전용 사용자 생성 및 자격 증명 제공

#### 1단계: 사용자 만들기

1. [AWS](https://console.aws.amazon.com/iam/home?#/policies) 로 이동하여 IAM 서비스를 사용하여 AWS 관리 콘솔에 로그인하고 **사용자** 페이지로 이동합니다.
2. **사용자 추가(Add users)**&#xB97C; 선택합니다.
3. 사용자 이름: **SnykCraUser**를 입력합니다.
4. **액세스 유형(Access type)**&#xC73C;로 **프로그래밍 방식의 액세스(Programmatic access)**&#xB97C; 선택합니다.
5. 권한 및 태그와 함께 다음으로 이동을 선택합니다.
6. 사용자를 검토하고 생성합니다.
7. 사용자가 생성되면 나중에 사용할 수 있도록 자격 증명(액세스 키 ID 및 비밀 액세스 키)을 저장합니다.
8. 사용자의 **요약(Summary)** 페이지에서 나중에 사용할 수 있도록 **사용자 ARN(User ARN)**&#xC744; 복사합니다.\
   예: `arn:aws:iam::aws-account:user` 또는`SnykCraUser`

#### 2단계: 사용자가 역할을 맡을 수 있도록 허용하는 정책을 만듭니다.

1. 새로 만든 사용자 페이지의 **권한(Permissions)** 탭에서 **인라인 정책(Inline policy)**&#xC744; 만듭니다.
2. **Service** 에서 **STS**를 선택합니다.
3. **작업(Actions)**&#xC5D0;서 **쓰기(Write)→역할 가정(AssumeRole)**&#xC744; 선택합니다.
4. **리소스(Resources)**&#xC5D0;서 **모든 리소스(All resources)**&#xB97C; 선택합니다(이후 단계에서 리소스를 강화할 예정임).
5.  **JSON** 탭에서 정책에 다음 문구가 포함되어 있는지 확인합니다:

    ```
    {
      Version: 2012-10-17,
      Statement: [
        {
          Sid: SnykCraAssumeRolePolicy,
          Effect: Allow,
          Action: sts:AssumeRole,
          Resource: *
        }
      ]
    }
    ```
6. 정책을 검토하고 정책 이름(**SnykCraAssumeRolePolicy**)을 입력합니다.
7. 정책 생성을 선택합니다.

#### 3단계: 컨테이너 레지스트리 에이전트를 실행할 때 자격 증명 사용

컨테이너 레지스트리 에이전트 이미지를 실행할 때 다음 환경 변수를 설정하여 자격 증명을 제공할 수 있습니다:

* `AWS_ACCESS_KEY_ID=User access key ID`
* `AWS_SECRET_ACCESS_KEY=User secret access key`

## 2단계: Snyk ECR 서비스 역할을 생성하고 ECR에 대한 교차 계정 액세스 활성화

이 단계에서는 ECR 리포지토리가 있는 계정에서 역할을 만듭니다. 이 역할은 리포지토리에 대한 읽기 전용 액세스를 허용하며 이전 단계에서 만든 역할이 이 역할을 맡을 수 있습니다.

### **1.** Snyk ECR 서비스 역할에서 사용할 읽기 전용 ECR 정책을 만듭니다.

1. [AWS](https://console.aws.amazon.com/iam/home?#/policies)로 이동하여 IAM 서비스를 사용하여 AWS 관리 콘솔에 로그인하고 **정책(Policies)** 페이지로 이동합니다.
2. 새 정책을 만듭니다.
3. JSON 데이터 편집을 선택합니다.
4.  기본 데이터를 삭제하고 그 자리에 다음을 복사하여 붙여넣습니다:

    ```
    {
      Version:2012-10-17,
      Statement: [
        {
          Sid:SnykAllowPull,
          Effect:Allow,
          Action: [
            ecr:GetLifecyclePolicyPreview,
            ecr:GetDownloadUrlForLayer,
            ecr:BatchGetImage,
            ecr:DescribeImages,
            ecr:GetAuthorizationToken,
            ecr:DescribeRepositories,
            ecr:ListTagsForResource,
            ecr:ListImages,
            ecr:BatchCheckLayerAvailability,
            ecr:GetRepositoryPolicy,
            ecr:GetLifecyclePolicy
          ],
          Resource:*
        }
      ]
    }
    ```
5. 정책을 검토하도록 선택합니다.
6. **AmazonEC2ContainerRegistryReadOnlyForSnyk**를 **Name**으로 설정합니다.
7. **컨테이너 레지스트리 에이전트에 Amazon EC2 컨테이너 레지스트리 리포지토리**에 대한 **읽기 전용 액세스 권한 제공**을 **설명**으로 설정합니다.
8. 정책을 생성하도록 선택합니다.

### 2. 정책을 구현할 Snyk ECR 서비스 역할 만들기

1. AWS 관리 콘솔에서 다시 **역할(Roles)** 페이지로 이동합니다. 필요한 경우 [로그인](https://console.aws.amazon.com/iam/home?#/roles)하여 AWS 관리 콘솔로 이동합니다.
2. 새 역할을 만듭니다.
3. 신뢰할 수 있는 엔티티로 **AWS 서비스**를 선택하고 이 역할의 서비스로 **EC2**를 선택합니다.
4. 권한이 있는 다음 단계를 선택합니다.
5. 목록에서 **AmazonEC2ContainerRegistryReadOnlyForSnyk** 정책을 확인합니다.
6. 태그와 함께 다음으로 이동을 선택하고 검토합니다.
7. **SnykEcrServiceRole**을 이름으로 설정합니다.
8. **EC2 인스턴스가 사용자를 대신하여 ECR AWS 서비스를 호출할 수 있도록 허용**을 설명으로 설정합니다.

### 3. Snyk ECR 서비스 역할의 사용성 범위 강화

이 단계는 컨테이너 레지스트리 에이전트 IAM 역할 또는 IAM 역할만 맡을 수 있도록 Snyk ECR 서비스 역할의 사용성을 강화합니다.

1. 다시 **역할(Roles)** 페이지에서 [SnykEcrServiceRole](https://console.aws.amazon.com/iam/home?#/roles/SnykEcrServiceRole)을 찾아서 선택하여 역할 구성을 입력합니다.&#x20;
2. **신뢰 관계(Trust relationships)** 탭을 선택합니다.
3. 신뢰 관계(Trust relationships)를 편집합니다.
4.  모든 데이터를 삭제하고 다음 JSON으로 바꿉니다:

    ```
    {
      Version:2012-10-17,
      Statement: [
        {
          Effect:Allow,
          Principal:{
            AWS:ARN of Container Registry Agent IAM User or IAM Role
          },
          Action:sts:AssumeRole,
          Condition:{
            StringEquals: {
              sts:ExternalId:optional external ID
            }
          }
        }
      ]
    }
    ```

    * **Statement.Principal.AWS**에 1단계에서 생성한 IAM 역할 또는 IAM 사용자를 입력합니다.\
      예: `arn:aws:iam::aws-account:user` 또는`SnykCraEc2Role`\
      또는`arn:aws:iam::aws-account:role` 또는`SnykCraUser`를 각각 입력합니다.
    * **Condition.StringEquals.sts:ExternalId** 에서 자격 증명 개체가 Broker 클라이언트에 제공될 때 사용되는 외부 ID를 사용할 수 있습니다.
    * 여러 개의 외부 ID를 지원하려면 대괄호 안에 ID 목록을 입력합니다. 예: `sts:ExternalId: [ 11111111-1111-1111-1111-111111111111, 22222222-2222-2222-2222-222222222222 ]`
5. 신뢰 정책을 업데이트합니다.

## 3단계: 컨테이너 레지스트리 에이전트에서 사용하는 IAM 역할 또는 IAM 사용자의 사용성 범위 강화하기

이 단계는 컨테이너 레지스트리 에이전트가 사용하는 IAM 역할 또는 IAM 사용자의 사용성을 강화하여 [SnykEcrServiceRole](https://console.aws.amazon.com/iam/home?#/roles/SnykEcrServiceRole)만 맡을 수 있도록 합니다.

1. [SnykEcrServiceRole](https://console.aws.amazon.com/iam/home?#/roles/SnykEcrServiceRole)의 **요약(Summary)** 섹션 상단에 표시되는 역할 ARN 키를 복사합니다.
2. 컨테이너 레지스트리 에이전트를 실행하기 위해 IAM 역할 또는 IAM 사용자가 생성된 AWS 계정에서 **SnykCraAssumeRolePolicy**를 편집합니다:
   1. IAM 역할이 생성된 경우, **역할(Roles)**&#xB85C; 이동하여 **SnykCraEc2Role** 역할을 선택합니다.
      1. **SnykCraAssumeRolePolicy**에서 JSON을 편집하도록 선택합니다.
      2. [SnykEcrServiceRole](https://console.aws.amazon.com/iam/home?#/roles/SnykEcrServiceRole)의 역할 ARN을 리소스로 추가합니다:\
         `Resource:SnykEcrServiceRole`의 역할 `ARN`
   2. IAM **사용자(Users)**&#xAC00; 생성된 경우 사용자로 이동하여 SnykCraUser 사용자를 선택합니다.
      1. **SnykCraAssumeRolePolicy**에서 JSON을 편집하도록 선택합니다.
      2. [SnykEcrServiceRole](https://console.aws.amazon.com/iam/home?#/roles/SnykEcrServiceRole)의 역할 ARN을 리소스로 추가합니다:\
         `Resource: SnykEcrServiceRol`의 역할 `ARN`&#x20;

컨테이너 레지스트리 에이전트가 서로 다른 계정에 있는 여러 ECR 레지스트리에 액세스해야 하는 경우, 예를 들어 각 ECR 계정에 별도의 명세서가 있도록 명세서 목록에 별도의 항목을 추가해야 합니다:

```
{
  Version: 2012-10-17,
  Statement: [
    {
      Sid: SnykCraAssumeRolePolicyAccountA,
      Effect: Allow,
      Action: sts:AssumeRole,
      Resource: role ARN of SnykEcrServiceRole of account A
    },
    {
      Sid: SnykCraAssumeRolePolicyAccountB,
      Effect: Allow,
      Action: sts:AssumeRole,
      Resource: Role ARN of SnykEcrServiceRole of account B
    },
  ]
}
```

## 4단계: Broker 클라이언트에 Snyk ECR 서비스 역할 ARN 및 외부 ID를 제공합니다.

이 단계에서는 Broker 클라이언트에 SnykEcrServiceRole \_\*\*\_의 역할 ARN을 제공하여 사용합니다. Broker 클라이언트는 이를 컨테이너 레지스트리 에이전트에 전달하고, 이 에이전트는 ECR에 연결한다고 가정합니다.

1. [SnykEcrServiceRole](https://console.aws.amazon.com/iam/home?#/roles/SnykEcrServiceRole)의 **요약(Summary)** 섹션 상단에 표시되는 **역할 ARN(Role ARN)** 키를 복사합니다.
2. Broker 클라이언트를 실행할 때 컨테이너 레지스트리 에이전트가 ECR 계정에 액세스할 수 있도록 다음 환경 변수를 제공하세요. 사용자 이름과 비밀번호는 필요하지 않습니다.
   * `CR_TYPE=ecr`
   * `CR_ROLE_ARN=the role ARN of SnykEcrServiceRole`
   * `CR_REGION=AWS Region of ECR`
   * `CR_EXTERNAL_ID=`선택 사항. 신뢰 관계 조건에서 찾은 외부 ID
