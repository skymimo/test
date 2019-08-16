# Screen Reader와 Browser 조합

### 스크린리더 사용자의 웹 브라우저 점유율

2017년 8월 [webaim.org](https://webaim.org/projects/screenreadersurvey7/)에서 조사한 미국 스크린리더 사용자의 웹브라우저 점유율로, Internet Explorer와 Firefox가 대부분을 차지하고 있다.

![](../../.gitbook/assets/image%20%2835%29.png)



###  스크린리더 사용자의 스크린리더 점유율

역시 webaim.org에서 조사한 내용으로 스크린리더별 점유율이다. 미국에서 스크린리더로는 JAWS와 NVDA를 가장 많이 사용하고 있다.

![](../../.gitbook/assets/image%20%2819%29.png)



### 스크린리더 사용자의 웹 브라우저와 스크린리더 조합

스크린리더와 브라우저도 궁합이 있다. 스크린리더의 기술이 W3C의 기술명세서만큼 빠르게 발전하지 못하기 때문에 가장 호환이 좋은 스크린리더와 브라우저 조합으로 스크린리더를 사용하게 된다.

아래 표를 보면 Internet Explorer에서는 JAWS를, Firefox에서는 NVDA를 가장 많이 사용하고 있다.

| Screen Reader & Browser | % |
| :--- | :--- |
|  **JAWS with Internet Explorer** |  **24.7%** |
|  **NVDA with Firefox** |  **23.6%** |
|  JAWS with Firefox |  15.1% |
|  VoiceOver with Safari |  10.0% |
|  JAWS with Chrome |  6.5% |
|  NVDA with Chrome |  5.9% |
|  NVDA with IE |  2.3% |

{% hint style="info" %}
ARIA로 제작한 위젯은 기본적으로 IE에서 JAWS를 실행하여 테스트하고, FF에서 NVDA를 실행하여 테스트를 하지만  **가장 중요한 위젯은 IE에서 JAWS와 NVDA, FF에서 JAWS와 NVDA를 모두 테스트한다.**
{% endhint %}

