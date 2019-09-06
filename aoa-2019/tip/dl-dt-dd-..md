# dl, dt, dd 태그를 남용하지 마세요.

### dl 은 Definition list 또는 description list

국내 사이트에는 구조화하여 마크업하기 쉽다는 이유로 무의식적으로 &lt;dl&gt;, &lt;dt&gt;, &lt;dd&gt;를 많이 사용한다.  사용 목적을 잘 이해하지 않고 시맨틱하다고 생각하고 사용하는 경우도 많다.

다음의 예제 화면을 보자.

![](../../.gitbook/assets/image%20%2823%29.png)

```markup
<dl>
    <dt>Cabin Class</dt>
    <dd><input type="radio" id="cla-1">
        <label for="cla-1">Economy Class</label>
    </dd>
    <dd><input type="radio" id="cla-2">
        <label for="cla-2">Prestige Class</label>
    </dd>
    <dd><input type="radio" id="cla-3">
        <label for="cla-3">First Class</label>
    </dd>
</dl>
```

처음 이렇게 제작해 놓고 잘 구조화 해놓았고 좋아했지만, 이런 형태는 정의형 목록도 아니고 설명을 위한 목록도 아니다. 

다음의 더 신박한 마크업을 보자.

![](../../.gitbook/assets/image%20%2829%29.png)

```markup
<dl>
    <dt><label for="ad">비밀번호</label></dt>
    <dd><input type="text" id="ad"></dd>
</dl>
```

이런 방법으로 제작하는 사람이 정말 드물겠지만\(?\), 이런 방법으로 마크업하는 사람도 있다. 물론 이것도 &lt;dl&gt;&lt;dt&gt;&lt;dd&gt;의 사용목적과 맞지 않다.

정의형\(설명형\) 목록에서 &lt;dd&gt;는 값이 바뀔 수 있다면, 그건 정의형이 될 수 없기 때문이다. 이미 정의가 되어 있거나 설명이 정해져 있는 경우에만 사용할 수 있는 태그인 것이다.

### 국내 포털 사이트에서는 잘 사용하고 있을까?

#### Daum의 메뉴

모 포털사이트의 메뉴 영역을 &lt;dl&gt;&lt;dt&gt;&lt;dd&gt;로 사용하고 있다.

![&#xB2E4;&#xC74C; &#xD3EC;&#xD138;&#xC0AC;&#xC774;&#xD2B8;&#xC758; &#xBA54;&#xB274;&#xB97C; dl, dt, dd&#xB85C; &#xC0AC;&#xC6A9; ](../../.gitbook/assets/image%20%2828%29.png)

```markup
<dl>
    <dt>커뮤니케이션</dt>
        <dd>메일</dd>
        <dd>카페</dd>
        <dd>블로그</dd>
        <dd>티스토리</dd>
        <dd>브런치</dd>
        <dd>아지트</dd>
        <dd>카카오스토리</dd>
</dl>
<dl>
    <dt>미디어</dt>
        <dd>뉴스</dd>
        <dd>스포츠</dd>
        <dd>연예</dd>
</dl>
.... 
```

위와 같이 마크업하였을 경우, 일단 가장 문제되는 것은 스크린리더 사용자들은 전체 메뉴구조를 파악할 수 없다는 것이다. 같은 제목 아래 한 개의 리스트로 있어야 존재해야 하는 항목은 단지 레이아웃 배치를 위해 9개의 &lt;dl&gt;을 사용하고 있다.  그리고 메뉴의 뎁스 구조를 &lt;dt&gt;&lt;dd&gt;로 표현했을 뿐 정의형도 아니고 설명을 위한 구조도 아닌 것이다. 

시맨틱하고 접근성을 고려한 마크업은 전체 1개의 &lt;ul&gt;로 제작하고 하위 &lt;ul&gt;태그로 구조화하는 것이 더 적절한 방법이다.

또 다른 포털사이트의 뉴스 페이지이다. 사진과 설명글을 &lt;dl&gt;&lt;dt&gt;&lt;dd&gt;로 마크업하였다.

#### 네이버의 뉴스

![&#xC774;&#xBBF8;&#xC9C0;&#xC640; &#xC774;&#xBBF8;&#xC9C0; &#xC124;&#xBA85;&#xC744; dl, dt, dd](../../.gitbook/assets/image%20%2813%29.png)

```markup
<dl>
    <dt><img src="비건.jpg" alt="훈련 끝 대화시작? 방한 비건에 쏠린 눈"></dt>
    <dd>훈련 끝 대화시작? 방한 비건에 쏠린 눈</dd>
</dl>  
```

HTML5에서는 description 의 역할이 가능하므로 이미지의 설명으로는 문제가 없을 것 같은 마크업이다. 하지만 소스를 들여다 보면, 이미지의 alt 속성의 값이 &lt;dd&gt;에 동일한 문구로 중복으로 삽입되는 것이 문제인 것이다.  시맨틱하게 마크업을 할 수 있다면 &lt;figure&gt;태그를 사용하는 것이 더 적절한 것이다.

### &lt;dl&gt;&lt;dt&gt;&lt;dd&gt;는 1:1로 쌍을 이룰 때 사용하는 것을 권장

스크린리더는 &lt;dt&gt;와 &lt;dd&gt;를 1:1로 쌍을 이룰 경우에 사용한 경우에 가장 정확한 의미를 읽어내어 스크린리더 사용자의 이해가 쉬워진다. 반드시 정의형이나 설명형을 만족하지 않더라도 제목과 데이터가 1:1로 쌍을 이룰 때만 사용하는 것이 좋다.

&lt;dt&gt;는 1개 이지만, &lt;dd&gt;가 2개 이상인 경우는 &lt;dl&gt;&lt;dt&gt;&lt;dd&gt; 태그 사용이 적합한지 다시 한번 생각해 보는 것이 좋다. 

{% hint style="info" %}
&lt;dl&gt; 태그 또한 &lt;ul&gt;이나 &lt;ol&gt;과 마찬가지로 화면에 보이는 병렬 배치를 위해 여러 개를 사용하지 않도록 해야 한다.  스크린리더 사용자는 몇 개의 리스트를 더 탐색해야  하는 건지 전혀 예측이 안되기 때문이다.
{% endhint %}

