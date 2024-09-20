# GitHub Enterprise - Snyk Broker의 환경 변수

Broker 클라이언트를 구성하려면 다음 환경 변수가 필요합니다: GitHub Enterprise의 경우:

* `BROKER_TOKEN` - Snyk 조직 설정 보기(app.snyk.io)에서 얻은 Snyk Broker 토큰입니다.
* `GITHUB_TOKEN` - 전체 `repo`, `read:org` 및`admin:repo_hook` 범위의 개인 액세스 토큰입니다.
* `GITHUB` -GitHub Enterprise 배포의 호스트 이름입니다:
  * 자체 호스팅 또는 사용자 지정 도메인의 경우, GitHub Enterprise 도메인`your.ghe.domain.com`입니다.
  * 사용자 지정 도메인이 없는 GitHub Enterprise Cloud의 경우 `github.com`을 사용합니다.
  * 도메인 뒤에 조직이나 경로를 포함하지 마세요.
* `GITHUB_API` - GitHub Enterprise 배포의 API 엔드포인트입니다. `http` 또는`https`를 사용하지 마세요.
  * 자체 호스팅의 경우, `your.ghe.domain.com/api/v3`이어야 합니다.
  * 사용자 지정 도메인이 없는 GitHub Enterprise Cloud의 경우, `api.github.com`을 사용하세요.
* `GITHUB_GRAPHQL` - GitHub Enterprise 배포의 graphql 엔드포인트입니다. `http` 또는`https`를 사용하지 마세요.
  * 자체 호스팅의 경우, `your.ghe.domain.com/api`여야 합니다.
  * 사용자 지정 도메인이 없는 GitHub Enterprise Cloud의 경우, `api.github.com/graphql`을 사용합니다.
* `PORT` - Broker 클라이언트가 연결을 수락하는 로컬 포트입니다. 기본값은 8000입니다.
* `BROKER_CLIENT_URL` - GitHub Enterprise 배포 웹훅에서 액세스할 수 있는 Broker 클라이언트의 전체 URL(예:`http://broker.url.example:8000`).
  * 여기에는 `http://` 및 포트 번호가 있어야 합니다.
  * HTTPS로 클라이언트를 구성하려면, [추가 설정이 필요합니다.](../advanced-configuration-for-snyk-broker-docker-installation/https-for-broker-client-with-docker.md)
* `ACCEPT_IAC` - 기본적으로, 코드형 인프라(IaC)에서 사용하는 일부 파일 형식은 활성화되지 않습니다. Broker에 리포지토리의 IaC 파일(예: Terraform 파일)에 대한 액세스 권한을 부여하려면 환경 변수 `ACCEPT_IAC` 를 `tf,yaml,yml,json,tpl`의 임의 조합으로 추가하면 됩니다.
* `ACCEPT_CODE` - 기본적으로 Snyk Broker - 코드 에이전트를 사용할 때 Snyk 코드는 코드 스니펫을 로드하지 않습니다. 코드 스니펫을 활성화하려면 환경 변수 `ACCEPT_CODE=true`를 추가하면 됩니다.
* `ACCEPT_APPRISK` - 애플리케이션 자산을 식별하고, 모니터링하고, 위험의 우선순위를 지정하기 위해 Snyk AppRisk를 활성화합니다. Snyk AppRisk를 활성화하려면 환경 변수 `ACCEPT_APPRISK=true`를 추가합니다.
