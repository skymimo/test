---
description: 토스트? 스낵바?
---

# 스낵바(Snack bar) 적용 사례

## 토스트(Toast)? 스낵바(Snack bar)?

<figure><img src="../../.gitbook/assets/image (82).png" alt="" width="326"><figcaption><p>G메일의 스낵바</p></figcaption></figure>

예전엔 토스트(Toast) 라는 용어로 화면 상단 또는 하단 등에 짧게 사용자 행동에 대한 피드백이나 오류를 짧게 보여주고 일정 시간이 경과하면 사라지는 형태로 많이 사용했다. 구글의 머티리얼 디자인에서 Toast가 사라지고 Snack bar가 대체하면서 많은 기업에서 지금은 그 UI를 혼용하여 사용하고 있다.

토스트이던 스낵바이던 그 이름보다 중요한 것은 접근성을 준수하여 구현하는 방법일 것이다.

### 시간이 지나면 사라지는 스낵바는 어떻게 접근성을 준수하지?

### [**2.2.1 Timing Adjustable**](https://www.w3.org/WAI/WCAG22/Understanding/timing-adjustable.html)

WCAG2.2의 2.2.1 Timing Adjustable 기준처럼 제한 시간이 있는 콘텐츠는 그 시간을 조정할 수 있어야 한다, 하지만 스낵바는 일정 시간이 지나면 사라져 다시 볼 수 없다.
