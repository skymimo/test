# 🖼️ SVG 이미지의 접근성 향상 방법

## SVG(Scalable Vector Graphics)&#x20;

Svg는 웹 친화적인 벡터 이미지 파일로 JPEG와 같은 픽셀 기반의 래스터 파일과 달리 그리드 위의 점과 선을 기반으로 이미지를 표현한다. 이런 svg 파일은 작은 용량, 해상도에 관계없이 선명하게 표현할 수 있기 때문에 현대의 웹 사이트에서 아이콘이나 로고, 정보를 가진 그래픽으로 점점 더 광범위하게 사용하고 있다.

그렇다면 이렇게 많은 웹사이트나 모바일에서 사용하고 있는 svg 파일을 모든 사용자와 장애를 가진 사용자들도 이 정보를 가진 그래픽을 보고 이해할 수 있을까? &#x20;

svg를 사용할 때 접근성을 준수하는 방법은 여러 가지가 있다.

* **그래픽이 가지고 있는 정보를 스크린리더를 사용하는 사용자도 이해할 수 있는 대체텍스트를 제공해야 하고,**&#x20;
* **시각 장애가 있는 사용자를 위해 색상으로만 구분하지 않고**&#x20;
* **최소한의 명도대비를 준수해야 하고**&#x20;
* **컨텍스트가 가지고 있는 정보를 이해할 수 있는 시맨틱한 태그를 사용하고**&#x20;
* **인터랙션이 있다면 키보드도 접근할 수 있도록 개발도 필요하다.**&#x20;

다음 스크린샷은 웹 접근성이 잘 구현되어 있다는 Apple 웹사이트 중 일부이다.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p>애플 웹사이트 <a href="https://www.apple.com/apple-vision-pro/">https://www.apple.com/apple-vision-pro/</a></p></figcaption></figure>

요즘 핫한 Apple vision의 홍보 영상이고 상단 오른쪽에 애니메이션을 컨트롤 할 수 있는 버튼이 있다.  영상 재생을 일시 정지할 수 있는 아이콘을 svg로 제작하였는데 소스는 다음과 같다.

{% code overflow="wrap" %}
```html
<button aria-label="play Entertainment animation"></button>

<svg>																<circle class="progress-background" cx="50" cy="50" r="45"></circle>																<circle class="progress-circle" cx="50" cy="50" r="45" style="stroke-dasharray: 283; stroke-dashoffset: 171.134;"></circle>															</svg>
```
{% endcode %}

배경의 돌아가는 원과 가운데의 일시정지, 플레이 정보를 갖고 있는 아이콘 모두 svg로 제작되어 있고 영상의 길이만큼 원이 돌아가고 svg로 제작되었다. 영상 하단에는 홍보 영상에서 전달하고 싶은 정보가 따로 시각적인 텍스트로 있기 때문에 자막은 따로 넣지 않은 것 같다.

위 영상과 컨트롤 버튼을 탐색하면서 NVDA 스크린리더로 들어보면 다음과 같이 들린다.

> 그래픽 Person using Apple Vision Pro to view content animation _**// video 영상 설명**_
>
> 버튼 Pause entertainment animation _**// 일시 정지 버튼**_

영상의 제목, 설명, 버튼명과 상태를 스크린리더가 잘 읽고 있기 때문에 스크린리더를 사용하는 사용자들에게도 정보를 충분히 전달했고 버튼의 역할과 상태를 알 수 있기 때문에 접근성은 잘 준수했다고 볼 수 있다.&#x20;



***

### 좀 더 다르게 구현할 수 있는 방법은 없을까?

영상을 보게 되면 약 14초 동안 돌아가는 svg 애니메이션을 통해 알 수 있는 동영상의 길이가 있다. 이 정보도 알려주고 \<button> 태그 없이 \<svg>태그를 변경해서 다음과 같이 제작해 볼 수 있다.

<pre class="language-html" data-overflow="wrap"><code class="lang-html">&#x3C;svg tabindex="0" role="button" aria-labelledby="title desc"> 

     //버튼 기능 설명
    &#x3C;title id="title">Pause entertainment animation&#x3C;/title>
    //영상에 대한 추가 정보
    &#x3C;desc id="desc">소리 없이 14초 동안 재생되는 영상&#x3C;/desc>
    
<strong>    &#x3C;circle class="progress-background" cx="50" cy="50" r="45">&#x3C;/circle>
</strong><strong>    &#x3C;circle class="progress-circle" cx="50" cy="50" r="45" style="stroke-dasharray: 283; stroke-dashoffset: 68.4728;">&#x3C;/circle>														&#x3C;/svg>
</strong></code></pre>

`<svg>` 태그 자체가 버튼 역할을 할 수 있도록 `role="button"` 속성을 삽입하고 키보드 탭키가 이동할 수 있도록 `tabindex="0"`을 삽입한다. 그리고 버튼명과 영상의 길이를 `<title>, <desc>` 요소를 `<svg>` 안으로 삽입하여 대체텍스트를 제공한다. 마지막으로 `<svg>`에 `aria-labelledby` 속성과 `<title>, <desc>`의 id를 연결하여 스크린리더가 대체텍스트를 읽도록 설정하면 된다.

위와 같이 수정하고 키보드 tab키로 이동하면서 스크린리더로 들어보자.

> 그래픽 Person using Apple Vision Pro to view content animation _**// video 영상 설명**_
>
> Pause entertainment animation 버튼  소리 없이 14초 동안 재생되는 영상 _**// 일시정지 버튼으로 tab키 이동**_

위와 같이 `<button>` 태그를 따로 사용하지 않아도 `<svg>`자체에  ARIA로 동등한 정보를 스크린리더에서 읽을 수 있도록 제작할 수 있게 된다.&#x20;

정보를 가지고 있는 그래픽 요소를 위와 같이 `<title>`이나 `<desc>` 요소로 충분히 설명이 가능하며 구현 방법 또한 어렵지 않으니 위 방법을 참고하여 접근성을 준수하여 `svg`를 사용해 보자.

{% hint style="info" %}
`<svg>`가 인터랙션이 없는 경우는 `<svg>` 속성에 `role="img"도` 삽입할 수 있고 짧은 대체텍스트는 `aria-label="대체텍스트`"로 사용할 수도 있다.
{% endhint %}

{% hint style="warning" %}
`<svg>`를 NVDA 탐색할 때 가상 커서와 tab키 이동 시 읽는 방법이 다르다. 가상 커서로 읽을 때는 `<desc>`를 생략할 수 있으므로 중요한 정보를 가진 텍스트는 `<title>`에 넣는 것이 좋다.
{% endhint %}
