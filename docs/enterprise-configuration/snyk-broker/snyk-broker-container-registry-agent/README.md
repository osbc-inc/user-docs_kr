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

### 컨테이너 레지스트리 에이전트 구성 및 실행

[필수 요구 사항](./#prerequisites-for-container-registry-agent)에 제공된 링크를 사용하여 Docker Hub에서 컨테이너 레지스트리 에이전트 이미지를 가져올 수 있습니다.

컨테이너 레지스트리 에이전트를 구성하려면 다음 환경 변수가 필요합니다:

* `SNYK_PORT` - 컨테이너 레지스트리 에이전트가 연결을 수락하는 로컬 포트(기본값: 17500).
* `SNYK_MAX_IMAGE_SIZE_IN_BYTES` - Snyk이 스캔할 수 있는 이미지의 최대 크기(기본값: 2147483648).

관련 구성으로 컨테이너 레지스트리 에이전트 컨테이너를 실행합니다:

```
docker run --restart=always \
       -p 8081:8081 \
       -e SNYK_PORT=8081 \
       snyk/container-registry-agent:latest
```

## 컨테이너 레지스트리별 구성

다음 컨테이너 레지스트리에는 특정 환경 변수, 설정 또는 둘 다 필요합니다.

### 디지털오션 컨테이너 레지스트리

디지털오션 컨테이너 레지스트리용 Broker 클라이언트를 설정할 때 `CR_USERNAME`과`CR_PASSWORD`는 필요하지 않습니다. 대신 디지털 오션 인증 토큰인`CR_TOKEN`을 지정합니다.

### GCR 및 Google 아티팩트 레지스트리

앞의 모든 정보는 이러한 컨테이너 레지스트리에 대한 Broker 클라이언트를 설정하는 데 적용됩니다. `CR_USERNAME`값은 영구적이며 `_json_key`여야 하고, `CR_PASSWORD` 값은 Google 인증에 사용되는 JSON 키여야 한다는 점에 유의하세요.

### **JFrog** 컨테이너 레지스트리(아티팩토리)

**리포지토리 경로**를 Docker 액세스 방법으로 사용하는 경우 컨테이너 레지스트리 호스트 이름을 이 구조의 `CR_BASE` 변수에 설정하세요:`<your artifactory host>/artifactory/api/docker/<artifactory-repo-name>`

카탈로그 엔드포인트 `/artifactory/api/docker/<artifactory-repository>/v2/_catalog` 는 Artifactory에서 프로젝트를 가져올 때 필요하지 않으며, 이미지 저장소를 나열하는 데 사용됩니다.

자세한 내용은 [JFrog Artifactory 컨테이너 레지스트리 통합 구성하기](../../../integrate-with-snyk/snyk-container-integrations/container-security-with-jfrog-artifactory-integration/configuring-your-jfrog-artifactory-container-registry-integration.md)를 참조하세요.

### **Elastic** 컨테이너 레지스트리 **(ECR)**

Elastic 컨테이너 레지스트리와 다른 컨테이너 레지스트리에서 통신은 동일합니다. 에이전트는 컨테이너 레지스트리를 동기식으로 호출하여 이미지를 나열하고 가져옵니다. 그런 다음 에이전트는 이미지를 스캔하고 콜백을 사용하여 결과를 Broker 클라이언트로 전송합니다. ECR에는 에이전트에서 IAM 역할 또는 사용자를 설정해야 하는 특수 인증 메커니즘이 있습니다.

<figure><img src="../../../.gitbook/assets/image (20) (3).png" alt="High-level architecture of the brokered ECR integration"><figcaption><p>Broker ECR 통합의 상위 수준 아키텍처</p></figcaption></figure>

#### ECR에 필요한 AWS 리소스

ECR 설정에는 다음과 같은 종류의 IAM 리소스를 만들어야 합니다:

* 컨테이너 레지스트리 에이전트 IAM 역할 또는 IAM 사용자: 에이전트가 ECR에 대한 액세스 권한이 있는 교차 계정 역할을 맡는 데 사용하는 IAM 역할 또는 IAM 사용자. 다음과 같은 권한을 가져야 합니다:"`sts:AssumeRole"`.
*   Snyk ECR 서비스 역할: 컨테이너 레지스트리 에이전트 IAM 역할 또는 IAM 사용자가 ECR에 대한 읽기 전용 액세스 권한을 얻기 위해 가정하는 ECR에 대한 액세스 권한이 있는 IAM 역할입니다. ECR 서비스 역할에는 다음과 같은 권한이 있어야 합니다:

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

#### ECR 설정 단계

설명된 리소스는 단일 컨테이너 레지스트리 에이전트 인스턴스가 서로 다른 계정에 있는 ECR 리포지토리에 액세스할 수 있도록 다음과 같이 사용할 수 있습니다.

**이 단계는 한 번만 실행하세요.** 컨테이너 레지스트리 에이전트 IAM 역할 또는 IAM 사용자를 생성하고 이를 사용하여 컨테이너 레지스트리 에이전트를 실행합니다. [AWS 문서](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/setting-credentials-node.html)에 설명된 방법 중 하나를 사용하여 컨테이너 레지스트리 에이전트에 IAM 역할 또는 IAM 사용자를 제공할 수 있습니다.

**각 ECR 계정에 대해 별도의 Broker 인스턴스를 사용하여 각 ECR 계정에 대해 다음 단계를 실행합니다:**

1. ECR이 있는 AWS 계정에서 ECR에 대한 읽기 권한이 있는 Snyk ECR 서비스 역할을 생성하고, 일회성 단계에서 생성한 특정 컨테이너 레지스트리 에이전트 IAM 역할 또는 IAM 사용자만 이 역할을 맡을 수 있도록 신뢰 관계를 편집합니다.
2. 컨테이너 레지스트리 에이전트 IAM 역할 또는 IAM 사용자가 Snyk ECR 서비스 역할만 맡을 수 있도록 제한합니다.
3. Broker 클라이언트에 ECR 리전과 함께 Snyk ECR 서비스 역할의 역할 ARN(Amazon 서비스 이름)을 제공합니다. Broker 클라이언트는 이 역할 ARN을 컨테이너 레지스트리 에이전트에 전달하고, 컨테이너 레지스트리 에이전트는 이 역할이 ECR에 액세스하는 것으로 간주합니다. 다음 환경 변수가 필요합니다:
   * CR\_ROLE\_ARN=\<SnykEcrServiceRole의 역할 ARN>
   * CR\_REGION=\<ECR의 AWS 지역>
   * CR\_EXTERNAL\_ID=<선택 사항. 신뢰 관계 조건에서 찾은 외부 ID>

## 시스템 검사 구성 및 사용

Broker 클라이언트의 `/systemcheck` 엔드포인트를 사용하여 Broker 클라이언트, 컨테이너 레지스트리 에이전트 및 컨테이너 레지스트리 간의 연결을 확인할 수 있습니다.

엔드포인트를 사용하려면 Broker 클라이언트에 다음 환경 변수를 제공하세요:\
`BROKER_CLIENT_VALIDATION_URL=<agent-url>/systemcheck`

Broker 클라이언트의 `/systemcheck` 엔드포인트를 호출하면, Broker 클라이언트에 제공된 자격 증명을 사용하여 `BROKER_CLIENT_VALIDATION_URL`을 사용하여 `/systemcheck` 엔드포인트 컨테이너 레지스트리 에이전트에 요청을 보냅니다. 그러면 컨테이너 레지스트리 에이전트가 컨테이너 레지스트리에 요청하여 연결 유효성을 검사합니다.

{% hint style="info" %}
The`/systemcheck` 엔드포인트는 중개된 통합이 작동하기 위해 반드시 필요한 것은 아닙니다. 자세한 내용은 [Systemcheck 문서](../troubleshooting-broker.md#monitoring-systemcheck)를 참조하세요.
{% endhint %}

## 컨테이너 레지스트리 에이전트의 디버깅 방법

컨테이너 레지스트리 에이전트 및 Broker 클라이언트 로그의 수준을 변경하기 위해`LOG_LEVEL`환경 변수를 원하는 수준(debug/info/warn/error)으로 설정할 수 있습니다.

보다 자세한 디버깅을 원하면`DEBUG=*` 환경 변수를 사용하여 컨테이너 레지스트리 에이전트를 실행하세요. 이렇게 하면 노드 [Debug](https://www.npmjs.com/package/debug) 패키지의 로그를 인쇄할 수 있습니다. 디버그 패키지는 컨테이너 레지스트리 에이전트의 여러 패키지에서 사용되며, 그 중 HTTP 요청을 하는 데 사용되는 [Needle](https://www.npmjs.com/package/needle) 패키지가 있습니다. 특히 Needle에서 디버그 로그를 인쇄하려면`DEBUG=needle`을 설정하세요.

{% hint style="warning" %}
타사 도구의 디버깅 옵션을 사용하는 것은 프로덕션 환경에서는 권장하지 않는데, 이는 HTTP 요청의 헤더 정보 등 Snyk에서 관리하지 않는 민감한 정보를 로그에 기록할 수 있기 때문입니다.
{% endhint %}
