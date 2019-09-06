# 탭 UI 적용 사례

### 탭 UI 기본 구조

탭 UI는 크게 탭버튼 영역과 탭패널로 구분된다.  
각각의 탭버튼은 연결되는 탭패널이 있어야 하며, 탭버튼이 활성화되면 연결된 탭패널도 활성화되어야 한다.  Tab키로 이동하는 포커스는 활성화된 콘텐츠로만 이동되어야 한다.

### 탭 버튼 영역

![](../../.gitbook/assets/image%20%2837%29.png)

탭버튼을 감싸고 있는 컨테이너 영역은 `role="tablist"`를 삽입하고, 탭버튼에는 `role="tab"`을 삽입한다. 선택된 탭버튼은 `aria-selected="true"`속성을 삽입하고, 비활성화된 탭버튼은`aria-selected="false"`를 삽입한다.

또한, 하단 콘텐츠와 연결되었다는 것을 스크린리더에서 읽을 수 있도록 aria-controls를 삽입하여 탭패널의 id 값과 연결한다.

```markup
<ul role="tablist">
    <li role="tab" aria-selected="true" aria-controls="탭패널 id" 
     tabindex="0" id="a1">스케줄 조회
    </li>
    <li role="tab" aria-selected="false" aria-controls="탭패널 id" 
     tabindex="-1" id="b1">출도착 조회
    </li>
</ul>
```

스크린리더로 들어보면 아래와 같다.

> 탭 컨트롤  
> 스케줄 조회 탭 선택됨 1/2

### 탭 패널 영역

![](../../.gitbook/assets/image%20%2855%29.png)

탭패널은 활성화된 탭버튼의 콘텐츠가 삽입되는 영역으로 `role="tabpanel"`을 삽입하고, 펼쳐진 상태는를 `aria-expanded="true"`를 삽입하여 스크린리더를 통해 알릴 수 있다.

탭이 활성화되면 탭패널 전체 컨테이너에 `tabindex="0"`을 삽입하고 포커스를 보내면 탭패널의 제목을 읽을 수 있도록 탭 패널에 aria-labelledby 속성을 삽입하여 연결된 탭버튼과 id값을 동일하게 삽입한다.

```markup
<ul role="tablist">
    <li role="tab" aria-selected="true" aria-controls="a1" tabindex="0" 
     id="schedule-tab">스케줄 조회</li>
    <li role="tab" aria-selected="false" aria-controls="b1" tabindex="-1" 
     id="flight-tab">출도착 조회</li>
</ul>
<div role="tabpanel" aria-labelledby="schedule-tab" aria-expanded="true" 
 tabindex="0" id="a1">
 스케줄 조회 탭패널
</div>
```

스케줄 조회 탭버튼이 활성화 되고 탭패널로 이동하면 스크린리더\( jaws\) 아래와 같이 읽는다.

> 스케줄 조회 탭 패널

{% embed url="https://youtu.be/uEK2-tgUc70" %}



{% hint style="info" %}
탭 UI는 JAWS와 NVDA에서 서로 읽는 방법이 상이하다.   
활성화된 탭패널 영역에 tabindex="0"을 삽입하고 포커스를 보내면 JAWS는 탭패널의 제목을 읽으나 NVDA는 전체 탭패널 영역의 콘텐츠를 줄줄줄 읽는다.
{% endhint %}

