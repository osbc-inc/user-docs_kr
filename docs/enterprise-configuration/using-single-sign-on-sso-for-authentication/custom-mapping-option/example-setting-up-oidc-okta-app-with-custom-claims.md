# 예시: Okta OIDC 앱에 대한 사용자 지정 매핑 설정하기

다음 단계에 따라 OIDC Okta에 대한 통합을 구성합니다.

## Okta OIDC 앱 만들기

1.  Okta에서 **Applications -> Applications -> Create App Integration** 를 선택한 다음, **OICD OpenID Connect** 및 **Web Application**을 선택합니다.

    <figure><img src="../../../.gitbook/assets/1 (4).png" alt="Create a new app integration in Okta"><figcaption><p>Okta에서 새 앱 통합 만들기</p></figcaption></figure>
2.  다음 단계에서 OIDC 애플리케이션의 **App integration name**을 추가하고, **Implicit** **Grant Type**을 선택하고,  [Snyk platform deployment](../set-up-snyk-single-sign-on-sso.md)와 관련된 **Sign-in redirect URI** 를 추가합니다. **Sign-out redirect URI**를 제거하고 **Save**를 클릭하기 전에 할당 액세스 제어를 선택합니다.

    <figure><img src="../../../.gitbook/assets/2 (1) (1) (1).png" alt="Provide details for new web app integration"><figcaption><p>새로운 웹 앱 통합에 대한 세부 정보 제공</p></figcaption></figure>
3. 저장 후 열리는 애플리케이션 페이지에서, 다음 세부 정보에 따라 [OIDC information to provide to Snyk](../set-up-snyk-single-sign-on-sso.md#oidc-information-to-provide-to-snyk) [following details](https://docs.snyk.io/features/user-and-group-management/setting-up-sso-for-authentication/set-up-snyk-single-sign-on-sso#oidc-information-to-provide-to-snyk) 복사하여 Snyk 담당자에게 제공합니다:
   * Client ID
   * Implicit Grant type을 사용하지 않는 경우, client secret
4. 또한 발급자 URL/도메인을 Snyk와 공유합니다. 일반적으로 브라우저 주소 표시줄에서 “-admin”이 없는 URL(예: https://customer.example.okta.com)을 찾을 수 있습니다. 또한 애플리케이션의 **Sign-On** 탭에서 **Dynamic** 발급자에서 **Okta URL**로 **OpenID Connect ID Token**을 편집하여 찾을 수도 있습니다.

사용자 지정 매핑을 설정하려면 이 가이드의 다음 섹션으로 이동하세요.

## 사용자 지정 매핑 추가

그룹 수준에서 사용자 지정 속성을 통해 Okta의 OIDC 애플리케이션에 대한 사용자 지정 매핑을 쉽게 관리할 수 있습니다.

### Snyk 조직 이름과 역할을 모두 포함하도록 사용자 지정 앱 사용자 속성을 만드세요.

1. Okta의 **Directory -> Profile editor**에서 새로 만든 OIDC 애플리케이션 사용자 프로필을 선택합니다.
2.  **+Add Attribute**를 선택합니다.

    <figure><img src="../../../.gitbook/assets/3 (3) (1).png" alt="Okta profile editor"><figcaption><p>Okta 프로필 편집기</p></figcaption></figure>
3.  해당 필드에 이 속성에 대한 다음 세부 정보를 추가하고 **Save**를 클릭합니다:\
    **Data type(데이터 유형)** : string array\
    **Display name(표시 이름)** : Snyk roles\
    **Variable name(변수 이름) :** roles\
    **Group Priority(그룹 우선순위)** : Combine values across groups

    <figure><img src="../../../.gitbook/assets/4 (4).png" alt="Attribute details"><figcaption><p>속성 세부 정보</p></figcaption></figure>

### 관련 Okta 그룹에 속성 할당하기

1. Okta의 메인 페이지에서 **Directory -> Groups**을 선택합니다.
2.  **Group**을 선택하고, **Applications**탭으로 이동하여, 아직 할당되지 않은 경우, **Assign** **application**을 클릭한 다음 Snyk OIDC 앱을 선택합니다. 그런 다음 표시된 Snyk OIDC 앱 옆에 있는 **연필**을 클릭합니다.

    <figure><img src="../../../.gitbook/assets/5 (1) (1) (1) (1) (1) (1) (1).png" alt="Group selected for modicification"><figcaption><p>수정을 위해 선택한 그룹</p></figcaption></figure>
3.  **Edit App Assignment** 대화 상자에서, [Example roles array mapping](./#example-roles-array-mapping)에 설명된 구문에 따라 Okta 그룹과 연결된 Snyk org name + role (공백 또는 대문자 제외)을 추가합니다. 예: `snyk-org-role`.

    <figure><img src="../../../.gitbook/assets/6 (1).png" alt="Adding Snyk roles"><figcaption><p>Adding Snyk roles</p></figcaption></figure>
4. 해당되는 모든 Okta 그룹에 대해 앞의 단계를 반복하여 구성된 각 그룹 내의 각 사용자에게 조직 이름과 역할 조합을 할당합니다.

###
