# NVDA는 그나마 낫지

테이블의 태그에 position:absolute를 사용하면 행을 하나 더 추가하여 읽는 현상이 있다. 확인 결과. [https://bugzilla.mozilla.org/show\_bug.cgi?id=995888](https://bugzilla.mozilla.org/show_bug.cgi?id=995888) 버그로 등록됨

로딩 콘텐츠가 존재하는 페이지는 FF/NVDA실행 시 초기 로드되면 “alert”이라고 읽는데, 이를 해결하기 위해 로딩 콘텐츠에 삽입되는 role="alert" 속성을 미리 삽입하지 않고 로딩이 발생할 때 삽입한다.

IE/NVDA 조합에서 클릭커블하지 않은 요소에서 스크린리더가 “clickable”이라고 읽는 현상이 있음. 이는 backbone 프레임웍에서 기본으로 사용하는 방법으로 전체를 감싸는 상위 콘텐츠에 자바스크립트로 온클릭 이벤트를 적용했을 때 발생함. 체크인과 회원가입은 수정되었으나, 부킹페이지 전반적으로 발생

캘린더에서 달이 바뀌면 바뀐 달을 스크린리더가 읽어야 하지만, aria-live="assertive"로 삽입하였지만 NVDA에서 두 번 읽는 현상이 발생하여 최하위 노드에 aria-live="off"를 삽입하니 NVDA에서 한번 읽음. 그러나 JAWS 에서는 안읽는 경우가 더러 발생함.

캘린더에서 모든 날짜를 선택하면 "선택됨"이라고 읽고 있어 aria-select="false"를 삽입하여 해결

