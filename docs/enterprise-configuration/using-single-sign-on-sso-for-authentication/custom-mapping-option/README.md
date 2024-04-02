# 사용자 정의 매핑 옵션

이 옵션을 사용하면 IdP(Identity Provider)가 제공하는 데이터를 기반으로 Snyk 그룹 및 조직에 사용자를 동적으로 할당하여 확장된 사용자 프로비저닝 및 액세스 모델을 구현할 수 있습니다.

{% hint style="info" %}
Snyk 계정 팀과 협력하여 이 옵션을 구현하세요.
{% endhint %}

Snyk 내의 역할 및 권한에 대해 자세히 알아보려면, [Managing permissions](broken-reference/)를 참조하세요.

[Member Roles](../../../snyk-admin/user-roles-and-permissions/user-role-management.md) 및 [Roles in Custom SSO](../../../snyk-admin/user-roles-and-permissions/user-role-management.md#roles-in-custom-sso)도 참조하세요.

## 요구 사항

* [Set up Snyk Single Sign-On (SSO)](../set-up-snyk-single-sign-on-sso.md) 리소스 섹션에 있는 해당 IdP에 대한 SSO 정보 워크시트 작성
* 역할 배열 매핑을 채우기 위한 IdP 내 사용자 정의 속성의 적절한 구성 ([Example roles array mapping](./#example-roles-array-mapping))

## Snyk를 사용한 역할 배열 매핑

IdP 내에서 먼저 `roles`이라는 사용자 지정 매핑을 문자열 배열로 전달해야 합니다. ([Example: Setting up custom mapping for Okta](example-setting-up-custom-mapping-for-okta.md)) 추가 IdP 공급자에 대한 사용자 지정 매핑을 구성하는 방법은 IdP 설명서를 참조하세요.

이 옵션을 구성하려면 SAML 속성 또는 OIDC 클레임 내의 `roles` 배열을 보내 다음 패턴 중 하나를 따르세요.

1\. snyk-groupadmin

* 이 역할 매핑은 사용자에게 그룹 관리자 및 조직 관리자 역할을 할당합니다.
* **groupadmin**은 이 역할을 가진 모든 사용자를 사용자가 할당된 모든 그룹과 해당 그룹에 속하는 모든 조직에 대한 그룹 관리자 및 조직 관리자로 구성합니다.

2\. snyk-groupviewer

* 이 역할 매핑은 사용자에게 그룹 뷰어 역할을 할당하고 그룹, 보고서 및 그룹과 연결된 모든 조직에 대한 읽기 전용 액세스 권한을 부여합니다.

3\. snyk-{groupID}

* 이 역할 매핑은 지정된 그룹 아래의 모든 조직에 대한 조직 공동 작업자 역할을 사용자에게 할당합니다.
*   **groupID** 는 Snyk의 그룹에 대한 ID 문자열입니다. (그룹 수준의 snyk URL에서 찾을 수 있음).

    Group ID를 찾는 방법: https://app.snyk.io/group/\<Group ID> 또는 Group dropdown -> <img src="../../../.gitbook/assets/cog_icon.png" alt="Settings" data-size="line"> -> General -> Group ID.

4\. snyk-{orgslug}-{role}

* 이 역할 매핑은 **orgslug**에 지정된 Snyk 조직에 대해 지정된 공동 작업자, 관리자 또는 사용자 정의 역할을 가진 사용자를 할당합니다.
* **orgslug**는 Snyk에서 조직 이름의 고유 식별자입니다.
  * orgslug를 찾는 방법: https://app.snyk.io/org/{orgslug 또는 Snyk [API List all organizations in a group endpoint](https://snyk.docs.apiary.io/#reference/groups/list-all-organizations-in-a-group/list-all-organizations-in-a-group)을 나열합니다.
  * 참고: **orgslug**는 대부분의 경우 조직의 이름입니다. 그러나 예외가 있을 수 있습니다.
  * 참고: **orgslug**의 값은 최대 60자일 수 있습니다.
* **역할:**
  * 표준 역할을 사용하는 경, **{role}**은(는) **공동작업자** 또는 **관리자**여야 합니다.
  * 맞춤 역할은 **{role}**에도 사용할 수 있으며 정규화된 이름을 사용해야 합니다. 자세한 내용은 [Roles in SSO](../../../snyk-admin/user-roles-and-permissions/user-role-management.md#roles-in-custom-sso) 을 참조하세요.

{% hint style="info" %}
사용자는 조직당 하나의 역할만 매핑해야 합니다. 조직에 대한 여러 역할 매핑은 지원되지 않으며 예기치 않은 동작이 발생할 수 있습니다.
{% endhint %}

## 역할 배열 매핑 형식

그룹 관리자 역할을 가진 사용자를 할당하려면 다음 형식을 사용하십시오.

```
{
    "roles": [
        "snyk-groupadmin"
    ]
}
```

그룹 뷰어 역할을 가진 사용자를 할당하려면 다음 형식을 사용하십시오.

```
{
    "roles": [
        "snyk-groupviewer"
    ]
}
```

사용자에게 조직 협력자 역할을 할당하려면 다음 형식을 사용하십시오.

```
{
    "roles": [
        "snyk-{groupID}"
    ]
}
```

사용자를 조직 관리자 또는 조직 협력자로 할당하려면 역할 배열에 다음 형식을 사용합니다. (**참고:** 조직별로 서로 다른 역할을 할당할 수 있습니다.) 다음 예에서는 사용자를 **orgslug** Org의 Org Admin으로 할당하지만 **orgslug2** Org의 Collaborator로 할당합니다.

```
{
    "roles": [
        "snyk-{orgslug}-admin",
        "snyk-{orgslug2}-collaborator"
    ]
}
```

사용자에게 사용자 정의 역할을 할당하려면 역할 배열에 다음 형식을 사용하십시오. 조직별로 다양한 역할을 할당할 수 있으며, 다양한 조직에 대해 표준 역할과 사용자 정의 역할을 조합하여 사용할 수 있습니다.

```
{
    "roles": [
        "snyk-{orgslug}-admin",
        "snyk-{orgslug2}-collaborator",
        "snyk-{orgslug3}-developer_readonly"
    ]
}
```

{% hint style="info" %}
시스템은 배열 대신 쉼표로 구분된 역할 목록을 지원합니다.

```
{
  "roles": "snyk-{orgslug}-admin,snyk-{orgslug2}-collaborator"
}
```
{% endhint %}

## 역할 배열 매핑 예시

다음 예에서는 매핑 규칙에 따라 Snyk 사용자에게 역할을 할당하는 방법을 보여줍니다.

* 고객 이름은 ABC이고, ABC라는 하나의 그룹이 있습니다.
* 고객은 Snyk 내에 Application-SecurityScanner1, Partner-Plugins 및 Application-Payments의 세 가지 조직을 가지고 있습니다.
* 고객은 비즈니스 개발, 엔지니어링, 보안, 제품의 4개 팀으로 구성되어 있습니다. 각각은 서로 다른 요구 사항을 가지고 있습니다:
  * 비즈니스 개발 팀은 조직 관리자로서 ABC 그룹과 파트너 플러그인 조직에만 액세스할 수 있어야 합니다.
  * 엔지니어링에서는 ABC 그룹, 조직 관리자로 Application-SecurityScanner1 조직, 조직 관리자로 파트너 플러그인 조직, 조직 공동 작업자로 애플리케이션 결제에 액세스해야 합니다.
  * 보안에서는 그룹 관리자로 ABC 그룹에 액세스하고 조직 관리자로 세 조직 모두에 액세스해야 합니다.
  * 제품 팀은 조직 공동 작업자로서 ABC 그룹과 세 조직 모두에 액세스해야 합니다.

비즈니스 개발 팀의 경우 Snyk는 snyk-{orgslug}-{role} 매핑을 사용합니다.

```
{
    "roles": [
        "snyk-partner-plugins-admin"
    ]
}
```

엔지니어링 팀의 경우 Snyk는 snyk-{orgslug}-{role} 매핑을 사용합니다.

```
{
    "roles": [
        "snyk-application-securityscanner1-admin",
        "snyk-partner-plugins-admin",
        "snyk-application-payments-collaborator"
    ]
}
```

보안 팀의 경우 Snyk는 snyk-groupadmin 매핑을 사용합니다.

```
{
    "roles": [
        "snyk-groupadmin"
    ]
}
```

제품 팀의 경우 Snyk는 groupID 값을 삽입해야 하는 snyk-{groupID} 매핑을 사용합니다.

```
{
    "roles": [
        "snyk-{groupID}"
    ]
}
```

## 사용자 정의 매핑에 따른 역할 요약 다이어그램

<figure><img src="../../../.gitbook/assets/custom-mapping-screenshot.png" alt="Summary diagram of role under custom mapping"><figcaption><p>사용자 정의 매핑에 따른 역할 요약 다이어그램</p></figcaption></figure>
