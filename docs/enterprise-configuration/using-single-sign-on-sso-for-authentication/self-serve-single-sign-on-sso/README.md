# 셀프 서비스 Single Sign-On (SSO)

SSO용 SAML을 사용하는 Snyk Enterprise 요금제의 그룹 관리자는 Snyk Single Sign-On을 직접 구성할 수 있습니다.&#x20;

새 사용자를 할당할 수 있는 그룹과 조직이 하나 이상 있는지 확인하세요. [Manage Groups and Organizations](../../../snyk-admin/manage-groups-and-organizations/) 를 참조하십시오.

{% hint style="info" %}
셀프 서비스 SSO 옵션을 활성화하려면 Snyk 계정 팀이나 [Snyk support](https://support.snyk.io/hc/en-us)팀에 문의하세요. \
\
이 옵션은 [custom role mapping](../custom-mapping-option/)을 수용하지 않습니다. TSnyk 그룹에 대해 SSO를 사용하여 사용자 정의 역할 매핑을 설정하려면 Snyk 계정 팀에 문의하세요.
{% endhint %}

다음 비디오에서는 SAML을 사용할 때 Single Sign-On을 설정하는 프로세스와 단계를 보여줍니다.

{% embed url="https://thoughtindustries-1.wistia.com/medias/dyg9opxlv8" %}

## SSO에 SAML 사용: 프로세스 개요

ID 공급자(IdP)와 Snyk 간의 신뢰를 설정하는 프로세스에는 그룹 관리자의 몇 가지 단계가 필요합니다.

1. 화면에 표시되는 Snyk 환경 및 사용자 속성에 대한 세부 정보를 사용하여 **IdP(identity provider)를 구성**합니다.
2. 그룹 SSO 설정 페이지에서 IdP(identity provider)의 **SAML 속성**을 입력하세요.
3. 회원이 로그인할 방법을 선택하여 **Snyk SSO 설정**을 구성하세요.
4. SSO 로그인을 확인하여 로그인 프로세스가 올바르게 작동하는지 확인하세요.

{% hint style="info" %}
Snyk와 회사 네트워크 모두에서 SSO가 구성되면 Snyk, Auth0(Snyk 대신) 및 네트워크와 신뢰 관계가 설정됩니다. 모든 민감한 데이터는 사용자 로그인을 활성화할 목적으로만 암호화되어 Auth0에 저장됩니다.

이 페이지에 나오는 모든 예가 Snyk 서명 확인을 다루는 것은 아니지만 신뢰 관계를 개선하고 무결성을 더욱 보장하는 것이 좋습니다. 가능한 경우 해당 IdP의 설명서에 따라 SP 서명 확인을 추가하세요.
{% endhint %}

## 사용자 로그인

사용자는 로그인할 때 Snyk에 [provisioned ](../choose-a-provisioning-option.md)됩니다. 새 사용자 역할이 그룹 구성원으로 선택되면 관리자가 적절한 조직에 추가할 때까지 조직 목록만 표시됩니다

## 대략적인 구성 단계

### &#x20;**IdP(identity provider)** 구성

1. Snyk 웹 UI에서 **그룹** 메뉴로 이동하여 **설정**을 선택합니다.
2. **SSO**를 선택하고 **1단계**에서 필요한 정보(**Entity ID, ACS URL, Snyk 서명 인증서 URL**)를 복사합니다.
3. 해당하는 경우 IdP에 이러한 세부 정보를 입력하고, IdP가 인증서 URL만 허용하지 않는 경우 로컬로 다운로드한 후 Snyk 서명 인증서를 업로드합니다.
4. Snyk UI로 다시 이동하기 전에, **IdP가 제공한 로그인 URL**을 **복사**하고 IdP가 제공한 **X509 서명 인증서 세부정보**를 **복사하거나 다운로드**하세요.

### Snyk 구성

1. Snyk 웹 UI의 SSO 설정 페이지 **2단계**에서, **로그인 URL, 로그아웃 URL**(사용 가능하고 원하는 경우), **IdP 서명 인증서**, **도메인 및 하위 도메인**을 제공하여 SSO 연결을 통해 IdP에서 수집한 세부 정보를 입력합니다.
2. 연결에 HTTP-Redirect 프로토콜 바인딩이 필요한 경우 기본 HTTP-POST에서 해당 옵션을 변경하십시오.
3. 마지막으로 IdP 시작 워크플로를 사용하도록 설정해야 하는지 확인한 다음 기존 연결\*\*.\*\*을수정하는 경우 **연결 생성** 또는 **변경 사항 저장**을 선택합니다.

### 사용자 프로비저닝 설정

1. 처음 로그인할 때 사용자에게 올바른 역할이 할당되었는지 확인하려면, **그룹 구성원**, **조직 협력자** 또는 **조직 관리자**를 선택하세요. 이 단계의 옵션에 대한 자세한 내용은 [choosing a provisioning option](../choose-a-provisioning-option.md) 을 참조하세요.
2. **프로필 속성** 섹션의 필드는 자동으로 채워지지만 **Email**, **Name** 및 **Username**(알고 있는 경우) 이 IdP에서 Snyk로 보낸 SAML 페이로드 원시 JSON의 해당 키와 정확히 일치하는지 확인합니다. **변경 사항 저장**을 선택하고 설정을 확인하는 마지막 단계로 이동합니다.

### 구성 테스트 및 확인

1. 모든 세부 정보를 올바르게 입력했다면, 이제 Snyk 웹 UI의 **3단계** 상단에 있는 direct URL을 사용하여 IdP 디렉터리에 사용자로 로그인하여 구성이 의도한 대로 작동하는지 확인할 수 있습니다.
2. 저장된 모든 세부 정보(이름, 이메일, 권한)가 정확한 것으로 확인되면 Snyk은 일반적으로 이전에 소셜 로그인 방법을 통해 로그인한 기존 사용자를 Snyk 플랫폼에서 제거할 것을 권장합니다. 이는 그룹 메뉴 **Members**에서 수행할 수 있습니다.
