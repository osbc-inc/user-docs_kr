# 예: Google Workspace에 대한 커스텀 매핑 설정

다음은 Google Workspace 사용자 지정 SAML 연결에 대한 역할의 [사용자 지정 매핑 옵션](./)을 위해 사용자 지정 매핑 옵션을 사용하는 방법을 보여 줍니다.

자세한 내용과 지침은 [Google 문서인, Manage Custom User Fields](https://developers.google.com/admin-sdk/directory/v1/guides/manage-schemas)를 참조하세요.

API를 사용하려면 Google Workspace 관리 영역에 로그인하여 다음 명령을 실행하거나 유연성 및 자동화를 위해 원하는 API 클라이언트 또는 스크립트와 함께 API를 사용하세요. API 자격 증명을 생성하려면, Google 문서 [Create access credentials](https://developers.google.com/workspace/guides/create-credentials)를 참조하세요.

## 사용자 스키마 추가하기

[schema endpoint](https://developers.google.com/admin-sdk/directory/reference/rest/v1/schemas/insert)를 사용하여, 사용자와 연결할 수 있는 스키마를 추가합니다. 다음은 스키마 예시입니다. 이 스키마를 사용하면 사용자에 대한 SAML 페이로드에서 원하는 사용자 지정 역할 매핑을 노출할 수 있습니다.

```json
{
   "fields":
   [
     {
       "fieldName": "roles",
       "fieldType": "STRING",
       "readAccessType": "ADMINS_AND_SELF",
       "multiValued": true,
       "displayName": "roles"
     }
   ],
   "schemaName": "Snyk-SSO"
 }
```

## 사용자 프로필 수정하기

사용자 [API endpoint](https://developers.google.com/admin-sdk/directory/reference/rest/v1/users/patch)를 사용하여 원하는 역할을 사용자 프로필에 첨부합니다. 참조를 위해 페이로드 예시가 아래에 나와 있습니다.

```json
{
 "customSchemas": {
   "Snyk-SSO": {
     "roles": [
       {
         "value": "snyk-org1-admin"
       },
       {
         "value": "snyk-org2-admin"
       }
     ]
   }
 }
}
```

## SAML 속성 수정

SAML 페이로드에서 이러한 역할을 노출하려면, SAML 속성 매핑에서 속성을 수정해야 합니다:

1.  Google Workspace 관리 영역에 로그인하고, **Apps**으로 이동한 다음 **Web and mobile apps**으로 이동하여 애플리케이션을 엽니다.

    <figure><img src="../../../.gitbook/assets/x1.png" alt="Open Google SAML app"><figcaption><p>Google SAML 앱 열기</p></figcaption></figure>
2. **SAML attribute mapping**을 클릭한 다음 **ADD MAPPING**를 클릭합니다.
3. **Select field**을 클릭하고 **Snyk-SSO - roles**를 찾을 때까지 스크롤하여 선택합니다.
4.  **App attributes** 값 필드에, **roles**입력하고 **Save**을 클릭합니다.

    <figure><img src="../../../.gitbook/assets/x2 (1).png" alt="Adding custom mapping app attribute"><figcaption><p>사용자 지정 매핑 앱 속성 추가</p></figcaption></figure>

그런 다음 사용자로 로그인하고 Snyk 담당자가 SAML 페이로드의 유효성을 검사하고 Snyk 백엔드에서 설정을 완료하도록 합니다.
