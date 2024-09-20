# GitLab - Snyk Broker의 환경 변수

다음 환경 변수는 GitLab용 Broker 클라이언트를 구성하는 데 필요합니다:

* `BROKER_TOKEN` - GitLab 통합 설정 보기(app.snyk.io)에서 얻은 Snyk Broker 토큰.
* `GITLAB_TOKEN` - `api`범위가 있는 GitLab 개인 액세스 토큰입니다.&#x20;
* `GITLAB` - GitLab 배포의 호스트 이름(예: `your.gitlab.domain.com` 또는`GitLab.com`).
* `PORT` - Broker 클라이언트가 연결을 수락하는 로컬 포트입니다. 기본값은 8000입니다.
* `BROKER_CLIENT_URL` - 웹훅 연결을 설정하기 위해 GitLab.com 또는 온프레미스 GitLab 배포에서 연결할 수 있어야 하는 Broker 클라이언트의 전체 URL입니다.`http://broker.url.example:8000`같은 전체 URL이어야 합니다.
  * 여기에는 http:// 및 포트 번호가 있어야 합니다.
  * HTTPS로 클라이언트를 구성하려면, [추가 구성이 필요합니다](https://docs.snyk.io/snyk-admin/snyk-broker/install-and-configure-broker-using-docker/advanced-configuration-for-snyk-broker-docker-installation/https-for-broker-client-with-docker).
* `ACCEPT_IAC` - 기본적으로 IaC(Infrastructure-as-Code)에서 사용하는 일부 파일 유형은 활성화되어 있지 않습니다. 예를 들어 Terraform과 같은 리포지토리에 있는 IaC 파일에 대한 Broker의 액세스 권한을 부여하려면 환경 변수`ACCEPT_IAC`를 `tf,yaml,yml,json,tpl`의 조합으로 추가하기만 하면 됩니다.
* `ACCEPT_CODE` - 기본적으로 Snyk Broker - 코드 에이전트를 사용할 때 Snyk 코드는 코드 스니펫을 로드하지 않습니다. 코드 스니펫을 활성화하려면 환경 변수 `ACCEPT_CODE=true`를 추가하면 됩니다.
* `ACCEPT_APPRISK` - 애플리케이션 자산을 식별하고, 모니터링하고, 위험의 우선순위를 지정할 수 있도록 Snyk AppRisk를 활성화합니다. 환경 변수 `ACCEPT_APPRISK=true`를 추가하여 활성화할 수 있습니다.
