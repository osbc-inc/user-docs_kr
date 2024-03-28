# Level 2: 정책

The [Snyk AppRisk policies](../policies-for-snyk-apprisk/)은 비즈니스 컨텍스트를 추가하고 알림을 받는 프로세스를 자동화하는 데 도움이 됩니다. 커버리지 제어 격차를 자동으로 식별하도록 정책을 설정할 수 있습니다.

## 정책 이해

정책을 만들고 이해하려면 다음 두 가지 구성 요소가 필요합니다:

* **필터**: 태그 또는 자산 이름과 같은 정의된 기준을 기반으로 자산 그룹을 생성할 수 있습니다.
* **작업**: 필터링된 자산에 대해 수행할 수 있는 작업(예: 자산 분류 설정 또는 Slack 메시지 또는 이메일 전송)을 설정합니다. 새로 만든 정책이 표시되고 적용되는 데 최대 30분이 걸릴 수 있습니다.

{% hint style="info" %}
새로 만든 정책이 표시되고 적용되는 데 최대 30분이 걸릴 수 있습니다.
{% endhint %}

## 정책 만들기

Policy view로 이동하고 오른쪽 상단의 New policy버튼을 클릭하여 정책을 만들 수 있습니다. 정책의 이름을 지정하고 선택적으로 설명을 작성합니다.

정책 작성기 편집기는 다음 두 가지 주요 영역에 중점을 둡니다:

* [Define the filters](../policies-for-snyk-apprisk/create-policies.md#define-filters) - 자산 속성에 필터 조건을 설정합니다.
* [Set actions](../policies-for-snyk-apprisk/create-policies.md#set-actions) - 필터링된 자산에 대해 수행할 작업을 정의합니다.

### 주요 필터 유형 <a href="#key-filter-types" id="key-filter-types"></a>

새 정책을 만들 때 사용 가능한 여러 필터 중에서 선택할 수 있습니다. 가장 많이 사용되는 필터는 다음과 같습니다:

* **Name:** Many companies have a naming convention for their repositories and other assets. Use the naming convention to check if asset names contain or match a certain string.
* **Asset Type:** you can apply policies only to certain asset types, such as repositories or software packages.
* **Class:** you can reduce a lot of noise on actions by only targeting a specific Class. For example, only taking actions on Class A assets, as these are business-critical assets.
* **Tags:** You can use either out-of-the-box system tags or custom tags that Snyk has defined.

Here are the steps for creating a policy:

1. Navigate to the Policy view and click the **New policy** button in the top right corner.
2. Provide a name and, optionally, a description of your policy, and click **Next**.
3. Define the filters of your policy and click **Apply**.
4.  Set actions for your policy. Click the + icon to add an action. You can trigger an action based on the assets you have filtered or create a logic node to combine it with another filter node.

    <figure><img src="../../../.gitbook/assets/image (2).png" alt="Create policy - multiple nodes"><figcaption><p>Create policy - Multiple nodes</p></figcaption></figure>
5. When you add another filter node and select the + icon next to it, you can flow into existing logic nodes.
6.  Trigger an action based on the assets you have filtered.

    <figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Create policy - Set action</p></figcaption></figure>

### Policy freshness

All policies are automatically run in a maximum of 30 minutes after creation, then every 30 minutes. You can manually run a policy by clicking Run to apply the policy to your assets. Changes are applied automatically to your assets by implementing the actions you set on the policy.

### Use cases for policies

Familiarize yourself with the Snyk AppRisk policies by going through these use cases:

* [Coverage control](../policies-for-snyk-apprisk/use-cases-for-policies/coverage-control-policy-use-case.md) policy - identify and set coverage policies to allow your team to define where certain security controls need to be in place.
* [Classification](../policies-for-snyk-apprisk/use-cases-for-policies/classification-policy-use-case.md) policy - classify assets based on importance.
* [Tagging](../policies-for-snyk-apprisk/use-cases-for-policies/tagging-policy-use-case.md) policy - sets a tag on the matched assets.
* [Notification](../policies-for-snyk-apprisk/use-cases-for-policies/notification-policy-use-case.md) policy - get notifications about changes that take place on your assets.
* [Coverage and coverage gap](../policies-for-snyk-apprisk/use-cases-for-policies/coverage-and-coverage-gap-policies.md) policies - use the Coverage filter to verify if an asset has ever been tested by the product and the Coverage gap filter to verify if the asset meets the coverage requirements set in a Set coverage control policy.
