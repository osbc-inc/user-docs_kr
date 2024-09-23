# Nexus 리포지토리 - Helm을 사용하여 설치 및 구성하기

{% hint style="info" %}
Artifactory 또는 Nexus 컨테이너 레지스트리와의 Broker 통합에 대한 자세한 내용은 [Snyk Broker -Container Registry Agent](../../snyk-broker-container-registry-agent/)를 참조하세요.
{% endhint %}

## Nexus 3 Helm 설치

Snyk Broker Helm 차트 사용에 대한 지침은[Helm을 사용하여 Broker 설치 및 구성하기](../install-and-configure-broker-using-helm.md)를 참조하세요. 사용할 명령어는 다음과 같다. 환경 변수에 대한 정의는[Nexus 리포지토리 -  Snyk Broker의 환경 변수](nexus-repository-environment-variables-for-snyk-broker.md)를 참조한다.

참고: for `baseNexusUrl` 및 `nexusUrl` 값의 경우 `https://`

```
helm install snyk-broker-chart snyk-broker/snyk-broker \
             --set scmType=nexus \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set baseNexusUrl=<ENTER_BASE_NEXUS_URL> \
             --set nexusUrl=<ENTER_NEXUS_URL>
             --set brokerClientValidationUrl=<ENTER_BROKER_CLIENT_VALIDATION_URL> \
             -n snyk-broker --create-namespace
```

## Nexus 2 Helm 설치

Snyk Broker Helm 차트 사용에 대한 지침은[Helm을 사용하여 Broker 설치 및 구성하기](../install-and-configure-broker-using-helm.md)를 참조하세요. 사용할 명령어는 다음과 같다. 환경 변수에 대한 정의는[Nexus 리포지토리 -  Snyk Broker의 환경 변수](nexus-repository-environment-variables-for-snyk-broker.md)를 참조한다.

참고: for `baseNexusUrl` 및 `nexusUrl` 값의 경우 `https://`

```
helm install snyk-broker-chart snyk-broker/snyk-broker \
             --set scmType=nexus2 \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set baseNexusUrl=<ENTER_BASE_NEXUS_URL> \
             --set nexusUrl=<ENTER_NEXUS_URL>
             --set brokerClientValidationUrl=<ENTER_BROKER_CLIENT_VALIDATION_URL> \
             -n snyk-broker --create-namespace
```
