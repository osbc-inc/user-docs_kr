# 보안 정책 및 규칙 만들기

새 보안 정책을 만들려면 그룹 메뉴에서 **정책(Policies)**으로 이동한 다음 정책 관리자에서 **보안 정책(Security policies)** 카테고리를 펼치고 **새 정책(new policy)** **추가**를 클릭합니다. 자세한 내용은 [정책 보기](../view-policies.md)를 참조하세요.

<figure><img src="../../../.gitbook/assets/screenshot_2020-10-20_at_10.01.49_am.png" alt="Security policies category expanded"><figcaption><p>Security policies category expanded</p></figcaption></figure>

{% hint style="info" %}
그룹의 모든 조직에 있는 모든 프로젝트에 적용되는 보안 정책의 조건 또는 작업을 변경하려면 **스닉 기본 보안 정책(Snyk Default Security Policy)**을 선택합니다.
{% endhint %}

## 규칙(Rules), 조건(conditions) 및 조치(actions)

보안 정책 규칙은 하나 이상의 조건과 동작이 있는 "if, then" 형식으로 되어 있습니다. 다음은 예시입니다:

<div align="left">

<figure><img src="../../../.gitbook/assets/screenshot_2020-07-06_at_11.38.07.png" alt="Security policy rule format with plus sign to add a rule and three dots top right"><figcaption><p>규칙을 추가하는 더하기 기호와 오른쪽 상단에 점 3개가 있는 보안 정책 규칙 형식</p></figcaption></figure>

</div>

{% hint style="info" %}
새 보안 정책을 만들면 첫 번째 빈 규칙이 자동으로 만들어집니다.
{% endhint %}

조건(conditions) 및 조치(actions)를 선택하여 규칙을 완성합니다. 자세한 내용은[보안 정책 조건(Security policy conditions)](security-policies-conditions.md) 및[보안 정책 조치(Security policy actions)](security-policy-actions.md) 를 참조하세요.

* 새 빈 규칙을 추가하려면 이전 규칙 아래의 더하기 기호를 클릭합니다.
* 규칙을 삭제하거나 복제하려면 규칙 상자의 오른쪽 상단에 있는 점 3개를 클릭합니다.

{% hint style="info" %}
작성하는 규칙의 순서에 따라 우선순위가 정해집니다. 충돌이 있는 경우 맨 위에 있는 규칙이 이후의 모든 규칙보다 우선합니다.
{% endhint %}
