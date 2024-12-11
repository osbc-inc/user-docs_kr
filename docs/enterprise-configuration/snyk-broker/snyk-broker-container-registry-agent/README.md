# Snyk Broker - 컨테이너 레지스트리 에이전트

{% hint style="info" %}
**기능 가용성**

Snyk Broker 컨테이너 레지스트리 에이전트는 Enterprise 요금제에서만 사용할 수 있습니다.

자세한 내용은,  [요금제 및 가격 책정](https://snyk.io/plans)을 참조하세요.
{% endhint %}

Snyk Broker 컨테이너 레지스트리 에이전트를 사용하면 네트워크가 제한된 컨테이너 레지스트리와 연결을 설정하여 Snyk 서비스를 사용하여 이러한 레지스트리를 스캔할 수 있습니다.

컨테이너 레지스트리 에이전트를 사용하면 Snyk는 사용자가 호스팅하는 비공개 컨테이너 레지스트리와 통합하여 해당 레지스트리에서 컨테이너 이미지를 더 안전하게 보호할 수 있습니다. 프라이빗 컨테이너 레지스트리와의 통합을 통해 다음을 수행할 수 있습니다:

* 액세스 토큰과 같은 민감한 데이터는 비공개 네트워크 내에 보관하고 해당 정보를 Snyk와 공유하지 마세요.
* Snyk에게 네트워크에 대한 제어된 액세스를 제공하여 Snyk의 액세스 및 Snyk이 수행할 수 있는 작업을 제한합니다.

이 페이지에서는 컨테이너 레지스트리 에이전트를 사용하여 Broker를 통해 이 페이지에 [나열된](./#supported-container-registries) 대로 지원되는 오픈 소스 컨테이너 레지스트리와 통합하는 방법을 설명합니다. 이 통합 방법은 Snyk 서비스 내부가 아닌 자체 환경에서 이미지를 스캔해야 하는 사용자를 위해 고안되었습니다.

**자체 환경에서 이미지를 스캔할 필요가 없는 경우**에는 컨테이너 레지스트리 에이전트를 사용할 필요가 없습니다. **계정의 연동 페이지에서 지원되는 컨테이너 레지스트리와 연동**할 수 있습니다. 자세한 내용은 [Snyk 컨테이너 - 통합](../../../integrate-with-snyk/snyk-container-integrations/)을 참조하세요.

## 네트워크 제한 컨테이너 레지스트리 솔루션의 구성 요소

네트워크 제한 컨테이너 레지스트리에는 다음 구성 요소가 필요합니다:

* Broker 서버: Snyk SaaS 백엔드에서 실행됩니다.
* Broker 클라이언트 및 컨테이너 레지스트리 에이전트: 인프라에 배포된 두 개의 Docker 이미지로, 컨테이너 레지스트리를 안전한 방식으로 샘플링하고 허용된 정보를 Snyk에 전송하는 두 개의 별도 서비스를 생성합니다.

Broker 클라이언트는 컨테이너 레지스트리 에이전트에 연결 세부 정보를 제공합니다. 에이전트는 이러한 세부 정보를 사용하여 컨테이너 레지스트리에 연결하고, 이미지를 스캔하고, 콜백을 사용하여 중개 통신을 통해 스캔 결과를 전송합니다. Broker 통신은 브로커 클라이언트가 Broker ID를 사용하여 Snyk 환경에서 실행되는 Broker 서버에 연결할 때 발생합니다. 자세한 내용은 [Snyk Broker](../) 소개 정보를 참조하세요.

<figure><img src="../../../.gitbook/assets/mceclip0-8-.png" alt="Highlevel architecture of the Snyk Broker Container Registry Agent"><figcaption><p>Snyk Broker 컨테이너 레지스트리 에이전트의 하이레벨 아키텍처</p></figcaption></figure>

## 지원되는 컨테이너 레지스트리

Snyk Broker 컨테이너 레지스트리 에이전트를 사용하면 Snyk을 다음 오픈소스 컨테이너 레지스트리와 통합할 수 있습니다:

* JFrog Container Registry (Artifactory) (유형: artifactory-cr)
* Harbor registry (유형: harbor-cr)
* Azure Container Registry (유형: acr)
* Google Cloud Container Registry (GCR) (유형: gcr)
* Amazon Elastic Container Registry (ECR) (유형: ecr)
* Google Artifact Registry (유형: google-artifact-cr)
* Docker Hub registry (유형: docker-hub). 참고: Snyk Broker는 OCI 배포의 자체 호스팅 인스턴스, 즉[`docker.io/registry`](http://docker.io/registry)에 연결할 수 없습니다.
* RedHat Quay container registry (유형: quay-cr)
* Nexus registry (유형: nexus-cr)
* GitHub Container registry (유형: github-cr)
* DigitalOcean Container Registry (유형: digitalocean-cr)
* GitLab Container Registry (유형: gitlab-cr)

아티팩토리와 넥서스는 Broker 옵션이 있는 프라이빗 패키지 리포지토리로도 사용할 수 있습니다. 컨테이너 레지스트리에 필요한 Broker는 [Container Registry Agent의 전제 조건](./#prerequisites-for-container-registry-agent)에 지정된 Broker여야 하며, snyk/Broker:아티팩토리 또는 snyk/Broker:넥서스용 Broker가 아니어야 합니다.

GitHub 컨테이너 레지스트리와 GitLab 컨테이너 레지스트리는 /v2/\_catalog 엔드포인트가 없는 Docker v2 API를 따르지 않습니다. 따라서 리포지토리에 이미지를 나열할 수 없으며 스캔하려는 이미지를 수동으로 지정해야 합니다.

## 컨테이너 레지스트리 에이전트의 전제 조건

Snyk Broker 와 컨테이너 레지스트리 에이전트를 설정하려면 Broker 토큰이 있어야 합니다. Broker 토큰을 받으려면 [Snyk 지원팀](https://support.snyk.io/hc/en-us)에 문의하세요.

{% hint style="warning" %}
F컨테이너 레지스트리 에이전트가 작동하려면 인프라에 두 개의 별도 컨테이너를 배포하여 두 개의 별도 서비스를 만들어야 합니다. 자세한 내용은 이 페이지의 [네트워크 제한 컨테이너 레지스트리 솔루션의 구성요소](./#components-of-the-network-restricted-container-registries-solution)를 참조하세요.
{% endhint %}

Snyk Broker 컨테이너 레지스트리 에이전트를 설정하고 실행하기 위한 시스템 및 소프트웨어 요구 사항은 다음과 같습니다;

* Broker 클라이언트 컴퓨터 시스템 요구 사항: CPU 1개, RAM 256MB
* 컨테이너 레지스트리 에이전트 머신 시스템 요구 사항은 다음과 같아야 합니다(MAX\_ACTIVE\_OPERATIONS=1): CPU: 1 vcpu
  * CPU: 1 vcpu
  * Memory: 2Gb (노드 메모리 설정에 반영되어야 함)
  * Storage: 5Gb
* 이미지 목록 및 풀 권한이 있는 컨테이너 레지스트리 자격 증명
* Broker와 에이전트 간 연결
* 에이전트와 레지스트리 간의 HTTPS 연결. HTTP 전용 레지스트리의 경우, 에이전트와 컨테이너 레지스트리 사이에 리버스 프록시를 배포하세요.
* [Docker에서 Broker 클라이언트 이미지 다운로드](https://hub.docker.com/r/snyk/broker/tags?page=1\&ordering=last_updated\&name=container-registry-agent): snyk/broker:container-registry-agent(Docker를 사용하는 경우)
* [Docker에서 컨테이너 레지스트리 에이전트 이미지 다운로드](https://hub.docker.com/r/snyk/container-registry-agent/tags?page=1\&ordering=last_updated) : snyk/container-registry-agent:최신(Docker를 사용하는 경우)

{% hint style="info" %}
**스캔 용량 조정을 위한 스케일링**

나열된 구성의 vCPU 1개와 2GB RAM을 사용하면 스캔 용량은 한 번에 약 350MB씩 약 160개의 이미지를 스캔할 수 있습니다. 이미지 크기에 따라 이 용량을 확장할 수 있습니다. 확장을 허용하지 않고 제한에 맞지 않는 특정 사용 사례가 있는 경우 [Snyk 지원팀](https://support.snyk.io/hc/en-us/)에 문의하세요.
{% endhint %}

## **Docker**를 사용하여 컨테이너 레지스트리 에이전트에 대한 원격 연결 설정하기

### 컨테이너 레지스트리 에이전트용 Broker 클라이언트 구성 및 실행

컨테이너 레지스트리 에이전트 배포와 함께 Broker 클라이언트를 사용하려면, [전제 조건](./#prerequisites-for-container-registry-agent)으로 아직 실행하지 않은 경우 `docker pull snyk/broker:container-registry-agent` docker pull snyk/broker:container-registry-agent를 실행하세요.

Broker 클라이언트를 구성하려면 다음 환경 변수가 필요합니다.

{% hint style="info" %}
**컨테이너 레지스트리, Google 아티팩트 레지스트리** 및 **아티팩토리**에는 몇 가지 주의해야 할 값이 있습니다. [컨테이너 레지스트리별 구성](./#container-registry-specific-configurations)을 참조하세요. **Elastic 컨테이너 레지스트리**의 경우, 추가 설정이 필요합니다. [구체적인 구성](./#container-registry-specific-configurations)도 제공됩니다.
{% endhint %}

* `BROKER_TOKEN` - Snyk 지원팀에서 제공하는 컨테이너 레지스트리 통합에서 얻은 Snyk Broker 토큰입니다.
* `BROKER_CLIENT_URL` - 컨테이너 레지스트리 에이전트가 브로커링된 연결을 통해 Snyk에 다시 호출하는 데 사용하는 스키마 및 포트를 포함한 Broker 클라이언트의 URL(예: Broker 클라이언트)입니다: "[http://my.broker.client:8000](http://my.broker.client:8000)".
  * http:// 및 포트 번호가 있어야 합니다.
  * HTTPS로 클라이언트를 구성하려면, [추가 설정이 필요합니다.](https://docs.snyk.io/snyk-admin/snyk-broker/install-and-configure-broker-using-docker/advanced-configuration-for-snyk-broker-docker-installation/https-for-broker-client-with-docker)
* `CR_AGENT_URL` - Broker 클라이언트가 요청을 라우팅할 컨테이너 레지스트리 에이전트의 URL(예: 스키마 및 포트 포함)입니다: "[http://my.container-registry-agent](http://my.container-registry-agent)".
* `CR_TYPE` - 이 페이지의 [지원되는 컨테이너 레지스트리](./#supported-container-registries)에 나열된 컨테이너 레지스트리 유형입니다(예: “docker-hub”, “gcr”, “artifactory-cr”).
* `CR_BASE` - 연결할 컨테이너 레지스트리 API의 호스트 이름(예: “cr.host.com”.
* `CR_USERNAME` - 컨테이너 레지스트리 API에 인증하기 위한 사용자 이름입니다.
* `CR_PASSWORD` - 컨테이너 레지스트리 API에 인증하기 위한 비밀번호입니다.
* `CR_TOKEN` -디지털오션 컨테이너 레지스트리를 위한 인증 토큰입니다.
* `PORT` - Broker 클라이언트가 연결을 수락하는 로컬 포트입니다(기본값: 7341).
* 선택 사항 - `BROKER_CLIENT_VALIDATION_URL` - 컨테이너 레지스트리 에이전트에 대해 /systemcheck를 구성할 URL입니다. 자세한 내용은 이 페이지의 [시스템 검사 구성 및 사용](./#configuring-and-using-systemcheck) 참조하세요.

관련 구성으로 Broker 클라이언트 컨테이너를 실행합니다:

```
docker run --restart=always \
       -p 8000:8000 \
       -e BROKER_TOKEN="<secret-broker-token>" \
       -e BROKER_CLIENT_URL="<broker-client-url>" \
       -e CR_AGENT_URL="<container-registry-agent-url>" \
       -e CR_TYPE="<container-registry-type>" \
       -e CR_BASE="<container-registry-hostname>" \
       -e CR_USERNAME="<username>" \
       -e CR_PASSWORD="<password>" \
       -e PORT=8000 \
       snyk/broker:container-registry-agent
```

이 명령의 대안으로 파생된 Docker 이미지를 사용하여 컨테이너 레지스트리 에이전트를 설정할 수 있습니다. 컨테이너 레지스트리 에이전트에 대해 재정의할 환경 변수는 [파생된 Docker 이미지](../install-and-configure-snyk-broker/derived-docker-images-for-broker-client-integrations-and-container-registry-agent.md)를 참조하세요.

### Configuring and running **the Container Registry Agent**

You can pull the Container Registry Agent image from Docker Hub using the link provided in the [prerequisites](./#prerequisites-for-container-registry-agent).

To configure the Container Registry Agent, the following environment variables are required:

* `SNYK_PORT` - the local port at which the Container Registry Agent accepts connections (default value: 17500).
* `SNYK_MAX_IMAGE_SIZE_IN_BYTES` - the maximum size of an image that Snyk is able to scan (default value: 2147483648).

Run the Container Registry Agent container with the relevant configuration:

```
docker run --restart=always \
       -p 8081:8081 \
       -e SNYK_PORT=8081 \
       snyk/container-registry-agent:latest
```

## **Container registry-specific configurations**

The following container registries require specific environment variables, setup, or both.

### **DigitalOcean Container Registry**

`CR_USERNAME` and `CR_PASSWORD` are not required to set up Broker Client for DigitalOcean Container Registry. Instead, specify `CR_TOKEN`, the Digital Ocean authentication token.

### **GCR and Google Artifact Registry**

All the preceding information applies to setting up the Broker Client for these container registries. Note that the `CR_USERNAME` value is permanent and should be `_json_key`, and the `CR_PASSWORD` value should be the JSON key used to authenticate to Google.

### **JFrog Container Registry (Artifactory)**

If you are using **Repository path** as your Docker access method, set the container registry hostname in the `CR_BASE` variable in this structure: `<your artifactory host>/artifactory/api/docker/<artifactory-repo-name>`

Note that the catalog endpoint `/artifactory/api/docker/<artifactory-repository>/v2/_catalog` is not required for importing a project in Artifactory; this is used for listing the image repositories.

See [Configuring your JFrog Artifactory container registry integration](../../../integrate-with-snyk/snyk-container-integrations/container-security-with-jfrog-artifactory-integration/configuring-your-jfrog-artifactory-container-registry-integration.md) for more details.

### **Elastic Container Registry (ECR)**

In Elastic Container Registries and other container registries the communication is the same. The Agent makes synchronous calls to the container registries to list and pull the image. Then the Agent scans the images and sends the results to the Broker Client using callbacks. ECR has a special authentication mechanism that requires setting up an IAM Role or User in the Agent.

<figure><img src="../../../.gitbook/assets/image (20) (3).png" alt="High-level architecture of the brokered ECR integration"><figcaption><p>High-level architecture of the brokered ECR integration</p></figcaption></figure>

#### **Required AWS Resource with ECR**

ECR setup requires that the following kinds of IAM resources be created:

* Container Registry Agent IAM Role or IAM User: an IAM Role or IAM User the Agent uses to assume a cross-account role with access to ECR. It should have the following permissions: "`sts:AssumeRole"`.
*   Snyk ECR Service Role: an IAM Role with access to ECR which is assumed by the Container Registry Agent IAM Role or IAM User to gain read-only access to ECR.\
    The ECR Service Role should have the following permissions:

    ```
    [
      "ecr:GetLifecyclePolicyPreview",
      "ecr:GetDownloadUrlForLayer",
      "ecr:BatchGetImage",
      "ecr:DescribeImages",
      "ecr:GetAuthorizationToken",
      "ecr:DescribeRepositories",
      "ecr:ListTagsForResource",
      "ecr:ListImages",
      "ecr:BatchCheckLayerAvailability",
      "ecr:GetRepositoryPolicy",
      "ecr:GetLifecyclePolicy"
    ]
    ```

#### **Setup steps for ECR**

The resources described can be used as follows so that a single Container Registry Agent instance can access ECR repositories located in different accounts.

**Run this step once only.** Create the Container Registry Agent IAM Role or IAM User and use it to run the Container Registry Agent. The IAM Role or IAM User could be provided to the Container Registry Agent using one of the methods described in the [AWS docs](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-credentials-node.html).

**Run the following steps for each of your ECR accounts, using a separate Broker instance for each ECR account:**

1. In the AWS account where your ECR resides, create the Snyk ECR Service Role with read access to your ECR, and edit the trust relationship to allow this role to be assumed only by the specific Container Registry Agent IAM Role or IAM User created in the one-time step.
2. Restrict the Container Registry Agent IAM Role or IAM User to be allowed to assume only the Snyk ECR Service Role(s).
3. Provide the Broker Client with the Role ARN (Amazon Service Name) of the Snyk ECR Service Role together with the ECR region. The Broker Client passes this Role ARN to the Container Registry Agent, and the Container Registry Agent assumes it to access your ECR. The following environment variables are required:
   * CR\_ROLE\_ARN=\<the role ARN of SnykEcrServiceRole>
   * CR\_REGION=\<AWS Region of ECR>
   * CR\_EXTERNAL\_ID=\<Optional. An external ID found in the trust relationship condition>

## **Configuring and using systemcheck**

You can use the `/systemcheck` endpoint of the Broker Client to verify connectivity between the Broker Client, the Container Registry Agent, and your container registry.

To use the endpoint, provide the following environment variable to the Broker Client:\
`BROKER_CLIENT_VALIDATION_URL=<agent-url>/systemcheck`

When you call the `/systemcheck` endpoint of the Broker Client, it uses the `BROKER_CLIENT_VALIDATION_URL` to make a request to the `/systemcheck` endpoint Container Registry Agent, with the credentials provided to the Broker Client. The Container Registry Agent then makes a request to the container registry to validate connectivity.

{% hint style="info" %}
The `/systemcheck` endpoint is not mandatory for the brokered integration to function. For more information, see [Systemcheck documentation](../troubleshooting-broker.md#monitoring-systemcheck).
{% endhint %}

## **Debugging methods for Container Registry Agent**

The `LOG_LEVEL` environment variable can be set to the desired level (debug/info/warn/error) in order to change the level of the Container Registry Agent and Broker Client logs.

For more verbose debugging, run the Container Registry Agent with the `DEBUG=*` environment variable. This allows you to print the logs of the Node [Debug](https://www.npmjs.com/package/debug) package. The Debug package is used by several packages in the Container Registry Agent, among them the [Needle](https://www.npmjs.com/package/needle) package, which is used for making HTTP requests. To print debug logs specifically from Needle, set `DEBUG=needle`.

{% hint style="warning" %}
Using the debugging options of third-party tools is not recommended for production environments, as this may result in logging sensitive information in logs that are not maintained by Snyk, for example, header information of HTTP requests.
{% endhint %}
