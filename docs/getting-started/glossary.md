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

명령줄 인터페이스. [Snyk CLI](glossary.md#snyk-cli)를 참조하세요

### Cloud Native Application Security

CI/CD 파이프라인 전반에 걸쳐 보안을 구현하고, 마이크로서비스에 보안 내장을 자동화하고, 반복을 최대화하여 취약점 발생을 줄입니다. Snyk는 포괄적인 [CNAS platform](https://snyk.io/product/cloud-native-application-security/)을 제공합니다.\
[Cloud-native security guide for building secure applications](https://snyk.io/learn/cloud-native-security-for-cloud-native-applications/) 문서를 참조하세요.

### Container

컨테이너를 사용하면 애플리케이션과 해당 디펜던시를 함께 패키징하여 실행 가능한 단일 단위로 배포할 수 있습니다. 컨테이너는 운영체제 커널이 제공하는 추상화이며, 시스템에서 실행 중인 다른 프로세스로부터 프로세스를 분리할 수 있습니다. 자세한 내용은 [Snyk Container](glossary.md#snyk-container)를 참조하십시오.

### Container engine

사용자의 경우, 컨테이너 이미지를 가져와 실행 중인 컨테이너로 바꾸는 애플리케이션입니다. 컨테이너 엔진은 일반적으로 컨테이너 레지스트리와 연결되며 컨테이너를 실행합니다. 컨테이너 엔진의 예로는 Docker, CRI-O 또는 LXC가 있습니다

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

취약점을 어떻게 활용할 수 있는지 보여줍니다. exploit이 널리 공개되면 일반적으로 ‘exploit in the wild’라고 합니다. [View exploits](../scan-with-snyk/find-and-manage-priority-issues/view-exploits.md)를 참조하세요.

### Exploit Maturity

취약점에 대한 공격이 얼마나 실현 가능한지, 취약점이 널리 게시되었는지, 공격자에게 얼마나 유용한지 측정합니다.&#x20;

## F

### Fixable / Partially fixable

A measure of whether a vulnerability can be fixed by Sny by applying a patch, upgrade, or pin. See [Vulnerability fix types](../scan-with-snyk/snyk-open-source/manage-vulnerabilities/vulnerability-fix-types.md).

### Fix PR

A pull request with an automatic fix for discovered vulnerabilities that Snyk can offer the user. See [Automated fix PRs](../scan-with-snyk/snyk-open-source/automatic-and-manual-prs-with-snyk-open-source/automated-fix-pull-requests-for-backlog-issues-and-known-vulnerabilities.md).

## G

### Git

A distributed version control system for tracking changes in source code during software development.

## I

### IaC

Infrastructure as Code. See [Snyk Infrastructure as Code.](glossary.md#snyk-infrastructure-as-code)

### IAST

Interactive Application Security Testing. This approach tests for vulnerabilities while running the application. See [DAST](glossary.md#dast) and [SAST](glossary.md#sast).

### IDE

Integrated Development Environment. An application that has facilities for software development, typically with a source code editor, build automation tools, and a debugger.

### Image

The stored instance of a container that holds a set of software needed to run an application.

### Image layer

Container images typically consist of several different file system layers, which are combined together at runtime into a single file system.

### Integrations

Third-party products, applications, and platforms that Snyk works with, for example, SCM systems such as GitHub. See [Integrate with Snyk](../integrate-with-snyk/).

### Issue

A license problem, vulnerability, or misconfiguration identified and listed by Snyk. See [Find and manage priority issues](../scan-with-snyk/find-and-manage-priority-issues/).

## L

### Library

A specific type of package.

### License policy

A set of criteria for evaluating open-source license issues. License policies enable you to set the severity level and define legal instructions for each license. See [License policies](../scan-with-snyk/policies/license-policies/).

## M

### Manifest

A file containing metadata about other files in a package.

### Monitor

The `snyk monitor` command tests a Project and uploads the results to Snyk. See the CLI help for [Monitor](../snyk-cli/commands/monitor.md).

## O

### OCI

Open Container Initiative. An independent body set up to facilitate collaboration on standards for containers, to ensure they are interoperable between vendor solutions.

### Organization

An Organization in Snyk is a way to collect and organize your Projects. Members of Organizations have access to these Projects. See [Manage Groups and Organizations](../snyk-admin/manage-groups-and-organizations/).

### Origin or source

The identifier for the ecosystem that a Target exists in. Snyk can scan Projects from multiple integrations, including CLI, API, GitHub, Kubernetes, and others. See [Snyk Projects](../snyk-admin/snyk-projects/).

## P

### Package

A group of files and additional metadata about those files, used by package managers.

### Package manager

A set of tools that automate and manage packages of bundled files, and are usually specific to a language. For example, npm.

### Package registry

A software package hosting service that allows customers to host packages and code in one place.

### Pinnable

A fix type: define and "pin" a specific version of an indirect dependency, to avoid a direct dependency pulling in a vulnerable version.

### Policy

See [license policy](glossary.md#license-policy), [security policy](glossary.md#security-policy), and [`.snyk` policy](glossary.md#.snyk-policy).

### **Policy (Snyk AppRisk)**

A way to automate actions in certain conditions, like classifying and tagging assets with business context. You can also use a policy to configure actions like sending a message or setting the coverage gap control using a Policy builder UI.

### PR

Pull Request. Allows a user to exchange changes made to source code and collaborate with others on the same branch.

### PR Checks

Use Snyk PR Checks to prevent new security issues from entering your codebase by automatically scanning code changes in real time as soon as you submit a pull request (PR) in your source code manager (SCM). See [Run PR Checks](../scan-with-snyk/run-pr-checks/).

### Priority Score

Snyk scores issues, including vulnerabilities and licenses for Open Source, to help prioritize the treatment of each one. Scores are based on multiple factors including the CVSS score and range from 0 (low) to 1000 (high). See [Priority Score](../scan-with-snyk/find-and-manage-priority-issues/priority-score.md).

### Project

An external item scanned by Snyk with configuration to define how to run that scan. Projects appear on the **Projects** menu on the Snyk dashboard. See also [Target](glossary.md#target). For details, see [Snyk Projects](../snyk-admin/snyk-projects/).

## R

### Reachability

Whether an application contains code that will hit a vulnerable code path during execution. See [Reachable vulnerabilities](../scan-with-snyk/find-and-manage-priority-issues/reachable-vulnerabilities.md).

### Registry

See [Container registry](glossary.md#container-registry) or [Package registry](glossary.md#package-registry).

### Repository

A storage area that contains all elements necessary for the distribution of an application.

### Resource

A cloud infrastructure entity such as an AWS S3 bucket, Identity and Access Management (IAM) role, or Virtual Private Cloud (VPC) flow log.

### Risk score

A value assigned to an issue, ranging from 0 to 1,000, representing the risk imposed on your environment.

### Rule

A security policy that checks cloud infrastructure and infrastructure as code (IaC) for misconfigurations that can lead to security problems.

## S

### SARIF

Static Analysis Results Interchange Format. A standard, JSON-based format for the output of static analysis tools.

### SAST

Static Application Security Testing. A method to secure software by reviewing the source code of your proprietary software and identifying sources of vulnerabilities. Also see [DAST](glossary.md#dast).

### SBOM

Software Bill Of Materials. A list of components in a piece of software.

### SCA

Software Composition Analysis. A technology that is used to identify open-source and third-party components in use in an application, including their known security vulnerabilities, and typically adversarial license restrictions. See also [Static Code Analysis](glossary.md#static-code-analysis).

### SCM

Source Code Management. Also known as a code repository (repo) or version control system. The method used by developers to store their source code and track changes to code. SCM helps resolve conflicts when merging updates from multiple contributors. GitHub is an example of a common SCM system. See [Git repositories (SCMs)](../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/).

### SDLC

Software Development Lifecycle. A process followed by a development team, describing how to develop and maintain software.

### Security policy

A set of criteria for evaluating open-source vulnerabilities. Security policies enable you to set custom rules to automatically prioritize or de-prioritize specific vulnerabilities. See [Security policies](../scan-with-snyk/policies/security-policies/).

### Severity

A severity level is applied to a vulnerability or a license issue, to indicate the risk for that item in an application. See [Severity levels](../scan-with-snyk/find-and-manage-priority-issues/severity-levels.md).

### Snapshot

An individual report within the test history of a Project. Includes a tree of dependencies and a list of vulnerabilities that was accurate at the time the test was conducted.

### `.snyk` policy

A policy file that Snyk uses to define certain analysis behaviors and to specify patches for the CLI and CI/CD plugins. See [The .snyk file](../scan-with-snyk/policies/the-.snyk-file.md).

### Snyk

A platform providing Cloud Native Application Security (CNAS) solutions, allowing developers to own and build security for the whole application, from code and open source to containers and cloud infrastructure. Snyk is also the company providing the Snyk platform. See [Introducing Snyk](broken-reference/).

### Snyk Advisor

A free web application that allows you to compare software packages across open-source ecosystems. It provides insights into the overall health of a particular package by combining community and security data into a single unified view. See [Snyk Advisor](https://snyk.io/advisor/).

### Snyk API

A Snyk tool that enables developers to integrate programmatically with Snyk. See [Snyk API](../snyk-api/).

### Snyk Apps

Snyk Apps are the modern and preferred way to build integrations with Snyk, exposing fine-grained scopes for accessing resources over the Snyk APIs, powered by OAuth 2.0 for a developer-friendly experience. See [Snyk Apps](../snyk-api-info/snyk-apps/).

### Snyk Broker

A client/server system that serves as an agent or proxy, allowing Snyk to scan private customer environments: Jira, code repositories, or container registries. Snyk Broker relays messages and allows users to filter which messages are allowed through, for example, allowing users to expose only some GitHub APIs to Snyk. See [Snyk Broker](../enterprise-configuration/snyk-broker/).

### Snyk CLI

A Snyk platform tool that enables developers to find and fix known vulnerabilities in dependencies, using a command line interface. See [Snyk CLI](../snyk-cli/).

### Snyk Code

A Snyk product. A SAST product enabling developers to find and fix vulnerabilities in your proprietary application code. See [Snyk Code](../scan-with-snyk/snyk-code/).

### Snyk Container

A Snyk product. Enables developers to find and fix vulnerabilities in container images and Kubernetes applications. See [Snyk Container](../scan-with-snyk/snyk-container/).

### Snyk Infrastructure as Code

A Snyk product. Enables developers to find and fix vulnerabilities in Kubernetes, Helm, and Terraform configuration files. See [Snyk Infrastructure as Code](../scan-with-snyk/scan-infrastructure/scan-your-iac-source-code/).

### Snyk Open Source

A Snyk product. Enables developers to find and fix open-source vulnerabilities. See [Snyk Open Source](../scan-with-snyk/snyk-open-source/).

### Snyk plugin

A library used by the Snyk CLI to scan a certain language or build system.

### Snyk Security Intelligence

A component powering the Snk cloud-native application security platform.\
Incorporates the Snyk Intel Vulnerability DB: the Snyk database of vulnerabilities, providing detailed information and fix advice for known vulnerabilities. See [Vulnerability DB](https://snyk.io/vuln).

### Snyk Web UI

The browser-based environment providing users access to Snyk functions. See [Explore the Snyk Web UI](explore-snyk-through-the-web-ui.md).

### Social Trends

Snyk shows a Trending banner on issues that are being actively discussed on Twitter. See [Vulnerabilities with Social Trends](../scan-with-snyk/find-and-manage-priority-issues/vulnerabilities-with-social-trends.md).

### Source

See [Origin](glossary.md#origin-or-source).

### SPDX

Software Package Data Exchange. A file format used to document information on the software licenses under which a piece of computer software is distributed. See [SPDX](https://spdx.dev/).

### Static Code Analysis

A method of debugging by examining source code before a program is run. See also [SCA, Software Composition Analysis](glossary.md#sca).

## T

### Target

Representation of an external resource Snyk has scanned. All [Snyk Projects](glossary.md#project) are associated with a parent Target. One Target may relate to many Projects. The structure of the Target depends on the [origin](glossary.md#origin-or-source).

### **Tags (Snyk AppRisk)**

A way to categorize assets. Helps you recognize or handle assets differently according to mutual properties. Assets can be filtered by their tags in the inventory or when creating policy rules. A tag can be automatically assigned to an asset, or the asset can be tagged by a policy you created. GitHub and GitLab topics are treated as asset tags and you can use them for creating policies.

## U

### Upgradable / Patchable

A fix type: a problem can be fixed by upgrading a version of a package or by applying a patch.

## V

### Vulnerability

A security vulnerability identified by Snyk. See [Manage vulnerabilities](../scan-with-snyk/snyk-open-source/manage-vulnerabilities/).

## W

### Webhook

A way for an app to provide other applications with real-time information. Snyk uses webhooks to check changes in code. See [Snyk Webhooks](../snyk-api-info/snyk-webhooks/).
