# Helm을 사용하여 Broker 설치 및 구성

Snyk Broker는 Snyk와 특수 통합 사이의 프록시 역할을 하는 오픈 소스 도구로, [snyk.io](http://snyk.io/) 가 코드에 액세스하여 코드를 스캔하고 결과를 사용자에게 반환할 수 있도록 합니다. Broker와의 SCM 통합은 Snyk 오픈 소스, Snyk 코드, Snyk 컨테이너(Docker파일) 및 Snyk IaC를 지원합니다. 작동 방식, 배포 방법, 커밋 서명, 업그레이드 및 문제 해결 등 Snyk Broker에 대한 자세한 내용은 [Snyk Broker 사용자 설명서](../)를 참조하세요.

**Kubernetes를 사용하는 경우**, Snyk은 [**Broker Helm Chart**](https://github.com/snyk/snyk-broker-helm)와 함께 **Snyk Broker를 설치**할 것을 권장합니다. 자세한 내용은 다음 섹션 “Snyk Broker Helm 차트를 사용한 설치”에 나열된 각 통합에 대한 지침을 참조하세요.

**다른 모든 환경**의 경우, Snyk에서 제공하는 [Docker 이미지](https://github.com/snyk/broker)를 사용하여 Snyk Broker를 설치할 수 있습니다. 자세한 내용은, [Docker를 사용하여 Broker 설치 및 구성](install-and-configure-broker-using-docker.md)을 참조하세요.

## Snyk Broker Helm 차트를 사용한 설치

**EU 및 AU용 멀티테넌트 설정**\
EU 또는 AU 멀티테넌트 환경에서 사용하기 위해 broker, 코드 에이전트 또는 둘 모두를 설정하는 경우 특정 URL이 포함된 추가 환경 변수가 필요합니다.\
예: `-e BROKER_SERVER_URL=https://broker.eu.snyk.io`\
URL에 대해서는, [EU and AU 계정 데이터 센터 생성](https://docs.snyk.io/snyk-processes/data-residency-at-snyk#eu-and-au-datacenter-account-creation)을 참조하세요.

**NOTE**\
Helm 차트는 연결을 관리하지 않으므로 쿠버네티스 클러스터에서 [ingress](advanced-configuration-for-helm-chart-installation/ingress-options-with-snyk-broker-helm-installation.md)를 관리할 책임은 사용자에게 있다.&#x20;

이 차트를 사용하려면 먼저 리포지토리를 추가하여 Snyk Broker Helm 차트를 추가해야 합니다:

`helm repo add snyk-broker https://snyk.github.io/snyk-broker-helm/`

그런 다음 사용자 설명서에 설명된 대로 각 SCM, 레지스트리 또는 Jira에 대한 명령을 실행합니다:

* [GitHub](github-install-and-configure-broker/githhub.com-install-and-configure-using-helm.md) `scmType`: `github-com`
* [GitHub Enterprise](github-enterprise-install-and-configure-broker/github-enterprise-install-and-configure-using-helm.md) `scmType`: `github-enterprise`
* [Bitbucket Server/Data Center](bitbucket-server-data-center-install-and-configure-broker/bitbucket-server-data-center-install-and-configure-using-helm.md) `scmType`: `bitbucket-server`
* [GitLab](gitlab-install-and-configure-broker/gitlab-install-and-configure-using-helm.md) `scmType`: `gitlab`
* [Azure Repos](azure-repos-install-and-configure-broker/azure-repos-install-and-configure-and-configure-using-helm.md) `scmType`: `azure-repos`
* [JFrog Artifactory](artifactory-repository-install-and-configure-broker/artifactory-repository-install-and-configure-using-helm.md) `scmType`: `artifactory`
* [Nexus 3](nexus-repository-install-and-configure-broker/nexus-repository-install-and-configure-using-helm.md) `scmType`: `nexus`
* [Nexus 2](nexus-repository-install-and-configure-broker/nexus-repository-install-and-configure-using-helm.md) `scmType`: `nexus2`
* [Jira](jira-install-and-configure-broker/jira-install-and-configure-using-helm.md) `scmType`: `jira`

**NOTE**\
`scmType`은 시스템 유형을 지정합니다. JFrog 및 Nexus의 경우 아티팩트 리포지토리이고, Jira의 경우 티켓 관리 시스템입니다,

각 SCM, 레지스트리 또는 Jira에 대한 명령을 실행하면 `snyk-broker`라는 네임스페이스가 만들어집니다. 기존 네임스페이스에 배포하려면 `-n` 매개 변수를 조정하고 `--create-namespace` 매개 변수를 삭제하세요. 동일한 네임스페이스에 여러 브로커 배포하기도 참조하세요.

**NOTE**\
버전 2.0.0부터 생성된 모든 객체에는 릴리스 이름에 따라 접미사가 붙어서 동일한 네임스페이스에 여러 브로커를 사용할 수 있습니다. 이전 버전과의 호환성을 위해 2.1.0에서는 `--set disableSuffixes=true`를 추가하여 1.x.x 동작으로 되돌릴 수 있는 disableSuffixes 플래그가 도입되었습니다.

추가 명령어를 사용하여 Snyk 브로커 코드 에이전트 및 컨테이너 레지스트리 에이전트를 설치할 수 있습니다.

* [Snyk Broker Code Agent](../snyk-broker-code-agent/) (SAST 분석을 활성화하는 데 필요)
* [Snyk Broker - Container Registry Agent](../snyk-broker-container-registry-agent/)(컨테이너 레지스트리에 연결하기 위해 필요; `scmType`: `container-registry-agent`\\)

Broker가 실행 중인지 확인하려면 [the Snyk Web UI](https://app.snyk.io) 에서 Broker 연동 설정을 확인하면 연결되었다는 확인 메시지가 표시됩니다. 연결되면 프로젝트 가져오기를 시작할 수 있습니다.

## Helm 차트를 사용하여 Snyk Broker의 고급 파라미터 설정하기

Helm을 사용하여 Snyk Broker를 설정할 때 다음 페이지에 설명된 대로 고급 매개변수를 설정할 수 있습니다:

* [Helm으로 문제를 해결하고 자체 인증서를 제공하기 위한 매개변수](advanced-configuration-for-helm-chart-installation/parameters-for-troubleshooting-and-providing-your-own-certificate-with-helm.md)
* [Helm 차트 설치를 위한 프록시 설정](advanced-configuration-for-helm-chart-installation/proxy-settings-for-broker-helm-chart-installation.md)
* [Docker와  Helm을 사용한 자격 증명 풀링](advanced-configuration-for-snyk-broker-docker-installation/credential-pooling-with-docker-and-helm.md)
* [Helm 설치를 위한 사용자 정의 accept.json 추가하기](advanced-configuration-for-helm-chart-installation/adding-custom-accept.json-for-helm-installation.md)
* [Snyk Broker Helm 설치를 통한  Ingress 옵션](advanced-configuration-for-helm-chart-installation/ingress-options-with-snyk-broker-helm-installation.md)
* [Helm 차트 설치를 위한 멀티테넌트 설정](advanced-configuration-for-helm-chart-installation/multi-tenant-settings-for-helm-chart-installation.md)
* [동일한 네임스페이스에 여러 Broker 배포하기](advanced-configuration-for-helm-chart-installation/deploying-multiple-brokers-in-the-same-namespace.md)
* [Broker Helm 차트 설치를 위한 사용자 정의 추가 옵션](advanced-configuration-for-helm-chart-installation/custom-additional-options-for-broker-helm-chart-installation.md)
* [Snyk 코드에 대한 Broker 규칙](advanced-configuration-for-helm-chart-installation/broker-rules-for-snyk-code.md)
* [고가용성 모드](../high-availability-mode.md)
* [대용량 메니페스트 파일 규칙 추가](advanced-configuration-for-helm-chart-installation/snyk-open-source-scans-sca-of-large-manifest-files-helm-setup.md)
* [안전하지 않은 다운스트림 모드](advanced-configuration-for-helm-chart-installation/insecure-downstream-mode.md)
