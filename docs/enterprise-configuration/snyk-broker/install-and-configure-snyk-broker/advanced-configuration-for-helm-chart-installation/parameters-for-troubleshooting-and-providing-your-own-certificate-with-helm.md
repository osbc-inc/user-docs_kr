# Helm으로 문제를 해결하고 자체 인증서를 제공하기 위한 매개변수

SSL 검사 문제를 해결하려면, `tlsRejectUnauthorized` 매개 변수를 `disable`하도록 설정할 수 있습니다.

```
--set tlsRejectUnauthorized=disable
```

자체 인증서(자체 CA가 서명)를 제공하려면 `caCert`매개변수에 파일 이름을 전달하면 된다. 파일은 Helm 차트 디렉터리 내에 있어야 한다.

```
--set caCert=<CERT_NAME>
```

Broker를 HTTPS 서버로 실행하려면 파일 `httpsCert` 및`httpsKey` 매개 변수에 전달하면 된다. 파일은 Helm 차트 디렉터리 내에 있어야 한다.

```
--set httpsCert=<CERT_NAME> --set httpsKey=<CERT_KEY>
```

자체 인증서 사용에 대한 자세한 내용은[Docker용 내부 인증서를 사용한 백엔드 요청](../advanced-configuration-for-snyk-broker-docker-installation/backend-requests-with-an-internal-certificate-for-docker.md) 및[Docker를 사용하는 Broker 클라이언트용 HTTPS](../advanced-configuration-for-snyk-broker-docker-installation/https-for-broker-client-with-docker.md)를 참조하세요.
