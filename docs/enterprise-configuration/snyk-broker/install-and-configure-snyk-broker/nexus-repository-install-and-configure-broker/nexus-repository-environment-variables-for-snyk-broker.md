# Nexus 리포지토리- Snyk Broker의 환경 변수

## Nexus 3 구성을 위한 환경 변수

Nexus 3용 Broker 클라이언트를 사용자 지정하려면 다음 환경 변수가 필요합니다:

`BROKER_TOKEN`\
Nexus 연동 설정**(Integrations > Nexus)**에서 얻은 Snyk Broker 토큰입니다.

`BASE_NEXUS_URL`\
Nexus 3 배포의 URL입니다.\
예시:\
`BASE_NEXUS_URL=https://[<username_or_token><password_or_token>]@<your.nexus.hostname>`\
슬래시로 끝나지 않아야 합니다.\
다음 필드는 선택 사항입니다:\
`Auth`: 인증이 필요하지 않은 경우 생략합니다.\
일반 텍스트 또는 두 부분으로 구성된 토큰일 수 있습니다. (`Nexus Pro`)\
인증을 방해할 수 있는 오류를 방지하기 위해 사용자 아이디, 비밀번호 및 토큰을 URL로 인코딩합니다.\
최소 예: `acme.com`\
복잡한 예: `https://alice:mypassword@acme.com`

`BROKER_CLIENT_VALIDATION_URL`\
Broker 클라이언트 `systemcheck` 엔드포인트에서 확인하는 Nexus 유효성 검사 URL입니다.\
Nexus 사용자에게 `auth`이 필요한 경우, `$BASE_NEXUS_URL/service/rest/v1/status/check`를 사용합니다.\
예시:\
`https://<user>:<pass>@<your.nexus.hostname>/service/rest/v1/status/check`)\
그렇지 않으면 `$BASE_NEXUS_URL/service/rest/v1/status`를 사용합니다.\
예시:\
`https://<your.nexus.hostname>/service/rest/v1/status`).

선택 사항입니다.`RES_BODY_URL_SUB`\
이 URL 대체는 **npm/Yarn 통합에 필요**하며 자격 증명이 추가되지 않은 Nexus의 URL에 `/repository`를 추가한 것과 동일합니다.\
예시:\
`https://<your.nexus.hostname>/repository`. 슬래시로 끝나지 않아야 합니다.

## Nexus 2 구성을 위한 환경 변수

Nexus 2용 브로커 클라이언트를 사용자 지정하려면 다음 환경 변수가 필요합니다:

`BROKER_TOKEN` - Nexus 연동 설정**(Integrations > Nexus)**에서 얻은 Snyk Broker 토큰입니다.

`BASE_NEXUS_URL`-Nexus 2 배포의 URL입니다.\
예시:\
`BASE_NEXUS_URL=https://[username_or_token:password_or_token]@acme.com`\
슬래시로 끝나지 않아야 합니다.\
다음 필드는 선택 사항입니다:\
`Auth`: 인증이 필요하지 않은 경우 생략합니다.\
일반 텍스트 또는 두 부분으로 구성된 토큰 중 하나만 입력할 수 있습니다. (`Nexus Pro`).\
인증을 방해할 수 있는 오류를 방지하기 위해 사용자 아이디, 비밀번호 및 토큰을 URL로 인코딩합니다.\
최소 예: `https://acme.com`\
복잡한 예:`https://alice:mypassword@acme.com:`

`RES_BODY_URL_SUB`\
기본 인증 자격 증명이 없는 `https://` and `/nexus/content` 를 포함한 Nexus 인스턴스의 URL입니다. **npm/Yarn 통합에만 필요합니다.** 슬래시로 끝나지 않아야 합니다.

예시:\
`https://acme.com/nexus/content/groups`\
`https://acme.com/nexus/content/repositories`
