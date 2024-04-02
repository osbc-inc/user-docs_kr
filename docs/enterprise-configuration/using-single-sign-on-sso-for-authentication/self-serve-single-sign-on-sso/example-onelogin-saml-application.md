# 예: OneLogin SAML Application

이 예에서는 OneLogin에서 SAML 애플리케이션을 설정하고 SSO를 용이하게 하기 위해 이를 Snyk에 연결하는 방법을 보여줍니다. Snyk에서 SSO를 사용하도록 OneLogin을 구성하려면 먼저 Snyk에서 엔터티 ID와 회신 URL(Assertion Consumer Service URL)을 얻어야 합니다.

1. 왼쪽 상단의 드롭다운에서 **GROUP OVERVIEW**를 선택한 다음 **톱니바퀴** 아이콘(오른쪽 상단)을 선택하여 그룹 설정으로 이동합니다.

<figure><img src="https://lh5.googleusercontent.com/nHeI8z3TliigfUaI1lTr46yVvgIYd18vjAf9kVwMgVgcV_X4S6bBJDCNjiOppGQVstJ-XtDD6ZK0ErVzMIj8yXZafaJk4Tu8JKoilGAOuddSRHsIKdpDasnviWAYK50NWFrAU9GTGMVqD_gGSe1pTOI" alt="Select group overview"><figcaption><p>그룹 개요 선택</p></figcaption></figure>

2. **SSO**를 클릭하고 **Entity ID** 및 **ACS URL** 아래의 값을 복사하거나 쉽게 액세스할 수 있도록 브라우저 탭을 열어 둡니다.
3. [OneLogin](https://www.onelogin.com/)으로 이동하여 **애플리케이션** 메뉴를 열고 **애플리케이션**을 클릭한 다음 오른쪽 상단에 있는 **앱 추가(Add App)** 버튼을 클릭하세요.

<figure><img src="https://lh4.googleusercontent.com/eWStu1dJQcV618MFMWswLT-88RtDQU4XV-dR25IxjMi_lZpvmgQ97FmF3wJlbWHSVG-kNYCfI7Nis0mB050nXeQJKvsw34irMC7fB_XYYu3GivpfmN-d775-3p64qcBSY0Q5ZfsDahcu_YLHuvem5XM" alt="Add app"><figcaption><p>앱 추가</p></figcaption></figure>

4\. "saml"로 필터링하고 **SAML Custom Connector(고급)** 앱을 선택합니다.

<figure><img src="https://lh5.googleusercontent.com/NcVS2ScxD3_3l464zhgBhVuxC6hpJLyJy7y5c5uyoYv0cfyY5izIiMnmYQIlrerUusud7bbIpFJjQeSHnDHH7v5CbnVhzBwm8qpoO9ryfpCC8WGo4sw3OpDU1SwZWXHaPtSR1-sGX103CoaugXPEI1w" alt="Select SAML Cusotm Connector (Advanced) app"><figcaption><p>SAML Custom Connector(고급) 앱 선택</p></figcaption></figure>

5. **앱의 표시 이름(Display Name**/예: Snyk)을 입력합니다. 선택적으로 아이콘을 선택합니다. Snyk의 프레스 키트 페이지에서 Snyk 로고를 찾을 수 있습니다.

<figure><img src="https://lh6.googleusercontent.com/Ar8VZnNLeqHKP0wgAZYFT4jNo87CTiiNkc4driJsI-ipg8vy13uN_z3CsFGmtnaxbJbpWciw7VH88nzLch68f-jiJOUqbPaiLHJxYZN7F6MZ374IJqzJC7Jj-_ijJefZ3zbvmPtOikZRzHpbln8EtZg" alt="Enter a display name and pick an icon"><figcaption><p>표시 이름을 입력하고 아이콘을 선택하세요.</p></figcaption></figure>

6. 앱이 저장되면 **구성(configuration)** 페이지로 이동하여 **Audience**(EntityID), **ACS URL**, ACS URL Validator를 입력합니다. 여기에서도 ACS URL 값을 사용하세요. 2단계의 EntityID 및 ACS URL을 복사합니다.

<figure><img src="https://lh4.googleusercontent.com/S11TB8rvOOs7abB3bOugmDB041wHIfyFzX9gByH6I12oDLiyiba7ZptPkheT_1wc2hR-QPhiCJgYd4swA_x4zqf1IW-zf2MF7Y4ClvDbgyyX42u12e77_VbQqOow8DPHRVoSFYcecFaHfBj8S3_MKxw" alt="Enter application details"><figcaption><p>신청 내용을 입력하세요</p></figcaption></figure>

7. Snyk에는 SAML 응답의 이메일 속성으로 이메일 주소가 필요하므로 매개변수 섹션으로 이동하여 **새 매개변수(new parameter)**를 추가하세요. **+** 아이콘을 클릭하세요.

<figure><img src="https://lh3.googleusercontent.com/XcsNQ0cEhNE-UTJHK2fOMBEM01KIxR3BHc8Y5M6dQnKHMQQuzJEQ6zuRARY3mXzyw6SPo9miw89pxr2bOPk3NuyMqVZAiIiMxibB0jQlH3kDRuWdkBZmKUKAd_8rdPVgB3Bs1T24HQ--3yRIEKAO_sY" alt="Add a new parameter"><figcaption><p>새 매개변수 추가</p></figcaption></figure>

**필드 이름**에는 **이메일**을 사용합니다. **SAML assertion에 포함** 확인란이 선택되어 있는지 확인하고 **저장**하세요.

<figure><img src="https://lh6.googleusercontent.com/nuR-C1_nGoY87m_fsQUiDhC5dV2nGjyaoyuz_K4uRonw3PB8gWWI3YIvsn0Yp67F2L_yhue-PlaBEYPEsDLjnkvR_hTok-BE4rA4a5xgYWW7Bgu-f44p6J5dSbTVCqZ5lTMHzo2Bpt71Wvt-DCYnpJM" alt="Enter email for the field name"><figcaption><p>필드 이름에 이메일을 입력하세요</p></figcaption></figure>

다음 화면의 **값** 드롭다운 목록에서 **이메일**을 선택하고 **저장**하세요.

<figure><img src="https://lh5.googleusercontent.com/IgUtsnagxiK8GIFB-FomTnlNWoymq-PWpRnsKqeHJebcjiOi9pK6mAdmW7JG-DRQSuzu2-oxjy90SQVJnDLjFE0nZ9Fo0x_lNLsVwceArXqzK2QlRBrTw9xzVsx7URFHeiw4jAzIYqzq9mK0HcIfReY" alt="Select Email form the value dropdown"><figcaption><p>값 드롭다운에서 이메일을 선택하세요.</p></figcaption></figure>

**이름** 속성에 대해 동일한 단계를 반복합니다.

<figure><img src="https://lh6.googleusercontent.com/mdS5fhCGEhI1CzJyUVhyv_Wdp3MiWJb33ImkBrcIparoO9FutqssO0668iiov12--VwevXmpVw8HT0cfMuq2P2Jg6aYX1o-d7ODqajSKLCPY-bI2LEt-lAzytx9u_tejJrJZbRE38lhr1H6lTWWXDfk" alt="Enter name for the field name"><figcaption><p>필드 이름에 이름을 입력하세요.</p></figcaption></figure>

<figure><img src="https://lh6.googleusercontent.com/mqFRW8bqzSEqpNFoHBSXbLsDvTVo0cSbb-B5AjiHd6MaMF6TyKcv1VDIxLMYUbk7CDFGoTzIuNrhssluwVycCV6GLNGAcn8fGRtBE8VSGXQpshmm2L8CrcMm8o1Ve9xPMQ__tSnC9QXBJt3bhxoA0rk" alt="Add the name parameter"><figcaption><p>이름 매개변수 추가</p></figcaption></figure>

8. &#x20;**SSO** 섹션으로 이동하여 **인증서**를 다운로드하고 **SAML 2.0** **Endpoint (HTTP)** 값을 기록해 둡니다.

<figure><img src="https://lh5.googleusercontent.com/qp6ACOk2bxhJiV8PG0XZIHsC_nUIKTCSu6fhPIybQ9FGI4JPWg6gwv72o00Xj1HEfDcQVNRe9jkrtuK0Bzvserc_NVgl0gVFyFozknHJ34dDyqHIceT3xH-iY753ZP7VeDGTS80baRwalnJFFBgKhbE" alt="SAML 2.o Endpoint (HTTP) value"><figcaption><p>SAML 2.o 엔드포인트(HTTP) 값</p></figcaption></figure>

9. 사용자를 위해 앱을 활성화하려면 **Users > Roles** 섹션으로 이동하여 Snyk라는 **새 역할을 만듭니다.**\
   Snyk SAML 앱을 활성화된 역할 앱으로 선택해야 합니다.  \
   저장한 후, Snyk를 사용할 수 있는 모든 사용자에게 이 역할을 할당합니다.

<figure><img src="https://lh4.googleusercontent.com/jZL7kElRSz3PX4LmKkCH1k5vYNCgj2BHqlGHU3dNmJRPIJwQjyMFchWSc6et-m7qeVv2QELr_OWH0IJok0Xwn8OifxWjdfkYqiD2YYs1ubmLBQL2ZM8XAOiPKadNfMSLYoOfMEQ4-JsVCQ0wo0YW4b8" alt="Create Snyk role"><figcaption><p>Snyk 역할 생성</p></figcaption></figure>

10. Snyk 포털로 돌아가서 2단계로 스크롤하고 SSO 연결을 통해 사용하려는 도메인을 포함하여 8단계의 세부 정보를 입력한 다음 **Create Auth0 connection**을 클릭합니다.

<figure><img src="https://lh6.googleusercontent.com/N_sEZ9IrkaSDpmkYVGhHTiSUf1kVL3P1VWBjBhIJfZgraVdifO8zFfS9Y6yQYjNlc5ic9mSimYGfw07-cm7LsweGdlywAAv99LqSz5964wne9EOjB_PvPuE8yhyLf3kvmKhRU6vQKhVsKxiGNR9Mb_E" alt="Enter SAML attributes in the Snyk portal"><figcaption><p>Snyk 포털에 SAML 속성 입력</p></figcaption></figure>

11. 3단계로 스크롤하여 로그인 시 신규 사용자를 어떻게 처리할지 결정하세요. **그룹 구성원, 조직 공동 작업자 또는 조직 관리자** 중에서 사용하려는 옵션을 선택하십시오.\
    마지막으로 OneLogin에서 구성한 **프로필 속성**(이메일, 이름, 닉네임)을 입력하고 **변경 사항 저장**을 클릭한 후 3단계 상단의 직접 URL을 사용하거나 [generic SSO login](https://app.snyk.io/login/sso) 으로 이동하여 로그인할 수 있는지 확인하세요.

<figure><img src="https://lh4.googleusercontent.com/OIEztWL9xGSkLQ1yu2jS8IzU1dLWVuX7YJgfTyHYt3aV_pUn53WWc7qOCZvgK0b2M28SmNsTUDtJJZMdQhhA-5kNA2je71LM-AwHwvyd8UyBtPhfHFEnn0rlCmBEM4tppxVXsiLY78KOLJihIMids0E" alt="Enter profile attributes"><figcaption><p>프로필 속성 입력</p></figcaption></figure>
