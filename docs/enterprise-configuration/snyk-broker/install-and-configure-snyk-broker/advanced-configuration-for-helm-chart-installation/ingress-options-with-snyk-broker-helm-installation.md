# Snyk Broker Helm 설치 시 Ingress 옵션

Helm을 사용하여 Broker를 설정하는 경우, `brokerClientUrl` 파라미터를 구성해야 할 수 있다. 이 매개변수는 SCM에 연결하는 경우 PR 확인을 활성화하고 컨테이너 레지스트리에 연결할 수 있게 한다.

이 연결이 이루어지려면 SCM 또는 컨테이너 레지스트리에서 Broker로의 인바운드 연결이 있어야 한다. 쿠버네티스는 인그레스를 통해 이 인바운드 연결을 관리한다.

Ingress는 들어오는 네트워크 트래픽을 쿠버네티스 클러스터의 특정 서비스로 라우팅하는 방법이다. Ingress를 설정하는 방법에 대한 자세한 내용은 [Ingress에 대한 Kubernetes](https://kubernetes.io/docs/concepts/services-networking/ingress/)를 참조한다

ingress 트래픽에 사용할 수 있는 옵션은 두 가지가 있습니다. 기본적으로 클러스터 외부에서는 파드에 액세스할 수 없습니다.

**load balancer**를 사용하려면, `--set service.<service-type>=LoadBalancer`를 추가합니다. 허용되는 값은 `brokertype`, `crType`, `caType`입니다. 서비스 유형은 실행 중인 Broker의 유형을 나타냅니다.

Github의 예입니다:

```
helm install snyk-broker-chart snyk-broker/snyk-broker \
             --set scmType=github-com \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set scmToken=<ENTER_REPO_TOKEN> \
             --set brokerClientUrl=<ENTER_BROKER_CLIENT_URL>:<ENTER_BROKER_CLIENT_PORT> \
             --set service.brokerType=LoadBalancer \
             -n snyk-broker --create-namespace
```

**ingress**를 추가하려면, `values.yaml`파일에서 ingress를 활성화하고 값 파일의 예제 값에 따라 관련 구성 파라미터를 추가합니다. 이 기능을 사용하려면 클러스터에 ingress 컨트롤러가 올바르게 구성되어 있어야 합니다.
