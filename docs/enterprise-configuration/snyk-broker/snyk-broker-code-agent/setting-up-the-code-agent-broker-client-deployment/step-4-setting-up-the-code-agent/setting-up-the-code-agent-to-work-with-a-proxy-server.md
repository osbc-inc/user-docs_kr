# 프록시 서버와 함께 작동하도록 코드 에이전트 설정하기

{% hint style="info" %}
환경 변수(-e와 함께 제공됨)는 대소문자를 구분합니다. 이 페이지에 정의된 대로 제공되었는지 확인하세요.
{% endhint %}

프록시를 사용하는 인프라에서 코드 에이전트 - Broker 클라이언트 배포를 사용하려면 코드 에이전트의 `docker run` 명령에 다음 환경 변수를 추가하세요:

```
-e HTTP_PROXY=http://my.proxy.address:<port_no.> \
-e HTTPS_PROXY=http://my.proxy.address:<port_no.>
```

프록시에 사용자 이름 및 비밀번호 인증이 필요한 경우 다음 환경 변수를 추가하세요:

```
-e PROXY_AUTH=userID:userPass
```

또한 이러한 환경 변수를 Broker 클라이언트 컴포넌트에 추가하고 코드 에이전트를 우회하는 명령을 추가합니다.

프록시와 함께 Docker 컨테이너를 사용하는 방법에 대한 자세한 내용은 [프록시 서버를 사용하도록 Docker 구성하기](https://docs.docker.com/network/proxy/)를 참조하세요.&#x20;

## 사용자 지정 인증서

사용자 지정 인증서(HTTPS)로 보안된 프록시와 함께 코드 에이전트를 사용하려면 코드 에이전트의 `docker run` 명령에 다음 환경 변수를 추가하세요:

```
-e HTTP_PROXY=http://my.proxy.address:<port_no.> \
-e HTTPS_PROXY=https://my.proxy.address:<port_no.>
```

다음 단계는 실행 중인 Code Agent 버전에 따라 다릅니다.`latest(최신)` 태그를 사용하는 경우 가장 최신 버전의 이미지를 찾습니다:

* 로컬 이미지의 `digest`를 [Docker Hub 코드 에이전트 태그](https://hub.docker.com/r/snyk/code-agent/tags)와 비교하세요:`docker images snyk/code-agent --digest`
* 로컬 이미지가 빌드되기 전에 릴리스된 `x.y.z` 형식의 다음 이미지 태그를 찾습니다.

## 버&#xC804;**`1.18.0`** 이상

사용자 지정 인증 기관을 신뢰하려면 둘 중 하나가 있어야 합니다:

* 단일 인증 기관(`PEM`으로 인코딩) 또는
* 여러 인증 기관이 포함된 디렉토리(`PEM`으로 인코딩)

단일 인증서를 신뢰하려면 코드 에이전트의 `docker run` 명령에 다음 인수를 추가합니다:

```
-v local/path/to/ca.pem:/etc/certs/ca.pem \
-e GIT_SSL_CAINFO='/etc/certs/ca.pem'
```

인증서 디렉터리를 신뢰하려면 코드 에이전트의 `docker run` 명령에 다음 인수를 추가합니다:

```
-v local/path/to/certdirectory:/etc/certs
-e GIT_SSL_CAPATH='/etc/certs'
```

## 버&#xC804;**`1.16.0`** \~**`1.17.0`**

앞의 단계에 따라 코드 에이전트의 `docker run`명령에 다음 인수를 추가합니다:

```
-e CODE_AGENT_GIT_CLI=true
```

## 버&#xC804;**`1.15.2`** 이하

코드 에이전트 `1.15.2` 이하는 사용자 지정 인증 기관의 신뢰를 지원하지 않으며, 대신 모든 인증서를 신뢰하는 모드로 실행해야 합니다.

코드 에이전트의 `docker run` 명령에 다음 환경 변수를 추가합니다:

```
-e NODE_TLS_REJECT_UNAUTHORIZED=0
```
