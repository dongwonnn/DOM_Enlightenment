# 2장. Document 노드

### 2-1. document 노드 개요

- document로부터 상속된 HTMLDocument 생성자는 DOCUMENT_NODE를 생성한다. (window.document)
  즉, window.document는 HTMLDocument가 생성자 함수가 생성하고 이 노드는 DOCUMENT_NODE 개체다.
  ```js
  console.log(window.document.constructor); // HTMLDocument
  console.log(window.document.nodeType); // 9. (DOCUMENT_NODE)
  ```

### 2-2. HTMLDocument의 속성 및 메서드( 상속된 것 포함 )

- 주목해야 할 속성과 메서드
  1. doctype
  2. documentElement
  3. implementation
  4. activeElement
  5. body
  6. head
  7. title
  8. lastModified
  9. referer
  10. URL
  11. defaultView
  12. compatMode
  13. ownerDocument
  14. hasFocus()

### 2-3. 일반적인 HTML 문서 정보 얻기

- 문서 정보
  1. 제목 : document.title
  2. url : document.URL
  3. referer : document.referer
  4. 최종 수정일 : document.lastModified
  5. 호환 모드 : document.compatMode

### 2-4. document 자식 노드

- document 노드는 DocumentType (예: window.document) 노드 개체 하나와 Element 노드 개체(태그들..) 하나를 가질 수 있다.
  cf) window.document와 Document 개체를 혼동해선 안된다. window.document는 DOM 인터페이스의 시작점이라는 것만 알면 된다.

### 2-5. document는 <!DOCTYPE>,< html lang='en' >, < head >, < body >에 바로가기를 제공한다.

- 차례 대로
  1. document.doctype : <!DOCTYPE>
  2. document.documentElement < html lang='en'>
  3. document.head : < head>
  4. document.body : < body>
     cf) window.document : HTMLDocument(DOCUMENT_NODE) 로 부터 생성
     doctype은 DcoumentType((DOCUMENT_TYPE_NODE)) 로 부터 생성

### 2-6. document.implementation.hasFeature()를 사용하여 DOM 사양/기능 탐지하기

- document.implementation.hasFeature()를 사용하면 현재 문서에 대해 브라우저가 구현/지원하는 기능 및 수준에 대해 알 수 있다.
  예를 들어 브라우저가 Core DOM Level 3 사양을 구현했는지 메서드에 기능 명칭과 버전을 전달한다.
  `console.log(document.implementation.hasFeature('Core','3.0'))`

### 2-7. 문서 내에서 포커스를 가지고 있거나 활성 상태인 노드에 대한 참조를 얻기

- document.activeElement를 사용하면 문서 내에서 포커스를 가지고 있거나 활성 상태인 노드에 대한 참조를 바로 얻을 수 있다.
- 페이지 로드 시에 문서의 포커스를 < textarea> 노드로 설정한 후, activeElement 속성을 사용하여 해당 노드에 대한 참조를 얻을 수 있다.

  ```js
  <textarea></textarea>;

  document.querySelector("textarea").focus();

  // 지금 포커스를 받는 노드는 ? <textarea>
  console.log(document.activeElement);
  ```

### 2-8. 문서 혹은 문서 내의 특정 노드가 포커스를 가지고 있는지 판별하기

- document.hasFocus() 메서드를 사용하면 사용자가 현재 HTML 문서가 로드된 창에 포커스를 두고 있는지를 알 수 있다.
  index.html을 새로고침하고 다른 창을 누르면 false 반환.
  ```JS
  setTimeout(function () {
    console.log(document.hasFocus())
  }, 1000)
  ```

### 2-9. document.defaultView는 최상위/전역 개체에 대한 바로가기다.

- document.defaultView 속성을 이용하면 최상위 개체를 부를 수 있다. JS 환경에선 window 개체를 가르킨다.
  ```js
  document.defaultView(); // window
  ```
- 최상위 개체가 없는 DOM, 웹 브라우저에서 실행되지 않는 JS 환경의 경우, 이 속성을 이용하면 최상위 개체 영역에 접근할 수 없게 해준다.

### 2-10. Element에서 ownerDocument를 사용하여 Document에 대한 참조 얻기

- ownerDocument 속성을 호출하면 노드가 포함된 document에 대한 참조를 반환한다.
