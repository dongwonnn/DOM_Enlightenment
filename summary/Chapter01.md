# 1장. 노드 개요

## 1.1 문서 개체 모델(DOM)은 자바스크립트 Node 개체의 계층화된 트리다.

- HTML을 작성할 때 HTML 콘텐츠를 다른 HTML 콘텐츠 내에 캡슐화하는 과정에서 **트리로 표현 가능한 계층 구조가 만들어진다.**
- HTML 문서가 **브라우저에 의해 해석되어 실제 문서를 나타내는 노드 개체들의 트리 구조로 변환된다.**
- **DOM의 목적은 JavaScript를 사용해서 이 문서에 대한 스크립트 작성(삭제, 추가, 이벤트 처리, 수정)을 위한 프로그래밍 인터페이스를 제공하는 것이다.**

## 1.2 노드 개체 유형

- HTML 문서를 다룰 때 일반적인 노드 유형

  1. DOCUMENT_NODE : ex) window.documnet
  2. ELEMENT_NODE : ex) <body>, <a>, <p>
  3. ATTRIBUTE_NODE : ex) class="body"
  4. TEXT_NODE : ex) HTML 내의 텍스트 문자
  5. DOCUMENT_FRAGMENT_NODE : ex) document.getByElementId(...)
  6. DOCUMENT_TYPE_NODE : ex) <!DOCTYPE html>

  - JavaScript 브라우저 환경에서 Node 개체의 속성으로 기록되는 상수 값으 속성과 동일히다.

  ```
  console.log(node.ELEMENT_NODE)    // 1 출력
  ```

## 1.3 Node 개체로부터 상속받은 하위 노드 개체

## 1.4 노드를 다루기 위한 속성 및 메소드

## 1.5 노드의 유형과 이름 식별하기

## 1.6 노드 값 가져오기

## 1.7 JavaScript 메서드를 사용해서 Element 및 Text 노드를 생성하기

## 1.8 JavaScript 문자열을 사용하여 DOM 에 Element 및 Text 노드를 생성 및 추가하기

## 1.9 DOM 트리의 일부를 JavaScript 문자열로 추출하기

## 1.10 appendChild() 및 insertBefore()를 사용하여 노드 개체를 DOM에 추가하기

## 1.11 removeChild() 및 replaceChild()를 사용하여 노드를 제거하거나 바꾸기

## 1.12 cloneNode()를 사용하여 노드를 복제하기

## 1.13 노드 컬렉션 (NodeList와 HTMLCollection)에 대한 이해

## 1.14 직계 자식 노드 전부에 대한 리스트/컬렉션 얻기

## 1.15 NodeList나 HTMLCollection을 JavaScript 배열로 변환

## 1.16 DOM 내의 노드 탐색

## 1.17 contains()와 compareDocumentPosition() 으로 DOM 트리 내의 Node 위치를 확인하기

## 1.18 두 노드가 동일한지 판단하기
