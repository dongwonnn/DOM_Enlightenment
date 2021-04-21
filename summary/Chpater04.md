# 3장. Element 노드 선택

### 3-1. 특정 Element 노드 선택하기

단일 element 노드에 대한 참조를 얻는 흔한 메서드

1. **querySelector()**
2. **getElementById()**

```javascript
<ul>
  <li>1</li>
  <li>2</li>
  <li>3</li>
</ul>;

document.querySelector("li").textContet; // 1
document.getElementById("last").textContet; // 3
```

**getElementById()** 메서드는 CSS 문법 형식의 매개변수를 허용한다.

### 4-2. Element 노드 리스트 선택 및 생성하기

HTML 문서 내의 노드 리스트를 선택 및 생성하는 메서드들

1. **querySelectorAll()**
2. **getElementByTagName()**
3. **getElementByClassName()**

```javascript
<ul>
  <li>1</li>
  <li>2</li>
  <li>3</li>
</ul>;

// 셋 다 동일하기 li element 리스트를 생성, 선택한다
document.querySelectorAll("li");
document.getElementByTagName("li");
document.getElementByClassName("liClass");
```

### 4-3. 직계 자식 Element 노드 모두 선택하기

**children** 속성을 사용해 element 의 자식 노드를 모두 선택한다.

```javascript
<ul>
  <li>
    <string>Hi</strong>
  </li>
  <li>there</li>
</ul>;

// [<li>, </li>] 출력
var ulElm = document.querySelector("ul").children;
```

### 4-4. 컨텍스트 기반 Elemenet 선택

1. **querySelector()**
2. **getElementById()**
3. **querySelectorAll()**
4. **getElementByTagName()**
5. **getElementByClassName()**
   위 5가지 메서드들은 해당 메서드의 결과를 DOM 트리의 특정 부분으로 제한할 수 있게 해준다.

### 4-5. 사전에 구성된 Element 노드 선택/리스트

사전 구성된 유사 배열 리스트

1. **document.all**
   HTML 문서 내의 모든 element
2. **document.forms**
   HTML 문서 내의 모든 **form** element
3. **document.images**
   HTML 문서 내의 모든 **img** element
4. **document.links**
   HTML 문서 내의 모든 **a** element
5. **document.scripts**
   HTML 문서 내의 모든 **script** element
6. **document.styleSheets**
   HTML 문서 내의 모든 **style** 혹은 **link** element
