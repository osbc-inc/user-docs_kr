# Docker용 내부 인증서를 사용한 백엔드 요청

기본적으로 Broker 클라이언트는 백엔드 시스템에 HTTPS 연결을 설정합니다: GitHub, BitBucket, Jira 또는 기타. 백엔드 시스템에서 내부 인증서(자체 인증 기관(CA)에서 서명)를 제공하는 경우, 브로커 클라이언트에 CA 인증서를 제공할 수 있습니다.

예를 들어, CA 인증서가`./private/ca.cert.pem`에 있는 경우, 폴더를 마운트하고 `NODE_EXTRA_CA_CERT` 환경 변수를 사용하여 Docker 컨테이너에 제공하세요. Bitbucket의 경우 다음 예제를 참조하세요:

```
docker run --restart=always \
           -p 8000:8000 \
           -e BROKER_TOKEN=secret-broker-token \
           -e BITBUCKET_USERNAME=username \
           -e BITBUCKET_PASSWORD=password \
           -e BITBUCKET=your.bitbucket-server.domain.com \
           -e BITBUCKET_API=your.bitbucket-server.domain.com/rest/api/1.0 \
           -e PORT=8000 \
           -e NODE_EXTRA_CA_CERTS=/private/ca.cert.pem \
           -v /local/path/to/private:/private \
       snyk/broker:bitbucket-server
```

{% hint style="info" %}
**최근 변경 사항**\
사용자 지정 CA 인증서 명령이 최근에 변경되었습니다. `CA_CERT`는 더 이상 사용되지 않으며`NODE_EXTRA_CA_CERTS`로 대체해야 합니다.
{% endhint %}

이것은 백엔드 시스템에 대한 모든 요청에 대해 기본 CA 인증서 목록을 완전히 대체하므로 백엔드 시스템에서 사용하는 인증서에 필요한 전체 체인이어야 합니다.

`PEM`형식이어야 하며, `DER`은 지원되지 않습니다. 지원되는 인증서 유형은 다음과 같습니다:

* `TRUSTED CERTIFICATE`
* `X509 CERTIFICATE`
* `CERTIFICATE`

다음은 예시입니다.

```
-----BEGIN CERTIFICATE-----
<base64-encoded certificate>
-----END CERTIFICATE----
-----BEGIN CERTIFICATE-----
<base64-encoded certificate>
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
<base64-encoded certificate>
-----END CERTIFICATE-----
```
