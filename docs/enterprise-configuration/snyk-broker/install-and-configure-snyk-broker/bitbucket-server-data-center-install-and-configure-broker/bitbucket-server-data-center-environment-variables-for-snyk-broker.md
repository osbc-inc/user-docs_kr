# BitBucket Server/Data Center - Snyk Broker의 환경 변수

브로커 클라이언트를 구성하려면 다음 환경 변수가 필요합니다:

* `BROKER_TOKEN` -Bitbucket Server 통합 설정 보기(app.snyk.io)에서 얻은 Snyk Broker 토큰입니다.
* `BITBUCKET_USERNAME` - Bitbucket Server 사용자 이름입니다.
* `BITBUCKET_PASSWORD` - Bitbucket Server 비밀번호입니다. 비밀번호 대신 API 토큰을 사용할 수 있습니다.
* `BITBUCKET` - Bitbucket Server 배포의 호스트 이름(예:`your.bitbucket-server.domain.com`).
* `BITBUCKET_API` - Bitbucket Server 배포의 API 엔드포인트입니다. `$BITBUCKET/rest/api/1.0`이어야 합니다.
* `BROKER_CLIENT_URL` - 웹훅용 Bitbucket Server에서 액세스할 수 있는 Broker 클라이언트의 전체 URL(예:`http://broker.url.example:8000`)입니다. 이 URL은 PR 수정 또는 PR 확인과 같은 기능에 액세스하는 데 필요합니다.
  * 여기에는 http:// 및 포트 번호가 있어야 합니다.
  * HTTPS로 클라이언트를 구성하려면, [추가 구성이 필요합니다](https://docs.snyk.io/snyk-admin/snyk-broker/install-and-configure-broker-using-docker/advanced-configuration-for-snyk-broker-docker-installation/https-for-broker-client-with-docker).
* `PORT` - Broker 클라이언트가 연결을 수락하는 로컬 포트입니다. 기본값은 8000입니다.
* `ACCEPT_IAC` -기본적으로 IaC(Infrastructure-as-Code)에서 사용하는 일부 파일 유형은 사용하도록 설정되어 있지 않습니다. 예를 들어 Terraform과 같은 리포지토리에 있는 IaC 파일에 대한 Broker의 액세스 권한을 부여하려면 환경 변수`ACCEPT_IAC`를`tf,yaml,yml,json,tpl`의 임의 조합으로 추가하기만 하면 됩니다.
* `ACCEPT_CODE` - 코드 에이전트를 사용할 때 Snyk 코드는 코드 스니펫을 로드하지 않습니다. 코드 스니펫을 활성화하려면 환경 변수`ACCEPT_CODE=true`를 추가하면 됩니다.
* `ACCEPT_APPRISK` - 애플리케이션 자산을 식별하고 모니터링하며 위험의 우선순위를 지정하기 위해 Snyk AppRisk를 활성화합니다. Snyk 앱리스크를 활성화하려면 환경 변수 `ACCEPT_APPRISK=true`를 추가합니다.
