# 조직에 정책 할당하기

정책을 만들면 하나의 조직에 적용할 수 있습니다. 정책 관리자를 사용하여 기본 정책에 조직을 직접 적용하거나 기본 정책에서 조직을 제거할 수는 없습니다.

{% hint style="info" %}
조직에 적용되는 정책은 `snyk test` 또는 `snyk monitor` CLI 명령을 실행할 때 적용됩니다.
{% endhint %}

## 조직에 정책 적용하기

조직에 정책을 적용하려면 조직 선택기 패널에서 정책을 적용하려는 조직의 확인란을 선택합니다.

조직에 다른 정책이 적용된 경우에는 선택기에서 해당 정책을 볼 수 있으며 조직 이름 옆의 정책 표시기가 회색으로 바뀝니다.

<div align="left">

<figure><img src="../../.gitbook/assets/mceclip3-2-.png" alt=".Gray indicator - Organization has another policy applied"><figcaption><p>회색 표시기 - 조직에 다른 정책이 적용됨</p></figcaption></figure>

</div>

조직에 이미 정책이 적용된 경우 정책 이름이 조직 이름 옆에 노란색 표시로 표시됩니다.

<div align="left">

<figure><img src="../../.gitbook/assets/mceclip2-6-.png" alt="Yellow indicator - Organization already assigned to this policy"><figcaption><p>노란색 표시기 - 이 정책에 이미 할당된 조직입니다.</p></figcaption></figure>

</div>

조직에 다른 정책을 적용하는 경우 해당 조직을 한 정책에서 다른 정책으로 옮기려면 선택기에서 조직 이름 옆에 두 개의 표시기가 나타납니다. 하나는 현재 적용 중인 정책을 노란색으로 표시합니다. 다른 하나는 조직에 적용할 정책을 회색으로 표시합니다.

<div align="left">

<figure><img src="../../.gitbook/assets/mceclip1-16-.png" alt="Gray and Yellow indicators - Policies applied to the Organization and to be applied"><figcaption><p>회색 및 노란색 표시기 - 조직에 적용되었거나 적용될 정책</p></figcaption></figure>

</div>

## 조직에서 정책 제거하기

조직에서 정책을 제거하려면 보고 있는 정책에서 제거하려는 조직 옆의 확인란을 선택 취소합니다.

<div align="left">

<figure><img src="../../.gitbook/assets/untitled-2-.png" alt="Remove an Organization from a policy"><figcaption><p>정책에서 조직 제거하기</p></figcaption></figure>

</div>

이제 선택하지 않은 조직은 자동으로 기본 정책으로 되돌아갑니다.

## 조직에 기본 정책 적용

현재 조직에 적용된 정책을 제거합니다. 조직이 자동으로 기본 정책으로 되돌아갑니다.

## 조직에서 기본 정책 제거

조직에 새 정책을 적용합니다. 조직이 기본 정책에서 자동으로 제거되고 새 정책이 적용됩니다.
