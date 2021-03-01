# 1장. 노드 개요

## 1.1 문서 개체 모델(DOM)은 자바스크립트 Node 개체의 계층화된 트리다.

- HTML을 작성할 때 HTML 콘텐츠를 다른 HTML 콘텐츠 내에 캡슐화하는 과정에서 **트리로 표현 가능한 계층 구조가 만들어진다.**
- HTML 문서가 **브라우저에 의해 해석되어 실제 문서를 나타내는 노드 개체들의 트리 구조로 변환된다.**
- **DOM의 목적은 JavaScript를 사용해서 이 문서에 대한 스크립트 작성(삭제, 추가, 이벤트 처리, 수정)을 위한 프로그래밍 인터페이스를 제공하는 것이다.**

## 1.2 노드 개체 유형

- HTML 문서를 다룰 때 일반적인 노드 유형

  - DOCUMENT_NODE : ex) window.documnet
  - ELEMENT_NODE : ex) <body>, <a>, <p>
  - ATTRIBUTE_NODE : ex) class="body"
  - TEXT_NODE : ex) HTML 내의 텍스트 문자
  - DOCUMENT_FRAGMENT_NODE : ex) document.getByElementId(...)
  - DOCUMENT_TYPE_NODE : ex) <!DOCTYPE html>

  - JavaScript 브라우저 환경에서 Node 개체의 속성으로 기록되는 상수 값으 속성과 동일히다.

  ```
  console.log(node.ELEMENT_NODE)    // 1 출력

    for(var key in Node)
        console.log(key, Node[key])     // DOCUMENT_NODE , 1
                                        // ATTRIBUTE_NODE , 2

  ```

## 1.3 Node 개체로부터 상속받은 하위 노드 개체

- 일반적으로 DOM 트리의 각 노드 개체는 Node로부터 속성과 메서드를 상속받는다.
- 노드 유형에 따라 Node 개체를 확장한 하위 노드 개체/인터페이스가 추가로 존재한다.
  - Object > Node > Element > HTMLElement..

## 1.4 노드를 다루기 위한 속성 및 메소드

- 모든 노드 개체는 속성과 메서드를 1차적으로 Node 개체로부터 상속받는다.
- 이 속성, 메소드는 DOM을 조작, 조사, 탐색하는 기준이 되는 값과 함수다.
- 노드 인터페이스에서 제공되는 속성, 메소드 외에 하위 노드 인터페이스에서도 수많은 속성, 메소드가 존재한다.
- 가장 흔히 사용되는 Node 속성 및 메서드들

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
