---
layout: article
title: JavaScript(1)

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