# 1단계: 설정 절차에 필요한 토큰 얻기

코드 에이전트 및 클라이언트 Broker 컴포넌트를 설정하려면 다음 토큰이 필요합니다:

* **Snyk API 토큰** - 이 토큰은 **코드 에이전트 컴포넌트 설정에 필요**합니다. 이 토큰은 `-e SNYK_TOKEN` 파라미터에 사용되어 Snyk 계정으로 코드 에이전트 컴포넌트를 인증하는 데 사용됩니다. [Snyk API 토큰을 얻는 방법 ](../../../../../getting-started/how-to-obtain-and-authenticate-with-your-snyk-api-token.md)및 [Code Agent 컴포넌트 설정](../step-4-setting-up-the-code-agent/step-4.2-running-the-code-agent-container.md) 정보를 참조하세요.
* **Broker 토큰** - 이 토큰은 **Broker 클라이언트 설정에 필요**합니다. 특정 조직 및 특정 SCM에 대한 Broker 배포를 활성화하기 위해 `-e BROKER_TOKEN` 매개변수에서 사용됩니다. [Broker 토큰 얻기](obtaining-your-broker-token.md)를 참조하세요.
* **통합 SCM 토큰** - 이 토큰은 Broker 클라이언트 설정에 필요합니다. 통합 SCM에 대한 특정 권한으로 액세스할 수 있도록 하기 위해 `-e <SCM>_TOKEN` 매개 변수에 사용됩니다. [SCM 토큰 얻기](obtaining-your-scm-token.md)를 참조하세요.

필요한 토큰을 획득한 후에는 안전하고 접근하기 쉬운 곳에 저장하세요. 코드 에이전트 및 클라이언트 Broker 구성 요소를 설정하기 시작할 때 이 토큰을 사용해야 합니다.
