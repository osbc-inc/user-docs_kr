# Snyk Enterprise 플랜 시작하기

이 페이지에서는 피드백을 받고 승인을 얻기 위해, Snyk을 사용해 보는 데 여러 팀원을 참여시키는 방법을 살펴봅니다.

{% hint style="info" %}
무료 또는 팀 플랜으로 Snyk를 사용하고 있으며 Enterprise 플랜으로 업그레이드하는 방법에 대한 지침을 찾고 있는 경우, [Enterprise implementation guide](../implement-snyk/enterprise-implementation-guide/)를 참조하세요.
{% endhint %}

Snyk에는 전체 소프트웨어 개발 수명주기를 보호하는 데 도움이 되는 다양한 도구와 프로세스가 있습니다. Snyk을 사용하면 코딩하는 동안 스캔하거나, 작업하지 않을 때 코드를 모니터링할 수 있습니다. Snyk은 또한 Git 리포지토리 통합을 통해 프로젝트 전체의 문제에 대한 가시성을 제공하거나 플러그인, CLI 또는 선별된 컨테이너를 통해 CI/CD에 통합할 수 있습니다.

Snyk을 평가하거나 엔터프라이즈 배포를 계획하는 사용자와 대부분의 프로그래밍 언어의 경우, Snyk은 Git 저장소와 통합하여 시작할 것을 권장합니다.

{% hint style="info" %}
기술 스택, 환경 및 워크플로에 가장 적합한 도구는 개별 상황에 따라 다릅니다. 자세한 내용은 해당 언어별 [guide](../scan-with-snyk/supported-languages-and-frameworks/)를 참조하세요.
{% endhint %}

(현재 보안 성숙도 수준에서) 귀하와 귀하의 팀을 위한 소프트웨어 개발 수명 주기 내에서 최상의 통합 지점을 선택하는 방법에 대해 자세히 알아보려면, [Integrating Snyk at your company](https://learn.snyk.io/lesson/integrate-snyk-at-your-company/)을 참조하세요.

Snyk이 무엇을 할 수 있는지 알아보려면, **프로젝트를 사용해 보세요.**

이 페이지의 나머지 부분에서는 Git 저장소를 Snyk에 연결하는 방법과 해당 저장소에 있는 Snyk 프로젝트를 스캔하여 결과를 표시하는 방법을 설명합니다. 팀과 함께 Snyk 구현 프로세스를 시작하기 전에 Snyk의 작동 방식을 이해하는 데 중점을 둡니다.

{% hint style="info" %}
Snyk는 각 스캔 유형, Snyk 오픈 소스, 코드, 컨테이너 또는 IaC에 대해 매월 제한된 무료 테스트를 제공합니다. 무제한 테스트의 경우, 수행해야 하는 테스트 유형에 대한 유료 계획이 있고 해당 유형에 대한 설정이 활성화되어 있는지 확인하십시오.
{% endhint %}

## Snyk 계정 생성 또는 로그인

로컬 환경 내에서도 Snyk 기능을 사용하려면 Snyk 계정이 있어야 합니다. 프로젝트에 Snyk을 사용해 보려면, [Create a free account](../getting-started/quickstart/create-or-log-in-to-a-snyk-account.md). 기업에서 이미 Snyk을 사용하고 있는 경우 Single Sign-On을 사용하여 로그인하여 Snyk 계정을 제공할 수 있습니다. 자세한 내용은 [Log in to an existing account](../getting-started/quickstart/create-or-log-in-to-a-snyk-account.md#log-in-to-an-existing-account)을 참조하세요.

## Snyk 코드 활성화

Snyk에서 새 조직을 생성하면 SAST(Snyk Code) 스캔이 기본적으로 비활성화됩니다. Snyk에서는 첫 번째 프로젝트를 Snyk으로 가져오기 전에 Snyk Code 제품을 활성화할 것을 권장합니다.

1. **Settings > Snyk Code** 옵션을 선택합니다.
2. Snyk Code를 활성화하려면 토글을 클릭하세요. 그런 다음 **Save changes**을 클릭합니다.

## Snyk 프로젝트 추가

Git repository 통합을 연결하려면 Snyk 프로젝트를 추가하세요. 이 비디오는 그 과정을 보여줍니다.

{% embed url="https://thoughtindustries-1.wistia.com/medias/9hwr0bnvko" %}
프로젝트 비디오 추가
{% endembed %}

## 초기 Snyk 통합 설정 구성

Git 리포지토리가 연결되면(자세한 내용은 [See Git repository integrations (SCMs)](../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/) 참조), 자동으로 취약점에 대한 pull request를 확인하고 자동으로 생성하며, 종속성 업그레이드 pull request를 자동으로 생성하는 데 사용할 수 있는 자동화된 프로세스가 있습니다. Snyk에서는 처음에 이러한 옵션을 비활성화할 것을 권장합니다.

각 Snyk 프로젝트의 설정은 Snyk 조직 통합 설정에서 상속됩니다. 풀 요청에 대한 기본 Snyk 테스트, 자동 수정 풀 요청, 자동 종속성 업그레이드 pull request 및 Dockerfile 기본 이미지에 대한 자동 업데이트 설정이 비활성화되어 있는지 확인하려면 다음 단계를 따르세요. 팀이 이러한 옵션을 구현할 준비가 되면 돌아가서 이러한 설정을 활성화할 수 있습니다.

1. 왼쪽 탐색 메뉴에서 **통합** 페이지를 선택합니다.
2. Git 리포지토리 통합을 위한 **설정 톱니바퀴 아이콘**을 선택하세요.
3. **pull request에 대한 기본 Snyk 테스트** 섹션에서 다음이 비활성화되어 있는지 확인하세요 :
   1. **오픈 소스 보안 & 라이선스**(PR이 열릴 때 기본 확인)
   2. **자동 수정 pull request** : **새로운 취약점** 및 **알려진 취약점(백로그)** 모두
   3. **Dockerfile 기본 이미지 자동 업데이트**
   4. **자동 디펜던시 업그레이드 pull request**

{% hint style="info" %}
Snyk은 여러 프로젝트를 추가하기 전에 이러한 옵션에 대한 표준과 알림 기본값을 정의할 것을 권장합니다. 팀이 더 광범위한 구현을 준비할 때 Snyk는 보안 성숙도에 따라 이러한 옵션에 대한 표준을 정의할 것을 권장합니다. 자세한 내용은 [Configure integrations](../implement-snyk/enterprise-implementation-guide/phase-2-configure-account/set-visibility-and-configure-an-organization-template/configure-integrations.md)을 참조하세요.
{% endhint %}

## Snyk 스캔 결과 검토

오픈 소스 프로젝트의 경우 Snyk은 디펜던시 및 라이선스 구성 요소 문제에 대한 가시성을 제공합니다. 일부 패키지 관리자는 이 비디오에서 설명한 것처럼 특정 문제를 해결하기 위해 pull request를 열 수 있는 링크도 제공합니다.

{% embed url="https://thoughtindustries-1.wistia.com/medias/z0lcfht0na" %}
문제 해결 비디오
{% endembed %}

Snyk은 독점 코드의 잠재적인 보안 및 품질 문제에 대한 정보를 제공합니다. 또한 이 비디오에서 설명한 대로 권장 사항 및 일부 해결 사례를 제공합니다.

{% embed url="https://thoughtindustries-1.wistia.com/medias/p32o09thet" %}
코드 문제 검토 비디오
{% endembed %}

Snyk이 저장소에서 Dockerfile을 식별하면, Snyk은 감지된 취약점을 포함하여 기본 이미지에 대한 정보를 제공합니다. 또한 이 비디오에서 설명한 것처럼 기본 이미지를 더 안전한 이미지로 교체하기 위해 pull request를 여는 옵션을 제공합니다.

{% embed url="https://thoughtindustries-1.wistia.com/medias/3s7h3r9o8h" %}
기본 이미지 비디오 교체
{% endembed %}

Snyk이 저장소에서 Kubernetes 또는 Terraform 파일을 식별하면, Snyk은 구성에 대한 정보를 제공합니다. 다음 비디오는 Snyk이 제공하는 정보를 보여줍니다.

{% embed url="https://thoughtindustries-1.wistia.com/medias/l29m2dwrk8" %}
인프라 문제 검토 비디오
{% endembed %}

## Snyk CLI로 스캔

일부 패키지 관리자는 **로컬 환경의 컨텍스트에 의존**합니다. 이러한 패키지 관리자를 사용하면 **로컬 환경에서 또는 CI/CD 파이프라인의 일부로 스캔하면 가장 정확한 결과를 얻을 수 있습니다.**

Snyk CLI 또는 CI/CD 플러그인 사용을 시작하려면, [install the Snyk CLI](../snyk-cli/install-or-update-the-snyk-cli/). 설치한 후에는, 이 비디오에 설명된 대로 [authenticate your machine to associate the CLI with your Snyk account](../snyk-cli/authenticate-the-cli-with-your-account.md)

{% embed url="https://thoughtindustries-1.wistia.com/medias/ava7rrg7al" %}
CLI 비디오 인증
{% endembed %}

[**Snyk test**](../snyk-cli/scan-and-maintain-projects-using-the-cli/snyk-cli-for-open-source/)를 사용한 스캔은 이 비디오에서 설명한 대로 수정 조언을 포함하여 오픈 소스 패키지 문제에 대한 정보를 제공합니다.

{% embed url="https://thoughtindustries-1.wistia.com/medias/b8vrvtmnbu" %}
Snyk 테스트 영상
{% endembed %}

[**Snyk code test**](../snyk-cli/scan-and-maintain-projects-using-the-cli/snyk-cli-for-snyk-code/)를 사용한 스캔은 해당 프로젝트의 코드에 대해 정적 코드 분석 테스트를 실행합니다. 그리고 감지된 취약성 문제 목록, 테스트에 대한 일반 정보 및 테스트 결과 요약을 반환합니다.

[**Snyk container test**](../snyk-cli/scan-and-maintain-projects-using-the-cli/snyk-cli-for-snyk-container/)를 사용한 스캔은 기본 이미지를 더 안전한 이미지로 업그레이드하기 위한 권장 사항과 함께 컨테이너 이미지의 취약점 목록을 반환합니다.

[**Snyk iac test**](../snyk-cli/scan-and-maintain-projects-using-the-cli/snyk-cli-for-iac/)를 사용한 스캔은 코드 파일로서의 인프라에서 발견된 문제를 해결하는 방법에 대한 조언을 반환합니다.

## Snyk Enterprise 계획 구현의 다음 단계

* 개발자가 IDE 또는 CLI를 사용하여 로컬 환경에서 Snyk를 사용해 보기를 원하는 경우, [Walkthrough: Initiate a scan locally](../implement-snyk/walkthrough-initiate-a-scan-locally.md).
* 귀하의 기술 스택에 대한 구체적인 권장 사항을 얻으려면 귀하의 언어에 해당하는 가이드를 방문하세요.
* 더 많은 팀에 Snyk 출시를 계획할 준비가 되면, [Enterprise implementation guide](../implement-snyk/enterprise-implementation-guide/)를 검토하여 자세한 내용을 알아보세요.
* Snyk를 더 많은 청중에게 출시하기 위한 추가 전략, 커뮤니케이션 템플릿 및 체크리스트는 [Developer launch package](https://assets.ctfassets.net/4un77bcsnjzw/2YfaqJNMsogGNJM6BBQz4p/8f5ca77b9c40a1bbe14cc9fb0aa05462/Snyk-developer-launch-package.pdf)를 참조하세요.
