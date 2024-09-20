# GitLab - Helm을 사용하여 설치 및 구성하기

Snyk Broker Helm 차트 사용에 대한 지침은 [Helm을 사용하여 Broker 설치 및 구성하기](../install-and-configure-broker-using-helm.md)를 참조하세요. 사용할 명령은 다음과 같습니다. 환경 변수에 대한 정의는[BitBucket Server/Data Center - Snyk Broker의 환경 변수](../bitbucket-server-data-center-install-and-configure-broker/bitbucket-server-data-center-environment-variables-for-snyk-broker.md)를 참조하세요.

{% hint style="info" %}
Helm을 사용한 설치 시 참고 사항

`gitlab`값의 경우`https://`을 포함하지 않는다.

`brokerToken`은`BROKER_TOKEN`환경 변수를 피드하고 설정하는 Helm 변수이다. 토큰을 전달하는 Helm 방식이다.

`ACCEPT_CODE`는 차트에서 [기본적으로 참으로 설정되어 있으며,](https://github.com/snyk/snyk-broker-helm/blob/465d4ef279755fa5c9507975a88348bab04c2264/charts/snyk-broker/templates/broker\_deployment.yaml#L383)[ACCEPT\_IAC](https://github.com/snyk/snyk-broker-helm/blob/465d4ef279755fa5c9507975a88348bab04c2264/charts/snyk-broker/templates/broker\_deployment.yaml#L386C23-L386C43)도 마찬가지입니다. 필요한 경우`disableAutoAcceptRules=true`를 사용하여 비활성화할 수 있지만, 그렇지 않으면 활성화됩니다.
{% endhint %}

```
helm install snyk-broker-chart snyk-broker/snyk-broker \
             --set scmType=gitlab \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set gitlab=<ENTER_GITLAB_URL> \
             --set scmToken=<ENTER_GITLAB_TOKEN> \
             --set brokerClientUrl=<ENTER_BROKER_CLIENT_URL>:<ENTER_BROKER_CLIENT_PORT> \
             --set enabledAppRisk=true \
             -n snyk-broker --create-namespace
```

{% hint style="info" %}
Snyk AppRisk는 기본적으로**`false`**로 설정되어 있습니다. 플래그를 **`true`**로 설정하여 사용하도록 설정합니다.
{% endhint %}
