# Nexus 리포지토리 - Docker를 사용하여 설치 및 구성하기

{% hint style="info" %}
**기능 가용성**

Nexus 리포지토리 관리자와의 통합은 Enterprise 요금제에서만 사용할 수 있습니다.

자세한 내용은 [요금제 및 가격](https://snyk.io/plans)을 참조하세요.
{% endhint %}

이 페이지의 안내에 따라 스닉 브로커로 Nexus 리포지토리 관리자를 설정하세요. 이 통합은 온프레미스 Nexus 리포지토리 관리자 배포와의 안전한 연결을 보장하는 데 유용합니다.

{% hint style="info" %}
**전제 조건**\
Snyk 계정 팀에 Broker 토큰 제공을 요청하거나 Snyk 웹 UI에서 토큰을 생성합니다.

Docker 또는 Docker Linux 컨테이너를 실행할 수 있는 방법이 필요합니다. 일부 Windows용 Docker 배포는 Windows 컨테이너만 실행합니다. 배포가 Linux 컨테이너를 실행할 수 있는지 확인하세요.
{% endhint %}

{% hint style="info" %}
지원되는 환경 및 버전, 사용자 권한 등 Nexus 리포지토리 관리자와의 비브로커 통합에 대한 자세한 내용은 [Nexus Repository 관리자 설정](../../../../integrate-with-snyk/package-repository-integrations/nexus-repository-manager-connection-setup/)을 참조하세요.
{% endhint %}

{% hint style="info" %}
넥서스 컨테이너 레지스트리와의 브로커 통합에 대한 자세한 내용은 [Snyk Broker -Container Registry Agent](../../snyk-broker-container-registry-agent/)를 참조하세요.
{% endhint %}

## Nexus 통합을 위한 Broker 토큰 받기

1. &#x20;<img src="../../../../.gitbook/assets/cog_icon.png" alt="Settings icon" data-size="line"> > **Integrations > Package Repositories > Nexus** 로 이동합니다.
2. Nexus를 구성하는 화면이 표시되는지 확인합니다.

<figure><img src="../../../../.gitbook/assets/Screenshot 2022-07-15 at 15.15.11.png" alt="Configure Nexus"><figcaption><p>Nexus 구성</p></figcaption></figure>

{% hint style="info" %}
**Snyk Broker** 스위치가 표시되지 않으면 필요한 권한이 없는 것이며 공개적으로 액세스할 수 있는 인스턴스만 추가할 수 있습니다.

비공개 레지스트리를 추가하려면 [Snyk  지원팀](https://support.snyk.io/hc/en-us/requests/new)에 요청을 제출하세요.
{% endhint %}

비공개 레지스트리를 추가할 수 있는 권한이 있으면 [Web UI에서 Broker 토큰 생성하기](set-up-snyk-broker-with-nexus-repository-manager.md#generate-a-broker-token-from-the-web-ui)를 계속 진행합니다.

## Web UI에서 브로커 토큰 생성하기

1. Nexus 연동 설정에서 **\[Snyk Broker on/off]** 스위치를 켜기로 이동하여 Broker 토큰을 생성하기 위한 양식을 표시합니다.
2. **\[Generate and Save]**을 선택합니다.
3. Broker 클라이언트를 설정할 때 사용하기 위해 생성된 토큰을 복사합니다.

## Nexus 플러그인에 사용하도록 Broker 구성하기

### Nexus 3 및 Nexus 2용 도커 풀 구성

Nexus 3 배포에서 Broker 클라이언트를 사용하려면 `docker pull snyk/broker:nexus`를 **실행**합니다.

넥서스 2 배포에서 브로커 클라이언트를 사용하려면, `docker pull snyk/broker:nexus2`를 **실행**하세요.

환경 변수에 대한 정의는 [Nexus Repository - Snyk Broker의 환경 변수](nexus-repository-environment-variables-for-snyk-broker.md)를 참조하세요.

### Nexus 3 및 Nexus 2 통합을 위한 Broker 클라이언트를 설정하기 위한 Docker 실행 명령

**다음 명령을 복사**하여 Nexus 3에서 사용할 수 있도록 완전히 구성된 Broker 클라이언트를 설정합니다. 관련 구성을 제공하여 Docker 컨테이너를 실행할 수 있습니다:

```console
docker run --restart=always \
           -p 7341:7341 \
           -e BROKER_TOKEN=secret-broker-token \
           -e BASE_NEXUS_URL=https://[<user>:<pass>@]<your.nexus.hostname> \
           -e BROKER_CLIENT_VALIDATION_URL=https://<your.nexus.hostname>/service/rest/v1/status[/check] \
           -e RES_BODY_URL_SUB=https://<your.nexus.hostname>/repository \
       snyk/broker:nexus
```

**다음 명령을 복사**하여 Nexus 2에서 사용할 수 있도록 완전히 구성된 Broker 클라이언트를 설정합니다. 관련 구성을 제공하여 Docker 컨테이너를 실행할 수 있습니다:

```
docker run --restart=always \
  -p 7341:7341 \
  -e BROKER_TOKEN=<secret-broker-token> \
  -e BASE_NEXUS_URL=https://[username:password]@acme.com \
  -e RES_BODY_URL_SUB=https://acme.com/nexus/content/(groups|repositories) \ 
  snyk/broker:nexus2
```

**Docker 실행 명령을 사용하는 대신** 파생된 Docker 이미지를 사용하여 Broker 클라이언트 연동을 설정할 수 있습니다. Nexus3 연동을 위해 재정의할 환경 변수는 [파생된 Docker 이미지](../derived-docker-images-for-broker-client-integrations-and-container-registry-agent.md)를 참조하세요.

## Broker 클라이언트 컨테이너를 시작하고 Nexus 리포지토리 관리자와의 연결을 확인합니다.

Broker 클라이언트 구성을 붙여넣어 Broker 클라이언트 컨테이너를 시작합니다.

Broker 클라이언트`/systemcheck` endpoint에 요청하여 연결 상태를 확인합니다.

예: `curl http://172.17.0.2:7341/systemcheck`

성공 결과는 다음과 같은 형식으로 표시됩니다:

`{"brokerClientValidationUrl":"https://acme.com/service/rest/v1/status","brokerClientValidationMethod":"GET","brokerClientValidationTimeoutMs":5000,"brokerClientValidationUrlStatusCode":200,"ok":true}`

Or failure output in the following form:

`{"brokerClientValidationUrl":"https://acme.com/service/rest/v1/status","brokerClientValidationMethod":"GET","brokerClientValidationTimeoutMs":5000,"ok":false,"error":"ETIMEDOUT"}`
