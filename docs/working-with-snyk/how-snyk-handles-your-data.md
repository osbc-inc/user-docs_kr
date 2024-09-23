# Snyk이 데이터를 처리하는 방법

Snyk은 데이터 보안을 가장 중요하게 생각하는 개발자 보안 플랫폼입니다. Snyk은 귀하의 개인 정보 보호 및 보안 요구 사항을 완전히 이해하고 Snyk이어떤 데이터에 액세스하고, 전송하고, 저장하는지에 대한 투명성을 귀하에게 제공한다는 목표로 이 문서를 제공합니다.

Snyk이 처리하는 데이터는 사용 중인 제품, Snyk와 통합하는 방법, Snyk 배포에 따라 다릅니다. Snyk은 빠르게 변화할 수 있으므로 Snyk이 액세스하고 저장하는 데이터 유형은 새로운 기능의 도입이나 기존 기능의 변경으로 인해 변경될 수 있습니다.

## 유연한 배포 옵션

Snyk 최신 소프트웨어 개발 사례와 기술을 활용하여 고객이 비즈니스 요구 사항에 가장 적합한 방식으로 Snyk의 개발자 보안 플랫폼을 사용할 수 있는 유연성을 제공합니다.

Snyk의 클라우드 우선 배포 옵션은 사용 편의성과 확장성을 제공하는 동시에 미국, EU 및 AUS에서 지원되는 multi- 및 single-tenancy 옵션을 통해 필요한 수준의 데이터 보호를 제공합니다.

앞으로 Snyk는 더 많은 지역을 지원할 예정입니다.

* **Multi-Tenant SaaS**: Snyk의 개발자 보안 플랫폼을 사용하는 가장 간단하고 일반적이며 비용이 효율적인 방법
* **Single-Tenant SaaS:**AWS에서 Snyk 개발자 보안 플랫폼의 격리된 완전 관리형 인스턴스입니다. 자세한 내용은 [Snyk Deployment Options](https://snyk.io/platform/deployment-options/)을 참조하세요.
* **Snyk Broker**: Snyk 개발자 보안 플랫폼(multi- 또는 single-tenant)과 온프레미스 코드베이스 간의 프록시 역할을 하는 개인 인프라에 설치된 클라이언트 서비스입니다.. [Snyk Broker](../enterprise-configuration/snyk-broker/) 는 인바운드 및 아웃바운드 연결을 안전하게 처리하고 전송 중 데이터를 암호화하며 Snyk이 귀하의 데이터에 대한 액세스를 의도적으로 제어합니다. 민감한 자격 증명은 방화벽 뒤에 있습니다.

## Snyk 전반에 걸친 고객 데이터 흐름

Snyk은 다양한 유형의 데이터를 필요로 하고 다양한 데이터 상호 작용을 수반하는 광범위한 개발 도구와 통합 지점을 제공합니다. 다음 섹션에서는 Snyk이 액세스하고 저장하는 일반적인 데이터 유형과 제품 및 통합 관련 데이터 유형에 대한 개요를 제공합니다. 이러한 정보는 1년에 최소 두 번 또는 제품 운영 내에서 중요한 변경 사항이 발생할 때 검토합니다.

## 일반적인 데이터 유형

* **취약점 데이터** - 고객의 애플리케이션에서 식별된 취약점 및 관련 수정 사항에 대한 정보를 저장합니다.
* **취약점 소스** - 취약점이 식별된 위치에 대한 정보를 저장합니다. 예: 소스 코드 리포지토리 또는 레지스트리, 파일 이름 및 위치, 디펜던시 트리, 취약점 경로.
* **연동 관련 데이터** - Snyk은 Snyk과의 연동을 설정하는 데 필요한 정보를 저장합니다.  예: 토큰 및 API 구성.
* **사용자 데이터** - Snyk은 플랫폼에 액세스하고 사용하는 데 필요한 사용자 정보를 저장합니다. 예: 사용자 이름, ID(예: GitHub 사용자 ID), 이메일 주소, IP 주소.
* **사용자 목록** - 정확한 기여자 수를 계산하기 위해 Snyk은 모니터링되는 리포지토리에 대해 지난 90일 동안의 커밋에 액세스합니다. 요청 시 사용자 이메일의 해시되지 않은 버전이 생성됩니다.
* **청구 데이터** - Snyk은 Snyk 계정에 청구하는 데 필요한 정보를 저장합니다.
* **사용자 행동 분석** - Snyk은 사용 패턴과 관련된 다양한 유형의 정보를 저장합니다. 예: 플랫폼 탐색 및 실행된 CLI 명령.

{% hint style="info" %}
모든 데이터는 SOC 2 표준에 따라 Snyk에서 처리합니다. 자세한 내용은 [Snyk certifications](how-snyk-handles-your-data.md#snyk-certifications)을 참조하세요.
{% endhint %}

### 취약점 소스 데이터와 관련된 캐시 보존 기간

Snyk은 취약성 소스 데이터를 처리하고 캐시에 저장하기 위해 AWS(Amazon Web Services) 및 GCP(Google Cloud Platform)의 클라우드 제품을 사용합니다. 이러한 데이터는 클라우드 서비스 제공업체의 스토리지 수명 주기 정책에서 제공하는 가능한 최단 기간에 따라 캐시되며, 이는 클라우드 서비스 제공업체에 따라 변경될 수 있으며 대략 다음과 같은 기간으로 설정됩니다:

* AWS 테넌트의 경우 - EU/AU/프라이빗 테넌트: [S3 정책](https://docs.aws.amazon.com/AmazonS3/latest/userguide/intro-lifecycle-rules.html)에 따라 24\~48시간
* GCP 테넌트의 경우 - 미국(기본값): [Google 클라우드 스토리지 정책](https://cloud.google.com/storage/docs/lifecycle?hl=ko)에 따라 24시간

## 제품별 데이터 유형

Snyk은 귀하의 데이터를 보호하는 것이 얼마나 중요한지 잘 알고 있습니다. 따라서 당사는 귀하에게 Snyk 서비스를 제공하고 각 Snyk 제품에 대해 설명된 대로 정확한 분석을 보장하는 데 필요한 정보에만 액세스하고 저장합니다: Snyk Open Source, Snyk Code, Snyk Container 및 Snyk IaC.

### **Snyk Open Source**

<figure><img src="../.gitbook/assets/SnykOSS.svg" alt="Snyk Open Source logo"><figcaption><p>Snyk Open Source</p></figcaption></figure>

* Snyk은 오픈 소스 의존성을 식별하기 위해 매니페스트 파일, Lock 파일 및 관련 구성 파일에 액세스합니다.
* 기본적으로 Snyk은 소스 코드에 액세스하지 않지만 `--unmanaged` 옵션을 사용하는 CLI 검사의 경우 예외적으로 소스 코드 파일에 액세스하여 파일 서명(해시)으로 변환하고 파일 서명 및 파일 이름을 저장합니다.
* Snyk은 의존성의 이름과 버전 번호에 액세스하여 저장합니다.
* Snyk은 저작권 및 저작자 표시 정보를 포함한 관련 라이선스 이름을 저장합니다.
* Snyk은 리포지토리별 정보에 액세스하고 저장합니다.
* Snyk은 Git Provider Push 및 Pull 관련 정보에 액세스하고 저장합니다. 예: 기여자 이름, 파일 이름, 타임스탬프.

**Snyk Open Source 애드온 옵션 (opt-in)**

귀하의 계정에는 이러한 기능을 활성화하는 기능을 제한할 수 있는 계약 조건이 적용됩니다. 이러한 기능을 활성화하면 귀하는 회사를 대신하여 이러한 기능을 허용하기 위한 계약 조건 변경에 동의하는 것이며, 귀하는 자신의 상황에 따라 이러한 기능을 사용할 책임이 있습니다.

* Go 모듈 전체 소스 코드 분석 기능의 경우, Snyk은 정확한 종속성 그래프를 쉽게 작성할 수 있도록 Git 리포지토리의 콘텐츠에 액세스하여 저장합니다. Snyk 분석이 완료되면 코드가 Snyk 시스템에서 삭제됩니다.
* 도달 가능한 취약점 기능의 경우, Snyk은 호출 그래프 작성을 용이하게 하기 위해 git 리포지토리의 콘텐츠에 액세스하여 저장합니다. 분석이 완료되면 Snyk 시스템에서 코드가 삭제됩니다. 호출 그래프와 함수 이름만 유지됩니다.

### **Snyk Code**

<figure><img src="../.gitbook/assets/SnykCode.svg" alt="Snyk Code logo"><figcaption><p>Snyk Code</p></figcaption></figure>

* Snyk은 일회성 분석을 위해 리포지토리 코드에 액세스하고 클라우드 제공업체의 최소 저장소 정책에 따라 [소스 코드를 캐시](how-snyk-handles-your-data.md)합니다. 이 기간이 지나면 발견된 이슈의 위치(파일 경로, 줄, 열), 이슈 ID 및 설명만 유지됩니다. 코드는 제거되며 Snyk 네트워크나 로그에 저장되지 않습니다.
* 결과는 데이터베이스에 저장되며 Snyk에서 분석 및 모니터링 목적으로 사용합니다.
* Snyk Code는 (1) 엔진 학습 목적으로 또는 (2) 가능한 수정 사항을 보여주기 위해 예제를 추출하기 위해 고객 코드를 사용하지 않습니다.
* Snyk Code 수정 제안을 위한 AI 모델은 허용 라이선스가 있는 공개 리포지토리에서 학습되며, 라이선스가 변경된 리포지토리의 모든 데이터는 즉시 제거됩니다. 데이터 수집 중에는 정적 분석, 자동화된 평가 및 부분적인 인적 라벨링이 사용됩니다.
* 스캔 결과에는 원본 소스 코드가 아닌 위치(예: 파일, 줄, 열 번호)에 대한 포인터와 식별 메타 정보가 포함되어 올바른 소스 코드 버전을 사용하여 결과가 표시됩니다.
* Snyk은 리포지토리별 정보를 저장합니다. 예: Git 리포지토리 이름 및 파일 이름.
* 서버 인프라는 인증 및 권한 부여를 사용하여 고객 간 분리를 보장합니다. Snyk Code는 소프트웨어 제어를 사용하여 고객 데이터 분리를 보장합니다. 모든 통신은 고급 산업 표준 프로토콜을 사용하여 암호화됩니다.

### **Snyk Container**

<figure><img src="../.gitbook/assets/image (201) (1).png" alt="Snyk Container logo"><figcaption><p>Snyk Container</p></figcaption></figure>

* Snyk은 패키지 버전, 실행 파일 해시 및 버전, 운영 체제, 컨테이너 이미지 메타데이터(예: rootfs 해시, 히스토리), 이미지 ID에 액세스하고 저장합니다.
* Snyk은 이름, 버전, 태그 등 상위 이미지와 관련된 정보에 액세스하여 저장합니다.
* Snyk은 도커파일에서 RUN 명령어에 액세스하고 저장합니다.
* Snyk은 도커파일에서 RUN 명령어에 액세스하고 저장합니다. 쿠버네티스 구성: Snyk은 워크로드 보안 설정(예: 'root로 실행')에 액세스합니다. 이 설정은 Snyk의 Kubernetes 통합을 사용하는 경우에만 액세스할 수 있습니다.
* 컨테이너 레지스트리 통합: Snyk은 컨테이너 이미지의 단기 복사본에 액세스한 다음 저장합니다(브로커를 사용하지 않는 경우). 이 사본은 분석 후 Snyk 네트워크에서 제거됩니다.

### **Snyk IaC**

<figure><img src="../.gitbook/assets/SnykIaC.svg" alt="Snyk IaC logo"><figcaption><p>Snyk Infrastructure as Code</p></figcaption></figure>

#### Current IaC

* CLI 테스트는 로컬에서 수행됩니다. `--report` 옵션을 사용하여 결과를 Snyk 플랫폼과 공유하면 리소스 구성이 포함됩니다.
* SCM 테스트는 코드 파일로 인프라에 액세스해야 합니다. Snyk은 분석 기간 동안 이러한 파일을 저장하고 이후 Snyk 시스템에서 삭제합니다. Snyk에서는 이슈 및 리소스에 대한 컨텍스트를 제공하기 위해 구문 분석된 리소스 구성을 유지합니다.
* Terraform Cloud 및 Terraform Enterprise 테스트는 Plan 파일을 분석합니다. Snyk은 시크릿과 민감한 값을 제거하고 리소스 구성을 유지하여 이슈와 리소스에 대한 컨텍스트를 제공합니다.
* `snyk iac describe`를 사용한 드리프트 탐지의 경우, Snyk는 최소 권한 원칙을 따르며 [AWS](../scan-with-snyk/scan-infrastructure/iac+-code-to-cloud-capabilities/detect-drift-and-manually-created-resources/configure-cloud-providers/configure-aws-provider.md#least-privileged-policy), [Azure](../scan-with-snyk/scan-infrastructure/iac+-code-to-cloud-capabilities/detect-drift-and-manually-created-resources/configure-cloud-providers/configure-azure-provider.md#least-privileged-policy), [Google](../scan-with-snyk/scan-infrastructure/iac+-code-to-cloud-capabilities/detect-drift-and-manually-created-resources/configure-cloud-providers/configure-google-provider.md#least-privileged-policy) 또는 [GitHub](../scan-with-snyk/scan-infrastructure/iac+-code-to-cloud-capabilities/detect-drift-and-manually-created-resources/configure-cloud-providers/configure-github-provider.md#least-privileged-policy)에 대한 읽기 전용 액세스만 필요합니다. 공급자 자격 증명은 Snyk에 전송되거나 저장되지 않습니다.
* Snyk은 로컬 읽기 전용 테라폼 상태 파일 액세스에 의존하며 관련 리소스 구성 데이터를 추출하여 플랫폼으로 전송합니다.

#### IaC+

* Snyk Cloud는 클라우드 플랫폼 API를 스캔하여 AWS 계정 및 Google Cloud 구독에 배포된 구성된 인프라에 대한 정보를 수집합니다.
* 스캔을 수행하기 위해 Snyk은 최소 권한 원칙에 따라 각 클라우드 플랫폼에서 지원하는 다양한 인증 메커니즘을 활용합니다.
  * Amazon Web Services(AWS)의 경우, 필수 AWS API에 대한 보안 액세스를 제공하려면 AWS 계정에 읽기 전용 AWS IAM 역할이 프로비저닝되어야 합니다.
  * Google Cloud의 경우, 필수 Google Cloud API에 안전하게 액세스할 수 있도록 읽기 전용 Google Cloud 서비스 계정을 프로비저닝해야 합니다.
* 스캔하는 동안 Snyk은 리소스 구성 상태를 수집 및 저장하여 분석을 수행하고, 문제를 일으키는 잘못된 구성의 세부 정보를 포함하여 해당 분석 결과를 저장합니다.
* Snyk Cloud는 이슈 및 리소스에 대한 컨텍스트를 제공하기 위해 스캔에서 발견된 리소스 구성 상태를 유지하지만 비밀 또는 민감한 값은 저장하지 않습니다.

### Snyk AppRisk

<figure><img src="../.gitbook/assets/AppRisk_Color_64px.png" alt="Snyk App Risk logo"><figcaption><p>Snyk AppRisk</p></figcaption></figure>

* Snyk AppRisk는 Snyk Group 레벨에서 데이터에 대한 가시성을 제공하므로 Snyk Group 내의 모든 Snyk 조직의 범위를 포함합니다.
* 연결된 Snyk 조직 내의 Snyk 대상 및 프로젝트에서 Snyk AppRisk는 자산 메타데이터에 접근하고 저장하여 코드 리포지토리 자산, 패키지(퍼스트 파티) 자산 및 컨테이너 이미지 자산을 생성합니다. 자산 메타데이터에는 Git 원격 URL, 리포지토리에 표시된 언어, 커밋 기록 메타데이터(기본 소스 코드가 아님)가 포함됩니다.
* Snyk AppRisk 통합 허브를 사용하여 구성된 SCM 통합에서 Snyk AppRisk는 다음 데이터에 접근하고 저장합니다:
  * 모니터링되는 리포지토리에 대한 최근 50개 커밋의 커밋 기록 메타데이터 Code Committer의 프로필 정보(예: GitHub 사용자 ID, 표시 이름 또는 이메일)를 포함합니다.
  * 특정 코드 리포지토리에 사용된 언어(예: Python, HTML)에 대한 메타데이터.
  * Asset tags로 표시되는 리포지토리 'topics'.

## Snyk integrations: Git 리포지토리 복제

{% hint style="info" %}
Git 리포지토리 복제 활성화 및 사용에 대한 자세한 내용은 [Git repository cloning for SCM integrations](../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/introduction-to-git-repository-integrations/git-repository-cloning-for-scm-integrations.md)를 참조하세요.
{% endhint %}

### 데이터 보안을 위해 Snyk이 마련한 보호 장치

* Snyk은 PR 확인, 가져오기, 테스트 등 SCM integration flow에 필요한 경우에만 복제를 수행합니다.
* 복제 서비스와 캐시 간의 통신은 TLS 1.2로 암호화합니다.
* 복제된 자산은 캐시를 채운 후 즉시 파일 시스템에서 삭제됩니다.
* 모든 데이터는 SOC 2 표준에 따라 Snyk에서 처리됩니다. 자세한 내용은 [Snyk certifications](how-snyk-handles-your-data.md#snyk-certifications)을 참조하세요.
* 데이터는 코드 보안 및 코드 품질을 개선하기 위한 목적으로만 데이터 처리 지침에 따라 분석됩니다.

### Git 복제 관련 계약 조건

이 기능을 사용 설정하면 귀하는 Git 리포지토리가 귀사와 Snyk 간의 계약에 정의된 대로 보호 대상 자산이라는 데 동의합니다.

## Snyk certifications

<figure><img src="../.gitbook/assets/Soc2.png" alt="Soc 2 Type 2 AICPA Soc"><figcaption><p>Soc 2 Type 2 AICPA Soc</p></figcaption></figure>

Snyk은 ISO 27001:2013 인증을 받았으며 ISO 27017:2015의 추가적인 엄격한 관리 기준을 준수합니다.

<figure><img src="../.gitbook/assets/Coalfire.png" alt="Coalfire ISO 27001 certified ISO"><figcaption><p>Coalfire ISO 27001 certified ISO</p></figcaption></figure>

## Snyk 정책

자세한 내용은 Snyk 웹사이트의 다음 페이지를 참조하세요:

* [Privacy](https://snyk.io/policies/privacy/)
* [Snyk Sub-processing](https://snyk.io/policies/subprocessors/)
* [Data Processing Addendum](https://snyk.io/policies/dpa/)
* [Tracking and analytics](https://snyk.io/policies/tracking-and-analytics/)
