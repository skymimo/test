---
description: '랜드마크 탐색키 -  JAWS : R키, NVDA : D키'
---

# Landmark Role

### role="banner"

> banner

웹 사이트의 로고나 사이트 제공자, 웹 페이지의 검색 기능을 포함하는 영역으로 웹 페이지의 상단의 영역을 뜻한다. role="banner"는 웹 페이지에서 1개만 사용 가능하며 최상위 레벨로 사용한다.

### role="main"

> main region

주요 정보를 포함하거나 직접적인 연관이 있는 영역에 사용하는 landmark로 웹 페이지 상단에서 "메인 콘텐츠로 이동" 과 같은 스킵네비게이션에서 메인으로 갈 때 사용하 목적지이다.

### role="complementary"

> complementary information

There are various types of content that would appropriately have this [role](https://www.w3.org/TR/wai-aria-1.1/#dfn-role). For example, in the case of a portal, this may include but not be limited to show times, current weather, related articles, or stocks to watch. 

### role="search"

> search region

A [`landmark`](https://www.w3.org/TR/wai-aria-1.1/#landmark) region that contains a collection of items and objects that, as a whole, combine to create a search facility.

### role="region"

Authors _SHOULD_ limit use of the region role to sections containing content with a purpose that is not accurately described by one of the other [`landmark`](https://www.w3.org/TR/wai-aria-1.1/#landmark) roles, such as [`main`](https://www.w3.org/TR/wai-aria-1.1/#main), [`complementary`](https://www.w3.org/TR/wai-aria-1.1/#complementary), or [`navigation`](https://www.w3.org/TR/wai-aria-1.1/#navigation).

### role="contentinfo"

> content information

Examples of information included in this region of the page are copyrights and links to privacy statements.

### role="navigation"

> navigation region

A collection of navigational [elements](https://www.w3.org/TR/wai-aria-1.1/#dfn-element) \(usually links\) for navigating the document or related documents.

### role="form"

authors SHOULD use the search role and not the generic form role. Authors SHOULD provide a visible label for the form referenced with aria-labelledby. If an author uses a script to submit a form based on a user action that would otherwise not trigger an onsubmit event \(for example, a form submission triggered by the user changing a form element's value\), the author SHOULD provide the user with advance notification of the behavior.

