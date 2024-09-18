# 스낵바(Snack bar) 적용 사례

## 토스트(Toast)일까? 스낵바(Snack bar)일까?

예전엔 토스트(Toast) 라는 용어로 화면 상단 또는 하단 등에 짧게 사용자 행동에 대한 피드백이나 오류를 보여주고 일정 시간이 경과하면 사라지는 형태로 많이 사용했다.&#x20;

하지만 시간이 지나면  자동으로 사라지는 것으로 인한 접근성에 대한 이슈는 계속 되다가  최근 Google의 머티리얼 디자인에서 Toast가 사라지고 Snack bar가 대체하면서 지금은 많은 기업에서 혼용하여 사용하고 있다.

토스트이던 스낵바이던 그 이름보다 중요한 것은 접근성을 준수하여 구현하는 방법일 것이다.

### 시간이 지나면 사라지는 스낵바는 어떻게 접근성을 준수하지?

WCAG2.2의 [2.2.1 Timing Adjustable](https://www.w3.org/WAI/WCAG22/Understanding/timing-adjustable.html) 기준처럼 제한 시간이 있는 콘텐츠는 그 시간을 조정할 수 있어야 한다, 하지만 스낵바는 일정 시간이 지나면 사라져 다시 볼 수 없다.&#x20;

<figure><img src="../../.gitbook/assets/image (83).png" alt="" width="332"><figcaption><p>G메일의 스낵바</p></figcaption></figure>

G메일에서는 메일을 보낸 후에 보낸 결과를 하단 왼쪽에 스낵바로 사용자에게 피드백을 알리고 있는데, 실행 취소와 메일 보기 , 닫기 버튼 총 3개의 액션 버튼으로 구성되어 있다.&#x20;

구글(Google)이니까 접근성은 잘 구현해 놓았겠지..라는 믿음을 갖고 스크린리더로 들어보았다.

> 메시지 전송됨 실행취소 메일 보기
>
> 알림 실행취소

```html
<div role="alert" aria-live="assertive" aria-atomic="true">
    <div>
        <span>메시지 전송됨</span>
        <span role="alert" aria-live="assertive" tabindex="0">실행취소</span>
        <span role="link" tabindex="0">메일 보기</span>
    </div>
    <div role="button" tabindex="0"></div>
</div>
```

소스를 보면 `role="alert"`의 역할과 `aria-live="assertive" aria-atomic="true"` 속성을 사용하여 스낵바가 표출되자마자 스크린리더가 잘 읽어주고 있다.

하지만 알림 실행취소를 반복적으로 두 번 읽어주고 있고 스낵바의 실행취소 버튼으로 키보드 tab키로 바로 이동이 되지 않았다.

### 조금 더 개선해 볼까?

1. 스낵바가 표출되면 스크린리더가 필요한 부분만 읽을 수 있게 한다.
2. Tab키를 누르면 표출된 스낵바의 액션 버튼으로 이동한다.

```html
//트리거 버튼 바로 하단에 스낵바 소스 삽입하여 바로 접근 가능
<button>메일 전송</button>
//스낵바 소스
<div role="alert" aria-live="assertive" aria-atomic="true">
    <div>// 스낵바 발생 시 삽입 소스
        <span>메시지 전송됨</span>
        <span role="button" tabindex="0">실행취소</span>
        <span role="link" tabindex="0">메일 보기</span>
        <span role="button" tabindex="0">닫기</div>
    </div>
</div>
```

메일 전송 후 실행 취소가 가능함을 바로 알려주기 위해 <mark style="color:blue;">`role="alert"`</mark>과 <mark style="color:blue;">`aria-live="assertive"`</mark>를 사용하였고, 메일 전송과 같이 트리거 버튼 바로 하단에 스낵바 소스가 삽입되어 tab키를 눌러 바로 실행 취소 버튼으로 포커스를 이동시킬 수 있어 키보드 사용자도 빠르게 실행을 취소할 수 있다.&#x20;

### 반드시 role="alert", aria-live="assertive"이지 않아도 된다.

만약,  피드백 내용이 스크린리더가 즉각 읽지 않아도 영향이 없다면 <mark style="color:blue;">`role="status"`</mark>와<mark style="color:blue;">`aria-live="polite"`</mark>를 사용할 수 있다.예를 들면,  항공사 사이트에서 사용자가 항공편을 예매하고 비행기 좌석을 선택할 수 있는데, 그 좌석을 선택한 후에 피드백을 스낵바로 구현할 수 있다.&#x20;

<figure><img src="../../.gitbook/assets/image (87).png" alt="" width="305"><figcaption></figcaption></figure>

```html
<div role="status" aria-live="polite" aria-atomic="true">
    <div>// 스낵바 발생 시 삽입 소스
        <span>39G 좌석이 선택되었습니다.</span>
        <span role="button" tabindex="0">닫기</div>
    </div>
</div>
```

이렇게 구현하면 스크린리더가 현재 읽고 있는 정보를 모두 읽은 후에 읽게 되어 사용자에게 방해가 되지 않을 수 있다.

{% hint style="info" %}
스낵바(Snack bar)는 시간이 지나면 자동으로 사라져 다시 볼 수 없어 접근성에 치명적일 수 있다. 사용자가 반드시 알아야 하는 중요한 정보로 사용하는 것을 권장하지 않는다. 사용자의 행동에 방해가 되지 않는 피드백을 제공하는 역할로 사용하는 것이 가장 바람직한 사용법이다.
{% endhint %}
