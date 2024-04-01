# 예: Okta SAML 애플리케이션

이 예에서는 Okta SAML 애플리케이션을 설정하고 SSO를 용이하게 하기 위해 이를 Snyk에 연결하는 방법을 보여줍니다. Snyk에서 SSO를 사용하도록 Okta를 구성하려면 Snyk의 엔터티 ID와 회신 URL(Assertion Consumer Service URL)이 필요합니다.

1.  왼쪽 상단의 드롭다운에서 **GROUP OVERVIEW** 를 선택한 다음 톱니바퀴(오른쪽 상단)를 선택하여 그룹 설정으로 이동합니다.

    <figure><img src="../../../.gitbook/assets/1 (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (3) (1).png" alt="Select group overview"><figcaption><p>group overview 선택</p></figcaption></figure>
2.  **SSO**를 클릭하고 **Entity ID** 및 **ACS URL** 아래의 값을 복사하거나 쉽게 액세스할 수 있도록 브라우저 탭을 열어 둡니다.

    <figure><img src="../../../.gitbook/assets/2 (1) (1) (1) (1).png" alt="Group Settings: SSO"><figcaption><p>그룹 설정: SSO</p></figcaption></figure>
3.  [Okta](https://www.okta.com/se/login/) 로 이동하여, 애플리케이션 메뉴를 열고 **Create App Integration**을 클릭합니다.

    <figure><img src="../../../.gitbook/assets/1 (5) (1).png" alt="Okta Applications main page"><figcaption><p>Okta 애플리케이션 메인 페이지</p></figcaption></figure>
4.  **SAML 2.0**을 선택하고 애플리케이션 이름을 적절하게 지정하세요. **Next**를 클릭하세요.&#x20;

    <figure><img src="../../../.gitbook/assets/2 (3).png" alt="Okta SAML application creation"><figcaption><p>Okta SAML 애플리케이션 생성</p></figcaption></figure>
5.  Snyk에서 복사한 Entity ID와 로그인 URL을 해당 필드에 추가합니다.

    <figure><img src="../../../.gitbook/assets/3 (4).png" alt="Add SSO details in Okta"><figcaption><p>Okta에 SSO 세부정보 추가</p></figcaption></figure>
6.  **Attribute Statements** 까지 아래로 스크롤하고 다음과 같이 값이 지정된 세 가지 속성을 추가합니다.

    * **Name**: email, **Value**: user.email
    * **Name**: name, **Value**: user.firstName + ' ' + user.lastName
    *   **Name**: username, **Value**: user.login

        <figure><img src="../../../.gitbook/assets/5 (2) (1) (1) (1) (1).png" alt="Add Okta attribute statements"><figcaption><p>Okta 속성 문 추가</p></figcaption></figure>

    이제 **Next**을 클릭하고 원하는 경우 피드백 세부 정보를 입력하거나 다음 단계로 이동하세요.
7. Okta 애플리케이션 목록을 다시 열고 새로 생성된 애플리케이션과 **Sign on** 탭을 클릭하세요. 페이지 오른쪽에서 **SAML 설정 지침 보기**를 클릭한 후 열리는 페이지에서 ID 공급자 Single Sign-On URL과 **X.509 인증서**를 복사하세요.
8.  이전 페이지로 돌아가서 **Assignments** 탭으로 이동하세요. **Assign**을 클릭하고 필요에 따라 사용자, 그룹 또는 둘 다를 선택합니다.

    <figure><img src="../../../.gitbook/assets/7 (1) (2).png" alt="Assign the SSO application"><figcaption><p>SSO 애플리케이션 할당</p></figcaption></figure>
9.  Snyk 포털로 돌아가서 2단계로 스크롤하고, SSO 연결을 통해 사용하려는 도메인을 포함하여 7단계의 세부 정보를 입력한 다음, **Create Auth0 connection**을 클릭합니다.

    <figure><img src="../../../.gitbook/assets/8 (3).png" alt="Snyk SSO step 2"><figcaption><p>Snyk SSO 2단계</p></figcaption></figure>
10. 3단계로 스크롤하여 로그인 시 신규 사용자를 어떻게 처리할지 결정하세요. 사용하려는 옵션(**그룹 구성원, 조직 공동작업자 또는 조직 관리자**)을 선택하세요. 마지막으로 Okta에서 구성한 대로 **프로필 속성**을 입력하고 **변경 사항 저장**을 클릭한 후 3단계 상단의 직접 URL을 사용하거나 [generic SSO login](https://app.snyk.io/login/sso)으로 이동하여 로그인할 수 있는지 확인합니다.

    <figure><img src="../../../.gitbook/assets/9 (1) (1) (1) (1) (1).png" alt="Profile attributes"><figcaption><p>프로필 속성</p></figcaption></figure>
