# Helm 차트 설치를 위한 서비스 계정

기존 서비스 계정을 사용하려면 설치 명령에 다음 매개변수를 추가합니다:

```
--set serviceAccount.create=false \
--set serviceAccount.name=<ENTER_EXISTING_SERVICE_ACCOUNT> \
```
