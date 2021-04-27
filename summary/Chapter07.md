# 7장. Text 노드

### 7-1. Text 개체 개요

HTML 문서에서 텍스트는 text 노드를 만들어내는 Text() 생성자 함수의 인스턴스로 표현된다. `element` 사이에 섞여있는 텍스트는 text 노드로 변환된다.

```javascript
<p>hi</p>;

var textHi = document.querySelector("p").firstChild;

textHi.constructor; // Text()
```

### 7-2. Text 개체 및 속성

주목할 만한 속성 및 메서드들

- textContent
- splitText()
- appendData()
- deleteData()
- insertData()
- repalceData()
- subStringData()
- normalize()
- data
- document.creteTextNode()

### 7-3. 공백도 Text 노드를 생성한다.

DOM이 생성될 때, 텍스트 문자뿐만 아니라 **공백, 줄바꿈**도 text 노드로 만들어진다.

### 7-4. Text 노드 생성 및 삽입하기

Text 노드는 브라우저가 HTML 문서로 해석되어 DOM이 자동으로 생성된다. 그 이후에는 `createTextNode()`를 사용해서 프로그래밍적으로 text 노드를 생성할 수 있다.

```javascript
<div></div>;

var textNode = docuement.createTextNode("Hi");
document.querySelector("div").appendChild(textNode);

document.querySelector("div").innerText; // Hi
```

- 프로그래밍 적으로 생성된 DOM 구조에도 text 노드를 삽입할 수 있다.

### 7-5. .data나 nodeValue로 text 노드 값 가져오기

Text 노드로 표현되는 텍스트 값과 데이터는 `.data`나 `nodeValue` 속성을 사용하여 노드에서 추출할 수 있다.

```javascript
<p>Hi</p>;

document.querySelector("p").firstChild.data; // Hi
document.querySelector("p").firstChild.nodeValue; // Hi
```

### 7-6. appendChild(), deleteData(), inserData(), replaceData(), subStringData()로 text 노드 조작하기

Text 노드가 메서드를 상속받는 CharctorData 개체는 Text 노드의 하위 값을 조작하고 추출하기 위한 메서드를 제공한다.

- **appendData()** : 데이터 추가
- **deleteData(index, 개수)** : index ~ index + 개수 까지 삭제
- **insertData(index, text)** : index 부터 추가할 text
- **replaceDta(index, 개수, 데이터)** : index ~ index + 개수 자리에 데이터 교체
- **subStringData(index, 개수)** : index ~ index + 개수 만큼의 데이터 추출

```javascript
<p>Go big Blue Blue</p>;

var pElementText = document.querySelector("p").firstChild();

pElementText.appendData("!"); // ! 추가
pElementText.deleteData(7, 5); // 7번째 index에서 5개 삭제. Blue 삭제
pElementText.insertData(7, "Blue "); // 7번째 index에 Blue 추가
pElementText.replaceDta(7, 5, "Bunny "); // Blue 대신 Bunny 교체
pElementText.subStringData(7, 10); // Blue Bunny 추출
```

### 7-9. textContent와 innerText 간의 차이

- **innerText**는 CSS가 반영된다. 숨겨진 텍스트가 있을 경우 무시하지만 **textContent**는 반영한다.
- **innerText**는 CSS의 영향을 받으므로 리플로우가 발생하지만 **textContent**는 그렇지 않다.
- **innerText**는 script 태그와 style element 내에 포함된 Text 노드를 무시한다
- **innerText**는 텍스트를 정규화해서 반환한다. **textContent**는 문서 내에 있는 것을 마크업만 제거해서 그대로 반환한다.
- **innerText**는 비표준이고 브라우저에 국한된다. **textContent**는 DOM 사양으로 구현되었다.

### 7-.11 splitText()를 사용하여 텍스트 노드를 분할하기

예를 들어 "Hey Yo!" 의 경우 splitText()를 사용하면 분할된 텍스트를 가진 노드를 반환한다.

```javascript
<p>Hey Yo!</p>;

document.querySelector("p").firstChild.splitText(4).data; // Yo!
```
