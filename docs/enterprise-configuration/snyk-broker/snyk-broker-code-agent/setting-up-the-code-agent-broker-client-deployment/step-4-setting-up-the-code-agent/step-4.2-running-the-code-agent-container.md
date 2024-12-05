# 4.2단계: 코드 에이전트 컨테이너 실행

코드 에이전트 이미지가 머신에 저장되면 `docker run` 명령을 사용하여 이미지를 실행하고 이를 기반으로 하는 코드 에이전트 컨테이너를 시작합니다.

{% hint style="info" %}
Environment variables (provided with -e) are case sensitive. Ensure that they are provided as d멘트 변수(-e와 함께 제공됨)는 대소문자를 구분합니다. 이 페이지에 정의된 대로 제공되었는지 확인하세요.
{% endhint %}

## 코드 에이전트 컨테이너 실행

터미널에서 다음 명령을 입력하여 Snyk 코드 에이전트 이미지를 기반으로 컨테이너를 실행합니다:

```
docker run --name <container_name> \
-p <host_machine_port_no._mapped to>:<Code_Agent_container_port_ no.> \
-e PORT=<Code_Agent_container_port_no.> -e SNYK_TOKEN=<Snyk_API_token> --network <network_name> \
snyk/code-agent:<image_tag>
```

어디에:

* `--name <container_name>`은 코드 에이전트 컨테이너의 새 이름입니다. 이 이름은 다음에 실행할 Broker 클라이언트의 `GIT_CLIENT_URL`매개 변수를 정의하는 데 사용됩니다. 예,`code-agent`.
* `-p <host_machine_port_no._mapped to>:<Code_Agent_container_port_no.>`는 호스트 머신의 실제 열린 포트를 코드 에이전트 컨테이너의 포트에 매핑하는 것입니다. 호스트 시스템과 컨테이너의 포트 번호가 동일할 필요는 없습니다. 예시:`3001:3000`.\
  호스트 컴퓨터의 포트 번호는 고유해야 합니다.
* `-e PORT`는 외부 연결을 수락하는 코드 에이전트 컨테이너의 포트입니다. 기본값은 `3000`입니다. 이 포트 번호는 위의 `-p` 매개 변수의 `<Code_Agent_container_port_ no.>` 와 동일해야 합니다.
* `-e SNYK_TOKEN`은 Snyk 웹 UI의 **계정 설정** 페이지에 표시되는 [Snyk API 토큰](../../../../../getting-started/how-to-obtain-and-authenticate-with-your-snyk-api-token.md)입니다.
* `--network`는 이전에 생성한 [Docker 브리지 네트워크](https://docs.snyk.io/features/snyk-broker/snyk-broker-code-agent/setting-up-the-code-agent-broker-client-deployment/step-3-creating-a-network-for-the-broker-client-and-code-agent-communication)의 이름입니다(예:`mySnykBrokerNetwork`).
* `snyk/code-agent:<image_tag>` 는 코드 에이전트 컨테이너의 Docker 이미지입니다. `latest(최신)`을 사용하지 않는 경우 태그를 지정합니다.

코드 에이전트 설정이 성공적으로 완료되면 터미널에 다음 메시지가 나타납니다:

`{ ..., "msg":"Application started", ... }`

<figure><img src="../../../../../.gitbook/assets/Code Agent - Exmaple - success.png" alt="Success message when Code Agent setup is completed"><figcaption><p>Success message when Code Agent setup is completed</p></figcaption></figure>

## 코드 에이전트 컨테이너의 설정 및 세부 정보 확인하기

다음을 실행합니다:

```
docker ps
```

출력은 다음과 비슷합니다:

```
CONTAINER ID   IMAGE            COMMAND                 CREATED      STATUS      PORTS                    NAMES
eebd7d4f0568   snyk/code-agent "docker-entrypoint.s…"   9 days ago   Up 9 days   0.0.0.0:3000->3000/tcp   code-agent
```

## 코드 에이전트 실행 예제

이 예제에서는 터미널에 다음 명령을 입력하여 코드 에이전트 컨테이너를 실행했습니다:

```
docker run --name code-agent \
-p 3000:3000 \
-e PORT=3000 -e SNYK_TOKEN=fa7fxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx --network mySnykBrokerNetwork \
snyk/code-agent
```

어디에:

* `--name` 은 새 코드 에이전트 컨테이너의 이름인 `code-agent`입니다.
* `-p` - 호스트 머신의 port `3000` 이 코드 에이전트 컨테이너의 포트 `3000`에 매핑됩니다.&#x20;
* `-e PORT` 는 외부 연결을 수락하는 코드 에이전트 컨테이너의 포트(`3000`)입니다.
* `-e SNYK_TOKEN`은 Snyk API 토큰`(fa7f…`)입니다.
* `--network` 클라이언트 Broker와의 통신에 사용되는 도커 브리지 네트워크의 이름인 `mySnykBrokerNetwork`입니다.
* `snyk/code-agent`는 코드 에이전트 컨테이너의 Docker 이미지입니다.

## 내부 인증서를 사용하여 Git에 연결하기

기본적으로 코드 에이전트는 Git에 HTTPS 연결을 설정합니다. Git에서 내부 인증서(자체 CA가 서명)를 제공하는 경우, 코드 에이전트에 CA 인증서를 제공할 수 있습니다.

예를 들어, CA 인증서가 `./private/ca.cert.pem`에 있는 경우, 폴더를 마운트하고 `CA_CERT` 환경 변수를 사용하여 Docker 컨테이너에 제공하면 됩니다:

```
docker run --name code-agent \
-p 3000:3000 \
-e PORT=3000 -e SNYK_TOKEN=fa7fxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx --network mySnykBrokerNetwork \
-e CA_CERT=/private/ca.cert.pem \
-v /local/path/to/private:/private \
snyk/code-agent
```
