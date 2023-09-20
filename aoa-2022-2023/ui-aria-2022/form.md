---
description: Radio 그룹, Ckeckbox 그룹에서 오류가 발생했다
coverY: 0
---

# 🕹 Form 그룹 오류 적용 사례

Radio 버튼으로 구성된 Radio 그룹이나 여러 개의 Checkbox로 구성된 Checkbox 그룹을 사용해야 하는 경우가 있다. 이렇게 그룹으로 된 Form을 사용할 때 오류 메시지는 어떻게 구현하는 것이 접근성을 준수하면서 사용성까지 만족할 수 있을 지에 대해서 알아보자.



다음과 같이 Radio 그룹으로 된 사례가 있다.

<div align="left">

<figure><img src="../../.gitbook/assets/스크린샷 2023-09-20 오후 2.58.18.png" alt="" width="375"><figcaption></figcaption></figure>

</div>

항공권을 조회할 수 있는 기능이고 4개의 Radio 버튼으로 구현하였다. 아무것도 선택하지 않고 submit 버튼을 누르면 위 스크린샷과 같이 오류 메세지가 그룹 영역 하단에 바로 노출된다.

소스는 다음과 같다.

{% code overflow="wrap" %}
```html
<h3 id="cagetype">Cage Type</h3>
<div role="group" aria-labelledby="cagetype">
    <input name="cageType" type="radio" id="cageTypeHard1">
    <label for="cageTypeHard1">Hard</label>
    <input name="cageType" type="radio" id="cageTypeSoft1" >
    <label for="cageTypeSoft1">Soft</label>
</div>
<!-- 에러메시지 -->
<p id="cagetype-error">조회를 원하는 달을 선택하세요</p>
```
{% endcode %}

