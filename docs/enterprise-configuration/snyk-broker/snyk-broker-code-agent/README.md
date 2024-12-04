# Snyk Broker - Code Agent

{% hint style="info" %}
Snyk Broker를 통해 Snyk 코드 분석을 실행하는 가장 선호되는 방법은 [Brokered Code](../install-and-configure-snyk-broker/advanced-configuration-for-snyk-broker-docker-installation/snyk-code-clone-capability-with-broker-for-docker.md)를 이용하는 것입니다. 코드 에이전트는 장점이 없는 대체 방법입니다. 그러나 조직에서 이를 설정하려면 Snyk 통합 컨설턴트 또는 기술 성공 관리자에게 문의하거나 [Snyk 지원팀](https://support.snyk.io/hc/en-us)에 문의하세요.
{% endhint %}

Snyk Broker를 통해 자체 호스팅 Git 서버에 Snyk 코드를 연결하려면, Snyk Broker 배포 구조에 코드 에이전트 구성 요소를 추가해야 합니다. 코드 에이전트 구성 요소를 Snyk Broker와 함께 사용하면 자체 호스팅 Git 제공업체에 저장된 리포지토리를 스캔하고 이러한 리포지토리에 Snyk Code 분석을 적용하여 소스 코드의 잠재적 취약성을 찾아 우선순위를 정하고 수정할 수 있습니다.

Snyk Broker 배포 방법에 대한 자세한 내용은 [Snyk Broker](../)를 참조하세요.

[자동 PR Checks 기능](../../../snyk-admin/snyk-broker/snyk-broker-code-agent/broken-reference/)은 현재 Snyk Broker - 코드 에이전트 배포 방법에서 지원되지 않습니다.

자체 호스팅 Git 서버에 저장된 리포지토리에 Snyk 코드 분석을 적용하려면 다음 **구성 요소**가 필요합니다:

* **Broker Server** - Snyk SaaS 백엔드에서 실행되는 서버입니다. Broker Server는 Snyk에서 제공하므로 사용자가 직접 설치할 필요가 없습니다.
* **Broker Client** - 인프라에 배포되는 [Docker 이미지](https://hub.docker.com/r/snyk/broker/)입니다.\
  자세한 내용은 [Broker Client 설정하기](setting-up-the-code-agent-broker-client-deployment/step-5-setting-up-the-broker-client/)를 참조하세요.
* **Code Agent** - 인프라에 배포되는 또 다른 [Docker 이미지](https://hub.docker.com/r/snyk/code-agent/)입니다.\
  자세한 내용은 [Code Agent 설정하기](setting-up-the-code-agent-broker-client-deployment/step-4-setting-up-the-code-agent/)를 참조하세요.\
  코드 에이전트는 Snyk Broker 버전 4.108.0 이상 버전에서만 지원됩니다. 이미 실행 중인 Broker 클라이언트가 있는 경우 최신 Docker 이미지를 가져와서 업데이트해야 합니다. 자세한 내용은 [Snyk Broker Client 다운로드 또는업데이트 – Docker 이미지](setting-up-the-code-agent-broker-client-deployment/step-5-setting-up-the-broker-client/step-5.1-downloading-or-updating-the-snyk-broker-client-docker-image.md)를 참조하세요.

**Broker Client** 및 **Code Agent** 구성 요소는 인프라에 배포되어 두 개의 개별 서비스를 생성합니다. 이러한 구성 요소는 Broker 서버, Snyk 코드 AI 엔진, Snyk 웹 UI와 함께 다음과 같은 코드 분석 워크플로우를 담당합니다:

1\. Snyk 웹 UI에서 사용자가 자체 호스팅된 Git 서버에서 코드 분석을 위해 Snyk로 리포지토리를 가져오기 위한 요청이 시작됩니다. 이 요청은 Snyk API v1에서 [Import targets request](https://snyk.docs.apiary.io/#reference/import-projects/import/import-targets)을 사용하여 시작할 수도 있습니다.

2\. 요청이 Snyk가 호스팅하는 Broker 서버에 도착합니다. Broker 서버는 요청을 Broker 클라이언트로 전송하고, Broker 클라이언트는 이를 코드 에이전트로 전송합니다. Broker 클라이언트는 코드 에이전트에게 필요한 리포지토리를 저장하는 통합 SCM에 대한 연결 세부 정보를 자동으로 제공합니다.

3\. 코드 에이전트가 통합 SCM에 연결하고 인프라에서 안전한 방식으로 로컬 리포지토리를 복제합니다. 복제된 리포지토리는 코드 에이전트 컨테이너에 임시로 저장됩니다. 복제는 HTTPS 연결을 통해 수행됩니다. SCM이 HTTPS를 지원하지 않는 경우 역방향 프록시를 사용하여 이 문제를 해결할 수 있습니다. 자세한 내용은 Snyk의 기술 담당자에게 문의하세요.

4\. 코드 에이전트는 복제된 리포지토리에서 지원되는 파일을 필터링하여 Snyk 코드 AI 엔진으로 전송합니다.

5\. [Snyk Code AI Engine](https://docs.snyk.io/products/snyk-code/introducing-snyk-code/key-features/ai-engine) 이 취약점 문제를 찾기 위해 코드 파일을 분석합니다. 분석 결과는 Snyk 웹 UI로 다시 전송됩니다. 복제된 파일은 클라우드 제공업체의 최소 스토리지 정책에 따라 [cached](./#how-snyk-processes-this-data) 됩니다.

<figure><img src="../../../.gitbook/assets/Code Agent - diagram - new - 4.png" alt="Snyk Code Analysis workflow with Broker"><figcaption><p>Broker를 사용한 Snyk 코드 분석 워크플로</p></figcaption></figure>
