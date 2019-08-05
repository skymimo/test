# 자동완성 적용 사례

### combobox = input + listbox

![](../../.gitbook/assets/image%20%2820%29.png)

출도착 도시 및 공항을 선택할 때 자동완성 기능을 사용할 수 있으며 키보드로 사용이 가능하다. 자동완성 컨테이너는`role="combobox"`를 가지게 되고, 검색결과가 표출되는 영역은 `role="listbox"`를 가진다. 

combobox는 input과 listbox의 조합으로 각 위젯의 키보드 인터랙션 방법으로 사용할 수 있어야 한다. 또한 자동완성 기능이 포함되어 있으므로 검색결과를 스크린리더에서도 읽을 수 있어야 한다.

### role="combobox"

상단 input에는 `role="combobox"`를 삽입하고 aria-autocomplete는 list를 삽입한다.  
하단 listbox가 펼쳐질 때는 `aria-expanded="true"`, 닫혀졌을 때는 false가 삽입된다.  검색된 결과를 읽어줄 수 있게 비어있는 &lt;div&gt;요소에 `role="status"`와 `aria-live="polite"`를 삽입한다.

![](../../.gitbook/assets/image%20%2825%29.png)

```markup
<input type="text" role="combobox" aria-autocomplete="list" aria-expanded="false" 
 aria-owns="결과 리스트박스 id" aria-activedescentant="선택된 리스트박스의 옵션 id">
 //검색결과 읽는 영역
 <div role="status" aria-live="polite"></div>
```

#### aria-owns \(나와 내 아이들과의 연결고리\)

aria-owns 속성은 시각적으로는 어떤 하위 메뉴가 상위 메뉴 근처에 배치되어 있지만, DOM 상위 항목의 바로 하위 항목일 수는 없는 경우에는 `aria-owns`를 사용하여 하위 메뉴를 상위 메뉴의 하위 메뉴로 스크린 리더에 알려줄 때 사용할 수 있다.

#### aria-activedescendant \(현재 선택된 내 아이\)

input 에 현재 하위 항목 중 선택된 값을 스크린리더에게 알려줄 때 aria-activedescendant 를 사용할 수 있다. 현재 선택한 목록 항목에 맞춰 계속 업데이트된 상태로 나타낼 수 있으며 스크린리더는 현재 선택한 항목이 마치 포커스된 항목인 것처럼 나타나게 할 수 있습니다.

### role="listbox"

![](../../.gitbook/assets/image%20%2834%29.png)

하위 영역 컨테이너는 `role="listbox"`와 상위 input의 aria-owns와 연결되는 id 값을 가지고, 각각의 하위 리스트는 `role="option"` 과 선택되었을 때는 `aria-selected="true"`와 상위 input에 삽입된 aria-activedescendant 속성과와 연결되는 id값을 가지게 되고, 선택되지 않았을 때는 `aria-selected="false"`를 가진다.

```markup
<ul role="listbox" id="xxx">
    <li role="option" aria-selected="true">A Coruna(LCG)</li>
    <li role="option" aria-selected="false">Dallas/Love Field(DAL), TX</li>
    <li role="option" aria-selected="false">Gran Canaria(LPA)</li>
    <li role="option" aria-selected="false">La Crosse(LSE),WI</li>
    <li role="option" aria-selected="false">Lafayette(LFT),LA</li>
</ul>
```

### 복잡한 키보드 인터랙션

`role="combobox"`는 스크린리더 사용자가 일반적으로 기대하고 있는 키보드 인터랙션이 있으며 아래와 같다. 

* **Alt + 아래 방향키** : 비어있는 input에서 리스트가 닫혀있을 때 열린다.
* **Enter or Space bar** : 리스트에서 Enter와 Space bar를 누르면 항목은 선택되고 리스트는 닫힌다.
* **상하 방향키** : 리스트 내에서 위아래로 탐색한다.
* **ESC** : 리스트박스가 닫히고 input 내의 텍스트는 삭제된다.
* 비어있는 input에 알파벳을 한 개씩 누르면 매칭되는 결과값만 리스트에 남는다. \(Native 셀렉트박스와 동일한 기능\)

스크린리더로 LAX \(로스앤젤레스\)을 한 글자씩 입력하다가 리스트를 탐색해보면 아래와 같이 들린다.

> 출발지 combobox 닫혀짐  
> 편집창 자동완성  
> _**L**_  
> 24개의 검색 결과가 있습니다.  
> 펼쳐짐  
> _**A**_   
> 6개의 검색 결과가 있습니다.  
> La Crosse\(LSE\), WI  
> Lafayette\(LFT\), LA  
> Lansing\(LAN\), MI  
> Las Vegas\(LAS\), NV, McCarran  
> Los Angeles\(LAX\), CA

