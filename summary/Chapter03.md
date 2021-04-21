# 3장. Element 노드

### 3-1. HTML \*Element 개체 개요

HTML 문서 내의 각 Element들은 고유한 성질을 가지며 각자 element를 DOM 트리내의 노드 개체로 인스턴스화하는 고유한 js 생성자를 가진다

### 3-2. HTML \*ELEMENT 개체의 속성 및 메서드

1. createElement()
2. tagName()
3. children
4. getAttribute()
5. setAttribute()
6. hasAttribute()
7. removeAttribute()
8. classList()
9. dataset
10. attributes

### 3-3. Element 생성

Element 노드는 브라우저가 HTML 문서를 해석해 DOM이 만들어질 때 인스턴스화한다.
이것 외에 **createElement()** 메서드를 사용하여 프로그래밍으로 Element 노드를 생성할 수도 있다.
주로 **appendChild**를 이용하여 추가할 수 있다.

```javascript
var elementNode = document.createElement("textarea");

document.body.appendChild(elementNode);
```

### 3-4 Element의 태그 이름 얻기

**tagName** 속성을 사용해 element의 이름에 접근할 수 있다.
특이점은 대문자로 변형되어 반환한다.

```javascript
console.log(document.querySelector("a").tagName); // 'A'
```

### 3-5 Element의 Attribute 및 값에 대한 리스트/컬렉션 얻기

**attributes** 속성을 사용하면 현대 element의 속성 노드의 컬렉션을 얻을 수 있다.

```javascript
<a href="#" title="asd" data="dd" />;

document.querySelector("a").attributes; // href, title, data..
```

### 3-6. Element의 Attribute 값 획득, 설정, 제거

각각 **getAttribute()**, **setAttribute()**, **removeAttribute()**를 이용해 설정할 수 있다.

```javascript
<a href="#" />;

var atts = document.querySelector("a");

a.removeAttribute("href");
a.setAttribute("href", "#");
a.getAttribute("href"); // #
```

### 3-7. Element가 특정 attribute를 가지고 있는지 확인하기

**hasAttribute()** 메서드를 이용해 true/false로 판별할 수 있다.

```javascript
<a href="#" />;

var atts = document.querySelector("a");
atts.hasAttribute("href"); // true
```

### 3-8. Class Attribute 값 리스트 얻기

**classList** 를 사용하면 className으로 얻는 것 보다 훨씬 쉽게 class attribute를 얻을 수 있다.

```javascript
<div class="big brown bear" />;

var elm = document.querySelector("div");
elm.classList; // big brown bear {0= "", 1 ="" , 2 =""}
```

### 3-9. Class attribute에 하위 값 추가 및 제거하기

**classList.add()** 와 **classList.remove()** 를 이용해 attribute를 간단히 편집 가능하다.

```javascript
<div class="dog" />;

var elm = document.querySelector("div");

elm.classList.add("cat");
elm.classList.remove("dog"); // cat만 남는다.
```

### 3-10. Class attribute 값 토글

**classList.toggle()** 을 사용하면 하위 값들을 토글시킬 수 있다. 없다면 생성도 가능하다.

```javascript
<div class="visible" />;

var elm = document.querySelector("div");

elm.classList.toggle("visible"); // visible 삭제
elm.classList.toggle("glow"); // glow 생성
```

### 3-11. Class attribute 값이 특정 값 가지고 있는지 확인하기

**classList.contains()** 메서드를 사용해 특정 값을 가지고 있는 지 판별 가능하다.

```javascript
<div class="big brown bear" />;

var elm = document.querySelector("div");

elm.classList.contains("brown"); // true
```

### 3-12. data-\* attribute를 가져오고 설정하기
