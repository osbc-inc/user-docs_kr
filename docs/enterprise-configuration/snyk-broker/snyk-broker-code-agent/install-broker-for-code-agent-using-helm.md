# Helm을 사용하여 코드 에이전트용 Broker 설치

Snyk 코드 에이전트를 배포하려면 `enableCodeAgent` 플래그를 `true`로 설정해야 합니다.  [Snyk Code Agent](https://docs.snyk.io/features/snyk-broker/snyk-broker-code-agent)에 대한 자세한 정보를 참조하세요. accept.json 파일에 올바른 항목이 있는지 확인하세요. [여기에서](https://github.com/snyk/broker/tree/master/client-templates)에서 적절한 SCM의 예제 파일을 가져옵니다. Snyk 코드 에이전트 문서에 지정된 대로 추가 항목이 있는지 확인합니다.

다음은 GitLab의 명령 예제입니다:

```
helm install snyk-broker-chart snyk-broker/snyk-broker \
             --set scmType=gitlab  \
             --set brokerToken=<ENTER_BROKER_TOKEN> \ 
             --set scmToken=<ENTER_SCM_TOKEN> \
             --set gitlab=<ENTER_GITLAB_URL>  \
            --set acceptJsonFile=accept.json \
            --set brokerClientUrl=http://<BROKER_CLIENT_URL> \ 
            --set enableCodeAgent=true \ 
            --set snykToken=<ENTER_SNYK_TOKEN> \
            -n snyk-broker --create-namespace
```

참고:`brokerClientUrl`은 Broker 컨테이너의 주소가 됩니다. Broker 컨테이너의 기본 포트는 `8000`입니다. 자세한 내용은 값 파일을 참조하세요. 또한 accept.json은 헬름 차트와 같은 디렉터리에 있어야 한다. 환경 변수의 정의는 [Code Agent 컨테이너 실행하기](https://docs.snyk.io/snyk-admin/snyk-broker/snyk-broker-code-agent/setting-up-the-code-agent-broker-client-deployment/step-4-setting-up-the-code-agent/step-4.2-running-the-code-agent-container#running-the-code-agent-container)를 참조한다.
