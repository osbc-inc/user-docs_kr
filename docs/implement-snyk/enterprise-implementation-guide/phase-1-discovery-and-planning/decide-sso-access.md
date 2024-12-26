# SSO 액세스 결정

## Single Sign-On(SSO) 설정 결정하기

SSO에 대한 자세한 내용은 [인증에 통합 인증(SSO) 사용하기](../../../enterprise-configuration/using-single-sign-on-sso-for-authentication/)를 참조하세요.

초기 파일럿 또는 평가판 팀에서는 개인 인증을 사용하는 것이 일반적이지만, 사용자에게 Snyk을 배포하기 전에 다음을 포함하여 SSO를 구현해야 합니다:

* 적절한 SSO 계정을 만들고 해당 계정을 관리자로 승격하기
* 더 많은 그룹에 배포하기 전에 Snyk에서 개인 계정을 제거합니다.

## SSO 프로비저닝 옵션

회사에서 새 사용자의 액세스 권한을 설정할 때 사용자 환경과 액세스 권한을 결정하는 몇 가지 접근 방식을 고려할 수 있습니다. 이 단계에서는 **모두에게 공개** 또는 **초대 필요**를 고려하고 **사용자 지정 매핑**을 원하는 경우 이를 고려합니다.

자세한 내용은 [프로비저닝 옵션 선택](../../../enterprise-configuration/using-single-sign-on-sso-for-authentication/choose-a-provisioning-option.md)을 참조하세요.&#x20;

{% hint style="info" %}
**사용자** **지정 매핑**\
이 기능은 [유료 서비스](broken-reference/)에서만 사용할 수 있습니다. 이 기능을 사용하면 사용자 지정 규칙으로 사용자 계정을 프로비저닝하여 특정 요구 사항에 따라 액세스 권한과 역할을 조정할 수 있습니다. 이 기능은 복잡한 구성 및 설정이 필요할 수 있으며, 고급 특정 액세스 관리 요구 사항이 있는 조직에 권장됩니다.
{% endhint %}

####
