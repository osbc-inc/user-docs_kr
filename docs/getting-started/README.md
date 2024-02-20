# 시작하기

## Snyk 이란?

Snyk은 자체 코드, 오픈소스 디펜던시, 컨테이너 이미지, laC(infrastructure as code) 구성의 보안 취약점을 스캔, 우선 순위 지정 및 수정할 수 있는 플랫폼입니다.

## Snyk 개발자 우선 접근 방식

Snyk는 개발자의 작업 흐름에 대한 가시성과 실행 가능한 통찰력을 제공합니다. 이점은 개발자가 개발 작업의 일부로 보안 업무에 참여한다는 것입니다. 따라서 하드 QA 게이트 설치와 같은 오버헤드 집약적인 작업보다는 보안 애플리케이션을 구축하는 데 중점을 둡니다.

이제 개발자는 독점 코드와 오픈 소스 코드를 조합하여 애플리케이션을 조립하고, 해당 코드를 컨테이너에서 실행한 다음, Kubernetes 및 Terraform과 같은 기술을 사용하여 코드 구성으로 인프라를 배포합니다.

강력한 보안 프로세스는 이러한 구성 요소가 구축되고 유지 관리되는 각 구성 요소를 보호합니다. Snyk는 DevOps 프로세스에 통합되어 개발자가 각자 선호하는 방법을 사용하여 작업하는 동시에 업계 모범 사례를 따르고 지원합니다. Snyk는 IDE, 워크플로우 및 자동화 파이프라인에 직접 통합되어 툴킷에 보안 전문 지식을 추가합니다.

<figure><img src="../.gitbook/assets/image (162) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt="Developer Security Platform: Products and Developer experience"><figcaption><p>Developer Security Platform: Products and Developer experience</p></figcaption></figure>

## 작업 흐름에서 Snyk 사용

* **코드 보호**:  [Snyk Open Source](../scan-with-snyk/snyk-open-source/)를 사용하여 오픈 소스 종속성의 취약성을 수정하고 [Snyk Code](../scan-with-snyk/snyk-code/)를 사용하여 소스 코드의 취약성을 수정합니다.
* **컨테이너 보호**: [Snyk Container](../scan-with-snyk/snyk-container/)를 사용하여 컨테이너 이미지 및Kubernetes  애플리케이션의 취약성을 수정합니다.
* **인프라 보호**: [Snyk Infrastructure as Code (IaC)](../scan-with-snyk/scan-infrastructure/scan-your-iac-source-code/)를 사용하여Terraform, CloudFormation, Kubernetes 및 Azure 템플릿의 잘못된 구성을 수정합니다.  [IaC+](../scan-with-snyk/scan-infrastructure/iac+-code-to-cloud-capabilities/)를 사용하여 Amazon Web Services 계정, Microsoft Azure 구독, Google Cloud Projects의 잘못된 구성을 수정합니다.

## Snyk 실행 방법 선택

다음과 같은 방법으로 Snyk를 실행할 수 있습니다.

* [**Web**](explore-snyk-through-the-web-ui.md): Snyk Web UI ([app.snyk.io](https://app.snyk.io))는 구성 설정, 발견된 문제 필터링 및 수정, 보고서 등의 기능을 갖춘 브라우저 기반 경험을 제공합니다.
* [**CLI**](../snyk-cli/): Snyk 명령줄 인터페이스를 사용하면 로컬 컴퓨터에서 취약점 스캔을 실행하고 Snyk을 파이프라인에 통합할 수 있습니다.
* [**IDEs**](../integrate-with-snyk/ide-tools/): Snyk IDE 통합을 통해 개발 환경에 Snyk을 내장할 수 있습니다.
* [**API**](../snyk-api/): Snyk API를 사용하면 프로그래밍 방식으로 Snyk과 통합하여 Snyk 보안 자동화를 특정 워크플로우에 맞게 조정할 수 있습니다.

이 비디오는 CLI를 사용하여 취약점을 검색하는 방법을 보여줍니다.

{% embed url="https://thoughtindustries-1.wistia.com/medias/b8vrvtmnbu" %}
Running Snyk from the command line.
{% endembed %}

## Snyk은 내 환경에서 어떻게 작동하나요?

지원되는 Snyk 기술 스택은 사용하는 Snyk 제품에 따라 다릅니다.

* **Snyk 오픈소스** 및 **Snyk 코드**:  [Supported languages and framework](../scan-with-snyk/supported-languages-and-frameworks/) 참조하세요.
* **Snyk Container**: [Supported operating system distributions](../scan-with-snyk/snyk-container/how-snyk-container-works/supported-operating-system-distributions.md)를 참조하세요.
* **코드형 Snyk 인프라**: [Supported IaC and cloud providers](../scan-with-snyk/scan-infrastructure/supported-iac-languages-cloud-providers-and-cloud-resources/)를 참조하세요.

## Snyk는 무엇과 통합할 수 있나요?

소프트웨어 개발 프로세스를 위한 Snyk 통합을 통해 소스 제어, IDE, CI/CD 등을 포함한 개발 및 보안 프로세스에 Snyk를 통합할 수 있습니다.

자세한 내용은 [Integrate with Snyk](../integrate-with-snyk/)을 참조하세요.

## Snyk의 가격은 얼마입니까?

Snyk에는 무료부터 엔터프라이즈까지 다양한 가격 계획이 있습니다. [Snyk Pricing Plans](../implement-snyk/enterprise-implementation-guide/trial-limitations.md)을 참조하세요.

## 내 데이터는 어떻게 되나요?

[How Snyk handles your data](../working-with-snyk/how-snyk-handles-your-data.md) 에 대한 자세한 내용은 Snyk가 데이터를 처리하는 방법을 참조하세요.
