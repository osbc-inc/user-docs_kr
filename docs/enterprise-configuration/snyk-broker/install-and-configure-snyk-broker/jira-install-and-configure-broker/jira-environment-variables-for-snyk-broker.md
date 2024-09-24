# Jira - Snyk Broker의 환경 변수

Jira용 Broker 클라이언트를 구성하려면 다음 환경 변수가 필요합니다:

* `BROKER_TOKEN` - Jira 통합 설정 보기에서 가져온 Snyk Broker 토큰입니다.
* `JIRA_USERNAME` - Jira 사용자 이름입니다.
* `JIRA_PASSWORD` -Jira 비밀번호입니다.
* `JIRA_HOSTNAME` - Jira 배포의 호스트 이름(예: `your.jira.domain.com`)입니다.
* `BROKER_CLIENT_URL` - 웹훅을 위해 Jira에서 액세스할 수 있는 브로커 클라이언트의 전체 URL(예:`http://my.broker.client:8000`)&#x20;
  * 여기에는 http:// 및 포트 번호가 있어야 합니다.
  * HTTPS로 클라이언트를 구성하려면, [추가 설정이 필요합니다.](https://docs.snyk.io/snyk-admin/snyk-broker/install-and-configure-broker-using-docker/advanced-configuration-for-snyk-broker-docker-installation/https-for-broker-client-with-docker)
* `PORT` - Broker 클라이언트가 연결을 수락하는 로컬 포트입니다. 기본값은 8000입니다.
