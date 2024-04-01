# 인벤토리 성능

각 인벤토리 레이아웃은 사용 가능한 주요 속성을 자세히 설명하는 표 형식으로 제공됩니다:

* [자산](inventory-capabilities.md#undefined)
* [커버리지 컨트롤](inventory-capabilities.md#undefined-1)
* [태그](inventory-capabilities.md#undefined-2)
* [개발자](inventory-capabilities.md#undefined-3)
* [클래스](inventory-capabilities.md#undefined-4)

## 자산

자산 열에는 저장소 자산의 이름, 패키지 또는 스캔한 아티팩트 및 Git 원격 URL(사용 가능한 경우)이 포함됩니다. 스캔한 아티팩트에는 Git 원격 URL이 없습니다.

자산은 여러 항목의 상위 항목이 될 수 있습니다. 상위 자산 이름 옆에 있는 화살표를 클릭하여 포함된 모든 항목의 목록을 확장합니다.

인벤토리 레이아웃에서 자산의 이름을 클릭하여 자산에 대해 자세히 알아봅니다. 팝업 화면에 해당 자산에 대한 모든 관련 정보가 표시됩니다.

자산 정보는 다음 탭으로 나뉩니다:

* **Summary** - 자산 속성을 집중적으로 볼 수 있습니다.

<figure><img src="../../../.gitbook/assets/Inventory2.png" alt="AppRisk Inventory - Assets Summary view"><figcaption><p>Snyk AppRisk Inventory - Assets Summary view</p></figcaption></figure>

* **Attributes** - 데이터 원본에서 가져왔지만 전용 열이 없는 기타 속성입니다. 이러한 정보를 갖는 것의 이점은 단순히 정보를 표시하는 것뿐만 아니라 대부분 검색 가능하게 만드는 것입니다. 인벤토리 서치바 또는 필터를 사용하여 속성을 검색할 수 있습니다.

<figure><img src="../../../.gitbook/assets/inventory3.png" alt="AppRisk - Assets Attributes window"><figcaption><p>Snyk AppRisk - Assets Attributes window</p></figcaption></figure>

자산의 이름을 복사하거나 저장소를 찾을 수 있습니다. 자산을 클릭하면 행의 끝에 메뉴가 나타납니다. 메뉴를 클릭한 다음 **Copy** 또는 **Browse**를 선택합니다.

<figure><img src="../../../.gitbook/assets/inventory4 (1).png" alt="AppRisk - Asset options"><figcaption><p>Snyk AppRisk - Asset options</p></figcaption></figure>

## 커버리지 컨트롤

컨트롤 열에는 특정 저장소 자산에서 실행된 모든 Snyk 제품이 표시됩니다. 이 열에는 각 Snyk 제품의 로고가 원형으로 표시됩니다.

컨트롤 로고는 다음 중 하나의 상태를 가질 수 있습니다:

| Logo                                                                                   | Description                       |
| -------------------------------------------------------------------------------------- | --------------------------------- |
| <img src="../../../.gitbook/assets/image (3) (5) (1).png" alt="" data-size="original"> | Snyk 제품이 실행되었습니다.                 |
| <img src="../../../.gitbook/assets/image (4) (7) (1).png" alt="" data-size="original"> | Snyk 제품이 실행되었지만 문제가 있습니다.         |
| <img src="../../../.gitbook/assets/image (5) (3) (1).png" alt="" data-size="original"> | Snyk 제품이 실행되었어야 하는데 실행되지 않았습니다.   |
| <img src="../../../.gitbook/assets/image (6) (6) (1).png" alt="" data-size="original"> | Snyk 제품이 실행하고 실패했습니다.             |
| <img src="../../../.gitbook/assets/image (7) (4).png" alt="" data-size="original">     | Snyk 제품이 실행되고 문제가 발생하여 실패했습니다.    |
| <img src="../../../.gitbook/assets/image (8) (3).png" alt="" data-size="original">     | Snyk 제품이 실행되어 정책에 적용되지 않아 실패했습니다. |

컨트롤 로고를 클릭하면 **Last test** details를 볼 수 있습니다. 이는 특정 제품에 의해 자산이 스캔된 가장 최근 시간을 반영합니다.

<figure><img src="../../../.gitbook/assets/inventory5.png" alt="AppRisk - Controls"><figcaption><p>Snyk AppRisk - Controls</p></figcaption></figure>

## 태그

Policies를 통해 저장소 자산 태그를 추가하거나 Snyk AppRisk에서 시스템 생성하여 더 많은 컨텍스트를 제공할 수 있습니다. 모든 태그를 보려면 태그 필드를 클릭하십시오.

시스템에서 생성된 태그에는 다음과 같은 정보가 포함됩니다:

* **Technology** - 저장소 자산 내의 소스 코드에서 Snyk AppRisk에서 탐지된 언어입니다.
* **SCM Topic** - 통합 SCM 저장소에서 찾을 수 있는 토픽. Snyk AppRisk는 현재 GitHub 및 GitLab의 토픽을 지원합니다.
* **Repository freshness** - 저장소의 상태 및 마지막 커밋 날짜입니다.
  * **Active**: 최근 3개월 동안 커밋이 있었습니다.
  * **Inactive**: 마지막 커밋이 지난 3개월에서 6개월 사이에 이루어졌습니다.
  * **Dormant**: 최근 6개월 동안 커밋이 없습니다.

<figure><img src="../../../.gitbook/assets/inventory6.png" alt="AppRisk - Tags"><figcaption><p>Snyk AppRisk - Tags</p></figcaption></figure>

## 개발자

특정 자산에 대해 작업한 모든 개발자의 목록을 볼 수 있습니다. 세부 정보 목록에는 저장소 자산에 대한 코드 커밋에 대한 SCM 프로파일 세부 정보가 포함됩니다.

<figure><img src="../../../.gitbook/assets/image (10) (4).png" alt="AppRisk - Developers"><figcaption><p>AppRisk - Developers</p></figcaption></figure>

## 클래스

정책 보기에서 정의한 대로 자산의 비즈니스 중요도를 A(가장 중요함)에서 D(가장 중요하지 않음)까지 반영합니다.

자산의 비즈니스 중요도를 수동으로 변경할 수 있습니다. 중요도 수준을 클릭하고 목록에서 다른 항목을 선택합니다.

수동으로 클래스 값을 설정한 후에는 자산 클래스 설정을 작업으로 하는 정책에 의해 우선되는 가능성을 방지하기 위해 값을 잠글 수 있습니다. 자산의 general 또는 summary views에서 값을 잠글 수 있습니다. 잠금 아이콘을 클릭하여 언제든지 클래스 값을 잠금 해제할 수 있습니다. 값 잠금 해제에 대한 확인을 요청하는 팝업이 표시됩니다.

<figure><img src="../../../.gitbook/assets/Code Asset - Lock Class.png" alt="Snyk AppRisk - Lock the value of a class"><figcaption><p>Snyk AppRisk - Lock the value of a class</p></figcaption></figure>

Asset Class 열은 위험 기반 우선순위 지정을 위해 Insights UI에서도 사용할 수 있으며 여기와 동일한 기능을 가지고 있습니다. 현재 Asset Class 열은 저장소 자산에만 사용할 수 있으며 Snyk Code에만 적용할 수 있습니다.

{% hint style="info" %}
Asset Class와 Insights UI 간의 동기화는 최대 3시간이 소요될 수 있습니다.
{% endhint %}

클래스 값은 정책을 사용하여 자동으로 생성할 수 있습니다. 자산 클래스 설정을 작업으로 하는 정책을 생성하기만 하면 됩니다.

<figure><img src="../../../.gitbook/assets/inventory7.png" alt="AppRisk - Class"><figcaption><p>Snyk AppRisk - Class</p></figcaption></figure>

###

