# Snyk Broker - commit signing

{% hint style="info" %}
Snyk Broker commit signing은 [Early Access](../../getting-started/snyk-release-process.md#open-beta)중입니다. 이 기능 사용에 관심이 있는 경우 Snyk 담당자 또는 팀에 문의하세요.
{% endhint %}

버전 v4.151.0부터 Snyk Broker 클라이언트는 GitHub 통합을 위한 commit signing을 지원합니다. Broker를 설정하면 GPG 키와 구성한 전용 사용자를 사용하여 수정 PR에 대한 GitHub 커밋에 서명할 수 있습니다.

## commit signing을 위한 요구 사항

* Broker Client 버전 v4.151.0 이상
* **Access->SSH 및 GPG keys** 섹션에서 올바르게 구성된 GPG 키로 커밋에 서명하도록 구성된 GitHub 계정입니다.

## commit signing 구성

1. commit signing을 사용하려면 Broker 클라이언트에 다음 환경 변수를 제공하세요:
   * **`GPG_PRIVATE_KEY`**: ASCII 아머드 버전으로 내보낸 GPG 개인 키입니다. 이 값은 `-----BEGIN PGP PRIVATE KEY BLOCK-----` 으로 시작하고 `-----END PGP PRIVATE KEY BLOCK-----`으로 끝나야 합니다.
   * **`GPG_PASSPHRASE`**: GPG 개인키의 암호문구입니다.
   * **`GIT_COMMITTER_NAME`**: committer 이름을 설정하는 데 사용됩니다.
   * **`GIT_COMMITTER_EMAIL`**: committer 이메일을 설정하는 데 사용됩니다.
2. Snyk 프리뷰 설정에서 **Broker Client Commit Signing**을 사용 설정합니다.

## commit signing 문제 해결

GitHub에서 커밋이 `Unverified`으로 표시되면 다음을 수행해야 합니다:

* environment variables. GPG 공개키를 올바른 GitHub 사용자에게 가져왔는지, 이메일 주소가 환경 변수에 있는 것과 GitHub에서 동일한지 확인합니다.
* Snyk 조직에서 Broker 클라이언트에 커밋 서명 기능이 활성화되었는지 확인하려면 로그를 확인하고 Broker 클라이언트가 시작될 때 다음 메시지가 표시되는지 확인합니다: ​​`loading commit signing rules (enabled=true, rulesCount=5)`
