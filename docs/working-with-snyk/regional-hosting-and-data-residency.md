# 지역 호스팅 및 데이터 레지던시

{% hint style="info" %}
**기능 지원 범위**

지역 호스팅 및 데이터 레지던시는 Enterprise 요금제에서만 사용할 수 있습니다.

자세한 내용은 [Plans and pricing](https://snyk.io/plans)을 참조하세요.
{% endhint %}

Snyk은 여러 지역에서 데이터를 호스팅할 수 있습니다. 시스템을 처음 온보딩하는 동안 계정 팀과 협력하여 멀티테넌트 지역을 선택할 수 있습니다. 단일 테넌트 가용성(Snyk 프라이빗 클라우드)의 경우 온보딩 전에 계정 팀에 문의하세요.

{% hint style="info" %}
기본적으로 고객은 미국 지역에서 호스팅됩니다.
{% endhint %}

## 데이터 레지던시란 무엇인가요**?**

데이터 레지던시를 사용하면 선택한 데이터의 하위 집합을 어느 지역에서 호스팅할지 제어할 수 있습니다. 자세한 내용은 [Regional and global data](regional-hosting-and-data-residency.md#regional-and-global-data)를 참조하세요.

데이터 레지던시는 [Snyk Open Source](../scan-with-snyk/snyk-open-source/), [Snyk Code](../scan-with-snyk/snyk-code/), [Snyk Container](../scan-with-snyk/snyk-container/) 및 [Snyk Infrastructure as Code (IaC)](../scan-with-snyk/scan-infrastructure/scan-your-iac-source-code/)에 사용할 수 있습니다.

## 데이터 레지던시는 어떻게 작동하나요?

시스템 온보딩 중에 계정 팀과 협력하여 호스팅 지역을 선택할 수 있습니다.

{% hint style="warning" %}
지역을 선택한 후에는 해당 지역의 데이터를 다른 지역으로 마이그레이션할 수 없습니다. 새 지역으로 이동하려면 온보딩을 완전히 다시 해야 합니다.
{% endhint %}

## 어떤 지역에서 사용할 수 있나요?

Snyk은 다음 지역에 대한 데이터 레지던시를 제공합니다:

|            지역           |           URL          |
| :---------------------: | :--------------------: |
|      USA (default)      |   https://app.snyk.io  |
| EU (Germany, Frankfurt) | https://app.eu.snyk.io |
|     AUS (Australia)     | https://app.au.snyk.io |

단일 테넌트 배포는 Snyk 엔지니어링의 아키텍처 서비스 지원 가능성 확인에 따라 여기에 나열된 지역보다 더 많은 지역을 지원할 수 있습니다.

## 지역 및 글로벌 데이터

Snyk은 고품질 서비스를 제공하기 위해 여러 하위 프로세서를 활용합니다. 따라서 모든 데이터 유형이 선택한 지역 내에 저장될 수 있는 것은 아닙니다. 하위 프로세서 목록은 [Snyk 웹사이트](https://snyk.io/policies/subprocessors/)에서 확인할 수 있습니다.

제품별 데이터 처리 방식에 대한 예시는 [How Snyk handles your data](how-snyk-handles-your-data.md)를 참조하세요.

{% tabs %}
{% tab title="제품" %}
* Snyk Open Source
* Snyk Code
* Snyk Container
* Snyk Infrastructure as Code (IaC)
{% endtab %}

{% tab title="지역적으로 저장된 데이터" %}
* 취약점 데이터
* 취약점 소스
* 감사 로그
* 통합 관련 데이터
* 고객 소스 코드
{% endtab %}

{% tab title="전 세계에 저장된 데이터" %}
* 청구 데이터
* 고객 관계 관리 데이터
* 운영 로그 및 메트릭
* 제품 분석
* 지원 티켓
* 사용자 인증 데이터
{% endtab %}
{% endtabs %}

## 지역 멀티 테넌트 및 단일 테넌트 호스팅 참고 사항

Snyk은 미국 지역과 거의 동일한 기능, 지원, 성능을 지역 멀티 테넌트 및 단일 테넌트 지역을 지원합니다. 지역 간 기능 동등성에 대한 최신 개요를 확인하려면 계정 팀에 문의하세요.

### EU 및 AU 데이터센터 계정 만들기

EU 및 AU 데이터센터 Snyk 계정은 Enterprise 요금제를 구매한 경우에만 사용할 수 있습니다. 리소스 및 URL은 다음과 같습니다.

### 로그인 및 웹 UI URL

#### **EU**

[https://app.eu.snyk.io/](https://app.eu.snyk.io/)

#### **AU**

[https://app.au.snyk.io/](https://app.au.snyk.io/)

{% hint style="warning" %}
Snyk.io 또는 app.snyk.io를 사용하면 이러한 URL로 리디렉션되지 않습니다.
{% endhint %}

### 고객지원 포털 티켓

#### **EU**

[EU Tenant Support Portal](https://snyk-mt-eu-prod-1.eu.auth0.com/samlp/xU6rUSC7zvEco2ndKemfJNT6oKtc13Qw)

#### **AU**

[AU Tenant Support Portal](https://snyk-mt-au-prod-1.au.auth0.com/samlp/HnGYPWKxM9JegYL2aq0OAdBAwGJDz0vQ)

### API URLs

기본 URL은 다음과 같습니다:

#### **EU**

API v1: https://api.eu.snyk.io/v1/\
REST API: https://api.eu.snyk.io/rest/

#### **AU**

API v1: https://api.au.snyk.io/v1/\
REST API: https://api.au.snyk.io/rest/

### CLI 및 CI 파이프라인 URL

인스턴스를 실행하는 CLI와 CI는 모두 인스턴스에 대해 실행하도록 구성해야 합니다. 이렇게 하려면 다음을 실행하세요:

#### **EU**

`snyk config set endpoint=https://app.eu.snyk.io/api`

#### **AU**

`snyk config set endpoint=https://app.au.snyk.io/api`

또는 머신이나 CI 도구에 환경 변수를 설정할 수도 있습니다:

#### **EU**

`SNYK_API=https://app.eu.snyk.io/api`

#### **AU**

`SNYK_API=https://app.au.snyk.io/api`

Jenkins를 실행할 때 추가 인수를 사용합니다:

#### **EU**

`--API=https://app.eu.snyk.io/api`

#### **AU**

`--API=https://app.au.snyk.io/api`

### IDE URL

Snyk IDE 확장 프로그램에는 CLI와 유사한 수정 가능한 옵션이 있으며 적절한 endpoint를 사용하도록 구성해야 합니다. IDE의 Snyk 확장 설정에서 **Custom Endpoint**를 다음과 같이 EU 및 AU에 적절한 값으로 설정하세요.

{% hint style="warning" %}
최신 버전의 IDE 플러그인을 사용하고 있는지 확인하세요. 다음은 필요한 최소 버전을 알려드립니다:\
VSCode - 1.2.18\
Visual Studio - 1.1.21\
IntelliJ - 2.4.32
{% endhint %}

#### EU

`https://app.eu.snyk.io/api`

#### **AU**

`https://app.au.snyk.io/api`

<figure><img src="../.gitbook/assets/Screenshot 2023-04-20 at 3.25.46 PM.png" alt="Configuring the AU endpoint in Visual Studio Code"><figcaption><p>Visual Studio Code에서 AU endpoint 구성하기</p></figcaption></figure>

### 브로커 URL

[github.com/snyk/broker](https://github.com/snyk/broker) 문서를 따르되 컨테이너에 추가 환경 변수를 추가합니다:

#### **EU**

`-e BROKER_SERVER_URL=https://broker.eu.snyk.io`

#### **AU**

`-e BROKER_SERVER_URL=https://broker.au.snyk.io`

Helm 차트에 의해 배포된 브로커의 경우 [https://github.com/snyk/snyk-broker-helm](https://github.com/snyk/snyk-broker-helm) 문서를 따르고 다음 변수를 추가합니다

#### **EU**

`--set brokerServerUrl=https://broker.eu.snyk.io`

#### **AU**

`--set brokerServerUrl=https://broker.au.snyk.io`

### 고가용성(HA) 모드 URL이 있는 브로커

[High availability mode](../enterprise-configuration/snyk-broker/high-availability-mode.md)를 따르되, BROKER\_DISPATCHER\_BASE\_URL에 대해 다음 정보를 사용합니다:

#### **EU**

`-e BROKER_DISPATCHER_BASE_URL=https://api.eu.snyk.io`

#### **AU**

`-e BROKER_DISPATCHER_BASE_URL=https://api.au.snyk.io`

Helm 차트에 의해 배포된 브로커의 경우, values.yaml 파일을 편집하여 brokerDispatcherUrl에 관련 세부 정보를 포함합니다.

### 코드 에이전트 URL이 있는 브로커

[Snyk Broker - Code Agent](https://docs.snyk.io/integrations/snyk-broker/snyk-broker-code-agent)를 따르되, 코드 에이전트 컨테이너에 추가 환경 변수를 추가합니다:

#### **EU**

`-e UPSTREAM_URL=https://deeproxy.eu.snyk.io`

#### **AU**

`-e UPSTREAM_URL=https://deeproxy.au.snyk.io`

Helm 차트에 의해 배포된 코드 에이전트가 있는 브로커의 경우 [https://github.com/snyk/snyk-broker-helm](https://github.com/snyk/snyk-broker-helm) 문서의 안내를 따르고 코드 에이전트 차트에 다음 변수를 추가합니다:

#### **EU**

`--set upstreamUrlCodeAgent=https://deeproxy.eu.snyk.io`

#### **AU**

`--set upstreamUrlCodeAgent=https://deeproxy.au.snyk.io`

### Snyk Code Local Engine (SCLE)

브로커 URL 가이드에 안내된 값에 따라 해당 지역에 맞는 올바른 브로커 서버 URL로 `values-customer-settings.yml`을 설정합니다.

그리고 `values-customer-settings.yml`에 추가 변수를 추가합니다:

#### **EU**

`deeproxy:`\
`verificationEndpoint: "https://api.eu.snyk.io/v1/validate/token/snyk-to-deepcode-proxy-validation"`

#### **AU**

`deeproxy:`\
`verificationEndpoint: "https://api.au.snyk.io/v1/validate/token/snyk-to-deepcode-proxy-validation"`

## Snyk이 GDPR 규정을 준수하는 방법

Snyk은 개인정보 보호를 중요하게 생각하며 GDPR, CCPA 및 기타 관련 개인정보 보호법의 요건을 충족하기 위해 글로벌 개인정보 보호 프로그램을 운영합니다. Snyk은 모든 사용자 데이터를 동일한 방식으로 취급하며 업계 표준의 기술 및 조직적 조치를 사용하여 Snyk이 저장하는 정보를 보호합니다. Snyk의 개인정보 보호 프로그램은 법적 요건과 사용자의 요구를 모두 충족하도록 마련되었습니다.

자세한 내용은[ ](https://www.atlassian.com/trust/privacy)[Snyk Privacy Policy](https://snyk.io/policies/privacy/)에서 확인하십시오.
