# Helm을 사용하여 컨테이너 레지스트리 에이전트용 Broker 설치하기

[Docker를 사용하여 컨테이너 레지스트리 에이전트](./) 설치하려면`CR_AGENT_URL`파라미터가 필요하지만 Helm을 사용하여 설치하는 데는 필요하지 않다. 환경 변수는 [Docker로 설치](https://docs.snyk.io/snyk-admin/snyk-broker/snyk-broker-container-registry-agent#configuring-and-running-the-broker-client-for-container-registry-agent)할 때 정의되며 Helm으로 설치할 때도 적용된다.

```
helm install snyk-broker-chart snyk-broker/snyk-broker \
             --set scmType=container-registry-agent \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set crType=<ENTER_CR_TYPE> \
             --set crBase=<ENTER_CR_BASE_URL> \
             --set crUsername=<ENTER_CR_URSERNAME> \
             --set crPassword=<ENTER_CR_PASSWORD> \
             -n snyk-broker --create-namespace
```

`crType`에 허용되는 값입니다:

`artifactory-cr`\
`harbor-cr`\
`acr`\
`gcr`\
`docker-hub`\
`quay-cr`\
`nexus-cr`\
`github-cr`\
`ecr`\
`digitalocean-cr`

Elastic 컨테이너 레지스트리와 디지털 오션 컨테이너 레지스트리에는 다음 섹션에서 설명하는 대로 특정 매개 변수가 필요합니다.

## Elastic 컨테이너 레지스트리(ecr)

* crRoleArn
* crRegion
* crExternalId

```
helm install snyk-broker-chart snyk-broker/snyk-broker \
             --set scmType=container-registry-agent \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set crType=ecr \
             --set crRoleArn=<ENTER_CR_ROLE_ARN> \
             --set crRegion=<ENTER_CR_REGION> \
             --set crExternalId=<ENTER_CR_EXTERNAL_ID> \
             -n snyk-broker --create-namespace
```

## **DigitalOcean** 컨테이너 레지스트리 **(digitalocean-cr)**

* crToken

```
helm install snyk-broker-chart snyk-broker/snyk-broker \
             --set scmType=container-registry-agent \
             --set brokerToken=<ENTER_BROKER_TOKEN> \
             --set crType=digitalocean-cr \
             --set crBase=<ENTER_CR_BASE_URL> \
             --set crToken=<ENTER_CR_TOKEN> \
             -n snyk-broker --create-namespace
```
