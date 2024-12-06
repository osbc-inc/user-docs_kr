# 5단계: Broker 클라이언트 설정하기

{% hint style="info" %}
**시작하기 전** - 현재 동일한 Snyk 조직과 동일한 SCM에 대해 실행 중인 Broker 클라이언트가 없는지 확인하세요. 실행 중인 Broker 클라이언트가 있는 경우 [중지하고 제거하세요.](../step-2-removing-an-existing-broker-client.md)
{% endhint %}

Broker 클라이언트의 설정은 [Docker 이미지를 다운로드하거나 업데이트하는 것으로 시작됩니다. ](step-5.1-downloading-or-updating-the-snyk-broker-client-docker-image.md)

{% hint style="info" %}
코드 에이전트는 Broker 클라이언트 버전 4.108.0 이상 버전에서만 지원됩니다. 이미 Broker 클라이언트의 Docker 이미지를 사용하고 있는 경우 최신 업데이트를 가져오세요.
{% endhint %}

다운로드한 Docker 이미지를 기반으로 Broker 클라이언트 컨테이너를 실행하여 설정을 계속합니다.

[웹 UI에서 Snyk 코드 결과의 코드 스니펫을 표시하지 않고도 Broker 클라이언트를 실행](step-5.2a-running-the-broker-client-without-the-code-snippet-display.md)할 수 있습니다:

<figure><img src="../../../../../.gitbook/assets/Broker - Results - without code snippets (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (4) (1).png" alt="Broker Client run with no display of code snippets"><figcaption><p>코드 스니펫 표시 없이 Broker 클라이언트 실행</p></figcaption></figure>

또는 [웹 UI에서 Snyk 코드 결과의 코드 스니펫을 표시하여 Broker 클라이언트를 실행](step-5.2b-running-the-broker-client-with-the-code-snippets-display.md)할 수도 있습니다:

<figure><img src="../../../../../.gitbook/assets/Broker - Results - with code snippets (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (2).png" alt="Broker Client run with display of code snippets"><figcaption><p>코드 스니펫 표시와 함께 실행되는 Broker 클라이언트</p></figcaption></figure>
