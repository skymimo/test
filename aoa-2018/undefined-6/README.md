# Screen Reader 테스트

직접 ARIA를 사용하여 제작한 콘텐츠를 스크린리더가 제대로 읽고 있는지를 확인하기 위해서는 스크린리더를 사용해야 하며, 효과적으로 스크린리더를 배우기 위한 시간을 투자하는 것이 필요하다.

누구나 처음 스크린리더를 사용하면 혼란스럽고 절망을 경험하게 된다. 오디오를 켜는 순간 스크린리더가 어느 부분을 읽고 있는지 알 수 없는데 이는 스크린리더의 기본 동작 방식을 모르기 때문이다.

{% hint style="info" %}
스크린리더는 DOM을 복사하여 그대로 읽게 되는데, 가끔 복사과정에서 오류가 발생한다. **스크린리더를 리프레시하여 다시 DOM을 복사하고 읽게 할 수 있는데 JAWS는 Insert + ESC 이다**.
{% endhint %}

### 스크린리더의 기본 동작

* 읽기 일시 중지 :  간격, 세미콜론, 쉼표, 물음표, 단락
* 대문자는 캐럿별로, 소문자는 단어로 읽기 : 스크린리더는 만약 발음이 가능하게 충분한 모음/자음이 있으면  의미없는 단어와 약어를 발음하려고 한다. 그렇지 않은 경우 글자를 한 자 한 자 읽는다. 예\) NASA : 나사, NSF : N.S,F,  URL : earl,  SQL: S,Q,L
* JAWS는 대문자와 소문자를 소리를 강조하여 구분
* 암호 입력창은 “Star”로 발음
* 웹 페이지를 처음 로딩했을 때 페이지 타이틀을 읽음.
* 이미지의 대체텍스트는 “Graphic”이라고 먼저 읽고 이미지가 링크면, JAWS는 “Graphic link”로 발음.
* 대체 텍스트가 없는 이미지는 무시하거나 아무것도 말하지 않음 \(alt가 없는 경우 파일이름을 읽기 위한 환경설정은 가능\)
* 대체텍스트가 없는 이미지가 링크일 때는 일반적으로 링크 URL을 읽거나 이미지 파일 이름을 읽음
* JAWS는 헤딩요소를 읽을 때 헤딩과 레벨을 함께 읽음 예\)  &lt;h1&gt;  : “heading level 1”
*  페이지 로딩이 끝나면 페이지의 링크의 개수를 읽음.
*  JAWS는 현재 페이지가 만약 링크 목적지의 최종 페이지라면 “same page link”로 읽고 이전에 접속했던 페이지 링크는 “visited link”로 읽음
* 테이블 탐색 모드에서 데이터 테이블의 행과 열을 개수를 읽음
* 테이블이 올바르게 마크업되어 있다면 새로운 셀에 진입하면 컬럼과 행 제목을 읽음
* 폼에 진입했을 때 비프음과,  폼 모드로 자동으로 진입

|   |
| :--- |

