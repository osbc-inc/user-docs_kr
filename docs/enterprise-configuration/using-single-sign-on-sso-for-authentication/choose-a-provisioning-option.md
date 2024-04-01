# 프로비저닝 옵션 선택

{% hint style="info" %}
Snyk 계정 팀과 협력하여 이 SSO 옵션 구현을 준비하세요.
{% endhint %}

회사의 신규 사용자가 Snyk에 액세스하는 방법을 결정하세요 :

* [Open to all](choose-a-provisioning-option.md#open-to-all)
* [Invitation required](choose-a-provisioning-option.md#invitation-required)
* [Custom mapping](choose-a-provisioning-option.md#custom-mapping)

## 모두에게 개방(Open to all)

열기 옵션을 사용하면 모든 사용자는 SSO를 사용하여 로그인하여 Snyk에 자동으로 액세스할 수 있습니다. 선택한 그룹의 모든 조직에 액세스할 수 있습니다. 그들의 계정은 모두 동일한 역할로 프로비저닝되며 두 가지 옵션이 있습니다.

* **조직 관리자** 역할을 통해 모든 신규 사용자는 다른 조직 관리자 및 공동 작업자를 관리하고, 그룹 보고서를 보고, 그룹 내의 조직과 작업할 수 있을 뿐만 아니라 조직에서 비관리 작업을 수행할 수 있습니다.
* **조직 공동 작업자** 역할은 조직에서 비관리 작업을 수행할 수 있습니다.

새로운 사용자가 조직의 **관리자** 역할 또는 **공동 작업자** 역할을 갖게 될지 Snyk 지원팀에 알려주십시오. 선택한 역할은 모든 사용자에게 적용됩니다. 자세한 내용은 [Permissions per role](broken-reference/)을 참조하세요.

## 초대 필요(Invitation required)

초대 필요 또는 **그룹 구성원** 옵션을 사용하면 관리자가 사용자를 초대하거나 사용자가 조직에 대한 액세스를 요청할 수 있습니다.

사용자를 조직에 초대하는 방법에는 두 가지가 있습니다. 구성원을 초대하거나([Manage users in your Organizations](../../snyk-admin/manage-users-in-organizations-and-groups/manage-users-in-organizations.md) 참조) Snyk [API Invite users endpoint.](https://snyk.docs.apiary.io/#reference/organizations/user-invitation-to-organization/invite-users)를 사용하여 프로세스를 자동화하세요.&#x20;

초대되지 않은 사용자가 SSO를 사용하여 로그인하는 경우, Snyk에 액세스할 수 있지만 관리자가 초대하거나 수동으로 조직에 추가할 때까지 프로젝트를 볼 수 없습니다. 새 사용자가 [request access](https://docs.snyk.io/user-and-group-management/managing-users-and-permissions/organization-access-requests) 할 수 있도록 적절한 담당자와 함께 조직 목록을 제공할 수 있습니다.

## 사용자 지정 매핑(Custom mapping)

{% hint style="warning" %}
**출시 상태**\
사용자 정의 매핑은 Enterprise 플랜에서만 사용할 수 있습니다.

[Pricing plans](https://snyk.io/plans)을 참조하세요.
{% endhint %}

[Custom Mapping Option](custom-mapping-option/) 옵션을 사용하여 사용자 정의된 규칙으로 사용자 계정을 프로비저닝할 수 있습니다.

서로 다른 그룹마다 SSO를 다르게 구성할 수 있습니다. 또한 ID 공급자의 정보를 기반으로 사용자를 특정 조직 및 역할 할당에 매핑할 수도 있습니다.
