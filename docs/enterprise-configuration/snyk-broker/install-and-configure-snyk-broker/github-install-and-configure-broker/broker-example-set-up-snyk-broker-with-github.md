# GitHub - Docker를 사용한 설치 및 구성

이 페이지의 안내에 따라 Snyk Broker로 GitHub를 설정하세요. 이 통합은 온프레미스 또는 클라우드 GitHub 배포와의 안전한 연결을 보장하는 데 유용합니다.

{% hint style="info" %}
**전제 조건**\
Snyk 계정 팀에 Broker 토큰을 제공하도록 요청하세요.

[필요한 권한](../../../../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/snyk-github-integration.md#required-permissions-scope-for-the-github-integration)이 있는 GitHub 서비스 계정 토큰을 구성해야 합니다. Snyk 웹 UI를 통해 트리거되는 작업과 자동 작업을 포함한 모든 작업은 Broker로 토큰을 구성한 GitHub 서비스 계정에 대해 수행됩니다.

Docker 또는 Docker Linux 컨테이너를 실행할 수 있는 방법이 필요합니다. 일부 Windows용 Docker 배포는 Windows 컨테이너만 실행합니다. 배포가 Linux 컨테이너를 실행할 수 있는지 확인하세요.
{% endhint %}

## Broker와 GitHub 통합 구성하기

Snyk Broker 클라이언트를 GitHub와 함께 사용하려면, `docker pull snyk/broker:github-com`을 **실행**하세요. 환경 변수에 대한 정의는[GitHub - Snyk Broker의 환경변수](github-environment-variables-for-snyk-broker.md)를 참조하세요.

**필요한 경우,** [고급 구성 페이지](../advanced-configuration-for-snyk-broker-docker-installation/)로 이동하여 GitHub 인스턴스가 비공개 인증서를 사용하는 경우 브로커 클라이언트 구성에 CA(인증 기관)를 제공하고 [proxy support](../advanced-configuration-for-snyk-broker-docker-installation/proxy-support-with-docker.md)을 설정하는 등 **필요한 구성 변경**을 수행합니다.

## Docker 실행 명령을 사용하여 GitHub용 Broker 클라이언트 설정하기

**다음 명령을 복사**하여 완전히 구성된 브로커 클라이언트를 설정하여 오픈 소스, IaC, 컨테이너, 코드 파일(코드 에이전트 포함) 및 Snyk AppRisk 정보를 분석하세요. 애플리케이션 자산을 식별하고, 모니터링하고, 위험의 우선순위를 지정할 수 있도록 [Snyk AppRisk](../../../../manage-risk/snyk-apprisk/)를 활성화합니다.

```bash
docker run --restart=always \
           -p 8000:8000 \
           -e BROKER_TOKEN=<secret-broker-token> \
           -e GITHUB_TOKEN=<secret-github-token> \
           -e PORT=8000 \
           -e BROKER_CLIENT_URL=<http://broker.url.example:8000 (dns/IP:port)> \
           -e ACCEPT_IAC=tf,yaml,yml,json,tpl \
           -e ACCEPT_CODE=true \
           -e ACCEPT_APPRISK=true \ 
       snyk/broker:github-com
```

{% hint style="info" %}
Snyk AppRisk는 기본적으로 **`false`**로 설정되어 있습니다. 플래그를 **`true`**로 설정하여 사용하도록 설정합니다.
{% endhint %}

Docker 실행 명령 대신 파생된 Docker 이미지를 사용하여 Broker 클라이언트 연동을 설정할 수 있습니다. GitHub 연동을 위해 재정의할 환경 변수는 [파생된 Docker 이미지](../derived-docker-images-for-broker-client-integrations-and-container-registry-agent.md)를 참조하세요.

## 브로커 클라이언트 컨테이너를 시작하고 GitHub와의 연결을 확인합니다.

Broker 클라이언트 구성을 붙여넣어 Broker 클라이언트 컨테이너를 시작합니다.

컨테이너가 시작되면 GitHub 통합 페이지에 GitHub 연결이 표시되고 프로젝트를 추가(`Add Projects`) 할 수 있습니다. .

## GitHub를 사용한 Broker의 기본 문제 해결

### GitHub용 대용량 매니페스트 파일(> 1Mb) 지원

오픈 수정/업그레이드 PR 또는 PR/반복 테스트가 실패하는 이유 중 하나는 대용량 매니페스트 파일(> 1Mb)을 가져오는 것일 수 있습니다. 이 문제를 해결하려면,[대용량 매니페스트 파일의 Snyk 오픈  소스 스캔(SCA)](https://docs.snyk.io/enterprise-setup/snyk-broker/install-and-configure-snyk-broker/advanced-configuration-for-snyk-broker-docker-installation/snyk-open-source-scans-sca-of-large-manifest-files-docker-setup)에 대한 추가 지침에 따라 Broker에서 추가 변수를 활성화하세요(Docker 설정).

{% hint style="info" %}
이 엔드포인트를 사용하면 경로에 허용된 특정 파일 이름이 포함되어 있지 않기 때문에 이론적으로 이 리포지토리에 있는 모든 파일에 액세스할 수 있으므로 최대한의 보안을 보장하기 위해 Snyk는 이 규칙을 기본적으로 활성화하지 않습니다.
{% endhint %}

### GitHub를 사용한 Broker의 추가 문제 해결

* `docker logs <container id>`를 실행하여 오류를 찾습니다. 여기서 `container id` 는 GitHub Broker 컨테이너 아이디입니다.
* 관련 포트가 GitHub에 노출되어 있는지 확인합니다.
