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

## **Container Registry and Broker Client with an internal certificate**

By default, the Container Registry Agent establishes HTTPS connections to the Container Registry and Broker Client. If your Container Registry or Broker Client is serving an internal certificate (signed by your own CA), you can provide the CA certificate to the Container Registry Agent. For example, if your CA certificate is at `./private/ca.cert.pem`, provide it to the Docker container by mounting the folder and using the `NODE_EXTRA_CA_CERTS` environment variable:

```
docker run --restart=always
-p 8081:8081
-e SNYK_PORT=8081
-e NODE_EXTRA_CA_CERTS=/private/ca.cert.pem
snyk/container-registry-agent:latest
```
