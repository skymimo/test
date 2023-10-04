---
description: 그룹에 발생한 오류도 그룹화하여 제공하자
coverY: 0
---

# 🕹 Form 그룹의 오류 적용 사례

Radio 버튼으로 구성된 Radio 그룹이나 여러 개의 Checkbox로 구성된 Checkbox 그룹을 사용해야 하는 경우가 있다. 비장애인은 시각적으로 그룹화 정보를 인식할 수 있지만 스크린리더 사용자들은 어떻게 그룹화된 정보를 인지할 수 있을까?&#x20;

그룹으로 된 Form을 사용할 때 오류 메시지는 어떻게 구현하는 것이 접근성을 준수하면서 사용성까지 만족할 수 있을 지에 대해서 알아보자.



_(사전지식 : 폼 그룹의 필수 항목 적용하는 방법)_

{% embed url="https://aoa.gitbook.io/skymimo/aoa-2019/2019-aria/group-label" %}

### **Radio 그룹 오류**

<div align="left">

<figure><img src="../../.gitbook/assets/스크린샷 2023-09-20 오후 2.58.18.png" alt="" width="375"><figcaption></figcaption></figure>

</div>

항공권을 조회할 수 있는 기능이고 4개의 Radio 버튼으로 구현하였다. 아무것도 선택하지 않고 submit 버튼을 누르면 위 스크린샷과 같이 오류 메세지가 그룹 영역 하단에 바로 노출된다.

소스는 다음과 같다.

{% code overflow="wrap" %}
```html
<h3 id="timerange">항공권 조회 기간</h3>
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

라디오 그룹 전체를 `<fieldset>`으로 묶고, `<legend>`태그에 제목을 삽입하고 하단 \<div>태그 안에 라디오 버튼을 감싸게 마크업한다. 그리고 오류가 발생하면 `<legend>`태그 안에 오류 메시지가 동적으로 삽입되고 포커스는 첫번째 라디오 버튼으로 이동시킨다.

이렇게 구현하면 NVDA에서는 다음과 같이 읽는다. 그룹이라는 단어의 출력 순서만 바뀌었을 뿐 첫번째에서 구현한 것과 큰 차이는 없다.&#x20;

> 항공권 조회 기간  \
> 조회를 원하는 달을 선택하세요 그룹
>
>> 9월 라디오 버튼 해제됨 4개 중 1번 째

2가지 방법 모두 단순하고 쉬운 방법이므로 상황에 맞게 구현해 보는 것을 권장한다.



***

###

### Checkbox 그룹 오류

Radio 그룹과 비슷한 Checkbox 그룹 오류도 다음과 같은 사례가 있다.

<div align="left">

<figure><img src="../../.gitbook/assets/스크린샷 2023-09-20 오후 2.49.58.png" alt="" width="563"><figcaption></figcaption></figure>

</div>

환불 전 동의 사항에 대한 내용을 한 개의 컨테이너 안에 넣고 전체에 대한 동의 체크박스를 2개를 배치한 사례이다. 위 사례와 마찬가지로 시각적으로 보여지는 박스 레이아웃 디자인으로 비장애인은 정보가 그룹화되어 있음을 바로 인지할 수 있다.

그럼 스크린리더 사용자들에게 어떻게 그룹화된 정보를 인지시킬 수 있을 지 `role=radio`와 `aria-labelledby`를 어디까지 묶어야 할 지 확인해 보자.

소스 구현 사례이다.

{% code overflow="wrap" %}
```html
<h3 id="agree-contents">환불 신청 전 동의 사항</h3>
<div role="group" aria-labelledby="agree-contents" aria-describedby="error-massege">
    <ul>
        <li>환불 수수료는 최초 지불 수단에서 공제됩니다.</li>
        <li>신용카드로 구매한 환불금은 승인 후 카드사로 이관되므로 환불금 수령시기는 해당 카드사에 문의해 주세요.</li>
        <li>환불에 대한 책임은 신청자 본인에게 있습니다.</li>
    </ul>
    <input type="checkbox" id="agree1">
    <label for="agree1">[동의] 환불 방법을 확인하였습니다.</label>
    <input type="checkbox" id="agree2">
    <label for="agree2">[동의] 위의 내용에 대해 모두 확인하였습니다.</label>
</div>
<!-- 에러 메시지 -->
<p id="error-massege">첫번째 항목에 동의해 주세요</p>
```
{% endcode %}

Checkbox 그룹을 `<div role="group">`으로 묶고 `aria-labelledby` 속성과 \<h3>의 id값을 삽입하여 그룹의 제목과 연결한다. 오류가 발생하면 `aria-describedby` 속성과 오류 문구의 id 값을 연결하고 포커스는 첫 번째 체크박스로 포커스를 이동시킨다.

다른 대안으로는 마찬가지로 `<fieldset><legend>`로 묶는 방법이 있다.

{% code overflow="wrap" %}
```html
<fieldset>
    <legend>환불 신청 전 동의 사항
        <!-- 에러 메시지 -->
        <p id="error-massege">첫번째 항목에 동의해 주세요</p>
    </legend>
    <div>
        <ul>
            <li>환불 수수료는 최초 지불 수단에서 공제됩니다.</li>
            <li>신용카드로 구매한 환불금은 승인 후 카드사로 이관되므로 환불금 수령시기는 해당 카드사에 문의해 주세요.</li>
            <li>환불에 대한 책임은 신청자 본인에게 있습니다.</li>
        </ul>
        <input type="checkbox" id="agree1">
        <label for="agree1">[동의] 환불 방법을 확인하였습니다.</label>
        <input type="checkbox" id="agree2">
        <label for="agree2">[동의] 위의 내용에 대해 모두 확인하였습니다.</label>
    </div>
</fieldset>
```
{% endcode %}

`<fieldset>` 태그 안에 동의 사항과 체크박스 내용을 모두 삽입하고 `<legend>`에 제목을 삽입하고 오류가 발생하면 오류 문구를 동적으로 삽입한다. 이렇게 구현하고 NVDA로 들어보면 다음과 같다.

> 환불 신청 전 동의 사항\
> 첫번째 항목에 동의해 주세요 그룹\
> \[동의] 환불 방법을 확인하였습니다. 체크상자 해제 됨

이렇게 구현하면 그룹 정보와 오류 내용을 그룹화하여 잘 읽어 주게 되므로 스크린리더 사용자들도 쉽게 사용할 수 있게 된다.&#x20;

{% hint style="warning" %}
현재 chceckbox 그룹을 `<div role="group">`으로 묶고 `aria-describedby` 속성과 오류 문구를 연결하는 경우 NVDA 스크린리더에서 제대로 오류 문구를 읽지 않는 버그가 있다. 그 버그가 해결되기 전까지 `<fieldset><legend>`로 구현하는 것을 사용할 것을 권장한다.
{% endhint %}
