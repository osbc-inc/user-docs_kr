# 정책(Policies)

{% hint style="info" %}
**기능 사용 가능 여부**

정책은 Enterprise 요금제에서 사용할 수 있으며 Snyk 오픈 소스 스캔에만 적용됩니다. [요금제 및 가격 책정](https://snyk.io/plans)을 참조하세요.

.snyk 파일은 Snyk에서 특정 분석 동작을 정의하고 CLI 및 CI/CD 플러그인에 대한 패치를 지정하는 데 사용하는 정책 파일이라는 점에 유의하세요. 자세한 내용은 [.snyk file](the-.snyk-file.md) 파일을 참조하세요.  for details
{% endhint %}

Snyk 정책에는 특정 유형의 문제가 발생할 때 Snyk이 작동하는 방식을 정의하는 규칙이 포함되어 있습니다. 정책을 사용하면 `no exploit available`과 같은 조건을 기반으로 문제 유형을 식별한 다음 심각도 변경과 같은 조치를 해당 문제에 적용할 수 있습니다. 따라서 사용자 지정 가능한 Snyk 정책을 사용하여 스캔 시 발생하는 특정 유형의 문제에 대한 조치를 정의할 수 있습니다.

<div align="left">

<figure><img src="../../.gitbook/assets/image (112) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (2) (1) (2) (3).png" alt="Snyk Policy manager"><figcaption><p>Snyk 정책 관리자(Snyk Policy manager)</p></figcaption></figure>

</div>

Snyk 정책 관리자를 사용하여 정책을 [보고](view-policies.md), [만들고, 편집](create-and-edit-policies.md)할 수 있습니다.

## Snyk 정책의 이점

정책을 사용하면 애플리케이션 개발과 관련이 없거나 중요하지 않은 문제를 빠르고 자동으로 식별하고 분류할 수 있습니다. 이를 통해 노이즈 수준을 줄여 귀중한 개발 시간을 절약하고 개발자가 보안에 대한 책임감과 소유권을 더 많이 가질 수 있습니다.

정책은 해결해야 할 문제의 우선순위를 정하고 취약하거나 규정을 준수하지 않는 구성 요소가 알림을 받지 않도록 하는 데 도움이 됩니다. 정책은 회사의 거버넌스 프레임워크의 일부입니다.

자세한 내용은 [SDLC의 정책 사용](use-policies-in-the-sdlc.md)을 참조하세요.

## 정책 카테고리

Snyk의 보안 및 라이선스 정책.

* [보안 정책(Security policies)](security-policies/)은 예를 들어 심각도 수준 또는 무시된 이슈에 따라 취약성을 처리할 때 Snyk의 동작을 정의합니다.
* [라이선스 정책(License policies)](license-policies/)은 특정 라이선스 유형의 패키지를 허용 또는 허용하지 않거나 호환되지 않는 라이선스가 포함된 패키지의 사용을 방지하는 등 라이선스 문제를 처리할 때 Snyk의 동작을 정의합니다.

## 프로젝트 또는 조직에 정책 할당

각기 다른 정책에 따라 애플리케이션을 검사해야 할 수도 있습니다. Mission-critical 애플리케이션은 샌드박스 환경에서 내부 애플리케이션보다 더 많은 제어가 필요할 수 있습니다. 다음에 정책을 할당하여 필요한 제어를 설정할 수 있습니다:

* [프로젝트](assign-policies-to-projects.md)에 속성을 적용한 후 프로젝트, 속성에 정책을 적용합니다.
* Snyk 그룹의 [조직](assign-a-policy-to-an-organization.md)
