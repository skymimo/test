---
description: WCAG2.1의 1.4.13 Content on Hover or Focus
---

# 호버 콘텐츠 적용사례

### 호버 콘텐츠는 툴팁과 같이 마우스 호버일 때 추가로 보여지는 콘텐츠를 의미하며, WCAG2.1 에서는 아래 3가지를 모두 준수해야 한다고 정의되어 있다.

1. 호버 콘텐츠를 삭제할 수 있는 방법을 제공해야 한다.
2. 호버 콘텐츠가 사라지지 않은 상태로 호버 콘텐츠 위로 포인터를 이동시킬 수 있어야 한다.
3. 사용자가 호버 콘텐츠를 닫거나 마우스 호버나 키보드 포커스가 제거되기 전까지 호버 콘텐츠는 계속 보여져야 한다.

### 기내 어매니티를 툴팁으로 제공하는 방법!

대한항공 항공편 선택 페이지에서는 항공편명 정보를 탐색하다가 "상세 보기" 버튼을 누르면 해당 편명에서 제공하는 어매니티를 볼 수 있다. 이 콘텐츠는 호버 콘텐츠로 마우스 커서나 키보드 포커스가 이동하면 상세 설명이 텍스트로 노출되는 형태로  다음 영상과 같이 구현되어 있다.

{% embed url="https://youtu.be/VDpRV4pE8rU" %}

위 영상처럼 마우스 호버나 키보드 포커스를 받으면 추가 콘텐츠가 노출되는 형태는 WCAG2.1의 1.4.13. Content on Hover or Focus 와 관련이 깊다. 비장애인은 마우스를 이용하여 바로 노출되는 콘텐츠를 쉽게 볼 수 있지만 키보드 사용자나 스크린리더를 사용하는 시각장애인도 추가 콘텐츠를 쉽게 인식할 수 있도록 제작되어야 한다.

이 콘텐츠를 \<div>태그로 구현한다면 코드는 다음과 같다.

{% hint style="info" %}
role="tooltip"은  스크린리더에서 호환성이 떨어져 사용하지 않았다.
{% endhint %}

```html
<div class="tooltip" aria-disabled="true" role="button" tabindex="0">
    <span aria-hidden="true" class="flight-plan__amenity"></span> // 아이콘
    <div class="tooltip__desc">
        <span class="tooltip__text">기내 전원 공급 장치</span>
    </div>
</div>
```

위 코드를 보면 기내 어메니티를 \<div> 태그로 감싸고 `tabindex="0"`을 삽입하여 키보드 포커스 이동할 수 있게 하였다. 또한 아무 의미가 없는 \<div>가 포커스를 가지게 되면 스크린리더 사용자는 당황할 수 밖에 없고 이 태그가 어떤 역할인지 이해하기 어렵게 되므로 `role="button"`을 삽입하여 이 태그가 버튼의 역할을 수행하고 있다는 것을 알려야 한다.

버튼으로 구현되었지만 화면에서의 변화만 있는 역할만 하기 때문에 `aria-disabled="true"`를 삽입하여 이 버튼이 활성화되지 않는다는 것을 스크린리더에게 알릴 수 있다.

화면에 보이는 것은 콘센트 아이콘이지만 스크린리더가 읽어야 하는 것은 **"기내 전원 공급 장치"**이므로 말풍선 형태로 보이는 텍스트를 버튼 텍스트로 삽입하면 해당 버튼에 스크린리더가 이동하면 "기내 전원 공급 장치"로 인지하게 된다.

### title 속성과 똑같은 기능 아닌가요? title로 쓰면 안되나요?

<figure><img src="../../.gitbook/assets/스크린샷 2023-04-09 오후 7.40.19.png" alt=""><figcaption></figcaption></figure>

{% code overflow="wrap" lineNumbers="true" %}
```html
<button id="search_btn" type="submit" title="검색" tabindex="3" class="btn_submit" onclick="window.nclick(this,'sch.action','','',event);" style="">
    <span class="blind">검색</span>
    <span class="ico_search_submit"></span>
</button>
```
{% endcode %}

위 예제와 같이 title 속성을 사용하면 마우스 호버 시 비장애인에게는 시각적 정보로 보여줄 수 있지만, 호버 콘텐츠 위로 포인터가 이동하지 않고 키보드 포커스가 이동해도 보여지지 않기 때문에 장애인에게 동등한 정보를 제공해 주기 어렵다..com

{% embed url="https://naver.com" %}

또한 모바일과 같은 디바이스는 호버가 동작하지 않기 때문에 사용성에 더욱 좋지 않으므로 title 속성으로 대체 제공하는 것은 부적절한 방법이다.&#x20;

###
