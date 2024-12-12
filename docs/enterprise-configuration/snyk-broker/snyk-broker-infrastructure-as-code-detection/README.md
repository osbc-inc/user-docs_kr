# Snyk Broker - 코드형 인프라 탐지

## Snyk Broker의 코드형 인프라(IaC)

기본적으로 코드형 인프라(IaC)에서 사용하는 일부 파일 형식은 활성화되어 있지 않습니다. 예를 들어 Terraform과 같은 리포지토리에 있는 IaC 파일에 대한 브로커의 액세스 권한을 부여하려면 환경 변수 `ACCEPT_IAC`를`tf,yaml,yml,json,tpl`의 조합으로 추가하면 됩니다.

예:

```
docker run --restart=always \
           -p 8000:8000 \
           -e BROKER_TOKEN=secret-broker-token \
           -e GITHUB_TOKEN=secret-github-token \
           -e PORT=8000 \
           -e BROKER_CLIENT_URL=http://my.broker.client:8000 \
           -e ACCEPT_IAC=tf,yaml,yml,json,tpl
       snyk/broker:github-com
```

그렇지 않으면`accept.json`을 편집하고 관련 IaC 특정 규칙을 추가한 다음 사용자 지정 수락 파일을 컨테이너에 로드할 수 있습니다. 별도의 폴더에 있는 사용자 지정 허용 파일을 사용하는 경우(`ACCEPT`환경 변수를 사용)`ACCEPT_IAC` 메커니즘을 사용할 수 없다는 점에 유의하세요.

## `ACCEPT`를 통한 사용자 지정 구성

`ACCEPT`환경 변수를 사용하여 Snyk Broker를 사용하여 인프라를 코드 파일로 감지하는 방법에 대한 자세한 내용은 다음 페이지를 참조하세요:

* [Broker를 사용하여 Terraform 구성 파일 감지하기](detecting-terraform-configuration-files-using-a-broker.md)
* [Broker를 사용하여 CloudFormation 구성 파일 탐지하기](detecting-cloudformation-configuration-files-using-a-broker.md)
* [Broker를 사용하여 Kubernetes 파일 탐지하기](detecting-kubernetes-configuration-files-using-a-broker.md)
