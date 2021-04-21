# 1장. 노드 개요

### 1.1 문서 개체 모델(DOM)은 자바스크립트 Node 개체의 계층화된 트리다.

HTML 콘텐츠를 다른 HTML 콘텐츠 내에 캡슐화하여 트리로 표현 가능한 계층구조가 만들어진다.
브라우저는 HTML 코드를 해석해서 트리 형태로 구조화된 노드를 이용해 **DOM**을 생성한다.
**DOM의 목적** : JS를 이용해 이 문서에 대한 스크립트 작성을 위한 프로그래밍 인터페이스 제공

### 1.2 노드 개체 유형

HTML을 다룰 때 마주치는 일반적인 노드 유형 (nodeType). 매핑되는 **숫자코드**가 존재한다.

```js
1: ELEMENT_NODE - 태그들. <body>, <a>, <p>...
2: ATTRIBUTE_NODE - class 지정 태그 class = "funEdges"...
3: TEXT_NODE - 텍스트 문자
9: DOCUMENT_TYPE
10: DOCUMENT_TYPE_NODE
11: DOCUMENT_FRAGMENT_NODE
```

노드 유형들의 인스턴스를 생성하는 인터페이스/생성자의 이름, 노드 예시

```js
HTMLBodyElement: ELEMENT_NODE;
TEXT: TEXT_NODE;
HTMLDocument: DOCUMENT_NODE;
```

### 1.3 Node 개체로부터 상속받은 하위 노드 개체

DOM 트리의 각 노드 개체는 Node로부터 속성과 메서드를 상속받는다.
`Object < Node < Document < HTMLDocument`

### 1.4 노드를 다루기 위한 속성 및 메소드

모든 노드 개체는 속성과 메서드를 Node 개체로부터 상속받는다.
이 **속성 및 메소드는 DOM을 조작, 조사, 탐색하는 기준이 되는 값과 함수다.** 또, document, HTMLElement 인터페이스와 같은 하위 노드 인터페이스에서도 속성 및 메소드를 제공한다.
Node 속성

- childNodes
- firstChild
- lastChild
- nextSibling
- nodeName
- nodeType
- nodeValue
- parentNode
- previousSibling

- Node 메소드

  - appendChild()
  - cloneNode()
  - compareDocumentPosition()
  - contains()
  - hasChildNodes()
  - insertBefore()
  - isEqualNode()
  - removeChild()
  - replaceChild()

Document 메서드

- document.createElement()
- document.createTextNode()
  HTML \*ELEMENT 속성
- innerHTML
- outerHTML
- textContent
- innerText
- outerText
- firstElementChild
- lastElementChild
- nextElementChild
- previousElementChild
- childrem
- HTML element 메서드
  - insertAdjacentHTML()

### 1.5 노드의 유형과 이름 식별하기

모든 노드는 Node로부터 상속받는 **NodeType 및 NodeName** 속성을 가진다.

- a 태그의 경우 nodeType은 ELEMENT_NODE에 매핑되는 1, nodeName은 'A'
- 이것으로 명확하지 않은 노드의 유형을 판별할 수 있다.

### 1.6 노드 값 가져오기

**noveValue** 속성은 Text와 Comment 노드에서 실제 텍스트 문자열을 추출하는데 초점을 가지고 있다.

```js
<a href="#">Hi</a>;

// sciprt
console.log(document.querySelector("a".firstChild.nodeValue)); // Hi
```

### 1.7 JavaScript 메서드를 사용해서 Element 및 Text 노드를 생성하기

브라우저는 HTML 문서를 해석할 때 초기 로딩을 HTML 파일 내용을 기반으로 노드와 트리를 구성한다. 이때 JS를 이용하여 **직접 노드를 생성하는 것**도 가능하다.

> createElement() : Element 노드 생성
> createTextNode() : Text 노드 생성

```js
// div Element 생성
var elementNode = document.createElement("div");
// Hi text 생성
var textNode = document.createTextNode("Hi");
```

### 1.8 JavaScript 문자열을 사용하여 DOM 에 Element 및 Text 노드를 생성 및 추가하기

JS 문자열을 사용하여 **DOM에 노드를 생성하고 추가**하는 기능

- innerHTML() : Element와 Text Node를 추가.
  문자열을 실제 DOM 노드로 변환. 무겁기 때문에 삼가야 한다.
- textContent() : Text 노드만 생성해 문자열로 갱신
- innerText() : DOM에 Text Node만 추가
- outerHTML() : 기존의 것 교체
- insertAdacentHTML()

```JS
<div id="A"></div>
// DOM에 <strong> Element와 Hi text node 추가
document.getElementById('A').innerHTML = `<strong>Hi</strong>`
```

### 1.9 DOM 트리의 일부를 JavaScript 문자열로 추출하기

생성하고 추가하는데 쓰는 innerHTML, outerHtml, textContent를 이용해 **DOM을 JS 문자열로 추출**할 수 있다.

- innerHtml : 일부 추출
- outerHtml : 전체 추출
- textContent : 모든 텍스트 추출

```JS
<div id="A"><i>Hi</i></div>
console.log(document.getElementById('A').innerHTML) // <i>Hi<i>
console.log(document.getElementById('A').outerHTML) // <div id="A"><i>Hi</i></div>
```

### 1.10 appendChild() 및 insertBefore()를 사용하여 노드 개체를 DOM에 추가하기

**JS 노드 개체를 DOM 트리에 삽입**할 수 있게 해준다.

- appendChild() : 메서드가 호출된 노드의 **자식 노드 끝**에 삽입 가능하게 한다. 자식이 존재하지 않으면 해당 노드가 첫 번째 자식으로 추가된다.

```js
<p>Hi</p>;

// strong Element 생성
var elementNode = document.createElement("strong");

// p 태그를 찾은 후 뒤에 삽입
// 결과적으로 <p><strong>Hi</strong></p>
document.querySelector("p").appendChild(elementNode);
```

- insertBefore() : **삽입 위치를 조정**할 때 사용한다. 삽입될 노드와 해당 노드를 삽입하고자 하는 문서 내의 참조 노드 **2가지 매개변수**가 필요하다.

```js
<ul>
  <li>2</li>
  <li>3</li>
</ul>;

var firstLi = document.createElment("li");
var ul = document.querySelector("ul");

// <li>2</li> 앞에 firstLi 생성
ul.insertBefore(firstLi, ul);
```

#### [next]()
