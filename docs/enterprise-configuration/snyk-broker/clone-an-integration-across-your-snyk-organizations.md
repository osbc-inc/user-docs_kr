# Snyk 조직 전체에서 통합 복제하기

이미 구성한 조직을 복사하고 복제하여 Snyk의 여러 조직에서 동일한 브로커링된 Git 통합을 사용하도록 선택할 수 있습니다.

예를 들어, Snyk 조직 X, Y, Z를 단일 Git 리포지토리 X와 통합할 수 있습니다.

**전제 조건**: 조직 구성을 복제하려면 팀 및 그룹이 활성화되어 있어야 합니다.

1. **조직(Organization)** 목록에서 함께 작업 중인 그룹에서 조직을 선택합니다.\
   <img src="../../.gitbook/assets/switch_org_02oct2022.png" alt="Choose Organization" data-size="original">
2.  같은 **조직(Organization)** 드롭다운에서 **+새 조직 만들기(+Create new Organization)**를 클릭합니다.

    <figure><img src="../../.gitbook/assets/clone-organization1_02oct2022.png" alt="Select +Create new Organization"><figcaption><p>새 조직 만들기를 선택합니다.</p></figcaption></figure>
3. 다음 창에서 새 조직의 이름을 입력합니다.
4. **기존 조직에서 설정 복사 섹션(Copy settings from an existing org)**에서 브로커 토큰에 대해 이미 구성한 조직을 선택합니다.
5.  새 조직으로 복사할 항목의 요약을 검토하고 **조직 만들기(Create organization)**를 클릭하여 확인합니다.&#x20;

    <figure><img src="../../.gitbook/assets/clone-org-3screens_02oct2022.png" alt="Review summary of what will be copied to the new Organization and Create"><figcaption><p>새 조직에 복사할 항목의 요약을 검토하고 만들기</p></figcaption></figure>

방금 생성한 조직의 **대시보드**가 열립니다. Broker 연동이 복제 및 설정되며 Broker 토큰은 원래 조직의 토큰과 동일합니다.
