# 자동완성 적용 사례

### combobox = input + listbox

![](../../.gitbook/assets/image%20%2816%29.png)

출도착 도시 및 공항을 선택할 때 자동완성 기능을 사용할 수 있으며 키보드로 사용이 가능하다. 자동완성 컨테이너는`role="combobox"`를 가지게 되고, 검색결과가 표출되는 영역은 `role="listbox"`를 가진다. 

combobox는 input과 listbox의 조합으로 각 위젯의 키보드 인터랙션 방법으로 사용할 수 있어야 한다. 또한 자동완성 기능이 포함되어 있으므로 검색결과를 스크린리더에서도 읽을 수 있어야 한다.

### role="combobox"

상단 input에는 `role="combobox"`를 삽입하고 aria-autocomplete는 list를 삽입한다.  
하단 listbox가 펼쳐질 때는 `aria-expanded="true"`, 닫혀졌을 때는 false가 삽입된다.  검색된 결과를 읽어줄 수 있게 비어있는 &lt;div&gt;요소에 `role="status"`와 `aria-live="polite"`를 삽입한다.

![](../../.gitbook/assets/image%20%2821%29.png)

```markup
<input type="text" role="combobox" aria-autocomplete="list" aria-expanded="false" 
 aria-owns="결과 리스트박스 id" aria-activedescentant="선택된 리스트박스의 옵션 id">
```

#### aria-owns \(나와 내 아이들과의 연결고리\)

aria-owns 속성은 시각적으로는 어떤 하위 메뉴가 상위 메뉴 근처에 배치되어 있지만, DOM 상위 항목의 바로 하위 항목일 수는 없는 경우에는 `aria-owns`를 사용하여 하위 메뉴를 상위 메뉴의 하위 메뉴로 스크린 리더에 알려줄 때 사용할 수 있다.

#### aria-activedescendant \(현재 선택된 내 아이\)

input 에 선택되어 삽입된 현재 선택된 값을 스크린리더에게 알려줄 때 `aria-activedescendant` 를 사용할 수 있다. 현재 선택한 목록 항목에 맞춰 계속 업데이트된 상태로 나타낼 수 있으며 스크린리더는 현재 선택한 항목이 마치 포커스된 항목인 것처럼 나타나게 할 수 있습니다.

