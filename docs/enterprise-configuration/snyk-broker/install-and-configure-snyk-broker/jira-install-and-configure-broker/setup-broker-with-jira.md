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

**Copy the following command** to set up a fully configured Broker Client to use with Jira. You can run the Docker container by providing the relevant configuration:

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

If necessary, navigate to [Advanced configuration for Snyk Broker Docker installation](../advanced-configuration-for-snyk-broker-docker-installation/) and make any configuration changes needed, for example, providing the CA (Certificate Authority) to the Broker Client configuration when the Jira instance is using a private certificate.

As an alternative to using the Docker run command, you can use a derived Docker image to set up the Broker Client integration. See [Derived Docker images](../derived-docker-images-for-broker-client-integrations-and-container-registry-agent.md) for the environment variables to override for the Jira integration.

## Jira PAT authentication for SSO-enabled JIRA

When SSO is enabled, JIRA usually prohibits the use of a username and password and requires the use of a personal access token (PAT).

When SSO is enabled, you must use a specific Jira version that will instead use the authorization header with the bearer token. To use this version, provide the following configuration:

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

## Start the Broker Client container and verify the connection with Jira

Paste the Broker Client configuration to start the Broker Client container.

After the container is set up, and the Jira Integrations page shows the connection to Jira, under Projects you can create Jira tickets

## **Basic troubleshooting for Broker with Jira**

* Run `docker logs <container id>` to look for any errors, where container id is the Jira Broker container ID.
* Ensure relevant ports are exposed to Jira.
