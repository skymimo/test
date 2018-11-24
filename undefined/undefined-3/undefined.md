# Modal Dialog 적용 사례

### Non Nodal Dialog vs Modal Dialog 

논모달과 모달은 목적이 다른 다이얼로그이다. 

모달은 다이얼로그를 제외한 나머지 부분은 컨트롤을 할 수 없게 하기 위해 배경 콘텐츠는 어두워지며 컨트롤을 할 수 없다. 논모달은 이 와는 반대로 다이얼로그와 함께 배경 콘텐츠도 컨트롤 할 수 있을 때 사용한다.

### Login Modal Dialog

Modal Dialog의 대표적 예제로 Login Modal Dialog를 보면 로그인 기능에만 집중시키기 위해 배경 콘텐츠는 컨트롤을 할 수 없으며 배경도 어두워지게 된다.

![](../../.gitbook/assets/image%20%287%29.png)

이런 시각적인 표현을 스크린리더 사용자에게 알리기 위해 Modal Dialog의 컨테이너 role="dialog"를 삽입하고 Modal Dialog를 제외한 배경 콘텐츠에는 모두 aria-hidden="true" 속성을 삽입하여 스크린리더에서 읽지 않게 한다. 

role="dialog"와 함께 aria-modal 속성을 사용하면 배경 콘텐츠에 삽입된 aria-hidden 속성을 대체할 수도 있으나 스크린리더 호환문제로 아직 사용하지 않았다.

기본 Modal Dialog 소스는 아래와 같이 전체 컨테이너에 role="dialog"가 삽입하고 제목은 시각적으로 보여지는 헤딩 요소와 aria-labelledby와 연결한다. 

```markup
<div role="dialog" aria-labelledby="title-dialog">
    <div role="document" tabindex="-1">
        <h2 id="title-dialog">로그인</h2>
        <p>아이디 또는 스카이패스 번호로 로그인이 가능합니다.</p>
         콘텐츠 영역
     </div>
</div>
```

### Modal Dialog 기본 포커스의 이동

Modal Dialog가 열리게 되면 기본적으로 dialog 안의 role="document" 를 갖고 있는 요소에 tabindex="-1"을 삽입하고 포커스가 이동된다. role="document"를 사용한 이유는 dialog 내에 가상모드로 탐색할 수 있는 콘텐츠가 있다는 것을 알리기 위함이다.

Tab키를 누르면 키보드의 포커스는 포커서블한 요소로 계속 이동하며 사용자가 닫지 않는 한 Modal Dialog 안에서만 계속 순환된다. 

#### 입력박스와 같은 폼 요소가 있는 Modal Dialog의 포커스 이동



