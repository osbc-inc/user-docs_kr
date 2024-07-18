# 정책(policies) 만들기 및 수정

정책 관리자를 사용하면 정책을 [만들고](create-and-edit-policies.md#policy), [수정하고](create-and-edit-policies.md#policy-1), [복제하거나 삭제](create-and-edit-policies.md#policy-2) 수 있습니다.

## 정책(**policy)** 만들기

1. 정책 관리자 화면에서 **Add new policy**를 선택하고 메시지가 표시되면 세부 정보를 입력합니다.
2. 정책을 빠르게 식별할 수 있도록 정책 이름과 설명을 입력합니다.\
   같은 카테고리에 있는 정책은 같은 이름을 가질 수 없습니다. 이름이 없는 정책은 저장할 수 없습니다.
3. 정책을 조직 또는 프로젝트 속성에 적용할지 선택합니다.
4. 정책을 적용할 [Organizations](assign-a-policy-to-an-organization.md) 또는 [attributes](assign-policies-to-projects.md)을 선택합니다.
5. 정책에 규칙을 추가합니다. [Create a license policy and rules](license-policies/create-a-license-policy-and-rules.md) 또는 [Create a security policy and rules](security-policies/create-a-security-policy-and-rules.md)를 참조하세요.
6. 정책을 만들고 **Submit**을 클릭하여 저장합니다.

<div align="left">

<figure><img src="../../.gitbook/assets/screenshot_2020-05-26_at_9.47.26_am.png" alt="Create a policy" width="563"><figcaption><p>정책(<strong>policy)</strong> 만들기</p></figcaption></figure>

</div>

## 정책(policy) 수정하기

1. Policy Manager tab에서 기존 정책의 이름을 클릭하여 변경합니다.
2. [Organizations](assign-a-policy-to-an-organization.md), [attributes](assign-policies-to-projects.md) 및 규칙을 원하는 대로 변경합니다.
3. **Submit**을 클릭하여 변경 내용을 저장합니다.

## 정책(**policy**) 복제 또는 삭제하기

정책을 복제하거나 삭제하려면 오른쪽에 있는 점 3개(...)를 클릭합니다:

<div align="left">

<figure><img src="../../.gitbook/assets/Screenshot 2023-03-28 at 16.42.45.png" alt="Other policy actions"><figcaption><p>Other policy actions</p></figcaption></figure>

</div>

### 정책(policy) 삭제하기

{% hint style="info" %}
정책을 삭제한 후에는 되돌릴 수 없습니다. 조직이 할당된 정책을 삭제하면 해당 조직은 기본 정책으로 돌아갑니다.
{% endhint %}

### 정책(policy) 복제

정책을 복제하면 정책의 규칙은 복사되지만 할당된 조직이나 프로젝트는 복사되지 않습니다. 새 정책은 자동으로 **(Policy Name)의 사본.**..으로 불리며 [정책 편집에 설명된 대로](create-and-edit-policies.md#policy) 편집할 수 있습니다.
