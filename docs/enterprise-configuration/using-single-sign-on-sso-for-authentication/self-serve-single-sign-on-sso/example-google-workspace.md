# 예: Google Workspace

이 예에서는 Google Workspace SAML 애플리케이션을 설정하고 이를 Snyk에 연결하여 SSO를 활용하는 방법을 보여줍니다.

{% hint style="info" %}
이 페이지에 제공된 정보 외에 자세한 내용은 [Google documentation](https://support.google.com/a/answer/6087519)를 참조하세요.
{% endhint %}

&#x20;Google Workspace [admin area](https://admin.google.com)에 로그인하여 시작하세요.

1.  **앱**으로 이동한 다음 **웹 및 모바일 앱**을 클릭합니다.

    <figure><img src="../../../.gitbook/assets/1 (1) (2) (1) (1) (1) (1) (1) (1).png" alt="Open Web and Mobile apps"><figcaption><p>웹 및 모바일 앱 열기</p></figcaption></figure>
2.  **앱 추가**를 클릭하고 **사용자 정의 SAML 앱 추가**를 선택합니다.

    <figure><img src="../../../.gitbook/assets/2 (5).png" alt="Add new custom SAML app"><figcaption><p>새로운 맞춤 SAML 앱 추가</p></figcaption></figure>
3.  애플리케이션의 이름을 적절하게 지정하고 **계속(Continue)**을 클릭하세요.

    <figure><img src="../../../.gitbook/assets/3 (2).png" alt="Name the SAML app"><figcaption><p>SAML 앱 이름 지정</p></figcaption></figure>
4.  인증서를 다운로드하고 원하는 텍스트 편집기에서 엽니다.

    <figure><img src="../../../.gitbook/assets/4 (3) (1) (1).png" alt="Download signing certificate"><figcaption><p>서명 인증서(signing certificate) 다운로드</p></figcaption></figure>
5.  Snyk 포털로 이동하여 로그인하고 왼쪽 상단의 드롭다운에서 **GROUP OVERVIEW**(그룹 개요)를 선택한 다음 톱니바퀴(오른쪽 상단)를 선택하여 그룹 설정으로 이동합니다.

    <figure><img src="../../../.gitbook/assets/1 (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (3) (1).png" alt="Open group view in Snyk"><figcaption><p>Snyk에서 그룹 보기 열기</p></figcaption></figure>
6.  **SSO**를 클릭하고 2단계까지 아래로 스크롤한 후 4단계의 Google SSO URL을 로그인 URL에 붙여넣고 텍스트 편집기의 인증서를 **X509 서명 인증서(signing certificate)**에 붙여넣습니다.\
    **SSO 액세스가 필요한 이메일 도메인 및 하위 도메인**에 이 연결을 구성하려는 도메인 이름을 추가하세요.\
    수정사항을 저장하세요.

    <figure><img src="../../../.gitbook/assets/6 (2) (1) (1) (1) (1).png" alt="Enter details from Google Workspace"><figcaption><p>Google Workspace의 세부정보를 입력하세요.</p></figcaption></figure>
7.  1단계까지 위로 스크롤하여 **Entity ID**와 **ACS URL**을 복사합니다.

    <figure><img src="../../../.gitbook/assets/7 (1).png" alt="Copy details from Snyk"><figcaption><p>Snyk에서 세부정보 복사</p></figcaption></figure>
8.  Google 관리 포털로 돌아가서 **Continue**를 클릭하고 두 값을 해당 필드에 붙여넣습니다. 그런 다음 **서명된 응답(Signed response)**을 선택합니다.

    <figure><img src="../../../.gitbook/assets/8 (2).png" alt="Enter details from Snyk in Google"><figcaption><p>Google에 Snyk의 세부정보를 입력하세요.</p></figcaption></figure>
9.  **Continue**를 클릭하고 **Primary Email**에 연결된 **email**이라는 앱 속성을 추가하고 구성을 저장합니다.

    <figure><img src="../../../.gitbook/assets/9 (3) (1).png" alt="Add email attribute"><figcaption><p>이메일 속성 추가</p></figcaption></figure>
10. **User Access**를 클릭하고 **모든 사용자(On for everyone)에** 대해 켜기를 선택한 후 **저장(Save)**을 선택하여 사용자가 앱에 액세스할 수 있도록 설정하세요. 필요에 따라 조직 액세스를 수정합니다.

    <figure><img src="../../../.gitbook/assets/10 (1).png" alt="Enable SSO app for the organization"><figcaption><p>조직에 SSO 앱 활성화</p></figcaption></figure>
11. Snyk 포털로 돌아가 설정을 마무리하고 로그인 시 새 사용자를 처리할 방법을 결정하세요. 사용하려는 옵션**(그룹 구성원, 조직 공동 작업자 또는 조직 관리자)**을 선택하세요.
12. 그런 다음 이전에 생성된 **email** 앱 속성을 **Email** 과 **Username** 모두에 추가하고 구성을 저장합니다. 전체 이름을 입력하려면 Google Workspace에서 맞춤 속성을 구성하면 됩니다.

    <figure><img src="../../../.gitbook/assets/11.png" alt="Tie together attributes from Google to Snyk"><figcaption><p>Google의 속성을 Snyk에 연결</p></figcaption></figure>
