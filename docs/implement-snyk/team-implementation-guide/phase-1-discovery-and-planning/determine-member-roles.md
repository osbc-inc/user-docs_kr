# 사용자 역할 결정

## 기본 역할

Snyk을 설정할 때 가장 중요하게 고려해야 할 사항은 필요에 맞는 [기본 사용자 역할](../../../snyk-admin/user-roles-and-permissions/pre-defined-roles.md)을 결정하는 것입니다.

{% hint style="info" %}
Snyk의 사용자 역할은 변경할 수 없는 고정된 권한 집합을 사용합니다.
{% endhint %}

다음은 기본 역할입니다:

* **Org 관리자**: 일반적으로 팀 리더에게 할당됩니다. 이 역할을 가진 사용자는 프로젝트를 추가/삭제하고, Snyk 검사를 재정의하고, 사용자를 프로비저닝할 수 있습니다. 일반적으로 팀 리더, 관리자 및 보안 팀 사용자에게 이 역할을 할당하는 것이 일반적입니다.
* **Org 공동 작업자**: 개발자를 위해 사용되는 Snyk의 기본 역할입니다. 이 역할은 소규모 팀이나 개발자 우선의 조직적 접근 방식에 이상적입니다.

{% hint style="info" %}
역할/권한을 더 세분화해야 하는 경우, 사용자 지정 역할 및 SSO 기능에 액세스할 수 있도록 Snyk Enterprise 요금제로 업그레이드하는 것이 좋습니다.
{% endhint %}
