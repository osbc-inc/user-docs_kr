# 검색 수행

## 비즈니스 크리티컬 애플리케이션 식별

주요 애플리케이션을 조기에 파악하면 중요한 연락처를 파악하고, 성공 지표를 정의하며, 우선순위를 조기에 정하는 데 도움이 됩니다. 비즈니스에 수천 개의 애플리케이션이 있을 수 있지만 진행 상황과 우선 순위를 벤치마킹할 몇 가지 주요 애플리케이션을 식별할 수 있나요?

대기업의 경우 모든 것을 가져올 수 있지만 추가 정보를 동시에 수집하여 작업의 우선순위를 정하고 성공을 측정할 수 있습니다. 이는 계획 및 구현 단계에서 병행하여 수행할 수 있는 작업으로, 방해가 되거나 지연이 되어서는 안 됩니다.

## 내부 연락 창구 및 역할 확인

Snyk을 성공적으로 구현하려면 필요한 기술과 이에 참여할 이해관계자를 파악해야 합니다. 예를 들어, 가능한 사람을 파악하는 것부터 시작해야 합니다:

* 필요한 싱글사인온(SSO) 연결을 만듭니다.
* Git 리포지토리 및 기타 고려 중인 통합에 필요한 권한이 있는 토큰을 생성합니다.

## RACI 매트릭스로 이해관계자 식별하기

소수의 개인에게 필요한 액세스 권한이 있는 소규모 조직에서는 이해관계자를 빠르고 쉽게 참여시킬 수 있습니다. RACI 매트릭스를 사용하여 누가 누구인지 확인할 수 있습니다:

* **R**esponsible(책임자): 작업 또는 결과물 수행에 대한 최종적인 책임이 있는 사람
* **A**ccountable(책임자): 작업이 완료된 것으로 간주되기 전에 반드시 서명해야 하는 승인자
* **C**onsulted(협의 대상): 의견을 구하는 사람, 양방향 커뮤니케이션
* **I**nformed(정보 제공): 진행 상황을 최신 상태로 유지, 단방향 커뮤니케이션

대기업의 경우 롤아웃 시 역할과 책임을 명확하게 정의하는 데 다음 RACI 매트릭스가 유용합니다:

<table><thead><tr><th width="179">작업</th><th width="136">챔피언</th><th width="146">관리자</th><th width="132">보안</th><th>DevOps</th></tr></thead><tbody><tr><td>Onboarding</td><td>Responsible</td><td>Responsible</td><td>Responsible</td><td>Responsible</td></tr><tr><td>SSO setup</td><td>Responsible</td><td>Accountable</td><td>Responsible</td><td>Responsible</td></tr><tr><td>Admin training</td><td>Accountable</td><td>Responsible</td><td>Consulted</td><td>Responsible</td></tr><tr><td>Security training</td><td>Responsible</td><td>Consulted</td><td>Accountable</td><td>Responsible</td></tr><tr><td>DevOps training</td><td>Responsible</td><td>Consulted</td><td>Consulted</td><td>Accountable</td></tr><tr><td>Source Control, IDE, pipeline setup</td><td>Responsible</td><td>Responsible</td><td>Responsible</td><td>Accountable</td></tr><tr><td>Policy management</td><td>Responsible</td><td>Responsible</td><td>Responsible</td><td>Accountable</td></tr><tr><td>Security triage</td><td>Responsible</td><td>Consulted</td><td>Accountable</td><td>Consulted</td></tr></tbody></table>

이를 통해 모든 이해관계자가 중복되거나 소홀히 하는 일 없이 적절한 역량을 발휘할 수 있습니다. 매트릭스를 따르면 개인이 지정된 영역 내에서 전문 기술을 제공함으로써 원활한 협업이 가능합니다.

명확한 업무 구분은 생산성, 효율성, 책임감을 촉진합니다. 전반적으로 RACI 프레임워크는 체계적이고 잘 조율된 온보딩 프로세스를 조율하는 데 효과적인 방법으로, Snyk을 성공적으로 구현할 수 있었습니다.
