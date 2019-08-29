# Live region 대신 모달 다이얼로그

### 화면에 보여진다면 Live region을 꼭 사용하지 않아도 돼요.

항공사의 경우, 항공편 좌석 확보 문제로 일정한 시간이 지나면 자동으로 세션이 끊어지고 초기화면으로 돌아간다. 항공편 선택 시 4분 마다 세션이 끊기고, 결제 화면에서는 7분 마다 세션이 끊기게 된다.

4분이라는 시간 동안 스크린리더 사용자가 항공편 정보를 탐색하기란 쉽지 않기 때문에 뒷단에서 자동 연장을 하며, 몇 회의 자동 연장 이후에 아래와 같은 세션 종료 안내 팝업이 뜨게 된다.

![](https://lh5.googleusercontent.com/xG4jJYIeYAVyyEqOpW-_UEMQxljQq6NVNpkhHFU7-isyh_FXZiJI5wo9ibwXeUPnpS7zEadw7-jXC2vnuZYwFAUERTKBxu7F0TaODTvDigPSC-GseXQKeuaWaI0sHBcKarIUXkU)

### 모달 다이얼로그와 aria-describedby 속성

처음엔 Live region을 사용하였다가 모달 다이얼로그를 사용하게 되면 스크린리더가 바로 인지하고 읽게 되므로 아래와 같은 방법으로 구현하였다.

```markup
<div role="dialog" aria-labelledby="title" aria-describedby="text">
  <h1 id="title">Session will be Timed Out </h1>
  <p id="text">Automatic Initialization:Remaining time [29] Second(s)</p>
  <p>This session will expire for security reasons and personal 
    data protection. When the remaining time is up, the site will be 
    automatically initialized and redirected to the main page of the 
    website.</p>
  <button>Proceed without session extension</button>
  <button>Extend the session time</button>
</div>
```

위와 같이 role="dialog"를 갖고 있는 div 태그에 aria-labelledby와 제목을 연결하고 남은 시간을 알려주는 문구와 aria-describedby 속성은 연결해주면, 스크린리더는 아래와 같이 다이얼로그가 뜰 때 제목과 중요 정보를 함께 읽어 준다.

> Session will be timed out dialog  
> Automatic initialization : Remaining time 29 seconds

이렇게 사용하게 되면 Live Region 속성을 사용하지 않고도 스크린리더 사용자에게 중요한 정보를 전달할 수 있게 된다.
