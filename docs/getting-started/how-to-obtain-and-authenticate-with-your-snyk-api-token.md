# Snyk API 토큰 획득 및 인증 방법

Snyk API 토큰은 사용자 프로필에서 사용할 수 있는 개인 토큰입니다. Snyk에 개별 사용자로 인증하려면 토큰이 필요하며 `SNYK_TOKEN` 파라미터에도 사용됩니다. Snyk API 토큰은 특정 조직이 아닌 Snyk 계정과 연결됩니다.

무료, 팀 및 평가판 사용자는 사용자 프로필에서 이 개인 토큰에만 액세스할 수 있습니다. **개인 토큰을 사용**하여 다음을 인증할 수 있습니다.

* CI/CD 통합
* 로컬 또는 빌드 머신에서 실행되는 Snyk CLI
* IDE, 토큰 수동 설정 시

기업 사용자는 자신의 프로필에 있는 개인 토큰과 서비스 계정 토큰에 액세스할 수 있습니다. 자세한 내용은 [Service accounts](../enterprise-configuration/service-accounts/)을 참조하세요.

* **기업 사용자**는 모든 종류의 자동화를 인증하려면 **서비스 계정을 사용**해야 합니다. 여기에는 API를 포함한 CLI 또는 빌드 시스템 플러그인 및 자동화를 사용한 CI/CD 스캐닝이 포함되지만 이에 국한되지는 않습니다.
* **기업 사용자**는 다음과 같은 경우 사용자 프로필에서 **개인 토큰을 사용**해야 합니다.
  * 머신에서 로컬로 CLI 실행
  * IDE를 사용하여 수동으로 인증
  * 예를 들어 무언가를 테스트하기 위해 API 호출을 한 번 실행합니다.

개인 Snyk API 토큰에 대한 자세한 내용은 다음 페이지를 참조하세요. [Authenticate the CLI with your account](../snyk-cli/authenticate-the-cli-with-your-account.md), [Authentication for API](../snyk-api-info/authentication-for-api.md).

{% hint style="info" %}
EU 및 AU tenants에서 Snyk를 사용하는 경우, 인증하기 전에 이에 따라 엔드포인트를 설정해야 합니다. 자세한 내용은 [Regional hosting and data residency](../working-with-snyk/regional-hosting-and-data-residency.md)를 참조하세요.
{% endhint %}

개인 Snyk API 토큰을 얻으려면 다음 단계를 따르십시오.

1. Snyk에 로그인하고 **계정 설정(Account settings)**으로 이동하세요.
2. **계정 설정(Account Settings)**에서 **일반(General) > 인증 토큰(Auth Token)**을 선택하세요.
3. **KEY** 상자 내부를 클릭하여 API 토큰을 표시합니다.
4. 토큰을 복사하고 나중에 사용할 수 있도록 안전한 위치에 저장합니다.

<figure><img src="../.gitbook/assets/Snyk Broker - API Token - Account settings - API Token box.png" alt="Settings page, display API token"><figcaption><p>설정 페이지, API 토큰 표시</p></figcaption></figure>
