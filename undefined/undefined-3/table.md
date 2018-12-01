# 정렬할 수 있는 table 적용 사례

### 오름차순/내림차순 정렬이 가능한 테이블

예약조회 페이지에는 예약번호, 출발날짜, 출도착 도시 등으로 정렬을 할 수 있는 테이블이 있다.  
상하 화살표 아이콘으로 정렬 상태를 표시하고 있으며, 스크린리더 사용자들을 위해 사용할 수 있는 ARIA 속성은 aria-sort 속성이 있다. 

![](../../.gitbook/assets/image%20%281%29.png)

aria-sort 속성 값으로는 오름차순 ascending과 내림차순 descending, 그리고 정렬되지 않은 상태 none을 사용할 수 있다. Reservation Number 내림차순으로 정렬되어 있으므로 가장 큰 수에서 작은 수 순으로 정렬되었다.  
또한, 정렬되지 않은 제목셀은 aria-sort 속성 값은 none을 갖고 정렬할 수 있음을 title 속성을 사용하여 알릴 수 있다.

```markup
<th scope="col" aria-sort="descending">
    <a href="#" role="button">Reservation Number</a>
</th>
<th scope="col" aria-sort="none">
    <a href="#" role="button" title="Sort in ascending order">Reservation Nickname</a>
</th>
```

스크린리더로 들어보면 아래와 같이 읽는다.

> column 1 clickable   
> 내림차순으로 정렬됨   
> Reservation Number   
> button  
>   
> column 2 clickable  
> Reservation nickname  
> button   
> 오름차순으로 정렬 가능

{% hint style="info" %}
요소 안에 버튼 기능을 로 사용한 이유는 JAWS 15, 16 버전의 버그로 IE에서  요소 안에서  기능이 제대로 동작이 되지 않기 때문이다. \(현재 17 버전은 잘 된다.\)
{% endhint %}

