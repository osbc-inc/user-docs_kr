# 가시성 설정 및 조직 템플릿 구성하기

단일 조직을 만들든 템플릿을 만들어 여러 조직을 만들든 간에 구성해야 할 몇 가지 초기 설정이 있습니다.

{% hint style="info" %}
프로젝트 가져오기에 대해서는 [Import Projects](../../phase-3-gain-visibility/import-projects.md) 및 [Rollout](../../phase-5-initial-rollout-to-team/) 토론을 참조하세요.
{% endhint %}

## 템플릿을 사용하여 조직 구조 만들기

새 조직을 만들 때 설정 및 통합을 위한 모델로 사용할 기존 조직을 선택할 수 있습니다. 조직 만들기를 간소화하려면 전체 조직 구조를 만들기 전에 템플릿 조직을 구성하는 것이 좋습니다.

이 템플릿 기반 접근 방식을 사용하면 각 조직에 대해 각 통합을 수동으로 구성할 필요가 없으므로 상당한 시간을 절약할 수 있습니다.

Snyk에는 특정 템플릿 기능이 없습니다. **템플릿**이라는 조직을 만든 다음 이 조직을 완전히 구성하는 것이 좋습니다. 나중에 조직을 더 만들 때 **템플릿**이 있는 기존 조직의 설정을 기존 조직으로 복제하는 옵션을 사용할 수 있습니다.\


{% hint style="info" %}
**API를 사용하여 템플릿 만들기**\
API를 사용하여 조직을 만드는 경우에도 템플릿 기능을 사용할 수 있습니다. [snyk-api-import](../../../../snyk-api-info/other-tools/tool-snyk-api-import/) 도구를 사용하여 GitHub 조직과 같은 기존 소스에서 조직을 미러링하든, `sourceOrgId`를 제공하여 [API endpoints](https://snyk.docs.apiary.io/#reference/organizations/create-organization/create-a-new-organization)를 사용하든 상관없이 API를 사용하여 조직을 만드는 경우에도 템플릿 기능을 사용할 수 있습니다.
{% endhint %}

## 템플릿 조직 설정 구성

조직 템플릿에서 전체 조직 구조를 만들 때 복사하도록 선택할 수 있는 다양한 설정을 구성합니다:

* 모든 관련 통합(예: GitHub Enterprise, Docker Hub)\
  참고: 온프레미스 소스 코드 관리 도구가 있는 경우 통합을 사용하려면 [Snyk Broker](../../../../enterprise-configuration/snyk-broker/)를 구성하고 실행해야 합니다.
* 통합 설정(예: Snyk가 PR에서 테스트를 실행할지 여부 구성).
  * 새 Git 리포지토리 통합의 기본 설정에는 새로 등록한 PR에 대해 Snyk가 테스트를 실행하고 새로운 취약점이 발견되면 자동으로 PR을 등록하는 옵션이 포함되어 있습니다. 처음에는 이러한 설정을 비활성화하고 [예방 단계](../../phase-6-rolling-out-the-prevention-stage/)에서 이러한 기능을 도입할 준비가 되면 켜는 것이 좋습니다.
  * 다음 [연동](configure-integrations.md) 기능 섹션에서는 템플릿을 복사하기 전에 템플릿에 추가할 수 있는 연동 기능에 대해 설명합니다.
* 제품 설정(예: Snyk 코드 활성화)을 예로 들 수 있습니다.
  * 기본적으로 새 조직에 대해서는 Snyk Code가 비활성화되어 있습니다.
  * Git 리포지토리 통합을 통해 가져온 리포지토리의 SAST 스캔을 활성화하려면 프로젝트를 가져오기 전에 토글을 사용하여 Snyk Code를 활성화해야 합니다.
  * Snyk Code를 사용하다가 **프로젝트를 가져오기 전에 활성화하는 것을 잊은 경우, Snyk Code를 활성화하고 Git에서 코드를 다시 임포트**해야 합니다. [Snyk 코드 활성화하기](enable-snyk-code.md)를 참조하세요.
* 알림 설정(이메일 알림)
  * 프로젝트를 가져오는 동안 사용자가 많은 알림을 받지 않도록 처음에는 모든 그룹 및 조직 이메일 알림을 비활성화하는 것이 좋습니다.
  * 이렇게 하려면 새 조직에 대해서는 그룹 수준에서, 모든 기존 조직에 대해서는 조직 수준에서 알림을 비활성화하세요.

다음 표는 템플릿 조직에서 웹 인터페이스 또는 API를 사용하여 만든 새 조직으로 복사되는 내용을 보여줍니다.

<table><thead><tr><th width="466">모든 통합 및 해당 설정이 복사됩니다.</th><th>The following WILL NOT be copied</th></tr></thead><tbody><tr><td>소스 제어 통합</td><td>Snyk 서비스 계정</td></tr><tr><td>컨테이너 레지스트리 통합</td><td>회원</td></tr><tr><td>컨테이너 오케스트레이터 통합(Kubernetes)</td><td>프로젝트</td></tr><tr><td>PaaS 및 서버리스 통합</td><td>알림 기본 설정</td></tr><tr><td>알림 통합(Slack 및 Jira)</td><td></td></tr><tr><td>정책</td><td></td></tr><tr><td>설정 무시</td><td></td></tr><tr><td>언어 설정</td><td></td></tr><tr><td>코드형 인프라(IaC) 설정</td><td></td></tr><tr><td>Snyk 코드 설정</td><td></td></tr></tbody></table>

## 조직 템플릿 복제

조직을 만들고 구성한 후에는 새 조직을 만들 때 템플릿으로 사용하여 나머지 구조를 구축할 수 있습니다.
