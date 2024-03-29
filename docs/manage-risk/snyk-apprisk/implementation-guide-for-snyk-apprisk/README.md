# Snyk AppRisk 구현 가이드

Snyk AppRisk 구현은 모든 사용자 제품에 대해 애플리케이션 보안 관리를 활성화하여 제품에 많은 이점을 가져다 줍니다.

Snyk AppRisk Essentials는 애플리케이션 보안 팀이 Snyk 기반 개발자 보안 프로그램을 구현, 관리 및 확장하는 데 도움을 줍니다. 이를 통해 다양한 소스의 자산을 하나의 central view로 끌어 들여 어떤 보안 제어 기능이 있는지 이해할 수 있습니다.

이 가이드는 그룹 level에서 Snyk AppRisk를 구현하는 데 도움이 됩니다. [엔터프라이즈 구현 가이드](../../../implement-snyk/enterprise-implementation-guide/) 문서에서 엔터프라이즈 level에서 Snyk를 사용과 관련한 자세한 내용을 확인할 수 있습니다.

## 구현 가이드

구현 가이드는 여러 단계로 나뉘며, 각 단계에서는 Snyk AppRisk의 특정 기능을 사용할 수 있습니다:

* [Level 1: Snyk AppRisk 구성 및 설정](level-1-configure-snyk-apprisk-and-setup-integrations.md)
* [Level 2: 정책](level-2-policies.md)
* [Level 3: 우선순위 설정](level-3-prioritization-setup.md)
* [Level 4: 소스 코드를 컨테이너 이미지와 연결](level-4-associate-the-source-code-with-the-container-images.md)

## 구현 목표

다양한 성숙도 level에서 Snyk AppRisk를 통합할 수 있는 유연성이 있습니다. 이를 통해 모든 기능을 완전히 채택하고 구현할 것인지 아니면 사용 가능한 기능 중 일부만 구현할 것인지 선택할 수 있습니다.

{% hint style="info" %}
가시성, 적용 범위 및 우선 순위 필드는 제한, 양호 및 우수 순위 점수를 사용합니다.
{% endhint %}

### Level 1

**필수 구현**: SCM 온보드

**목표**: 애플리케이션(SCM 저장소에 존재하는 코드 자산)에 대한 가시성을 파악하고 Snyk 커버리지 제어를 이해합니다. OS 상태 위험 요소를 사용하여 컨테이너 문제의 우선순위를 지정합니다.

**가시성**: Good

**커버리지**: Good

**우선순위**: Limited

### Level 2

**필수 구현**: 정책 구현

**목표**: 비즈니스 상황에 따라 자산을 관리하고 비즈니스 요구에 맞게 커버리지 격차 및 경고를 구성합니다.

예시:

1. 자산관리(태그 부착, 분류)
2. Notification 워크플로우
3. 커버리지 갭

**가시성**: Great

**커버리지**: Great

**우선순위**: Limited

### Level 3

**필수 구현**: 우선순위 설정 - Kubernetes 커넥터

**목표**: Kubernetes 커넥터를 탑재하여 컨테이너 이미지에 "deployed" 및 "public facing"로 설정된 위험 요소가 있는지 여부에 대한 문제의 우선 순위를 지정합니다.

**가시성**: Great

**커버리지**: Great

**우선순위**: Limited

### Level 4

**필수 구현**: 태그를 사용하여 Snyk 코드 및 Snyk 오픈 소스 프로젝트를 이미지와 연결합니다.

**목표**: 코드 자산을 관련 컨테이너 이미지와 연결하여 "deployed" 위험 요소와 "public facing" 위험 요소를 기반으로 Snyk Open Source 및 Snyk 코드 문제의 우선 순위를 지정합니다.

**가시성**: Great

**커버리지**: Great

**우선순위**: Great

## Resources

Snyk AppRisk에 대한 자세한 내용은 다음 문서를 확인하세요:

* [Snyk AppRisk ](../getting-started-with-snyk-apprisk.md)documentation
* [Enterprise implementation guide](../../../implement-snyk/enterprise-implementation-guide/)
* [Snyk Learn](https://learn.snyk.io/)
