# Derived Docker images for Broker Client integrations and Container Registry Agent

{% hint style="info" %}
Using the information on this page is not required to set up Broker Client integrations. You may use a derived Docker image to set up a Broker Client integration. This is an alternative to running the command explained in the instructions for setting up each integration.
{% endhint %}

## Derived Docker image for Azure Repos Broker integration setup

As an alternative to using the Docker run command shown on the [setup page](../../../user-and-group-management/snyk-broker/snyk-broker-set-up-examples/setup-broker-with-azure-repos.md), you can build your own Docker image and override relevant environment variables:

```dockerfile
FROM snyk/broker:azure-repos

ENV BROKER_TOKEN        secret-broker-token
ENV AZURE_REPOS_TOKEN   secret-azure-token
ENV AZURE_REPOS_ORG     org-name
ENV AZURE_REPOS_HOST    your.azure-server.domain.com
ENV BROKER_CLIENT_URL   http://my.broker.client:8000
ENV PORT                8000
```

## Derived Docker image for Bitbucket Server/Data Center Broker integration setup

As an alternative to using the Docker run command shown on the [setup page](../../../user-and-group-management/snyk-broker/snyk-broker-set-up-examples/data-center.md), you can build your own Docker image and override relevant environment variables:

```dockerfile
FROM snyk/broker:bitbucket-server

ENV BROKER_TOKEN        secret-broker-token
ENV BITBUCKET_USERNAME  username
ENV BITBUCKET_PASSWORD  password
ENV BITBUCKET           your.bitbucket-server.domain.com
ENV BITBUCKET_API       your.bitbucket-server.domain.com/rest/api/1.0
ENV PORT                8000
```

## Derived Docker image for GitHub Broker integration setup

As an alternative to using the Docker run command shown on the [setup page](../../../user-and-group-management/snyk-broker/snyk-broker-set-up-examples/broker-example-set-up-snyk-broker-with-github.md), you can build your own Docker image and override relevant environment variables:

```dockerfile
FROM snyk/broker:github-com

ENV BROKER_TOKEN      secret-broker-token
ENV GITHUB_TOKEN      secret-github-token
ENV PORT              8000
ENV BROKER_CLIENT_URL http://my.broker.client:8000
```

## Derived Docker image for GitHub Enterprise Broker integration setup

As an alternative to using the Docker run command shown on the [setup page](../../../user-and-group-management/snyk-broker/snyk-broker-set-up-examples/setup-broker-with-github-enterprise.md), you can build you own Docker image and override relevant environment variables:

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

## Derived Docker image for GitLab Broker integration setup

As an alternative to using the Docker run command shown on the [setup page](../../../user-and-group-management/snyk-broker/snyk-broker-set-up-examples/setup-broker-with-gitlab.md), you can build your own Docker image and override relevant environment variables:

```dockerfile
FROM snyk/broker:gitlab

ENV BROKER_TOKEN        secret-broker-token
ENV GITLAB_TOKEN        secret-gitlab-token
ENV GITLAB              your.gitlab.domain.com
ENV BROKER_CLIENT_URL   http://my.broker.client:8000
ENV PORT                8000
```

## Derived Docker image for Jira Broker integration setup

As an alternative to using the Docker run command shown on the [setup page](../../../integrations/snyk-broker/snyk-broker-set-up-examples/setup-broker-with-jira.md), you can build your own Docker image and override relevant environment variables:

```dockerfile
FROM snyk/broker:jira

ENV BROKER_TOKEN        secret-broker-token
ENV JIRA_USERNAME       username
ENV JIRA_PASSWORD       password
ENV JIRA_HOSTNAME       your.jira.domain.com
ENV PORT                8000
```

## Derived Docker image for Artifactory Broker integration setup

As an alternative to using the Docker run command shown on the [setup page](set-up-snyk-broker-with-artifactory.md), you can build your own Docker image and override relevant environment variables:

```dockerfile
FROM snyk/broker:artifactory

ENV BROKER_TOKEN      secret-broker-token
ENV ARTIFACTORY_URL   <yourdomain>.artifactory.com
```

## Derived Docker image for Nexus 3 Broker integration setup

As an alternative to using the Docker run command shown on the [setup page](set-up-snyk-broker-with-nexus3.md), you can build your own Docker image and override relevant environment variables:

```dockerfile
FROM snyk/broker:nexus

ENV BROKER_TOKEN                     secret-broker-token
ENV BASE_NEXUS_URL                   https://[<user>:<pass>@]<your.nexus.hostname>
ENV BROKER_CLIENT_VALIDATION_URL     https://<your.nexus.hostname>/service/rest/v1/status[/check]
ENV RES_BODY_URL_SUB                 https://<your.nexus.hostname>/repository

```

{% hint style="info" %}
By default for Nexus 3, the X-Forwarded-For headers are stripped off by the broker client so Nexus returns the npm tarball uri to the Nexus registry instead of the broker server. Include the environment variable `REMOVE_X_FORWARDED_HEADERS=false` to disable this behavior.
{% endhint %}

## Derived Docker image for Container Registry Agent Setup

As an alternative to using the Docker run command shown on the [setup page](../../../user-and-group-management/snyk-broker/snyk-broker-container-registry-agent/), you can build your own Docker image and override relevant environment variables:

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