# 라이선스 정책 및 규칙 만들기

{% hint style="warning" %}
**Release 상태**

라이선스 정책은 Enterprise 요금제에서 사용할 수 있으며 Snyk 오픈 소스 스캔에만 적용됩니다.

[요금제](https://snyk.io/plans)를 참조하세요.
{% endhint %}

그룹 관리자는 각 라이선스에 대해 다음 설정을 구성할 수 있습니다:

* 심각도 수준: 값에는 `None`, `Low`, `Medium`,`High`등이 있습니다.
  * `None`을 선택하면 없음으로 표시된 라이선스는 Snyk 테스트 결과에 나타나지 않으므로 지침을 삽입할 수 없습니다.
  * Snyk에 의해 추가된 새 라이선스는 `Unknown` 라이선스 유형 심각도를 상속합니다. 이 심각도를 `None`으로 설정하지 않은 경우에는 새로 추가된 라이선스가 Snyk 테스트 결과에 나타납니다.
* 개발자를 위한 법적 지침: 개발자에게 필요한 지침을 제공하려면 자유 텍스트(free text)를 입력하세요.
  * 회사의 구체적인 정책을 설명하고 개발자의 협업 필요성을 설명하며 필요한 경우 단계별 지침을 제공하는 것이 좋습니다.
  * 법적 지침은 CLI 결과, PR 확인 및 프로젝트 보기의 이슈 카드에 표시됩니다.

## 라이선스 정책 보기 및 편집

회사 계정에 하나 이상의 그룹이 있는 경우 다음 단계에 따라 라이선스 정책 설정을 보고 편집할 수 있습니다. :

1.  **그룹 전환(Switch Group)** 선택기를 사용하여 그룹을 선택하면 그룹 개요가 열립니다.

    <figure><img src="../../../.gitbook/assets/license_choose-group_19oct2022.png" alt="Switch Group"><figcaption><p><strong>그룹 전환(Switch Group)</strong> </p></figcaption></figure>
2.  **Policies > Policy manager > License policies > Organization**으로 이동하여 편집하려는 정책을 선택합니다.

    <figure><img src="../../../.gitbook/assets/policy_license_18oct2022.png" alt="Choose the policy to update"><figcaption><p>업데이트할 정책을 선택하세요.</p></figcaption></figure>

**라이선스 정책(License policy)** 화면에는 정책이 적용되는 조직 목록, 정책 설명 및 정책에 포함된 라이선스가 표시됩니다.

라이선스 심각도 및 지침을 편집할 수 있습니다.

<figure><img src="../../../.gitbook/assets/choose-org_customize_19oct2022.png" alt="License policy overview."><figcaption><p>라이선스 정책 개요</p></figcaption></figure>

## 라이선스 정책에 대한 규칙 및 심각도 지정하기

1. **정책 관리자(Policy manager)**&#xC5D0;서 **License policies(라이선스 정책) > Organization(조직)**&#xC73C;로 이동하고 정책 링크를 선택하여 **라이선스 정책(License policy)** 화면을 엽니다.
2. 특정 라이선스에 대한 심각도를 설정하려면 **라이선스 정책(License policy)** 화면에서 **심각도(Severity)** 선택기를 클릭하고 **심각도(Severity)** 수준을 선택하여 Snyk 테스트가 실행될 때 식별하려는 라이선스 문제를 정의합니다.\
   **없음(None)** 이외의 심각도를 선택하고 해당 라이선스 문제가 식별될 때 추가 지침 또는 수정 권장 사항을 표시하려면 **심각도(Severity)** 드롭다운의 오른쪽에 있는 지침 아이콘을 선택하고 라이선스 지침에 대한 텍스트를 입력합니다.
3. **추가(Add)** 또는 **업데이트(Update)**&#xB97C; 클릭하여 변경 사항을 확인합니다.
4. **제출(Submit)**&#xC744; 클릭하여 정책을 저장합니다.

<figure><img src="../../../.gitbook/assets/policy-severity-instructions-x_06oct2022 (1).png" alt="Update license policy instructions"><figcaption><p>라이선스 정책 지침 업데이트</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/policy-severity-instructions-2_06oct2022.png" alt="Submit policy instructions"><figcaption><p>정책 지침 제출</p></figcaption></figure>

업데이트된 심각도 또는 지침 또는 둘 다는 Snyk 서버에서 자동으로 업데이트됩니다. 다음 예약된 테스트가 실행되거나 사용자가 프로젝트를 다시 테스트할 때 이러한 변경 사항에 따라 업데이트된 결과가 전달됩니다. 자세한 내용은 [라이선스 정책 결과](license-policy-results.md)를 참조하세요.

## Unknown 라이선스 유형에 대한 심각도 설정

`Unknown` 라이선스 유형은 Snyk 특정 패키지 버전에 대한 라이선스를 인식하지 못했음을 나타냅니다. 예를 들어 **Unknown**에 심각도 수준을 설정하여 이러한 라이선스 문제에 더 높은 심각도를 부여하여 결과에 더 눈에 띄게 표시되도록 할 수 있습니다.

편집 중인 정책의 오른쪽에 있는 라이선스 목록을 아래로 스크롤한 다음 **Unknown** 라이선스 유형에 대한 심각도 드롭다운을 선택합니다:

<div align="left"><figure><img src="../../../.gitbook/assets/Screenshot 2023-05-12 at 10.42.12.png" alt="Set severity for Unknown license type"><figcaption><p>Unknown 라이선스 유형에 대한 심각도 설정</p></figcaption></figure></div>

{% hint style="info" %}
Snyk은 새 라이선스를 라이선스 정책에 추가할 때 **Unknown**으로 설정된 심각도 수준을 새 라이선스에 적용합니다.
{% endhint %}
