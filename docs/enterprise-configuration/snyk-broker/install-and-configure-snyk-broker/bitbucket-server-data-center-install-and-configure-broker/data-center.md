# Bitbucket Server/Data Center - Docker를 사용한 설치 및 구성

이 페이지의 지침에 따라 Snyk Broker로 Bitbucket Server/Data Center를 설정하세요. 이 통합은 온프레미스 Bitbucket 배포와의 안전한 연결을 보장하는 데 유용합니다.

{% hint style="info" %}
**전제 조건**\
Snyk 계정 팀에 Broker 토큰을 제공해 달라고 요청하세요..

도커 또는 도커 리눅스 컨테이너를 실행할 수 있는 방법이 필요합니다. 일부 Windows용 Docker 배포는 Windows 컨테이너만 실행합니다. 배포가 Linux 컨테이너를 실행할 수 있는지 확인하세요.
{% endhint %}

## Bitbucket과 함께 사용하도록 Broker 구성하기

{% hint style="warning" %}
**릴리스 상태**

Snyk 코드 PR 확인은 Bitbucket DC/Server 버전 7.0 이상에서만 사용할 수 있습니다.
{% endhint %}

다음은 비트버킷 서버 배포에서 브로커 클라이언트를 사용하도록 Snyk Broker를 구성하는 방법에 대해 설명합니다.

BitBucket과 함께 Snyk Broker 클라이언트를 사용하려면,`docker pull snyk/broker:bitbucket-server`를 **실행**합니다. 환경 변수에 대한 정의는[BitBucket Server/Data Center - Snyk Broker의 환경변수](bitbucket-server-data-center-environment-variables-for-snyk-broker.md)를 참조하세요.

**필요한 경우,** [ 고급 구성 페이지](../advanced-configuration-for-snyk-broker-docker-installation/)로 이동하여 Bitbucket 인스턴스에서 비공개 인증서를 사용하는 경우 브로커 클라이언트 구성에 CA(인증 기관)를 제공하고 [proxy 지원](../advanced-configuration-for-snyk-broker-docker-installation/proxy-support-with-docker.md)을 설정하는 등 필요한 **구성 변경을 수행**합니다.

## 비트버킷용 Broker 클라이언트를 설정하기 위한 Docker 실행 명령

**다음 명령을 복사**하여 완전히 구성된 브로커 클라이언트를 설정하여 오픈 소스, IaC, 컨테이너, 코드 파일(코드 에이전트 포함) 및 Snyk AppRisk 정보를 분석하세요. 애플리케이션 자산을 식별하고, 모니터링하고, 위험의 우선순위를 지정할 수 있도록 [Snyk AppRisk](../../../../manage-risk/snyk-apprisk/)를 활성화합니다.

```bash
docker run --restart=always \
           -p 8000:8000 \
           -e BROKER_TOKEN=<secret-broker-token> \
           -e BITBUCKET_USERNAME=<username> \
           -e BITBUCKET_PASSWORD=<password> \
           -e BITBUCKET=<your.bitbucket-server.domain.com (no http/s)> \
           -e BITBUCKET_API=<your.bitbucket-server.domain.com/rest/api/1.0 (no http/s)> \
           -e PORT=8000 \
           -e BROKER_CLIENT_URL=<http://broker.url.example:8000 (dns/IP:port)> \
           -e ACCEPT_IAC=tf,yaml,yml,json,tpl \
           -e ACCEPT_CODE=true \
           -e ACCEPT_APPRISK=true \
       snyk/broker:bitbucket-server
```

{% hint style="info" %}
Snyk AppRisk는 기본적으로**`false`**로 설정되어 있습니다. 플래그를 **`true`**로 설정하여 사용하도록 설정합니다.
{% endhint %}

Docker 실행 명령을 사용하는 대신 파생된 Docker 이미지를 사용하여 브로커 클라이언트 연동을 설정할 수 있습니다. BitBucket Server/Data Center 연동을 위해 재정의할 환경 변수는 [파생된Docker 이미지](../derived-docker-images-for-broker-client-integrations-and-container-registry-agent.md)를 참조하세요.

## Broker 클라이언트 컨테이너를 시작하고 Bitbucket과의 연결을 확인합니다.

Broker 클라이언트 구성을 붙여넣어 Broker 클라이언트 컨테이너를 시작합니다.

컨테이너가 시작되면 Bitbucket 통합 페이지에 Bitbucket에 대한 연결이 표시되고 프로젝트 추가(`Add Projects`)를 할 수 있습니다.

## BitBucket을 사용한 Broker의 기본 문제 해결

* `docker logs <container id>` 를 실행하여 오류를 찾습니다. 여기서 컨테이너 ID는 Bitbucket 브로커 컨테이너 ID입니다.
* 관련 포트가 Bitbucket에 노출되어 있는지 확인합니다.
