# role=application은 언제 사용할까?

### 복잡한 API를 개발했는데 어떻게 접근성을 준수할까?

UX 디자인이 부각되면서 다양한 인터페이스가 등장했지만 모든 브라우저에서 동일하게 지원하는 적절한 HTML의 태그가 없는 경우가 많다.\
(요즘은 정말 부족함을 자주 느낀다... HTML 태그도 많이 만들어주세요...)

### 정말 복잡한 위젯 Date Picker

![](<../../.gitbook/assets/image (38).png>)

날짜 선택이 필요하여 date picker 컴포넌트를 개발했지만 모든 브라우저에서 동등하게 호환이 가능한 HTML 태그도 부족하고, ARIA 속성이 없는데 이런 경우 `role="application"`을 사용할 수 있다.

**`role="application"`은 한 개 이상의 사용자의 인터랙션이 필요한 요소가 포함되었을 때 사용할 수 있는 Role 이다.** 하지만, `role="application"`은 스크린리더가 사용하고 있던 기본 키보드 조작 기능을 사용할 수 없게 하기 때문에 꼭 필요한 경우에만 신중히 사용해야 한다.

### **role="application"을 사용해야 할 때는 아래 3가지 조건 중 하나를 만족**

1. **모든 브라우저에서 동등하게 호환이 가능한 native HTML 태그가 없을 때,**
2. **ARIA에서 동일한 role이 없을 때,**
3. **만약에 동일한 ARIA role이 있지만, 보조기기에서 지원하지 않을 때**

`role="application"` 영역은 스크린리더가 사용하고 있던 단축키와 같은 키보드 사용방법을 후킹하기 때문에 키보드 인터랙션 방법을 반드시 제공 해야 한다.

Date Picker 의 경우 모든 브라우저에서 호환이 가능한 HTML이 없고, ARIA role도 동일한 기능이 없기 때문에 사용했고, 스크린리더 사용자와 키보드 사용자를 위해 시각적으로 키보드 운용방법을 제공하였다.

```markup
<div>키보드 운용방법 :  화살표 키로 날짜를 탐색하고 Enter키로 날짜를 선택할 수 있습니다.</div>
<div role="application">
date picker 영역
</div>
```

{% hint style="info" %}
role="application"을 사용하기 바로 전에 application 영역이 있다는 것을 사전에 알려주고 키보드 운용방법을 알려주는 것이 가장 좋은 방법이다.
{% endhint %}

스크린리더로 들어보면 아래와 같다.

> 키보드 운용방법 : 화살표 키로 날짜를 탐색하고 Enter키로 날짜를 선택할 수 있습니다.\
> application

{% hint style="danger" %}
role="application"을 사용하면 키보드 인터랙션 구현이 쉬워지기 때문에 불필요함에도 불구하고 사용하여 구현하는 경우가 있는데 절대 그런 목적으로 사용해서는 안된다.
{% endhint %}

