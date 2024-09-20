# 아티팩토리 저장소 - Snyk Broker의 환경 변수

아티팩토리 리포지토리용 Broker 클라이언트를 사용자 지정하려면 다음 환경 변수가 필요합니다:

`BROKER_TOKEN` - 아티팩토리 연동 설정(**Integrations > Artifactory**)에서 얻은 Snyk Broker 토큰입니다.&#x20;

`ARTIFACTORY_URL` -아티팩토리 배포의 URL(예:`<yourdomain>.artifactory.com/artifactory`).

다음 필드는 선택 사항입니다:

* _Port_: 포트 번호가 필요하지 않은 경우 생략합니다.
* _Basic auth_: 기본 인증이 필요하지 않은 경우 생략합니다.\
  URL은 사용자 이름과 비밀번호 정보를 모두 인코딩하여 인증을 방해할 수 있는 오류를 방지합니다.
* _Protocol_: 기본값은 `https://`\
  인증서가 없고 `http://` 대신 인스턴스에 필요한 경우에만 지정해야 합니다.

`ARTIFACTORY_URL` 형식(선택적 필드 포함)::\
`[http://][username:password@]hostname[:port]/artifactory`\
예시:\
`http://alice:mypassword@acme.com:8080/artifactory`

선택 사항입니다. `RES_BODY_URL_SUB` - 기본 인증 자격 증명을 포함하지 않는 아티팩토리 인스턴스의 URL(http:// 포함). **npm/Yarn 통합에만 필요**합니다.\
예시:\
`http://acme.com/artifactory`
