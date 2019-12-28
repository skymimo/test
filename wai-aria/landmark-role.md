# Landmark Role

### role="banner"

Site-oriented content typically includes things such as the logo or identity of the site sponsor, and a site-specific search tool. A banner usually appears at the top of the page and typically spans the full width.

### role="main"

This marks the content that is directly related to or expands upon the central topic of the document.

### role="complementary"

There are various types of content that would appropriately have this [role](https://www.w3.org/TR/wai-aria-1.1/#dfn-role). For example, in the case of a portal, this may include but not be limited to show times, current weather, related articles, or stocks to watch. 

### role="search"

A [`landmark`](https://www.w3.org/TR/wai-aria-1.1/#landmark) region that contains a collection of items and objects that, as a whole, combine to create a search facility.

### role="region"

Authors _SHOULD_ limit use of the region role to sections containing content with a purpose that is not accurately described by one of the other [`landmark`](https://www.w3.org/TR/wai-aria-1.1/#landmark) roles, such as [`main`](https://www.w3.org/TR/wai-aria-1.1/#main), [`complementary`](https://www.w3.org/TR/wai-aria-1.1/#complementary), or [`navigation`](https://www.w3.org/TR/wai-aria-1.1/#navigation).

### role="contentinfo"

Examples of information included in this region of the page are copyrights and links to privacy statements.

### role="navigation"

A collection of navigational [elements](https://www.w3.org/TR/wai-aria-1.1/#dfn-element) \(usually links\) for navigating the document or related documents.

### role="form"

authors SHOULD use the search role and not the generic form role. Authors SHOULD provide a visible label for the form referenced with aria-labelledby. If an author uses a script to submit a form based on a user action that would otherwise not trigger an onsubmit event \(for example, a form submission triggered by the user changing a form element's value\), the author SHOULD provide the user with advance notification of the behavior.

