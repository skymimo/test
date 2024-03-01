# SVG 이미지의 접근성 향상 방법

## SVG(Scalable Vector Graphics)&#x20;

Svg는 웹 친화적인 벡터 이미지 파일로 JPEG와 같은 픽셀 기반의 래스터 파일과 달리 그리드 위의 점과 선을 기반으로 이미지를 표현한다. 이런 svg 파일은 작은 용량, 해상도에 관계없이 선명하게 표현할 수 있기 때문에 현대의 웹 사이트에서 아이콘이나 로고, 정보를 가진 그래픽으로 점점 더 광범위하게 사용하고 있다.

그렇다면 이렇게 많은 웹사이트나 모바일에서 사용하고 있는 svg 파일을 모든 사용자와 장애를 가진 사용자들도 이 정보를 가진 그래픽을 보고 이해할 수 있을까? &#x20;

svg를 사용할 때 접근성을 준수하는 방법은 여러 가지가 있다.

1. **그래픽이 가지고 있는 정보를 스크린리더를 사용하는 사용자도 이해할 수 있는 대체텍스트를 제공**해야 하고,&#x20;
2. 시각 장애가 있는 사용자를 위해 색상으로만 구분하지 않고&#x20;
3. 최소한의 명도대비를 준수해야 하고&#x20;
4. 컨텍스트가 가지고 있는 정보를 이해할 수 있는 시맨틱한 태그를 사용하고&#x20;
5. 키보드도 접근할 수 있도록 개발도 필요하다.&#x20;

웹 접근성이 잘 구현되어 있는 Apple 웹사이트 중 일부이다.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>애플 웹사이트 <a href="https://www.apple.com/apple-vision-pro/">https://www.apple.com/apple-vision-pro/</a></p></figcaption></figure>

요즘 핫한 Apple vision의 홍보 영상이고 상단 오른쪽에 애니메이션를 컨트롤 할 수 있는 버튼이 있다.  영상 재생을 일시 정지할 수 있는 아이콘을 svg로 제작하였는데 소스는 다음과 같다.

{% code overflow="wrap" %}
```html
<button aria-label="play Entertainment animation">
::before
::after
</button>
<svg>																<circle class="progress-background" cx="50" cy="50" r="45"></circle>																<circle class="progress-circle" cx="50" cy="50" r="45" style="stroke-dasharray: 283; stroke-dashoffset: 171.134;"></circle>															</svg>
```
{% endcode %}

배경의 돌아가는 원과 가운데의 일시정지, 플레이 정보를 갖고 있는 아이콘 모두 svg로 제작되어 있고 영상의 길이만큼 원이 돌아가고 svg로 제작되었다. 영상 하단에는 홍보 영상에서 전달하고 싶은 정보가 따로 시각적인 텍스트로 있기 때문에 자막은 따로 넣지 않은 것 같다.

위 영상과 컨트롤 버튼을 탐색하면서 NVDA 스크린리더로 들어보면 다음과 같이 들린다.

> 헤딩 레벨2 Entertaionment // 제목 읽기
>
> The ultimate theater // 제목 아래 문구 읽기
>
> Where you are // 제목 아래 문구 읽기
>
> 그래픽 Person using Apple Vision Pro to view content animation // video 영상 설명
>
> 버튼 Pause entertainment animation // 일시 정지 버튼

영상의 제목, 설명, 버튼명과 상태를 스크린리더가 잘 읽고 있기 때문에 스크린리더를 사용하는 사용자들에게도 정보를 충분히 전달했고 버튼의 역할과 상태를 알 수 있기 때문에 접근성은 잘 준수했다고 볼 수 있다.&#x20;



### 다르게 구현할 수 있는 방법은 없을까?

필수는 아니겠지만 영상을 보게 되면 svg 애니메이션을 통해 알 수 있는 영상의 길이가 있다. 여기서 우리는 Apple에서 구현한 방법보다 좀 더 접근성을 개선할 수 있도록 다음과 같이 소스를 변경해 보았다.

```
// Some code
<svg tabindex="0" data-inline-media-control="PlayProgress" class="play-progress-circle" viewBox="0 0 100 100" role="button" aria-labelledby="title desc"> 
    <title id="title">play Entertainment animation</title>
    <desc id="desc">
        Large red circle with a black border
    </desc>

																<circle class="progress-background" cx="50" cy="50" r="45"></circle>
																<circle class="progress-circle" cx="50" cy="50" r="45" style="stroke-dasharray: 283; stroke-dashoffset: 68.4728;"></circle>
															</svg>
```
