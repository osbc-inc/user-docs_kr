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

1.  Use the **Switch Group** selector and choose a Group to open its overview.

    <figure><img src="../../../.gitbook/assets/license_choose-group_19oct2022.png" alt="Switch Group"><figcaption><p>Switch Group</p></figcaption></figure>
2.  Navigate to **Policies > Policy manager > License policies > Organization** and choose the policy you want to edit.

    <figure><img src="../../../.gitbook/assets/policy_license_18oct2022.png" alt="Choose the policy to update"><figcaption><p>Choose the policy to update</p></figcaption></figure>

The **License policy** screen displays the list of Organizations that the policy applies to, a policy description, and the licenses included in the policy.

You can edit the license severities and instructions.

<figure><img src="../../../.gitbook/assets/choose-org_customize_19oct2022.png" alt="License policy overview."><figcaption><p>License policy overview</p></figcaption></figure>

## Assign rules and severities for a license policy

1. In the **Policy manager**, navigate to **License policies > Organization**, and choose a policy link to open the **License policy** screen.
2. To set the severity for specific licenses, click the **Severity** selector on the **License policy** screen, and choose a **Severity** level to define which license issues you want to identify when Snyk tests run.\
   If you select a severity other than **None** and want additional instructions or fix recommendations to appear when that license issue is identified, select the instructions icon to the right of the **Severity** dropdown and enter the text for the license instruction.
3. Click **Add** or **Update** to confirm your changes.
4. Click **Submit** to save your policy.

<figure><img src="../../../.gitbook/assets/policy-severity-instructions-x_06oct2022 (1).png" alt="Update license policy instructions"><figcaption><p>Update license policy instructions</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/policy-severity-instructions-2_06oct2022.png" alt="Submit policy instructions"><figcaption><p>Submit policy instructions</p></figcaption></figure>

The updated severities or instructions or both are automatically updated on Snyk servers. When the next scheduled test runs or when a user re-tests a Project, updated results are delivered according to these changes. See [License policy results](license-policy-results.md) for details.

## Set severity for the Unknown license type

The `Unknown` license type indicates Snyk has not recognized a license for a given package version. You can set a severity level for **Unknown**, for example, to ensure these license issues are given a higher severity and so appear more prominently in results.

Scroll down the licenses list on the right of the policy you are editing, then select the Severity dropdown for the **Unknown** license type:

<div align="left">

<figure><img src="../../../.gitbook/assets/Screenshot 2023-05-12 at 10.42.12.png" alt="Set severity for Unknown license type"><figcaption><p>Set severity for Unknown license type</p></figcaption></figure>

</div>

{% hint style="info" %}
Snyk applies the severity level set for **Unknown** to new licenses when Snyk adds them to your license policy.
{% endhint %}
