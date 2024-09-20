# GitLab - Docker를 사용한 설치 및 구성

이 페이지의 안내에 따라 Snyk Broker로 GitLab을 설정하세요. 이 통합은 온프레미스 또는 클라우드 GitLab 배포와의 안전한 연결을 보장하는 데 유용합니다.

{% hint style="info" %}
**전제 조건**

Snyk 계정 팀에 브로커 토큰을 제공하도록 요청하세요.

Snyk과의 연동을 위해 GitLab 권한이 올바른지 확인합니다. 자세한 내용은 [GitLab 연동](../../../../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/snyk-gitlab-integration.md)을 참조하세요.&#x20;

Docker 또는 Docker Linux 컨테이너를 실행할 수 있는 방법이 필요합니다. 일부 Windows용 Docker 배포는 Windows 컨테이너만 실행합니다. 배포가 Linux 컨테이너를 실행할 수 있는지 확인하세요.
{% endhint %}

## GitLab에 사용할 Broker 구성하기

definitions of the environment variables. GitLab.com 또는 온프레미스 GitLab 배포에서 Broker 클라이언트를 사용하려면`docker pull snyk/broker:gitlab`을 **실행**하세요. 환경 변수에 대한 정의는 [GitLab - Snyk Broker의 환경 변수](gitlab-environment-variables-for-snyk-broker.md)를 참조하세요.

**필요한 경우,** [고급 구성 페이지](../advanced-configuration-for-snyk-broker-docker-installation/)로 이동하여 CA(인증 기관을 브로커 클라이언트 구성에 제공하거나(GitlLab 인스턴스가 비공개 인증서를 사용하는 경우) [proxy 지원](../advanced-configuration-for-snyk-broker-docker-installation/proxy-support-with-docker.md)을 설정하는 등 **필요한 구성을 변경**합니다.

## Docker 실행 명령으로 GitLab용 브로커 클라이언트 설정하기

**다음 명령을 복사하여**, 완전히 구성된 Broker 클라이언트를 설정하여 오픈 소스, IaC, 컨테이너, 코드 파일(코드 에이전트 포함) 및 Snyk AppRisk 정보를 분석하세요. 애플리케이션 자산을 식별하고, 모니터링하고, 위험의 우선순위를 지정할 수 있도록 [Snyk AppRisk](../../../../manage-risk/snyk-apprisk/)를 활성화합니다.&#x20;

```bash
docker run --restart=always \
           -p 8000:8000 \
           -e BROKER_TOKEN=<secret-broker-token> \
           -e GITLAB_TOKEN=<secret-gitlab-token> \
           -e GITLAB=<your.gitlab.domain.com (no http/s)> \
           -e PORT=8000 \
           -e BROKER_CLIENT_URL=<http://broker.url.example:8000 (dns/IP:port)> \
           -e ACCEPT_IAC=tf,yaml,yml,json,tpl \
           -e ACCEPT_CODE=true \
           -e ACCEPT_APPRISK=true \
       snyk/broker:gitlab
```

{% hint style="info" %}
Snyk AppRisk는 기본적으로**`false`**로 설정되어 있습니다. 플래그를 **`true`**로 설정하여 사용하도록 설정합니다.
{% endhint %}

Docker 실행 명령을 사용하는 대신 파생된 Docker 이미지를 사용하여 Broker 클라이언트 연동을 설정할 수 있습니다. GitLab 연동을 위해 재정의할 환경 변수는 [파생된 Docker 이미지](../derived-docker-images-for-broker-client-integrations-and-container-registry-agent.md)를 참조하세요.

## Broker 클라이언트 컨테이너를 시작하고 GitLab과의 연결을 확인합니다.

Broker 클라이언트 구성을 붙여넣어 Broker 클라이언트 컨테이너를 시작합니다.

컨테이너가 시작되면 GitLab 통합 페이지에 GitLab 연결이 표시되고 프로젝트를 추가(`Add Projects`)할 수 있습니다.

## GitLab을 사용한 Broker의 기본 문제 해결

* `docker logs <container id>`실행하여 오류를 찾습니다. 여기서 컨테이너 ID는 GitLab Broker 컨테이너 ID입니다.
* 관련 포트가 GitLab에 노출되어 있는지 확인합니다.
