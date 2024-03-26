# 인증을 위한 Single Sign-On(SSO) 사용

{% hint style="warning" %}
**출시 상태**\
SSO는 Enterprise 플랜에서만 사용할 수 있습니다.

[Pricing plans](https://snyk.io/plans)을 참조하세요.
{% endhint %}

## SSO 개요

회사의 기존 ID 관리 시스템을 활용하고 직원이 회사 ID를 사용하여 Snyk에 로그인하도록 할 수 있습니다. 이를 통해 사용자에게 Snyk을 보다 쉽게 프로비저닝할 수 있습니다. 또한 그룹 및 조직 멤버십, 역할 기반 액세스 등에 대한 심층적인 통합이 가능합니다.

<figure><img src="../../.gitbook/assets/image (1) (4).png" alt="Log in to Snyk with SSO"><figcaption><p>SSO로 Snyk에 로그인</p></figcaption></figure>

Snyk은 모든 SAML 기반 및 OIDC(OpenID Connect) 기반 SSO는 물론 ADFS와 통합할 수 있습니다. [Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-whatis) 및 [Google G Suite](https://community.snowflake.com/s/article/configuring-g-suite-as-an-identity-provider)를 포함하여 SSO용 엔터프라이즈 ID 공급자를 사용할 수도 있습니다. [the Auth0 documentation](https://auth0.com/docs/protocols/saml)에서 SAML에 대해 자세히 알아보세요.

## SSO를 위한 사용자 인증 및 프로비저닝

SSO를 구성하면 사용자가 이전에 자신의 계정을 만들었더라도, SSO를 통해 처음 로그인할 때 새 Snyk 계정이 프로비저닝됩니다.

로그온 프로세스에는 다음 단계가 포함됩니다.

1. 사용자가 Snyk.io에서 SSO를 선택하여 로그인하면 요청한 ID 공급자로 리디렉션되고 인증됩니다.
2. ID 공급자는 이 인증을 Snyk 서버에 전달하고 관련 데이터를 Snyk에 보내 각 사용자를 생성합니다.
3. Snyk는 해당 사용자의 디렉터리를 확인합니다.
4. 사용자가 이미 구성된 경우 Snyk는 적절한 액세스를 활성화합니다. 새 사용자의 경우 Snyk은 사용자를 디렉터리에 추가한 다음 적절한 액세스 권한을 통해 사용자를 Snyk.io로 리디렉션합니다.

## SSO에 대한 추가 리소스

교육: [SSO, authentication and user provisioning](https://learn.snyk.io/lesson/sso-authentication-provisioning/)
