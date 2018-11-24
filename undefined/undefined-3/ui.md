# Tabs UI 적용 사례

### Tabs UI 기본 구조

Tabs UI는 크게 Tab button영역과 Tab panel로 구분된다.  
각각의 Tab button은 연결되는 Tab panel이 있어야 하며, Tab button이 활성화되면 연결된 Tab panel도 활성화되어야 한다.  Tab키로 이동할 때는 활성화된 콘텐츠로 이동되는 것이 기본이다.  

### 탭 버튼 영역

![](../../.gitbook/assets/image%20%289%29.png)

Tab button을 감싸고 있는 컨테이너 영역은 role="tablist"를 삽입하고, Tab button에는 role="tab"을 삽입한다. 선택된 Tab button은 aria-selected="true" 속성을 삽입하고, 비활성화된 Tab button은 aria-selected="false"를 삽입한다.

또한, 하단 콘텐츠와 연결되었다는 것을 스크린리더에서 읽을 수 있도록 aria-controls를 삽입하여 Tab panel의 id 값과 연결한다.

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

![](../../.gitbook/assets/image%20%2815%29.png)

Tab panel 은 활성화된 Tab button의 콘텐츠가 삽입되는 영역으로 role="tabpanel"을 삽입하고, 펼쳐진 상태는를 aria-expanded="true"를 삽입하여 스크린리더를 통해 알릴 수 있다.

탭이 활성화되면 Tab panel 전체 컨테이너에 tabindex="0"을 삽입하고 포커스를 보내면 Tab panel의 제목을 읽을 수 있도록 탭 패널에 aria-labelledby 속성을 삽입하여 연결된 Tab button과 id값을 동일하게 삽입한다.

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

스케줄 조회 Tab button이 활성화 되고 Tab panel로 이동하면 스크린리더는 아래와 같이 읽는다.

> 스케줄 조회 탭 패널

{% hint style="info" %}
Tabs UI는 JAWS와 NVDA에서 서로 읽는 방법이 상이하다.   
활성화된 Tab panel 영역에 tabindex="0"을 삽입하고 포커스를 보내면 JAWS는 Tab panel의 제목을 읽으나 NVDA는 전체 Tab panel 영역의 콘텐츠를 줄줄줄 읽는다.
{% endhint %}

