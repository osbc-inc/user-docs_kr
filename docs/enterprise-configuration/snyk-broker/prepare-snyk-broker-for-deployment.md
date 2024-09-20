# 배포를 위한 Snyk Broker 준비하기

## Snyk Broker의 전제 조건

Windows에서 Snyk Broker를 사용하는 것은 지원되지 않습니다. Windows 사용자는 Linux를 사용하여 Broker를 배포할 것을 권장합니다.

EU 또는 AU 멀티테넌트 환경에서 사용하기 위해 Broker, 코드 에이전트 또는 둘 모두를 설정하는 경우 특정 URL이 포함된 추가 환경 변수가 필요합니다.\
예: `-e BROKER_SERVER_URL=https://broker.eu.snyk.io`\
URL에 대해서는 지역 호스팅 및 데이터 상주 페이지의 [Broker URLs](../../working-with-snyk/regional-hosting-and-data-residency.md#broker-urls)을 참조하세요.

다음은 모든 환경에서 Snyk Broker를 사용하기 위한 전제 조건입니다:

* 클라이언트 컴퓨터 시스템 요구 사항: CPU 1개, 256MB RAM
* 네트워크 액세스: 네트워크에 설치된 모든 방화벽에서도 허용되는 [https://broker.snyk.io](https://broker.snyk.io)으로의 아웃바운드 TLS(443)
* Snyk 계정
* Snyk API를 사용하여 자체 활성화된 브로커 통합 또는 [Snyk 지원팀](https://support.snyk.io/hc/en-us)에 문의하여 활성화된 브로커 통합
* Broker 토큰이라는 고유한 UUID 토큰. [Snyk Broker용 대상 애플리케이션에서 자격 증명 생성](prepare-snyk-broker-for-deployment.md#generate-credentials-in-the-target-application-for-snyk-broker)을 참조하세요.
* SCM 토큰 또는 비밀번호. 토큰을 얻는 방법에 대한 자세한 내용은 각 SCM의 [연동 서비스 문서](../../integrate-with-snyk/)를 참조하세요. Snyk Broker mTLS 방식의 인증을 지원하지 않습니다.
* Docker Hub에서 이미지를 가져오도록 구성된 Docker

## Snyk Broker 설치를 위한 호스트 준비하기

각 통합을 위해 Broker 클라이언트의 인스턴스를 서로 다른 호스트에 두 개 이상 구성하거나 Kubernetes 시스템을 통해 설치할 것을 권장합니다. 이렇게 하면 중복성을 위해 항상 두 개 이상의 인스턴스를 실행할 수 있습니다.

## Snyk Broker 사용을 위한 네트워크 구성

프록시 서버를 사용하는 경우 Broker 클라이언트의 인바운드 및 아웃바운드 액세스를 허용하도록 프록시 서버와 방화벽을 구성해야 합니다:

* Broker 클라이언트(사용자 환경에서 실행 중)에서 포트 443의 [broker.snyk.io](https://broker.snyk.io) (또는[https://broker.eu.snyk.io](https://broker.eu.snyk.io) / [https://broker.au.snyk.io](https://broker.au.snyk.io))로의 아웃바운드 연결
* 연동 서비스(SCM, CR)에서 구성한 포트(일반적으로 8000)의 BROKER\_CLIENT\_URL에서 Broker 클라이언트로의 인바운드 액세스를 허용하는 내부 연결입니다. 이것은 인터넷에서 인바운드가 아닙니다.

Snyk Broker 서버 측에서 시작된 트래픽은 항상 사용 가능한 최신 Broker 연결을 사용합니다. Snyk 측의 모든 활동(예: 반복 테스트에 의해 구동되는 트래픽)은 한 번에 하나의 복제본에만 나타납니다. Snyk 활동의 양은 리포지토리 또는 Jira 항목의 활동에 비례합니다. 해당 활동은 모든 복제본에 배포되는 웹훅을 생성합니다.

## Broker 배포 구성 요소 정의

배포에 필요한 구성 요소가 무엇인지 이해하려면 다음을 고려하세요:

* Broker를 어떤 서비스에 연결하고 있나요?
  * GitHub, Jira, Bitbucket, Harbor, 기타 서비스
  * [Snyk Broker - 클라이언트 통합 설정](broken-reference/)을 참조하세요.
* Infrastructure를 코드 파일로 감지할 계획인가요?
  * 예. -- 환경 변수 `-e ACCEPT_IAC`또는 사용자 지정 허용 목록 `accept.json` 파일을 배포에 추가해야 합니다.
  * [Snyk Broker - 코드형 Infrastructure 탐지](snyk-broker-infrastructure-as-code-detection/)를 참조하세요.
* Snyk 코드 취약점을 탐지할 계획인가요?
* 컨테이너 레지스트리에 연결할 계획인가요?
  * Broker와 함께 추가 에이전트인 Snyk Broker 컨테이너 레지스트리 에이전트를 배포해야 합니다.
  * [Snyk Broker 컨테이너 레지스트리 에이전트](snyk-broker-container-registry-agent/)를 참조하세요.

모든 연동에는 특정 Broker 토큰이 할당되어 있습니다. 즉, Snyk 코드 취약점을 분석하고 컨테이너 레지스트리에 연결하려는 경우 통합이 이루어집니다:

* 추가 환경 변수 `-e ACCEPT_CODE` 또는 사용자 지정 허용 목록 `accept.json`이 있는 SCM용 브로커 1개와 Broker 코드 에이전트 1개
* 컨테이너 레지스트리용 브로커 1개 및 컨테이너 레지스트리 Broker 에이전트 1개

## Snyk Broker를 위한 대상 애플리케이션에서 자격 증명 생성하기

{% hint style="info" %}
Snyk은 90일마다 Snyk Broker에 사용되는 모든 API 토큰과 자격 증명을 교체할 것을 권장합니다.

Broker를 처음 배포할 때는 Snyk 계정 팀과의 협업이 필요합니다.
{% endhint %}

Broker의 대상 애플리케이션에 대한 자격 증명을 생성한 후, Snyk Broker 실행하기 위한 환경 변수를 구성합니다.

Broker 토큰은 필수이며, Broker를 사용하려면 반드시 생성해야 합니다.

코드 리포지토리(SCM) 통합의 경우 Broker 토큰은 API를 통해 생성하거나 [Snyk 지원팀](https://support.snyk.io/hc/en-us/requests/new)에 문의하여 생성할 수 있습니다.

1. Snyk API v1 문서로 이동하여 [연동 서비스 API](https://snyk.docs.apiary.io/#reference/integrations/integration/update-existing-integration) 내의 “기존 연동 서비스를 위한 broker 설정” 아래의 예시를 따르거나 [Snyk 지원팀](https://support.snyk.io/hc/en-us/requests/new)에 문의하세요.
2. Snyk API v1 문서로 이동하여 연동 서비스 API 내의 “기존 연동 서비스를 위한 broker 설정” 아래의 예시를 따르거나 Snyk 지원팀에 문의하세요. 2. 특정 연동 업데이트에 대한 **설정(Settings) > 연동(Integrations)**을 선택하여 브로커 토큰을 확인하여 브로커 토큰이 지정된 SCM 연동 아래의 Snyk 웹 UI에서 생성되었는지 확인합니다.

[Artifactory Repository](../../integrate-with-snyk/package-repository-integrations/artifactory-package-repository-connection-setup/) 및 [Nexus Repository 관리자](../../integrate-with-snyk/package-repository-integrations/nexus-repository-manager-connection-setup/) 브로커 인스턴스 또는 [Jira](install-and-configure-snyk-broker/jira-install-and-configure-broker/setup-broker-with-jira.md) 통합의 경우, Snyk UI에서 Broker 토큰을 생성하거나 [Snyk 지원팀](https://support.snyk.io/hc/en-us/requests/new)에 문의할 수 있습니다.

1. Broker 토큰을 생성하려면 해당 특정 연동 서비스에 대한 **설정(Settings) > 연동(Integrations)**을 선택합니다.
2. Broker 토큰이 생성되면 연동 아래에서 아직 클라이언트를 설치 및 구성하지 않았으므로 이 화면의 알림에 “연결할 수 없음...”이 올바르게 표시됩니다.
3. UI에서 Broker 토큰을 복사하여 붙여넣어 클라이언트를 설치할 때 사용합니다.

## 여러 조직에서 Broker 사용

동일한 Broker 토큰을 사용하여 Snyk의 여러 조직에서 동일한 Git 서비스를 사용할 수 있습니다. 이렇게 하려면 조직에 대한 토큰을 만든 다음 원본을 기반으로 새 조직을 만듭니다. 그러면 토큰이 복제되고 이제 해당 토큰에 대해 Broker를 사용 설정할 수 있습니다.

기존 조직에 대해 소급 적용하려면 API v1 엔드포인트 [통합 복제(설정 및 자격 증명 포함)](https://snyk.docs.apiary.io/#reference/integrations/integration-cloning) 를 사용하여 Broker 토큰을 포함한 특정 통합을 복제할 수 있습니다.

이렇게 하지 않는 경우에는 각 연동 서비스 및 조직마다 고유한 Broker 토큰이 있으므로 조직에 대한 새 Broker 토큰을 생성해야 합니다.
