# 5장. Element 노드 지오메트리와 스크롤링 지오메트리

### 5-1. Element 노드 크기, 오프셋, 스크롤링 개요

노드의 시각적인 형태와 지오메트리를 프로그래밍을 통해 살펴보고 조작하기 위한 일련의 API가 존재한다.

### 5-2. offsetParent를 기준으로 element의 offsetTop 및 offsetLeft 값을 가져오기

`offsetTop`과 `offsetLeft` 속성을 이용하면 `offsetParent`로부터 `element` 노드의 오프셋 픽셀 값을 가져올 수 있다. 즉 `elemenet`의 **좌상단** 경계로부터 안쪽 **좌상단** 경계 까지의 거리를 픽셀로 제공해준다.

`offsetParent`는 가장 가까운 부모 `element`를 검색하게 된다.

```javascript
<body>
    #blue{
        height: 100px;
        width: 100px;
        border: 10px solid gray;
    }
    #red{
        height: 50px;
        width: 50px;
        border: 10px solid gray;
    }
</body>

var div = document.querySelector('#red');

div.offsetTop       // 60
div.offsetLeft;     // 60
div.offsetParent;   // <body>
```

### 5-3. getBoundingClientRect()를 사용하겨 뷰포트를 기준으로 element의 Top, Right, Bottom, Left 테두리 오프셋을 얻기

`getBoundingClientRect()`를 이용하면 뷰포트의 **좌상단 끝**을 기준으로 `elememt`의 바깥쪽 테두리 위치를 얻을 수 있다.

```javascript
<body>
    div{
        height: 50px;
        width: 50px;
        border: 10px solid gray;
    }
</body>

var divEdges = document.querySelector('div').getBoundingClientRect();

divEdges.top    // 100
divEdges.right  // 170
divEdges.bottom // 170
divEdges.left   // 100

```

### 5-4. 뷰포트에서 element의 크기(테두리 + 패딩 + 내용) 얻기

`getBoundingClientRect()`는 top, bottom, left, right 뿐 만 아니라 **height**, **width** 값도 반환한다. 이는 **테두리 + 패딩 + 내용**을 모두 더한 값이다.

```javascript
<body>
    div{
        height: 25px;
        width: 25px;
        border: 25px solid gray
    }
</body>

var div = document.querySelector('div').getBoundingClientRect();

div.height  // 125
div.width   // 125
```

`offsetHeight`와 `offsetWidht`를 이용해 쉽게 얻을 수 있다.

```javascript
var div = document.querySelector("div");
div.offsetHeight; // 125
div.offsetWidht; // 125
```

### 5-5. 뷰퐅에서 테두리를 제외한 element의 크기 (패딩 + 내용) 얻기

`clientHight`와 `clientWidht`를 이용해 **패딩 + 내용**을 얻을 수 있다.

```javascript
<body>
    div{
        height: 25px;
        width: 25px;
        border: 25px solid gray
    }
</body>

var div = document.querySelector('div')
div.clientHight     // 75 ( 테두리 제외 )
div.clientWidth     // 75 ( 테두리 제외 )
```

### 5-6. elementFromPoint()를 사용하여 뷰포트의 특정 지점에서 최상단 element 얻기

`elementFromPoint()`를 사용하여 최상단 `element`에 대한 참조를 얻을 수 있다. 즉 dom 에 접근 가능

```javascript
<body>
  <div id="bottom"></div>
  <div id="top"></div>
</body>;

console.log(document.elementFromPoint(50, 50)); // top
```

### 5-7. scrollHeight와 scrollWidth를 사용하여 스크롤될 element의 크기를 얻기

`scrollHeight`와 `scrollWidth`를 이용해 스크롤될 노드의 높이와 너비를 알 수 있다. 즉 스크롤 막대의 길이를 알 수 있다.

```javascript
<body>
    div{
        height: 100px;
        width: 100px;
        overflow: auto;
    }
    p{
        hight: 1000px;
        width: 1000px;
    }
</bidy>

var div = document.querySelector('div');

div.scrollHeight    // 1000
div.scrollWidht     // 1000
```

### 5-8. scrollTop과 scollLeft를 사용하여 top 및 left로 부터 스크롤될 픽셀을 가져오거나 설정하기

`scrollTop과`과 `scollLeft`를 이용해 스크롤의 위치를 알 수 있다. 상하 스크롤이라면 top, 좌우 스크롤이라면 left를 이용해 스크롤된 바의 위치를 알 수 있다.

### 5-9. scollIntoView()를 사용하여 element를 View로 스크롤하기

스크롤이 가능한 노드 내에 있는 노드를 선택하면 `scrollIntoView()` 메서드를 사용해 선택된 노드가 view로 스크롤되도록 할 수 있다. `scoroll spy` 기능 처럼 필요한 dom 에 스크롤이 되게 할 수 있다.
