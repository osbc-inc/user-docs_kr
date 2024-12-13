# Snyk Broker - AppRisk

SCM 인스턴스에 공개적으로 액세스할 수 없는 경우 Snyk Broker가 필요합니다. Docker 또는 Helm을 사용하여 Snyk Broker를 설치하고 구성할 수 있습니다. Snyk AppRisk에서 지원되는 최소 Broker 버전은 [4.171.0](https://github.com/snyk/broker/releases/tag/v4.171.0)입니다.

{% hint style="info" %}
명령을 실행하기 전에 Snyk Broker 배포 환경에서 Snyk AppRisk 플래그를 활성화합니다.
{% endhint %}

* GitHub - Snyk Broker 설치 및 구성
  * [Docker 사용](install-and-configure-snyk-broker/github-install-and-configure-broker/broker-example-set-up-snyk-broker-with-github.md#docker-run-command-to-set-up-a-broker-client-for-github)
  * [Helm 사용](install-and-configure-snyk-broker/github-install-and-configure-broker/githhub.com-install-and-configure-using-helm.md)
  * [환경 변수 (environment variables)](install-and-configure-snyk-broker/github-install-and-configure-broker/github-environment-variables-for-snyk-broker.md)
* GitHub Enterprise - Snyk Broker 설치 및 구성:
  * [Docker 사용](install-and-configure-snyk-broker/github-enterprise-install-and-configure-broker/setup-broker-with-github-enterprise.md#docker-run-command-to-set-up-a-broker-client-for-github-enterprise)
  * [Helm 사용](install-and-configure-snyk-broker/github-enterprise-install-and-configure-broker/github-enterprise-install-and-configure-using-helm.md)
  * [환경 변수 (environment variables)](install-and-configure-snyk-broker/github-enterprise-install-and-configure-broker/github-enterprise-environment-variables-for-snyk-broker.md)
* BitBucket - Snyk Broker 설치 및 구성:
  * [Docker 사용](install-and-configure-snyk-broker/bitbucket-server-data-center-install-and-configure-broker/data-center.md#docker-run-command-to-set-up-a-broker-client-for-bitbucket)
  * [Helm 사용](install-and-configure-snyk-broker/bitbucket-server-data-center-install-and-configure-broker/bitbucket-server-data-center-install-and-configure-using-helm.md)
  * [환경 변수(environment variables)](install-and-configure-snyk-broker/bitbucket-server-data-center-install-and-configure-broker/bitbucket-server-data-center-environment-variables-for-snyk-broker.md)
* GitLab - Snyk Broker 설치 및 구성:
  * [Docker 사용](install-and-configure-snyk-broker/gitlab-install-and-configure-broker/setup-broker-with-gitlab.md#docker-run-command-to-set-up-a-broker-client-for-gitlab)
  * [Helm 사용](install-and-configure-snyk-broker/gitlab-install-and-configure-broker/gitlab-install-and-configure-using-helm.md)
  * [환경 변수(environment variables)](install-and-configure-snyk-broker/gitlab-install-and-configure-broker/gitlab-environment-variables-for-snyk-broker.md)
* Azure - Snyk Broker 설치 및 구성:
  * [Docker 사용](install-and-configure-snyk-broker/azure-repos-install-and-configure-broker/setup-broker-with-azure-repos.md#docker-run-command-to-set-up-a-broker-client-for-azure-repos)
  * [Helm 사용](install-and-configure-snyk-broker/azure-repos-install-and-configure-broker/azure-repos-install-and-configure-and-configure-using-helm.md)
  * [환경 변수(environment variables)](install-and-configure-snyk-broker/azure-repos-install-and-configure-broker/azure-repos-environment-variables-for-snyk-broker.md)

통합에 허용된 액세스 가능한 엔드포인트 목록이 포함된 업데이트된 모든`.json` 파일은 [GitHub](https://github.com/snyk/broker/tree/565242baf003f06f445489dd96cc68c8386ede38/defaultFilters/apprisk)에서 찾을 수 있습니다.
