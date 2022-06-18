# 에러메세지는 왜 보이기만 하지?

### 에러메시지가 잘... 보이기만 하네?

에러가 발생하여 에러메세지가 입력박스 하단에 선명하고 빨간색 폰트로 에러메시지를 보여주고 있지만, 스크린리더 사용자는 에러가 발생했는지 조차도 알 수가 없다.

![](../.gitbook/assets/529.png)

### 문제발생

사용자의 생년월일을 입력하는 입력박스에 "1111"이라는 잘못된 연도와 "33"이라는 잘못된 날짜를 입력하면 잘못된 연도와 날짜라는 에러메시지를 바로 보여주고 포커스도 에러 발생한 곳으로 이동한다.\
하지만, 에러가 시각적으로만 보일 뿐 스크린리더 사용자는 에러가 발생했는지 어떤 에러인지 바로 인지하지 못한다.

```markup
<div id="birthlabel">Date of Birth</div> 
<div role="group" aria-labelledby="birthlabel">
  <div>
    <span id="placeholder-year" aria-hidden="true">YYYY</span>                                                
    <input type="text" title="4 digit year" aria-required="true">
    <p class="error">Invalid Year</p>
  </div>                                            
  <div>                                               
   <span id="placeholder-month" aria-hidden="true">MM</span>
   <input type="text" title="2 digit month" aria-required="true">                                   
  </div>                                            
  <div>
    <span id="placeholder-day" aria-hidden="true">DD</span>
    <input type="text" title="2 digit day" aria-required="true">
    <p class="error">Invalid Date</p>                                            
  </div>                                        
</div>    
```

스크린리더는 아래와 같이 읽는다.

> Date of Birth 그룹\
> 4 digit year edit required 편집창\
> selected 1111

### 해결방안

```markup
<span id="placeholder-year" aria-hidden="true">YYYY</span>                                                
<input type="text" title="4 digit year" aria-invalid="true" aria-describedby="error-1" aria-required="true" >
<p class="error" id="error-1">Invalid Year</p>                                     
```

에러가 발생한 입력박스에 `aria-invaild="true"`를 삽입하여 에러가 발생한 폼이라는 것을 알리고, 에러문구가 포함된 컨테이너에 id 값을 삽입하고 aria-describedby와 연결하여 포커스가 입력박스에 도달하면 에러문구를 읽도록 설정한다.

> Date of Birth 그룹\
> 4 digit year edit required invalid entry 편집창 \
> Invalid year \
> selected 1111

{% hint style="info" %}
4자리 연도를 YYYY로 표현하는 경우가 많은데, JAWS에서는 연속된 글자를 개수에 맞게 모두 읽지 않기 때문에 4 digit year로 표현하는 것이 좋다.
{% endhint %}

#### <mark style="color:orange;">AOA동영상 강의</mark>

{% embed url="https://youtu.be/7LdLOTZei5M" %}
