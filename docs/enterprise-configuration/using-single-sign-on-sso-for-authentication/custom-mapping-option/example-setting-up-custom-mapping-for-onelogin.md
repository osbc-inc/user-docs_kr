# 예: OneLogin에 대한 사용자 정의 매핑 설정

이 예에서는 [configured OneLogin SSO for Snyk](../set-up-snyk-single-sign-on-sso.md)한 후 **사용자 역할을 구성**하는 방법을 보여줍니다.

OneLogin에는 **그룹**과 **역할**이라는 개념이 있습니다. 그러나 OneLogin은 사용자에게 여러 그룹을 할당하는 것을 지원하지 않습니다.

따라서 역할은 그룹을 통해 간접적으로 할당되는 대신 사용자에게 직접 할당됩니다.

1.  OneLogin에서 **사용자**로 이동한 다음 **역할** 섹션으로 이동하여 [사용자 정의 매핑 옵션](./)에 대해 설명된 명명 규칙에 따라 역할을 생성합니다. 각 역할에는 Snyk SAML 앱이 역할 앱으로 활성화되어 있어야 합니다.\
    필요에 따라 사용자를 해당 역할에 할당하십시오.

    <figure><img src="https://lh5.googleusercontent.com/wa_91qbjH1ucVdDbF-3CMRdR6Yc4t-ZQl8-ouJrB8iE3-SZbec7JhmzoIpV9gYW-YEkpijGVI0SnCFJfHAo3p4yTrXEE387rmuwZ1N3h25ili0HEU9ynpGC1noNrOTUVUAr2TO5bCSaq1WU_YmgJxrE" alt="OneLogin Roles section"><figcaption><p>OneLogin 역할 섹션</p></figcaption></figure>
2.  SAML assertion의 사용자 역할을 Snyk로 이전하려면 **애플리케이션**으로 이동하여 Snyk SAML 앱을 선택한 후 왼쪽의 매개변수 섹션을 선택하세요.

    <figure><img src="https://lh6.googleusercontent.com/zseB83vGEsQBiQ2_Rc6zOgkKHkv_KN6S-uLHbZc9k_US_aEzFX1AJUJkEgJpucRtdWYgx0mpUhpHiAhCVTsp3xj2o8hVEB0ArnuMmAVYQ9mw44zULICe57XRZDYxkKHpvpnk6o-TXrqYQHN3MuYMyjA" alt="OneLogin Applications Parameters"><figcaption><p>OneLogin Applications Parameters</p></figcaption></figure>
3. **SAML assertion에 포함** 및 **다중 값 매개 변수** 확인란을 모두 선택하여 **역할**이라는 **새 매개 변수**를 생성하고 **저장**합니다.
4.  다음 화면에서 **기본값**으로 **사용자 역할**을 선택하고 **세미콜론으로 구분된 출력(다중 값 출력)**을 선택합니다.\
    **SAML assertion에 포함** 확인란이 선택되어 있는지 확인하고 **저장**합니다.

    <figure><img src="https://lh3.googleusercontent.com/fnsu9d998jEzxyzuIfHl3JSZHBh5iXsPATUj9jL_SZsFoFPFvvus_JyyY3YAeey5ZMtC9oCuhtjrmSMKAVlY8Tq_Sjf9plgDWagoFuLBQX2U0vbFPU76fNvpjSkpJdgL0JsPhXwq3ngBlgJvdsidoyM" alt=""><figcaption><p>OneLogin 편집 필드 역할</p></figcaption></figure>
