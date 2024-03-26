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

## Set up SAML for SSO

To establish trust with Snyk, add an Entity ID, an Assertion Consumer Service (ACS) URL, and a Signing certificate in your identity provider.

* The **Entity ID** is the URL that uniquely identifies Snyk as a SAML entity or service provider. Note: **default Entity ID must be checked** manually as no default is set for this.
* The **Assertion Consumer Service (ACS)** is the endpoint on the Snyk network that listens for requests from your identity provider to enable communication between users on your network and Snyk. This URL is sometimes called a Reply URL.
* The **Signing certificate** is the Snyk certificate, stored on your server that is needed to maintain the trust relationship. It contains the necessary encryption keys for authentication.

Use these details to set up the connection with your Identity provider (IdP):

| **Details**                                    | **Description**                                                                                                                                                             |
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
Replace **{group-name-normalized}** with the name of your Snyk Group. If your Group name includes spaces, replace them with dashes. For example, if your Group name is `Your Company Group`, then the **{group-name-normalized}** value is **your-company-group**.
{% endhint %}

To map information from your Identity provider to Snyk, name your user attributes as follows, using the same capitalization and spelling:

| **Attribute** | **Description**                                 |
| ------------- | ----------------------------------------------- |
| email         | The user email address                          |
| name          | The name of the person to be authenticated      |
| username      | The person’s username for the identity provider |

If your user attributes do not match, note that the Snyk configuration for your SSO will take more time.

## SAML information to provide to Snyk

Obtain the following information from your identity provider. Provide this information to Snyk to establish trust on the service-provider side.

| Information                   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Sign-in URL                   | The URL for your identity provider sign-in page                                                                                                                                                                                                                                                                                                                                                                                                           |
| X509 Signing Certificate      | The identity provider public key, encoded in Base64 format                                                                                                                                                                                                                                                                                                                                                                                                |
| Sign-out URL                  | <p>Optional, but recommended -</p><p>The URL for redirect whenever a user logs out of Snyk</p>                                                                                                                                                                                                                                                                                                                                                            |
| User ID attribute             | <p>Optional default is <strong>http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier</strong><br><br><strong>Important:</strong> This value uniquely identifies Snyk users and if changed will result in a duplicate user being created. If you see a duplicate user after changing identity provider <a href="https://support.snyk.io/hc/en-us/requests/new">submit a request </a>to Snyk support to have the duplicate user removed.</p> |
| Protocol binding              | HTTP-POST is recommended, HTTP-Redirect is also supported                                                                                                                                                                                                                                                                                                                                                                                                 |
| IdP initiated flow supported? | Idp-initiated flows carry a security risk and are therefore not recommended. Make sure you understand the risks before enabling                                                                                                                                                                                                                                                                                                                           |
| Email domains and subdomains  | The email domains and subdomains that need access to the SSO                                                                                                                                                                                                                                                                                                                                                                                              |

##

## Set up OpenID Connect (OIDC) for SSO

{% hint style="info" %}
The IdP (or issuer URL) must be publicly reachable. If these cannot be made public then SAML should be used rather than OIDC
{% endhint %}

When using OIDC for the connection between your Identity provider and Snyk, add the Callback/Redirect URIs and OAuth Grant Type in your identity provider to establish trust with Snyk.

| Information                                       | Description                                                                                                    |
| ------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Callback/Redirect URIs                            | [https://snyk.auth0.com/login/callback](https://snyk.auth0.com/login/callback)                                 |
| Callback/Redirect URIs (Snyk EU Tenant Customers) | [https://snyk-mt-eu-prod-1.eu.auth0.com/login/callback](https://snyk-mt-eu-prod-1.eu.auth0.com/login/callback) |
| Callback/Redirect URIs (Snyk AU Tenant Customers) | [https://snyk-mt-au-prod-1.au.auth0.com/login/callback](https://snyk-mt-au-prod-1.au.auth0.com/login/callback) |
| OAuth Grant Type                                  | Implicit (or Authorization Code)                                                                               |

## OIDC information to provide to Snyk

Obtain the following information from your identity provider. Provide this information to Snyk to establish trust on the service-provider side.

| Information                  | Description                                                                                                                 |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Issuer URL                   | The URL of the discovery document of the OpenID Connect provider you want to connect with. This must be publicly reachable. |
| Client ID                    | The public identifier unique for your authorization server                                                                  |
| Client Secret                | Needed only if the IdP does not allow the Implicit grant type                                                               |
| Email domains and subdomains | The email domains and subdomains that need access to the SSO                                                                |

## Set up Azure AD as SSO (via App Registration/OIDC)

When using Azure AD for the connection between your Identity provider and Snyk, you must add the Redirect URIs in your Identity provider to establish trust with Snyk.

{% hint style="info" %}
Use your Azure AD name when authenticating rather than the SCM user account name, or a connection error can occur.
{% endhint %}

| Information                              | Description                                                                                                    |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Redirect URIs                            | [https://snyk.auth0.com/login/callback](https://snyk.auth0.com/login/callback)                                 |
| Redirect URIs (Snyk EU Tenant Customers) | [https://snyk-mt-eu-prod-1.eu.auth0.com/login/callback](https://snyk-mt-eu-prod-1.eu.auth0.com/login/callback) |
| Redirect URIs (Snyk AU Tenant Customers) | [https://snyk-mt-au-prod-1.au.auth0.com/login/callback](https://snyk-mt-au-prod-1.au.auth0.com/login/callback) |

## Azure AD information to provide to Snyk

Obtain the following information from your identity provider. Provide this information to Snyk to establish trust on the service-provider side.

| Information               | Description                                                                                                                 |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Client ID                 | The public identifier unique for your authorization server                                                                  |
| Client Secret             | The secret for your authorization that grants tokens to authorized requestors                                               |
| Microsoft Azure AD Domain | The numbers and letters shown in the Directory (tenant) ID, which can be found from the Snyk app you created under Overview |

## Set up ADFS as SSO

When using Active Directory Federation Service (ADFS) for the connection between your Identity provider and Snyk, add the Realm Identifier, a Callback URL, and a Signing certificate in your Identity provider to establish trust with Snyk. For more information, see [Connecting Auth0 to an ADFS server (video)](https://www.youtube.com/watch?v=ICW6sGP9ht8).

| **Information**                         | **Description**                                                                                                                                                  |
| --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Realm Identifier                        | urn:auth0:snyk                                                                                                                                                   |
| EU Realm Identifier                     | urn:auth0:snyk-mt-eu-prod-1                                                                                                                                      |
| AU Realm Identifier                     | urn:auth0:snyk-mt-au-prod-1                                                                                                                                      |
| Callback URL                            | [https://snyk.auth0.com/login/callback](https://snyk.auth0.com/login/callback)                                                                                   |
| Callback URL (Snyk EU Tenant Customers) | [https://snyk-mt-eu-prod-1.eu.auth0.com/login/callback](https://snyk-mt-eu-prod-1.eu.auth0.com/login/callback)                                                   |
| Callback URL (Snyk AU Tenant Customers) | [https://snyk-mt-au-prod-1.au.auth0.com/login/callback](https://snyk-mt-au-prod-1.au.auth0.com/login/callback)                                                   |
| Signing cert                            | [https://snyk.auth0.com/pem](https://snyk.auth0.com/pem) (add as a signature and not encryption)                                                                 |
| Signing cert (Snyk EU Tenant Customers) | [https://snyk-mt-eu-prod-1.eu.auth0.com/pem?cert=connection](https://snyk-mt-eu-prod-1.eu.auth0.com/pem?cert=connection) (add as a signature and not encryption) |
| Signing cert (Snyk AU Tenant Customers) | [https://snyk-mt-eu-prod-1.au.auth0.com/pem?cert=connection](https://snyk-mt-eu-prod-1.au.auth0.com/pem?cert=connection) (add as a signature and not encryption) |

## ADFS information to provide to Snyk

Obtain the following information from your Identity provider. Provide this information to Snyk in order to establish trust on the service-provider side.

* ADFS URL or Federation Metadata XML file

## Map Enterprise users

For Enterprise plans, Snyk can map new users to a specific Organization and role when they first sign in using SSO. This option requires additional configuration, including specific naming conventions for organizations.

Work with your Snyk account team to prepare for implementing this SSO option.

## Complete SSO connection

After you set up the connection with your Identity provider and provide the necessary details to Snyk Support, Snyk sends you a link to generate a payload.

{% hint style="info" %}
Ignore any error message you see after clicking this link the first time, as Snyk uses the generated payload to complete the configuration.
{% endhint %}

When Snyk finishes the configuration, the support agent asks you to navigate to the login page in incognito mode to prevent cookies from interfering with the login process.

Use [https://app.snyk.io/login/sso](https://app.snyk.io/login/sso) for logging into your production environment.

To complete your login:

1. Enter your email address.
2. Select **Continue to provider**.
3. Log in with your identity provider as you would for other applications.
4. Let Snyk Support know which user to promote as the Group administrator.

## Resources for SSO setup

These worksheets include the information to enter in your Identity provider and the information you need to collect before submitting a ticket to Snyk Support to request single sign-on.

{% file src="../../.gitbook/assets/SSO Azure Worksheet (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (2) (3).pdf" %}

{% file src="../../.gitbook/assets/SSO SAML Worksheet (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).pdf" %}

{% file src="../../.gitbook/assets/SSO ADFS Worksheet (2) (1).pdf" %}

{% file src="../../.gitbook/assets/SSO OIDC Worksheet (1) (1) (1) (1) (1) (1) (1) (1).pdf" %}
