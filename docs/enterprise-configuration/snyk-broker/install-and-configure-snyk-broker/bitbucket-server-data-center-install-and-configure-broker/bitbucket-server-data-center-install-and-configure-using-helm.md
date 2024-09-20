# Bitbucket Server/데이터 센터 - Helm을 사용한 설치 및 구성

{% hint style="warning" %}
**릴리스 상태**

Snyk 코드 PR 확인은 Bitbucket DC/Server 버전 7.0 이상에서만 사용할 수 있습니다.
{% endhint %}

Snyk Broker Helm 차트 사용에 대한 지침은 [Helm을 사용하여 Broker 설치 및 구성하기](../install-and-configure-broker-using-helm.md)를 참조하세요. 사용할 명령은 다음과 같습니다. 환경 변수에 대한 정의는[BitBucket Server/Data Center - Snyk Broker의 환경 변수](bitbucket-server-data-center-environment-variables-for-snyk-broker.md)를 참조하세요.

도커 설정 지침에 있습니다.

참고:`bitbucket` 및 `bitbucketApi`값에는 `https://`

```
helm install snyk-broker-chart snyk-broker/snyk-broker \
             --set scmType=bitbucket-server \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set bitbucketUsername=<ENTER_USERNAME> \
             --set bitbucketPassword=<ENTER_PASSWORD> \
             --set bitbucket=<ENTER_BITBUCKET_URL> \
             --set bitbucketApi=<ENTER_BITBUCKET_API_URL> \
             --set brokerClientUrl=<ENTER_BROKER_CLIENT_URL>:<ENTER_BROKER_CLIENT_PORT> \
             --set enabledAppRisk=true \
             -n snyk-broker --create-namespace
```

{% hint style="info" %}
Snyk AppRisk는 기본적으로**`false`**로 설정되어 있습니다. 플래그를 **`true`**로 설정하여 사용하도록 설정합니다.
{% endhint %}
