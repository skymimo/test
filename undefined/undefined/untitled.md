# 이해하기 어려운 폼 레이블

### 구분 없이 반복되는 문구

입력 박스의 레이블과 입력 지침\(Placeholder\), 에러 메시지까지 동일한 문구가 불필요하게 반복이 되면 스크린리더 사용자는 어떤 정보인지 구분을 할 수가 없어 사용이 어렵게 된다.

### 문제발생

First Name을 입력하는 입력박스에 숨김텍스트로 Required가 삽입되어있고, 레이블과 Placeholder에는 First Name 문구가 반복 제공되어 있다.   
아무것도 입력하지 않고 submit을 누르면 에러가 발생하지만 First Name Required 문구가 또 다시 반복이 된다.

![](../../.gitbook/assets/image%20%289%29.png)

```markup
<label for="aa">First Name <span class="offscreen">Required</span></label>
<span class="placeholder" id="bb">First Name</span>
<input type="text" id="aa" aria-describedby="bb error-txt">
<p class="error" id="error-txt">First Name Required</p>
```

에러가 발생하고 포커스가 입력박스로 이동하면 스크린리더는 아래와 같이 읽게 된다.

> First Name Required   
> edit has auto complete   
> First Name   
> First Name Required

### 해결방안

레이블의 숨김텍스트 Required 문구는 그대로 두고, 레이블은 First Name,  Placeholder는 입력포맷으로 바꾸었다. 그리고 에러메시지는 많이 달라지지 않았지만  필수입력정보라는 내용으로 변경하였다.

```markup
<label for="aa">First Name <span class="offscreen">Required</span></label>
<span class="placeholder" id="bb">ex)GIL DONG</span>
<input type="text" id="aa" aria-describedby="bb error-txt">
<p class="error" id="error-txt">This information is required.</p>
```

스크린리더로 읽게 되면 다음과 같이 들리게 되고 훨씬 이해하기 쉽게 개선이 되었다.

> First Name Required   
> edit has auto complete   
> ex\)GIL DONG   
> This information is required.



