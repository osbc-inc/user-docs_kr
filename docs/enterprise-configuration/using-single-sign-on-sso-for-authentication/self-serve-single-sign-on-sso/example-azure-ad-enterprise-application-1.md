# 예: Ping Identity

이 페이지에서는 Ping Identity 애플리케이션을 설정하고 이를 Snyk에 연결하여 SSO를 활성화하는 방법을 설명합니다.

Snyk에서 SSO를 사용하도록 Ping ID 애플리케이션을 구성하기 전에, Snyk에서 entity ID와 응답 URL(Assertion Consumer Service URL)을 얻으세요. 이후다음 단계를 따르십시오.

1.  왼쪽 메뉴에서 **그룹(Group)**을 선택한 다음 **설정(Settings)**을 선택하세요.

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-09-05 at 10.54.23 AM.png" alt="" width="375"><figcaption></figcaption></figure>
2.  **SSO**를 선택하고 **Entity ID** 및 **ACS URL** 아래의 값을 복사하거나 쉽게 액세스할 수 있도록 브라우저 탭을 열어 둡니다.

    <figure><img src="../../../.gitbook/assets/2 (1) (1) (1) (1).png" alt="Group Settings: SSO"><figcaption><p>그룹 설정: SSO</p></figcaption></figure>
3.  Ping Identity로 이동하여 **연결(Connections)** 메뉴에서 **애플리케이션**을 선택합니다. 더하기 기호를 클릭하여 새 애플리케이션을 만듭니다.

    <figure><img src="../../../.gitbook/assets/1 (2) (1).png" alt="Create a new application"><figcaption><p>새 애플리케이션 만들기</p></figcaption></figure>
4.  애플리케이션 이름을 적절하게 지정하고 **SAML Application**을 선택한 후 **구성(Configure)**을 클릭합니다.

    <figure><img src="../../../.gitbook/assets/2 (1).png" alt="Configure as SAML Application" width="563"><figcaption><p>SAML 애플리케이션으로 구성</p></figcaption></figure>
5.  Snyk에서 복사한 세부정보 **ACS URL**및 **Entity ID**를 입력하고 **저장(Save)**을 선택합니다.

    <figure><img src="../../../.gitbook/assets/3.png" alt="Add Snyk configuration details" width="563"><figcaption><p>Snyk 구성 세부정보 추가</p></figcaption></figure>
6.  **구성(Configuration)**을 선택하고 서명 인증서를 PEM 형식으로 다운로드합니다.

    <figure><img src="../../../.gitbook/assets/4 (1) (1).png" alt="Download signing certificate"><figcaption><p>서명 인증서(signing certificate) 다운로드</p></figcaption></figure>
7.  아래로 스크롤하여 **Single Signon 서비스** 세부 정보를 복사합니다.

    <figure><img src="../../../.gitbook/assets/5 (2).png" alt="Copy the Single Signon Service details"><figcaption><p>Single Signon 서비스 세부정보 복사</p></figcaption></figure>
8.  Snyk 포털로 돌아가서 2단계에서 복사한 단일 로그인 URL을 **로그인 URL** 필드에 붙여넣습니다.

    <figure><img src="../../../.gitbook/assets/single-sign-on-URL-field.png" alt="Paste Sign in URL"><figcaption><p>로그인 URL 붙여넣기</p></figcaption></figure>
9.  원하는 텍스트 편집기에서 다운로드한 인증서를 열고 텍스트를 복사하여 **Snyk X509 서명 인증서** 필드에 붙여넣고 이 SSO 연결에서 지원되는 관련 도메인을 추가하세요.\
    마지막으로 완전히 새로운 연결을 생성하는 경우 **Auth0 연결 생성**을 클릭하고 기존 연결을 편집하는 경우 **변경 사항 저장**을 클릭합니다.

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-09-05 at 11.01.53 AM.png" alt="Enter the Ping Identity details"><figcaption><p>Ping Identity 세부 정보를 입력하세요.</p></figcaption></figure>
10. Ping Identity에서 **속성 매핑(Attribute mappings)**을 선택하고 연필을 클릭하여 편집합니다.

    <figure><img src="../../../.gitbook/assets/6 (3) (1).png" alt="Edit attribue mappings"><figcaption><p>속성 매핑 편집</p></figcaption></figure>
11. 톱니바퀴 아이콘을 클릭하고 다음 속성을 추가합니다.

    **email**: 이메일 주소\
    **username**: 사용자 이름\
    **name**: `user.name.given + ' ' + user.name.famil`표현식; 고급 설명을 입력하려면 톱니바퀴 아이콘을 클릭하세요.

    <figure><img src="../../../.gitbook/assets/7 (2) (1).png" alt="Add attribute mappings"><figcaption><p>속성 매핑 추가</p></figcaption></figure>

    <figure><img src="../../../.gitbook/assets/8 (2) (1).png" alt="Add an advanced expression for the name attribute"><figcaption><p>이름 속성에 대한 고급 표현식 추가</p></figcaption></figure>
12. Snyk 포털에서 로그인 시 신규 사용자를 어떻게 처리해야 하는지 결정하고 사용하려는 옵션(**그룹 구성원, 조직 협력자 또는 조직 관리자**)을 선택하세요.
13. **프로필 속성**을 Ping Identity에 입력한 속성 이름으로 변경한 다음 **변경 사항 저장**을 클릭합니다.

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-09-05 at 11.07.37 AM.png" alt="Step 3 Snyk SSO settings"><figcaption><p>3단계 Snyk SSO 설정</p></figcaption></figure>
14. **3단계 Snyk SSO 설정** 상단의 직접 URL(이미지에는 표시되지 않음)을 사용하거나 일반 SSO 로그인으로 이동하여 로그인할 수 있는지 확인하세요.
15. 마지막 단계로 애플리케이션을 활성화하고 사용자에게 할당합니다.

    <figure><img src="../../../.gitbook/assets/10 (1) (1).png" alt="Enable and assign the application to users"><figcaption><p>애플리케이션을 활성화하고 사용자에게 할당</p></figcaption></figure>
