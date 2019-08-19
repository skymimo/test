# 접근성 주요 개선 항목

### 주요 위젯을 스크린리더 사용자들은 사용할 수 없다. <a id="tabs-combobox-dialog-date-picker-autocomplete-radio-checkbox-button"></a>

Tabs, Combobox, Dialog, Date picker, Autocomplete, Radio, Checkbox, Button 등 주요 위젯을 각 UI의 역할과 상태를 모양이나 위치, 색상을 통해 시각적으로 사용자에게 전달되고 있지만, 스크린리더 사용자는 이해할 수도 운용할 수도 없다.

### 이해와 운용의 불가능 <a id="undefined"></a>

* **Dialog**가 시각적으로 제목과 함께 표출 되었지만 스크린리더는 아무 것도 읽지 않아 스크린리더 사용자는 이해할 수 없다.
* **Date picker** 테이블 헤더에 요일이 한 글자로 표시되어 있지만 잘 읽어주지 않아 정보 이해하기 어렵고, 날짜를 선택하여도 선택했다는 상태 정보를 읽어 주지 않아 운용할 수 없다.
* **Tabs**에서 현재 선택된 탭 정보를 알 수 없어 이해하기 어렵고, 키보드 방향키로 탭 전환을 할 수 없어 운용할 수 없다.
* **Combobox**는 상태정보와 레이블이 없어 스크린리더 사용자는 현재 선택된 값을 알 수 없고, 검색결과도 알 수 없어 이해하기도 운용할 수 없다.
* 링크로 제작 되었으나 **버튼**과 같이 동작하여 스크린리더 사용자가 이해하기 어렵다.
* **Radio**로 제작 되어 있으나 그룹 정보가 없어 이해하기 어렵고 선택이 되었는지 알 수 없어 운용할 수 없다.

Combobox와 autocomplete를 구현하기 위해 chosen.js를 사용했으나 접근성을 준수할 수 없어 결국 제거해야 했다.

### 스크린리더에서 들리는 키보드 인터랙션 \(JAWS\) <a id="jaws"></a>

* Combobox : 방향키를 사용하거나 텍스트를 입력하여 값을 설정하세요.
* Selectbox : 방향키로 선택을 변경하세요.
* Radio button : 위아래 방향키로 선택값을 변경하세요.

### 주요 UI 키보드 인터랙션 <a id="ui"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">UI</th>
      <th style="text-align:left"><b>&#xD0A4;&#xBCF4;&#xB4DC; &#xC778;&#xD130;&#xB799;&#xC158;</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Combobox</td>
      <td style="text-align:left">
        <p>&#xC544;&#xB798; &#xBC29;&#xD5A5;&#xD0A4;&#xB97C; &#xB20C;&#xB7EC; &#xC804;&#xCCB4;
          &#xB9AC;&#xC2A4;&#xD2B8;&#xB97C; &#xD3BC;&#xCE5C;&#xB2E4;.</p>
        <p>&#xC0C1;&#xD558; &#xBC29;&#xD5A5;&#xD0A4;&#xB97C; &#xB20C;&#xB7EC; &#xC120;&#xD0DD;&#xAC12;&#xC744;
          &#xBCC0;&#xACBD;&#xD558;&#xACE0; &#xC5D4;&#xD130;&#xD0A4;&#xB97C; &#xB20C;&#xB7EC;
          &#xC120;&#xD0DD;&#xD55C;&#xB2E4;.</p>
        <p>ESC&#xB97C; &#xB204;&#xB974;&#xBA74; &#xB9AC;&#xC2A4;&#xD2B8;&#xB294;
          &#xB2EB;&#xD600;&#xC9C4;&#xB2E4;.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Tabs</td>
      <td style="text-align:left">
        <p>&#xC218;&#xD3C9;&#xD0ED;&#xC740; &#xC88C;&#xC6B0; &#xBC29;&#xD5A5;&#xD0A4;&#xB85C;
          &#xD0ED;&#xC744; &#xC804;&#xD658;&#xC2DC;&#xD0A4;&#xACE0;, &#xC218;&#xC9C1;&#xD0ED;&#xC740;
          &#xC0C1;&#xD558; &#xBC29;&#xD5A5;&#xD0A4;&#xB85C; &#xD0ED;&#xC744; &#xC804;&#xD658;&#xD55C;&#xB2E4;.</p>
        <p>&#xD0ED; &#xC21C;&#xC11C;&#xAC00; &#xB9C8;&#xC9C0;&#xB9C9;&#xC774;&#xC5B4;&#xB3C4;
          &#xB2E4;&#xC2DC; &#xCC98;&#xC74C;&#xC73C;&#xB85C; &#xB3CC;&#xC544;&#xAC00;
          &#xC21C;&#xD658;&#xD574;&#xC57C; &#xD55C;&#xB2E4;.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Checkbox</td>
      <td style="text-align:left">&#xC2A4;&#xD398;&#xC774;&#xC2A4;&#xBC14;&#xB85C; &#xC120;&#xD0DD;&#xC744;
        &#xD558;&#xAC70;&#xB098; &#xC120;&#xD0DD;&#xC744; &#xD574;&#xC81C;&#xD55C;&#xB2E4;.</td>
    </tr>
    <tr>
      <td style="text-align:left">Radio</td>
      <td style="text-align:left">
        <p>&#xC704;/&#xC67C;&#xCABD; &#xBC29;&#xD5A5;&#xD0A4;&#xB294; &#xC774;&#xC804;
          &#xB77C;&#xB514;&#xC624; &#xBC84;&#xD2BC;&#xC73C;&#xB85C; &#xC774;&#xB3D9;&#xD558;&#xACE0;,
          &#xC544;&#xB798;/&#xC624;&#xB978;&#xCABD; &#xBC29;&#xD5A5;&#xD0A4;&#xB294;
          &#xB2E4;&#xC74C; &#xB77C;&#xB514;&#xC624; &#xBC84;&#xD2BC;&#xC73C;&#xB85C;
          &#xC774;&#xB3D9;&#xD55C;&#xB2E4;.</p>
        <p>&#xB77C;&#xB514;&#xC624;&#xBC84;&#xD2BC;&#xC758; &#xC21C;&#xC11C;&#xAC00;
          &#xB9C8;&#xC9C0;&#xB9C9;&#xC774;&#xC5B4;&#xB3C4; &#xB2E4;&#xC2DC; &#xCC98;&#xC74C;&#xC73C;&#xB85C;
          &#xB3CC;&#xC544;&#xAC00; &#xC21C;&#xD658;&#xD574;&#xC57C; &#xD55C;&#xB2E4;.</p>
      </td>
    </tr>
  </tbody>
</table>​[https://www.w3.org/TR/wai-aria-practices-1.1/](https://www.w3.org/TR/wai-aria-practices-1.1/)​



