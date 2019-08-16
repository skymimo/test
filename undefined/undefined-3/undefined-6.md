# 확장과 축소 콘텐츠 적용 사례

### 국가/언어 선택 영역

Region/Language 버튼을 선택하면 국가와 언어를 선택할 수 있는 콘텐츠가 확장되는데 확장/축소 기능의 대표적인 사례이다.

다이얼로그와 비슷해 보이지만  다이얼로그는 아니므로 `role="dialog"`는 사용하지 않아야 한다.

![](../../.gitbook/assets/image%20%289%29.png)

확장과 축소 기능은 가장 쉽고 많이 사용하는 기능 중에 하나이다. 사용도 쉽고 간편한 것처럼 스크린리더 사용자에게도 간단한 ARIA의 사용으로 시각적으로 보여지는 것처럼 알려줄 수 있다.

### aria-expanded와 aria-controls

확장과 축소가 되는 버튼 영역은 &lt;button&gt;으로 마크업하고, 확장되었을 때는 `aria-expanded="true"`, 축소되었을 때는 `aria-expanded="false"`를 삽입한다. 그리고 확장과 축소되는 콘텐츠의 컨테이너의 id와 aria-controls로 연결한다.

aria-expanded를 사용하면 확장이나 축소된 상태를 스크린리더가 읽게 되므로, 숨김텍스트로 상태를 중복으로 제공하지 않도록 해야 한다.

```markup
<button aria-controls="site-select" aria-expanded="true">Region/Language</button>
<div id="site-select" aria-hidden="false">
    <label for="utilnav-country-selector">Select a country/region</label>
    ...
</div>
```

### 키보드의 포커스 이동

버튼을 눌러 콘텐츠가 확장되면 포커스는 그대로 버튼 요소에 유지되어야 하고 tab키로 콘텐츠 안으로 이동해야한다. 그리고 콘텐츠 안에서 포커스가 밖으로 나가게 되면 확장 콘텐츠는 닫힌다. 

스크린리더로 읽어보면 다음과 같이 들리게 된다.

> Region/Language 버튼  
> 확장됨

{% hint style="info" %}
확장 콘텐츠가 배경 콘텐츠를 가리게 되는 경우에 포커스가 나가게 되면 확장된 콘텐츠를 닫아야  하고 그렇지 않은 경우에는 닫히지 않아도 된다.
{% endhint %}

