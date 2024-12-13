# Broker 이미지 서명 확인

버전 4.169.1부터 모든 브로커 컨테이너 이미지는 Cosign을 사용하여 서명됩니다.

Cosign은 컨테이너 서명 및 검증을 위한 도구입니다. Cosign은 오픈 컨테이너 이니셔티브(OCI) 레지스트리에 저장합니다.

Cosign은 간단하고 효율적인 서명 및 검증 방법을 제공하여 컨테이너 이미지의 보안을 강화하도록 설계되었습니다. 이는 디지털 서명 개념을 활용하여 개인 키로 컨테이너 이미지에 서명하면 수신자가 해당 공개 키를 사용하여 서명을 확인할 수 있습니다.

## Broker 이미지 서명 확인을 위한 전제 조건

[Cosign](https://docs.sigstore.dev/system_config/installation/) 버전 2.2.0 이상을 [설치](https://docs.sigstore.dev/system_config/installation/)해야 합니다.

## 서명된 컨테이너 이미지 확인

서명된 이미지를 확인하려면 기본 제공된 `cosign verify` 명령을 사용해야 합니다.

확인 단계를 수행하기 위해 Broker 컨테이너 이미지를 가져올 필요는 없습니다.

```
$ cosign verify --key cosign.pub snyk/broker:4.169.1-github-com

Verification for index.docker.io/snyk/broker:4.169.1-github-com --
The following checks were performed on each of these signatures:
  - The cosign claims were validated
  - Existence of the claims in the transparency log was verified offline
  - The signatures were verified against the specified public key

[{"critical":{"identity":{"docker-reference":"index.docker.io/snyk/broker"},"image":{"docker-manifest-digest":"sha256:a2ff856b180a532c3e31a90b9788cad567fa05d78c84bccc637de54c6f46ebf2"},"type":"cosign container image signature"},"optional":{"Bundle":{"SignedEntryTimestamp":"MEUCIEOmElvKK0eC/hvpM9SE66RAekcV6DpF6NSO4Gz5aftrAiEAlQY8lKe1RUqYtCK1WRwWhWT/f/PvyBTJC8qBjgU20kU=","Payload":{"body":"eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJjOTE2NDQ1N2YxMDA0NTQxNWNlMjBlN2I3YjNmYjg4YjZmMmNhNzI4MDNkODY4NTk0ZDhlY2UzMGJkYTFiZjQ4In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUNRQVp6VVdqbkNFai9GZkpxTGU4YVdoYXhacWJzZnZTc21JNXRiRzZuRmdBSWhBTFgyMWVLRHl6OXNqWHQrVStVZUZNTUFyN1oyV09Gd0k1b1oxclc0dlJBUCIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCUVZVSk1TVU1nUzBWWkxTMHRMUzBLVFVacmQwVjNXVWhMYjFwSmVtb3dRMEZSV1VsTGIxcEplbW93UkVGUlkwUlJaMEZGWkNzeWJVVlhlVVJyT0VOdGJUQkRSREZhT0dwamMxaEhZVkV5YVFwelREaHdlRWh5ZDI5SlNEUkVlRzFrZVVveWJucDNWMkY0V1daelpscE5OazV2UTFKV2MyZFpRVlpsTlVkQ2FFWmljalpvZW1OcU5XZDNQVDBLTFMwdExTMUZUa1FnVUZWQ1RFbERJRXRGV1MwdExTMHRDZz09In19fX0=","integratedTime":1698788303,"logIndex":46732614,"logID":"c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"}},"tag":"4.169.1-github-com"}}]
```

## Broker Cosign 공개키

```
-----BEGIN PUBLIC KEY-----
MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEd+2mEWyDk8Cmm0CD1Z8jcsXGaQ2i
sL8pxHrwoIH4DxmdyJ2nzwWaxYfsfZM6NoCRVsgYAVe5GBhFbr6hzcj5gw==
-----END PUBLIC KEY-----
```
