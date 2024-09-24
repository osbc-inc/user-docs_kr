# Kubernetes 시크릿 및 Helm 차트 설치

API 토큰과 비밀번호는 Kubernetes 시크릿을 사용한다. 다음 형식으로 생성된 기존 시크릿을 사용할 수 있습니다.

## Helm 차트 설치용 Broker 토큰

```
apiVersion: v1
kind: Secret
metadata:
  name: <ENTER_SCM_TYPE>-broker-token
  labels:
    app: <ENTER_SCM_TYPE>-broker-token
type: Opaque
data:
  <ENTER_SCM_TYPE>-broker-token-key: <BASE64_ENCODED_SECRET>
```

## Helm 차트 설치용 SCM 토큰

```
apiVersion: v1
kind: Secret
metadata:
  name: <ENTER_SCM_TYPE>-token
type: Opaque
data:
  <ENTER_SCM_TYPE>-token-key: <BASE64_ENCODED_SECRET>
```
