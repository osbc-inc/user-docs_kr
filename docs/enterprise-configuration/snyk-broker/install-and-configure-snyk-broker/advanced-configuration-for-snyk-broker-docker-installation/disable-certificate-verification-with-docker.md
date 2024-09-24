# Docker로 인증서 확인 사용 안 함

예를 들어 자체 서명 인증서의 경우 인증서 확인을 사용하지 않으려면 **docker 실행** 명령에 다음을 추가합니다:

```
-e NODE_TLS_REJECT_UNAUTHORIZED=0
```
