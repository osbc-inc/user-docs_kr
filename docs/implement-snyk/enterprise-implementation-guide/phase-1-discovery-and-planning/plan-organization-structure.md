# 계획 조직 구조

## 구조 소개

<div align="left"><figure><img src="../../../.gitbook/assets/determine-account-structure.png" alt="Determine your account structure" width="563"><figcaption><p>계정 구조 결정</p></figcaption></figure></div>

Snyk은 자산, 액세스 및 롤업 보고를 관리하기 위해 계층적 접근 방식을 사용합니다.

* **Snyk 그룹**: 최상위 레벨
  * 일반적으로 계정을 나타내며 회사 이름입니다.
  * 규모가 큰 고객은 각 회사를 대표하는 여러 그룹을 보유할 수 있습니다.
* S**nyk 조직:** 그룹 수준 이하로, 일반적으로 다음을 대표합니다.
  * 사업 분야
  * Git 조직 또는 팀 구조
  * 애플리케이션 유형
  * 개발 팀
* **Snyk 프로젝트**
  * Snyk으로 테스트하고 모니터링한 가져오기입니다.
  * 모니터링 중인 CLI 스캔, 레지스트리 또는 Kubernetes에서 모니터링 중인 컨테이너 또는 오픈 소스 매니페스트, 코드 분석 스캔 또는 인프라스트럭처로서의 코드 파일과 같이 Git 가져오기 중에 감지된 자산이 감지된 경우입니다.

자세한 내용은 [그룹 및 조직 관리하기](../../../snyk-admin/manage-groups-and-organizations/)를 참조하세요.

## 구조 결정

구조를 결정하는 것은 가장 먼저 해야 할 결정 중 하나입니다. 계정 구조를 결정할 때는 비즈니스 요구사항에 맞게 Snyk 조직을 구성하세요.

조직을 구성할 때는 다음과 같은 다양한 요소를 고려하세요:

* 팀 기반 구조: 개발자 팀 A와 조직 팀 A를 연결합니다.
* 제품 기반 구조:
  * 결제 프런트엔드, 결제 백엔드 등 애플리케이션의 각 부분에 대해 별도의 조직을 설정합니다.
  * 풀스택 개발자가 필요에 따라 여러 조직에 참여할 수 있도록 허용합니다.
* Git 조직 기반: 일부 회사는 Git의 조직을 모방한 구조를 사용하며, 일반적으로 고객이 Git 플랫폼에 10개 이상의 조직을 보유하고 있는 경우 볼 수 있습니다.

{% hint style="info" %}
[api-import-tool](../../../snyk-api-info/other-tools/tool-snyk-api-import/)을 사용하려는 경우 Git 조직 기반 접근 방식이 앞으로 나아갈 길입니다.
{% endhint %}

이러한 옵션을 살펴보고 회사의 요구 사항을 파악하여 협업과 효율성을 향상시키는 계정 구조를 구축할 수 있습니다.

## 추가 정보

자세한 내용은 [조직 관리](../../../snyk-admin/manage-groups-and-organizations/create-and-delete-organizations.md)를 참조하세요.
