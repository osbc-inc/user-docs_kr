# Snyk API를 사용하여 서비스 계정 관리하기

&#x20;[Snyk REST API](https://apidocs.snyk.io/?version=2023-09-07#tag--ServiceAccounts)를 사용하여 서비스 계정을 관리할 수 있습니다.

{% hint style="info" %}
이러한 모든 작업을 수행하려면 특정 권한이 필요합니다([서비스 계정 권한](broken-reference/)을 참조하세요)
{% endhint %}

## 서비스 계정 속성

`id` - 서비스 계정의 ID입니다.

`name` - 서비스 계정의 인간 친화적인 이름입니다.

`auth_type` - 서비스 계정에 대한 인증 전략. 다음 옵션을 사용할 수 있습니다:

* `api_key` - 서비스 계정은 일반 Snyk API 키를 사용합니다.
* `oauth_client_secret` - 서비스 계정은 클라이언트 비밀로 검색되는 [OAuth 2.0 access token](./#service-accounts-using-oauth-2.0)을 사용합니다.
* `oauth_private_key_jwt` - 서비스 계정은 개인 키로 서명된 JWT로 검색되는 [OAuth 2.0 access token](./#service-accounts-using-oauth-2.0)을 사용합니다.

`role_id` - 서비스 계정의 역할로, 계정이 가진 권한을 정의합니다. 사용 가능한 역할은 Snyk API v1 endpoint[ 그룹의 모든 역할 리스트](https://snyk.docs.apiary.io/#reference/groups/list-all-roles-in-a-group/list-all-roles-in-a-group) 사용하여 찾을 수 있습니다.

`jwks_url` - 서명된 JWT 요청을 확인하는 데 사용되는 공개 키를 호스팅하는 JWK의 URL(`https`여야 함)입니다. `auth_type`이 `oauth_private_key_jwt`인 경우에만 필요합니다.

`access_token_ttl_seconds` - 생성된 액세스 토큰이 유효할 시간(초)입니다. 설정하지 않으면 기본값은 1시간입니다. `auth_type` 이`oauth_client_secret` 또는`oauth_private_key_jwt`인 경우에만 필요합니다.

## 그룹 수준 서비스 계정 관리

### 그룹의 서비스 계정 목록 가져오기

**Request**: `GET https://api.snyk.io/rest/groups/{groupId}/service_accounts`

**API 문서** **:** [https://apidocs.snyk.io/?version=2023-09-07#get-/groups/-group\_id-/service\_accounts](https://apidocs.snyk.io/?version=2023-09-07#get-/groups/-group\_id-/service\_accounts)

[페이지가 지정된](../../snyk-api-info/using-snyk-api/links-for-pagination-in-snyk-rest-api.md) 이 호출은 각각 서비스 계정을 설명하는 객체 배열을 반환합니다.

### 그룹을 위한 서비스 계정 만들기

**Request**: `POST https://api.snyk.io/rest/groups/{groupId}/service_accounts`

**API 문서:** [https://apidocs.snyk.io/?version=2023-09-07#post-/groups/-group\_id-/service\_accounts](https://apidocs.snyk.io/?version=2023-09-07#post-/groups/-group\_id-/service\_accounts)

이 호출은 새 서비스 계정을 만듭니다. 서비스 계정이 사용할 수 있는 권한을 정의하는 JSON 형식의 요청 본문에 `role_id`를 전달합니다. 이 `role_id`는 Snyk API v1 endpoint [그룹의 모든 역할 list](https://snyk.docs.apiary.io/#reference/groups/list-all-roles-in-a-group/list-all-roles-in-a-group)를 사용하여 찾을 수 있습니다. 역할은 여러 서비스 계정에 재사용할 수 있습니다.

### 그룹에서 서비스 계정 받기

**Request**: `GET https://api.snyk.io/rest/groups/{groupId}/service_accounts/{serviceAccountId}`

**API 문서:** [https://apidocs.snyk.io/?version=2023-09-07#get-/groups/-group\_id-/service\_accounts/-serviceaccount\_id-](https://apidocs.snyk.io/?version=2023-09-07#get-/groups/-group\_id-/service\_accounts/-serviceaccount\_id-)

이 호출은 특정 서비스 계정을 설명하는 세부 정보를 반환합니다.

### 그룹에서 서비스 계정 업데이트

**Request**: `PATCH https://api.snyk.io/rest/groups/{groupId}/service_accounts/{serviceAccountId}`

**API 문서:** [https://apidocs.snyk.io/?version=2023-09-07#patch-/groups/-group\_id-/service\_accounts/-serviceaccount\_id-](https://apidocs.snyk.io/?version=2023-09-07#patch-/groups/-group\_id-/service\_accounts/-serviceaccount\_id-)

이 호출은 특정 서비스 계정의 세부 정보(현재 서비스 계정의 이름)를 업데이트합니다

### 그룹에서 서비스 계정 삭제

**Request**: `DELETE https://api.snyk.io/rest/groups/{groupId}/service_accounts/{serviceAccountId}`

**API 문서:** [https://apidocs.snyk.io/?version=2023-09-07#delete-/groups/-group\_id-/service\_accounts/-serviceaccount\_id-](https://apidocs.snyk.io/?version=2023-09-07#delete-/groups/-group\_id-/service\_accounts/-serviceaccount\_id-)

이 호출은 지정된 서비스 계정을 영구적으로 삭제하고 해당 자격 증명을 해지합니다.

### 그룹의 서비스 계정 클라이언트 비밀 관리하기

**Request**: `POST https://api.snyk.io/rest/groups/{groupId}/service_accounts/{serviceAccountId}/secrets`

**API 문서:** [https://apidocs.snyk.io/?version=2023-09-07#post-/groups/-group\_id-/service\_accounts/-serviceaccount\_id-/secrets](https://apidocs.snyk.io/?version=2023-09-07#post-/groups/-group\_id-/service\_accounts/-serviceaccount\_id-/secrets)

이 호출을 통해 `oauth_client_secret`서비스 계정의 클라이언트 비밀번호를 관리할 수 있습니다. 다음 작업을 수행할 수 있습니다:

* `create` - 새 클라이언트 비밀번호를 생성합니다. 서비스 계정에는 한 번에 최대 2개의 활성 비밀번호를 가질 수 있습니다.
* `delete` - 기존 클라이언트 비밀을 삭제합니다. 이를 위해서는 요청 본문에 `client_secret` 을 입력해야 합니다. 기존 클라이언트 비밀을 삭제하면 해당 비밀이 무효화됩니다. 서비스 계정에는 활성 비밀이 하나 이상 있어야 하며, 마지막 비밀로 delete를 호출하면 실패합니다.
* `replace` - 기존 클라이언트 비밀을 삭제하고 동시에 새 비밀을 생성합니다. 이 옵션은 `client_secret`이 손상된 경우에 사용하는 것이 좋습니다.

## 조직 수준 서비스 계정 관리

### 조직의 서비스 계정 목록 가져오기

**Request**: `GET https://api.snyk.io/rest/orgs/{orgId}/service_accounts`

**API 문서:** [https://apidocs.snyk.io/?version=2023-09-07#get-/orgs/-org\_id-/service\_accounts](https://apidocs.snyk.io/?version=2023-09-07#get-/orgs/-org\_id-/service\_accounts)

[페이지가 지정된](../../snyk-api-info/using-snyk-api/links-for-pagination-in-snyk-rest-api.md) 이 호출은 각각 서비스 계정을 설명하는 객체 배열을 반환합니다.

### 조직을 위한 서비스 계정 만들기

**Request**: `POST https://api.snyk.io/rest/orgs/{orgId}/service_accounts`

**API 문서:** [https://apidocs.snyk.io/?version=2023-09-07#post-/orgs/-org\_id-/service\_accounts](https://apidocs.snyk.io/?version=2023-09-07#post-/orgs/-org\_id-/service\_accounts)

이 호출은 새 서비스 계정을 만듭니다. 서비스 계정이 사용할 수 있는 권한을 정의하는 JSON 형식의 요청 본문에 `role_id`를 전달합니다. 이 `role id`는  Snyk API v1 endpoint [그룹의 모든 역할 list](https://snyk.docs.apiary.io/#reference/groups/list-all-roles-in-a-group/list-all-roles-in-a-group) 사용하여 찾을 수 있습니다. 역할은 여러 서비스 계정에 재사용할 수 있습니다.

### Get a service account from your Organization

**Request**: `GET https://api.snyk.io/rest/orgs/{orgId}/service_accounts/{serviceAccountId}`

**API 문서:** [https://apidocs.snyk.io/?version=2023-09-07#get-/orgs/-org\_id-/service\_accounts/-serviceaccount\_id-](https://apidocs.snyk.io/?version=2023-09-07#get-/orgs/-org\_id-/service\_accounts/-serviceaccount\_id-)

This call returns details describing a specific service account.

### Update a service account in your Organization

**Request**: `PATCH https://api.snyk.io/rest/orgs/{orgId}/service_accounts/{serviceAccountId}`

**API 문서:** [https://apidocs.snyk.io/?version=2023-09-07#patch-/orgs/-org\_id-/service\_accounts/-serviceaccount\_id-](https://apidocs.snyk.io/?version=2023-09-07#patch-/orgs/-org\_id-/service\_accounts/-serviceaccount\_id-)

This call updates the details of a specific service account, at this time, the name of the service account.

### Delete a service account from your Organization

**Request**: `DELETE https://api.snyk.io/rest/orgs/{orgId}/service_accounts/{serviceAccountId}`

**API 문서:** [https://apidocs.snyk.io/?version=2023-09-07#delete-/orgs/-org\_id-/service\_accounts/-serviceaccount\_id-](https://apidocs.snyk.io/?version=2023-09-07#delete-/orgs/-org\_id-/service\_accounts/-serviceaccount\_id-)

This call permanently deletes the specified service account.

### Manage a service account client secret for your Organization

**Request**: `POST https://api.snyk.io/rest/orgs/{orgId}/service_accounts/{serviceAccountId}/secrets`

**API 문서:** [https://apidocs.snyk.io/?version=2023-09-07#post-/orgs/-org\_id-/service\_accounts/-serviceaccount\_id-/secrets](https://apidocs.snyk.io/?version=2023-09-07#post-/orgs/-org\_id-/service\_accounts/-serviceaccount\_id-/secrets)

This call allows you to manage the client secret for `oauth_client_secret` service accounts. You can perform the following operations:

* `create` - generate a new client secret. A service account can have a maximum of two active secrets at a time.
* `delete` - delete an existing client secret. This requires putting `client_secret` in the request body. Deleting an existing client secret would render it invalid. A service account must have at least one active secret; calling delete with your last secret will fail.
* `replace` - simultaneously delete the existing client secret and generate a new secret. This option is recommended if your `client_secret` is compromised.
