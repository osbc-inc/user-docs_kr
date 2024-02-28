# Glossary

## A

### Advisor

[Snyk Advisor](https://snyk.io/advisor/)를 참조하세요.

### **Asset (Snyk AppRisk)**

Snyk AppRisk 자산은 애플리케이션의 일부이며 보안 및 개발자와 관련된 식별 가능한 엔터티입니다.

## B

### Base image

컨테이너 이미지를 구성하는 데 사용되는 상위 이미지이며, 일반적으로 Dockerfile의 `FROM`지시문에 정의됩니다.  base image는 다른 base image에서 구성할 수 있습니다.

### Broker

[Snyk Broker](../enterprise-configuration/snyk-broker/)를 참조하십시오.

### Build System

소스 코드를 가져와 배포 가능한 애플리케이션(예: 컨테이너)을 빌드하는 시스템입니다.

## C

### CI/CD

지속적 통합(CI), 지속적 배포(CD) 및 지속적 배포(CD)가 함께 소프트웨어 개발 수명 주기(SDLC) 모델을 구성하여 개발자가 작고 빈번한 변경 사항의 개발 및 전달을 자동화하도록 안내합니다. 이를 통해 모든 팀 구성원이 최신 코드베이스에 액세스할 수 있고 개발 중에 커밋된 코드의 호환성을 보장할 수 있습니다. Snyk CI/CD 통합에 대한 자세한 내용은 [Snyk CI/CD](../integrate-with-snyk/snyk-ci-cd-integrations/)를 참조하세요. &#x20;

### **Class (Snyk AppRisk)**

자산에 비즈니스 컨텍스트를 할당하고 비즈니스 중요도를 기준으로 자산을 분류하는 방법입니다. 자산에 클래스 A, B, C 또는 D를 할당할 수 있습니다. 여기서 클래스 A(비즈니스 크리티컬, 중요한 데이터 처리, 규정 준수 대상 자산 등)가 가장 중요하고 클래스 D(테스트 앱, 샌드박스 환경 등)가 가장 중요하지 않습니다. 자산에는 기본적으로 클래스 C가 할당됩니다. 클래스는 정책에서 정의된 것뿐만 아니라 정책에서도 사용할 수 있습니다.

### CLI

Command Line Interface의 약자로, [Snyk CLI](glossary.md#snyk-cli)를 참조하세요

### Cloud Native Application Security

CI/CD 파이프라인 전반에 걸쳐 보안을 구현하고, 마이크로서비스에 보안 내장을 자동화하고, 반복을 최대화하여 취약점 발생을 줄입니다. Snyk는 포괄적인 [CNAS platform](https://snyk.io/product/cloud-native-application-security/)을 제공합니다.\
[Cloud-native security guide for building secure applications](https://snyk.io/learn/cloud-native-security-for-cloud-native-applications/) 문서를 참조하세요.

### Container

컨테이너를 사용하면 애플리케이션과 해당 디펜던시를 함께 패키징하여 실행 가능한 단일 단위로 배포할 수 있습니다. 컨테이너는 운영체제 커널이 제공하는 추상화이며, 시스템에서 실행 중인 다른 프로세스로부터 프로세스를 분리할 수 있습니다. 자세한 내용은 [Snyk Container](glossary.md#snyk-container)를 참조하십시오.

### Container engine

사용자의 경우, 컨테이너 이미지를 가져와 실행 중인 컨테이너로 바꾸는 애플리케이션입니다. 컨테이너 엔진은 일반적으로 컨테이너 레지스트리와 연결되며 컨테이너를 실행합니다. 컨테이너 엔진의 예로는 Docker, CRI-O 또는 LXC가 있습니다.

### Container image

컨테이너 엔진 또는 런타임에 의해 인스턴스화된 경우 실행 중인 컨테이너를 제공하는 하나 이상의 파일입니다. 이미지는 컨테이너의 패키징 및 배포 형식입니다.

### Container registry

컨테이너 이미지를 저장하고 검색하는 메커니즘을 제공하는 서버입니다.

### **Controls (Snyk AppRisk)**

자산과 관련된 보안 통제입니다. Snyk AppRisk Controls 섹션으로 이동하여 보안 제어에 사용 가능한 모든 상태를 확인하세요.

### **Coverage (Snyk AppRisk)**

애플리케이션 보안 프로그램과 관련하여 해당 자산을 보안 도구(예: Snyk Open Source)로 검사하고 테스트하는지 여부에 대한 평가입니다. 어떤 통제를 적용해야 하는지, 선택적으로 실행 빈도를 지정할 수 있는 정책 유형입니다.

### CVE

Common Vulnerabilities and Exposures의 약자로, 잘 알려진 취약점에 대해 널리 사용되는 식별자입니다.

### CVSS

Common Vulnerability Scoring System의 약자로, 0점(가장 낮음)에서 10점(가장 높음) 사이의 점수를 사용하여 취약성의 심각도를 평가하는 업계 표준입니다. Snyk는 CVSS를 사용합니다.

### CWE

Common Weakness Enumeration의 약자로, 소프트웨어 및 하드웨어의 약점을 다양한 유형으로 분류하는 용어집입니다. (예: CWE-20: 입력 검증)

## D

### DAST

동적 애플리케이션 보안 테스트(Dynamic Application Security Testing)를 말합니다. 사이트 또는 서비스를 가리킬 수 있는 애플리케이션입니다. 그런 다음 일반적으로 사이트 또는 서비스를 성능 분석한 다음 출력 및 동작을 검사하여 보안 취약점을 파악합니다. [SAST](glossary.md#sast)를 참조하십시오.&#x20;

### Dependency

애플리케이션이 다른 패키지를 사용하는 경우, 이 다른 패키지는 자체 소프트웨어에 종속됩니다.

* 직접 의존성은 사용자가 자신의 프로젝트에 포함하는 패키지입니다.
* 간접 의존성(deep, chained 또는 transitive dependency라고도 함)은 직접 의존성 중 하나에 사용되는 패키지입니다.

### Dependency tree

종속성 경로라고도 하며, 소프트웨어 애플리케이션의 종속성을 보여주는 계층적 그래프입니다. 그래프에는 직접 및 간접 종속성이 모두 포함되며, 많은 수준의 디펜던시가 포함될 수 있습니다.

### DevOps

시스템 개발 수명 주기를 단축하기 위해 소프트웨어 개발과 IT 운영을 결합하는 일련의 문학적 철학, 관행 및 도구입니다.

### DevSecOps

새로운 민첩한 IT 및 DevOps 개발에 최대한 원활하고 투명하게 보안을 통합합니다.

### Dockerfile

Docker를 사용하여 컨테이너 이미지를 빌드하는 데 사용되는 텍스트 파일 형식입니다. Dockerfile에는 상위 기본 이미지 지정을 포함하여 최종 이미지를 구성하는 데 필요한 모든 명령이 포함되어 있습니다.

## E

### Environment

클라우드 환경,[Project attribute](../snyk-admin/snyk-projects/project-attributes.md) 또는 Snyk [CLI](glossary.md#cli), [Web UI](glossary.md#snyk-web-ui), [IDE](glossary.md#ide) 등 Snyk 작업을 위한 인터페이스를 참조할 수 있습니다.

### Exploit

취약점을 어떻게 활용할 수 있는지 보여줍니다. exploit이 널리 공개되면 일반적으로 ‘exploit in the wild’라고 합니다. [View exploits](../scan-with-snyk/find-and-manage-priority-issues/view-exploits.md)를 참조하십시오.&#x20;

### Exploit Maturity

취약점에 대한 공격이 얼마나 실현 가능한지, 취약점이 널리 게시되었는지, 공격자에게 얼마나 유용한지 측정합니다.&#x20;

## F

### Fixable / Partially fixable

패치, 업그레이드 또는 핀을 적용하여 Snyk에서 취약점을 수정 여부를 확인합니다. [Vulnerability fix types](../scan-with-snyk/snyk-open-source/manage-vulnerabilities/vulnerability-fix-types.md)을 참조하십시오.&#x20;

### Fix PR

Snyk은 사용자에게 취약점에 대한 자동 수정이 포함된 pull request를 제공할 수 있습니다. [Automated fix PRs](../scan-with-snyk/snyk-open-source/automatic-and-manual-prs-with-snyk-open-source/automated-fix-pull-requests-for-backlog-issues-and-known-vulnerabilities.md)을 참조하십시오.&#x20;

## G

### Git

소프트웨어 개발 중 소스 코드의 변경 사항을 추적하기 위한 분산 버전 관리 시스템입니다.

## I

### IaC

Infrastructure as Code의 약자로, [Snyk Infrastructure as Code](glossary.md#snyk-infrastructure-as-code) 참조하십시오.&#x20;

### IAST

Interactive Application Security Testing의 약자로, 이 접근 방식은 애플리케이션을 실행하는 동안 취약점을 테스트합니다. [DAST](glossary.md#dast) 및 [SAST](glossary.md#sast)를 참조하십시오.&#x20;

### IDE

Integrated Development Environment의  약자로, 일반적으로 소스 코드 편집기, 빌드 자동화 도구 및 디버거를 포함하여 소프트웨어 개발을 위한 기능을 갖춘 애플리케이션입니다.

### Image

애플리케이션을 실행하는 데 필요한 소프트웨어 집합을 포함하는 컨테이너의 저장된 인스턴스입니다.

### Image layer

컨테이너 이미지는 일반적으로 여러 개의 서로 다른 파일 시스템 계층으로 구성되어 있으며, 런타임에 단일 파일 시스템으로 결합합니다.

### Integrations

Snyk가 작동하는 타사 제품, 애플리케이션 및 플랫폼(예: GitHub와 같은 SCM 시스템). [Snyk 연동](../integrate-with-snyk/)을 참조하십시오.

### Issue

Snyk가 식별하고 나열한 라이선스 문제, 취약성 또는 구성 오류입니다. [Find and manage priority issues](../scan-with-snyk/find-and-manage-priority-issues/)를 참조하십시오.

## L

### Library

특정 유형의 패키지입니다.

### License policy

오픈 소스 라이선스 문제를 평가하기 위한 일련의 기준입니다. 라이센스 정책을 사용하면 심각도 수준을 설정하고 각 라이센스에 대한 법적 지침을 정의할 수 있습니다. [License policies](../scan-with-snyk/policies/license-policies/)를 참조하십시오.

## M

### Manifest

패키지의 다른파일들에 대한 메타데이터를 포함하는 파일입니다.

### Monitor

`snyk monitor`명령은 프로젝트를 테스트하고 결과를 Snyk에 업로드합니다. [Monitor](../snyk-cli/commands/monitor.md)에 대한 CLI 도움말을 참조하세요.

## O

### OCI

Open Container Initiative의 약자로, 컨테이너 표준에 대한 협업을 용이하게 하고 공급 업체 솔루션 간에 상호 운용성을 보장하기 위해 설립된 독립적인 기구입니다.

### Organization

Snyk의 조직은 프로젝트를 수집하고 구성하는 방법입니다. 그런 다음 구성원이 특정 프로젝트에 액세스할 수 있습니다. [Manage Groups and Organizations](../snyk-admin/manage-groups-and-organizations/)를 참조하십시오.

### Origin or source

Target이 존재하는 생태계의 식별자입니다. Snyk는 CLI, API, GitHub, Kubernetes 등을 포함한 여러 통합에서 프로젝트를 스캔할 수 있습니다. [Snyk Projects](../snyk-admin/snyk-projects/)를 참조하십시오.

## P

### Package

패키지 관리자가 사용하는 파일 그룹 및 해당 파일에 대한 추가 메타데이터입니다.

### Package manager

패키지를 자동화하고 관리하는 도구 집합으로, 일반적으로 언어에 따라 다른 Package manager를 사용합니다. (예: npm)

### Package registry

고객이 패키지와 코드를 한 곳에서 호스팅할 수 있는 소프트웨어 패키지 호스팅 서비스입니다.

### Pinnable

수정 유형 중 하나이며, 취약한 버전을 가져오는 직접 의존성을 피하기 위해 간접 의존성의 특정 버전을 정의하고 “pin”합니다.

### Policy

[license policy](glossary.md#license-policy), [security policy](glossary.md#security-policy), [`.snyk` policy](glossary.md#.snyk-policy)를 참조하십시오.

### **Policy (Snyk AppRisk)**

비즈니스 상황에 따라 자산을 분류하고 태그를 지정하는 등 특정 조건에서 작업을 자동화하는 방법입니다. 정책 빌드 UI를 사용하여 메시지를 보내거나 커버리지 갭 컨트롤을 설정하는 등의 작업을 구성할 수도 있습니다.

### PR

Pull Request의 약자로, 사용자가 소스 코드의 변경 사항을 교환하고 동일한 branch의 다른 사용자와 협업할 수 있습니다.

### PR Checks

Snyk PR Checks를 사용하면 소스 코드 관리자(SCM)에서 pull request(PR)을 하자마자 실시간으로 코드 변경 사항을 자동으로 스캔하여 새로운 보안 문제가 코드베이스에 유입되는 것을 방지할 수 있습니다. [Run PR Checks](../scan-with-snyk/run-pr-checks/)를 참조하십시오.

### Priority Score

Snyk는 Issue(취약점 및 라이선스)를 점수화하여 각각의 Issue 해결의 우선순위를 정하는 데 도움이 됩니다. 점수는 CVSS 점수를 포함한 여러 요소를 기반으로 하며 0(낮음)에서 1000(높음) 사이의 범위를 가집니다. [Priority Score](../scan-with-snyk/find-and-manage-priority-issues/priority-score.md)를 참조하십시오.

### Project

Snyk이 스캔하는 외부 항목으로, 해당 스캔을 실행하는 방법을 정의하는 구성입니다. Snyk 대시보드의 프로젝트 메뉴에 나타납니다. 자세한 내용은 [Target](glossary.md#target), [Snyk Projects](../snyk-admin/snyk-projects/)를 참조하십시오.

## R

### Reachability

실행 중 공격 가능한 취약한 경로의 코드가 애플리케이션에 포함되어 있는지 여부입니다. [Reachable vulnerabilities](../scan-with-snyk/find-and-manage-priority-issues/reachable-vulnerabilities.md)를 참조하십시오.

### Registry

[Container registry](glossary.md#container-registry), [Package registry](glossary.md#package-registry)를 참조하십시오.

### Repository

애플리케이션 배포에 필요한 모든 요소를 포함하는 저장소 영역을 말합니다.

### Resource

AWS S3 버킷, Identity and Access Management(IAM) 역할 또는 Virtual Private Cloud(VPC) 흐름 로그와 같은 클라우드 인프라 엔터티입니다.

### Risk score

환경에 부과되는 위험을 나타내는 문제에 할당된 값(범위: 0\~1,000) 입니다.

### Rule

보안 문제로 이어질 수 있는 잘못된 구성이 있는지 클라우드 인프라 및 IaC(Infrastructure as Code)를 확인하는 보안 정책입니다.

## S

### SARIF

Static Analysis Results Interchange Format의 약자로, 정적 분석 도구의 출력을 위한 표준 JSON 기반 형식입니다.

### SAST

Static Application Security Testing의 약자로, 독점 소프트웨어의 소스 코드를 검토하고 취약점의 원인을 식별하여 소프트웨어를 보호하는 방법입니다. [DAST](glossary.md#dast)를 참조하십시오.

### SBOM

Software Bill Of Materials의 약자로,  소프트웨어의 구성 요소 목록입니다.

### SCA

Software Composition Analysis의 약자로, 알려진 보안 취약성과 일반적으로 적대적인 라이선스 제한을 포함하여 애플리케이션에서 사용 중인 오픈 소스 및 타사 구성 요소를 식별하는 데 사용되는 기술입니다. [Static Code Analysis](glossary.md#static-code-analysis)를 참조하십시오.

### SCM

Source Code Management의 약자로, code repo / repository / version control system이라고도 합니다. 개발자가 소스 코드를 저장하고 코드의 변경 사항을 추적하기 위해 사용하는 방법입니다. SCM은 여러 기여자의 업데이트를 병합할 때 발생하는 충돌을 해결하는 데 도움이 됩니다. [Git repositories (SCMs)](../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/)를 참조하십시오.

### SDLC

Software Development Life Cycle의 약자로, 소프트웨어 개발 수명 주기를 말합니다. 개발 팀이 뒤따르는 프로세스로, 소프트웨어 개발 및 유지 관리 방법을 설명합니다.

### Security policy

오픈 소스 취약점을 평가하기 위한 일련의 기준입니다. 보안 정책을 사용하면 특정 취약점의 우선 순위를 자동으로 지정하거나 우선 순위를 낮추는 사용자 지정 규칙을 설정할 수 있습니다. [Security policies](../scan-with-snyk/policies/security-policies/)를 참조하십시오.

### Severity

심각도 수준은 취약점 또는 라이선스 문제에 적용되어 애플리케이션에서 해당 항목의 위험을 나타냅니다. [Severity levels](../scan-with-snyk/find-and-manage-priority-issues/severity-levels.md)를 참조하십시오.

### Snapshot

프로젝트 테스트 기록 내의 개별 보고서입니다. 테스트가 수행된 당시 정확했던 디펜던시 트리와 취약점 목록이 포함됩니다.

### `.snyk` policy

Snyk가 특정 분석 동작을 정의하고, CLI 및 CI/CD 플러그인에 대한 패치를 지정하는 데 사용하는 정책 파일입니다. [The .snyk file](../scan-with-snyk/policies/the-.snyk-file.md)를 참조하십시오.

### Snyk

CNAS(Cloud Native Application Security) 솔루션을 제공하는 플랫폼으로 개발자는 코드 및 오픈소스에서 컨테이너 및 클라우드 인프라에 이르기까지 전체 애플리케이션에 대한 보안을 유지하고 구축할 수 있습니다. Synk은 또한 Snyk 플랫폼을 제공하는 회사입니다. [Introducing Snyk](broken-reference/)를 참조하십시오.

### Snyk Advisor

오픈 소스 생태계 전반에서 소프트웨어 패키지를 비교할 수 있는 무료 웹 애플리케이션입니다. 커뮤니티 및 보안 데이터를 단일 통합 뷰에 결합하여 특정 패키지의 전반적인 상태에 대한 통찰력을 갖게 합니다. [Snyk Advisor](https://snyk.io/advisor/)를 참조하십시오.

### Snyk API

개발자가 Snyk와 프로그래밍 방식으로 통합할 수 있게 해주는 Snyk 도구입니다. [Snyk API](../snyk-api/)를 참조하십시오.

### Snyk Apps

Snyk 앱은 Snyk와의 통합을 구축하는 현대적이고 선호되는 방법입니다. 개발자 친화적인 환경을 위해 OAuth 2.0으로 구동되는 Snyk API를 통해 리소스에 액세스하기 위한 세분화된 범위를 노출합니다. [Snyk Apps](../snyk-api-info/snyk-apps/)를 참조하십시오.

### Snyk Broker

Agent/Proxy 역할을 하는 클라이언트/서버 시스템으로, Snyk이 개인 고객 환경(Jira, 소스코드 저장소 또는 컨테이너 레지스트리)을 스캔할 수 있습니다. 메시지를 중계하고 사용자가 허용되는 메시지를 필터링할 수 있도록 합니다. 예를 들어, 사용자는 Snyk에 일부 GitHub API만 노출할 수 있습니다. [Snyk Broker](../enterprise-configuration/snyk-broker/)를 참조하십시오.

### Snyk CLI

Snyk 플랫폼 도구입니다. Snyk CLI를 사용하면 개발자가 CLI를 사용하여 디펜던시의 알려진 취약점을 찾아 수정할 수 있습니다. [Snyk CLI](../snyk-cli/)를 참조하십시오.

### Snyk Code

Snyk 제품 중 하나입니다. 개발자가 독점 애플리케이션 코드의 취약점을 찾아 수정할 수 있는 SAST 제품입니다. [Snyk Code](../scan-with-snyk/snyk-code/)를 참조하십시오.

### Snyk Container

Snyk 제품 중 하나입니다. 개발자가 컨테이너 이미지 및 Kubernetes 애플리케이션의 취약점을 찾아 수정할 수 있습니다. [Snyk Container](../scan-with-snyk/snyk-container/)를 참조하십시오.

### Snyk Infrastructure as Code

Snyk 제품 중 하나입니다. 개발자가 Kubernetes, Helm 및 Terraform 구성 파일의 취약점을 찾아 수정할 수 있습니다. [Snyk Infrastructure as Code](../scan-with-snyk/scan-infrastructure/scan-your-iac-source-code/)를 참조하십시오.

### Snyk Open Source

Snyk 제품 중 하나입니다. 개발자가 오픈 소스 취약점을 찾아 수정할 수 있습니다. [Snyk Open Source](../scan-with-snyk/snyk-open-source/)를 참조하십시오.

### Snyk plugin

Snyk CLI에서 특정 언어를 스캔하거나 시스템을 구축하는 데 사용되는 라이브러리입니다.

### Snyk Security Intelligence

Snk 클라우드 네이티브 애플리케이션 보안 플랫폼을 지원하는 구성 요소입니다. \
**Snyk Intel Vulnerability DB** 통합: Snyk의 취약점 데이터베이스를 통합하여 자세한 정보를 제공하고 알려진 취약점에 대한 조언을 제공합니다. [Vulnerability DB](https://snyk.io/vuln)를 참조하십시오.

### Snyk Web UI

사용자에게 Snyk 기능에 대한 액세스를 제공하는 브라우저 기반 환경입니다. [Explore the Snyk Web UI](explore-snyk-through-the-web-ui.md)를 참조하십시오.

### Social Trends

Snyk는 트위터에서 활발하게 논의되고 있는 문제에 대한 인기 배너를 표시합니다. [Vulnerabilities with Social Trends](../scan-with-snyk/find-and-manage-priority-issues/vulnerabilities-with-social-trends.md)를 참조하십시오.

### Source

[Origin](glossary.md#origin-or-source)를 참조하십시오.

### SPDX

Software Package Data Exchange의 약자로, 소프트웨어가 배포되는 소프트웨어 라이센스에 대한 정보를 문서화하는 데 사용되는 파일 형식입니다. [SPDX](https://spdx.dev/)를 참조하십시오.

### Static Code Analysis

프로그램을 실행하기 전에 소스 코드를 검사하여 디버깅하는 방법입니다. [SCA, Software Composition Analysis](glossary.md#sca)를 참조하십시오.

## T

### Target

Snyk가 스캔한 외부 리소스의 표현입니다. 모든 [Snyk Projects](glossary.md#project)는상위 Target과 연결되어 있습니다. 하나의 타겟은 여러 프로젝트와 관련될 수 있습니다. Target의 구조는[origin](glossary.md#origin-or-source)에 따라 다릅니다.

### **Tags (Snyk AppRisk)**

자산을 분류하는 방법입니다. 상호 재산에 따라 자산을 다르게 인식하거나 처리할 수 있도록 도와줍니다. 자산은 인벤토리의 태그를 기준으로 필터링하거나 정책 규칙을 생성할 때 필터링할 수 있습니다. 태그는 자산에 자동으로 할당되거나 생성된 정책에 따라 자산에 태그가 지정될 수 있습니다. GitHub 및 GitLab 주제는 자산 태그로 처리되며 정책 생성에 사용할 수 있습니다.

## U

### Upgradable / Patchable

수정 유형 중 하나이며, 패키지 버전을 업그레이드하거나 패치를 적용하여 문제를 해결할 수 있습니다.

## V

### Vulnerability

Snyk가 식별한 보안 취약점입니다. [Manage vulnerabilities](../scan-with-snyk/snyk-open-source/manage-vulnerabilities/)를 참조하십시오.

## W

### Webhook

프로그램이 다른 애플리케이션에 실시간 정보를 제공하는 방법입니다. Snyk는 웹훅을 사용하여 코드 변경 사항을 확인합니다. [Snyk Webhooks](../snyk-api-info/snyk-webhooks/)를 참조하십시오.
