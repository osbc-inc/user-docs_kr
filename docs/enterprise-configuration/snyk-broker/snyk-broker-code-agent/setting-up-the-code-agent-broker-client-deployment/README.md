# Docker를 사용하여 코드 에이전트용 Broker 설치하기

{% hint style="info" %}
FBroker 클라이언트 - 코드 에이전트를 처음 배포하려면 통합 컨설턴트/기술 성공 관리자 또는 [Snyk 지원팀](https://support.snyk.io/hc/en-us)과의 협업이 필요합니다.
{% endhint %}

전체 배포를 위해 코드 에이전트 - Broker 클라이언트 구성 요소를 설정하는 워크플로우는 다음과 같습니다:

1\. [설정 절차에 필요한 토큰을 받습니다](step-1-obtaining-the-required-tokens-for-the-setup-procedure/).

2\. 동일한 조직과 동일한 통합에 대해 이미 실행 중인 Broker 클라이언트가 있는 경우: [기존 Broker 클라이언트를 중지하고 제거합니다](step-2-removing-an-existing-broker-client.md).

3\. [Code Agent – Broker 클라이언트 통신을 위한 내부 네트워크를 생성합니다](step-3-creating-a-network-for-the-broker-client-and-code-agent-communication.md).

4\. [Code Agent 컴포넌트를 설정합니다](step-4-setting-up-the-code-agent/).

5\. [Broker 클라이언트를 설정합니다](step-5-setting-up-the-broker-client/).\
웹 UI 결과에 코드 스니펫을 표시하거나 표시하지 않고 Broker 클라이언트 컴포넌트를 설정할 수 있습니다. [코드 조각 없이 Broker 클라이언트 실행하기 ](step-5-setting-up-the-broker-client/step-5.2a-running-the-broker-client-without-the-code-snippet-display.md)및 [코드 조각을 사용하여 Broker 클라이언트 실행하기](step-5-setting-up-the-broker-client/step-5.2b-running-the-broker-client-with-the-code-snippets-display.md)를 참조하세요.

6\. [Code Agent 테스트 – 클라이언트 Broker 설정](step-6-testing-the-code-agent-snyk-broker-setup.md).
