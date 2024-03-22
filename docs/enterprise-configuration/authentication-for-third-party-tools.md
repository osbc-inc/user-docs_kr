# 타사 도구에 대한 인증

타사 도구 내에서 Snyk으로 작업할 때,  프로세스를 시작하기 위한 인증이 필요합니다.

Snyk는 타사 개발자 도구와 통합할 수 있는 API 토큰을 제공합니다. 개인 토큰을 사용하여 개인 계정을 통해 인증하거나, 해당 계정과 연결된 토큰을 사용하여 [service account](service-accounts/)을 통해 인증할 수 있습니다. 서비스 계정을 통해 인증할 때는 개인 토큰을 사용하지 않습니다.

{% hint style="info" %}
인증 목적으로 제3자 ID 공급자는 **귀하의 리포지토리에 대한 액세스를 요구하지 않으며** 귀하의 이메일 주소만 요구합니다.
{% endhint %}

## 지원되는 ID 공급자

Snyk 인증을 위해 다음 ID 공급자 중 하나를 사용할 수 있습니다.

* GitHub
* Bitbucket
* Google
* Azure AD
* Docker ID
* Single Sign-On (SSO): Enterprise 플랜에서 사용할 수 있습니다.\
  [Setting up Single Sign-On (SSO) for authentication](using-single-sign-on-sso-for-authentication/)을 참조하세요.

{% hint style="info" %}
추가 지침은 [Git repositories (SCMs)](../integrate-with-snyk/git-repositories-scms-integrations-with-snyk/) 통합 페이지를 참조하세요.
{% endhint %}

{% hint style="warning" %}
Snyk 계정을 처음 만들 때 등록한 공급자와 다른 공급자로 로그인하면 별도의 새 Snyk 계정이 생성됩니다.
{% endhint %}

## 개인 토큰을 사용하여 타사 도구를 인증하는 방법

1. [your Snyk account](https://app.snyk.io/account)을 방문하세요.
2. **일반 계정 설정(General Account Settings)**으로 이동하여 토큰을 복사하세요.
3. 토큰 필드에서 **클릭하여 표시**한 다음 API 토큰을 선택하고 복사하세요.
4. 타사 인터페이스에서 메시지가 표시되면 Snyk 토큰을 붙여넣어 통합을 구성합니다.

<figure><img src="../.gitbook/assets/uuid-8d94edf8-b42b-e5b3-ada1-e157d18ff884-en (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (3) (16).png" alt="API token screen; revoke; regenerate; click to show"><figcaption><p>API token 화면; revoke; regenerate; 보려면 클릭하세요</p></figcaption></figure>
