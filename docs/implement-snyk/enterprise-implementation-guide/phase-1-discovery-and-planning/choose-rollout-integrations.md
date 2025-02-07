# 롤아웃 통합 선택

## **SDLC** 통합 포인트

Snyk은 SDLC의 모든 단계에서 Snyk과 원활하게 연동할 수 있는 다양한 통합 기능을 제공합니다.

많은 기업이 자동화된 솔루션을 먼저 배포한 다음 개발자가 사용할 수 있는 도구를 천천히 도입합니다. 또한 게이팅 기능은 일정 기간에 걸쳐 점진적으로 사용하도록 설정하여 업무 중단을 최소화합니다.

{% hint style="info" %}
여러 통합 기능을 사용하면 이슈가 중복 보고될 수 있으므로 처음에는 두 개 이상의 통합 유형을 구현할 필요가 없습니다. 예를 들어 Git 리포지토리로 모든 것을 가져오는 것으로 시작한 다음 나중에 CI/CD 보기를 사용하여 세분화된 세부 정보를 확인할 수 있습니다. 두 가지 보기를 모두 원하지 않는 경우 소스 제어 통합을 제거할 수 있습니다.
{% endhint %}

## 통합 유형

다음은 일반적인 초기 통합 사례입니다.

### SCM(소스 코드 관리) 통합

GitHub, GitLab, Azure Repos, Bitbucket 등 널리 사용되는 버전 제어 플랫폼과의 통합을 통해 코드 검토 프로세스에 Snyk 보안 검사를 원활하게 통합할 수 있습니다. 이를 통해 코드가 메인 브랜치에 병합되기 전에 잠재적인 취약점을 식별하고 해결할 수 있습니다. 중요한 기능은 다음과 같습니다:

* 특정 브랜치(일반적으로 개발 브랜치)에 대한 일일 테스트 및 모니터링
* (선택 사항) 리포지토리의 모든 브랜치에 대한 풀 리퀘스트/병합 리퀘스트 검사
* (선택 사항) 풀 리퀘스트를 통한 자동화된 종속성 업그레이드 및 자동화된 보안 수정 업그레이드

SCM 통합의 장점은 다음과 같습니다:

* 리포지토리 보안 상태에 대한 가시성 확보
* 코드 변경 시 자동 스캔
* 개발자에게 문제에 대한 즉각적인 피드백 제공
* UI 또는r [API/API Import 도구](https://docs.snyk.io/snyk-api-info/other-tools/tool-snyk-api-import)를 통해 온보딩 리포지토리 구성 가능
* Snyk Enterprise 플랜에서 클라우드 및 비공개 코드 리포지토리 지원

자세한 내용은 [Git 리포지토리(SCMs)](../../../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/)를 참조하세요.

온프레미스 Git 리포지토리가 있는 경우, 리포지토리와 통신할 수 있도록 Snyk용 [Snyk Broker](https://docs.snyk.io/snyk-admin/snyk-broker)를 배포하는 것을 고려해야 합니다.

{% hint style="info" %}
기업 고객은 API를 통해 [Snyk Broker](https://docs.snyk.io/enterprise-setup/snyk-broker)를 활성화하고 관리할 수 있습니다.

[유료 서비스](broken-reference/)를 통해 Snyk Broker 배포를 지원할 수 있습니다.
{% endhint %}

### 지속적 통합/지속 배포(CI/CD) 파이프라인 통합

Jenkins, Travis CI, CircleCI와 같은 CI/CD 파이프라인에 Snyk을 통합하면 빌드 및 배포 프로세스 중 보안 검사를 자동화할 수 있습니다. 이를 통해 소프트웨어 개발 수명 주기 초기에 취약점을 발견하고 프로덕션으로 전파되는 것을 방지할 수 있습니다. 일반적인 기능은 다음과 같습니다:

* (선택 사항) 빌드 중 수동적으로 결과를 모니터링하고 Snyk에서 결과를 볼 수 있는 기능
* (선택 사항) 지정한 기준에 따라 결과가 발견되면 빌드를 테스트하고 잠재적으로 중단할 수 있는 기능

CI/CD 통합의 장점은 다음과 같습니다:

* 로컬 코드 취약성 평가
* 테스트에 대한 완전한 제어: 빌드 스크립트에서 실행할 테스트와 위치 지정
* 원하는 경우, CI/CD를 통한 자동화

자세한 내용은 [Snyk CI/CD 통합](../../../integrate-with-snyk/snyk-ci-cd-integrations/)을 참조하세요.

### IDE 통합

개발자는 Visual Studio Code, IntelliJ IDEA, Eclipse와 같은 통합 개발 환경(IDE)과의 통합을 통해 코딩 환경 내에서 바로 Snyk 보안 기능에 액세스할 수 있습니다. 이를 통해 개발자가 코드를 작성할 때 실시간으로 스캔하고 문제를 해결할 수 있습니다.

자세한 내용은 [IDE에서 Snyk 사용](../../../integrate-with-snyk/ide-tools/)을 참조하세요.

## import 전략에 대한 고려 사항

<table><thead><tr><th width="200">프로젝트 Import 전략</th><th>고려 사항</th><th>장점</th><th>단점</th></tr></thead><tbody><tr><td>CLCLI(CI/CD로 자동화)</td><td>Has to be CI/CD 내에서 각 애플리케이션에 대해 구성해야 합니다.</td><td><ul><li>테스트 대상 및 시기 선택 가능: 어떤 패키지 관리자, 프로세스 내 어디에서, 어떤 언어를 분석할지 선택 가능</li><li>통합을 위한 개발 노력이 필요할 수 있음</li></ul></td><td>애플리케이션별로 구성이 필요합니다.</td></tr><tr><td>CLI(사용자가 로컬에서 실행)</td><td>개발자가 애플리케이션을 작업하는 동안 로컬에서 테스트를 수행하는 데 사용할 수 있으며, 스캔 유형별로 매우 다양하게 구성할 수 있습니다.</td><td>로컬 사용 사례</td><td>가시성 또는 자동화를 위한 것이 아닙니다. 빌드 가능한 코드 또는 종속성을 설치해야 할 수 있습니다(예: 잠금 파일이 없는 Gradle, Scala).</td></tr><tr><td>API</td><td><ul><li>일반적으로 고급 사용 사례에 적합합니다.</li><li>CI/CD 워크플로 또는 사용자 지정 도구에 통합.</li></ul></td><td>CI/CD 파이프라인에 자동화된 통합CI/CD pipelines</td><td>API에 익숙해야 하며, Enterprise 요금제를 통해 액세스해야 합니다.</td></tr><tr><td>Git 코드 리포지토리 통합</td><td>온보딩 및 일일 모니터링에 사용: 애플리케이션 포트폴리오 전반의 신속한 취약성 평가</td><td><ul><li>작업하지 않을 때에도 리포지토리에 대한 지속적인 모니터링</li><li>팀을 위한 중앙 집중식 가시성</li><li>지정된 브랜치 모니터링</li><li>코드를 빌드할 필요가 없음</li></ul></td><td><ul><li>UI를 통해 시작할 수 있지만, 대규모 포트폴리오는 <a href="https://docs.snyk.io/snyk-api/other-tools/tool-snyk-api-import">Api Import 도구</a>로 리포지토리 온보딩을 시작하기 위해 API를 사용해야 합니다. </li><li>일부 언어/패키지 관리자는 CLI 사용을 통해 더 나은 해상도를 제공합니다: 잠금 파일이 없는 Gradle, Scala</li></ul></td></tr><tr><td></td><td><ul><li>Pull request (풀 리퀘스트(PR)/병합 리퀘스트(MR) 스캔</li></ul></td><td><ul><li>리포지토리의 모든 브랜치에 대해 PR/MR에 도입된 이슈에 대해 즉각적인 피드백 제공</li></ul></td><td>합격/불합격에 대한 구성 가능한 규칙</td></tr></tbody></table>

## 통합 시 추가 고려 사항

### 인프라를 코드로 통합

코드형 Snyk 인프라의 경우, Terraform 또는 yaml 구성 파일이 SCM에 보관되는 것이 일반적이지만 별도의 영역이나 리포지토리에 있을 수도 있습니다. 따라서 가져와야 하는 다른 영역이 있는지 고려하세요. 또한 해당되는 경우 Terraform Cloud와 통합하여 `terraform run`프로세스의 일부로 Snyk 테스트를 활성화할 수도 있습니다.

복잡한 환경, 모듈, 고도로 템플릿화된 구현의 경우, 테라폼 플랜 파일에 CLI를 사용하면 최상의 결과를 얻을 수 있습니다.

### CR (Container Registries) 통합

또한 Snyk은 다양한 [Container Registries](../../../integrate-with-snyk/snyk-container-integrations/)와 통합되어 컨테이너를 가져와서 취약점이 있는지 모니터링할 수 있습니다. Snyk은 사용자가 제어하는 주기로 가져온 컨테이너에서 발견된 알려진 보안 취약점이 있는지 테스트합니다.

### Kubernetes

Kubernetes에 배포된 워크로드를 모니터링하도록 Snyk을 구성할 수 있습니다. 컨트롤러를 구성하는 방법에 대한 자세한 내용 [Kubernetes 통합 개요](../../../scan-with-snyk/snyk-container/integrate-with-kubernetes/overview-of-the-kubernetes-integration/)를 참조하세요.
