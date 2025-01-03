# 검색 및 필터 기능

Snyk AppRisk는 강력한 검색 및 필터링 기능을 제공하여 조사 및 완화를 위한 자산의 범위를 좁힐 수 있도록 지원합니다.

## 검색 기능

검색 바를 사용하여 다양한 자산 속성에서 특정 키워드를 검색할 수 있습니다. 결과에는 자산 이름뿐만 아니라 자산의 속성 탭에서 검색한 데이터도 포함될 수 있습니다.

## 필터 기능

이 기능을 사용하면 필터를 정의하고 매우 특정한 기준에 따라 자산을 필터링할 수 있습니다. 예를 들어 이름에 `AWS`가 있고 **A** 또는 **B**로 분류되며 실행된 컨트롤로 Snyk IaC가 없는 저장소 자산을 찾을 때 유용할 수 있습니다.

화면 왼쪽 위에서 Filters를 클릭합니다. 새 필터를 추가할 수 있는 팝업이 표시됩니다. 필터 기능을 사용하면 다음과 같이 하나 이상의 기준 집합을 지정할 수 있습니다:

* 자산의 **속성**(예: 자산 이름, 클래스, 실행된 컨트롤).
* **조건**은 선택한 자산 (`asset name`에 포함하거나 포함하지 않음)에 따라 달라집니다.
* **값**은 속성과 조건에 따라 다릅니다.

<figure><img src="../../../.gitbook/assets/inventory8.png" alt="AppRisk - Filters"><figcaption><p>Snyk AppRisk - Filters</p></figcaption></figure>

필요한 만큼 필터를 추가할 수 있습니다. 다른 필터를 추가하려면 **Add Filter**를 클릭하고 조건을 **And** 또는 **Or**로 설정하고 Property, Condition, Value 필드를 지정합니다.

필터링 옵션에는 다음과 같은 항목이 있습니다:

* **Name** - 자산을 이름별로 필터링합니다.
* **Tags** - 특정 범주(예: 태그)를 기준으로 자산을 필터링합니다. 자산에는 활성/비활성 자산 추적, 특정 기술별 필터링 등 다양한 사용 사례에 대한 기본 태그가 있습니다. 그 위에 사용자는 자신의 논리에 따라 자산에 태그를 지정하는 정책 규칙을 만들 수 있습니다.
* **Discovered** - 자산이 발견된 이후 지속 기간에 따라 필터링합니다.
* **Locked attributes** - 잠금 속성이 있는 자산을 필터링하여 정책의 영향을 받지 않는 자산을 식별합니다.
* **Coverage and Coverage gap -** 대부분 스캔 적용 범위 질문에 답하는 데 사용됩니다.
  * **Coverage** 자산이 과거 어느 시점에 이 제품으로 테스트되었음을 의미합니다.
  * **Coverage gap** 은 자산이 커버리지 제어 정책 설정에서 **설정한 커버리지 요구 사항**을 충족하지 않음을 의미합니다.

{% hint style="info" %}
Snyk AppRisk를 처음 사용하는 경우 **커버리지** 필터부터 시작하여 현재 Snyk 구현 위치를 확인합니다.
{% endhint %}
