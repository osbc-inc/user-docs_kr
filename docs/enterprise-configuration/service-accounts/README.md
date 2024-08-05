# 서비스 계정

{% hint style="warning" %}
**Release 상태** \
SSO는 Enterprise 요금제에서만 사용할 수 있습니다.

무료 및 팀 요금제 사용자와 평가판 사용자는 프로필에서 Snyk 사용자 토큰에 액세스할 수 있으며 이 토큰을 사용하여 CI/CD로 인증하고, 로컬 또는 빌드 머신에서 CLI를 실행하고, IDE로 수동으로 인증할 수 있습니다.

[요금제](https://snyk.io/plans)를 참조하세요.
{% endhint %}

서비스 계정은 특별한 유형의 시스템 사용자입니다. 서비스 계정을 만들면 서비스 계정과 연결된 유일한 토큰인 API 토큰이 생성되며 표준 사용자 자격 증명을 대신합니다. Snyk 프로세스를 시작하려면 인증이 필요합니다.

Snyk 사용자 토큰을 사용하지 않고 자동화에 사용하고 통합을 관리하기 위해 **서비스 계정(service account)**을 설정할 수 있습니다.

조직 또는 그룹 수준에서 하나 또는 여러 개의 토큰을 생성하여 연동을 관리할 수 있습니다. 각 서비스 계정에는 쉽게 알아볼 수 있도록 고유한 이름이 있습니다. 이 이름은 재사용할 수 없습니다.

## 서비스 계정 사용 시기

Enterprise 사용자의 경우 프로필 아래에 Snyk 사용자 토큰이 있습니다. 또한 서비스 계정 토큰에 액세스할 수 있습니다.

### 서비스 계정을 사용하여 모든 종류의 자동화를 만들 수 있습니다.

여기에는 CI/CD 또는 빌드 시스템 플러그인을 사용한 스캔과 Snyk API를 사용한 자동화가 포함되며 이에 국한되지 않습니다.

### GitHub Enterprise 통합을 위해 서비스 계정을 사용할 수 있습니다.

팀에서 GitHub에서 서비스 계정을 설정해야 하는 경우, Snyk Enterprise 계정으로만 사용할 수 있는 GitHub Enterprise를 사용해야 합니다.

Snyk 사용자 토큰이 아닌 서비스 계정을 사용하여 통합 인증을 하면 사용자가 역할을 변경하거나 개인 Snyk 계정을 폐쇄할 때 연속성을 보장할 수 있습니다.

### 통합을 관리할 때 그룹 수준 토큰을 사용합니다.

그룹 수준 토큰을 사용하여 그룹 API 엔드포인트 및 조직 API 엔드포인트를 호출하고 그룹의 모든 조직에 대한 CLI를 실행할 수 있습니다.

그룹 역할은 그룹 수준의 서비스 계정에만 해당되며 Enterprise 계정으로 제한됩니다.

### 로컬 스캔 및 API 호출 테스트에 Snyk 사용자 토큰을 사용하세요.

Enterprise 사용자의 경우, Snyk 사용자 토큰을 사용하여 컴퓨터에서 로컬로 CLI를 실행하고, IDE로 수동으로 인증하고, 엔드포인트 사용을 테스트하는 등 가끔 API 호출을 하세요.

{% hint style="warning" %}
Snyk은 서비스 계정 토큰을 사용하여 IDE로 인증하지 말 것을 권장합니다.
{% endhint %}

## 그룹 또는 조직 수준 서비스 계정 설정

그룹 또는 조직 수준에서 단일 또는 여러 개의 토큰을 생성하여 통합을 관리하세요.

### 서비스 계정을 설정하기 위한 전제 조건

{% hint style="warning" %}
그룹 뷰어는 조직 역할에 관계없이 서비스 계정을 만들 수 없습니다.
{% endhint %}

**그룹 서비스 계정(Group service account)**을 만들려면 그룹 관리자여야 합니다. **조직 서비스 계정(Organization service account)**을 만들려면 그룹 회원이자 조직 관리자 또는 그룹 관리자여야 합니다.

이 프로세스에서는 모든 옵션에 대해 설명합니다. 동일하거나 다른 그룹 또는 조직에 대해 여러 개의 토큰을 만들려면 단계를 반복합니다.

### 그룹 또는 조직 서비스 계정을 설정하는 방법

* 계정에 로그인하고 관리하려는 관련 그룹 및 조직으로 이동합니다.
* **Settings(설정) > Service accounts(서비스 계정)**을 클릭하여 기존 서비스 계정과 해당 세부정보를 확인합니다.
* **Create a service account(서비스 계정 만들기)**를 클릭하여 새 계정을 만듭니다.\
  **그룹(Group)** 또는 **조직(Organization)**을 선택했는지 여부에 따라 로드되는 화면이 달라집니다.

**그룹 서비스 계정(Group service account)**을 만들 때 그룹 수준의 역할을 선택할 수 있다는 점에 유의하세요.

<figure><img src="../../.gitbook/assets/Screenshot 2022-07-06 at 12.01.28.png" alt="Group settings"><figcaption><p>그룹 설정(Group settings)</p></figcaption></figure>

반면 **조직 서비스 계정(Organization service account)**을 만드는 동안에는 조직에 대해 설정한 사용자 지정 [구성원 역할](../../snyk-admin/user-roles-and-permissions/user-role-management.md)을 포함하여 조직 수준 역할을 선택할 수 있습니다.

<figure><img src="../../.gitbook/assets/Screenshot 2022-07-06 at 12.06.35.png" alt="Organization settings"><figcaption><p>조직 설정(Organization settings)</p></figcaption></figure>

#### 서비스 계정 이름을 입력합니다.

**서비스 계정(Service Account)** 이름 필드에 이 토큰의 고유한 이름을 입력합니다. 이 이름은 **조직(Organization)** 또는 **그룹(Group)** 중 같은 영역의 토큰에 대해 한 번만 사용할 수 있습니다.

<figure><img src="../../.gitbook/assets/uuid-01c4cc98-23c9-3cb1-4972-1aa4f83ad98e-en.png" alt="Service account name and role"><figcaption><p>서비스 계정 이름 및 역할</p></figcaption></figure>

#### 역할(**Role**) 선택

**역할(Role)** 드롭다운 목록에서 적절한 역할을 선택합니다.

<figure><img src="../../.gitbook/assets/image (1) (4) (1) (1).png" alt="Roles"><figcaption><p>Roles(역할)</p></figcaption></figure>

그룹 서비스 계정의 경우 다음 역할 목록 중에서 선택하여 토큰의 범위를 구성합니다(보기 또는 관리자를 선택하는 것이 좋습니다).

* **Group Viewer**는 읽기 전용 액세스를 활성화합니다. API 토큰을 읽기 전용으로 설정하고 플랫폼에 쓸 수 없도록 설정하려면 서비스 계정을 사용하여 그룹 보기로 설정해야 합니다. [사용자가 제어할 수 있는 Snyk API 토큰 권한](../../snyk-api-info/using-snyk-api/api-token-permissions-users-can-control.md)을 참조하세요.
* **그룹 관리자(Group Admin)**는 전체 관리자 액세스 권한을 활성화합니다.
* **그룹 구성원(Group Member)**은 서비스 계정을 그룹에 연결하지만 특정 액세스 권한은 부여하지 않습니다.

**조직 서비스 계정(Organization service accounts)**의 경우 표준 역할, **조직 관리자(Org Admin)** 또는 **조직 공동 작업자(Org Collaborator)** 또는 사용자 지정 역할을 설정한 경우에는 사용자 지정 역할 중에서 선택합니다. 조직 관리자 및 조직 공동 작업자 역할의 범위는 [권한 관리하기](broken-reference/)를 참조하세요.

### 서비스 계정 만들기

**생성(Create)**을 클릭합니다.

토큰이 생성되어 표시됩니다.

이 토큰은 다시 표시되지 않으므로 반드시 복사해야 합니다. 토큰을 복사한 후에는 **닫기 및 숨기기(Close and Hide)**를 클릭할 수 있으며, 복사 여부와 관계없이 이 페이지에서 다른 곳으로 이동하면 토큰이 더 이상 표시되지 않습니다. 이는 토큰을 안전하게 유지하기 위한 표준 보안 관행입니다.

#### 토큰이 그룹 및 조직과 연결되는 방법

새 토큰은 이 예의 목록과 같이 **기존 서비스 계정(Existing service accounts)** 목록에도 추가됩니다:

<figure><img src="../../.gitbook/assets/uuid-799b88fc-d1d7-72c9-5ceb-30fb2a8d572e-en (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (14) (15).png" alt="Existing service accounts for a Group"><figcaption><p>그룹에 대한 기존 서비스 계정(Existing service accounts for a Group)</p></figcaption></figure>

또한 **그룹 관리자(Group Admin)** 역할로 전체 그룹에 대한 토큰을 만든 경우 토큰은 **그룹(Group)** 수준에서만 편집할 수 있지만 각 조직의 **기존 서비스 계정(Existing service accounts)** 목록에도 표시됩니다.

<figure><img src="../../.gitbook/assets/uuid-1110723e-74e7-3090-3e69-da65f93acfcc-en.png" alt="Existing accounts for an organization"><figcaption><p>조직의 기존 계정(Existing accounts for an Organization)</p></figcaption></figure>

그룹에 속한 조직에서 토큰을 만든 경우 이제 토큰이 그룹 수준의 **기존 서비스 계정(Existing service account)** 목록에도 표시됩니다. 이 목록에서 그룹 관리자는 토큰 이름을 변경하거나 토큰을 삭제할 수도 있습니다.

<figure><img src="../../.gitbook/assets/uuid-50563edb-6a75-9f37-2040-cd814fdf9ead-en.png" alt="Group service accounts with Organization accounts listed"><figcaption><p>조직 계정이 나열된 서비스 계정 그룹화</p></figcaption></figure>

## 서비스 계정 토큰의 이름 업데이트

서비스 계정 토큰의 이름을 업데이트하려면 링크를 클릭합니다:

* **그룹 레벨 토큰(Group-level tokens)**의 경우, **그룹(Group)** 레벨에서만 가능합니다.
* **조직 수준 토큰(Organization-level tokens)**의 경우, **해당 조직(Organization)** 및 **그룹(Group)** 수준에서도 가능합니다:

<figure><img src="../../.gitbook/assets/uuid-b34e3d10-bb0c-b608-bc08-12f2bf0a4fc0-en.png" alt="Update a service account name"><figcaption><p>서비스 계정 이름 업데이트</p></figcaption></figure>

## 서비스 계정 수정 및 삭제

관리자는 토큰 이름을 변경하고 토큰을 삭제할 수 있습니다.

### 삭제된 계정의 서비스 계정 토큰은 어떻게 되나요?

서비스 계정을 삭제하면 해당 계정과 연결된 API 토큰이 즉시 무효화됩니다.

계정이 그룹으로 관리되는 경우 조직과 그룹 관리자는 조직의 토큰을 삭제할 수 있으며, 그룹 관리자만 그룹 수준에서 토큰을 보고 관리할 수 있습니다.

서비스 계정을 삭제하는 것은 API 토큰을 해지하는 것과 동일합니다.

### 서비스 계정을 수정하거나 삭제하는 방법

*   계정에 로그인하고 관리하려는 그룹 및 조직으로 이동합니다.

    **그룹 토큰(Group tokens)**의 경우, 그룹 레벨로 이동합니다.\
    **조직 토큰(Organization tokens)**의 경우, 그룹 관리자는 그룹 또는 해당 조직에서 삭제할 수 있으며, 조직 관리자는 해당 조직으로 이동해야 합니다.
* **설정(Settings) > 서비스 계정(Service accounts)**을 클릭합니다..
* 스크롤하여 기존 서비스 계정 목록을 찾습니다:

<figure><img src="../../.gitbook/assets/uuid-799b88fc-d1d7-72c9-5ceb-30fb2a8d572e-en (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (14) (15).png" alt="Existing service accounts for a Group"><figcaption><p>그룹에 대한 기존 서비스 계정</p></figcaption></figure>

* 기존 토큰 목록에서 :
  * 토큰 이름을 클릭하여 이동하여 **토큰 이름을 변경(change the token name)**한 다음 **저장(Save)**을 클릭합니다.
  * **토큰을 삭제하고 즉시 무효화**하려면 **삭제(Delete)**를 클릭합니다. 메시지가 표시되면 **확인(OK)**을 클릭합니다. 동일한 토큰은 다시 생성할 수 없다는 점을 기억하세요.

##
