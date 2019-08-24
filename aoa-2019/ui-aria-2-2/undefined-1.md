# 그룹명 필수 항목 적용 사례

### 그룹에게 그룹명을 알려주자.

지난 시간\(작년 12월...ㅋㅋ\)에 &lt;label&gt;이 한 개이고 입력박스가 여러 개인 경우 role="group"을 이용하여 그룹으로 묶고 그룹명을 aria-labelledby 속성으로 안내해 줄 수 있다고 한 것과 연결되는 내용이다.

지난 시간 내용은 AOA 유튜브 채널에서 확인하실 수 있습니다.

[https://youtu.be/9kwnt1xjtj4](https://youtu.be/9kwnt1xjtj4)

#### &lt;input type="text"&gt; 

레이블이 한 개이고 `<input type="text">`가 여러 개인 경우 각각의 `<input>`의 title 속성을 삽입하고 고유의 입력 문구와 함께 **"필수입력"**을 삽입한다. 여러 개의 그룹 입력 박스인 경우 필수 입력을 선택하여 적용할 수 있기 때문에 각각의  `<input type="text">`의 title 속성에 **"필수입력"**을 삽입한다.

![](../../.gitbook/assets/image%20%2812%29.png)

```markup
<div id="label-title">Date of Birth
    <span class="require-ico"></span>
</div>
<div role="group" aria-labelledby="label-title">
    <input type="text" title="4 digit year (Required)">
    <input type="text" title="2 digit month (Required)">
    <input type="text" title="2 digit date (Required)">
</div>
```

> Date of Birth 그룹   
> 4 digit year \(Required\) 편집창   
> 2 digit month \(Required\) 편집창  
> 2 digit date \(Required\) 편집창

####  &lt;input type="radio"&gt; 

`<input type="radio">` 는 한 개 이상의 `input type="radio"`로 구성되고 각각의 `<label>`을 가지게 되어 있다. 라디오버튼인 경우 필수 입력을 선택하여 적용할 수 없으므로 그룹 레이블에서 **"필수입력"**을 하한번만 읽도록 적용한다.

![](../../.gitbook/assets/image%20%2836%29.png)

```markup
<div id="label-title">Mailing Address Type
    <span class="require-ico">(Required)</span>
</div>
<ul role="group" aria-labelledby="label-title"> 
   <li role="presentation">
       <input type="radio" id="homeRadio">
       <label for="homeRadio">Home</label>  
   </li>
   <li role="presentation">
       <input type="radio" id="officeRadio">                            
       <label for="officeRadio">Office</label>
   </li>
   ...
</ul>

```

> Mailing Address Type \(Required\) 그룹   
> Home 라디오 버튼 선택됨   
> Office 라디오 버튼 선택됨   
> Other 라디오 버튼 선택됨

#### &lt;select&gt;

레이블이 한 개이고 `<select>`가 여러 개인 &lt;select&gt;의 경우에도 각각의 `<select>`의 title 속성을 삽입하고 고유의 입력 문구와 함께 **"필수선택"**을 삽입한다. 여러 개의 셀렉트박인 경우 필수 선택을 선택하여 적용할 수 있기 때문이다.

![](../../.gitbook/assets/image%20%2828%29.png)

```markup
<div id="label-title">Expiration (Month/Year)
    <span class="require-ico"></span>
</div>
<div role="group" aria-labelledby="label-title">
    <select title="Month (Required)">
        <option>select</option>
        ...
    </select>
    <select title="Year (Required)">
        <option>select</option>
        ...
    </select>
</div>
```

> Expiration \(Month/Year\) 그룹   
> Month \(Required\) 콤보상자 Select 축소됨   
> Year \(Required\) 콤보상자 Select 축소됨

