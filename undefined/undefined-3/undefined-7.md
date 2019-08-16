# 메뉴 적용 사례

### menu, menubar로 구현한 마이페이지 메뉴

메뉴를 구현하는 방법은 여러 가지가 있는데, 아래 화면과 같은 마이페이지의 메뉴는 role="menu"와 role="menubar"로 구현하였다.

![](../../.gitbook/assets/image%20%285%29.png)

#### 상위 메뉴는 role="menubar", 하위 메뉴는 role="menu"

전체 메뉴 컨테이너에 role="navigation"과 aria-label를 사용하여 메뉴 네비게이션임을 안내한다. 상위 메뉴에 role="menubar"와 role="menuitem"을 삽입하고 그 하위 메뉴에는 role="menu"와 role="menuitem"을 사용한다.  

상위 메뉴가 하위 메뉴를 가지고 있는 경우 aria-haspopup="true" 속성을 삽입하여 하위 메뉴가 있음을 알려야 하고 펼쳐졌을 때는 aria-expanded는 true 를 삽입하고 aria-controls 속성으로 하위 메뉴랑 연결한다. 하위 메뉴가 없는 상위 메뉴는 aria-haspopup 속성이 없어야 하고, 펼쳐질 하위 메뉴가 없으므로 aria-expanded 와 aria-controls 속성 또한 삭제해야 한다.

마크업을 완성하면 아래와 같다.

```markup
<nav role="navigation" aria-label="마이페이지">
    <ul class="depth-1" role="menubar">
        <li role="menuitem" tabindex="-1">
            마이페이지
        </li>
        <li role="menuitem" aria-haspopup="true" aria-expanded="false" 
        aria-controls="menu1" tabindex="-1">
            나의 마일리지
            <ul role="menu" id="menu1" style="display:none">
                <li role="menuitem" tabindex="-1">
                    마일리지 현황
                </li>
                <li role="menuitem" tabindex="-1">
                    마일리지 상세 조회
                </li>
                <li role="menuitem" tabindex="-1">
                    마일리지 사후적립 신청
                </li>
            </ul>
        </li>
        <li role="menuitem" aria-haspopup="true" aria-expanded="true" 
        aria-controls="menu2" tabindex="0">
            마일리지 사용
            <ul role="menu" id="menu2">
                <li role="menuitem" tabindex="0">
                    항공 보너스
                </li>
                <li role="menuitem" tabindex="-1">
                    로고 상품
                </li>
                ...
            </ul>
        </li>
    </ul>
</nav>
```

### 키보드 인터랙션은 방향키로~

현재 활성화 된 메뉴는 탭키로 이동이 가능해야 하므로 해당 메뉴는 tabindex="0"을 삽입한다. 

상위 메뉴 간의 이동은 좌우 방향키로 이동하고 원하는 메뉴에서 엔터키를 누르면 하위 메뉴가 펼쳐진다. 하위 메뉴 간의 이동은 상하 방향키로 이동할 수 있는데 하위 메뉴에 포커스가 있더라도 좌우 방향키로 상위 메뉴 간 탐색이 가능하다. 또한 하위 메뉴에서 ESC키를 누르면 하위 메뉴는 닫히고 상위 메뉴로 포커스가 이동된다. 

위 마이페이지 예제의 경우 하위 메뉴는 상위 메뉴와 함께 항상 열려 있는 상태로 구현하였기 때문에 ESC나 엔터키로 하위 메뉴를 제어할 필요는 없다. 

{% hint style="info" %}
메인 메뉴와 마이페이지 메뉴를 다르게 구현한 이유는 다음을 자체 기준을 삼았기 때문이다.  
1. 메인 메뉴는 서브 메뉴를 열기 위한 버튼의 역할로 단독으로 존재하지 않음.  
2. 마이페이지 메뉴는 "마이페이지" 메뉴 같이 하위 메뉴 없이 그 자체로 단독으로 메뉴가 존재할 수 있음.
{% endhint %}



