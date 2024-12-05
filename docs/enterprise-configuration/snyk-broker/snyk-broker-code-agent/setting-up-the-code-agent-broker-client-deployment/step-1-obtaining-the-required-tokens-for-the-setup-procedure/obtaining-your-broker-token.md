# Broker 토큰 받기

Broker 토큰은 [Broker 클라이언트 구성 요소 설정](../step-5-setting-up-the-broker-client/step-5.2a-running-the-broker-client-without-the-code-snippet-display.md)에 필요하며,  `-e BROKER_TOKEN` 매개변수에 사용됩니다. Broker 토큰은 기본적으로 특정 조직 및 특정 통합 SCM과 연결되며, 이 경우 Snyk Broker 배포 방법을 활성화합니다. 각 통합 SCM마다 다른 Broker 토큰이 필요합니다.

* **코드 에이전트 설정에 기존 Broker 토큰 사용** - 동일한 조직 및 동일한 SCM에서 다른 Snyk 제품용 Broker 클라이언트를 실행하는 데 사용한 Broker 토큰이 이미 있는 경우 코드 에이전트용 Broker 클라이언트 설정에도 사용할 수 있습니다.
* **여러 Snyk 조직에 동일한 Broker 토큰 사용** -\
  기본적으로 Broker 토큰은 하나의 Snyk 조직에만 연결되지만, 다음 절차를 수행하면 여러 조직에 동일한 Broker 토큰을 사용할 수 있습니다. 이러한 절차를 수행하려면 조직 관리자 권한이 필요합니다:
  * **새 조직** - Broker 토큰이 있는 기존 조직을 기반으로 새 조직을 만드는 경우, 새 조직을 만드는 동안 기존 Broker 토큰이 복제되며 새 조직에도 사용할 수 있습니다.
  * 기**존 조직** - 다른 기존 조직에 기존 Broker 토큰을 사용하려는 경우 통합 API v1 엔드포인트 [복제](https://snyk.docs.apiary.io/#reference/integrations/integration-cloning/clone-an-integration-\(with-settings-and-credentials\))하기를 사용할 수 있습니다. 이 API는 통합의 Broker 토큰을 포함하여 기존 통합 설정을 복제합니다.
* **중복성을 위해 Broker 토큰 사용** - 중복성을 위해 동일한 조직과 동일한 SCM에 대해 두 개의 Broker 클라이언트를 설정하는 경우, 두 Broker 클라이언트 모두에 동일한 브로커 토큰을 사용해야 하며, 다음과 같은 방법으로 Snyk 브로커 토큰을 얻을 수 있습니다:
  * 권장: 브로커 토큰을 생성해 달라고 Snyk IC/TSM에 요청한 다음 웹 UI에서 Broker 토큰을 받습니다.
  * Snyk API를 사용하여 Broker 토큰을 생성합니다(다음 지침 참조).

어느 방법으로든 Broker 토큰이 생성되면 웹 UI에 토큰이 표시되며, 여기에서 토큰을 받을 [여기에서토큰을 받을](obtaining-your-broker-token.md#obtaining-your-broker-token-via-the-web-ui) 수 있습니다. .

## API를 통해 Broker 토큰 생성하기

다음과 같이 API를 사용하여 Broker 토큰을 생성할 수 있습니다.

1\. [기존 통합](https://snyk.docs.apiary.io/#reference/integrations/integration/update-existing-integration) API v1 업데이트 엔드포인트를 사용하여 특정 조직 및 특정 SCM에 대해 Snyk 브로커를 활성화합니다.

2\. 프로그래밍 방식으로 Broker 토큰을 생성하려면 1단계에서 Broker를 활성화한 후 Broker 토큰을 생성하는 [새 Broker 토큰 API v1 엔드포인트 프로비저닝](https://snyk.docs.apiary.io/#reference/integrations/integration-broker-token-provisioning/provision-new-broker-token) 사용합니다.

생성된 Broker 토큰은 API 응답 본문과 웹 UI에서 확인할 수 있습니다.

3\. 나중에 사용할 수 있도록 Broker 토큰을 복사하여 안전한 위치에 저장하거나 나중에 웹 UI를 통해 Broker 토큰을 받습니다.

## 웹 UI를 통해 Broker 토큰 받기

Broker 토큰은 Snyk IC/TSM이 생성하거나 사용자가 Snyk API를 사용하여 생성한 후 웹 UI에 표시됩니다. Broker 토큰은 특정 조직 및 특정 통합과 연결됩니다.

1\. Snyk 웹 UI를 열고 왼쪽 탐색에서 Snyk Broker를 설정할 조직을 선택합니다.

2\. 선택한 조직의 왼쪽 탐색에서 **연동(Integration)**&#xC744; 선택합니다. Snyk Broker를 연결하려는 연동 서비스를 찾아 설정(**Settings**) 아이콘을 클릭합니다.

<figure><img src="../../../../../.gitbook/assets/Snyk Broker - Organization - Integrations page.png" alt="Select Settings for an Integration"><figcaption><p>Select Settings for an Integration</p></figcaption></figure>

3\. 선택한 연동 서비스의 **설정** (**Settings**)페이지의 Broker **자격증명**(**Credentials**) 섹션에서 토큰 상자에서 Broker **토큰**을 복사하여 나중에 사용할 수 있도록 저장합니다:

<figure><img src="../../../../../.gitbook/assets/Snyk Broker - Broker Token - box.png" alt="Copy the Broker token"><figcaption><p>Broker 토큰 복사</p></figcaption></figure>
