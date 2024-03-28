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

* **Name:** 많은 회사들이 저장소 및 기타 자산에 대한 명명 규칙을 가지고 있습니다. 자산 이름에 특정 문자열이 포함되어 있는지 또는 일치하는지 확인하려면 명명 규칙을 사용하십시오.
* **Asset Type:** 정책은 리포지토리 또는 소프트웨어 패키지와 같은 특정 자산 유형에만 적용할 수 있습니다.
* **Class:** 특정 클래스만을 대상으로 하여 작업에 대한 많은 소음을 줄일 수 있습니다. 예를 들어, 클래스 A 자산은 비즈니스적으로 크리티컬한 자산이므로 작업만 수행합니다.
* **Tags:** 기본 제공 시스템 태그 또는 Snyk이 정의한 사용자 지정 태그를 사용할 수 있습니다.

다음은 정책을 만드는 단계입니다:

1. Policy view로 이동하고 오른쪽 상단 모서리에 있는 **New policy**를 클릭합니다.
2. Provide a name and, optionally, a description of your policy, and click **Next**.
3. 정책에 대한 이름과 설명(선택적)을 제공하고 **Apply**을 클릭합니다.
4.  정책에 대한 작업을 설정합니다. + 아이콘을 클릭하여 작업을 추가합니다. 필터링한 자산을 기반으로 작업을 트리거하거나 논리 노드를 만들어 다른 필터 노드와 결합할 수 있습니다.

    <figure><img src="../../../.gitbook/assets/image (2).png" alt="Create policy - multiple nodes"><figcaption><p>Create policy - Multiple nodes</p></figcaption></figure>
5. 다른 필터 노드를 추가하고 그 옆에 + 아이콘을 선택하면 기존 로직 노드로 유입될 수 있습니다.
6.  필터링한 자산을 기반으로 작업을 트리거합니다.

    <figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Create policy - Set action</p></figcaption></figure>

### Policy freshness

모든 정책은 생성 후 최대 30분 이내에 자동으로 실행되고 30분마다 실행됩니다. apply를 클릭하여 수동으로 정책을 실행하여 자산에 정책을 적용할 수 있습니다. 변경 사항은 정책에 설정한 작업을 구현하여 자산에 자동으로 적용됩니다.

### 정책에 대한 사용 사례

Snyk AppRisk 정책에 대해서 다음과 같은 사용 사례가 존재합니다:

* [Coverage control](../policies-for-snyk-apprisk/use-cases-for-policies/coverage-control-policy-use-case.md) policy - 팀이 특정 보안 제어가 필요한 위치를 정의할 수 있도록 커버리지 정책을 식별하고 설정합니다.
* [Classification](../policies-for-snyk-apprisk/use-cases-for-policies/classification-policy-use-case.md) policy - 중요도를 기준으로 자산을 분류합니다.
* [Tagging](../policies-for-snyk-apprisk/use-cases-for-policies/tagging-policy-use-case.md) policy - 일치하는 자산에 태그를 설정합니다.
* [Notification](../policies-for-snyk-apprisk/use-cases-for-policies/notification-policy-use-case.md) policy - 자산에서 발생하는 변경 사항에 대한 알림을 가져옵니다.
* [Coverage and coverage gap](../policies-for-snyk-apprisk/use-cases-for-policies/coverage-and-coverage-gap-policies.md) policies - 커버리지 필터를 사용하여 자산이 제품에서 테스트한 적이 있는지 확인하고 커버리지 갭 필터를 사용하여 자산이 커버리지 제어 정책 설정에 설정된 커버리지 요구 사항을 충족하는지 확인합니다.
