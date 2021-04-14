# 1장. 노드 개요 (2)

### 1.11 removeChild() 및 replaceChild()를 사용하여 노드를 제거하거나 바꾸기

- DOM을 제거하는 과정 : removeChild()

  1. 삭제하고자 하는 노드를 선택
  2. 부모 노드에 대한 접근 얻기 (parentNode)
  3. 부모 노드에서 삭제할 노드에 대한 참조 전달하여 removeChild() 메소드 호출

  ```js
  <div id="A">Hi</div>;
  <div id="B">Dude</div>;

  //script
  var divA = document.getElementById("A");
  divA.parentNode.removeChild(divA);

  // divB는 textNode를 가르킴.
  // removeChild를 제거하면 <div id="B">만 남게됨
  var divB = document.getElementById("B").firstChild;
  divB.parentNode.removeChild(divB);
  ```

- 노드를 제거하는 대신 업데이트 : replaceChild()

  ```js
  <div id="A">Hi</div>;
  <div id="B">Dude</div>;

  //script
  var divA = document.getElementById("A");
  var newSpan = document.createElement("span");

  // div 대신 <span>Howdy</span>으로 업데이트
  newSpan.textContent = "Howdy";
  divA.parentNode.replaceChild(newSpan, divA);
  ```

### 1.12 cloneNode()를 사용하여 노드를 복제하기

- cloneNode() 메서드를 사용하여 단일 노드 혹은 모든 자식 노드를 복제할 수 있다.

  1. 단일 노드 복사

  ```js
  <ul>
    <li>2</li>
    <li>3</li>
  </ul>;

  // cloneUL 은 <ul> 껍데기만 복사한다.
  var cloneUL = document.querySelector("ul").cloneNode();
  ```

  2. 모든 자식 노드 복사. cloneNode() 매개변수로 true 전달

  ```js
  <ul>
    <li>2</li>
    <li>3</li>
  </ul>;

  // 매개변수 true 전달, 자식 노드 모두 복사
  var cloneUL = document.querySelector("ul").cloneNode(true);
  ```

- 이벤트로 인한 추가된 것은 복제되지 않는다.

### 1.13 노드 컬렉션 (NodeList와 HTMLCollection)에 대한 이해

- 트리에서 노드 그룹을 선택하거나 사전에 정의된 노드 집합에 접근하려면 해당 노드들이 NodeList (예 : document.querySelectorAll(\*))나 HTMLCollection (예: document.scripts) 내에 있어야 한다.
- 배열과 유사한 이 개체 컬렉션은 다음과 같은 특징을 가진다.
  1. 컬렉션은 라이브 상태 혹은 정적일 수 있다. 컬렉션 내의 노드들이 현재 문서 혹은 현재 문서의 **스냅샷**의 일부라는 뜻.
     cf) **스냅샷 : 특정 시점의 리파지토리에 보관**
  2. 노드 컬렉션은 트리 순서에 따라 컬렉션 내에서 정렬.
  3. 요소 개수를 나타내는 length 속성

### 1.14 직계 자식 노드 전부에 대한 리스트/컬렉션 얻기

- childNodes 속성을 사용하면 **직계 자식 노드에 대해 배열 형태**의 리스트가 나온다.

  ```js
  <ul>
    <li>2</li>
    <li>3</li>
  </ul>;

  var ulElementChildNodes = document.querySelector("ul").childNodes;

  // 결과 : NodeList(5) : 0 : text, 1 : li : <li>2</li>
  //                      2 : text, 3 : <li>3</li>, 4: text
  ```

- element 노드 뿐 아니라 Text, Comment 노드도 포함된다.

## 1.15 NodeList나 HTMLCollection을 JavaScript 배열로 변환

- 노드 컬렉션은 배열 형태지만 array의 메소드를 상속받는 진정한 배열은 아니다. isArray()를 사용하여 배열인지 아닌지 true/false로 확인 가능하다.
  `Array.isArray(document.querySelectorAll('a')) // false`
- 진정한 JS 배열로 바꾸면 좋은 점
  1. 라이브 리스트를 현재 DOM에 국한되지 않은 리스트 **스냅샷**을 만들 수 있다.
  2. Array 개체가 제공하는 **메서드들에 접근** 가능하다
- **call(), apply()**에 유사 배열 리스트를 전달하면 진짜 JS 배열을 반환하는 메서드를 호출한다.
  ```javascript
  // call로 진짜 배열을 반환해 true 값을 가진다.
  Array.isArray(Array.prototype.slice.call(document.querySelectorAll("a")));
  ```

## 1.16 DOM 내의 노드 탐색

- 노드 참조 (document.querySelector('ul'))에 다음과 같은 속성들을 사용하여 DOM을 탐색하여 다른 노드에 대한 참조를 얻을 수 있다.

  1. parentNode : 참조 노드의 부모 노드 탐색
  2. firstChild : 참조 노드의 첫 번째 자식 노드
  3. lastChild : 참조 노드의 마지막 자식 노드
  4. nextSibling : 참조 노드의 다음 형제 노드
  5. previousSibling : 참조 노드의 이전 형제 노드

  ```js
  <body>
    <ul>
      <!-- comment -->
      <li>2</li>
      <li>3</li>
    </ul>
  </body>;

  var ul = document.querySelector("ul");
  ul.parentNode.nodeName; // body
  ul.firstChild.nodeName; // li가 아닌 comment가 출력
  ```

- **text와 comment 노드를 무시하고 DOM을 탐색하고 싶을 때**

  1. firstElementChild
  2. lastElementChild
  3. nextElementChild
  4. previousElementChild
  5. children
  6. parentElement

  ```js
  <body>
    <ul>
      <li>2</li>
      <li>3</li>
    </ul>
  </body>;

  var ul = document.querySelector("ul");
  ul.firstElementChild.nodeName; // comment 대신 li
  ```

## 1.17 contains()와 compareDocumentPosition() 으로 DOM 트리 내의 Node 위치를 확인하기

- **contains()** 메서드를 사용하면 특정 노드가 다른 노드 내에 **포함**되었는지를 알 수 있다.
  ```js
    // html 안에 body가 있는지 확인.
    // inside : true
    ver inside = document.querySelector('html').contains(document.querySelector('body'));
  ```
  - 노드가 동일한 경우 true 반환
- compareDocumentPosition()을 이용하면 **주변 노드 위치에 대한 확실한 정보**를 얻을 수 있다.
  - compareDocumentPosition()를 통해 반환되는 숫자 코드
    0 : 동일한 노드, 1 : 존재하지 않음. 2 : 선택된 노드 앞에 있음
    4 : 선택된 노드 뒤에 있음. 8 : 선택된 노드의 조상임.
    16,10 : 선택된 노드의 자손임

## 1.18 두 노드가 동일한지 판단하기

- 동일한 경우인지 판단하는 기준

  1. 두 노드가 동일한 형식이다 .
  2. 둘 다 null 이거나, 동일한 길이와 동일한 문자여야 한다.
  3. 둘 다 null 이거나, 동일한 길이를 가지고 같은 인덱스의 노드가 동일해야 한다. **정규화**가 동일성에 영향을 미쳐 비교하기 전에 노드를 정규화 해야한다.
     cf) **노드 정규화 : Element 안에서 띄어쓰기 같은 text가 있을 경우 하나의 dom을 차지한다. 이런 경우 한 줄로 깔끔하게 정규화할 수 있다.**

- **isEqualNode() 메서드**를 호출해서 알 수 있다. true / false

  ```js
  // 동일 상태
  <input type="text">
  <input type="text">

  // 동일하지 않은 상태 ( 자식 노드 )
  <textarea>foo</textarea>
  <textarea>bar</textarea>

  var input = document.querySelectorAll('input');
  input[0].isEqualNode(input[1])  // 완전 동일한 상태. true

  ```

- 완전히 동일한 것이 아니라 **동일한 노드를 참조하고 있는지 확인하려면 '===' 연산자**를 이용하여 확인할 수 있다.
  `document.body === document.body`
