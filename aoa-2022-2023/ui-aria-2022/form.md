---
description: Radio 그룹, Ckeckbox 그룹에서 오류가 발생했다
coverY: 0
---

# 🕹 Form 그룹 오류 적용 사례

Radio 버튼으로 구성된 Radio 그룹이나 여러 개의 Checkbox로 구성된 Checkbox 그룹을 사용해야 하는 경우가 있다. 이렇게 그룹으로 된 Form을 사용할 때 오류 메시지는 어떻게 구현하는 것이 접근성을 준수하면서 사용성까지 만족할 수 있을 지에 대해서 알아보자.

### **Radio 그룹 오류**

<div align="left">

<figure><img src="../../.gitbook/assets/스크린샷 2023-09-20 오후 2.58.18.png" alt="" width="375"><figcaption></figcaption></figure>

</div>

항공권을 조회할 수 있는 기능이고 4개의 Radio 버튼으로 구현하였다. 아무것도 선택하지 않고 submit 버튼을 누르면 위 스크린샷과 같이 오류 메세지가 그룹 영역 하단에 바로 노출된다.

소스는 다음과 같다.

{% code overflow="wrap" %}
```html
<h3 id="timerange">ㅇ</h3>
<div role="group" aria-labelledby="timerange" aria-describedby="timerange-error">
    <input name="range" type="radio" id="nine">
    <label for="nine">9월</label>
    <input name="range" type="radio" id="ten" >
    <label for="ten">10월</label>
    <input name="range" type="radio" id="eleven" >
    <label for="eleven">11월</label>
    <input name="range" type="radio" id="twelve" >
    <label for="twelve">12월</label>
</div>
<!-- 에러메시지 -->
<p id="timerange-error">조회를 원하는 달을 선택하세요</p>
```
{% endcode %}

전체 Radio 그룹을 `role="group"`으로 묶고 `aria-labelledby`로 상위 `<h3>`의 제목의 id와 연결한다.  Radio 그룹의 오류이므로 오류 문구는 `role="group"`속성을 갖고 있는 `<div>` 태그에 `aria-describedby` 속성을 삽입하고 오류문의 id와 연결한다.&#x20;

오류가 발생했을 때 포커스는 Radio 그룹의 첫번째 항목으로 포커스를 이동시킨다. 이렇게 하면 <mark style="color:green;background-color:yellow;">그룹 레이블과 그룹 오류를 한 번에 읽고 있어서 스크린리더 사용자도 쉽게 이해할 수 있는 UI</mark><mark style="color:blue;">가</mark> 될 수 있다.

\
**스크린리더 NVDA는 다음과 같이 읽게 된다.**

> 항공권 조회 기간 그룹 \
> 조회를 원하는 달을 선택하세요
>
>> 9월 라디오 버튼 해제됨 4개 중 1번 째

위 구현 방법 외에도 \<filedset>\<legend>를 활용하는 방법도 있다. 다음 소스를 확인해보자.

```html
<fieldset>
    <legend>항공권 조회 기간
        <!-- 에러메시지 -->
        <p id="timerange-error">조회를 원하는 달을 선택하세요</p>
    </legend>
    <div>
        <input name="range" type="radio" id="nine">
        <label for="nine">9월</label>
        <input name="range" type="radio" id="ten" >
        <label for="ten">10월</label>
        <input name="range" type="radio" id="eleven" >
        <label for="eleven">11월</label>
        <input name="range" type="radio" id="twelve" >
        <label for="twelve">12월</label>
    </div>
</fieldset>
```

`role=group`과 `aria-labelledby, aria-decribedby` 속성을 삭제하고 전체를 `<fieldset>`으로 묶는다. `<legend>` 태그에 제목을 삽입하고, 오류가 발생했을 때 `<legend>` 태그 안에 노드로 삽입한다.

이렇게 구현하면 NVDA에서는 다음과 같이 읽는다. 그룹이라는 단어의 출력 순서만 바뀌었을 뿐 첫번째에서 구현한 것과 큰 차이는 없다.&#x20;

> 항공권 조회 기간  \
> 조회를 원하는 달을 선택하세요 그룹
>
>> 9월 라디오 버튼 해제됨 4개 중 1번 째

2가지 방법 모두 단순하고 쉬운 방법이므로 상황에 맞게 구현해 보는 것을 권장한다.

### Checkbox 그룹 오류

Radio 그룹과 비슷한 Checkbox 그룹 오류도 다음과 같은 사례가 있다.

<div align="left">

<figure><img src="../../.gitbook/assets/스크린샷 2023-09-20 오후 2.49.58.png" alt="" width="563"><figcaption></figcaption></figure>

</div>

환불 전 동의 사항에 대한 내용을 한 개의 컨테이너 안에 넣고 전체에 대한 동의 체크박스를 2개를 배치한 사례이다.

role=radio와 aria-labelledby를 어디까지 묶어야 할까? 소스로 확인해 보자.
