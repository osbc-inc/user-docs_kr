# 예: Azure AD에 대한 사용자 지정 매핑 설정

다음 정보는 [사용자 지정 매핑 옵션](./)을 사용하여 Azure AD에 대한 사용자 지정 역할 매핑을 구성하는 방법을 보여줍니다.

{% hint style="info" %}
초기 엔터프라이즈 애플리케이션 설정에 대한 지침은 [Azure AD Enterprise Application 예제](../self-serve-single-sign-on-sso/example-azure-ad-enterprise-application.md)를 참조하세요.
{% endhint %}

{% hint style="info" %}
셀프 서비스 SSO는 사용자 지정 매핑을 수용하지 않으므로 Snyk 담당자가 Enterprise Application 설정 시 Snyk 측의 모든 단계를 수행해야 합니다.
{% endhint %}

다음은 **App roles를 구성**하기 위한 **필수 구성 요소** :&#x20;

* Snyk 지원팀에서는 Snyk SSO를 Microsoft Azure AD(WAAD 또는 SAML)로 구성해야 합니다.
* SAML을 선택하는 경우 사용자 지정 클레임을 추가해야 합니다. 이를 수행하는 단계는 이 지침에 나와 있습니다.
* 해당 SSO 구성에 연결된 기존 Azure Enterprise Application 및 앱 등록이 있어야 합니다.

**앱 역할을 구성**하는 **단계**는 다음과 같습니다.

1.  앱 등록 메뉴에서 Enterprise Application의 이름을 선택하세요.

    <figure><img src="../../../.gitbook/assets/image (113) (1).png" alt="App registration, select name of Enterprise Application"><figcaption><p>앱 등록, Enterprise Application 이름 선택</p></figcaption></figure>
2.  **App roles**을 선택한 다음, **Create app role**를 선택합니다.

    <figure><img src="../../../.gitbook/assets/image (1) (1) (2) (1) (1).png" alt="Select App roles, Create app role"><figcaption><p>App roles 선택, app role 생성</p></figcaption></figure>
3.  필요에 따라 세부정보가 포함된 app role을 만듭니다.\
    **Allowed member types**: **Users/Groups**, **Applications**, 또는 **Both**을 선택합니다.\
    선택한 유형에 대한 **Value** 과 **Description**을 입력합니다.\
    app role을 활성화합니다.\
    완료되면 **Apply**을 선택합니다.

    <figure><img src="../../../.gitbook/assets/image (2) (2) (1).png" alt="Create app role with details"><figcaption><p>Create app role with details</p></figcaption></figure>
4.  In Azure AD, select your Enterprise Application.

    <figure><img src="../../../.gitbook/assets/image (3) (2) (1) (1) (1) (1) (1) (1) (1) (1).png" alt="Select Enterprise Application in Azure AD"><figcaption><p>Select Enterprise Application in Azure AD</p></figcaption></figure>
5.  Select **Users and groups**; then **Add user/group**.\
    Search and select the users and groups to add.

    <figure><img src="../../../.gitbook/assets/image (4) (5).png" alt="Select Users and groups, Add user/group"><figcaption><p>Select Users and groups, Add user/group</p></figcaption></figure>
6.  Select **Users and groups**; from the dropdown, select a role; and select **Assign**.

    <figure><img src="../../../.gitbook/assets/image (5) (1) (1) (1).png" alt="Add assignment"><figcaption><p>Add assignment</p></figcaption></figure>
7.  Repeat for all required groups and roles that should be assigned. Then verify that the list looks similar to this.

    <figure><img src="../../../.gitbook/assets/image (6) (1) (1) (2) (1) (1) (1) (1) (1).png" alt="Users and group list"><figcaption><p>Users and group list</p></figcaption></figure>

    Note that it is also possible add multiple Snyk roles to one App role, as the payload can be interpreted as a comma-separated string. However, this can not be used in conjunction with multiple App roles, as only one syntax will be respected (string or array).
8. If you have configured a SAML connection, add a custom claim to pass the roles array in the SAML payload to Snyk. Select **Single sign-on** in the left hand menu.
9.  Select **Edit** next to **Attributes and Claims.**

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-03-10 at 3.19.31 PM.png" alt="Edit attributes and claims"><figcaption><p>Edit attributes and claims</p></figcaption></figure>
10. Select **Add new claim** add the following details, and **Save.**\
    **Name**: roles\
    **Source**: Attribute\
    **Source attribute**: user.assignedroles

<figure><img src="../../../.gitbook/assets/Screenshot 2023-03-10 at 2.55.05 PM.png" alt="Custom claim"><figcaption><p>Custom claim</p></figcaption></figure>

When you have completed these steps, reach out to your Snyk point of contact to have the configuration completedd.
