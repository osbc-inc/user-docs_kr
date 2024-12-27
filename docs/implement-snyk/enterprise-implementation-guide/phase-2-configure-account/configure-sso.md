# SSO 구성하기

SSO 구성은 프로젝트를 온보딩하거나, 조직 구조를 만들거나, 통합을 구성하는 동안에도 할 수 있습니다. 프로젝트를 Snyk에 온보딩하기 전에 사용자를 추가하려는 경우 조직에 대한 알림을 비활성화하세요.

[Snyk으로 Single Sign On](../../../enterprise-configuration/using-single-sign-on-sso-for-authentication/)을 설정하면 사용자가 애플리케이션에 로그인하는 일관된 방법을 제공하는 동시에 조직에 액세스할 수 있는 사용자를 제어할 수 있습니다.

대부분의 경우 Snyk에서는 ID 공급자에 대한 SAML 연결을 구성할 수 있는 [셀프 서비스 Single Sign-On 옵션](../../../enterprise-configuration/using-single-sign-on-sso-for-authentication/self-serve-single-sign-on-sso/)을 사용할 것을 권장합니다. 이를 통해 유효한 이메일 도메인과 조직에서 새 사용자가 갖게 될 기본 권한을 구성할 수 있습니다.

## 지원을 받는 방법

Snyk 라이선스에 따라 그룹 설정 페이지에 SSO 옵션이 표시되지 않을 수 있습니다. 표시되지 않으면 [지원팀에 요청을 제출하여 ](https://support.snyk.io/hc/en-us)활성화하세요. 이 옵션을 사용하면 SAML로 SSO를 구성할 수 있지만, 다른 SSO 구성 옵션(예: OIDC)을 사용하려는 경우 [Snyk 지원팀에 요청을 제출하면](https://support.snyk.io/hc/en-us), Snyk 지원팀이 도움을 드립니다.

## SSO 사용자 지정 매핑 지원

이 옵션을 사용하려면 유료 전문 서비스가 필요하며 셀프 서비스 SSO 옵션으로는 완료할 수 없습니다. 필요한 서비스를 구매하려면 Snyk 계정팀 또는 [Snyk 지원팀에 문의하세요.](https://support.snyk.io/hc/en-us)

## API를 통해 사용자를 프로비저닝하는 방법

Snyk API v1의 [사용자 엔드포인트 프로비저닝](https://docs.snyk.io/snyk-admin/manage-users-in-organizations-and-groups/provision-users-to-orgs-using-the-snyk-api-v1)을 사용하면 사용자가 Snyk 플랫폼에 로그인하기 전에 조직 수준의 액세스 권한과 권한을 부여할 수 있습니다.

또한 API 프로비저닝을 통해 조직 액세스를 제한하고 사용자 지정 멤버 역할을 할당할 수 있습니다. 이를 통해 제어할 수 있습니다:

* 각 사용자에게 할당된 역할
* 각 사용자에게 액세스 권한이 있어야 하는 조직
