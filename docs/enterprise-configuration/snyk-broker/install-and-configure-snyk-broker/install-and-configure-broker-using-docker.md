# Docker를 사용하여 Broker 설치 및 구성하기

Snyk Broker는 Snyk와 특수 통합 사이의 프록시 역할을 하는 오픈 소스 도구로, [snyk.io](http://snyk.io/) 가 코드에 액세스하여 코드를 스캔하고 결과를 사용자에게 반환할 수 있도록 합니다. Broker와의 SCM 통합은 Snyk 오픈 소스, Snyk 코드, Snyk 컨테이너(Docker파일) 및 Snyk IaC를 지원합니다. 작동 방식, 배포 방법, 커밋 서명, 업그레이드 및 문제 해결 등 Snyk Broker에 대한 자세한 내용은 Snyk Broker 사용자 설명서를 참조하세요.

**Kubernetes를 사용하는 경우**, Snyk은 [**Broker Helm Chart**](https://github.com/snyk/snyk-broker-helm)와 함께 **Snyk Broker를 설치**하는 것을 권장한다. 자세한 내용은 [Helm을 사용하여 Broker 설치 및 구성](install-and-configure-broker-using-helm.md)을 참조한다.

**다른 모든 환경**의 경우, Snyk에서 제공하는 [Docker 이미지](https://github.com/snyk/broker)를 사용하여 Snyk Broker를 설치할 수 있습니다. 여기에 나열된 페이지에서는 Docker를 사용하여 Snyk Broker 클라이언트 통합을 설정하는 방법을 설명합니다.

## Docker를 사용한 설치

**EU 및 AU용 멀티테넌트 설정**\
EU 또는 AU 멀티테넌트 환경에서 사용하기 위해 broker, 코드 에이전트 또는 둘 모두를 설정하는 경우 특정 URL이 포함된 추가 환경 변수가 필요합니다.\
예:`-e BROKER_SERVER_URL=https://broker.eu.snyk.io`\
URL에 대해서는 [EU and AU 계정 데이터 센터 생성](https://docs.snyk.io/snyk-processes/data-residency-at-snyk#eu-and-au-datacenter-account-creation)을 참조하세요.

* [GitHub](github-install-and-configure-broker/broker-example-set-up-snyk-broker-with-github.md)
* [GitHub Enterprise](github-enterprise-install-and-configure-broker/setup-broker-with-github-enterprise.md)
* [Bitbucket Server/Data Centre](bitbucket-server-data-center-install-and-configure-broker/data-center.md)
* [Gitlab](gitlab-install-and-configure-broker/setup-broker-with-gitlab.md)
* [Azure Repos](azure-repos-install-and-configure-broker/setup-broker-with-azure-repos.md)
* [JFrog Artifactory Repository](artifactory-repository-install-and-configure-broker/set-up-snyk-broker-with-artifactory-repository.md)
* [Nexus Repository Manager](nexus-repository-install-and-configure-broker/set-up-snyk-broker-with-nexus-repository-manager.md)
* [Jira](jira-install-and-configure-broker/setup-broker-with-jira.md)
* [Snyk Broker - Container Registry Agent](../snyk-broker-container-registry-agent/) (컨테이너 레지스트리에 연결하기 위해 필요)
* [Snyk Broker - Code Agent](../snyk-broker-code-agent/) (SAST 분석을 활성화하는 데 필요)
* [Derived Docker images for Broker Client integrations and Container Registry Agent](derived-docker-images-for-broker-client-integrations-and-container-registry-agent.md)

{% hint style="info" %}
Docker 이미지의 환경 변수를 사용하여 구성을 사용자 지정할 수 있습니다. 따라서 적절한 구성과 중복성을 보장하기 위해 서로 다른 통합 유형에 대해 Broker 클라이언트의 여러 인스턴스를 별도로 설치하세요.
{% endhint %}

Broker가 실행 중인지 확인하려면[ Snyk Web UI](https://app.snyk.io)에서 Broker 연동 설정을 확인하면 연결되었다는 확인 메시지가 표시됩니다. 연결되면 프로젝트 가져오기를 시작할 수 있습니다.

Docker를 사용하여 설치하는 경우 다음 지침에 따라 필요에 따라 Broker를 구성하세요:

* [Docker로 인증 방법 변경하기](advanced-configuration-for-snyk-broker-docker-installation/changing-the-auth-method-with-docker.md)
* [Docker를 사용한 자격 증명 풀링](advanced-configuration-for-snyk-broker-docker-installation/credential-pooling-with-docker-and-helm.md)
* [Docker를 사용한 Broker 클라이언트용  HTTPS](advanced-configuration-for-snyk-broker-docker-installation/https-for-broker-client-with-docker.md)
* [Docker용 내부 인증서를 사용한 백엔드 요청 ](advanced-configuration-for-snyk-broker-docker-installation/backend-requests-with-an-internal-certificate-for-docker.md)&#x20;
* [Docker에서 프록시 지원](advanced-configuration-for-snyk-broker-docker-installation/proxy-support-with-docker.md)
* [Docker에서 인증서 확인 비활성화](advanced-configuration-for-snyk-broker-docker-installation/disable-certificate-verification-with-docker.md)
* [Docker 설치에 대한 사용자 지정 허용 목록 추가하기](broken-reference/)
* [Docker를 사용한 사용자 지정 승인 목록 필터](advanced-configuration-for-snyk-broker-docker-installation/custom-approved-listing-filter-with-docker.md)
* [Docker를 사용한 마운팅 시크릿](advanced-configuration-for-snyk-broker-docker-installation/mounting-secrets-with-docker.md)
* [Snyk 코드- Docker용 Broker를 사용한 복제 기능](advanced-configuration-for-snyk-broker-docker-installation/snyk-code-clone-capability-with-broker-for-docker.md)
* [고가용성 모드](../high-availability-mode.md)
* [대용량 매니페스트 파일 규칙 추가](advanced-configuration-for-snyk-broker-docker-installation/snyk-open-source-scans-sca-of-large-manifest-files-docker-setup.md)
* [안전하지 않은 다운스트림 모드](advanced-configuration-for-snyk-broker-docker-installation/insecure-downstream-mode.md)

## Snyk Broker에 대한 일반적인 질문

**Snyk Broker는 얼마나 자주 업데이트되나요?**\
Snyk Broker는 새로운 기능이 추가되거나 수정 사항이 있을 때마다 업데이트됩니다.

**Snyk Broker는 얼마나 자주 취약점을 검사하나요?**\
Snyk Broker 애플리케이션과 이미지의 취약점은 매일 테스트됩니다.

**취약점 수정에 대한 SLA는 어떻게 되나요?**\
높은 수준의 취약점을 수정하는 데는 14일, 공개 이미지의 중요한 취약점을 수정하는 데는 5일의 SLA가 있습니다.

## 개발자를 위한 추가 정보

업그레이드해야 하는 경우, [Snyk Broker 클라이언트 업그레이드](https://docs.snyk.io/snyk-admin/snyk-broker/upgrade-the-snyk-broker-client)를 참조하세요.

문제 해결 정보는 [Broker 문제 해결](https://docs.snyk.io/snyk-admin/snyk-broker/troubleshooting-broker) 페이지에 나와 있습니다.

&#x20;[license, Apache License, Version 2.0](https://github.com/snyk/broker/blob/master/LICENSE)을 확인할 수 있습니다.

풀 리퀘스트를 제출하려면 [기여하기](https://github.com/snyk/broker/blob/master/.github/CONTRIBUTING.md)를 참조하세요.

Broker에 대한 구체적인 정보는 [보안](https://github.com/snyk/broker/blob/master/SECURITY.md)을 참조하세요.
