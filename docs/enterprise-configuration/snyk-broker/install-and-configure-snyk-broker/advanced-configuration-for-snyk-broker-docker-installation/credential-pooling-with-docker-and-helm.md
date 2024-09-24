# Docker 및 Helm을 사용한 자격 증명 풀링

예를 들어 속도 제한 문제를 해결하기 위해 자격증명 '풀'을 만드는 것이 바람직할 수 있습니다. 쉼표로 각 자격 증명을 구분하여 `_POOL`로 끝나는 환경 변수를 만들면 됩니다. 그러면 Broker 클라이언트는 변수 교체를 수행할 때 사용 중인 변수에`_POOL` 접미사가 붙은 변형이 있는지 확인하고, 있는 경우 해당 풀의 다음 항목을 사용합니다. 예를 들어 환경 변수`GITHUB_TOKEN`을 설정했지만 여러 개의 토큰을 제공하려는 경우 이렇게 하면 됩니다:

```
GITHUB_TOKEN_POOL=token1, token2, token3
```

Helm 차트에서 env var + 값으로 추가할 수 있다.

그러면 Broker 클라이언트는 `GITHUB_TOKEN`이 필요할 때마다, `GITHUB_TOKEN_POOL`에서 항목을 가져올 것이다.

자격 증명은 라운드 로빈 방식으로 가져오는데, Broker 클라이언트가 마지막에 도달할 때까지 첫 번째, 두 번째, 세 번째 자격 증명을 가져온 다음 다시 첫 번째 자격 증명을 가져오는 식으로 진행됩니다.

`/systemcheck`엔드포인트를 호출하면 모든 자격 증명의 유효성을 순서대로 검사하고 첫 번째 항목이 첫 번째 자격 증명인 배열을 반환합니다. 예를 들어 GitHub 클라이언트를 실행 중이고 다음과 같은 자격 증명이 있다고 가정해 보세요:

```
GITHUB_TOKEN_POOL=good_token, bad_token
```

`/systemcheck` 엔드포인트는 다음을 반환하며, 첫 번째 객체는 `good_token`에 대한 것이고 두 번째 객체는 `bad_token`에 대한 것입니다:

```
[
  {
    "brokerClientValidationUrl": "https://api.github.com/user",
    "brokerClientValidationMethod": "GET",
    "brokerClientValidationTimeoutMs": 5000,
    "brokerClientValidationUrlStatusCode": 200,
    "ok": true,
    "maskedCredentials": "goo***ken"
  },
  {
    "brokerClientValidationUrl": "https://api.github.com/user",
    "brokerClientValidationMethod": "GET",
    "brokerClientValidationTimeoutMs": 5000,
    "ok": false,
    "error": "401 - {\"message\":\"Bad credentials\",\"documentation_url\":\"https://docs.github.com/rest\"}",
    "maskedCredentials": "bad***ken"
  }
]
```

자격 증명이 마스크로 가려집니다. 그러나 자격 증명에 6자 이하의 문자가 포함되어 있으면 마스크로 완전히 대체됩니다.

## 자격증명 풀링의 제한 사항

자격증명 사용 전에 자격증명 유효성을 확인하거나 유효하지 않은 자격증은 풀에서 제거하지 않으므로 자격증은 Broker 클라이언트에서만 사용하여 자격증이 다른 시간에 요금 제한에 도달하는 것을 방지하고 사용하기 전에 `/systemcheck` 엔드포인트를 호출할 것을 _강력히_ 권장합니다.

GitHub와 같은 일부 제공업체는 토큰 또는 자격증명 단위가 아닌 사용자 단위로 속도 제한을 적용하며, 이러한 경우 계정당 하나의 자격증으로 여러 개의 계정을 만들어야 합니다.

## 자격 증명 매트릭스

자격증명 매트릭스 생성은 지원되지 않습니다.

이 경우 '매트릭스'는 길이`x` 와`y` 의 `_POOL`을 2개(또는 그 이상) 가져와서 길이 `x * y`의 최종 풀 하나를 생성하는 것으로 정의됩니다. 예를 들어 다음과 같은 입력이 주어집니다:

```
USERNAME_POOL=u1, u2, u3
PASSWORD_POOL=p1, p2, p3
CREDENTIALS_POOL=$USERNAME:$PASSWORD
```

매트릭스 지원은 내부적으로 이를 생성합니다::

```
CREDENTIALS_POOL=u1:p1,u1:p2,u1:p3,u2:p1,u2:p2,u2:p3,u3:p1,u3:p2,u3:p3
```

대신 Broker 클라이언트는 처음 찾은 풀만 사용하여 내부적으로 이를 생성합니다:

```
CREDENTIALS_POOL=u1:$PASSWORD,u2:$PASSWORD,u3:$PASSWORD
```
