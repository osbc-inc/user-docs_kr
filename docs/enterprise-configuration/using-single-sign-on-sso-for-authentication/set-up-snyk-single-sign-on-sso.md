# Snyk SSO(Single Sign-On) 설정

개발자와 팀이 기존 SSO 공급자를 통해 Snyk에 쉽게 액세스할 수 있도록 SSO(Single Sign-On)를 설정하세요.

Snyk와 ID 공급자 간에 신뢰를 구축하는 데 필요한 정보는 사용 중인 SSO 유형에 따라 다릅니다.

새 사용자가 할당될 위치를 나타내는 그룹과 조직이 하나 이상 있는지 확인하세요. 자세한 내용은 [Manage Groups and Organizations](../../snyk-admin/manage-groups-and-organizations/)를 참조하세요.

{% hint style="info" %}
다음 섹션에서 확인된 필요한 정보를 수집한 후 SSO 설정을 요청하기 위한 지원 티켓을 만드세요.

또는 그룹 관리자가 Snyk Single Sign-On을 구성할 수 있습니다. 단계는 [Self-Serve Single Sign-On (SSO)](self-serve-single-sign-on-sso/) 를 참조하세요.
{% endhint %}

## SSO 개요

IdP(ID 공급자)와 Snyk 간에 신뢰를 설정하는 프로세스에는 SSO 관리자와 Snyk 지원 간에 조정되는 몇 가지 단계가 필요합니다.

* ID 공급자 플랫폼에서 Snyk 환경 및 사용자 속성에 대한 세부 정보를 입력합니다.
* IdP의 세부정보를 Snyk에 제공하세요.
* 테스트할 사용자를 설정하고 해당 사용자의 사용자 이름과 비밀번호를 Snyk에 보냅니다.
* Snyk에서 제공하는 링크를 사용하여 페이로드를 생성하세요.
* Snyk이 연결을 완료한 후 로그인 프로세스가 올바르게 작동하는지 확인하세요.

사용자는 로그인할 때 Snyk에 프로비저닝됩니다. 초대가 필요한 경우, 관리자가 사용자를 적절한 조직에 추가할 때까지 사용자는 조직 목록만 볼 수 있습니다.

Snyk와 회사 네트워크 모두에서 SSO가 구성되면 Snyk, Auth0(Snyk 대신) 및 네트워크와 신뢰 관계가 설정됩니다. 모든 민감한 데이터는 사용자 로그인을 활성화할 목적으로만 암호화되어 Auth0에 저장됩니다.

각 유형의 SSO 연결에는 ID 공급자와 Snyk 간의 신뢰를 구축하기 위한 서로 다른 세부 정보가 필요합니다. 다음 섹션에서는 이러한 세부정보를 설명합니다. 자세한 내용은 이 기사 마지막 부분의 리소스 섹션에 있는 워크시트에도 포함되어 있습니다.

## SSO용 SAML 설정

Snyk과 신뢰를 구축하려면, ID 공급자에 Entity ID, ACS(Assertion Consumer Service) URL 및 서명 인증서를 추가하세요.

* **Entity ID**는 Snyk를 SAML Entity 또는 서비스 제공업체로 고유하게 식별하는 URL입니다. (참고: **기본 Entity ID는** 기본값이 설정되어 있지 않으므로 수동으로 **확인해야 합니다.**)
* **Assertion Consumer Service (ACS)**는 네트워크 사용자와 Snyk 간의 통신을 활성화하기 위해 ID 공급자의 요청을 수신하는 Snyk 네트워크의 엔드포인트입니다. 이 URL을 Reply URL이라고도 합니다.
* **서명 인증서(Signing certificate)**는 신뢰 관계를 유지하는 데 필요한 서버에 저장된 Snyk 인증서입니다. 인증에 필요한 암호화 키가 포함되어 있습니다.

다음 세부 정보를 사용하여 ID 공급자(IdP)와의 연결을 설정하세요.

| **Details**                                    | **설명**                                                                                                                                                                      |
| ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entity ID                                      | **urn:auth0:snyk:saml-{group-name-normalized}**                                                                                                                             |
| Entity ID (Snyk EU Tenant Customers)           | **urn:auth0:snyk-mt-eu-prod-1:saml-{group-name-normalized}**                                                                                                                |
| Entity ID (Snyk AU Tenant Customers)           | **urn:auth0:snyk-mt-au-prod-1:saml-{group-name-normalized}**                                                                                                                |
| ACS URL                                        | [https://snyk.auth0.com/login/callback?connection=saml-](https://snyk.auth0.com/login/callback?connection=saml-)**{group-name-normalized}**                                 |
| ACS URL (Snyk EU Tenant Customers)             | [https://snyk-mt-eu-prod-1.eu.auth0.com/login/callback?connection=saml-](https://snyk-mt-eu-prod-1.eu.auth0.com/login/callback?connection=saml-)**{group-name-normalized}** |
| ACS URL (Snyk AU Tenant Customers)             | [https://snyk-mt-au-prod-1.au.auth0.com/login/callback?connection=saml](https://snyk-mt-au-prod-1.au.auth0.com/login/callback?connection=saml)-**{group-name-normalized}**  |
| Signing certificate                            | [https://snyk.auth0.com/pem](https://snyk.auth0.com/pem)                                                                                                                    |
| Signing certificate (Snyk EU Tenant Customers) | [https://snyk-mt-eu-prod-1.eu.auth0.com/pem?cert=connection](https://snyk-mt-eu-prod-1.eu.auth0.com/pem?cert=connection)                                                    |
| Signing certificate (Snyk AU Tenant Customers) | [https://snyk-mt-au-prod-1.au.auth0.com/pem?cert=connection)](https://snyk-mt-au-prod-1.au.auth0.com/pem?cert=connection\))                                                 |

{% hint style="info" %}
**{group-name-normalized}**를 Snyk 그룹 이름으로 바꾸세요. 그룹 이름에 공백이 포함된 경우 대시로 바꾸세요. 예를 들어, 그룹 이름이 `Your Company Group`인 경우,  **{group-name-normalized}** 값은 **your-company-group**입니다.
{% endhint %}

ID 공급자의 정보를 Snyk에 매핑하려면, 동일한 대소문자 및 철자를 사용하여 다음과 같이 사용자 속성의 이름을 지정하세요.

| **속성**   | **설명**             |
| -------- | ------------------ |
| email    | 사용자 이메일 주소         |
| name     | 인증할 사람의 이름         |
| username | ID 제공업체의 개인 사용자 이름 |

사용자 속성이 일치하지 않으면, SSO에 대한 Snyk을 구성하는데 시간이 더 소요됩니다.

## Snyk에 제공할 SAML 정보

ID 제공자로부터 다음 정보를 얻으십시오. 서비스 제공자 측에서 신뢰를 구축하려면 이 정보를 Snyk에 제공하세요.

| Information(정보)               | 설명                                                                                                                                                                                                                                                                                                                  |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Sign-in URL                   | ID 공급자 로그인 페이지의 URL                                                                                                                                                                                                                                                                                                 |
| X509 Signing Certificate      | Base64 형식으로 인코딩된 ID 공급자 공개 키                                                                                                                                                                                                                                                                                        |
| Sign-out URL                  | <p>선택사항이지만 권장됩니다 -</p><p>사용자가 Snyk에서 로그아웃할 때마다 redirect 되는 URL</p>                                                                                                                                                                                                                                                  |
| User ID attribute             | <p>선택적 기본값은<strong>http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier</strong><br><br><strong>중요:</strong> T이 값은 Snyk 사용자를 고유하게 식별하며, 변경되면 중복 사용자가 생성됩니다. ID 공급자를 변경한 후 중복 사용자가 표시되면 Snyk 지원팀에 <a href="https://support.snyk.io/hc/en-us/requests/new">submit a request </a>하여 중복 사용자를 제거하세요.</p> |
| Protocol binding              | HTTP-POST가 권장되며, HTTP-Redirect도 지원됩니다.                                                                                                                                                                                                                                                                              |
| IdP initiated flow supported? | Idp에서 시작된 흐름은 보안 위험을 수반하므로 권장되지 않습니다. 활성화하기 전에 위험을 인지했는지 확인하십시오.                                                                                                                                                                                                                                                    |
| Email domains and subdomains  | SSO에 액세스해야 하는 이메일 도메인 및 하위 도메인                                                                                                                                                                                                                                                                                      |

##

## SSO용 OpenID Connect(OIDC) 설정

{% hint style="info" %}
IdP(또는 issuer URL)는 공개적으로 연결할 수 있어야 합니다.If these cannot be made public then SAML should be used rather than OIDC
{% endhint %}

ID 공급자와 Snyk 간의 연결에 OIDC를 사용하는 경우, ID 공급자에 콜백/리디렉션 URI 및 OAuth 부여 유형을 추가하여 Snyk와의 신뢰를 설정하세요.

| Information(정보)                                   | 설명                                                                                                             |
| ------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Callback/Redirect URIs                            | [https://snyk.auth0.com/login/callback](https://snyk.auth0.com/login/callback)                                 |
| Callback/Redirect URIs (Snyk EU Tenant Customers) | [https://snyk-mt-eu-prod-1.eu.auth0.com/login/callback](https://snyk-mt-eu-prod-1.eu.auth0.com/login/callback) |
| Callback/Redirect URIs (Snyk AU Tenant Customers) | [https://snyk-mt-au-prod-1.au.auth0.com/login/callback](https://snyk-mt-au-prod-1.au.auth0.com/login/callback) |
| OAuth Grant Type                                  | Implicit (or Authorization Code)                                                                               |

## Snyk에 제공할 OIDC 정보

ID 제공자로부터 다음 정보를 얻으십시오. 서비스 제공자 측에서 신뢰를 구축하려면 이 정보를 Snyk에 제공하세요.

| Information(정보)              | 설명                                                           |
| ---------------------------- | ------------------------------------------------------------ |
| Issuer URL                   | 연결하려는 OpenID Connect 공급자의 검색 문서 URL입니다. 공개적으로 접근할 수 있어야 합니다. |
| Client ID                    | 인증 서버의 고유한 공개 식별자                                            |
| Client Secret                | IdP가 암시적 부여 유형을 허용하지 않는 경우에만 필요합니다.                          |
| Email domains and subdomains | SSO에 액세스해야 하는 이메일 도메인 및 하위 도메인                               |

## Azure AD를 SSO로 설정(앱 등록/OIDC를 통해)

ID 공급자와 Snyk 간의 연결에 Azure AD를 사용하는 경우, ID 공급자에 Redirect URI를 추가하여 Snyk와의 신뢰를 설정해야 합니다.

{% hint style="info" %}
인증할 때 SCM 사용자 계정 이름 대신 Azure AD 이름을 사용하세요. 그렇지 않으면 연결 오류가 발생할 수 있습니다.
{% endhint %}

| Information(정보)                          | 설명                                                                                                             |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Redirect URIs                            | [https://snyk.auth0.com/login/callback](https://snyk.auth0.com/login/callback)                                 |
| Redirect URIs (Snyk EU Tenant Customers) | [https://snyk-mt-eu-prod-1.eu.auth0.com/login/callback](https://snyk-mt-eu-prod-1.eu.auth0.com/login/callback) |
| Redirect URIs (Snyk AU Tenant Customers) | [https://snyk-mt-au-prod-1.au.auth0.com/login/callback](https://snyk-mt-au-prod-1.au.auth0.com/login/callback) |

## Snyk에 제공할 Azure AD 정보

ID 제공자로부터 다음 정보를 얻으십시오. 서비스 제공자 측에서 신뢰를 구축하려면 이 정보를 Snyk에 제공하세요.

| Information(정보)           | 설명                                                      |
| ------------------------- | ------------------------------------------------------- |
| Client ID                 | 인증 서버의 고유한 공개 식별자                                       |
| Client Secret             | 승인된 요청자에게 토큰을 부여하는 승인의 비밀입니다.                           |
| Microsoft Azure AD Domain | 개요에서 생성한 Snyk 앱에서 찾을 수 있는, 디렉터리(tenant) ID에 표시되는 숫자와 문자 |

## ADFS를 SSO로 설정

ID 공급자와 Snyk 간의 연결을 위해 ADFS(Active Directory Federation Service)를 사용하는 경우, ID 공급자에 영역 식별자, 콜백 URL 및 서명 인증서를 추가하여 Snyk와의 신뢰를 설정하세요. 자세한 내용은[Connecting Auth0 to an ADFS server (video)](https://www.youtube.com/watch?v=ICW6sGP9ht8)을 참조하세요.

| **Information**(정보)                     | **설명**                                                                                                                                     |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Realm Identifier                        | urn:auth0:snyk                                                                                                                             |
| EU Realm Identifier                     | urn:auth0:snyk-mt-eu-prod-1                                                                                                                |
| AU Realm Identifier                     | urn:auth0:snyk-mt-au-prod-1                                                                                                                |
| Callback URL                            | [https://snyk.auth0.com/login/callback](https://snyk.auth0.com/login/callback)                                                             |
| Callback URL (Snyk EU Tenant Customers) | [https://snyk-mt-eu-prod-1.eu.auth0.com/login/callback](https://snyk-mt-eu-prod-1.eu.auth0.com/login/callback)                             |
| Callback URL (Snyk AU Tenant Customers) | [https://snyk-mt-au-prod-1.au.auth0.com/login/callback](https://snyk-mt-au-prod-1.au.auth0.com/login/callback)                             |
| Signing cert                            | [https://snyk.auth0.com/pem](https://snyk.auth0.com/pem) (암호화가 아닌 서명으로 추가)                                                                 |
| Signing cert (Snyk EU Tenant Customers) | [https://snyk-mt-eu-prod-1.eu.auth0.com/pem?cert=connection](https://snyk-mt-eu-prod-1.eu.auth0.com/pem?cert=connection) (암호화가 아닌 서명으로 추가) |
| Signing cert (Snyk AU Tenant Customers) | [https://snyk-mt-eu-prod-1.au.auth0.com/pem?cert=connection](https://snyk-mt-eu-prod-1.au.auth0.com/pem?cert=connection) (암호화가 아닌 서명으로 추가) |

## Snyk에 제공할 ADFS 정보

ID 공급자로부터 다음 정보를 얻으십시오. 서비스 제공자 측에서 신뢰를 구축하려면 이 정보를 Snyk에 제공하세요.

* ADFS URL 또는 Federation Metadata XML file

## 기업 사용자 지도

Enterprise 요금제의 경우, Snyk은 새 사용자가 SSO를 사용하여 처음 로그인할 때 특정 조직 및 역할에 매핑할 수 있습니다. 이 옵션을 사용하려면 조직의 특정 명명 규칙을 포함한 추가 구성이 필요합니다.

Snyk 계정 팀과 협력하여 이 SSO 옵션 구현을 준비하세요.

## SSO 연결 완료

ID 공급자와의 연결을 설정하고 Snyk 지원팀에 필요한 세부 정보를 제공하면, Snyk에서 페이로드를 생성하기 위한 링크를 보냅니다.

{% hint style="info" %}
Snyk는 생성된 페이로드를 사용하여 구성을 완료하므로, 이 링크를 처음 클릭한 후 표시되는 오류 메시지를 무시하세요.
{% endhint %}

Snyk가 구성을 마치면, 지원 담당자는 쿠키가 로그인 프로세스를 방해하지 않도록 시크릿 모드에서 로그인 페이지로 이동하도록 요청합니다.

프로덕션 환경에 로그인하려면 [https://app.snyk.io/login/sso](https://app.snyk.io/login/sso) 를 사용하세요.

로그인을 완료하려면:

1. 당신의 이메일 주소를 입력 해주세요.
2. **Continue to provider** 을 선택합니다.
3. 다른 애플리케이션과 마찬가지로 ID 공급자로 로그인합니다.
4. 그룹 관리자로 승격할 사용자를 Snyk 지원팀에 알려주세요.

## SSO 설정을 위한 리소스

이 워크시트에는 ID 공급자에 입력할 정보와 Single Sign-On을 요청하기 위해, Snyk 지원팀에 티켓을 제출하기 전, 수집해야 하는 정보가 포함되어 있습니다.

{% file src="../../.gitbook/assets/SSO Azure Worksheet (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (2) (3).pdf" %}

{% file src="../../.gitbook/assets/SSO SAML Worksheet (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).pdf" %}

{% file src="../../.gitbook/assets/SSO ADFS Worksheet (2) (1).pdf" %}

{% file src="../../.gitbook/assets/SSO OIDC Worksheet (1) (1) (1) (1) (1) (1) (1) (1).pdf" %}
