# 액세스 요구 사항

[CLI ](../getting-started-with-the-snyk-cli.md)또는 [IDE integrations](../../integrate-with-snyk/ide-tools/) 같은 Snyk 애플리케이션을 사용하는 경우 특정 로컬 및 원격 리소스에 액세스할 수 있어야 합니다. 이 문서에서는 Snyk 기능에 영향을 주지 않고 시스템을 강화하는 방법을 설명합니다.

## 로컬 파일 시스템

필요한 파일 시스템 액세스 권한은 제품마다 다를 수 있습니다.

* CACHE\_PATH (읽기, 쓰기, 실행)
  * Windows: `C:\\Users\\<USERNAME>\\AppData\\Local\\snyk`
  * Linux/Alpine: `/home/<USERNAME>/.cache/snyk`
  * macOS: `/Users/<USERNAME>/Library/Caches/snyk`
* CONFIG\_PATH (읽기, 쓰기)
  * Windows: `%USERPROFILE%\\.config\\configstore`
  * Linux: `$HOME/.config/configstore`
  * macOs: `$HOME/.config/configstore`

## 네트워크 리소스

### 필수

* api.\<SNYK\_INSTANCE>.io:443
* app.\<SNYK\_INSTANCE>.io:443

### 선택 사항

* static.snyk.io:443 (사용된 기능에 따라 다름)
* snyk.io:443 (사용된 기능에 따라 다름)
* \*_.sentry.io:443 (_&#xC624;류 보&#xACE0;_)_
* \*_.amplitude.com:443 (analytics)_
