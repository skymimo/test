# 접근성 주요 개선 항목

### Tabs, Combobox, Dialog, Date picker, Autocomplete, Radio, Checkbox, Button 등 주요 위젯을 스크린리더가 이해할 수 없고 운용할 수 없다. <a id="tabs-combobox-dialog-date-picker-autocomplete-radio-checkbox-button"></a>

각 UI의 역할과 상태를 모양이나 위치, 색상을 통해 시각적으로 사용자에게 전달되고 있지만, 스크린리더 사용자는 이해할 수도 운용할 수도 없다.

### 이해와 운용의 불가능 <a id="undefined"></a>

* **Dialog**가 시각적으로 제목과 함께 표출되었지만 스크린리더는 아무 것도 읽지 않아 스크린리더 사용자는 이해할 수 없으며, 스크린리더는 화살표키를 눌러 Tab을 전환하라고 하지만 동작하지 않아 운용할 수 없다.
* **Date picker** 테이블 헤더에 요일이 한글자로 표시되어 있지만 잘 읽어주지 않아 이해하기 어렵고, 날짜를 선택하여도 선택했다는 정보를 읽어 주지 않아 의미를 알 수 없어 운용할 수 없다.
* **Tabs**에서 현재 선택된 탭 정보를 알 수 없어 이해하기 어렵고, 키보드 방향키로 탭 전환을 할 수 없어 운용할 수 없다.
* **Combobox**는 상태정보와 레이블이 없어 보조기기 사용자는 제어 유형이나 조작 방법 또는 선택할 옵션에 대해 알 수 없고 운용할 수 없다.
* 링크로 구현되었으나 **버튼**과 같이 동작하여 스크린리더 사용자가 이해하기 어렵다.
* **Radio**로 구현되어 있으나 그룹 정보가 없어 이해하기 어렵고 선택이 되었는지 알 수 없이 운용할 수 없다.
* **Autocomplete**로 구현되었으나 스크린리더 사용자는 현재 선택된 값을 알 수 없고, 검색결과도 알 수 없어 운용할 수 없다.

Combobox와 autocomplete를 구현하기 위해 chosen.js를 사용했으나 접근성을 준수할 수 없어 결국 제거해야 했다.

### 주요 UI 키보드 인터랙션 <a id="ui"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">UI</th>
      <th style="text-align:left"><b>키보드 인터랙션</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Combobox</td>
      <td style="text-align:left">
        <p>아래 방향키를 눌러 전체 리스트를 펼친다.</p>
        <p>상하 방향키를 눌러 선택값을 변경하고 엔터키를 눌러 선택한다.</p>
        <p>ESC를 누르면 리스트는 닫혀진다.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Tabs</td>
      <td style="text-align:left">
        <p>수평탭은 좌우 방향키로 탭을 전환시키고, 수직탭은 상하 방향키로 탭을 전환한다.</p>
        <p>탭 순서가 마지막이어도 다시 처음으로 돌아가 순환해야 한다.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Checkbox</td>
      <td style="text-align:left">스페이스바로 선택을 하거나 선택을 해제한다.</td>
    </tr>
    <tr>
      <td style="text-align:left">Radio</td>
      <td style="text-align:left">
        <p>위/왼쪽 방향키는 이전 라디오 버튼으로 이동하고, 아래/오른쪽 방향키는 다음 라디오 버튼으로 이동한다.</p>
        <p>라디오버튼의 순서가 마지막이어도 다시 처음으로 돌아가 순환해야 한다.</p>
      </td>
    </tr>
  </tbody>
</table>​[https://www.w3.org/TR/wai-aria-practices-1.1/](https://www.w3.org/TR/wai-aria-practices-1.1/)​

### 스크린리더에서 들리는 키보드 인터랙션 \(JAWS\) <a id="jaws"></a>

* Combobox : 방향키를 사용하거나 텍스트를 입력하여 값을 설정하세요.
* Selectbox : 방향키로 선택을 변경하세요.
* Radio button : 위아래 방향키로 선택값을 변경하세요.

