# Docker를 사용한 마운팅의 비밀

환경 변수가 아닌 파일에서 민감한 구성인 GitHub 또는 Snyk 토큰을 로드해야 하는 경우가 있습니다. Broker는 [dotenv](https://www.npmjs.com/package/dotenv)를 사용하여 구성을 로드하므로 프로세스가 비교적 간단합니다:

* &#x20;`.env`라는 파일을 만들고 여기에 민감한 구성을 넣습니다.
* 이 파일을 마운트합니다(예: [Kubernetes secret](https://kubernetes.io/docs/tasks/inject-data-application/distribute-credentials-secure/#create-a-pod-that-has-access-to-the-secret-data-through-a-volume)). 파일을`/broker`와 같은 위치에 마운트합니다.
* 도커 이미지의 작업 디렉토리를 `/broker/`로 변경합니다. 이러한 파일의 예는 브로커 컨테이너의 $HOME/.env에 있습니다.
