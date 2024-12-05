# 4.1단계: 코드 에이전트 다운로드 또는 업데이트 - Docker 이미지

{% hint style="info" %}
코드 에이전트 도커 이미지를 다운로드하기 전에 컴퓨터에서 도커 컨테이너를 실행할 수 있는지 확인해야 합니다.
{% endhint %}

## 코드 에이전트 도커 이미지 다운로드

먼저 도커 허브에서 코드 에이전트 도커 이미지를 가져옵니다. 코드 에이전트를 실행할 각 머신에 Snyk 코드 에이전트 도커 이미지를 다운로드합니다. Docker 이미지는 일반적으로 호스트 머신에 캐시됩니다.

코드 에이전트의 도커 이미지는 [Docker Hub](https://hub.docker.com/r/snyk/code-agent/)에 있습니다.

**코드 에이전트 도커 이미지를 가져오려면**, 터미널에서 다음을 입력합니다:

```
docker pull snyk/code-agent
```

예를 들어 코드 에이전트 도커 이미지에 대한 다운로드 프로세스가 시작됩니다:

<figure><img src="../../../../../.gitbook/assets/Code Agent - Pull docker image - New.png" alt="Download process for Code Agent Docker image"><figcaption><p>코드 에이전트 도커 이미지 다운로드 프로세스</p></figcaption></figure>

## 코드 에이전트 도커 이미지 업데이트하기

코드 에이전트 도커 이미지를 다시 가져옵니다. 최신 태그를 사용하는 경우 이미지가 자동으로 업데이트됩니다. 그렇지 않으면 새 이미지 태그를 제공하세요:

```
docker pull snyk/code-agent:<image_tag>
```

이전 코드 에이전트 컨테이너를 제거하거나 중지합니다.

새 코드 에이전트 컨테이너를 시작하려면, [코드에이전트 컨테이너 실행](step-4.2-running-the-code-agent-container.md)의 단계를 따르세요.
