# SPA 페이지의 네비게이션은?

### 한 페이지로 구성되어 있는 페이지

아래 페이지를 보면 6개의 메뉴에 해당하는 페이지를 한 페이지로 제작해 놓았다. 왼쪽의 7개 메뉴를 각각 클릭하면 부드럽게 스크롤이 되면서 해당 페이지로 이동한다.

[https://www.koreanair.com/content/koreanair/korea/ko/traveling/baggage-services.html\#loss-delayed-damaged](https://www.koreanair.com/content/koreanair/korea/ko/traveling/baggage-services.html#loss-delayed-damaged)

![](../../.gitbook/assets/image%20%2816%29.png)

 7개의 각 메뉴로 이동하면 섹션 페이지 안에  동일한 헤딩 태그가 삽입되어 있고 왼쪽의 6개의 메뉴 기본 마크업은 아래와 같다.

```markup
<div role="navigation" aria-label="수하물 메뉴">
    <ul>
        <li><a href="#">운송가능 수하물</a></li>
        <li><a href="#">운송 제한 품목</a></li>
        <li><a href="#">수하물 연결 수속</a></li>
        <li><a href="#">분실/지연/파손</a></li>
        <li><a href="#">기내유실물 찾기</a></li>
        <li><a href="#">수하물 준비방법 및 유의사항</a></li>
    </ul>
</div>
```

원하는 메뉴를 클릭하면 해당 페이지로 스크롤되고 해당하는 섹션 페이지 내의 헤딩 태그에 tabindex="-1" 속성을 삽입하고 포커스를 이동시키고,  헤딩 태그로부터 키보드 포커스가 나가게 되면 tabindex 속성은 삭제한다.

스크린리더로 읽어보면 다음과 같.

> 운송가능 수하물 링크  
> 운송 제한 품목 링크  
> 수하물 연결 수속 링크  
> 분실/지연/파손 링크  // 엔터키를 누르  
>   
> 분실/지연/파손 헤딩 레벨 2

이 방법과 같이 SPA에 메뉴를 클릭하고 포커스를 해당 페이지로 이동시키면, 스크린리더 사용자는 쉽고 빠르게 원하는 콘텐츠 탐색이 가능하게 된다. 

