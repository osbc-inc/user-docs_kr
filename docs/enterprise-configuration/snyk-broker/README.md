# Snyk Broker

{% hint style="info" %}
**기능 사용 가능 여부(Feature availability)**

Snyk Broker는 엔터프라이즈 요금제에서만 사용할 수 있습니다. \
자세한 내용은 [요금제 및 가격 책정](https://snyk.io/plans)을 참조하세요.
{% endhint %}

Snyk Broker는 Snyk와 특수 통합 사이의 프록시 역할을 하는 오픈 소스 도구로, [snyk.io](http://snyk.io/)가 코드에 액세스하여 코드를 스캔하고 결과를 사용자에게 반환할 수 있도록 해줍니다. Broker와의 SCM연동은 Snyk 오픈 소스, Snyk 코드, Snyk 컨테이너(Docker파일) 및 Snyk IaC를 지원합니다. \
자세한 내용은[Snyk Broker의 작동 방식](./#how-snyk-broker-works)을 참조하세요.&#x20;

## Snyk Broker 다운로드 및 설치 방법

Snyk Broker는 [GitHub](https://github.com/snyk/broker) 에서 호스팅되며 특정 통합을 위해 Docker 이미지 집합으로 게시됩니다. Snyk은 Kubernetes를 사용하는 경우 Snyk Broker를 배포하기 위한 [Helm Chart](https://github.com/snyk/snyk-broker-helm)를 제공합니다. Broker를 배포하려면 통합을 설치하고 구성해야 합니다.

Snyk Broker 문서는 [Helm](install-and-configure-snyk-broker/install-and-configure-broker-using-helm.md)과 [Docker](install-and-configure-snyk-broker/install-and-configure-broker-using-docker.md) 사용에 대한 자세한 지침을 제공합니다.  . Snyk은 Snyk Broker를 배포하는 가장 간단한 방법으로 Helm을 사용할 것을 권장합니다. Docker를 사용하여 Snyk Broker 클라이언트를 실행하거나 npm `install snyk-broker`를 실행할 수도 있습니다.

## Snyk Broker와 통합

각 유형의 통합을 설치하고 환경 변수를 사용하여 구성하는 방법은 [Docker](install-and-configure-snyk-broker/install-and-configure-broker-using-docker.md) 및 [Helm](install-and-configure-snyk-broker/install-and-configure-broker-using-helm.md)에 대해 설명한 대로 따르세요.

Broker에서 지원되는 연동 유형은 다음과 같습니다:

* YSCM(소스 코드 관리) 시스템([GitHub](install-and-configure-snyk-broker/github-install-and-configure-broker/), [GitHub Enterprise](install-and-configure-snyk-broker/github-enterprise-install-and-configure-broker/), [BitBucket Server/Data Center](install-and-configure-snyk-broker/bitbucket-server-data-center-install-and-configure-broker/), [GitLab](install-and-configure-snyk-broker/gitlab-install-and-configure-broker/), [Azure Repos](install-and-configure-snyk-broker/azure-repos-install-and-configure-broker/))
  * 인터넷에 연결할 수 없는 SCM
  * 공개적으로 액세스할 수 있는 SCM으로, 데이터 보안을 강화하기 위해 Snyk 활동을 보고 제어할 수 있습니다.
* on-premise [Jira](install-and-configure-snyk-broker/jira-install-and-configure-broker/), [JFrog Artifactory](install-and-configure-snyk-broker/artifactory-repository-install-and-configure-broker/) 또는[Nexus](install-and-configure-snyk-broker/nexus-repository-install-and-configure-broker/) 설치
* 네트워크 제한 [container registries](snyk-broker-container-registry-agent/)
* 비공개 Git 기반 리포지토리에 있는 Snyk IaC를 사용하는 [코드형 인프라(IaC) 구성 파일](snyk-broker-infrastructure-as-code-detection/)

각 통합 및 컨테이너 Registry Agent에 대해 [파생된 Docker 이미지](https://docs.snyk.io/snyk-admin/snyk-broker/install-and-configure-broker-using-docker/snyk-broker-set-up-examples/derived-docker-images-for-broker-client-integrations-and-container-registry-agent)를 사용할 수도 있다.\
\
설치에 필요한 고급 구성에 대한 자세한 내용은 [Snyk Broker Docker 설치를 위한 고급 구성](https://docs.snyk.io/snyk-admin/snyk-broker/install-and-configure-broker-using-docker/advanced-configuration-for-snyk-broker-docker-installation) 및[Helm Chart 설치를 위한 고급설정](https://docs.snyk.io/snyk-admin/snyk-broker/install-and-configure-broker-using-helm/advanced-setup-for-helm-chart-installation)을 참조하세요.

## Snyk Broker를 사용하여 코드 스캔하기

Snyk Broker와 함께 **Snyk Open Source**를 사용하려면 Broker 서버와 Broker 클라이언트 구성 요소만 있으면 됩니다. Broker 클라이언트는 각각 특정 Git 서비스에 맞게 구성된 Docker 이미지 집합으로 게시됩니다. 이전 섹션인 [Snyk Broker와의 통합](./#integrations-with-snyk-broker)에 있는 링크를 따라 환경 변수를 사용하여 각 유형의 통합을 구성하세요.

Snyk Broker로 다른 유형의 코드를 스캔하려면 구성 요소 또는 구성을 추가하고 Broker 클라이언트 설정에 매개 변수를 추가해야 합니다:

* **Snyk Code** – [Code Agent](snyk-broker-code-agent/)구성 요소를 추가하여 Snyk Broker를 통해 통합된 SCM의 리포지토리에 대한 Snyk Code 분석을 활성화합니다. 환경 변수를 추가하여 [리포지토리의 Git 복제](install-and-configure-snyk-broker/advanced-configuration-for-snyk-broker-docker-installation/snyk-code-clone-capability-with-broker-for-docker.md)를 수행할 수 있는 브로커 액세스 권한을 부여할 수도 있습니다:`ACCEPT_CODE=true.`
* **Snyk Container** – 컨테이너 레지스트리 에이전트를 추가하여 네트워크가 제한된 컨테이너 레지스트리에 연결하고 컨테이너 이미지를 분석할 수 있도록 합니다. [Docker 로 설치하는 방법](https://docs.snyk.io/snyk-admin/snyk-broker/snyk-broker-container-registry-agent#configuring-and-running-the-broker-client-for-container-registry-agent) 및[Helm으로 설치하는 방법](snyk-broker-container-registry-agent/install-broker-for-container-registry-agent-using-helm.md)에 대한 지침이 있습니다.\

* **Snyk Infrastructure as Code** –[ 추가 매개변수로 ](snyk-broker-infrastructure-as-code-detection/)[`accept.json`](snyk-broker-infrastructure-as-code-detection/)[파일을 구성하여 ](snyk-broker-infrastructure-as-code-detection/)Snyk Broker를 통해 Terraform, CloudFormation 및 Kubernetes 구성 파일을 감지하고 분석합니다.

## Snyk Broker 작동 방식

Snyk Broker는 인터넷에서 공개적으로 액세스할 수 없는 자체 호스팅 통합에 Snyk 제품을 연결하도록 설계되었습니다. 또한 Snyk Broker를 사용하면 다음을 수행할 수 있습니다:

* Snyk이 액세스할 수 있는 파일과 Snyk이 수행할 수 있는 작업을 제한하여 네트워크에 대한 Snyk의 액세스를 제어합니다.
* Broker를 대상으로 통합을 위한 고정 사설 IP를 관리합니다.

Snyk Broker includes a Server and a Client, basic components that are the same across all integrations. The Broker Server runs on the Snyk SaaS backend and is provided by Snyk; no installation is required. The Broker Client is a  deployed in your infrastructure. For more information, see  and .\
Snyk Broker에는 모든 연동 서비스에서 동일한 기본 구성 요소인 서버와 클라이언트가 포함되어 있습니다. Broker 서버는 Snyk SaaS 백엔드에서 실행되며 Snyk에서 제공하므로 설치가 필요하지 않습니다. Broker 클라이언트는 인프라에 배포된 [Docker 이미지](https://hub.docker.com/r/snyk/broker/)입니다. 자세한 내용은 [Snyk Broker의 구성요소](components-of-snyk-broker.md) 및 [Snyk Broker와의 연결](connections-with-snyk-broker.md)을 참조하세요.

사전 요구 사항, 구성 요소 선택, 네트워크 구성 및 자격 증명에 대한 자세한 내용은 [배포를 위한 Snyk Broker 준비하기](prepare-snyk-broker-for-deployment.md)를 참조하세요.
