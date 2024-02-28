# Snyk 계정 생성 및 로그인

Snyk 기능을 사용하려면 Snyk 계정이 필요합니다.

{% hint style="info" %}
이미 Snyk 계정이 있는 경우, [기존 계정에 로그인](create-or-log-in-to-a-snyk-account.md#undefined-1)을 참조하세요.
{% endhint %}

## Snyk 계정 만들기

{% hint style="info" %}
무료 계정을 만들거나 Snyk 가격 플랜에 가입할 수 있습니다. 자세한 내용은 [Snyk Pricing Plans](../../implement-snyk/enterprise-implementation-guide/trial-limitations.md) 을 참조하세요.
{% endhint %}

Snyk 계정을 만들려면 다음 단계를 따르세요.

1.  [https://snyk.io/](https://snyk.io) 에 접속한 후,  페이지 왼쪽의 **무료 시작(Start free)** 또는 **회원가입(Sign up)**을 클릭하세요.

    <figure><img src="../../.gitbook/assets/start-free_signup.png" alt="Start free or sign up for a Snyk account"><figcaption><p>무료로 시작하거나 Snyk 계정에 가입하세요</p></figcaption></figure>
2.  원하는 가입 방법을 선택하세요. 아래 예시는 무료 계정을 만드는 방법입니다.

    <figure><img src="../../.gitbook/assets/signin_method_10nov2022.png" alt="Choose signup method"><figcaption><p>가입 방법 선택</p></figcaption></figure>
3. 메시지에 따라 새 계정을 만드세요. \
   무료 Snyk 계정이 생성되면, [https://app.snyk.io](https://app.snyk.io)에서 언제든지 로그인할 수 있습니다.

<figure><img src="../../.gitbook/assets/new_acct_created-10nov2022.png" alt="Get started options for a new Snyk account"><figcaption><p>새 Snyk 계정 시작 옵션</p></figcaption></figure>

## 가입 후 다음 단계는 무엇입니까**?**

코드를 스캔하려면, 먼저 Snyk를 해당 코드가 있는 저장소와 통합해야 합니다.

* Snyk 계정을 만든 직후, 자동 프롬프트를 따릅니다.
* 언제든지 수동으로 가능합니다.

자세한 내용은 [통합 설정](set-up-an-integration.md)을 참조하세요.

## 기존 계정에 로그인

[Snyk](https://snyk.io/) 으로 이동하여 링크를 사용하여 로그인 할 수 있습니다. 회사에서 SSO(Single Sign-On)를 사용하는 경우 관리자가 제공한 SSO 링크를 사용하세요.

회사에서 Snyk 사용을 위해 초대를 요구하는 경우, 처음 로그인할 때 조직 목록을 확인할 수 있습니다. 이는 귀하가 아직 초대되지 않았음을 의미합니다. 해당 조직에 대한 액세스를 요청하기 위해 이메일을 보내려면 조직 관리자의 이름을 선택하세요.

Snyk의 조직은 프로젝트에 대한 액세스를 제어합니다. 자세한 내용은 [Snyk Organizations](../../snyk-admin/manage-groups-and-organizations/whats-a-snyk-organization.md) 페이지를 참조하세요.

조직 설정 및 정책은 프로젝트를 추가할 때 사용하는 조직에 따라 스캔 결과에 영향을 미칩니다.

{% hint style="info" %}
회사에서 Snyk 계정에 사용하는 인증 제공업체가 아닌 다른 인증 제공업체로 로그인하는 경우 새 계정을 생성하세요. 귀하의 회사에 맞는 올바른 조직에 로그인되지 않습니다.
{% endhint %}

Snyk는 Snyk Web UI에 로그인할 때 선호하는 조직, 즉 기본 조직을 표시합니다. Snyk는 또한 CLI를 사용하여 로컬로 프로젝트를 테스트할 때 선호하는 조직에 대한 설정을 사용합니다.

{% hint style="info" %}
기본 조직을 변경하려면, Snyk 웹 UI 탐색에서 [Manage account preferences and settings](../explore-snyk-through-the-web-ui.md#manage-account-preferences-and-settings) 를 참조하세요.
{% endhint %}
