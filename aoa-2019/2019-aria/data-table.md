# 이해하기 쉬운 데이터 테이블 적용 사례

### 제목행과 제목열에 모두 th와 scope를 사용하자.

아래와 같이 방콕에서 인천으로 오는 항공편에 초과수하물을 4명의 가족이 1개씩 추가하여 구매 정보를 보여주는 테이블이 있다. 이런 테이블을 스크린리더를 사용하는 시각 장애인들에게도 쉽게 이해할 수 있는 테이블로 만들 수 있다.

![](../../.gitbook/assets/2019-08-29-7.23.48.png)

첫번 째 제목 행은 \<th>로 마크업하고 scope="col" 속성을 사용하고, 테이블의 캡션은 "탑승자 별 방콕출발 인천도착 여정에 구매한 초과수하물 개수 현황"이라고 제공한다.

그리고 테이블을 보면 어두운 배경의 제목행이 아닌 탑승자 열도 제목열이 될 수 있다. 위의 경우 탑승자와 여정정보까지 제목열로 지정하면 초과 수하물 개수 정보 탐색할 때 빠르게 이해가 가능해진다.

마크업 소스는 다음과 같다.&#x20;

```markup
<table>
    <caption>탑승자 별 방콕출발 인천도착 여정에 구매한 초과수하물 개수 현황</caption>
    <thead>
        <tr>
            <th scope="col">탑승자</th>
            <th scope="col">여정정보</th>
            <th scope="col">첫번째 초과수하물</th>
            <th scope="col">두번째 초과수하물</th>
            <th scope="col">세번째 초과수하물</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scope="row">father</th>
            <th scope="row">방콕 출발 서울/인천 도착</th>
            <td>무료</td>
            <td>1개</td>
            <td>미구매</td>
        </tr>
        <tr>
            <th scope="row">mother</th>
            <th scope="row">방콕 출발 서울/인천 도착</th>
            <td>무료</td>
            <td>1개</td>
            <td>미구매</td>
            ....
    </tbody>
</table>
```

테이블을 탐색 시 JAWS에서는 ctrl + alt + 방향키를 사용하게 되는데 데이터 열을 읽을 때 연관된 제목행과 제목열을 읽고  ctrl + alt + 5(numpad)를 누르면 현재의 데이터 열의 제목열과 제목행을 같이 읽게 된다.

![](<../../.gitbook/assets/image (52).png>)

위 화면 mother의 두번째 초과수하물을 JAWS로 탐색하여 읽으면 다음과 같이 들린다.

> 4열 3행 \
> 두번째 초과수하물 mother 방콕 출발 서울/인천 도착 1개

### 총액은 테이블과 분리하자.

위 마크업 소스를 보게되면 총액 부분은 \<tfoot>으로 제작하지 않는 것이 좋다.

이유는 총액은 스크린리더가  읽지 말아야 할 제목열과 제목행을 총액과 같이 연관있게 읽을 수 있기 때문이다. 차라리 이렇게 테이블 제목과 연관이 없는 경우는 테이블과  분리하여 별도로 마크업하는 것이 스크린리더 사용자가 이해하기 쉬운 테이블이 된다.&#x20;

{% hint style="info" %}
\<table>태그의 \<thead>, \<tbody>,\<tfoot>은 테이블 소스의 구조화를 위한 태그일 뿐, 스크린리더가 테이블을 읽는데 전혀 영향을 주지 않는다.
{% endhint %}

#### <mark style="color:orange;">AOA동영상 강의</mark>

{% embed url="https://youtu.be/YWAF8fRYInA" %}
1
{% endembed %}

{% embed url="https://youtu.be/S1dAgQkt5CQ" %}
2
{% endembed %}
