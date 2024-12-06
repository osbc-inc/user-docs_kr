# 6단계: 코드 에이전트 테스트 - Snyk Broker 설정

코드 에이전트 - Snyk Broker 배포 설정을 테스트하려면 리포지토리를 Snyk으로 가져오고 **코드 분석(Code analysis)** 프로젝트 및 결과를 받는지 확인합니다. 선택한 리포지토리를 Snyk으로 가져오고 Snyk 코드 결과가 표시되면 코드 에이전트 - Snyk Broker 배포가 성공적으로 작동하는 것입니다.

**코드 에이전트** - **Snyk Broker** 배포를 테스트하려면 다음 단계를 따르세요:

1\. Snyk 웹 UI의 왼쪽 탐색에서 코드 에이전트를 테스트할 조직을 엽니다.

2\. 필요한 조직이 열리면 **프로젝트 추가(Add project)**&#xB97C; 선택합니다. 그런 다음 코드 에이전트를 설정한 SCM을 선택합니다:

<figure><img src="../../../../.gitbook/assets/Code Agent - Test - Selecting SCM for import.png" alt="Select Add Project and the SCM"><figcaption><p>프로젝트 추가(Add Project)를 선택하고 SCM</p></figcaption></figure>

3\. **개인 및 조직 리포지토리(Personal and Organization repositories)** 페이지에서 Snyk Code가 분석할 리포지토리를 선택하고 **선택한 리포지토리 추가(Add selected repositories)** 버튼을 클릭합니다:

<figure><img src="../../../../.gitbook/assets/Code Agent - Test - Selecting repos for import.png" alt="Select repositories for Snyk Code to analyze"><figcaption><p>분석할 Snyk 코드의 리포지토리 선택</p></figcaption></figure>

선택한 리포지토리를 Snyk Code로 가져오면 **Projects** 페이지에 진행률 표시줄이 나타납니다. 가져오기가 완료되면 **Projects** 페이지에 가져오기 성공을 확인하는 메시지가 나타납니다. 가져온 리포지토리는 각각 Snyk Code 테스트 결과가 포함된 **코드 분석(Code analysis)** 프로젝트를 포함하는 Target 폴더로 나타납니다:

<figure><img src="../../../../.gitbook/assets/Code Agent - Test - Code Analysis Project.png" alt="Confirmation message and target folders"><figcaption><p>확인 메시지 및 대상 폴더</p></figcaption></figure>

4\. Snyk 코드 결과를 보려면 **코드 분석(Code analysis)** 프로젝트를 선택합니다.

**코드 분석(Code analysis)** 페이지가 열리고 선택한 리포지토리에서 발견된 취약성 이슈의 목록과 세부 정보가 표시됩니다:

<figure><img src="../../../../.gitbook/assets/Code Agent - Test - Code Analysis page.png" alt="Code Analysis page showing issues"><figcaption><p>문제를 보여주는 코드 분석 페이지</p></figcaption></figure>

5\. 특정 취약성 이슈의 세부 정보를 보려면 **전체 세부 정보(Full details)**&#xB97C; 선택합니다.

문제의 세부 정보가 표시되며, Broker 클라이언트를 설정하는 방식에 따라 코드 조각이 **Data flow** 탭에 표시되거나 표시되지 않습니다:

코드 스니펫이 포함된 Snyk 코드 결과:

<figure><img src="../../../../.gitbook/assets/Broker - Results - with code snippets (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (2).png" alt="Broker Client run with display of code snippets"><figcaption><p>코드 스니펫 표시와 함께 실행되는 Broker 클라이언트</p></figcaption></figure>

코드 스니펫이 없는 Snyk 코드 결과:

<figure><img src="../../../../.gitbook/assets/Broker - Results - without code snippets (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (4) (1).png" alt="Broker Client run with no display of code snippets"><figcaption><p>코드 스니펫 표시 없이 Broker 클라이언트 실행</p></figcaption></figure>

Snyk Broker - 코드 에이전트 배포 문제를 해결하는 방법에 대한 자세한 내용은 [Broker 문제해결](../../troubleshooting-broker.md) 참조하세요.
