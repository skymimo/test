# 좌석선택 적용사례

비행기의 좌석 선택 기능에는 많은 정보가 제공되고 있으며, 탑승객은 제공되는 정보를 참고하여 원하는 좌석을 선택할 수 있다.

좌석 선택 기능도 모든 브라우저에서 동일하게 호환이 가능한 Native HTML이나 Role 속성이 없으므로 `role="application"`을 삽입하고 키보드 운용 방법을 스크린리더 사용자와 키보드 사용자 모두에게 알릴 수 있도록 제공한다.

### 반드시 알려주어야 하는 좌석의 기본 정보는 무엇일까?

아래 화면과 같이 시각적으로 툴팁을 통해 좌석 정보를 보여주고 있으며, 그 정보를 동등하게 스크린리더 사용자에게도 알려주어야 한다.

1. **줄 수**
2. **창가좌석/복도좌석/중간좌석**
3. **비상구 앞좌석/비상구 뒷좌석**
4. **날개 위 좌석/화장실 근처 좌석/ 갤리 근처 좌석**
5. **선택이 가능한 좌석**
6. **일행이 이미 선택한 좌석**

위의 경우의 수 말고도 상당히 많은 정보가 더 있다. \
아기바구니를 신청할 수 있는 좌석, 장애인이 앉을 수 있는 좌석, 유아 동반 좌석이지만 산소마스크가 부족한 좌석, 창문이 없는 좌석 등등 항공사에서 제공해야 하는 정보는 무수히 많다. ㅠ.ㅠ

![](<../../.gitbook/assets/image (7).png>)

### 복잡하지만 쉽게 운용할 수 있다.

좌석선택 기능은 복잡해 보이지만, 의외로 쉽게 운용할 수 있다.

전체 좌석선택 영역으로의 이동은 쉽게 tab키로 진입하며 tab키를 다시 누르면 좌석선택 밖의 영역으로 이동한다. 좌석 간의 이동은 키보드 방향키로 탐색하고 Enter키를 눌러 선택한다. ESC키를 누르면 좌석 선택 영역 이전의 포커서블한 요소로 포커스가 이동한다.

표 형태이지만 표가 아니므로 table은 `role="presentation"`을 삽입하며, 선택된 \<td>는 버튼 요소로 마크업하고 제공되어야 하는 정보를 가진 문구의 id와 연결하는 aria-describedby를 삽입한다.

```markup
<div role="application" aria-label="seat selector">
    //키보드 운용 방법
    <h2>How to select a date using keyboards</h2>
    <ul>
        <li>In the seat selector, the arrow keys move between seats</li>
        <li>Enter or Space bar selects the seat.</li>
    </ul>
    <table role="presentation">
        ...
        <td class="seating-column">
            <button aria-describedby="seat-info" tabindex="-1" aria-disabled="true">
                <strong>Seat Number 36D</strong>
            </button>
            //화면에 보여지는 좌석 정보
            <div class="tooltip" id="seat-info">
                <span class="occupied">점유된 좌석</span>,
                복도 좌석, 비상구 좌석, 날개 위 좌석, 중간 위치, 오른쪽 위치
             </div>
         </td>
         ...
    </table> 
</div>
```

36D 좌석에 포커스가 이동하면 스크린리더는 아래와 같이 읽게 된다.

> Seat Number 36D 버튼 사용 불가\
> 점유된 좌석, 복도 좌석, 비상구 좌석, 날개 위 좌석, 중간 위치, 오른쪽&#x20;



{% hint style="info" %}
특정 항공사의 기종에서는 비상구 열의 앞 좌석은 뒤로 젖혀지지 않기 때문에 비상구 열 앞 좌석이라는 정보를 제공해야 한다.\
하지만, 대한항공에서 운영하는 기종은 그런 경우가 없기 때문에 해당 정보는 제공하지 않는다.
{% endhint %}

#### <mark style="color:orange;">AOA동영상 강의</mark>

{% embed url="https://youtu.be/WOJ3jp51kf8" %}
