# Code Agent 및 Broker 클라이언트의 전제 조건

설정 프로세스를 시작하기 전에 Broker 클라이언트 및 Code Agent 구성 요소를 실행하기 위한 최소 요구 사항을 Broker 클라이언트 및 Code Agent 시스템에 충족하는지 확인하세요.

Broker 클라이언트 - Code Agent 배포 방법을 사용하려면 Broker 클라이언트 및 Code Agent 구성 요소를 Snyk에서 활성화해야 합니다. Broker 클라이언트 및 코드 에이전트 구성 요소를 활성화하려면 다음 중 한 곳에 문의하세요:

* 구현 컨설턴트(IC)
* 기술 성공 관리자(TSM)
* [Snyk 지원](https://support.snyk.io/hc/en-us)

Snyk Broker - Code Agent 배포 방법을 통해 가져올 수 있는 최대 파일 크기는 CLI를 통한 것과 동일하게 1MB입니다. 자세한 내용은 [Snyk 코드 분석을 위한 파일 크기 제한](https://docs.snyk.io/scan-applications/supported-languages-and-frameworks/introduction-to-snyk-supported-languages-and-frameworks#file-size-limit-for-snyk-code-analysis) 참조하세요.

Broker 클라이언트와 Code agent를 호스팅하는 머신은 Docker 데스크톱 또는 Kubernetes를 사용하여 Docker 컨테이너를 실행할 수 있어야 합니다.

{% hint style="info" %}
**EU 및 AU용 멀티테넌트 설정**\
EU 또는 AU 멀티테넌트 환경에서 사용하기 위해 Broker, Code Agent 또는 둘 모두를 설정하는 경우 특정 URL이 포함된 추가 환경 변수가 필요합니다.\
예: `-e BROKER_SERVER_URL=https://broker.eu.snyk.io`\
URL에 대해서는 [EU 및 AU 계정 데이터 센터 생성](https://docs.snyk.io/snyk-processes/data-residency-at-snyk#eu-and-au-datacenter-account-creation) 참조하세요.
{% endhint %}

## Code Agent 구성 요소의 전제 조건

**Code Agent** 컴포넌트를 실행하기 위한 최소 요구 사항은 다음과 같습니다:

* **CPU** - 1 vCPU
* **메모리**- 2Gb
* **디스크 공간** - 2Gb\
  사용 가능한 디스크 공간에 따라 동시에 가져올 수 있는 리포지토리의 최대 크기가 결정됩니다. 이 크기를 초과하는 리포지토리를 가져오려면 사용 가능한 디스크 공간을 늘려야 합니다. 그러나 2Gb보다 큰 리포지토리를 가져오기 전에 구현 컨설턴트와 상담하는 것이 좋습니다.
* **네트워크 :**
  * SCM 연결 - 분석하려는 리포지토리를 저장하는 SCM과의 HTTPS 통신. HTTP 전용 SCM 배포에 대한 지원은 Code Agent와 SCM 사이에 역방향 프록시를 배포하여 해결할 수 있습니다.
  * Snyk 코드 AI 엔진 연결 - [https://deeproxy.snyk.io/](https://deeproxy.snyk.io/)에서 코드 분석 엔진에 대한 아웃바운드 통신.
* 인터넷 대역폭 및 연결 - Broker 서버에 소스 코드를 업로드하는 속도는 낮은 대역폭과 느린 인터넷 연결의 영향을 받습니다.
* **Snyk API 토큰** - Snyk 계정으로 코드 Code Agent 요소를 인증하려면 Snyk API 토큰이 필요합니다. 자세한 내용은 [Snyk API 토큰받기](../../../getting-started/how-to-obtain-and-authenticate-with-your-snyk-api-token.md)를 참조하세요.

{% hint style="info" %}
현재 Code Agent 를 Broker 이중화 솔루션의 일부로 배포할 수 없습니다.
{% endhint %}

## Broker 클라이언트 구성 요소의 전제 조건

**Broker 클라이언트** 컴포넌트를 실행하기 위한 최소 요구 사항은 다음과 같습니다:

* **CPU** - 1 vCPU
* **RAM** - 256MB
* **네트워크 액세스**- Broker 서버([https://broker.snyk.io](https://broker.snyk.io))로의 아웃바운드 TLS(443) 통신. 이 아웃바운드 통신은 네트워크에 설치된 모든 방화벽에서도 허용되어야 합니다.\
  다른 Snyk 제품에 동일한 Broker 클라이언트를 사용 중이고 거기서 자동 PR 확인 기능을 사용하려면 다음 사항도 구성해야 합니다: 구성한 포트(일반적으로 8000)의 BROKER\_CLIENT\_URL에서 통합(SCM)에서 Broker 클라이언트로의 인바운드 액세스를 허용하는 내부 연결입니다. 이것은 인터넷에서 인바운드가 아닙니다. [Broker 클라이언트 실행하기](setting-up-the-code-agent-broker-client-deployment/step-5-setting-up-the-broker-client/step-5.2a-running-the-broker-client-without-the-code-snippet-display.md)를 참조하세요.
* **Broker 토큰** - 특정 조직 및 특정 통합 SCM에 대해 Broker 토큰을 배포하려면 고유한 Broker 토큰이 필요합니다. 자세한 내용은 [Broker 토큰 얻기](setting-up-the-code-agent-broker-client-deployment/step-1-obtaining-the-required-tokens-for-the-setup-procedure/obtaining-your-broker-token.md)를 참조하세요.
* **SCM 토큰** - SCM에 대한 특정 권한으로 액세스하려면 통합 SCM 토큰이 필요합니다. 자세한 내용은 [SCM 토큰 얻기](setting-up-the-code-agent-broker-client-deployment/step-1-obtaining-the-required-tokens-for-the-setup-procedure/obtaining-your-scm-token.md)를 참조하세요.
