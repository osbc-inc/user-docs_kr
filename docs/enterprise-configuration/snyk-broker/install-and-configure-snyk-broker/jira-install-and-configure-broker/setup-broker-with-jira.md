# Jira - Docker를 사용하여 설치 및 구성하기

이 페이지의 지침에 따라 Snyk Broker로 Jira를 설정하세요. 이 통합은 온프레미스 Jira 배포와의 안전한 연결을 보장하는 데 유용합니다.

{% hint style="info" %}
Docker는 필수입니다.
{% endhint %}

## Web UI에서 Broker 토큰 생성하기

1. **Settings(설정)** > **Integrations(통합)** > **Jira** > **개인 네트워크 내에 Jira를 설치하려면** 여기를 클릭합니다.
2. **Generate(생성)** 을 클릭하여 Jira용 Broker 토큰을 생성하고 **Show(표시)**를 클릭하여 확인합니다.

## Jira에 사용하도록 Broker 구성하기

Jira 배포와 함께 Broker 클라이언트를 사용하려면 `docker pull snyk/broker:jira`를 실행하세요.환경 변수에 대한 정의는[Jira - Snyk Broker의 환경 변수](jira-environment-variables-for-snyk-broker.md)를 참조하세요.

## Docker 실행 명령으로 Jira용 Broker 클라이언트 설정하기

**다음 명령을 복사**하여 Jira와 함께 사용할 완전히 구성된 Broker 클라이언트를 설정하세요. 관련 구성을 제공하여 Docker 컨테이너를 실행할 수 있습니다:

```console
docker run --restart=always \
           -p 8000:8000 \
           -e BROKER_TOKEN=secret-broker-token \
           -e JIRA_USERNAME=username \
           -e JIRA_PASSWORD=password \
           -e JIRA_HOSTNAME=your.jira.domain.com \
           -e BROKER_CLIENT_URL=http://my.broker.client:8000 \
           -e PORT=8000 \
       snyk/broker:jira
```

필요한 경우, [Snyk Broker Docker 설치를 위한 고급 구성](../advanced-configuration-for-snyk-broker-docker-installation/)으로 이동하여 필요한 구성 변경(예: Jira 인스턴스에서 비공개 인증서를 사용하는 경우 Broker 클라이언트 구성에 CA(인증 기관)를 제공하는 등)을 수행합니다.

Docker 실행 명령을 사용하는 대신 파생된 Docker 이미지를 사용하여 브로커 클라이언트 연동을 설정할 수 있습니다. Jira 통합을 위해 재정의할 환경 변수에 대해서는 [파생된 Docker 이미지](../derived-docker-images-for-broker-client-integrations-and-container-registry-agent.md)를 참조하세요.

## SSO 지원 JIRA를 위한 Jira PAT 인증

SSO가 활성화된 경우, JIRA는 일반적으로 사용자 이름과 비밀번호 사용을 금지하고 개인용 액세스 토큰(PAT)을 사용하도록 요구합니다.

SSO를 사용하도록 설정한 경우 무기명 토큰과 함께 권한 부여 헤더를 대신 사용하는 특정 Jira 버전을 사용해야 합니다. 이 버전을 사용하려면 다음 구성을 제공하세요:

```
docker run --restart=always \
           -p 8000:8000 \
           -e BROKER_TOKEN=secret-broker-token \
           -e JIRA_PAT=<your_pat_token> \
           -e JIRA_HOSTNAME=your.jira.domain.com \
           -e BROKER_CLIENT_URL=http://my.broker.client:8000 \
           -e PORT=8000 \
       snyk/broker:jira-bearer-auth
```

## Broker 클라이언트 컨테이너를 시작하고 Jira와의 연결을 확인합니다.

Broker 클라이언트 구성을 붙여넣어 Broker 클라이언트 컨테이너를 시작합니다.

컨테이너가 설정되고 Jira 통합 페이지에 Jira에 대한 연결이 표시되면 프로젝트 아래에서 Jira 티켓을 만들 수 있습니다.

## Jira를 사용한 Broker의 기본 문제 해결

* `docker logs <container id>` 를 실행하여 오류를 찾습니다(여기서 컨테이너 ID는 Jira Broker 컨테이너 ID).
* 관련 포트가 Jira에 노출되어 있는지 확인합니다.
