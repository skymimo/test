---
description: 메세지는 1,000자 이내로 적어주세요(?)
---

# \<textarea> 입력 글자 수 제한 사례

## 네이버의 쪽지

네이버에서 쪽지 메뉴로 들어가면 다음과 같이 `<textarea>`가 있으며, 그 `<textarea>` 밑에는 **"33/1000자"** 가 있어서 글자 수 입력이 1,000자까지 제한이 있는 것으로 예상이 된다.

비장애인은 시각적 정보로 글자 수가 제한이 있음을 알 수 있지만 시각장애가 있는 스크린리더 사용자들은 어떻게 이 정보를 알 수 있을까?&#x20;

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>네이버의 쪽지</p></figcaption></figure>

네이버의 쪽지에 삽입된 `<textarea>` 구현된 소스는 다음과 같다.

{% code overflow="wrap" lineNumbers="true" %}
```html
<div class="writing_area">
    <textarea id="writeNote" style="resize:none;"    
     onkeyup="nWrite.checkContentLength();" rows="5" cols="55" 
     title="쪽지 내용을 입력해 주세요.">
    </textarea>
</div>
<div class="writing_option">
   <div class="character">
      <span id="noteLen">33</span> / <span id="noteMaxLen">1000</span>자
   </div>
</div>
```
{% endcode %}

`<textarea>`태그에 id가 삽입되어 있지만 `<label>`태그가 없어 연결할 수 있는 for도 찾을 수 없다. `<textarea>`를 스크린리더가 "편집창 멀티라인"으로 읽기 때문에 많은 글자 수를 입력할 수 있다는 것은 알지만 1,000자 이내로 입력해야 한다는 것은 스크린리더 사용자는 알 수 없다.

`<textarea>` 하단에 33/1000자 라는 정보가 있어서 예상할 수 있지만 스크린리더가 탐색하기 전까지는 스크린리더 사용자는 그 정보를 알 수 없다.

<figure><img src="../../.gitbook/assets/image.png" alt="" width="375"><figcaption></figcaption></figure>

위 이미지와 같이 사용자가 1,000자를 모두 입력하게 되면 브라우저 alert으로 1,000자 까지만 입력이 가능하다는 안내를 하지만 사용자는 `<textarea>`에서 1,000자 이상을 입력하기 전까지 몇 글자를 입력했는 지에 대한 정보를 알 수 없어  시용이 쉽지 않다.  (도대체 네이버는 \<label>도 왜 사용하지 않았을까...?)



## 대한항공 홈페이지 구현 사례

대한항공 홈페이지에서는 `<textarea>`를 마일리지몰 메뉴에서 찾을 수 있다. \
상품을 장바구니에 담고 나서 배송지 입력 시 배송메세지를 입력할 때 50자까지 입력 제한이 있는 `<textarea>`가 있다.

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

아래와 같이 시각적 레이블과 `<label>` 태그로 입력박스가 50자 이내 글자 수 제한이 있음을 정보 안내하고 있어 스크린리더 사용자가 글자 수 제한이 있다는 정보를 입력 전에 알 수 있다.

또한 **"총 50자 중 0자 입력"**을 `aria-live` 속성을 사용하여 실시간으로 입력한 글자 수를 안내하도록 구현하였고, 해당 노드에 id를 삽입하여 `<textarea>`의 `aria-describedby` 속성 값과 연결하였다.&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```markup
<div class="field">
    <label class="label" for="delivery"> 배송 메시지(50자 이내)</label>
    <div class="forms">
        <textarea aria-describedby="calcuateMessage" id="delivery" maxlength="50">
        </textarea>
    </div>
    <div class="counter">
        <span aria-hidden="true"><em>0</em>/50</span>
        <div aria-atomic="true" aria-live="off" class="_hidden" 
         id="calcuateMessage">
            <span>총 50자 중 <span>0</span>자 입력</span>
        </div>
    </div>
</div>
```
{% endcode %}

입력한 글자 수를 실시간으로 글자 수마다 `aria-live`로 안내하면 오히려 사용에 불편을 줄 수 있어 10글자가 단위로 입력이 되면 `aria-live=off`에서 `aria-live=polite`로 변경하여 사용자가 입력하는 데 방해가 되지 않도록 구현하였다. 알림 빈도 수는 처음은 10글자 단위로 안내하다가 제한 글자 수에 다다르면 높이는 방식으로 하였다.

스크린리더(NVDA)로 들어보면 다음과 같다.

> 배송 메세지(50자 이내) 편집창 멀티라인 총 50자 중 0자 입력
>
> ..10글자 입력..
>
> 총 50자 중 10자 입력
>
> ..20글자 입력..
>
> 총 50자 중 20자 입력
>
> ..30글자 입력..
>
> 총 50자 중 30자 입력
>
> ..35글자 입력..
>
> 총 50자 중 35자 입력

하지만 여기도 아쉬운 부분도 있다. 사용자가 50자를 모두 입력하면 별도의 안내 문구 없이 **"총 50자 중 50자 입력"**이라고만 반복 안내를 한다.&#x20;

50글자에 다다르면 <mark style="color:red;">"50자를 모두 입력하여 더 이상 입력할 수 없습니다"</mark>를 안내하여 사용자가 더 이상 입력하지 않도록 개선한다면 장애인, 비장애인 모두 쉽게 사용할 수 있을 것이다.&#x20;
