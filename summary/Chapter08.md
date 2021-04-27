# 8장. DocumenetFragment 노드

**virtual DOM, 가상 돔과 관련이 많음**

### 8-1. DocumenetFragment 개체 개요

`DocumenetFragment` 노드를 사용하면 라이브 DOM 트리 외부에 경량화된 문서 DOM을 사용할 수 있다. 마치 라이브 DOM 트리처럼 동작하되, 메모리상으로만 존재하는 빈 문서 템플릿으로 자식 노드를 메모리상에서 손쉽게 조작한 후, 라이브 DOM에 추가하는 것도 가능하다.

### 8-2. createDocumentFragment()를 사용하여 DocumentFragment를 생성하기

`DocumenetFragment`를 사용하여 메모리상에서 노드 구조를 만들고 라이브 노드 구조에 삽입하면 매우 효율적이다.

일반 `element`와의 비교해서 좋은점.

- `DocumenetFragment`는 어떤 종류의 노드를 가질 수 있다.
- `DocumenetFragment`를 추가하면 노드의 내용만 추가된다.
- `DocumenetFragment`를 DOM에 추가할 때, `DocumenetFragment`는 추가되는 위치로 이전되며 생성한 메모리상에는 더 이상 존재하지 않는다.

```javascript
<script>
    var docFrag = document.createDocumentFragment();
    ["blue","pink","red","blue","green"].forEach(function(e)) {
        var li = document.createElement("li");
        li.textContent = e;
        docFrag.appendChild(li);
    }
</script>

```

### 8-3. DocumenetFragment를 라이브 DOM에 추가하기

`appendChild()`와 `insertBefore()` 노드 메서드의 인수 `DocumentFragment`를 전달하면 메서드가 호출되는 DOM 노드의 자식 노드로 옮겨진다.

```javascript
var ulElm = document.querySelecotr('ul')
var docFrag = document.createDocumentFragment();

["blue","pink","red","blue","green"].forEach(function(e)) {
    var li = document.createElement("li");
    li.textContent = e;
    docFrag.appendChild(li);
}
ulElm.appendChild(docFrag)

document.body.innerHTML // <ul><li>.... </li></ul> 출력
```

### 8-4. DocumenetFragment에서 innerHTML 사용하기

`DocumentFragment`를 생성해서 div 태그를 추가한 다음, HTML 문자열로 갱신하기 위해 innerHTML 속성을 사용하면 HTML 문자열로 부터 DOM 구조가 만들어진다.

```javascript
var divElm = document.createElement("div");
var docFrag = document.createDocumentFragment();

docFrag.appendChild(divElm);
docFrag.querySelector("div").innerHTML = "<ul><li>foo</li><li>bar</li></ul>";

// div 태그 안에 DOM 추가
document.querySelector('div').appendChild(
    docFrag.querySelector('div').firstChild();
)
```

### 8-5. 복제를 사용하여 Fragment의 노드를 메모리상으로 유지하기

노드를 추가한 이후에 Fragment의 내용을 메모리상에서 유지하려면, `cloneNode()`를 사용하여 추가할 `DocumentFragment`를 복제하면 된다.

```javascript
var ulElm = document.createElement("div");
var docFrag = document.createDocumentFragment();

ulElm.appendChild(docFrag.cloneNode(true));
```
