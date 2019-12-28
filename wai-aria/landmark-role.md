---
description: '랜드마크 탐색키 -  JAWS : R키, NVDA : D키'
---

# Landmark Role

### role="banner"

> banner

웹 사이트의 로고나 사이트 제공자, 웹 페이지의 검색 기능을 포함하는 영역으로 웹 페이지의 상단의 영역을 뜻한다. role="banner"는 웹 페이지에서 1개만 사용 가능하며 최상위 레벨로 사용한다.

### role="main"

> main region

주요 정보를 포함하거나 직접적인 연관이 있는 영역에 사용하는 landmark로 웹 페이지 상단에서 "메인 콘텐츠로 이동" 과 같은 스킵네비게이션에서 메인으로 갈 때 사용하는 목적지이다.

### role="complementary"

> complementary information

웹 사이트 내에서 보조 정보 영역에 사용하는 landmark로 날씨나 주식정보 등 주요 정보가 아닌 영역에 사용하는 landmark이다.

### role="search"

> search region

웹 사이트의 검색 기능을 수행하는 입력박스와 검색 버튼 등이 조합된 영역에 사용한다.

### role="region"

main, complementary, navigation 등의 landmark 를 사용하지 않은 곳으로 사용 목적이 불분명한 영역에 제한적으로 사용한다. 

### role="contentinfo"

> content information

copyright와 개인정보 관련 링크가 포함된 영역에 사용하는 landmark이다.

### role="navigation"

> navigation region

웹 사이트 탐색을 위한 링크의 집합과 같은 영역에 사용하는 landmark이다.

### role="form"

authors SHOULD use the search role and not the generic form role. Authors SHOULD provide a visible label for the form referenced with aria-labelledby. If an author uses a script to submit a form based on a user action that would otherwise not trigger an onsubmit event \(for example, a form submission triggered by the user changing a form element's value\), the author SHOULD provide the user with advance notification of the behavior.

