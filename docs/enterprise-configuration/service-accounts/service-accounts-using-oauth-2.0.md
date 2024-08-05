# OAuth 2.0을 사용하는 서비스 계정

{% hint style="info" %}
**Release 상태**

OAuth 2.0을 사용하는 서비스 계정은 Snyk REST API를 통해 사용할 수 있습니다. [Snyk API를 사용하여 서비스 계정 관리하기](manage-service-accounts-using-the-snyk-api.md)를 참조하세요.
{% endhint %}

기존 Snyk API 키가 아닌 [OAuth 2.0 `client_credentials` grant flow](https://datatracker.ietf.org/doc/html/rfc6749#section-4.4) 로 인증하는 서비스 계정을 만들 수 있습니다. OAuth 2.0 액세스 토큰은 Snyk API 키와 동일한 방식으로 사용할 수 있지만 짧은 TTL(타임투라이프)의 보안이 추가되었으며 자동으로 새로 고쳐질 수 있습니다.

## 클라이언트 비밀이 포함된 OAuth 2.0

그룹 또는 조직 수준에서 `oauth_client_secret` 서비스 계정을 만들 수 있습니다.

### 클라이언트 비밀 받기(Receive a client secret)

서비스 계정이 생성되면 `client_secret`을 받게 됩니다. 서비스 계정이 생성된 후에는`client_secret`을 다시 볼 수 없습니다. 비밀번호를 잘못 입력한 경우, `client_secret` 를 [돌려서](manage-service-accounts-using-the-snyk-api.md#manage-a-service-account-client-secret-for-your-group) 새 비밀번호를 받을 수 있습니다.

{% hint style="danger" %}
`client_secret`은 서비스 계정을 인증하는 데 사용되므로 절대 공개적으로 공유하지 마세요. 안전하게 비공개로 유지하세요.
{% endhint %}

### OAuth 2.0 액세스 토큰 가져오기

서비스 계정이 생성된 후, `client_secret`을 사용하여 [Snyk OAuth 2.0 token endpoint](https://snykoauth2.docs.apiary.io/#reference/apps/app-tokens/token-exchange-&-refresh)를 통해  `access_token`검색할 수 있습니다. 본문 형식과 `Content-Type` 헤더는 form-urlencoded되어야 합니다.&#x20;

Snyk API 키를 사용하는 것과 같은 방법으로 `access_token`을 사용할 수 있지만, `Authorization: bearer $access_token` 헤더 (Snyk [REST API documentation](https://apidocs.snyk.io/) 참조) 또는 `SNYK_OAUTH_TOKEN` 환경 변수를 Snyk CLI와 함께 사용할 수 있습니다.

`access_token`의 수명은 짧으며 만료되면 새로 고쳐야 합니다. 이 프로세스를 크게 간소화하는 많은 OAuth 2.0 라이브러리를 사용할 수 있습니다.

## 개인 키 JWT가 포함된 OAuth 2.0

또한 서비스 계정은 기존의 `client_secret` 대신 [OIDC Core 1.0 spec](https://openid.net/specs/openid-connect-core-1\_0.html#ClientAuthentication)에 정의된 대로 `client_assertion`의`private_key_jwt` 형식을 인증에 사용할 수도 있습니다.

이는 공개적으로 액세스할 수 있는 [JWKS](https://datatracker.ietf.org/doc/html/rfc7517) 엔드포인트를 호스팅하고 공개 및 비공개 서명 키를 관리할 수 있는 인프라가 있는 고객을 위한 고급 기능입니다. 이 기능은 액세스 토큰 요청을 요청 본문에 단순한 클라이언트 ID와 클라이언트 비밀 쌍이 아닌 서명된 JWT 형식으로 보내도록 요구하여 OAuth 서비스 계정에 대한 보안 계층을 추가합니다.&#x20;

### 개인키 JWT 서비스 계정을 설정하기 위한 전제 조건

서비스 계정을 만들기 전에 다음을 수행해야 합니다:

* 공개 및 비공개 서명 키를 생성합니다.
* 공개 키에 액세스할 수 있는 공개적으로 액세스할 수 있는 JWKS 엔드포인트를 호스팅합니다(`https`여야 함).

고객이 관리하는 서명 키는 마음대로 교체할 수 있습니다.

### 개인 키 JWT 서비스 계정 만들기

그룹 또는 조직 수준에서  [Snyk REST API](manage-service-accounts-using-the-snyk-api.md)를 사용하여 `oauth_private_key_jwt`서비스 계정을 만들 수 있습니다. 서비스 계정을 만들려면 공개적으로 액세스할 수 있는 JWKS 엔드포인트의 URL과 서비스 계정에 할당하려는 역할을 제공해야 합니다.

응답에는 다음 단계에 필요한 `client_id`가 포함됩니다.

### Prepare the JWT signed with a private key

Snyk recommends you prepare a tool or script to build a `private_key_jwt` with the proper claims and sign it with the private signing key you generated. as a prerequisite

The JWT should include the [claims](https://datatracker.ietf.org/doc/html/rfc7519#section-4) outlined in the [Snyk OAuth 2.0 token endpoint](https://snykoauth2.docs.apiary.io/#reference/apps/app-tokens/token-exchange-&-refresh) for the `client_assertion` property. Note that the `aud` claim may vary based on the Snyk instance, for example, `api.snyk.io`, or `api.eu.snyk.io`. For more information, see [Regional hosting and data residency](../../working-with-snyk/regional-hosting-and-data-residency.md).

### 개인 키 JWT 액세스 토큰 가져오기

서비스 계정을 만들고 서명된 JWT가 준비되면  [Snyk OAuth 2.0 token endpoint](https://snykoauth2.docs.apiary.io/#reference/apps/app-tokens/token-exchange-&-refresh)를 사용하여 `access_token` 을 검색할 수 있습니다. 이 액세스 토큰은 Snyk API 키가 사용되는 것처럼 사용할 수 있습니다. 요청 본문에는 다음이 포함되어야 합니다:

* `grant_type: client_credentials`
* `client_assertion_type: private_key_jwt`
* `client_assertion:` `<signed JWT>`

`access_token`의 수명은 짧으며 만료되면 새로 고쳐야 합니다. 이 프로세스를 크게 간소화할 수 있는 많은 OAuth 2.0 라이브러리가 있습니다.
