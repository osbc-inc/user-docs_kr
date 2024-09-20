# Azure Repos - Snyk Broker의 환경 변수

Azure Repos용 Broker 클라이언트를 구성하려면 다음 환경 변수가 필요합니다:

* `BROKER_TOKEN` - Azure Repos 통합 설정 보기(app.snyk.io)에서 가져온 Snyk Broker 토큰입니다.
* `AZURE_REPOS_TOKEN` - Azure Repos 개인 액세스 토큰. 토큰을 가져오거나 만드는 방법은 이 가이드를 참조하세요. 필수 범위: 사용자 정의가 선택되어 있는지 확인하고 코드에서 _읽기 및 쓰기_를 선택합니다.
* `AZURE_REPOS_ORG` - 조직 이름(Azure의 조직 개요 페이지에서 찾을 수 있음). 온-프레미스 Azure Repos의 경우, 일반적인 조직 이름은 `tfs/Main`입니다.&#x20;
* `AZURE_REPOS_HOST` - Azure Repos Server 배포의 호스트 이름(예: `your.azure-server.domain.com`)
* `PORT` - Broker 클라이언트가 연결을 수락하는 로컬 포트입니다. 기본값은 8000입니다.
* `BROKER_CLIENT_URL` - Azure Repos의 웹훅에서 액세스할 수 있는 Broker 클라이언트의 전체 URL(예:`http://broker.url.example:8000`)입니다. 이 URL은 PR 수정 또는 PR 확인과 같은 기능에 액세스하는 데 필요합니다.
  * 여기에는 http:// 및 포트 번호가 있어야 합니다.
  * HTTPS로 클라이언트를 구성하려면, [추가 설정이 필요합니다.](https://docs.snyk.io/snyk-admin/snyk-broker/install-and-configure-broker-using-docker/advanced-configuration-for-snyk-broker-docker-installation/https-for-broker-client-with-docker)
* `ACCEPT_IAC` - 기본적으로 IaC(코드형 인프라)에서 사용하는 일부 파일 유형은 사용하도록 설정되어 있지 않습니다. Broker가 리포지토리에 있는 IaC 파일(예: Terraform)에 대한 액세스 권한을 부여하려면 환경 변수 `ACCEPT_IAC`를 `tf,yaml,yml,json,tpl`의 임의 조합으로 추가하면 됩니다.
* `ACCEPT_CODE` - 코드 에이전트를 사용할 때 Snyk 코드는 코드 스니펫을 로드하지 않습니다. 코드 스니펫을 활성화하려면 환경 변수`ACCEPT_CODE=true`를 추가할 수 있습니다.
* `ACCEPT_APPRISK` - 애플리케이션 자산을 식별하고, 모니터링하고, 위험의 우선순위를 지정하기 위해 Snyk AppRisk를 사용하도록 설정합니다. 환경 변수 `ACCEPT_APPRISK=true`를 추가하여 활성화할 수 있습니다.
