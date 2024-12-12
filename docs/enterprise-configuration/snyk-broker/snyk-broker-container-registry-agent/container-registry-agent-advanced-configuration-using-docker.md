# Docker를 사용한 컨테이너 레지스트리 에이전트 고급 구성

Docker를 사용한 Broker 컨테이너 레지스트리 에이전트 설치에 대한 지침은 [Snyk Broker - 컨테이너 레지스트리 에이전트](./) 를참조하세요. 헬름 방법에 대한 지침은 [Helm을 사용하여 컨테이너 레지스트리용 Broker 설치하기](install-broker-for-container-registry-agent-using-helm.md)를 참조하세요.

## 컨테이너 레지스트리 에이전트 서버 HTTPS 구성

CRA(컨테이너 레지스트리 에이전트)는 기본적으로 HTTP 서버를 실행합니다. 로컬 연결을 위해 HTTPS 서버를 실행하도록 CRA를 구성할 수 있습니다. 이를 위해서는 런타임에 Docker 컨테이너에 SSL 인증서와 개인 키를 제공해야 합니다.

예를 들어 인증서 파일이 로컬에 `./private/container-registry-agent.crt` 및`./private/container-registry-agent.key`에 있는 경우, 폴더를 마운트하고 `HTTPS_CERT` 및`HTTPS_KEY`환경 변수를 사용하여 이 파일을 Docker 컨테이너에 제공하세요:

```
docker run --restart=always \
       -p 8081:8081 \
       -e SNYK_PORT=8081 \
       -e HTTPS_CERT=/private/container-registry-agent.crt \
       -e HTTPS_KEY=/private/container-registry-agent.key \
       snyk/container-registry-agent:latest
```

## 내부 인증서가 있는 컨테이너 레지스트리 및 Broker 클라이언트

기본적으로 컨테이너 레지스트리 에이전트는 컨테이너 레지스트리 및 Broker 클라이언트에 대한 HTTPS 연결을 설정합니다. 컨테이너 레지스트리 또는 Broker 클라이언트가 내부 인증서(자체 CA가 서명)를 제공하는 경우, 컨테이너 레지스트리 에이전트에 CA 인증서를 제공할 수 있습니다. 예를 들어, CA 인증서가`./private/ca.cert.pem`에 있는 경우, 폴더를 마운트하고 `NODE_EXTRA_CA_CERTS` 환경 변수를 사용하여 Docker 컨테이너에 제공하세요:

```
docker run --restart=always
-p 8081:8081
-e SNYK_PORT=8081
-e NODE_EXTRA_CA_CERTS=/private/ca.cert.pem
snyk/container-registry-agent:latest
```
