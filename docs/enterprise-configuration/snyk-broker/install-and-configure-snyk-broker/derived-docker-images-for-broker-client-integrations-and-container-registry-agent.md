# Broker 클라이언트 통합 및 컨테이너 레지스트리 에이전트를 위한 파생된 Docker 이미지

{% hint style="info" %}
이 페이지의 정보를 사용하여 Broker 클라이언트 연동을 설정할 필요는 없습니다. 파생된 Docker 이미지를 사용하여 Broker 클라이언트 연동을 설정할 수 있습니다. 이는 각 연동 서비스 설정 지침에 설명된 명령을 실행하는 대신 사용할 수 있습니다.
{% endhint %}

## Azure Repos Broker 통합 설정을 위한 파생된 Docker 이미지

[설정 페이지](azure-repos-install-and-configure-broker/setup-broker-with-azure-repos.md)에 표시된 Docker 실행 명령을 사용하는 대신 자체 Docker 이미지를 빌드하고 관련 환경 변수를 재정의할 수 있습니다:

```dockerfile
FROM snyk/broker:azure-repos

ENV BROKER_TOKEN        secret-broker-token
ENV AZURE_REPOS_TOKEN   secret-azure-token
ENV AZURE_REPOS_ORG     org-name
ENV AZURE_REPOS_HOST    your.azure-server.domain.com
ENV BROKER_CLIENT_URL   http://my.broker.client:8000
ENV PORT                8000
```

## Bitbucket Server/데이터 센터 Broker 통합 설정을 위한 파생된 Docker 이미지

[설정 페이지](bitbucket-server-data-center-install-and-configure-broker/data-center.md)에 표시된 Docker 실행 명령을 사용하는 대신 자체 Docker 이미지를 빌드하고 관련 환경 변수를 재정의할 수 있습니다:

```dockerfile
FROM snyk/broker:bitbucket-server

ENV BROKER_TOKEN        secret-broker-token
ENV BITBUCKET_USERNAME  username
ENV BITBUCKET_PASSWORD  password
ENV BITBUCKET           your.bitbucket-server.domain.com
ENV BITBUCKET_API       your.bitbucket-server.domain.com/rest/api/1.0
ENV PORT                8000
```

## GitHub Broker 통합 설정을 위한 파생된 Docker 이미지

[설정 페이지](github-install-and-configure-broker/broker-example-set-up-snyk-broker-with-github.md)에 표시된 Docker 실행 명령을 사용하는 대신 자체 Docker 이미지를 빌드하고 관련 환경 변수를 재정의할 수 있습니다:

```dockerfile
FROM snyk/broker:github-com

ENV BROKER_TOKEN      secret-broker-token
ENV GITHUB_TOKEN      secret-github-token
ENV PORT              8000
ENV BROKER_CLIENT_URL http://my.broker.client:8000
```

## GitHub Enterprise Broker 통합 설정을 위한 파생된 Docker 이미지

[설정 페이지](github-enterprise-install-and-configure-broker/setup-broker-with-github-enterprise.md)에 표시된 Docker 실행 명령을 사용하는 대신 직접 Docker 이미지를 빌드하고 관련 환경 변수를 재정의할 수 있습니다:

```dockerfile
FROM snyk/broker:github-enterprise

ENV BROKER_TOKEN      secret-broker-token
ENV GITHUB_TOKEN      secret-github-token
ENV GITHUB            your.ghe.domain.com
ENV GITHUB_API        your.ghe.domain.com/api/v3
ENV GITHUB_GRAPHQL    your.ghe.domain.com/api
ENV PORT              8000
ENV BROKER_CLIENT_URL http://my.broker.client:8000
```

## GitLab Broker 통합 설정을 위한 파생된 Docker 이미지

[설정 페이지](gitlab-install-and-configure-broker/setup-broker-with-gitlab.md)에 표시된 Docker 실행 명령을 사용하는 대신 자체 Docker 이미지를 빌드하고 관련 환경 변수를 재정의할 수 있습니다:

```dockerfile
FROM snyk/broker:gitlab

ENV BROKER_TOKEN        secret-broker-token
ENV GITLAB_TOKEN        secret-gitlab-token
ENV GITLAB              your.gitlab.domain.com
ENV BROKER_CLIENT_URL   http://my.broker.client:8000
ENV PORT                8000
```

## Jira Broker 통합 설정을 위한 파생된 Docker 이미지

[설정 페이지](jira-install-and-configure-broker/setup-broker-with-jira.md)에 표시된 Docker 실행 명령을 사용하는 대신 자체 Docker 이미지를 빌드하고 관련 환경 변수를 재정의할 수 있습니다:

```dockerfile
FROM snyk/broker:jira

ENV BROKER_TOKEN        secret-broker-token
ENV JIRA_USERNAME       username
ENV JIRA_PASSWORD       password
ENV JIRA_HOSTNAME       your.jira.domain.com
ENV PORT                8000
```

## Artifactory Broker 연동 설정을 위해 파생된 Docker 이미지

[설정 페이지](artifactory-repository-install-and-configure-broker/set-up-snyk-broker-with-artifactory-repository.md)에 표시된 Docker 실행 명령을 사용하는 대신 자체 Docker 이미지를 빌드하고 관련 환경 변수를 재정의할 수 있습니다:

```dockerfile
FROM snyk/broker:artifactory

ENV BROKER_TOKEN      secret-broker-token
ENV ARTIFACTORY_URL   <yourdomain>.artifactory.com
```

## Nexus 3 Broker 통합 설정을 위한 파생된 Docker 이미지

[설정 페이지](nexus-repository-install-and-configure-broker/set-up-snyk-broker-with-nexus-repository-manager.md)에 표시된 Docker 실행 명령을 사용하는 대신 자체 Docker 이미지를 빌드하고 관련 환경 변수를 재정의할 수 있습니다:

```dockerfile
FROM snyk/broker:nexus

ENV BROKER_TOKEN                     secret-broker-token
ENV BASE_NEXUS_URL                   https://[<user>:<pass>@]<your.nexus.hostname>
ENV BROKER_CLIENT_VALIDATION_URL     https://<your.nexus.hostname>/service/rest/v1/status[/check]
ENV RES_BODY_URL_SUB                 https://<your.nexus.hostname>/repository

```

{% hint style="info" %}
Nexus 3의 경우 기본적으로 Broker 클라이언트에 의해 X-Forwarded-For 헤더가 제거되므로 Nexus는 Broker 서버가 아닌 Nexus 레지스트리에 npm tarball uri를 반환합니다. 이 동작을 비활성화하려면 환경 변수 `REMOVE_X_FORWARDED_HEADERS=false` to disable 를 포함하세요.
{% endhint %}

## Nexus 2 Broker 통합 설정을 위한 파생된 Docker 이미지

[설정 페이지](nexus-repository-install-and-configure-broker/set-up-snyk-broker-with-nexus-repository-manager.md)에 표시된 Docker 실행 명령을 사용하는 대신 자체 Docker 이미지를 빌드하고 관련 환경 변수를 재정의할 수 있습니다:

```dockerfile
FROM snyk/broker:nexus2

ENV BROKER_TOKEN                     secret-broker-token
ENV BASE_NEXUS_URL                   https://[<user>:<pass>@]<your.nexus.hostname>
ENV BROKER_CLIENT_VALIDATION_URL     https://<your.nexus.hostname>:<port>/systemcheck 
ENV RES_BODY_URL_SUB                 https://<your.nexus.hostname>/nexus/content/(groups|repositories)
```

{% hint style="info" %}
Nexus 2의 경우 기본적으로 Broker 클라이언트에 의해 X-Forwarded-For 헤더가 제거되므로 Nexus는 Broker 서버가 아닌 Nexus 레지스트리에 npm tarball uri를 반환합니다. 이 동작을 비활성화하려면 환경 변수 REMOVE\_X\_FORWARDED\_HEADERS=false를 포함하세요.
{% endhint %}

## 컨테이너 레지스트리 에이전트 설정을 위한 파생된 Docker 이미지

[설정 페이지](../snyk-broker-container-registry-agent/)에 표시된 Docker 실행 명령을 사용하는 대신 자체 Docker 이미지를 빌드하고 관련 환경 변수를 재정의할 수 있습니다:

```dockerfile
FROM snyk/broker:container-registry-agent

ENV BROKER_TOKEN          secret-broker-token
ENV BROKER_CLIENT_URL     https://my.broker.client:8000
ENV CR_AGENT_URL          https://my.container.registry.agent
ENV CR_TYPE               container-registry-type
ENV CR_BASE               your.container.registry.domain.com
ENV CR_USERNAME           secret-container-registry-username
ENV CR_PASSWORD           secret-container-registry-password
ENV PORT                  8000
```
