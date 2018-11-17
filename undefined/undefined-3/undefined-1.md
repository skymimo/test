# Date Picker 적용사례

Date picker는 동일한 Native HTML과 Role이 없기 때문에 role="application"을 사용하고, 키보드 운용방법을 제공한다. 

### Date Picker는 다음의 정보를 읽을 수 있어야 한다.

* Date Picker의 키보드 운용방법
* 현재 탐색하는 날짜의 현재 연도, 월, 일, 요
* 선택이 불가능한 날짜와 가능한 날짜
* 선택이 된 날짜

![](../../.gitbook/assets/574.png)

#### 월을를 선택하는 영역은 구분  role="navigation"

날짜 탐색 영역 위의 월을 선택하는 부분은 role="navigation"으로 구분하고 보이는 레이블을 아래와 같이 정의한다. 

![](../../.gitbook/assets/575.png)

날짜 탐색 시 월과 연도가 변경될 때마다 실시간으로 변경된 연과 월을 스크린리더가 읽을 수 있도록 aria-live 속성과 함께 숨김텍스트로 삽입하였다.

```markup
<h2 id="year-title">Departure Date</h2>
<div role="navigation" aria-labelledby="year-title">
    <button>Previous Departure Month</button>
    <button>Next Departure Month</button>
    //월과 연도가 변경될 때마다 변경
    <div class="offscreen" id="KE1542367602716-26-dummy0" aria-live="assertive">
        <span>December 2018</span>
    </div>
    <select title="select start date month/year">
    ...
</div>
```

#### 날짜를 선택하는 영역의 구분  role="grid"

role="grid"는 시각적으로는 표 형태로 보이지만, 방향키 등을 통해 탐색하거나 인터랙션이 필요할 때 사용할 수 있는 role이다. 

전체 컨테이너 역할을 하는 &lt;table&gt; 요소에  role="grid"를 삽입하고 각각의 &lt;td&gt;에 role="gridcell"을 삽입한다. 그리고  role="grid" 안에서 탐색방법은 주로 방향키를 사용하기 때문에 포커스가 이동할 수 있도록 tabindex="-1"을 각각의 gridcell 에 삽입하였다. 

![](../../.gitbook/assets/576.png)

Date picker 는 스크린리더가 읽어야 하는 정보는 상당히 많다. 현재 날짜, 요일, 월, 선택할 수 있는 날짜, 선택할 수 없는 날짜, 오늘, 선택한 날짜 등.... 이 많은 정보를 어떻게 간단명료하게 전달할 수 있을지를 고민해야 했다.

#### 천상천하 유아독존 aria-label

이처럼 복잡한 정보를  제공할 경우에는 aria-label을 제공하는 것이 가장 쉽다\(?\). 왜냐하면 aria-label의 장점이자 단점은 aria-label을 사용하게 되면 aria-label만 읽고 다른 것들은 무시한다는 것이다.

각 &lt;th&gt;와 &lt;td&gt; 안에 정보를 잘 넣는다고 하여도 스크린리더의 수많은\(?\) 버그와 때에 따라 달라질 수 있는 오류들 대응하기가 쉽지 않기 때문이다.  aria-label로 제공해야 하는 다양한 정보를  모두 삽입했다. 

**만약, 선택한 날짜가 금요일이고 16일이며, 선택이 가능하고, 오늘이라고 한다면,**

```markup
<td tabindex="-1" aria-label="friday, 16, today, available, selected">16</td>
```

위와 같이 소스를 작성하면 정확하게 우리가 원하는 정보를 읽어 준다.

또한, 날짜를 이동할 때마다 연도와 월까지 계속 읽게 되면 읽어주어야 하는 정보의 양이 너무 많기 때문에 월과 연도는 월이 변경될 때만 읽어줄 수 있도록 role="grid"를 갖고 있는 컨테이너에 aria-labelledby를 월과 연도와 연결하였다.

