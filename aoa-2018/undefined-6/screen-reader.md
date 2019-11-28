# Screen Reader와 Browser 조합

### 스크린리더 사용자의 웹 브라우저 점유율

2019년 9월 [webaim.org](https://webaim.org/projects/screenreadersurvey7/)에서 조사한 미국 스크린리더 사용자의 웹브라우저 점유율이다. 절반 정도가 Chrome을 사용하고 있으며 점유율은 44%,  Firefox 27%, Internet Explorer 11% 차지하고 있다.

![](../../.gitbook/assets/image%20%2821%29.png)

{% hint style="info" %}
2015~2016년도 미국 접근성 개선 프로젝트 당시에는 절반 이상이 Internet Explorer를 사용하여 그 기준으로 개선하으나 그 이후 Internet Explorer 점유율이 급속도로 추락하고 있다.
{% endhint %}

###  스크린리더 사용자의 스크린리더 점유율

역시 webaim.org에서 조사한 내용으로 스크린리더별 점유율이다. 미국에서 스크린리더로는 JAWS와 NVDA를 가장 많이 사용하고 있다.

![](../../.gitbook/assets/image%20%2870%29.png)

{% hint style="info" %}
스크린리더 점유율도 2015~2016년도와 비교했을 때 다소 차이가 있다. 1위였던 JAWS가 NVDA에게 1위를 내주고 점유율이 떨어지고 있다. 무료로 사용 가능한 NVDA는 앞으로도 계속 점유율이 상승할 것으로 보인다.
{% endhint %}



### 스크린리더 사용자의 웹 브라우저와 스크린리더 조합

스크린리더와 브라우저도 궁합이 있다. 스크린리더의 기술이 W3C의 기술명세서만큼 빠르게 발전하지 못하기 때문에 가장 호환이 좋은 스크린리더와 브라우저 조합으로 스크린리더를 사용하게 된다.

아래 표를 보면  JAWS는 Chrome과 Internet Explorer를, NVDA에서는 Firefox와 Chrome 사용하고 있다.

### 2019년 9월 기준

| Screen Reader & Browser | 점유율 |
| :--- | :--- |
| JAWS with Chrome | 21.4% |
| NVDA with Firefox | 19.6% |
| NVDA with Chrome | 18.0% |
| JAWS with Internet Explorer | 11.5% |
| VoiceOver with Safari | 9.1% |

{% hint style="info" %}
주요 위젯은 모든 조합별로 테스트하는 것을 추천한다.   
즉,  JAWS는 Chrome과 Internet Explorer를, NVDA에서는 Firefox와 Chrome 을 테스트해야 한다.
{% endhint %}

