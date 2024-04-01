# Snyk AppRisk를 위한 Integrations

## 개요

통합 페이지에는 기존 Snyk 조직에서 자동으로 동기화된 모든 데이터를 포함하여 모든 활성 integration이 표시되며 Integration Hub에 접근할 수 있습니다.

다음과 같은 Snyk 데이터는 자동으로 동기화됩니다:

* Snyk Open Source
* Snyk Code
* Snyk IaC
* Snyk Container

각각의 연결된 integration을 통해 다음과 같은 이점을 얻을 수 있습니다:

* 데이터 동기화 일시 중지
* Integration 프로파일 및 구성 수정
* Integration 삭제
* Integration이 마지막으로 동기화된 시점과 다음 동기화가 예약된 시점 확인

## Integration Hub 사용

Integration Hub 페이지를 사용하여 integration을 온보드하고 SCM 도구의 데이터로 Snyk AppRisk를 채웁니다.

다음 단계를 수행하여 integration을 추가할 수 있습니다:

1. AppRisk를 열고 Integrations 페이지로 이동합니다.
2. **Integration Hub**를 클릭합니다.
3. 연결할 integration에서 **Add**를 클릭합니다.
4. 구성 연결을 완료하고 **Done**를 클릭합니다.

Integration 설정 방법에 대한 단계별 자세한 내용은 [Connect an SCM integration](connect-an-scm-integration.md)페이지를 참조하십시오.

Integration이 확인되면 카드가 Integration 페이지에 표시되어 연결을 활성화 또는 비활성화하거나 설정을 편집하거나 구성에서 연결을 제거할 수 있습니다.

<figure><img src="../../../.gitbook/assets/image (11) (4).png" alt="AppRisk - Integration status" width="375"><figcaption><p>Snyk AppRisk - Integration status</p></figcaption></figure>

## Snyk Broker 사용

SCM 인스턴스에 공개적으로 접근할 수 없는 경우 Snyk Broker가 필요합니다. Docker 또는 Helm을 사용하여 Snyk Broker를 설치하고 구성할 수 있습니다. Snyk Broker에 대한 자세한 내용은 [Snyk Broker - AppRisk](../../../enterprise-configuration/snyk-broker/snyk-broker-apprisk.md)를 참조하십시오.

{% hint style="info" %}
명령을 실행하기 전에 Snyk Broker 배포 환경에서 Snyk AppRisk 플래그를 활성화합니다.
{% endhint %}

* GitHub - Snyk Broker 설치 및 구성
  * [using Docker](../../../enterprise-configuration/snyk-broker/install-and-configure-snyk-broker/github-install-and-configure-broker/broker-example-set-up-snyk-broker-with-github.md#docker-run-command-to-set-up-a-broker-client-for-github)
  * [using Helm](../../../enterprise-configuration/snyk-broker/install-and-configure-snyk-broker/github-install-and-configure-broker/githhub.com-install-and-configure-using-helm.md)
  * [environment variables](../../../enterprise-configuration/snyk-broker/install-and-configure-snyk-broker/github-install-and-configure-broker/github-environment-variables-for-snyk-broker.md)
* GitHub Enterprise - Snyk Broker 설치 및 구성
  * [using Docker](../../../enterprise-configuration/snyk-broker/install-and-configure-snyk-broker/github-enterprise-install-and-configure-broker/setup-broker-with-github-enterprise.md#docker-run-command-to-set-up-a-broker-client-for-github-enterprise)
  * [using Helm](../../../enterprise-configuration/snyk-broker/install-and-configure-snyk-broker/github-enterprise-install-and-configure-broker/github-enterprise-install-and-configure-using-helm.md)
  * [environment variables](../../../enterprise-configuration/snyk-broker/install-and-configure-snyk-broker/github-enterprise-install-and-configure-broker/github-enterprise-environment-variables-for-snyk-broker.md)
* BitBucket - Snyk Broker 설치 및 구성
  * [using Docker](../../../enterprise-configuration/snyk-broker/install-and-configure-snyk-broker/bitbucket-server-data-center-install-and-configure-broker/data-center.md#docker-run-command-to-set-up-a-broker-client-for-bitbucket)
  * [using Helm](../../../enterprise-configuration/snyk-broker/install-and-configure-snyk-broker/bitbucket-server-data-center-install-and-configure-broker/bitbucket-server-data-center-install-and-configure-using-helm.md)
  * [environment variables](../../../enterprise-configuration/snyk-broker/install-and-configure-snyk-broker/bitbucket-server-data-center-install-and-configure-broker/bitbucket-server-data-center-environment-variables-for-snyk-broker.md)
* GitLab - Snyk Broker 설치 및 구성
  * [using Docker](../../../enterprise-configuration/snyk-broker/install-and-configure-snyk-broker/gitlab-install-and-configure-broker/setup-broker-with-gitlab.md#docker-run-command-to-set-up-a-broker-client-for-gitlab)
  * [using Helm](../../../enterprise-configuration/snyk-broker/install-and-configure-snyk-broker/gitlab-install-and-configure-broker/gitlab-install-and-configure-using-helm.md)
  * [environment variables](../../../enterprise-configuration/snyk-broker/install-and-configure-snyk-broker/gitlab-install-and-configure-broker/gitlab-environment-variables-for-snyk-broker.md)
* Azure - Snyk Broker 설치 및 구성
  * [using Docker](../../../enterprise-configuration/snyk-broker/install-and-configure-snyk-broker/azure-repos-install-and-configure-broker/setup-broker-with-azure-repos.md#docker-run-command-to-set-up-a-broker-client-for-azure-repos)
  * [using Helm](../../../enterprise-configuration/snyk-broker/install-and-configure-snyk-broker/azure-repos-install-and-configure-broker/azure-repos-install-and-configure-and-configure-using-helm.md)
  * [environment variables](../../../enterprise-configuration/snyk-broker/install-and-configure-snyk-broker/azure-repos-install-and-configure-broker/azure-repos-environment-variables-for-snyk-broker.md)

[GitHub](https://github.com/snyk/broker/tree/565242baf003f06f445489dd96cc68c8386ede38/defaultFilters/apprisk)에서 integration에 대한 접근 가능한 엔드포인트의 허용된 목록을 포함하는 `.json` 파일을 찾을 수 있습니다.
