# 메뉴 적용 사례

### menu, menubar로 구현한 마이페이지 메뉴

메뉴를 구현하는 방법은 여러 가지가 있는데, 아래 화면과 같은 마이페이지의 메뉴는 role="menu"와 role="menubar"로 구현하였다.

![](../../.gitbook/assets/image%20%284%29.png)

기본 마크업은 다음과 같다.

```text
<nav role="navigation" aria-label="메인">
    <ul class="depth-1" role="menubar">
        <li role="menuitem">
            <button aria-expanded="false" aria-controls="menu1">
            <div id="menu1" aria-hidden="true" style="display:none">
                <h2><a href="#">항공권 예매</a></h2>
                <ul class="depth-2">
                    <li><a href="#">일반 예매</a></li>
                    ...
                </ul>
            </div>
        </li>
        <li>
            <button aria-expanded="true" aria-controls="menu2">
            <div id="menu2" style="display:block">
                <h2><a href="#">회원 혜</a></h2>
                <ul class="depth-2">
                    <li><a href="#">스카이패스 회원 혜</a></li>
                    <li><a href="#">스카이팀 공동 혜택</a></li>
                    ...
                </ul>
            </div>
        </li>
        ...
    </ul>
</nav>
```

