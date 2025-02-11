# PR에서 Snyk 활성화 및 구성하기

## PR 검사를 사용하여 게이팅 도입하기

[Snyk 풀리퀘스트(PR)/병합 요청(MR) 검사](../../../scan-with-snyk/run-pr-checks/)를 사용하면 풀 리퀘스트(PR)를 제출할 때 코드 변경 사항을 자동으로 스캔하여 새로운 보안 문제가 코드베이스에 유입되는 것을 방지할 수 있습니다. PR 검사는 오픈 소스 취약성, 라이선스 규정 준수 문제 및 자체 코드 문제에 대해 사용할 수 있습니다.

소스 제어 통합을 통해 프로젝트를 임포트하는 경우, Snyk 오픈 소스 PR 체크는 gatin 도입을 시작하기에 좋은 곳입니다.

{% hint style="info" %}
It변경 사항을 적용하기 전에 공지하는 것이 좋습니다. 개발자에게 메시지를 보내는 방법의 예는 [공지 템플릿](announcement-templates-for-prevention.md)을 참조하세요.
{% endhint %}

## PR 점검 구현

실패 조건을 사용하면 개발팀과의 마찰을 피하기 위해 점진적으로 PR 확인을 도입하는 데 도움이 될 수 있습니다.

실패 조건을 사용하면 PR 자체에 문제가 있는 종속성이 추가되는 경우(가장 일반적인 경우) 또는 리포지토리 전체에 문제가 있는 경우 테스트가 실패할지 여부를 제어할 수 있습니다.

실패한 테스트를 구성하는 기준도 사용자 지정할 수 있습니다. 기본적으로 테스트는 심각도 또는 수정 가능성을 기준으로 필터링하지 않으므로 PR 테스트가 정기적으로 실패할 수 있습니다. 테스트 실패 기준을 사용자 지정할 수 있습니다:

* 심각도가 높음 또는 심각인 문제에 대해서만 실패; Snyk 오픈 소스 및 Snyk 코드에서 사용 가능한 기능입니다.
* 발견된 이슈에 사용 가능한 수정 사항이 있는 경우에만 실패; Snyk 오픈 소스에서 사용 가능한 기능입니다.

처음 PR 검사를 사용 설정할 때는 이 두 상자를 모두 선택하여 높음 또는 심각하고 수정 가능한 문제가 발견되면 테스트가 실패하도록 하는 것이 좋습니다. 이 경우 계속 진행하기 전에 개발자에게 문제를 해결하도록 권장하고 싶을 것입니다.

이러한 PR 테스트는 기본적으로 선택 사항이므로 테스트에 실패하더라도 개발자는 계속 진행하여 PR을 병합할 수 있습니다. PR 테스트의 선택 사항 또는 차단 여부는 GitHub의 브랜치 보호 규칙과 같은 소스 제어 관리 플랫폼 내에서 구성할 수 있습니다.

## 단계적 롤아웃을 위해 PR 확인 사용

Snyk 기능은 단계적으로 출시하는 것이 일반적입니다. PR 확인을 예로 들어 보겠습니다:

* 처음에 Snyk 테스트를 실행하고 소스 제어 설정을 통해 선택적 검사로 설정할 수 있습니다. 결과는 표시되지만 개발자가 PR을 병합하는 것은 차단되지 않습니다.
* 시간이 지나면서 개발자가 이러한 결과를 보는 데 적응하고 중요한 문제를 사전에 해결하기 시작하면 심각도가 높거나 심각한 새로운 문제가 있거나 Snyk 오픈 소스의 경우 사용 가능한 수정 사항이 있는 경우 PR이 병합되지 않도록 차단하도록 선택할 수 있습니다.

이 단계적 롤아웃은 보안 팀과 개발 팀 간의 마찰을 줄이는 데 도움이 됩니다.

## 추가 정보

웨비나 [PR 확인을 사용한 개발자 우선 예방 전략](https://www.youtube.com/watch?v=6x33EJW_d_E)에서는 PR 확인에 대해 자세히 다루며 이 기능을 점진적으로 도입하는 방법에 대한 예시가 포함되어 있습니다.
