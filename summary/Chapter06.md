# 6장. Element 노드 인라인 스타일

### 6-1. style attribute(element 인라인 CSS 속성) 개요

모든 HTML element는 해당 `element`에 한정된 인라인 CSS 속성을 넣을 수 있다.

```javascript
<div style = "background-color: red">
```

### 6-2. 개별 인라인 CSS 속성 가져오기, 설정, 제거

`element` 노드 개체에 존재하는 스타일을 설정, 가져오고 제거할 수 있다.

```javascript
<body>
  <div></div>
</body>;

var divStyle = document.querySelector("div").style;

// 설정
divStyle.backgroundColor = "red";

// 가져오기
console.log(divStyle.backgroundColor);

// 제거하기
divStyle.backgroundColor = "";
```

### 6-3. 모든 인라인 CSS 속성 가져오기, 설정, 제거

`CSSStyleDeclaration` 개체의 `cssText`와 `getAttribute()`, `setAttribute()`, `removeAttribute()` 를 이용하면 모든 인라인 CSS를 가져오고, 설정, 제거할 수 있다.

```javascript
<body>
  <dib></div>
</body>;

var div = document.querySelector("div");
var divStyle = div.style;

divStyle.cssText = "bacground-color: red";
console.log(divStyle.cssText);
divStyle.cssText = "";

div.setAttribute("style", "background-color: red");
console.log(div.getAttribute("style"));
div.removeAttribute("style");
```

### 6-5. class 및 id attribute를 사용하여 element의 CSS 속성을 적용 및 제거하기

스타일 규칙은 class 및 id attribute를 사용하여 element에 추가하거나 제거할 수 있다.
`setAttribute()`와 `classList.add()`, `removeAttribute()`와 `classList.remove()` 사용

```javascript
div.setAttribute("id", "bar");
div.classList.add("foo");

div.removeAttribute("id");
div.classList.remove("foo");
```
