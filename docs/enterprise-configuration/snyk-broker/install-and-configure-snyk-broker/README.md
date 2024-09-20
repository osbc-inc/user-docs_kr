# Snyk 브로커 설치 및 구성

## Snyk Broker 개요

Snyk Broker는 Snyk와 특수 통합 사이의 프록시 역할을 하는 오픈 소스 도구로, [snyk.io](http://snyk.io/) 가 코드에 액세스하여 코드를 스캔하고 결과를 사용자에게 반환할 수 있도록 합니다. Broker와의 SCM 통합은 Snyk 오픈 소스, Snyk 코드, Snyk 컨테이너(Docker파일) 및 Snyk IaC를 지원합니다. 작동 방식, 배포 방법, 커밋 서명, 업그레이드 및 문제 해결 등 Snyk Broker에 대한 자세한 내용은 [Snyk Broker 사용자 설명서](../)를 참조하세요.

## 배포 옵션

<table data-card-size="large" data-view="cards" data-full-width="false"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-cover data-type="files"></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><p><a href="https://github.com/snyk/snyk-broker-helm"><strong>Broker Helm Chart</strong></a><strong>를 사용하여 Snyk Broker를 설치한다.</strong></p><p>자세한 내용은 <a href="install-and-configure-broker-using-helm.md">Helm을 사용하여 Broker 설치 및 구성</a>을 참조한다.</p></td><td></td><td></td><td><a href="../../../.gitbook/assets/helmkube.png">helmkube.png</a></td><td><a href="install-and-configure-broker-using-helm.md">install-and-configure-broker-using-helm.md</a></td></tr><tr><td><p>Snyk에서 제공하는 <a href="https://github.com/snyk/broker"><strong>Docker images</strong></a> <strong>사용하여 Snyk Broker를 설치합니다.</strong></p><p>자세한 내용은<a href="install-and-configure-broker-using-docker.md">Docker를 사용하여 Broker 설치 및 구성하기</a>를 참조하세요.</p></td><td></td><td></td><td><a href="../../../.gitbook/assets/Docker-Logo.jpg">Docker-Logo.jpg</a></td><td><a href="install-and-configure-broker-using-docker.md">install-and-configure-broker-using-docker.md</a></td></tr></tbody></table>

또는 [각 Github 릴리스](https://github.com/snyk/broker/releases)에서 제공되는 바이너리를 사용할 수 있습니다.
