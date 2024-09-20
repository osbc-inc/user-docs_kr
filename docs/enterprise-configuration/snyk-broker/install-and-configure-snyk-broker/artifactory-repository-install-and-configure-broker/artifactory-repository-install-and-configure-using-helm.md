# 아티팩토리 저장소 - Helm을 사용하여 설치 및 구성하기

{% hint style="info" %}
아티팩토리 또는 넥서스 컨테이너 레지스트리와의 브로커 통합에 대한 자세한 내용은 [Snyk Broker -Container Registry Agent](../../snyk-broker-container-registry-agent/)를 참조하세요.
{% endhint %}

Snyk Broker Helm 차트 사용에 대한 지침은 [Helm을 사용하여 Broker 설치 및 구성](../install-and-configure-broker-using-helm.md)을 참조하세요.   환경 변수의 정의를 포함한 자세한 내용은[Artifactory Repository - Snyk Broker 환경 변수](artifactory-repository-environment-variables-for-snyk-broker.md)를 참조한다.

참고: `artifactoryUrl` 값에 `https://`

```
helm install snyk-broker-chart snyk-broker/snyk-broker \
             --set scmType=artifactory \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set artifactoryUrl=<ENTER_ARTIFACTORY_URL> \
             -n snyk-broker --create-namespace
```
