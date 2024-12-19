# 롤아웃 계획 만들기

비즈니스마다 상황이 다릅니다. 팀이 이미 보안 도구를 사용해 왔고 규정 준수에 중점을 두는 산업에 속해 있다면 상대적으로 더 빨리 제어 기능을 사용할 수 있습니다. 그러나 개발의 일부로서 보안을 처음 도입하는 경우에는 단계적으로 도구와 제어 기능을 도입하는 것이 좋습니다.

## 제안된 온보딩 접근 방식

비즈니스에 Snyk을 도입하는 경우 통합을 구성한 후 다음과 같은 단계적 롤아웃을 제안합니다.

### 1. 파일럿 팀과 함께 시작하기

먼저 참여도가 높은 소규모 파일럿 사용자 그룹을 선택하세요:

* 애플리케이션 보안 팀(해당되는 경우)
* 새로운 애플리케이션을 구축하는 프로젝트 팀
* 비즈니스 크리티컬 애플리케이션 개발자.

이를 통해 다음을 수행할 수 있습니다:

* 철저한 초기 사용자 온보딩
* 피드백을 수집하여 프로세스 개선
* 광범위한 배포 전에 문제 파악
* 성공 사례를 구축하여 Snyk을 홍보하세요.

일반적으로 가시성을 위해 리포지토리 통합을 사용하여 모든 것을 가져오고 소규모 파일럿 팀과 함께 롤아웃을 진행하면 사용자 환경 내에서 Snyk를 구현할 수 있는 최상의 프로세스와 방법을 파악할 수 있습니다.

### 2. Git 리포지토리 통합을 통한 가시성 확보

다음으로, Git 리포지토리 전체에 Snyk 통합을 설정하여 보안 상태에 대한 광범위한 가시성을 확보하세요.

{% hint style="info" %}
노이즈를 줄이려면 모든 사용자를 온보딩한 경우 가져오기 전에 알림을 비활성화하세요.
{% endhint %}

이 프로세스를 사용하면 다음과 같은 주요 이점이 있습니다:

* 코드베이스 전반에 걸친 광범위한 스캔
* 코드 변경 시 자동 스캔 트리거
* 커버리지를 확보하는 편리한 방법.

### 3. 주요 애플리케이션 우선순위 지정

파일럿 팀이 타겟팅된 Snyk CLI 스캔을 사용하여 우선 순위 애플리케이션을 보호하는 데 집중하도록 하세요.

이 프로세스를 사용하면 다음과 같은 주요 이점이 있습니다:

* 중요 앱에 대한 가시성 향상
* 정밀도를 위해 미세 조정된 CLI 테스트
* 집중된 보기를 위해 리포지토리 노이즈 제거.

### 4. 액세스 확장

우선순위를 정하고 프로세스를 개선한 후 팀 전체로 액세스를 더 광범위하게 확장하세요.

이러한 단계적 접근 방식을 통해 신중한 온보딩을 진행하는 동시에 신속하게 가시성과 제어력을 확보할 수 있습니다.

### 5. Turn on gating

After the first month, gradually turn on gating measures.

* Pull Request/Merge Request Checks using criteria such as `severity` and `is fixable`.
* Fail builds based on criteria such as `High` or `Critical`, `CVSS`, `Mature Exploit` for Open Source and other criteria using the [Snyk Filter](https://github.com/snyk-labs/snyk-filter) plugin.

It's recommended to start with a few applications, especially during the pilot team phase, work through the processes then roll out more widely.

## Exception handling

Ensure there is an exception process in place and users are aware. For example:

* If a pull request/merge request is failed by Snyk, let the users know who is the Snyk admin who can override it.
* Similarly, if Snyk fails in CI/CD, let users know who can create an ignore rule, authorize it to progress, or configure CI/CD to run without the Snyk `test` or set it to `monitor` only.
