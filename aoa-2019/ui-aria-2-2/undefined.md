# 날짜 입력 적용 사례

### 접근성이 좋지 않은 Jquery UI datepicker

Jquery 공식 홈페이지에 있는 날짜선택기 화면이다. 입력박스에 포커스가 이동하면 자동으로 캘린더가 열리지만 캘린더가 열렸다는 것을 알 수도 없고 키보드로 접근을 할 수 없어 날짜 선택이 어렵다. 

![](../../.gitbook/assets/2019-08-24-8.58.19.png)

### 날짜 입력은 유연하게~

날짜 표기는 다양하다. 국가별 문화차이로 일자를 먼저 입력할 수도 있고 "/"를 입력할 수도 있고 "-"를 입력할 수도 있다. 표준화되어 있지 않은 입력 방법 때문에 시각장애인은 더욱 날짜 선택이 어려워하고 불편해 하게 된다.

![](../../.gitbook/assets/2019-08-24-8.56.02.png)

```markup
<label for="date" class="offscreen">
    Start Date (e.g. 2016-12-01)
</label>  
<span aria-hidden="true">Start Date (YYYY-MM-DD)</span>    
<input id="date" type="text" maxlength="10">
<button>Select the date</button>
```



