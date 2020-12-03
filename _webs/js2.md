---
layout: article
title: JavaScript(2)

mode: immersive
header:
  theme: dark
article_header:
  type: overlay
  theme: dark
  background_color: '#203028'
  background_image:
    src: /assets/cover2.jpg
    gradient: 'linear-gradient(135deg, rgba(34, 139, 87 , .4), rgba(139, 34, 139, .4))'
aside:
  toc: true
---

# 브라우저 객체 모델
- 브라우저 객체 모델은 웹 브라우저와 관련된 객체의 집합을 의미합니다
- 대표적인 브라우저 객체 모델로는 window, location, navigator, history, document, screen이 있습니다


## window 객체
- 자바스크립트의 브라우저 기반 최상위 객체
    window.open();
    window.open('http://hanbit.co.kr', 'child', 'width=600, height=300', true);


- open() 메서드는 새로운 window 객체를 생성하는 메서드
- 단지 팝업창을 여는 것에서 그치지 않고 윈도우 객체를 리턴함
    var child = winodw.open('','', 'width=300, height=200');
    child.document.write('<h1>From Parent Window</h1>');


## screen 객체
- screen 객체는 웹 브라우저의 화면이 아니라 운영체제 화면의 속성을 갖는 객체입니다


- 브라우저의 크기를 화면에 일치시키기
    var child = window.open('', '', 'width = 300, height = 200');
    var width = screen.width;
    var height = screen.height;
    
    child.moveTo(0, 0);
    child.resizeTo(width, height);
    setInterval(function () {
      child.resizeBy(-20, 20);
      child.moveBy(10, 10);
      }, 1000);


## location 객체
- location 객체는 웹 브라우저의 주소 표시줄과 관련된 객체입니다
- 프로토콜의 종류, 호스트 이름, 문서 위치 등의 정보가 있습니다


- 페이지를 이동할 때 많이 사용합니다
    location = 'http://hanbit.co.kr';
    location.href = 'http://hanbit.co.kr';
    
    location.assign('http://hanbit.co.kr');
    location.replace('http://hanbit.co.kr');


- 페이지 새로고침
    location = location;
    location = location.href;
    
    location.assign(location);
    location.replace(location);
    location.reload();


## navigator 객체
- navigator 객체는 웹 페이지를 실행하고 있는 브라우저에 대한 정보가 있습니다.


## window 객체의 onload 이벤트 속성
    <script>
      window.onload = function() {
      }
    </script>


- 문서 객체의 속성 중 ‘on’으로 시작하는 속성을 이벤트 속성이라고 부르며, 이 이벤트 속성은 함수를 할당해야 합니다.
- html 페이지에 존재하는 모든 태그가 화면에 올라가는 순간이 로드가 완료되는 순간입니다.



----------
# 문서 객체 모델(DOM)
- 태그, 문서 객체, 노드
- html 페이지에 존재하는 html이나, body 태그를 ‘태그’라고 부릅니다
- 이 태그를 자바스크립트에서 이용할 수 있는 개체로 만들면 그것이 문서 객체
    <script>
      window.onload = function () {
        var header = document.getElementById('header');
        };
    </script>
- 이 때 header 객체를 ‘문서 객체’라고 부릅니다.
- html 페이지를 트리 모양으로 나타 냈을 때 각 요소를 ‘노드’라고 부릅니다.


- 요소 노드, 텍스트 노드
    <!DOCTYPE html>
    <html>
    <head>
      <title>INDEX</title>
    </head>
    <body>
      <h1>Text Node</h1>
      <img src="image.jpg" />
    </body>
    </html>
- 요소 노드란 바로 html 태그를 의미하고
- 텍스트 노드는 요소 노드 안에 들어 있는 글자를 의미합니다.


## 문서 객체 생성


- 웹페이지가 처음 html 페이지에 적혀 있는 태그들을 읽으며 생성하는 것을 “정적으로 문서 객체를 생성한다”라고 표현
- 자바스크립트로 원래 html 페이지에는 없던 문서 객체를 생성하는 것을 “동적으로 문서 객체를 생성한다”라고 표현


- 요소 노드와 텍스트 노드를 만들어서 텍스트 노드를 요소 노드에 붙여준다

```javascript
    window.onload = function () {
      var header = document.createElement('h1');
      var textNode = document.createTextNode('Hello DOM');
    
      header.appendChild(textNode);
      document.body.appendChild(header);
    };
```

- 텍스트 노드를 갖지 않는 노드를 생성하는 방법
```javascript
    window.onload = function () {
      var img = document.createElement('img');
      img.src = 'Penguins.jpg';
      img.width = 500;
      img.height = 350;
     
      document.body.appendChild(img);
    };
```

- 다른 방법
```javascript
    window.onload = function () {
      var img = document.createElement('img');
      img.setAttribute('src', 'Penguins.jpg');
      img.setAttribute('width', 500);
      img.setAttribute('height', 350);
    
      img.setAttribute('data-property', 350);
      
      document.body.appendChild(img);
    };
```


- 지금까지 문서 객체를 생성하는 방법은 노드를 만들고 연결하는 방법
- 이 방법도 굉장히 쉽지만 일반적으로 더 쉬운 방법 사용
- innerHTML 속성을 사용하는 것


- 문서객체의 innerHTML 속성은 태그의 내부를 의미하는 속성
- 문자열을 선언하고 body 문서 객체의 innerHTML 속성에 넣기만 하면 문서 객체를 생성해 줍니다

```javascript
    window.onload = function () {
      var output = '';
      output +='<ul>';
      output +=    '<li>JavaScript</li>'
      output +=    '<li>JQuery</li>'
      output +=    '<li>Ajax</li>'
      output +='</ul>';
      // innerHTML 속성에 문자열을 할당합니다
      document.body.innerHTML = output;
    
      doucument.body.innerHTML += '<h1>Document Object Model</h1>';
    };
```

## 문서 객체 가져오기
- 웹 페이지에 이미 존재하는 HTML 태그를 자바스크립트로 가져오는 방법을 알아보자
- document 객체가 갖는 표 10-4의 메서드를 사용하면 이미 웹페이지에 존재하는 문서 객체를 가져올 수 있음

```javascript
- getElementById(id)
    <body>
      <h1 id="header-1">Header</h1>
      <h1 id="header-2">Header</h1>
    </body>
```

- document 객체의 getElementById() 메서드는 id 속성을 갖는 태그만 가져올 수 있음
```javascript
    window.onload = function () {
      var header1 = document.getElementById('header-1');
      var header2 = document.getElementById('header-2');
    };
```


- header1과 header2는 문서 객체이므로 점을 찍으면 문서 객체의 속성과 메서드를 살펴볼 수 있음.
```javascript
    window.onload = function () {
      var header1 = document.getElementById('header-1');
      var header2 = document.getElementById('header-2');
      
      //문서 객체의 속성을 변경합니다
      header1.innerHTML = 'with getElementById()';
      header2.innerHTML = 'with getElementById()';
    };
```

- document 객체의 getElementById() 메서드는 한 번에 한 가지 문서 객체만 가져올 수 있습니다.
- 반면 getElementsByName(name), getElementsByTagName(tagName)을 사용하면 한번에 여러 개의 문서 객체를 가져 올 수 있습니다.
    window.onload = function() {
      var headers = document.getElementsByTagName('h1');
    };


- headers는 문서 객체를 갖는 배열이며, HTML 페이지의 h1 태그가 순서대로 들어갑니다.
    headers[0].innerHTML = 'with getElementsByTagName()';
    headers[1].innerHTML = 'with getElementsByTagName()';
- headers는 배열이므로 반복문을 사용할 수 있습니다. 주의 할 점은 for in 반복문을 사용해서는 안된다는 점 입니다
    for(var i = 0; i < headers.length; i++) {
      headrs[i].innerHTML = 'with getElementsByTagName()';
    }
- for in 반복문을 사용하면 문서 객체 이외의 속성에도 접근하기 때문입니다.


- querySelector(선택자) : 선택자로 가장 처음 선택되는 문서 객체를 가져옵니다
- querySelectorAll(선택자) : 선택자를 통해 선택되는 문서 객체를 배열로 가져옵니다
- 이는 css 선택자로 문서 객체를 선택하는 메서드입니다
    window.onload = function () {
      var header1 = document.querySelector('#header-1');
      var header2 = document.querySelector('#header-2');
    };


## 문서 객체의 스타일 조작
- 문서 객체의 style 속성을 사용하면 해당 문서 객체의 스타일을 변경할 수 있습니다.
```javascript
    window.onload = function () {
      var header = document.getElementById('header');
      
      header.style.border = '2px solid black';
      header.style.color = 'orange';
      header.style.fontFamiy = 'helvetica';
```

- 자바스크립트는  특수기호 - 를 식별자로 사용할 수 없으므로 header.style.background-color = ‘red’ 라고 하면 에러


## 문서 객체 제거
- 문서 객체를 제거할 때는 문서 객체가 가지는 제거 메서드를 사용합니다
- removeChild(child) : 문서 객체의 자식 노드를 제거합니다
```javascript
    window.onload = function () {
      var willRemove = document.getElementById('will-remove');
    
      document.body.removeChild(willRemove);
    };
    
    willRemove.parnetNode.remoeChild(willRemove);
```

----------
# 이벤트
- 이벤트는 키보드를 이용해 버튼을 입력하거나 마우스 클릭과 같이 다른 것에 영향을 미치는 것을 의미합니다.
- 이벤트는 애플리케이션 사용자가 발생시킬 수도 있고 애플리케이션이 스스로 발생시킬 수도 있습니다
    window.onload = function () {};

→ 이렇게 window 객체의 onload 속성에 함수 자료형을 할당하는 것을 “이벤트에 연결한다”고 합니다.

- 이 때 load를 이벤트 이름 또는 이벤트 타입이라고 하며 onload를 이벤트 속성이라고 합니다
- 또한 이벤트 속성에 할당한 함수를 이벤트 리스너 또는 이벤트 핸들러라고 합니다.
```javascript
    window.onload = function() {
      var header = document.getElementById('header');
    
      function whenClick() { alert('CLICK'); }
      header.onclick = whenClick;
    };
```
- header 객체의 이벤트 이름은 click
- 이벤트 속성은 onclick
- 이벤트 리스너는 whenClick() 함수


- 문서 객체에 이벤트를 연결하는 방법을 이벤트 모델이라고 합니다. 이벤트 모델은 다음과 같이 DOM Level 단계에 따라 두 가지로 분류할 수 있고, 다시 두 가지로 각각 나뉩니다.
- 따라서 총 네 가지 방법으로 이벤트를 연결 할 수 있습니다.


## 고전 이벤트 모델
- 고전 이벤트 모델은 자바스크립트에서 문서 객체의 이벤트 속성으로 이벤트를 연결하는 방법입니다.
- 이름은 고전이지만 현대에도 많이 사용합니다.
```javascript
    window.onload = function () {
      var header = document.getElementById('header');
      
      header.onclick = function () {
        alert('click');
      };
    };
```
- getElementById로 문서 객체를 가져 와서 거기에 이벤트를 연결
- 코드를 실행하고 h1 태그를 클릭하면 이벤트가 발생하고 경고창이 출력
- 이벤트 리스너를 제거할 때는 문서 객체의 이벤트 속성에 null을 넣어줍니다.
- 이벤트 리스너가 한 번 실행된 이후에 이벤트를 제거하므로, 두 번째 클릭부터는 이벤트가 발생하지 않습니다.

```javascript
    window.onload = function () {
      var header = document.getElementById('header');
      
      header.onclick = function () {
        alert('click');
    
      header.onclick = null;
      };
    };
```
- 고전 이벤트 모델은 이벤트 하나에 이벤트 리스너 하나만 연결할 수 있습니다.


## 이벤트 발생 객체와 이벤트 객체
- 이벤트 객체를 사용하면 누가, 언제, 어디서, 무엇을, 어떻게, 왜 를 정의할 수 있습니다.


- 누가?
- 이벤트 리스너 안에서 this 키워드를 사용하면 이벤트가 발생한 객체를 찾을 수 있습니다
```javascript
    window.onload = function() {
      document.getElementById('header').onclick = function () {
        alert(this);
      };
    };
```

→ object HTMLHeadingElement가 출력이 된다
```javascript
    window.onload = function () {
      document.getElementById('header').onclick = function () {
        this.style.color = 'orange';
        this.style.backgroundColor = 'red';
      };
    };
```
- header라는 아이디를 가진 태그의 값이 변경됨


## 인라인 이벤트 모델
- 인라인 이벤트 모델은 html 페이지의 가장 기본적인 이벤트 연결 방법입니다.
```javascript
    <body>
      <h1 onclick="">Click</h1>
    </body>
```
- 모든 태그의 이벤트 속성에는 자바스크립트 코드를 적어줍니다
- 다음 코드처럼 적으면 h1 태그를 클릭할 때 onclick 속성의 자바스크립트 코드를 실행합니다
```javascript
    <body>
      <h1 onclick="alert('click')">Click</h1>
    </body>


    <body>
      <h1 onclick="var alpha=10; alert(alpha);">Click</h1>
    </body>
```
- 하지만 이렇게 이벤트 속성에 여러 줄의 코드를 작성하면 굉장히 지저분해집니다.
- 따라서 HTML 태그의 이벤트 속성 안에 코드를 모두 쓰기보다는 함수를 script 태그 안에 만들고 이를 호출하는 방식을 더 많이 사용합니다.
```javascript
    <script>
      function whenClick(e) {
        alert('click');
      }
    </script>
    
    <body>
      <h1 onclick="whenClick(event)">Click</h1>
    </body>
```
- h1 태그가 가지는 이벤트 속성에서 이벤트를 호출할 때 매개변수를 넣었습니다. 이것이 이벤트 객체를 전달하는 방법입니다. 이벤트 객체는 고전 이벤트 모델과 마찬가지의 방법으로 사용할 수 있습니다.
## 디폴트 이벤트 제거
    document.getElementById('my-form').onsubmit = function () {
      return false;
    };
- submit 버튼을 눌러도 제출되지 않는다


## 이벤트 전달
```javascript
    <div onclick="alert('outer-div')">
      <div onclick="alert('inner-div')">
        <h1 onclick="alert('header')">
          <p onclick="alert('paragraph')">Paragraph</p>
        </h1>
      </div>
    </div>
```
- 마우스로 p 태그를 클릭할 때 마우스 커서의 좌표에 네 개의 태그가 있으므로 네 개의 태그에서 동시에 이벤트가 발생합니다.
- 이와 같이 어떠한 이벤트가 먼저 발생해 어떤 순서로 발생하는지를 이벤트 전달이라고 합니다.
- 일반적으로 자바스크립트의 이벤트 전달 순서는 이벤트 버블링 방식을 따릅니다
- 이벤트 버블링은 자식 노드에서 부모 노드 순으로 이벤트를 실행하는 것을 의미합니다.
- 반대는 이벤트 캡쳐링으로 부모 노드에서 자식 노드 순으로 실행합니다.


## 표준 이벤트 모델
- 표준 이벤트 모델은 웹 표준을 만드는 단체인 w3c에서 공식적으로 지정한 dom level 2 이벤트 모델입니다.
- 인터넷 익스플로러 이벤트 모델과 마찬가지로 한 번에 여러 가지의 이벤트 리스너를 추가할 수 있습니다.

- addEventListener(eventName, handler, useCapture)
- removeEventListener(eventName, handler)
```javascript
    window.onload = function () {
      var header = document.getElementById('my-header');
    
      header.addEventListener('click', function () {
        this.innerHTML += '+';
      });
    };
```