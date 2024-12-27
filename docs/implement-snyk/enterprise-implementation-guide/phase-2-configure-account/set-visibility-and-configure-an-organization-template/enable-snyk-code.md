# Snyk 코드 활성화

새 조직을 만들면 기본적으로 Snyk 코드(SAST) 스캔이 비활성화됩니다. Snyk는 첫 번째 프로젝트를 Snyk으로 가져오기 전에 Snyk 코드를 활성화하는 것이 좋습니다. 프로젝트를 가져온 후에 Snyk Code를 활성화하면 Snyk은 Snyk 코드 파일을 감지하지 못합니다.

1. **설정(Settings) > Snyk Code** 옵션을 선택합니다.
2. 토글을 클릭하여 Snyk 코드를 활성화한 다음 **변경 사항 저장(Save changes)**&#xC744; 클릭합니다.

[조직에 대한 Snyk REST API 엔드포인트 코드 사용/사용 안 함 설정](https://apidocs.snyk.io/#patch-/orgs/-org_id-/settings/sast)을 사용하여 많은 조직에서 이 작업을 대규모로 수행할 수 있습니다.
