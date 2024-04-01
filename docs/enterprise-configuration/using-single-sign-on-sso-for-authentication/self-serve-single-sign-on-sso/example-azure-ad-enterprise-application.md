# 예: Azure AD Enterprise 애플리케이션

이 예에서는 Azure AD 엔터프라이즈 애플리케이션을 설정하고 SSO를 용이하게 하기 위해 이를 Snyk에 연결하는 방법을 보여줍니다. Snyk에서 SSO를 사용하도록 Azure 엔터프라이즈 애플리케이션을 구성하려면 먼저 Snyk에서 엔터티 ID와 회신 URL(Assertion Consumer Service URL)을 가져옵니다.

1.  왼쪽 상단의 드롭다운에서 **GROUP OVERVIEW**를 선택한 다음 **톱니바퀴** 아이콘(오른쪽 상단)을 선택하여 그룹 설정으로 이동합니다.

    <figure><img src="../../../.gitbook/assets/1 (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (3) (1).png" alt="Select group overview"><figcaption><p>그룹 개요 선택</p></figcaption></figure>
2.  **SSO**를 클릭하고 **Entity ID** 및 **ACS URL** 아래의 값을 복사하거나 쉽게 액세스할 수 있도록 브라우저 탭을 열어 둡니다.

    <figure><img src="../../../.gitbook/assets/2 (1) (1) (1) (1).png" alt="Group Settings: SSO"><figcaption><p>그룹 설정: SSO</p></figcaption></figure>
3.  Azure로 이동하여 Azure AD를 엽니다.

    <figure><img src="../../../.gitbook/assets/3 (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt="Azure AD Default Directory"><figcaption><p>Azure AD 기본 디렉터리</p></figcaption></figure>
4.  **Add**를 클릭한 다음 **Enterprise application**을 클릭합니다.

    <figure><img src="../../../.gitbook/assets/4 (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt="Add Enterprise application"><figcaption><p><strong>Enterprise application</strong> 추가</p></figcaption></figure>
5.  **Create your own application**를 선택합니다.

    <figure><img src="../../../.gitbook/assets/5 (5) (1).png" alt="Create your own application"><figcaption><p>나만의 애플리케이션 만들기</p></figcaption></figure>
6.  응용 프로그램 이름을 적절하게 지정합니다(예: **Snyk-SSO**). **갤러리에서 찾을 수 없는 다른 응용 프로그램 통합**(비갤러리)이 선택되어 있는지 확인한 다음 **Create**를 클릭합니다.

    <figure><img src="../../../.gitbook/assets/6 (1) (1) (1) (1).png" alt="Application name and integration"><figcaption><p>애플리케이션 이름 및 통합</p></figcaption></figure>
7.  새 앱의 경우, **Set up single sign on** 및 **Get started**을 선택합니다.

    <figure><img src="../../../.gitbook/assets/7 (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (2) (3).png" alt="Set up single sign-on, Get started"><figcaption><p>Single Sign-On 설정, 시작하기</p></figcaption></figure>
8.  SSO 방법으로 **SAML**을 선택합니다.

    <figure><img src="../../../.gitbook/assets/8 (1) (1).png" alt="Select SAML"><figcaption><p>SAML 선택</p></figcaption></figure>
9.  **기본 SAML 구성**에서 **Edit**을 클릭합니다.

    <figure><img src="../../../.gitbook/assets/9 (2) (1) (1) (1).png" alt="Edit basic SAML configuration"><figcaption><p>기본 SAML 구성 편집</p></figcaption></figure>
10. Snyk에서 얻은 ID(엔티티 ID) 및 응답 URL(Assertion Consumer Service URL)을 추가하고 **Save**를 클릭합니다. \*\*\*\* 그런 다음 편집 창을 닫으십시오.&#x20;

    <figure><img src="../../../.gitbook/assets/10.png" alt="Entity ID and Assertion Consumer Service URL"><figcaption><p>Entity ID 및 Assertion소비자 서비스 URL</p></figcaption></figure>
11. 스크롤하여 Snyk에서 구성을 완료하는 데 필요한 로그인 URL을 찾습니다. 이를 복사하여 Snyk 포털의 SSO 설정에 붙여넣습니다.

    <figure><img src="../../../.gitbook/assets/11 (2).png" alt="Login URL"><figcaption><p>로그인 URL</p></figcaption></figure>

    <figure><img src="../../../.gitbook/assets/1 (1) (3) (1) (1) (1) (1) (1) (1) (1).png" alt="Sign in URL in Snyk portal"><figcaption><p>Snyk 포털의 로그인 URL</p></figcaption></figure>
12. Azure AD로 돌아가 **인증서(Base64)** 옆에 있는 **다운로드**를 클릭합니다.

    <figure><img src="../../../.gitbook/assets/13.png" alt="Download SAML Certificate (Base 64)"><figcaption><p>Download SAML Certificate (Base 64)</p></figcaption></figure>
13. 원하는 텍스트 편집기에서 다운로드한 인증서를 열고 텍스트를 복사하여 **Snyk X509 서명 인증서** 필드에 붙여넣고 이 SSO 연결에서 지원되는 관련 도메인을 추가하세요. 마지막으로 완전히 새로운 연결을 생성하는 경우 **Auth0 연결 생성**을 클릭하고 기존 연결을 편집하는 경우 **변경 사항 저장**을 클릭합니다.

    <figure><img src="../../../.gitbook/assets/14.png" alt="Enter certificate and domains supported, set connection"><figcaption><p>지원되는 인증서 및 도메인을 입력하고 연결을 설정하세요.</p></figcaption></figure>
14. 로그인 시 신규 사용자를 어떻게 처리해야 하는지 결정하고 사용하려는 옵션(**그룹 구성원, 조직 협력자 또는 조직 관리자**)을 선택하세요. 마지막으로 Azure의 설정이 기본값에서 벗어나는 경우 **프로필 속성**을 수정합니다. 그런 다음 **변경 사항 저장**을 클릭하고 3단계 상단의 직접 URL을 사용하거나 일반 SSO 로그인으로 이동하여 로그인할 수 있는지 확인하세요.\
    \
    프로필 값이 예상대로 수신되지 않으면 **Azure SSO** **설정** 내에서 **추가 클레임**으로 이메일, 이름 및 사용자 이름을 추가한 다음 Snyk SSO **프로필 속성** 섹션에 적절하게 매핑해야 할 수 있습니다

    <figure><img src="../../../.gitbook/assets/claim1.png" alt="Azure claim settings"><figcaption><p>Azure 클레임 설정</p></figcaption></figure>

    <figure><img src="../../../.gitbook/assets/image2 (2).png" alt="Profile attributes section"><figcaption><p>프로필 속성 섹션</p></figcaption></figure>

들어오는 Snyk 요청에 대한 서명 확인을 추가하려는 경우:

1. Snyk SSO 설정 1단계에서 **서명 인증서(Signing certificate)**를 다운로드합니다.
2. 다음 openssl 명령을 사용하여 `openssl x509 -outform DER -in snyk.pem -out snyk.cer`로 변환합니다.&#x20;
3. Active Directory에 있는 SSO 앱의 **SAML 인증서** 설정 하단에서, **Verification certificates** 옆에 있는  **Edit**을 클릭합니다.
4. **Require verification certificates**를 선택하고 위의 openssl 명령 출력에서 인증서를 업로드한 후 저장(**Save**)을 클릭합니다.
