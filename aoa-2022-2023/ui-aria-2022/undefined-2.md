# 비밀번호 실시간 오류 적용 사례

### 쿠팡 사이트에서 회원가입을 해볼까?

새벽배송과 다양한 상품을 쉽고 빠르게 구매할수 있어서 우리나라의 정말 많은 사람들이 사용하고 있는 쿠팡 사이트는 UX 디자인에서도 앞서간다는 호평을 듣고 있는 사이트이다.  이렇게 편리한 서비스가 장애인에게도 편리할까?

쿠팡에서 회원가입을 하면 다음과 같은 회원가입 화면이 보인다. 화면 공간을 효율적으로 사용하기 위해서인지 모르겠지만 입력박스 레이블은 입력박스 안에 삽입되어 있다.&#x20;

딱 보아도 웹접근성 이슈는 바로 보인다. \
레이블의 명도대비는 2.3:1 수준으로 상당히 미흡하며 레이블 또한 입력박스에 포커스가 이동하면 사라져서 사용자는 내가 무엇을 입력해야 하는지는 입력하던 내용을 모두 삭제해야 확인할 수 있다.&#x20;

<figure><img src="../../.gitbook/assets/image (78).png" alt="" width="375"><figcaption><p>쿠팡의 회원가입 화면</p></figcaption></figure>

### 그럼 비밀번호를 입력해볼까?

비밀번호 입력박스가 활성화되면 다음 3가지 조건을 화면에서 확인할 수 있다.&#x20;

입력박스에 입력을 하게 되면 조건이 맞게되면 체크표시로 변경되고 컬러도 녹색으로 변경되어 실시간으로 잘 입력하고 있는지를 확인할 수 있다.&#x20;

* 영문/숫자/특수문자 2가지 이상 조합 (8\~20자)
* 3개 이상 연속되거나 동일한 문자/숫자 제외
* 아이디(이메일) 제외

일부러 오류를 발생시키기 위해서 비밀번호를 12345로 입력하면 어떤 오류가 났는지 확인이 가능하고 화면의 오류 정보로 보면 3가지 입력 조건 중에서 아이디 제외라는 1가지 조건만 맞은 상태이고 2가지 조건이 맞지 않아 오류가 난 상태가 된다.&#x20;

<figure><img src="../../.gitbook/assets/스크린샷 2023-12-28 오전 10.25.51.png" alt="" width="375"><figcaption><p>실시간 오류 발생 화면</p></figcaption></figure>

그럼 이런 정보를 스크린리더를 사용하는 시각장애인들도 잘 확인할 수 있을까?  위와 같이 오류가 발생한 상태에서 직접 소스를 직접 확인해보자.

<pre class="language-html" data-overflow="wrap" data-line-numbers><code class="lang-html">&#x3C;div>
<strong>    &#x3C;input type="password" id="join-password-input" maxlength="20" 
</strong><strong>     aria-label="비밀번호">
</strong>    &#x3C;span aria-hidden="true">비밀번호&#x3C;/span>
&#x3C;/div>
&#x3C;div>
    &#x3C;div>
        &#x3C;span>&#x3C;i class="icon-cross-red">&#x3C;/i>&#x3C;/span>
        &#x3C;span>영문/숫자/특수문자 2가지 이상 조합 (8~20자)&#x3C;/span>
    &#x3C;/div>
<strong>    &#x3C;div>
</strong>        &#x3C;span>&#x3C;i class="icon-cross-red">&#x3C;/i>&#x3C;/span>
        &#x3C;span>3개 이상 연속되거나 동일한 문자/숫자 제외&#x3C;/span>
    &#x3C;/div>
    &#x3C;div>
        &#x3C;span>&#x3C;i class="icon-check-green">&#x3C;/i>&#x3C;/span>
        &#x3C;span>아이디(이메일) 제외&#x3C;/span>
<strong>    &#x3C;/div>
</strong>&#x3C;/div>
</code></pre>

위 소스로 확인하면 오류가 난 상태이지만 3가지 조건 텍스트는 변함이 없다. class로 아이콘과 색상이 변경되었음을 예측할 수 있지만 class는 스크린리더에 전혀 영향을 주지 못한다. 이렇게 비밀번호 입력에 오류가 발생한 상황도 인지할 수 없고 어떤 오류가 발생했는지도 알 수 없다.&#x20;

결국 이건 뭐 아무것도 알 수도 없다는 것이다.

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

이 상태를 NVDA 스크린리더로 들어보자.  혹시 모르니..

> <mark style="color:blue;">(비밀번호 입력박스 포커스 이동)</mark>&#x20;
>
> 비밀번호 편집창 보호됨 빈줄
>
> <mark style="color:blue;">(숫자 12345 입력)</mark>&#x20;
>
> star star star star star
>
> <mark style="color:blue;">(폼모드 벗어나서 아래 방향키로 하단 탐색)</mark>
>
> 영문/숫자/특수문자 2가지 이상 조합 (8\~20자)
>
> 3개 이상 연속되거나 동일한 문자/숫자 제외&#x20;
>
> 아이디(이메일) 제외

혹시나가 역시나다. 스크린리더는 그냥 조건만 열심히만 읽는다.

***

### 그럼 어떻게 수정할 수 있을까?

이를 수정할 수 있는 방안은 여러 가지가 있으며 그 중 다음 2가지 방법으로 수정할 수 있다.

1안. 오류가 발생하면 실시간으로 충족되지 못한 조건의 문구를 aria-live="assertive" 속성을 가진 노드 안에 실시간으로 삽입한다. 화면에 보이는 시각적인 3가지 조건 텍스트는 aria-hidden="true"를 삽입하여 스크린리더가 읽지 않게 한다

{% code overflow="wrap" %}
```markup
<div aria-live="assertive">
    <p>영문/숫자/특수문자 2가지 이상 조합(8~20자), 충족 안됨
    3개 이상 연속되거나 동일한 문자/숫자로 사용, 충족 안됨 </p>
</div>
<div aria-hidden="true">
    <div>
        <span><i class="icon-cross-red"></i></span>
        <span>영문/숫자/특수문자 2가지 이상 조합 (8~20자)</span>
    </div>
    <div>
        <span><i class="icon-cross-red"></i></span>
        <span>3개 이상 연속되거나 동일한 문자/숫자 제외</span>
    </div>
    <div>
        <span><i class="icon-check-green"></i></span>
        <span>아이디(이메일) 제외</span>
    </div>
</div>
```
{% endcode %}

2안. 화면에 보이는 입력 조건 전체를 감싸는 태그에 실시간으로 읽어주는 aria-live="assertive"속성과 변경되는 노드 전체를 읽어주는 aria-atomic="true"을 삽입한다. 비밀번호 입력할 때 3가지 조건 문장 뒤에 "충족안됨", "충족됨"이라는 문구를 동적으로 삽입하여 현재 상태를 스크린리더가 실시간으로 읽을 수 있도록 한다.

{% code overflow="wrap" %}
```html
<div aria-live="assertive" aria-atomic="true">
    <div>
        <span><i class="icon-cross-red"></i></span>
        <span>영문/숫자/특수문자 2가지 이상 조합 (8~20자), 충족 안됨</span>
    </div>
    <div>
        <span><i class="icon-cross-red"></i></span>
        <span>3개 이상 연속되거나 동일한 문자/숫자 제외, 충족 안됨</span>
    </div>
    <div>
        <span><i class="icon-check-green"></i></span>
        <span>아이디(이메일) 제외, 충족됨</span>
    </div>
</div>
```
{% endcode %}

두 가지 방법 모두 접근성을 준수하는 방법이 될 수 있으나 두 가지 중 한 가지를 선택한다면 2안보다는 1안이 더 수정하기 쉽고 스크린리더가 읽는 텍스트의 양으로 보아도 1안을 더 적절하다고 생각된다.

실제 구현 예시는 대한항공 홈페이지 회원가입 페이지에서 비밀번호 입력 박스를 참고할 수 있다.

<figure><img src="../../.gitbook/assets/image (79).png" alt=""><figcaption><p>대한항공 홈페이지 회원가입 페이지 스크린샷</p></figcaption></figure>

{% hint style="info" %}
비밀번호 입력 박스에서 한 글자씩 입력할 때마다 오류 문구를 읽게 하면 너무 많은 텍스트를 스크린리더가 자동으로 읽게 되어 스크린리더 사용자의 사용성을 현저히 저하시킬 수 있다. &#x20;

입력박스에서 한글자씩 입력할 때 보다 입력박스에서 입력을 모두 마친 후 포커스가 나갔을 때 오류를 발생시키는 것을 권장한다.
{% endhint %}

### 비장애인에게 너무 편리한 서비스 쿠팡.&#x20;

다양한 환경에서도 장애를 가진 사용자에게도 그 편리한 서비스를 경험하게 해 준다면 더욱 가치 있고 빛이 날 것이다. \
(쿠팡 관계자님들 여기좀 봐주세요\~\~네에?)

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt="" width="105"><figcaption></figcaption></figure>

















