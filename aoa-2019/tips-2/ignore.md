# 제발 나를 무시해 주세요.

### 스크린리더가 이미지를 무시하는 가장 좋은 방법

스크린리더가 이미지를 읽지 못하게 하는 방법은 여러 가지가 있지만 가장 호환성이 좋아 추천하는 방법은 다음과 같다.

#### css의 background 속성 사용

```css
{background-image: url("bg.gif");}
```

#### &lt;img&gt; 태그에 alt 속성을 빈 값으로 사용

```markup
<img src="spacer.gif" alt="">
```

#### &lt;img&gt; 태그에 aria-hidden 사용

```markup
<img src="bg.jpg" aria-hidden="true">
```

#### &lt;img&gt; 태그에 role="presentation" 사용

```markup
<img src="bg.jpg" role="presentation">
```

### 스크린리더가 아이프레임을 무시하는 가장 좋은 방법

비어 있는 아이프레임을 사용할 때 스크린리더가 읽지 않게 하는 가장 좋은 코드는 다음과 같다.

```markup
<iframe role="presentation" tabindex="-1" title="hidden"></iframe>
```

### 이미지 폰트를 사용할 때 주의해 주세요.

스크린리더가 가상선택자를 읽기 때문에 이미지 폰트를 사용하는 경우는 특별히 주의해야 한다.

이미지 폰트로 사용할 때 가장 흔히 사용하는 방법은 아래 두 가지이다.

![address &#xC544;&#xC774;&#xCF58;](../../.gitbook/assets/image%20%2868%29.png)

```markup
.icon-address:before {content: "p";} //1번 방법
.icon-address:before {content: "/f02f";} //2번 방법
```

css의 가상 선택자로 :before 또는 :after 를 사용하여 content로 불러오는 방법으로, 위  두 가지 방법 모두 스크린리더가 읽게 된다. 

1번 방법으로 사용하게 되면 스크린리더는 해당 영역을 "p"로 읽게 되어 스크린리더 사용자는 무엇을 읽는지 알 수 없게 된다. 2번 방법으로 사용하면 스크린리더는 해당 문구를 읽으려고 부단히도 애를 쓰지만 역슬래시에서 무엇을 말해야 할지 알 수 없어 아무것도 읽지 않는다.

#### 그렇다면 가장 좋은 방법은 무엇일까?

이미지 폰트를 스크린리더가 읽지 못하도록 `aria-hidden="true"` 속성을 삽입하고 숨김텍스트로 그 의미를 삽입하면 스크린리더는 해당 의미를 정상적으로 읽게 된다.

```markup
<a href="../icon/address">
    <i class="icon-address" aria-hidden="true"></i>
    <span class="offscreen">address</span>
</a>
```

