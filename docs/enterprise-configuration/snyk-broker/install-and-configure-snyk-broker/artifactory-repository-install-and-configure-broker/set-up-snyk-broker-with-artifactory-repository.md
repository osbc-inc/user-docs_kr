# 아티팩토리 리포지토리 - Docker를 사용한 설치 및 구성

{% hint style="info" %}
**기능 사용 가능성**

Artifactory 리포지토리와의 통합은 Enterprise 요금제에서만 사용할 수 있습니다.

자세한 내용은 [요금제 및 가격 책정](https://snyk.io/plans)을 참조하세요.
{% endhint %}

이 페이지의 안내에 따라 Snyk Broker로 아티팩토리 리포지토리를 설정하세요. 이 통합은 온프레미스 아티팩토리 리포지토리 배포와의 안전한 연결을 보장하는 데 유용합니다.

아티팩토리 리포지토리와의 non-brokered 통합에 대한 자세한 내용은[Artifactory Repository 설정](../../../../integrate-with-snyk/package-repository-integrations/artifactory-package-repository-connection-setup/)을 참조하세요. 아티팩토리 컨테이너 레지스트리와의 브로커 통합에 대한 자세한 내용은 [Snyk Broker -Container Registry Agent](https://docs.snyk.io/snyk-admin/snyk-broker/snyk-broker-container-registry-agent)를 참조하세요.

{% hint style="info" %}
**전제 조건**\
Snyk 계정 팀에 Broker 토큰 제공을 요청하거나 Snyk 웹 UI에서 토큰을 생성합니다.

Docker 또는 Docker Linux 컨테이너를 실행할 수 있는 방법이 필요합니다.

일부 Windows용 Docker 배포는 Windows 컨테이너만 실행합니다. 배포가 Linux 컨테이너를 실행할 수 있는지 확인하세요.
{% endhint %}

## 아티팩토리 저장소 설정을 위한 Broker 토큰 받기

1. **Settings** > **Integrations > Package Repositories > Artifactory**로 이동합니다.
2. 아티팩토리 인스턴스의 URL을 입력합니다(**/artifactory로 끝나야 함**).
3. 사용자 이름과 비밀번호를 입력합니다.
4. **Save**를 선택합니다.

<figure><img src="../../../../.gitbook/assets/screenshot_2020-04-17_at_14.38.12.png" alt="Artifactory integration setup"><figcaption><p>아티팩토리 저장소 설정</p></figcaption></figure>

{% hint style="info" %}
**Snyk Broker** 켜기/끄기 스위치가 표시되지 않으면 필요한 권한이 없는 것이며 공개적으로 액세스할 수 있는 인스턴스만 추가할 수 있습니다.

비공개 레지스트리를 추가하려면 [Snyk 지원팀](https://support.snyk.io/hc/en-us/requests/new)에 요청을 제출하세요.
{% endhint %}

비공개 레지스트리를 추가하는 데 필요한 권한이 있으Web UI에서 Broker 토큰 생성하기Web UI에서 Broker 토큰 생성하기 [Web UI에서 Broker 토큰 생성하기](set-up-snyk-broker-with-artifactory-repository.md#web-ui-broker) 계속 진행합니다.

## &#x20;Web UI에서 Broker 토큰 생성하기

1. 아티팩토리 연동 설정에서 **Snyk Broker on/off**스위치를 켜기로 이동하여 Broker 토큰을 생성하는 양식을 표시합니다.
2. **Generate and Save**을 선택합니다.
3. Broker 클라이언트를 설정할 때 사용하기 위해 생성된 토큰을 복사합니다.

## 아티팩토리 레지스트리에 사용하도록 Broker 구성하기

아티팩토리 리포지토리 배포와 함께 Broker 클라이언트를 사용하려면 `docker pull snyk/broker:artifactory`를 **실행**하세요. 환경 변수에 대한 정의는[Artifactory Repository - Snyk Broker의 환경 변수](artifactory-repository-environment-variables-for-snyk-broker.md)를 참조하세요.

## 아티팩토리 리포지토리에 대한 Broker 클라이언트를 설정하는 Docker 실행 명령어

**다음 명령을 복사**하여 아티팩토리 레지스트리와 함께 사용하도록 완전히 구성된 Broker 클라이언트를 설정합니다. 관련 구성을 제공하여 Docker 컨테이너를 실행할 수 있습니다:

```console
docker run --restart=always \
           -p 8000:8000 \
           -e BROKER_TOKEN=secret-broker-token \
           -e ARTIFACTORY_URL=<yourdomain>.artifactory.com/artifactory \
       snyk/broker:artifactory
```

**npm 또는 Yarn**의 경우 다음 **명령**을 사용하세요.

```
docker run --restart=always \
  -p 8000:8000 \
  -e BROKER_TOKEN=secret-broker-token \
  -e ARTIFACTORY_URL=acme.com/artifactory \
  -e RES_BODY_URL_SUB=http://acme.com/artifactory \ 
  snyk/broker:artifactory
```

**Docker 실행 명령을 사용하는 대신,** 파생된 Docker 이미지를 사용하여 Broker 클라이언트 연동을 설정할 수 있습니다. 아티팩토리 연동을 위해 재정의할 환경 변수에 대해서는[파생된 Docker 이미지](../derived-docker-images-for-broker-client-integrations-and-container-registry-agent.md)를 참조하세요

## Broker 클라이언트 컨테이너를 시작하고 아티팩토리 리포지토리와의 연결을 확인합니다.

Broker 클라이언트 구성을 붙여넣어 Broker 클라이언트 컨테이너를 시작합니다.

아티팩토리 연동 설정 페이지를 새로 고침하여 연결 상태를 확인할 수 있습니다. 연결이 올바르게 설정되면 연결 오류가 발생하지 않습니다.
