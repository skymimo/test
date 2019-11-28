# 페이지 네비게이터 적용 사례

### 내가 보고 있는 페이지는 몇 페이지?

보여주어야 하는 데이터가 많은 비행기 유실물 찾기 페이지에는 아래와 같이 페이지 네비게이션을 사용하고 있다. 대한항공의 경우 유실물은 습득 후 90일 이내로 조회해 볼 수 있기 때문에 전체 리스트는 약 300~400 페이지로 구성되어 있다. 

![](../../.gitbook/assets/image%20%2835%29.png)

몇 백 페이지로 구성되어 있는 검색 결과는 카테고리별 검색 기능을 추가하는 것이 사용자가 가장 빠르게 탐색할 수 있는 방법이므로, 검색 결과 페이지에서의 검색 기능을 추가하는 것을 권장한다.

#### 컨텐츠 제목에 몇 페이지 알려주자.

위 예제 화면은 page 1의 결과 페이지이므로 헤딩태그에 숨김텍스트로 page 1을 삽입한다.

```markup
<h2>Lost and Found <span class="offscreen">Page 1</span></h2>
```

 그리고, 하단 페이지 네비게이터 영역은 아래와 같이 마크업한다.

```markup
<div role="navigation" aria-label="Page selection area">
    <ul>
    <li><span class="offscreen">Current page</span> 1</li>
    <li><a href="#"><span class="offscreen">View page</span> 2</a></li>
    <li><a href="#"><span class="offscreen">View page</span> 3</a></li>
    ...
    </ul>
</div>
```

`role="navigation"`을 컨테이너에 삽입하여 네비게이션 임을 알려주고 `aria-label`로 네비게이션 제목을 제공한다. 현재 선택된 페이지는 해당 숫자 앞에 current page를 삽입하고 선택되지 않는 페이지는 숫자 앞에 view page를 삽입하여 스크린리더 사용자의 이해를 도울 수 있다.

원하는 페이지를 선택하면 키보드 포커스는 현재의 페이지를 알려주고 있는 상단의 헤딩 &lt;h2&gt;로 이동하여 정보를 바로 인식할 수 있도록 구현하였다. 

tab키로 이동하여 페이지 2를 선택하는 과정을 스크린리더로 들어보면 아래와 같다.

> Page selection area   
> navigation   
>   
> 목록 항목 수 12개  
> Current page 1  
> View Page 2 링크  
>   
> Lost and Found Page 2 of 395   
> 대화상자

{% hint style="info" %}
현재 선택된 페이지 정보는 구 버전 스크린리더에서 호환을 고려하여 숨김텍스트로 사용하였지만 , WAI-ARIA 1.1의 새로운 속성인 aria-current="page"로 대체 사용할 수 있다. 
{% endhint %}

