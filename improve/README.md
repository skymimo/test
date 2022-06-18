# 접근성 주요 개선 항목

### 주요 위젯을 스크린리더 사용자들은 사용할 수 없다. <a href="#tabs-combobox-dialog-date-picker-autocomplete-radio-checkbox-button" id="tabs-combobox-dialog-date-picker-autocomplete-radio-checkbox-button"></a>

Tabs, Combobox, Dialog, Date picker, Autocomplete, Radio, Checkbox, Button 등 주요 위젯을 각 UI의 역할과 상태를 모양이나 위치, 색상을 통해 시각적으로 사용자에게 전달되고 있지만, 스크린리더 사용자는 이해할 수도 운용할 수도 없다.

### 이해와 운용의 불가능 <a href="#undefined" id="undefined"></a>

* **Dialog**가 시각적으로 제목과 함께 표출 되었지만 스크린리더는 아무 것도 읽지 않아 스크린리더 사용자는 이해할 수 없다.
* **Date picker** 테이블 헤더에 요일이 한 글자로 표시되어 있지만 잘 읽어주지 않아 정보 이해하기 어렵고, 날짜를 선택하여도 선택했다는 상태 정보를 읽어 주지 않아 운용할 수 없다.
* **Tabs**에서 현재 선택된 탭 정보를 알 수 없어 이해하기 어렵고, 키보드 방향키로 탭 전환을 할 수 없어 운용할 수 없다.
* **Combobox**는 상태정보와 레이블이 없어 스크린리더 사용자는 현재 선택된 값을 알 수 없고, 검색결과도 알 수 없어 이해하기도 운용할 수 없다.
* 링크로 제작 되었으나 **버튼**과 같이 동작하여 스크린리더 사용자가 이해하기 어렵다.
* **Radio**로 제작 되어 있으나 그룹 정보가 없어 이해하기 어렵고 선택이 되었는지 알 수 없어 운용할 수 없다.

Combobox와 autocomplete를 구현하기 위해 chosen.js를 사용했으나 접근성을 준수할 수 없어 결국 제거해야 했다.

### 스크린리더에서 들리는 키보드 인터랙션 (JAWS) <a href="#jaws" id="jaws"></a>

* Combobox : 방향키를 사용하거나 텍스트를 입력하여 값을 설정하세요.
* Selectbox : 방향키로 선택을 변경하세요.
* Radio button : 위아래 방향키로 선택값을 변경하세요.

### 주요 UI 키보드 인터랙션 <a href="#ui" id="ui"></a>

| UI       | **키보드 인터랙션**                                                                                                  |
| -------- | ------------------------------------------------------------------------------------------------------------- |
| Combobox | <p>아래 방향키를 눌러 전체 리스트를 펼친다.</p><p>상하 방향키를 눌러 선택값을 변경하고 엔터키를 눌러 선택한다.</p><p>ESC를 누르면 리스트는 닫혀진다.</p>             |
| Tabs     | <p>수평탭은 좌우 방향키로 탭을 전환시키고, 수직탭은 상하 방향키로 탭을 전환한다.</p><p>탭 순서가 마지막이어도 다시 처음으로 돌아가 순환해야 한다.</p>                   |
| Checkbox | 스페이스바로 선택을 하거나 선택을 해제한다.                                                                                      |
| Radio    | <p>위/왼쪽 방향키는 이전 라디오 버튼으로 이동하고, 아래/오른쪽 방향키는 다음 라디오 버튼으로 이동한다.</p><p>라디오버튼의 순서가 마지막이어도 다시 처음으로 돌아가 순환해야 한다.</p> |

​[https://www.w3.org/TR/wai-aria-practices-1.1/](https://www.w3.org/TR/wai-aria-practices-1.1/)​

#### <mark style="color:orange;">AOA동영상 강의</mark>

{% embed url="https://youtu.be/nHmUnTpivlo" %}
