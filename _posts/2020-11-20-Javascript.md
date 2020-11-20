---
layout: article
title: JavaScript
tags: TeXt
aside:
  toc: true
---
# 기본 문법
- 표현식
- 키워드
- 식별자
    - 함수
    - 속성
    - 변수
    - 메서드
- 주석


## 출력
```javascript
alert('Hello JavaScript);
```

- 큰 따옴표와 작은 따옴표를 써서 문자열을 만듬


## 이스케이프 문자
- \t
- \n
- \’
- \”
- \\


## 변수
- 변수를 선언
- 변수에 값을 할당


    var <식별자>


- 자바 스크립트는 기존에 존재하는 변수를 재선언할 수 있습니다
- 이러한 특성으로 인해 실수를 할 수 있음


## typeof
- 자바스크립트는 숫자, 문자열, 불 같은 자료형을 확인할 때 typeof 연산자를 사용

```javascript
<script>
  alert(typeof ('string'));
  alert(typeof (273));
</script>
```

## 자료형
- 문자열
- 숫자
- 불
- 함수
- 객체
- undefined


## undefined
- 선언하지 않은 변수 또는 변수를 선언했지만 초기화하지 않았을 때 해당 변수의 자료형은 undefined


## 형변환
    Number(input);
    String(input);
    Boolean(input);
    -> undefined 자료형은 false


## 일치연산자
- ===  : 양쪽 변의 자료형과 값이 일치합니다
- !== : 양쪽 변의 자료형과 값이 다릅니다


## 템플릿 문자열
    <script>
      alert('표현식 273 + 52의 값은 ${52 + 273}입니다...!');
    </script>



## let과 const
| 키워드   | 구분 | 선언 위치  | 재선언 |
| ----- | -- | ------ | --- |
| var   | 변수 | 전역 스코프 | 가능  |
| let   | 변수 | 해당 스코프 | 불가능 |
| const | 상수 | 해당 스코프 | 불가능 |

- let 키워드는 자원을 적절하게 이용할 수 있게 특정 스코프 내부에서만 변수를 사용할 수 있게 합니다.



## for in 반복문
```javascript
    for(var i in array) {
      alert(array[i]);
    }
    
    for(const element of [1, 2, 3, 4]) {
      alert('요소는 ${element}입니다.');
    }
```

- for in 반복문은 반복 인덱스가 들어감
- for of 반복문은 요소가 순서대로 들어감
----------
# 함수
## 익명 함수
```javascript
    var 함수 = function() {};
    
    <!-- <script>
      var func = function() {
        var output = prompt();
        alert(output);
        };
      alert(func);
    </script>; -->
```

## 선언적 함수
- 함수는 선언적 함수부터 읽음
- 선언적 함수와 익명 함수가 있으면 선언적 함수를 먼저 읽고 그다음 익명 함수를 읽기 때문에
- 재정의가 되었을 때 익명함수가 덮어쓰게 됨


## 내부 함수
    function 외부함수() {
      function 내부함수() {
      }
    
      function 내부함수() {
      }
      <function code>
    }


## 콜백 함수
- 자바스크립트에서는 함수도 하나의 자료형이므로 매개변수로 전달 가능
- 이렇게 매개변수로 전달하는 함수를 콜백 함수라고 함
```javascript
    function callTenTimes(callback) {
      for(var i = 0; i < 10; i++) {
        callback();
      }
    }
    
    var callback = function () {
      alert('ㅎㅅ ㅎㅊ');
    };
    
    callTenTimes(callback);


- 익명 콜백 함수
    function callTenTimes(callback) {
      for(var i = 0; i < 10; i++) {
        callback();
      }
    }
    
    callTenTimes(function () {
      alert('ㅎㅅ ㅎㅊ');
    });
```


## 함수를 리턴 하는 함수
```javascript
    function returnFunction() {
      return function () {
        alert('hello function .. !');
      };
    }
    
    returnFunction()();
```

## 클로저
```javascript
    function test(name) {
      var output = 'hello ' + name + ' ..!';
      return function () {
        alert(output);
      };
    }
    
    test('JavaScript')();
```
- 클로저의 정의는 워낙 다양합니다
- 이렇게 지역 변수를 남겨두는 현상을 클로저라고 부르기도 하고, 함수 test() 내부의 변수들이 살아있는 것이므로 test() 함수로 생성된 공간을 클로저라고 부르기도 합니다.
- 또한 리턴된 함수 자체를 클로저라고 부르기도 하며, 살아남은 지역 변수 output을 클로저라고 부르기도 합니다.
- 추가로 지역 변수 output을 남겨둔다고 외부에서 마음대로 사용할 수 있는 것은 아닙니다.
- 반드시 리턴된 클로저 함수를 사용해야 지역 변수 output을 사용할 수 있습니다.
- 클로저 함수로 인해 남은 지역변수는 클로저 함수 각각의 고유한 변수입니다.



## 내장 함수
- setTimeout(function, millsecond)

: 일정 시간 후 함수를 한 번 실행합니다


- setInterval(function, millsecond)

: 일정 시간마다 함수를 반복해서 실행합니다


- clearTimeout(id), clearInterval(id)


- eval(String) : 문자열을 코드로 실행하는 함수

→ 클로저를 이용한 콜백 함수 실행 시간 조절

```javascript
    for(var i = 0; i < 3; i++) {
      (function (closed_i) {
        setTimeout(function () {
          alert(closed_i);
        } ,0);
      })(i);
    }
```

## 짧은 조건문을 활용한 기본 매개 변수
```javascript
    <script>
      function test(a, b, c) {
        b = b || 52;
        c = c || 273;
        
        alert(a + ':' + b + ':' + c);
    }
    
    test(1, 2);
    }
```

## 화살표 함수
```javascript
    function() {}  ==  () => {}
    
    const multiply = (a, b) => a * b;
    
    alert(multiply(1, 2));
    alert(multiply(3, 4));
```

----------
# 객체
```javascript
    <script>
      var product = {
        제품명 : 'asf',
        유형 : 'ejkasdf',
        원산지 : 'fda'
      };
    </script>
```

- product.제품명
- product[‘제품명’]
- 둘 다 가능


- 객체의 키는 식별자 또는 문자열을 모두 사용할 수 있습니다
- 대부분 개발자가 식별자를 키로 사용하지만, 식별자로 사용할 수 없는 단어를 키로 사용할 때는 문자열을 사용
- 식별자가 아닌 문자열을 키로 사용했을 경우 무조건 대괄호를 사용해야 객체의 요소에 접근할 수 있습니다.


## 속성과 메소드
- 배열 내부에 있는 값을 요소라고 합니다.
- 반면 객체 내부에 있는 값은 속성이라고 합니다
    var object = {
      number : 273,
      string : 'RintIanTta',
      boolean : true,
      array : [52. 273. 103, 32],
      method : function () {}
    };
- 객체의 속성 중 함수 자료형인 속성을 특별히 메서드라고 부릅니다
- 메서드 내에서 자기 자신이 가진 속성을 출력하고 싶을 때는 자신이 가진 속성임을 분명하게 표시해야 합니다.

→ this를 사용해야 함


## 객체와 반복문
- 배열은 단순 for 반목문과 for in 반복문으로 요소에 쉽게 접근할 수 있습니다.
- 하지만 객체는 단순 for 반복문으로 객체의 속성을 살펴보는 것이 불가능합니다
- 객체의 속성을 모두 살펴보려면 for in 반복문을 사용해야 합니다
```javascript
    var product = {
      name : 'microsofr visual studio',
      price : '15000',
      language : '한국어',
      supportOS : 'Win 32/64',
      subscription : true
    };
    
    var output = "";
    
    for(var key in product) {
      output += 'key' + ': ' + product[key] + '\n';
    }
    alert(output);
```

## in 키워드
    ('이름' in student)


- student 객체에 이름 속성이 존재한다면 true, 아니라면 false


## with 키워드
- 복잡하게 사용해야 하는 코드를 짧게 줄여주는 키워드
- 중복되는 식별자 student를 여러번 사용하는 것을 막아준다
    with<객체> {
      <코드>
    }


## 객체의 속성 추가와 제거
- 처음 객체를 생성하는 시점 이후에 속성을 추가하거나 제거하는 것을 동적으로 속성을 추가한다고 표현


- 추가
```javascript
    var student = {};
    
    student.name = 'tom';
    student.hobby = 'music';
    student.dream = 'singer';
    
    student.toString = function () {
      var output = '';
      for(var key in this) {
        if(key != 'toString') {
          output += key + '\t' + this[key] + '\n';
        }
      }
      return output;
    };
    
    alert(student.toString());
```

- 제거
    delete(student.dream);
    delete(Student.name);
    
    alert(student.toString());


## 객체와 배열을 사용한 데이터 관리
```javascript
    for(var i in students) {
      students[i].getSum = function () {
        return this.국어 + this.수학 + this.영어 + this.과학;
      };
      
      students[i].getAverage = function () {
        this.getSum() / 4;
      };
    }
    
    var output = '이름\t총점\t평균\n';
    for(var i in students) {
      with(students[i]) {
        output += .....;
      }
    }
```

## 함수를 사용한 객체 생성
- 앞에서는 배열 안에 객체를 하나씩 직접 만들어서 넣었습니다
- 이 경우, 서로 다른 형태의 객체를 배열 안에 넣을 수 있다는 장점이 있음
- 근데 귀찮아, 객체를 만드는 틀을 만들자

```javascript
    function makeStudent(name, korean, math, english, science) {
      var willReturn = {
        ...
        getSum: function () {};
        getAverage: function () {};
        toString : function () {};
      };
      return willReturn;
    }


    var students = [];
    students.push(makeStudents(.....));
    students.push(makeStudents(.....));
    
    var output = '';
    for(var i in students) {
      output += students[i].toString() + '\n';
    }
    alert(output);
```

- 하지만 이런거 안써
- 생성자 함수를 사용한다…. 그럼 왜 나온거야 짜증나게


## 옵션 객체
- 함수의 매개변수로 전달하는 객체를 일반적으로 옵션 객체라고 함
- 옵션이라는 말은 입력해도 되고, 입력하지 않아도 된다는 의미
- 기본 매개변수처럼 값을 입력하지 않으면 초기화 하는 과정이 필요
    function test(options) {
      options.valueA = options.valueA || 10;
      options.valueB = options.valueB || 20;
      options.valueC = options.valueC || 30;
      
      alert(options.valueA  ...);


## 깊은 복사
```javascript
    function clone(obj) {
      var output = {};
      for(var i in obj) {
        output[i] = obj[i];
      }
      return output;
    }
```

----------
# 생성자 함수
- 객체를 생성할 때 사용 되는 함수
```javascript
    function Student(name, korean, math, english, science) {
      this.name = name;
      this.korean = korean;
      this.math = math;
      this.english = englisth;
      this.science = science;
    
      this.getSum = function () {};
      this.getAverage = function () {};
      this.toString = function () {};
    }
```

## 프로토 타입
- 객체의 속성들은 모두 다른 값을 가지지만, 메서드는 모두 같은 값을 가진다
- 프로토타입은 생성자 함수로 생성된 객체가 공통으로 가지는 공간


```javascript
    function Student(name, korean, math, english, science) {
      this.name = name;
      this.korean = korean;
      this.math = math;
      this.english = englisth;
      this.science = science;
    }
    
    Student.prototype.getsum = function () {};
    Student.prototype.getAverage = function () {};
    Student.prototype.toString = function () {};
```

----------

 

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

