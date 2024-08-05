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

#### Select a role

From the **Role** dropdown list, select an appropriate role.

<figure><img src="../../.gitbook/assets/image (1) (4) (1) (1).png" alt="Roles"><figcaption><p>Roles</p></figcaption></figure>

For Group service accounts, choose from the following list of roles to configure the scope of the token; Snyk recommends selecting Viewer or Admin.

* **Group Viewer** enables read-only access. Note that to set an API token to be read-only and unable to write to the platform, you must use a service account and set it to Group Viewer. See [Snyk API token permissions users can control](../../snyk-api-info/using-snyk-api/api-token-permissions-users-can-control.md).
* **Group Admin** enables full administrator access.
* **Group Member** associates a service account with a group but does not grant any specific access.

For **Organization service accounts**, choose from the standard roles, **Org Admin** or **Org** **Collaborator**, or a custom role if you have set up any custom roles. See [Managing permissions](broken-reference/) for the scope of the Org Admin and Org Collaborator roles.

### Create the service account

Click **Create**.

The token is generated and displayed.

Make sure you copy this token, as you will not see it again. You can click **Close and Hide** once you have copied the token; whether you do or not, when you navigate away from this page, the token will no longer be visible. This is a standard security practice to keep your tokens safe.

#### How the token is associated with a Group and Organizations

The new token is also added to your **Existing service accounts** list, like the list in this example:

<figure><img src="../../.gitbook/assets/uuid-799b88fc-d1d7-72c9-5ceb-30fb2a8d572e-en (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (14) (15).png" alt="Existing service accounts for a Group"><figcaption><p>Existing service accounts for a Group</p></figcaption></figure>

In addition, if you created the token for the entire Group with a **Group Admin** role, the token also appears in the **Existing service accounts** list for each of its Organizations, though it can only be edited at the **Group** level.

<figure><img src="../../.gitbook/assets/uuid-1110723e-74e7-3090-3e69-da65f93acfcc-en.png" alt="Existing accounts for an organization"><figcaption><p>Existing accounts for an Organization</p></figcaption></figure>

If you created the token from an Organization that is part of a Group, the token now also appears in the **Existing service account** list on the Group level. From that list, the Group Admin can also change the token name or delete it.

<figure><img src="../../.gitbook/assets/uuid-50563edb-6a75-9f37-2040-cd814fdf9ead-en.png" alt="Group service accounts with Organization accounts listed"><figcaption><p>Group service accounts with Organization accounts listed</p></figcaption></figure>

## Update the name for a service account token

Click any of the links to update the name for a service account token:

* For **Group-level tokens**, from the **Group** level only
* For **Organization-level tokens**, from the relevant **Organization** and also from the **Group** level:

<figure><img src="../../.gitbook/assets/uuid-b34e3d10-bb0c-b608-bc08-12f2bf0a4fc0-en.png" alt="Update a service account name"><figcaption><p>Update a service account name</p></figcaption></figure>

## Edit and delete a service account

Administrators can change token names and delete tokens.

### What happens to the service account token for a deleted account

When you delete a service account, the API token associated with it is invalidated immediately.

When an account is managed with Groups, the Organization and the Group admins can delete tokens for the Organization; only Group admins can view and manage tokens on the Group level.

Deleting a service account is the same as revoking the API token.

### How to edit or delete a service account

*   Log in to your account and navigate to the Group and Organization that you want to manage.

    For **Group tokens**, navigate to the Group level.\
    For **Organization tokens**, group admins can delete from either the Group or the relevant Organization; Organization admins should navigate to the relevant Organization.
* Click on **Settings** > **Service accounts**.
* Scroll to find the list of existing service accounts:

<figure><img src="../../.gitbook/assets/uuid-799b88fc-d1d7-72c9-5ceb-30fb2a8d572e-en (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (14) (15).png" alt="Existing service accounts for a Group"><figcaption><p>Existing service accounts for a Group</p></figcaption></figure>

* From the list of existing tokens:
  * Click the token name to navigate to **change the token name** and click **Save**.
  * Click **Delete** to **delete a token and invalidate it immediately**. When prompted, click **OK**. Remember that you cannot re-generate the same token.

##
