# Javascript
> 프로토타입 기반의 객체지향 언어

### 브라우저 동작 원리
<ul>
    <li>script 요소를 만나면 웹페이지의 파싱을 잠시 중단한다.</li>
    <li>src 어트리뷰트에 정의된 자바스크립트 파일을 로드한 후 파싱하고 실행한다.</li>
    <li>중단된 웹페이지의 파싱을 계속 진행한다.</li>
</ul>
 
> body 요소의 가장 아래에 스크립트를 위치시키는 것은 좋은 아이디어이다. 그 이유는 아래와 같다.  
- HTML 요소들이 스크립트 로딩 지연으로 인해 렌더링에 지장 받는 일이 발생하지 않아 페이지 로딩 시간이 단축된다.
- DOM이 완성되지 않은 상태에서 자바스크립트가 DOM을 조작한다면 에러가 발생한다.
  
  
    async    
    웹페이지 파싱과 외부 스크립트 파일의 다운로드가 동시에 진행된다. 스크립트는 다운로드 완료 직후 실행된다. IE9 이하 버전은 지원하지 않는다.
    
    defer
    웹페이지 파싱과 외부 스크립트 파일의 다운로드가 동시에 진행된다. 스크립트는 웹페이지 파싱 완료 직후 실행된다. IE9 이하 버전에서 정상적으로 동작하지 않을 수 있다.
    
### Data Type (자료형)
> 기본 자료형(primitive data type)
    <ul>
     <li>Boolean</li>
     <li>null</li>
     <li>undefined</li>
     <li>Number</li>
     <li>String</li>
     <li>Symbole(ECMAScript 6에서 추가)</li>
    </ul>
  객체형
    <ul>
     <li>Object</li>
    </ul>
    
### 기본 자료형(Primitive Data Type)
> 기본 자료형의 값은 변경 불가능한 값이며 pss-by-value(값으로 접근) 이다. 또한 이들 값은 메모리의 스택 영역(Stack Segment)에 고정된 메모리 영역을 점유하고 저장된다.

### 객체형(Object type, 참조형)
> 객체는 데이터와 그 데이터에 관련되는 동작(절차,방법,기능)을 모두 포함할 수 있는 개념적 존재이다. 달리 말해, 이름과 값을 가지는 데이터를 의미하는 프로퍼티(property)와 동작을 의미하는 메소드(method)를 포함할 수 있는 독립적 주체이다.

> 자바스크립트는 객체(object)기반의 스크립트 언어로서 자바스크립트를 이루고 있는 거의 “모든 것”이 객체이다. 기본자료형(Primitives)을 제외한 나머지 값들(배열, 함수, 정규표현식 등)은 모두 객체이다. 또한 객체는 pass-by-reference(참조로 접근)이며 메모리의 힙 영역(Heap Segment)에 저장된다.

## 변수 호이스팅
> var 키워드로 선언된 변수는 선언 단계와 초기화 단계가 한번에 이루어진다. 즉, 스코프에 변수가 등록되고 변수는 메모리에 공간을 확보한 후 undefined로 초기화된다. 따라서 변수 선언문 이전에 변수에 접근하여도 Variable Object에 변수가 존재하기 때문에 에러가 발생하지 않는다. 다만 undefined 를 반환한다. 이러한 현상을 변수 호이스팅(Variable Hoisting)
 
> JavaScript의 변수는 다른 C-family와는 달리 block-level scope를 가지지 않고 function-level scope를 갖는다. 단, ECMAScript 6에서 도입된 let, const 키워드를 사용하면 block-level scope를 사용할 수 있다.
 
    Function-level scope
    함수내에서 선언된 변수는 함수 내에서만 유효하며 함수 외부에서는 참조할 수 없다. 즉, 함수 내부에서 선언한 변수는 지역 변수이며 함수 외부에서 선언한 변수는 모두 전역 변수이다.
<br/>
    
    Block-level scope
    코드 블럭 내에서 선언된 변수는 코드 블럭 내에서만 유효하며 코드 블럭 외부에서는 참조할 수 없다.
   
## Scope (유효범위)
> 변수에서의 접근성과 생존기간(life-cycle)을 의미한다. 달리 말하자면 변수가 가지고 있는 참조 범위를 의미한다.

    전역 Scope (Global scope)
    - 코드 어디에서든지 참조할 수 있다.
<br/>
    
    지역 Scope (Local scope or Function-level scope)
    정의된 함수 내에서만 참조할 수 있다.
    
> 모든 변수는 Scope 를 갖는다
    
    젼역 변수 (Global variable)
    전역 Scope 를 갖는 변수
<br/>

    지역 변수 (Local variable)
    지역 Scope 를 갖는 변수
    
> 변수는 선언위치(전역 또는 지역)에 의해 Scope 를 가지게 된다. 즉, 전역에서 선언된 변수는 전역 Scope를 갖는 전역 변수이고, 지역(자바스크립트의 경우 함수 내부)에서 선언된 변수는 지역 Scope 를 갖는 지역 변수가 된다.
<br/><br/>
전역 Scope 를 갖는 전역 변수는 전역에서 참조할 수 있다. 지역(함수 내부)에서 선언된 지역 변수는 그 지역과 그지역의 하부 지역에서만 참조할 수 있다.

    var x = 10;
    
    function foo(){
      var x = 100;
      console.log(x);   //  100
    
      function bar(){   // 내부함수
        x = 1000;
        console.log(x); // 1000
      }
    
      bar();
    }
    foo();
    console.log(x); // 10
    
> 중첩 scope는 가장 인접한 지역을 우선하여 참조한다.
    
### Lexical scoping (Static scoping)
> 자바스크립트는 함수가 선언된 시점에서의 유효범위를 갖는다. 예제의 함수 bar가 어떤 상황에서 호출될 지 선언 시점에서는 알 수 없다.

    var i = 5;
    
    function foo() {
      var i = 10;
      bar();
    }
    
    function bar() { // 선언된 시점에서의 scope를 갖는다!
      console.log(i);
    }
    
    foo(); // 5
    
> [전역변수를 반드시 사용하여야 할 이유를 찾지 못한다면 지역변수를 사용하여야 한다. 변수의 범위인 스코프는 좁을수록 좋다.]

### 최소한의 전역변수 사용
> 전역변수 사용을 최소화하는 방법 중 하나는 애플리케이션에서 전역변수 사용을 위해 다음과 같이 전역변수 객체 하나를 만들어 사용하는 것이다. (더글라스 크락포드의 제안)

    var MYAPP = {};
    
    MYAPP.student = {
      name: 'Lee',
      gender: 'male'
    };
    
    console.log(MYAPP.student.name);

### 즉시실행함수를 이용한 전역변수 사용 억제
> 전역변수 사용을 억제하기 위해, 즉시 실행 함수(IIFE, Immediately-Invoked Function Expression)를 사용할 수 있다. 이 방법을 사용하면 전역변수를 만들지 않으므로 라이브러리 등에 자주 사용된다. 즉시 실행 함수는 즉시 실행되고 그 후 전역에서 바로 사라진다.

    (function () {
      var MYAPP = {};
    
      MYAPP.student = {
        name: 'Lee',
        gender: 'male'
      };
    
      console.log(MYAPP.student.name);  //  Lee
    }());
    
    console.log(MYAPP.student.name);  //  ReferenceError: MYAPP is nor defined

## this
> 자바스크립트의 함수는 호출될 때, 매개변수로 전달되는 인자값 이외에, arguments 객체와 this를 암묵적으로 전달 받는다.

    function square(number) {
    
      console.log(arguments);
      console.log(this);
    
      return number * number;
    }
    
    var result = square();
    
> 자바스크립트의 경우 함수 호출 패턴에 따라 어떤 객체를 this에 바인딩할 지가 결정된다. 즉 함수 호출 패턴에 따라 this의 참조값이 달라진다.

> 함수 호출 패턴
<br/><br/>1. 함수 호출 패턴<br/>2. 메소드 호출 패턴<br/>3. 생성자 호출 패턴<br/>4. apply 호출 패턴

### 1. 함수 호출 패턴
> 전역객체(Global Object)는 모든 객체의 유일한 최상위 객체를 의미하며 일반적으로 Browser-side에서는 window, Server-side(Node.js)에서는 global 객체를 의미한다.

    // in browser console
    this === window // true
    
    // in Terminal
    node
    this === global // true

> 기본적으로 this 는 전역객체(Global object)에 바인딩된다. 전역함수는 물론이고 심지어 내부함수의 경우도 this는 외부함수가 아닌 전역객체에 바인딩된다.
    
    function foo() {
      console.log("foo's this: ",  this);  // window
      function bar() {
        console.log("bar's this: ", this); // window
      }
      bar();
    }
    foo();
    
> 또한 메소드의 내부함수일 경우에도 this 는 전역객체에 바인딩된다.
    
    var value = 1;
    
    var obj = {
      value: 100,
      foo: function() {
        console.log("foo's this: ",  this);  // obj
        console.log("foo's this.value: ",  this.value); // 100
        function bar() {
          console.log("bar's this: ",  this); // window
          console.log("bar's this.value: ", this.value); // 1
        }
        bar();
      }
    };
    
    obj.foo();
    
> 콜백함수의 경우에도 this는 전역객체에 바인딩된다.
  
    var value = 1;
    
    var obj = {
      value: 100,
      foo: function() {
        setTimeout(function() {
          console.log("callback's this: ",  this);  // window
          console.log("callback's this.value: ",  this.value); // 1
        }, 100);
      }
    };
    
    obj.foo();
    
> 더글라스 크락포드는 “이것은 설계 단계의 결함으로 메소드가 내부함수를 사용하여 자신의 작업을 돕게 할 수 없다는 것을 의미한다” 라고 말한다. 내부함수의 this가 전역객체를 참조하는 것을 회피방법은 아래와 같다.

    var value = 1;
    
    var obj = {
      value: 100,
      foo: function() {
        var that = this;  // Workaround : this === obj
    
        console.log("foo's this: ",  this);  // obj
        console.log("foo's this.value: ",  this.value); // 100
        function bar() {
          console.log("bar's this: ",  this); // window
          console.log("bar's this.value: ", this.value); // 1
    
          console.log("bar's that: ",  that); // obj
          console.log("bar's that.value: ", that.value); // 100
        }
        bar();
      }
    };
    
    obj.foo();
    
<img src="http://poiemaweb.com/img/Function_Invocation_Pattern.png">    

## 연산자 (Operator)
### 삼항연산자 (Ternary Operator)
    
    // 삼항연산자(ternary operator)
    // 조건 ? 조건이 ture일때 반환할 값 : 조건이 false일때 반환할 값
    var condition = true;
    var result = condition ? 'true' : 'false';
    console.log(result); // 'true'
    
### 타입연산자 (Type Operator)

    typeof 피연산자의 데이터 타입(자료형)을 문자열로 반환한다. nill과 배열의 경우 object, 함수의 경우 function를 반환하는 것에 유의하여야 한다.
    instanceof 객체가 동일 객체형의 인스턴스이면 true를 반환한다.
    
    console.log(typeof 'John');                 // string
    console.log(typeof 3.14);                   // number
    console.log(typeof NaN);                    // number
    console.log(typeof false);                  // boolean
    console.log(typeof [1, 2, 3, 4]);           // object
    console.log(typeof {name:'John', age:34});  // object
    console.log(typeof new Date());             // object
    console.log(typeof function () {});         // function
    console.log(typeof myCar);                  // undefined (설계적 결함)
    console.log(typeof null);                   // object (설계적 결함)
    
    function Person() {}
    var me = new Person();
    console.log(me instanceof Person); // true
    
### !!
> !! 의 역할은 피연사자를 불린값으로 변환하는 것이다.

    console.log(!!1);         // true
    console.log(!!0);         // false
    console.log(!!'string');  // true
    console.log(!!'');        // false
    console.log(!!null);      // false
    console.log(!!undefined); // false
    console.log(!!{});        // true
    console.log(!![]);        // true
    
> 객체(배열 포함)의 경우 빈 객체라도 존재하기만하면 true로 변환된다.
  
> 객체의 존재 확인 후 그 결과를 반환해야 하는 경우, !!를 사용하면 강제로 피연산자를 boolean으로 형 변환 할 수 있다.
    
    var obj;
    console.log(!!obj); // false
    
    obj = {};
    console.log(!!obj); // true
    

> 아래 값들은 Boolean context에서 false로 평가된다.<ul><li>false</li><li>undefined</li><li>null</li><li>0</li><li>NaN (Not a Number)</li><li>'' (빈문자열)</li></ul>
이들을 Falsy value라 한다.  

## 객체(Object)란?
> 객체는 데이터와 그 데이터에 관련되는 동작(절차, 방법, 기능)을 모두 포함할 수 있는 개념적 존재이다. 달리 말해, 이름(키)과 값으로 구성된 데이터를 의미하는 프로퍼티(property)와 동작을 나타내는 메소드(method)를 포함하고 있는 독립적 주체이다.

### 프로퍼티(Property)
> 객체는 이름(name)과 값(value)의 쌍인 프로퍼티들을 포함하는 컨테이너라고 할 수 있다.<ul><li>프로퍼티 이름 : 빈 문자열을 포함하는 문자열과 숫자</li><li>프로퍼티 값 : undefined을 제외한 모든 값</li></ul> 

### 메소드(Method)
> 메소드는 객체에 제한되어 있는 함수를 의미한다. 즉 프로퍼티 값이 함수일 경우, 일반 함수와 구분하기 위해 메소드라 칭한다.

