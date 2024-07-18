# 정책(Policies) 보기

{% hint style="info" %}
You must be a Group administrator to view, create, and modify policies for that Group.
{% endhint %}

\
**Policies** 메뉴 옵션을 선택하면 그룹의 정책을 카테고리, [라이선스 정책(License policies)](license-policies/) 및 [보안 정책](security-policies/)[(](security-policies/)[Security policies](security-policies/)[)](security-policies/)별로 정렬하여 볼 수 있습니다.

<div align="left">

<figure><img src="../../.gitbook/assets/Policies-menu.png" alt="View policies"><figcaption><p>정책 보기</p></figcaption></figure>

</div>

카테고리를 펼치면 해당 카테고리의 정책 목록을 볼 수 있습니다:

<figure><img src="../../.gitbook/assets/snyk-policy-manager.png" alt="License policies list expanded"><figcaption><p>라이선스 정책 목록 확장</p></figcaption></figure>

{% hint style="info" %}
이 목록에는 각 정책 카테고리의 새 그룹에 대해 자동으로 생성되며 제거할 수 없는 [default policy](view-policies.md#default-policies)이 포함되어 있습니다.
{% endhint %}

## 정책 세부 정보(Policy details)

카테고리를 확장하면 **프로젝트 속성(Project attributes)**에 적용되고 **조직(Organizations)**에 적용된 정책이 화면에 표시됩니다. 클릭하여 각 카테고리에서 **어떤 정책이 우선 적용되는지** 알아볼 수 있습니다. 특정 정책을 **검색(search)**할 수도 있습니다.

<figure><img src="../../.gitbook/assets/screenshot_2021-03-26_at_11.04.50_am.png" alt="Policy manager screen including attributes and Organizations to which each policy is applied"><figcaption><p>각 정책이 적용되는 속성 및 조직을 포함한 정책 관리자 화면</p></figcaption></figure>

## 기본 정책(Default policies)

각 정책 카테고리에는 기본 정책(default policy)이 있습니다. 기본 정책(default policy)은 프로젝트 속성이 아닌 조직에만 적용할 수 있습니다.

새 조직을 만들면 기존 조직의 설정을 복사하지 않는 한 기본 정책(default policy)에 자동으로 추가됩니다. 원하는 경우 조직을 다른 정책에 할당할 수 있습니다.

기본 정책(default policy)은 삭제할 수 없지만 기본 정책 이름, 설명 및 규칙은 원하는 대로 편집할 수 있습니다. 원하는 경우 기본 정책(default policy)에 규칙을 포함하지 않을 수도 있습니다.

자세한 내용은 [Organization에 policy 할당하기](assign-a-policy-to-an-organization.md)를 참조하세요.
