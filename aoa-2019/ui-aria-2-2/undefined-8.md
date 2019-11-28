# 툴팁 적용 사례

### 읽어야 하는 툴팁과 읽지 않아야 하는 툴팁

홈페이지에서 사용하고 있는 툴팁은 2가지 종류가 있다. 화면 공간이 좁아 소스 상으로는 텍스트가 있지만 말줄임으로 표현한 경우가 있고, 약어를 이해하기 쉽도록 보여주는 설명하는 툴팁이 있다. 

role="tooltip"으로 구현도 가능하지만, 읽지 않아야 하는 툴팁 기능도 포함되어 있어 여기서는 role 속성 없이 제작해 보았다.

각각의 화면 예제와 구현된 소스는 아래와 같다.

#### 약어를 설명하는 읽어야 하는 툴팁

KE는 대한항공을 뜻하고, DL은 델타항공을 뜻한다. 이처럼 모든 항공사는 2글자 약어를 갖고 있는데 일반 사용자는 이해하기 어렵기 때문에 아래 화면과 같이 설명을 제공하는데 스크린리더 사용자도 읽어야 하는 툴팁이다.

![](../../.gitbook/assets/image%20%2829%29.png)

"KE" 영역은 &lt;a&gt;로 마크업하고 동작하지 않으므로 `role="presentation"`과 aria-disabled를 삽입하여 스크린리더 사용자가 링크로 오해하지 않도록 제작하고 "KE"는 `aria-hidden="true"`로 스크린리더에서 읽지 않게 하고 실제 읽어야 하는 "대한항공"은 숨김 텍스트로 삽입하여 가상 모드나 브라우즈 모드에서 "대한항공"만 읽히게 한다.

마크업 화면은 다음과 같다.

```markup
<a href="#" class="tooltip" aria-disabled="true" role="presentation">
    <span class="offscreen">대한항공</span>
    <span aria-hidden="true">KE</span>
</a>
```

#### 말줄임을 보여주는 읽지 않아도 되는 툴팁

화면 공간의 제약상 긴 공항명은 말줄임으로 표현하고 말풍선을 통해 풀네임을 보여주고 있다. 실제 DOM안에는 풀네임으로 존재하므로 중복으로 스크린리더가 읽을 필요가 없다.

![](../../.gitbook/assets/image%20%2819%29.png)

말줄임으로 표현해야 하는 영역은 일반 div나 span으로 제작하고 키보드 포커스가 동작하도록 `tabindex="0"`을 삽입한다. 그리고 실제 DOM에서 확인하면 해당 텍스트는 두 개가 중복된다. 중복된 내용을 스크린리더에서 읽지 않도록 `aria-hidden="true"`를 삽입하면 된다. 읽어야 하는 툴팁보다는 아주 간단히 해결이 가능하다.

```markup
<span class="ellipsis" tabindex="0">
    New York-John F.Kennedy(JFK)
</span>
<span class="tooltip" aria-hidden="true">
    New York-John F.Kennedy(JFK)
</span>
```

