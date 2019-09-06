# 스핀 버튼 적용 사례

### 빠르고 편리하게 개수를 조정하는 스핀 버튼!

소량의 상품의 수량을 조정하기에 가장 쉽고 편리한 스핀 버튼은 쇼핑몰에서 흔하게 사용한다. 

항공사에서도 승객 수를 선택할 때 스핀 버튼을 사용하는데 제대로 구현하지 않으면 스크린리더 사용자는 현재 상태를 알 수 없어 사용하기가 아주 어렵게 된다. 

![](../../.gitbook/assets/image%20%2860%29.png)

#### 접근성을 준수한 스핀버튼을 제작해보자.

기본 마크업은 다음과 같다.

제작된 소스는 시맨틱하지 않은 &lt;dl&gt;, &lt;dt&gt;, &lt;dd&gt;로 되어 있어 `role="presentation"` 속성을 삽입하여 의미를 삭제했다. 물론 태그를 시맨틱하게 변경하여 수정할 수도 있었지만.......... 일정이..... 또르르...\(변명 중\)

```markup
 <dl role="presentation">
   <dt><span>성인</span></dt>
   <dd>
     <button>성인 탑승자 한 명 줄이기</button>       
     <label for="KE" class="offscreen">성인</label>
     <input type="text" id="KE" value="0" maxlength="1">        
     <div class="offscreen" aria-live="assertive" 
      aria-relevant="additions" aria-atomic="true"></div>        
     <button>성인 탑승자 한 명 늘리기</button>    
   </dd>
 </dl>          
```

+와 -의 버튼명은 각 레이블에 맞게 변경하여 성인인 경우 "성인 탑승자 한 명 줄이기", " 성인 탑승자 한 명 늘리기"로 적용하였다. 각 버튼을 클릭하면 `aria-live="assertive", aria-relevant="additions", aria-atomic="true"` 속성을 갖고 있는 비어있는 &lt;div&gt; 안에 현재의 탑승객 수를 읽는 노드가 들어오게 구현하였다.

![](../../.gitbook/assets/image%20%2822%29.png)

탭키로 이동하여 승객을 3명으로 늘리기까지 스크린리더\(NVDA\)는 아래와 같이 읽게 된다.

> 성인 탑승자 한명 줄이기\( - 버튼\)  
> 성인 편집창 1 \(입력박스\)  
> 성인 탑승자 한명 늘리기 \( + 버튼\)  
> 성인 탑승자 2명으로 변경됨  
> 성인 탑승자 3명으로 변경됨

항공사는 최대 9명까지만 신청이 가능하기 때문에 9명에 도달하면 + 버튼은 비활성 버튼으로 변경되고 해당 버튼에 `aria-disabled="true"`속성이 삽입되고 비활성화된 디자인으로 변경된다.

`aria-disabled="true"`속성을 사용하게 되면 사용할 수 없는 버튼으로 스크린리더가 읽게 되므로 버튼명을 사용할 수 없다는 버튼명으로 변경하거나 숨김 텍스트로 사용할 수 없음을 알려주지 않도록 주의해야 한다.

{% hint style="info" %}
위 버튼을 토글 버튼으로 제작하지 않도록 주의해야 한다. 토글 버튼은 눌려진 상태와 눌려지지 않은 상태로 2가지 상태가 있을 때만 사용해야 하고, aria-disabled 속성을 사용하지 않는 것이 일반적이다. 
{% endhint %}

