# Level 1: Snyk AppRisk 구성 및 설정

모든 인벤토리 코드 기반 자산을 식별하고 보안 제어가 설정된 자산을 탐지하여 AppRisk 온보딩을 시작합니다.

## Access Snyk AppRisk

[Snyk Web UI](../../../getting-started/explore-snyk-through-the-web-ui.md)에서 Snyk AppRisk에 액세스할 수 있습니다.

* Snyk 그룹의 그룹 level에서 Snyk AppRisk에 액세스합니다.
* 그룹 관리자 권한이 있는지 확인합니다.
* Snyk AppRisk 버튼을 클릭하여 Snyk AppRisk를 시작합니다.
* 브라우저의 새 탭이 열리고 Snyk AppRisk [Dashboard](../dashboard-for-snyk-apprisk.md)가 표시됩니다.

## 설치 및 integrations <a href="#setup-integrations" id="setup-integrations"></a>

Snyk AppRisk에 올바르게 액세스할 수 있는지 확인한 후 integration 설정하여 자산 인벤토리 구축을 시작할 수 있습니다.

{% hint style="info" %}
Snyk AppRisk를 활성화한 후 2시간 이내에 Snyk 스캔 정보가 자동으로 가져옵니다.
{% endhint %}

Integrations view에서 integration에 액세스하고 구성할 수 있습니다. 사용 가능한 모든 integration 목록을 보려면 Integration Hub 옵션을 선택하십시오. integration 구성에 대한 자세한 내용은 [Using the Integration Hub](../integrations-for-snyk-apprisk/#using-the-integration-hub) 섹션에서 확인할 수 있습니다.

Integrations view의 기본 표시에는 구성된 Snyk integrations에 포함됩니다. 각 integration의 **Connected** 또는 **Not Connected**는 Snyk으로 가져온 특정 내용에 따라 달라집니다.

Integrations view는 기존 [integration을 사용자 정의](../integrations-for-snyk-apprisk/customize-an-integration.md)하거나 새 [SCM integration을 연결](../integrations-for-snyk-apprisk/connect-an-scm-integration.md)할 수 있으므로 필요에 맞게 구성할 수 있습니다.

<figure><img src="../../../.gitbook/assets/image (357).png" alt="Snyk AppRisk - Integration Hub option displaying the list of available integrations"><figcaption><p>Snyk AppRisk - 사용 가능한 integrations 목록을 표시하는 Integration Hub 옵션</p></figcaption></figure>

Integration Hub를 클릭하면 사용 가능한 integrations 목록이 표시됩니다. 각 integrations에 대해 하나 또는 여러 프로파일을 추가할 수 있습니다.

### SCM integrations

SCM integrations를 구성하려면 Snyk AppRisk Integrations Hub를 사용합니다. 이 인터페이스는 Organization 통합 인터페이스와 별도로 Snyk AppRisk 전용 별도의 integrations 인터페이스입니다.

각 Snyk Organization에서 관리자는 개발자가 사용하는 애플리케이션에 제한된 액세스 권한을 가진 토큰을 제공할 수 있습니다.

Snyk AppRisk에서 사용되는 토큰의 범위는 Snyk로 가져온 것과 비교하여 기존 자산의 overview를 제공합니다.

지원하는 SCM 통합은 다음과 같습니다:

* GitHub
* GitLab
* Azure DevOps (Azure Repos)
* BitBucket

지원하는 SCM integrations에 대한 자세한 내용은 [Connect an SCM integration](../integrations-for-snyk-apprisk/connect-an-scm-integration.md)에서 확인할 수 있습니다.

### Brokered SCM integration <a href="#brokered-scm-integration" id="brokered-scm-integration"></a>

[Snyk Broker](../../../enterprise-configuration/snyk-broker/)를 설정할 때 새 브로커를 설치하거나 기존 Snyk Broker 연결을 업데이트하는 것과 관련하여 몇 가지 확인사항이 있습니다:

* API Rate Limit 문제가 발생하고 있습니까?
* 모든 관련 SCM 저장소에 액세스할 수 있는 사용자에게 SCM 토큰을 업데이트해야 합니까?
* 1000개 이상의 저장소가 있습니까?

위의 질문 중 하나에 해당하는 경우 새 Snyk Broker를 배포하여 Snyk AppRisk SCM 연결이 필요합니다.

{% hint style="info" %}
Snyk은 특히 Snyk AppRisk Broker를 위해 Snyk에 새로운 조직을 만들 것을 권장합니다.
{% endhint %}

Snyk Broker를 사용하여 Snyk AppRisk를 설치하고 구성하는 방법에 대한 자세한 내용은 [Snyk Broker - AppRisk](../../../enterprise-configuration/snyk-broker/snyk-broker-apprisk.md)에서 확인할 수 있습니다.

## 특징

자신의 화면에서 다양한 Snyk AppRisk 기능에 액세스할 수 있으므로 한 번에 각 기능에 집중할 수 있습니다.

* [Dashboard](../dashboard-for-snyk-apprisk.md)
* [Inventory](../inventory-for-snyk-apprisk/)
* [Policies](../policies-for-snyk-apprisk/)
* [Integrations](../integrations-for-snyk-apprisk/)

#### Inventory view

Inventory 기능은 4개의 섹션으로 구성되며, 각 섹션은 특정 영역에 중점을 둡니다:

* **Code assets**: 저장소에서 찾을 수 있는 모든 저장소 자산 및 패키지 자산 목록을 제공합니다. 코드 자산 보기에서 사용할 수 있는 모든 옵션에 대한 자세한 개요를 보려면 [인벤토리 기능](../inventory-for-snyk-apprisk/inventory-capabilities.md) 페이지로 확인하고 필터링 옵션 및 사용 방법에 대한 자세한 내용은 [필터 기능](../inventory-for-snyk-apprisk/inventory-capabilities.md) 페이지에서  확인합니다.
* **Organization teams**: 팀별로 그룹화된 리포지토리 자산 목록을 제공합니다. 팀과 리포지토리가 팀에 할당된 SCM 조직만 이 레이아웃에 나타납니다.
* **Technology**: Snyk AppRisk에서 탐지하고 태그를 지정한 기술별로 그룹화된 리포지토리 자산 목록을 제공합니다.
* **Type**: 검색한 모든 자산을 유형별로 그룹화한 목록을 제공합니다.

Snyk AppRisk를 처음 사용하는 경우 먼저 커버리지 필터를 사용하여 현재 Snyk를 구현한 위치를 확인할 것을 권장합니다. 그런 다음 커버리지 갭 필터를 사용하여 커버리지 제어 정책에서 **설정한 커버리지 요구 사항**을 충족하지 않는 자산을 식별할 수 있습니다.

Coverage Gap 필터를 사용하여 다음 작업을 수행할 수 있습니다:

*   적용 범위를 설정하여 제어 정책 요구 사항을 준수하지 않는 자산을 찾습니다:

    <figure><img src="../../../.gitbook/assets/image.png" alt="Use the Coverage gap filter to Find any asset that is out of policy"><figcaption><p>Coverage gap - Use case 1</p></figcaption></figure>
*   Find any assets that do not meet the coverage requirements for Snyk Open Source or Snyk Code, or both of them simultaneously:

    <figure><img src="../../../.gitbook/assets/image (1).png" alt="Use the Coverage gap filter to Find any asset that is out of policy for Snyk Open Source OR Snyk Code"><figcaption><p>Coverage gap - Use case 2</p></figcaption></figure>

#### Tags <a href="#hardbreak-tags" id="hardbreak-tags"></a>

태그를 사용하여 자산을 분류할 수 있습니다. 태그는 여러 가지 방법으로 사용할 수 있습니다:

* Automatic tags: Snyk AppRisk는 저장소 및 저장소 최신 업데이트에 있는 사용된 기술(Python, Terraform 등)에 대한 정보로 저장소 자산에 자동 태그를 지정합니다. 또한 정책을 사용하여 저장소 및 패키지 자산에 태그를 지정할 수 있습니다. GitHub 및 GitLab 항목을 저장소에서 끌어다 Snyk AppRisk의 자산 태그로 적용할 수도 있습니다.
* User Defined tags: 정책을 통해 사용자 정의 태그를 설정하여 시스템에서 생성된 태그를 넘어 자산을 분류할 수 있습니다. 자세한 내용은 [Create policies](../policies-for-snyk-apprisk/create-policies.md)를 참조하십시오.

#### Dashboard

대시보드를 사용하여 응용프로그램 및 보안 제어에 대한 간략한 개요를 확인할 수 있습니다. 기본 위젯을 사용하고 필요에 따라 표시된 정보를 사용자 지정하거나 필요에 따라 새 위젯을 추가할 수 있습니다. 자세한 내용은 [Dashboard for Snyk AppRisk](../dashboard-for-snyk-apprisk.md)를 참조하십시오.

사용 가능한 대시보드 위젯은 다음과 같습니다:

* **SAST coverage**: Snyk Code 및 Snyk Infrastructure as Code에서 적용 중인 리포지토리를 확인합니다.

{% hint style="info" %}
SAST coverage 위젯은 OR 문을 사용하는데, 이는 저장소가 Snyk Code 또는 Snyk Infrastructure as Code에도 적용되는 경우 SAST에 적용된다는 것을 의미합니다.
{% endhint %}

* **SCA coverage**: 적용 대상이 되는 리포지토리와 Snyk Open Source 및 Snyk Container인지 확인합니다. Snyk Open Source 적용 범위 또는 Snyk Container 적용 범위를 보려면 위젯을 편집할 수 있습니다.

{% hint style="info" %}
The SCA coverage 위젯은 OR 문을 사용하는데, 이는 저장소가 Snyk Open Source OR Snyk Container에도 적용되는 경우 SCA에 적용된다는 것을 의미합니다.
{% endhint %}

* **소스별 리포지토리 분석**: SCM integrations (Azure DevOps(Azure Repos), Gitlab, GitHub, BitBucket)을 사용하여 Snyk AppRisk가 검색한 리포지토리를 확인합니다. 기타 범주는 Snyk가 검색했지만 SCM 리포지토리와 관련이 없는 리포지토리입니다.
* **기술 내역**: Snyk가 발견한 저장소의 상위 기술(언어) 태그를 확인합니다.
* **유형별 자산 내역**: 자산이 저장소인지 패키지인지 확인합니다.
* **리포지토리 활동**: 리포지토리가 활성, 비활성 또는 휴면 상태인지 확인합니다.
