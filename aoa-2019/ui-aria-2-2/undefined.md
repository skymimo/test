# 날짜 입력 적용 사례

### 접근성이 좋지 않은 Jquery UI datepicker

Jquery 공식 홈페이지에 있는 날짜선택기 화면이다. 입력박스에 포커스가 이동하면 자동으로 캘린더가 열리지만 캘린더가 열렸다는 것을 알 수도 없고 키보드로 접근을 할 수 없어 날짜 선택이 어렵다. 

![](../../.gitbook/assets/2019-08-24-8.58.19.png)

![](../../.gitbook/assets/2019-08-24-8.56.02.png)

```markup
<label for="date" class="offscreen">
    Start Date (e.g. 2016-12-01)
</label>  
<span aria-hidden="true">Start Date (YYYY-MM-DD)</span>    
<input id="date" type="text" maxlength="10">
<button>Select the date</button>
```



