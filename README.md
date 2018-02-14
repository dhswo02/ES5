# Javascript
> 프로토타입 기반의 객체지향 언어

## 브라우저 동작 원리
<ul>
    <li>script 요소를 만나면 웹페이지의 파싱을 잠시 중단한다.</li>
    <li>src 어트리뷰트에 정의된 자바스크립트 파일을 로드한 후 파싱하고 실행한다.</li>
    <li>중단된 웹페이지의 파싱을 계속 진행한다.</li>
</ul>
 
 body 요소의 가장 아래에 스크립트를 위치시키는 것은 좋은 아이디어이다. 그 이유는 아래와 같다.  
- HTML 요소들이 스크립트 로딩 지연으로 인해 렌더링에 지장 받는 일이 발생하지 않아 페이지 로딩 시간이 단축된다.
- DOM이 완성되지 않은 상태에서 자바스크립트가 DOM을 조작한다면 에러가 발생한다.
  
  
    async    
    웹페이지 파싱과 외부 스크립트 파일의 다운로드가 동시에 진행된다. 스크립트는 다운로드 완료 직후 실행된다. IE9 이하 버전은 지원하지 않는다.
    
    defer
    웹페이지 파싱과 외부 스크립트 파일의 다운로드가 동시에 진행된다. 스크립트는 웹페이지 파싱 완료 직후 실행된다. IE9 이하 버전에서 정상적으로 동작하지 않을 수 있다.
    
## Data Type (자료형)
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
*기본 자료형의 값은 변경 불가능한 값이며 pss-by-value(값으로 접근) 이다. 또한 이들 값은 메모리의 스택 영역(Stack Segment)에 고정된 메모리 영역을 점유하고 저장된다.*

### 객체형(Object type, 참조형)
*객체는 데이터와 그 데이터에 관련되는 동작(절차,방법,기능)을 모두 포함할 수 있는 개념적 존재이다. 달리 말해, 이름과 값을 가지는 데이터를 의미하는 프로퍼티(property)와 동작을 의미하는 메소드(method)를 포함할 수 있는 독립적 주체이다.*

*자바스크립트는 객체(object)기반의 스크립트 언어로서 자바스크립트를 이루고 있는 거의 “모든 것”이 객체이다. 기본자료형(Primitives)을 제외한 나머지 값들(배열, 함수, 정규표현식 등)은 모두 객체이다. 또한 객체는 pass-by-reference(참조로 접근)이며 메모리의 힙 영역(Heap Segment)에 저장된다.*

#

## 변수 호이스팅
*var 키워드로 선언된 변수는 선언 단계와 초기화 단계가 한번에 이루어진다. 즉, 스코프에 변수가 등록되고 변수는 메모리에 공간을 확보한 후 undefined 로 초기화된다. 따라서 변수 선언문 이전에 변수에 접근하여도 Variable Object 에 변수가 존재하기 때문에 에러가 발생하지 않는다. 다만 undefined 를 반환한다. 이러한 현상을 변수 호이스팅(Variable Hoisting)*
 
*JavaScript 의 변수는 다른 C-family 와는 달리 block-level scope 를 가지지 않고 function-level scope 를 갖는다. 단, ECMAScript 6에서 도입된 let, const 키워드를 사용하면 block-level scope 를 사용할 수 있다.*
 
    Function-level scope
    함수내에서 선언된 변수는 함수 내에서만 유효하며 함수 외부에서는 참조할 수 없다. 즉, 함수 내부에서 선언한 변수는 지역 변수이며 함수 외부에서 선언한 변수는 모두 전역 변수이다.
<br/>
    
    Block-level scope

    코드 블럭 내에서 선언된 변수는 코드 블럭 내에서만 유효하며 코드 블럭 외부에서는 참조할 수 없다.
#
   
## Scope (유효범위)
> 변수에서의 접근성과 생존기간(life-cycle)을 의미한다. 달리 말하자면 변수가 가지고 있는 참조 범위를 의미한다.

    전역 Scope (Global scope)
    - 코드 어디에서든지 참조할 수 있다.
<br/>
    
    지역 Scope (Local scope or Function-level scope)
    정의된 함수 내에서만 참조할 수 있다.
    
 모든 변수는 Scope 를 갖는다
    
    젼역 변수 (Global variable)
    전역 Scope 를 갖는 변수
<br/>

    지역 변수 (Local variable)
    지역 Scope 를 갖는 변수
    
 변수는 선언위치(전역 또는 지역)에 의해 Scope 를 가지게 된다. 즉, 전역에서 선언된 변수는 전역 Scope를 갖는 전역 변수이고, 지역(자바스크립트의 경우 함수 내부)에서 선언된 변수는 지역 Scope 를 갖는 지역 변수가 된다.
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
    
 중첩 scope는 가장 인접한 지역을 우선하여 참조한다.
    
### Lexical scoping (Static scoping)
*자바스크립트는 함수가 선언된 시점에서의 유효범위를 갖는다. 예제의 함수 bar가 어떤 상황에서 호출될 지 선언 시점에서는 알 수 없다.*

    var i = 5;
    
    function foo() {
      var i = 10;
      bar();
    }
    
    function bar() { // 선언된 시점에서의 scope를 갖는다!
      console.log(i);
    }
    
    foo(); // 5
    
전역변수를 반드시 사용하여야 할 이유를 찾지 못한다면 지역변수를 사용하여야 한다. 변수의 범위인 스코프는 좁을수록 좋다.

### 최소한의 전역변수 사용
*전역변수 사용을 최소화하는 방법 중 하나는 애플리케이션에서 전역변수 사용을 위해 다음과 같이 전역변수 객체 하나를 만들어 사용하는 것이다. (더글라스 크락포드의 제안)*

    var MYAPP = {};
    
    MYAPP.student = {
      name: 'Lee',
      gender: 'male'
    };
    
    console.log(MYAPP.student.name);

### 즉시실행함수를 이용한 전역변수 사용 억제
*전역변수 사용을 억제하기 위해, 즉시 실행 함수(IIFE, Immediately-Invoked Function Expression)를 사용할 수 있다. 이 방법을 사용하면 전역변수를 만들지 않으므로 라이브러리 등에 자주 사용된다. 즉시 실행 함수는 즉시 실행되고 그 후 전역에서 바로 사라진다.*

    (function () {
      var MYAPP = {};
    
      MYAPP.student = {
        name: 'Lee',
        gender: 'male'
      };
    
      console.log(MYAPP.student.name);  //  Lee
    }());
    
    console.log(MYAPP.student.name);  //  ReferenceError: MYAPP is nor defined

#

## this
> 자바스크립트의 함수는 호출될 때, 매개변수로 전달되는 인자값 이외에, arguments 객체와 this 를 암묵적으로 전달 받는다.

    function square(number) {
    
      console.log(arguments);
      console.log(this);
    
      return number * number;
    }
    
    var result = square();
    
 자바스크립트의 경우 함수 호출 패턴에 따라 어떤 객체를 this 에 바인딩할 지가 결정된다. 즉 함수 호출 패턴에 따라 this 의 참조값이 달라진다.

> 함수 호출 패턴
<br/><br/>1. 함수 호출 패턴<br/>2. 메소드 호출 패턴<br/>3. 생성자 호출 패턴<br/>4. apply 호출 패턴

### 1. 함수 호출 패턴 (Function Invocation Pattern)
*전역객체(Global Object)는 모든 객체의 유일한 최상위 객체를 의미하며 일반적으로 Browser-side 에서는 window, Server-side(Node.js)에서는 global 객체를 의미한다.*

    // in browser console
    this === window // true
    
    // in Terminal
    node
    this === global // true

 기본적으로 this 는 전역객체(Global object)에 바인딩된다. 전역함수는 물론이고 심지어 내부함수의 경우도 this 는 외부함수가 아닌 전역객체에 바인딩된다.
    
    function foo() {
      console.log("foo's this: ",  this);  // window
      function bar() {
        console.log("bar's this: ", this); // window
      }
      bar();
    }
    foo();
    
 또한 메소드의 내부함수일 경우에도 this 는 전역객체에 바인딩된다.
    
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
    
 콜백함수의 경우에도 this 는 전역객체에 바인딩된다.
  
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
    
 더글라스 크락포드는 “이것은 설계 단계의 결함으로 메소드가 내부함수를 사용하여 자신의 작업을 돕게 할 수 없다는 것을 의미한다” 라고 말한다. 내부함수의 this가 전역객체를 참조하는 것을 회피방법은 아래와 같다.

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

 메소드 호출 패턴이든 함수 호출 패턴이든 내부함수의 this 는 모두 전역객체에 바인딩된다. 이러한 문제를 해소하기 위해 자바스크립트는 this 바인딩을 명시적으로 할 수 있는 call, apply 메소드를 제공한다.

### 2. 메소드 호출 패턴 (Method Invocation Pattern)
*함수가 객체의 프로퍼티이면 메소드 호출 패턴으로 호출된다. 이때 메소드 내부의 this 는 해당 메소드를 소유한 객체 즉 해당 메소드를 호출한 객체에 바인딩된다.*

    var obj1 = {
      name: 'Lee',
      sayName: function() {
        console.log(this.name);
      }
    }
    
    var obj2 = {
      name: 'Kim'
    }
    
    obj2.sayName = obj1.sayName;
    
    obj1.sayName();
    obj2.sayName();

 <img src="http://poiemaweb.com/img/Method_Invocation_Pattern.png">

 프로토타입 객체도 메소드를 가질 수 있다. 프로토타입 객체 메소드 내부에서 사용된 this 도 일반 메소드 방식과 마찬가지로 해당 메소드를 호출한 객체에 바인딩된다.    

    function Person(name) {
      this.name = name;
    }
    
    Person.prototype.getName = function() {
      return this.name;
    }
    
    var me = new Person('Lee');
    console.log(me.getName());
    
    Person.prototype.name = 'Kim';
    console.log(Person.prototype.getName());
    
<img src="http://poiemaweb.com/img/prototype_metthod_invocation_pattern.png">

### 3. 생성자 호출 패턴(Constructor Invocation Pattern)
*자바스크립트의 생성자 함수는 말 그대로 객체를 생성하는 역할을 한다. 하지만 자바와 같은 객체지향 언어의 생성자 함수와는 다르게 그 형식이 정해져 있는 것이 아니라 기존 함수에 new 연산자를 붙여서 호출하면 해당 함수는 생성자 함수로 동작한다.*

##### 3.1 생성자 함수 동작 방식
*new 연산자와 함께 생성자 함수를 호출하면 다음과 같은 수순으로 동작한다.*

    1. 빈 객체 생성 및 this 바인딩
       생성자 함수의 코드가 실행되기 전 빈 객체가 생성된다. 이 빈 객체가 생성자 함수가 새로 생성하는 객체이다. 이후 생성자 함수 내에서 사용되는 this는 이 빈 객체를 가리킨다. 그리고 생성된 빈 객체는 생성자 함수의 prototype 프로퍼티가 가리키는 객체를 자신의 프로토타입 객체로 설정한다.
    
    2. this를 통한 프로퍼티 생성
       생성된 빈 객체에 this를 사용하여 동적으로 프로퍼티나 메소드를 생성할 수 있다. this는 새로 생성된 객체를 가리키므로 this를 통해 생성한 프로퍼티와 메소드는 새로 생성된 객체에 추가된다.
       
    3. - 반환문이 없는 경우, this에 바인딩된 새로 생성한 객체가 반환된다. 명시적으로 this를 반환하여도 결과는 같다.
       - 반환문이 this가 아닌 다른 객체를 명시적으로 반환하는 경우, this가 아닌 해당 객체가 반환된다. 이때 this를 반환하지 않은 함수는 생성자 함수로서의 역할을 수행하지 못한다. 따라서 생성자 함수는 반환문을 명시적으로 사용하지 않는다.  

<img src="http://poiemaweb.com/img/constructor.png"> 

##### 3.2 객체 리터럴 방식과 생성자 함수 방식의 차이
> 객체 리터럴 방식과 생성자 함수 방식의 차이를 비교

    // 객체 리터럴 방식
    var foo = {
      name: 'foo',
      gender: 'male'
    }
    
    console.dir(foo);
    
    // 생성자 함수 방식
    var Person = function(name, gender) {
      this.name = name;
      this.gender = gender;
    }
    
    var me  = new Person('Lee', 'male');
    console.dir(me);
    
    var you = new Person('Kim', 'female');
    console.dir(you);
    
*객체 리터럴 방식과 생성자 함수 방식의 차이는 프로토타입 객체([[prototype]])에 있다.*

- 객체 리터럴 방식의 경우, 생성된 객체의 프로토타입 객체는 Object.prototype 이다.
- 생성자 함수 방식의 경우, 생성된 객체의 프로토타입 객체는 Person.prototype 이다.

##### 3.3 생성자 함수에 new 연산자를 붙이지 않고 호출할 경우
*일반함수와 생성자 함수에 특별한 형식적 차이는 없으며 함수에 new 연산자를 붙여서 호출하면 해당 함수는 생성자 함수로 동작한다.*

그러나 객체 생성 목적으로 작성한 생성자 함수를 new 없이 호출하거나 일반함수에 new 를 붙여 호출하면 오류가 발생할 수 있다. 일반함수와 생성자 함수의 호출 시 this 바인딩 방식이 다르기 때문이다.

일반 함수를 호출하면 this 는 전역객체에 바인딩되지만 new 연산자와 함께 생성자 함수를 호출하면 this 는 생성자 함수가 암묵적으로 생성한 빈 객체에 바인딩된다.
    
    var Person = function(name) {
      // new없이 호출하는 경우, 전역객체에 name 프로퍼티를 추가
      this.name = name;
    };
    
    // 일반 함수로서 호출되었기 때문에 객체를 암묵적으로 생성하여 반환하지 않는다.
    // 일반 함수의 this는 전역객체를 가리킨다.
    var me = Person('Lee');
    
    console.log(me); // undefined
    console.log(window.name); // Lee

### 4. apply 호출 패턴(Apply Invocation Pattern)
this에 바인딩될 객체는 함수 호출 패턴에 의해 결정된다. 이는 자바스크립트 엔진이 수행하는 것이다. 이러한 자바스크립트 엔진의 암묵적 this 바인딩 이외에 this를 특정 객체에 명시적으로 바인딩하는 방법도 제공된다. 이것을 가능하게 하는 것이 Function.prototype.apply(), Function.prototype.call() 메소드이다.

이 메소드들은 모든 함수 객체의 프로토타입 객체인 Function.prototype 객체의 메소드이다.

    func.apply(thisArg, [argsArray])
    
    // thisArg: 함수 내부의 this에 바인딩할 객체
    // argsArray: 함수에 전달할 argument의 배열

기억해야 할 것은 apply() 메소드를 호출하는 주체는 함수이며 apply() 메소드는 this 를 특정 객체에 바인딩할 뿐 본질적인 기능은 함수 호출이라는 것이다.

    var Person = function (name) {
      this.name = name;
    };
    
    var foo = {};
    
    // apply 메소드는 생성자함수 Person을 호출한다. 이때 this에 객체 foo를 바인딩한다.
    Person.apply(foo, ['name']);
    
    console.log(foo); // { name: 'name' }
    
빈 객체 foo 를 apply() 메소드의 첫번째 매개변수에, argument 의 배열을 두번째 매개변수에 전달하면서 Person 함수를 호출하였다. 이때 Person 함수의 this는 foo 객체가 된다. Person 함수는 this의 name 프로퍼티에 매개변수 name에 할당된 인수를 할당하는데 this에 바인딩된 foo 객체에는 name 프로퍼티가 없으므로 name 프로퍼티가 동적 추가되고 값이 할당된다.

apply() 메소드의 대표적인 용도는 arguments 객체와 같은 유사 배열 객체에 배열 메소드를 사용하는 경우이다. arguments 객체는 배열이 아니기 때문에 slice() 같은 배열의 메소드를 사용할 수 없으나 apply() 메소드를 이용하면 가능하다.

    function convertArgsToArray() {
      console.log(arguments);
    
      // arguments 객체를 배열로 변환
      // slice: 배열의 특정 부분에 대한 복사본을 생성한다.
      var arr = Array.prototype.slice.apply(arguments); // arguments.slice
      // var arr = [].slice.apply(arguments);
    
      console.log(arr);
      return arr;
    }
    
    convertArgsToArray(1, 2, 3);
Array.prototype.slice.apply(arguments)는 “Array.prototype.slice() 메소드를 호출하라. 단 this 는 arguments 객체로 바인딩하라”는 의미가 된다. 결국 Array.prototype.slice() 메소드를 arguments 객체 자신의 메소드인 것처럼 arguments.slice()와 같은 형태로 호출하라는 것이다.
<img src="http://poiemaweb.com/img/apply.png">

call() 메소드의 경우, apply()와 기능은 같지만 apply()의 두번째 인자에서 배열 형태로 넘긴 것을 각각 하나의 인자로 넘긴다.

    Person.apply(foo, [1, 2, 3]);
    
    Person.call(foo, 1, 2, 3);

apply()와 call() 메소드는 콜백 함수의 this 를 위해서 사용되기도 한다.

    function Person(name) {
      this.name = name;
    }
    
    Person.prototype.doSomething = function(callback) {
      if(typeof callback == 'function') {
        // --------- 1
        callback();
      }
    };
    
    function foo() {
      console.log(this.name); // --------- 2
    }
    
    var p = new Person('Lee');
    p.doSomething(foo);  // undefined
    
1의 시점에서 this 는 Person 객체이다. 그러나 2의 시점에서 this 는 전역 객체 window 를 가리킨다. 콜백함수를 호출하는 외부 함수 내부의 this와 콜백함수 내부의 this가 상이하기 때문에 문맥상 문제가 발생한다. 따라서 콜백함수 내부의 this 를 콜백함수를 호출하는 함수 내부의 this 와 일치시켜 주어야 하는 번거로움이 발생한다.

    function Person(name) {
      this.name = name;
    }
    
    Person.prototype.doSomething = function(callback) {
      if(typeof callback == 'function') {
        callback.call(this);
      }
    };
    
    function foo() {
      console.log(this.name);
    }
    
    var p = new Person('Lee');
    p.doSomething(foo);  // 'Lee'
    


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
*!! 의 역할은 피연사자를 불린값으로 변환하는 것이다.*

    console.log(!!1);         // true
    console.log(!!0);         // false
    console.log(!!'string');  // true
    console.log(!!'');        // false
    console.log(!!null);      // false
    console.log(!!undefined); // false
    console.log(!!{});        // true
    console.log(!![]);        // true
    
 객체(배열 포함)의 경우 빈 객체라도 존재하기만하면 true 로 변환된다.
  
 객체의 존재 확인 후 그 결과를 반환해야 하는 경우, !!를 사용하면 강제로 피연산자를 boolean 으로 형 변환 할 수 있다.
    
    var obj;
    console.log(!!obj); // false
    
    obj = {};
    console.log(!!obj); // true
    

 아래 값들은 Boolean context 에서 false 로 평가된다.<ul><li>false</li><li>undefined</li><li>null</li><li>0</li><li>NaN (Not a Number)</li><li>'' (빈문자열)</li></ul>
이들을 Falsy value 라 한다.  

#

## 1. 객체(Object)란?
*객체는 데이터와 그 데이터에 관련되는 동작(절차, 방법, 기능)을 모두 포함할 수 있는 개념적 존재이다. 달리 말해, 이름(키)과 값으로 구성된 데이터를 의미하는 프로퍼티(property)와 동작을 나타내는 메소드(method)를 포함하고 있는 독립적 주체이다.*

### 프로퍼티(Property)
*객체는 이름(name)과 값(value)의 쌍인 프로퍼티들을 포함하는 컨테이너라고 할 수 있다.*
<ul><li>프로퍼티 이름 : 빈 문자열을 포함하는 문자열과 숫자</li><li>프로퍼티 값 : undefined을 제외한 모든 값</li></ul> 

### 메소드(Method)
*메소드는 객체에 제한되어 있는 함수를 의미한다. 즉 프로퍼티 값이 함수일 경우, 일반 함수와 구분하기 위해 메소드라 칭한다.*

## 2. 객체 생성 방법

### 2.1 객체 리터럴
가장 일반적이고 간편한 자바스크립트의 객체 생성 방식

중괄호({})를 사용하여 객체를 생성하는데 {} 내에 아무것도 기술하지 않으면 빈 객체가 생성

    var emptyObject = {};
    console.log(typeof emptyObject); // object
    
    var person = {
      name: 'Lee',
      gender: 'male',
      sayHello: function () {
        console.log('Hi! My name is ' + this.name);
      }
    };
    
    console.log(typeof person); // object
    console.log(person); // { name: 'Lee', gender: 'male', sayHello: [Function: sayHello] }
    
    person.sayHello(); // Hi! My name is Lee
    
### 2.2 Object() 생성자 함수
new 연산자와 Object() 생성자 함수를 사용하여 빈 객체를 생성

빈 객체 생성 이후 프로퍼티와 메소드를 추가하여 객체를 완성하는 방법

    // 빈 객체의 생성
    var person = new Object();
    // 프로퍼티 추가
    person.name = 'Lee';
    person.gender = 'male';
    person.sayHello = function () {
      console.log('Hi! My name is ' + this.name);
    };
    
    console.log(typeof person); // object
    console.log(person); // { name: 'Lee', gender: 'male', sayHello: [Function] }
    
    person.sayHello(); // Hi! My name is Lee
    
Object() 생성자 함수 방식은 특별한 이유가 없다면 그다지 유용해 보이지 않는다. 하지만 객체 리터럴 방식으로 생성된 객체는 결국 내장(Built-in) 함수인 Object() 생성자 함수로 객체를 생성하는 것을 단순화 시킨 short-hand(축약법)이다. 자바스크립트 엔진은 객체 리터럴로 객체를 생성하는 코드를 만나면 내부적으로 Object() 생성자 함수를 사용하여 객체를 생성한다.

### 2.3 생성자 함수
생성자 함수를 사용하면 마치 객체를 생성하기 위한 템플릿(클래스)처럼 사용하여 구성이 동일한 객체 여러개를 간편하게 생성할 수 있다.

    // 생성자 함수
    function Person(name, gender) {
      this.name = name;
      this.gender = gender;
      this.sayHello = function(){
        console.log('Hi! My name is ' + this.name);
      };
    }
    
    // 인스턴스의 생성
    var person1 = new Person('Lee', 'male');
    var person2 = new Person('Kim', 'female');
    
    console.log('person1: ', typeof person1);
    console.log('person2: ', typeof person2);
    console.log('person1: ', person1);
    console.log('person2: ', person2);
    
    person1.sayHello();
    person2.sayHello();

- 생성자 함수 이름은 일반적으로 대문자로 시작한다. 이것은 생성자 함수임을 인식하도록 도움을 준다.
- 프로퍼티 또는 메소드명 앞에 기술한 this 는 생성자 함수가 생성할 인스턴스(instance)를 가리킨다.
- this 에 연결(바인딩)되어 있는 프로퍼티와 메소드는 public(외부에서 참조 가능)하다.
- 생성자 함수 내에서 선언된 일반 변수는 private(외부에서 참조 불가능)하다. 즉 생성자 함수 내부에서는 자유롭게 접근이 가능하나 외부에서 접근할 수 없다.


## 3 객체와 변경불가성 (Immutability)
*Immutability(변경불가성)는 객체가 생성된 이후 그 상태를 변경할 수 없는 디자인 패턴을 의미한다. Immutability 은 함수형 프로그래밍의 핵심 원리이다.*

### 3.1 immutable value vs. mutable value
Javascript 의 기본 자료형(primitive data type)은 변경 불가능한 값(immutable value)이다.
- Boolean
- null
- undefined
- Number
- String
- Symbol (New in ECMAScript 6)

기본 자료형 이외의 모든 값은 객체(Object) 타입이며 객체 타입은 변경 가능한 값(mutable value)이다. 즉 객체는 새로운 값을 다시 만들 필요없이 직접 변경이 가능하다는 것이다.

Javascript 의 문자열은 변경 불가능한 값(immutable value) 이다. 이런 값을 “primitive values” 라 한다. (변경이 불가능하다는 뜻은 메모리 영역에서의 변경이 불가능하다는 뜻이다. 재할당은 가능하다)

### 3.2 불변 데이터 패턴(immutable data pattern) (new in ECMAScript 6)
- 객체의 방어적 복사(defensive copy)

     Object.assign
     
Object.assign 은 타킷 객체로 소스 객체의 프로퍼티를 복사한다. 이때 소스 객체의 프로퍼티와 동일한 프로퍼티를 가진 타켓 객체의 프로퍼티들은 소스 객체의 프로퍼티로 덮어쓰기된다. 리턴값으로 타킷 객체를 반환한다. ES6에서 추가된 메소드이며 Internet Explorer는 지원하지 않는다.

    // Syntax
    Object.assign(target, ...sources)
    
    // Copy
    const obj = { a: 1 };
    const copy = Object.assign({}, obj);
    console.log(copy); // { a: 1 }
    console.log(obj == copy); // false
    
    // Merge
    const o1 = { a: 1 };
    const o2 = { b: 2 };
    const o3 = { c: 3 };
    
    const merge1 = Object.assign(o1, o2, o3);
    
    console.log(merge1); // { a: 1, b: 2, c: 3 }
    console.log(o1);     // { a: 1, b: 2, c: 3 }, 타겟 객체가 변경된다!
    
    // Merge
    const o4 = { a: 1 };
    const o5 = { b: 2 };
    const o6 = { c: 3 };
    
    const merge2 = Object.assign({}, o4, o5, o6);
    
    console.log(merge2); // { a: 1, b: 2, c: 3 }
    console.log(o4);     // { a: 1 }

Object.assign 을 사용하여 기존 객체를 변경하지 않고 객체를 복사(Shallow copy)하여 사용할 수 있다.

    const user1 = {
      name: 'Lee',
      address: {
        city: 'Seoul'
      }
    };
    
    // Shallow copy
    const user2 = Object.assign({}, user1); // user1을 {}에 Copy
    
    user2.name = 'Kim';
    
    // 상기 2행은 아래와 동치이다.
    // {name: 'Kim'}은 user1에 병합되는 것이 아니라 첫번째 인자인 {}에 병합된다.
    // const user2 = Object.assign({}, user1, {name: 'Kim'});
    
    console.log(user1.name); // Lee
    console.log(user2.name); // Kim
    
- 불변객체화를 통한 객체 변경 방지

    Object.freeze
    
Object.freeze()를 사용하여 불변(immutable) 객체로 만들수 있다.

    const user1 = {
      name: 'Lee',
      address: {
        city: 'Seoul'
      }
    };
    
    // Shallow copy
    const user2 = Object.assign({}, user1, {name: 'Kim'});
    
    console.log(user1.name); // Lee
    console.log(user2.name); // Kim
    
    Object.freeze(user1);
    
    user1.name = 'Kim'; // 무시된다!
    
    console.log(user1); // { name: 'Lee', address: { city: 'Seoul' } }
    
    console.log(Object.isFrozen(user1)); // true
    
하지만 객체 내부의 객체(Nested Object)는 변경가능하다.

    const user = {
      name: 'Lee',
      address: {
        city: 'Seoul'
      }
    };
    
    Object.freeze(user);
    
    user.address.city = 'Busan'; // 변경된다!
    console.log(user); // { name: 'Lee', address: { city: 'Busan' } }
    
내부 객체까지 변경 불가능하게 만들려면 Deep freeze 를 하여야 한다.    

    function deepFreeze(obj) {
      const props = Object.getOwnPropertyNames(obj);
    
      props.forEach((name) => {
        const prop = obj[name];
        if(typeof prop === 'object' && prop !== null) {
          deepFreeze(prop);
        }
      });
      return Object.freeze(obj);
    }
    
    const user = {
      name: 'Lee',
      address: {
        city: 'Seoul'
      }
    };
    
    deepFreeze(user);
    
    user.name = 'Kim';           // 무시된다
    user.address.city = 'Busan'; // 무시된다
    
    console.log(user); // { name: 'Lee', address: { city: 'Seoul' } }
    
Object.assign 과 Object.freeze 을 사용하여 불변 객체를 만드는 방법은 번거러울 뿐더러 성능상 이슈가 있어서 큰 객체에는 사용하지 않는 것이 좋다.

## 4. 함수 (Function)
### 4.1 함수선언식(Function declaration)
    function square(number) {
      return number * number;
    }

### 4.2 함수표현식(Function expression)
자바스크립트의 함수는 *일급 객체*이므로 아래와 같은 특징이 있다.

1. 무명의 리터럴로 표현이 가능하다.
2. 변수나 자료 구조(객체, 배열…)에 저장할 수 있다.
3. 함수의 파라미터로 전달할 수 있다.
4. 반환값(return value)으로 사용할 수 있다.

함수의 일급객체 특성을 이용하여 함수 리터럴 방식으로 함수를 정의하고 변수에 할당할 수 있는데 이러한 방식을 함수표현식(Function expression)이라 한다.

    var square = function(number) {
      return number * number;
    };
    
함수표현식으로 정의한 함수는 함수명을 생략할 수 있다. 이러한 함수를 익명 함수(anonymous function)이라 한다. 함수표현식에서는 함수명을 생략하는 것이 일반적이다.    

    // 기명 함수표현식(named function expression)
    var foo = function multiply(a, b) {
      return a * b;
    };
    // 익명 함수표현식(anonymous function expression)
    var bar = function(a, b) {
      return a * b;
    };
    
    console.log(foo(10, 5)); // 50
    console.log(multiply(10, 5)); // Uncaught ReferenceError: multiply is not defined
    
함수는 일급객체이기 때문에 변수에 할당할 수 있는데 이 변수는 함수명이 아니라 할당된 함수를 가리키는 참조값을 저장하게 된다. 함수 호출시 함수명이 아니라 함수를 가리키는 변수명을 사용하여야 한다.

### 4.3 함수 호이스팅 (Function Hoisting)

    var res = square(5);
    
    function square(number) {
      return number * number;
    }
    
자바스크립트는 ES6의 let, const 를 포함하여 모든 선언(var, let, const, function, function*, class)을 호이스팅(Hoisting)한다.

호이스팅이란 var 선언문이나 function 선언문 등 모든 선언문이 해당 Scope 의 선두로 옮겨진 것처럼 동작하는 특성을 말한다. 즉 자바스크립트는 모든 선언문(var, let, const, function, function*, class)이 선언되기 이전에 참조 가능하다.

함수선언식으로 정의된 함수는 자바스크립트 엔진이 스크립트가 로딩되는 시점에 바로 초기화하고 이를 VO(variable object)에 저장한다. 즉, *함수 선언, 초기화, 할당이 한번에 이루어진다.* 그렇기 때문에 함수 선언의 위치와는 상관없이 소스 내 어느 곳에서든지 호출이 가능하다.

    var res = square(5); // TypeError: square is not a function
    
    var square = function(number) {
      return number * number;
    }

함수선언식의 경우와는 달리 TypeError 가 발생하였다. 함수표현식의 경우 함수 호이스팅이 아니라 변수 호이스팅이 발생한다.

*변수 호이스팅은 변수 생성 및 초기화와 할당이 분리되어 진행된다. 호이스팅된 변수는 undefined 로 초기화 되고 실제값의 할당은 할당문에서 이루어진다.*

함수표현식은 함수선언식과는 달리 스크립트 로딩 시점에 변수 객체(VO)에 함수를 할당하지 않고 runtime 에 해석되고 실행되므로 이 두가지를 구분하는 것은 중요하다.

*자바스크립트의 권위자인 더글러스 크락포드(Douglas Crockford)는 이와 같은 문제 때문에 함수표현식만을 사용할 것을 권고하고 있다. 함수 호이스팅이 함수 호출 전 반드시 함수를 선언하여야 한다는 규칙을 무시하므로 코드의 구조를 엉성하게 만들 수 있다고 지적한다.*

*또한 함수선언식으로 함수를 정의하면 사용하기에 쉽지만 대규모 애플리케이션을 개발하는 경우 인터프리터가 너무 많은 코드를 변수 객체(VO)에 저장하므로 애플리케이션의 응답속도는 현저히 떨어질 수 있으므로 주의해야 할 필요가 있다.*

### 4.4 First-class object (일급 객체)
*일급 객체(first-class object)란 생성, 대입, 연산, 인자 또는 반환값으로서의 전달 등 프로그래밍 언어의 기본적 조작을 제한없이 사용할 수 있는 대상을 의미한다.*

1. 무명의 리터럴로 표현이 가능하다.
2. 변수나 자료 구조(객체, 배열…)에 저장할 수 있다.
3. 함수의 파라미터로 전달할 수 있다.
4. 반환값(return value)으로 사용할 수 있다.


    // 1. 무명의 리터럴로 표현이 가능하다.
    // 2. 변수나 데이터 구조안에 담을 수 있다.
    var increase = function(num) {
      return num + 1;
    };
    
    var decrease = function(num){
      return num - 1;
    };
    
    var obj = {
      increase: increase,
      decrease: decrease
    };
    
    // 2. 함수의 파라미터로 전달 할 수 있다.
    function calc(func, num){
      return func(num);
    }
    
    console.log(calc(increase, 1));
    console.log(calc(decrease, 1));
    
    // 3. 반환값(return value)으로 사용할 수 있다.
    function calc(mode){
      var funcs = {
        plus:  function(left, right){ return left + right; },
        minus: function(left, right){ return left - right; }
      };
      return funcs[mode];
    }
    console.log(calc('plus')(2,1));
    console.log(calc('minus')(2,1));

## 5. 매개변수(Parameter, 인자)
*함수의 작업 실행을 위해 추가적인 정보가 필요할 경우, 매개변수를 지정한다. 매개변수는 함수 내에서 변수와 동일하게 동작한다.*

### 5.1 Call-by-value
Primitives(기본자료형) 인수는 Call-by-value(값에 의한 호출)로 동작한다. 이는 함수 호출 시 기본자료형 인수를 함수에 매개변수로 전달할 때 매개변수에 값을 복사하여 함수로 전달하는 방식이다. 이때 함수 내에서 매개변수를 통해 값이 변경되어도 전달이 완료된 기본자료형 값은 변경되지 않는다.

    function foo(primitive) {
      primitive += 1;
      return primitive;
    }
    
    var x = 0;
    
    console.log(foo(x)); // 1
    console.log(x);      // 0
    
### 5.2 Call-by-reference
객체형(참조형) 인수는 Call-by-reference(참조에 의한 호출)로 동작한다. 이는 함수 호출 시 참조 타입 인수를 함수에 매개변수로 전달할 때 매개변수에 값이 복사되지 않고 객체의 참조값이 매개변수에 저장되어 함수로 전달되는 방식이다. 이때 함수 내에서 매개변수의 참조값이 이용하여 객체의 값을 변경했을 때 전달되어진 참조형의 인수값도 같이 변경된다.

    function changeVal(primitive, obj) {
      primitive += 100;
      obj.name = 'Kim';
      obj.gender = 'female';
    }
    
    var num = 100;
    var obj = {
      name: 'Lee',
      gender: 'male'
    };
    
    console.log(num); // 100
    console.log(obj); // Object {name: 'Lee', gender: 'male'}
    
    changeVal(num, obj);
    
    console.log(num); // 100
    console.log(obj); // Object {name: 'Kim', gender: 'female'}
    
어떤 외부 상태도 변경하지 않는 함수를 순수함수(Pure function), 외부 상태도 변경시켜는 부수 효과(side-effect)가 발생시키는 함수를 비순수 함수(Impure function)라 한다.

## 6. 반환값 (return value)
함수는 자신을 호출한 코드에게 수행한 결과를 반환(return)할 수 있다.
- return 키워드는 함수를 호출한 코드(caller)에게 값을 반환할 때 사용한다.
- 함수는 배열 등을 이용하여 한 번에 여러 개의 값을 리턴할 수 있다.
- 함수는 반환을 생략할 수 있다. 이때 함수는 암묵적으로 undefined 를 반환한다.
- 자바스크립트 해석기는 return 키워드를 만나면 함수의 실행을 중단한 후, 함수를 호출한 코드로 되돌아간다. 만일 return 키워드 이후에 다른 구문이 존재하면 그 구문은 실행되지 않는다.


    function calculateArea(width, height) {
      var area = width * height;
      return area; // 단일 값의 반환
    }
    console.log(calculateArea(3, 5)); // 15
    console.log(calculateArea(8, 5)); // 40
    
    function getSize(width, height, depth) {
      var area = width * height;
      var volume = width * height * depth;
      return [area, volume]; // 복수 값의 반환
    }
    
    console.log('area is ' + getSize(3, 2, 3)[0]);   // area is 6
    console.log('volume is ' + getSize(3, 2, 3)[1]); // volume is 18
    
## 7. 함수 객체의 프로퍼티
함수는 객체이다. 따라서 함수도 프로퍼티를 가질 수 있다.

    function square(number) {
      return number * number;
    }
    
    square.x = 10;
    square.y = 20;
    
    console.log(square.x, square.y);
    

### 7.1 arguments 프로퍼티
arguments 객체는 함수 호출 시 전달된 인수(argument)들의 정보를 담고 있는 순회가능한(iterable) 유사 배열 객체(array-like object)이다.
 
함수 객체의 arguments 프로퍼티는 arguments 객체를 값으로 가지며 함수 내부에서 지역변수처럼 사용된다. 즉 함수 외부에서는 사용할 수 없다.

매개변수(parameter)는 인수(argument)로 초기화된다.

- 매개변수의 갯수보다 인수를 적게 전달했을 때(multiply(), multiply(1)) 인수가 전달되지 않은 매개변수는 undefined 으로 초기화된다.
- 매개변수의 갯수보다 인수를 더 많이 전달한 경우, 초과된 인수는 무시된다.

arguments 객체는 매개변수 갯수가 확정되지 않은 *가변 인자 함수*를 구현할 때 유용하게 사용된다.

    function sum() {
      var res = 0;
    
      for (var i = 0; i < arguments.length; i++) {
        res += arguments[i];
      }
    
      return res;
    }
    
    console.log(sum());        // 0
    console.log(sum(1, 2));    // 3
    console.log(sum(1, 2, 3)); // 6
    
자바스크립트는 함수를 호출할 때 인수들과 함께 암묵적으로 arguments 객체가 함수 내부로 전달된다. arguments 객체는 배열의 형태로 인자값 정보를 담고 있지만 실제 배열이 아닌 *유사배열객체(array-like object)*이다.

유사배열객체란 length 프로퍼티를 가진 객체를 말한다. 유사배열객체는 배열이 아니므로 배열 메소드를 사용하는 경우 에러가 발생하게 된다. 따라서 배열 메소드를 사용하려면 Function.prototype.call, Function.prototype.apply 를 사용하여야 하는 번거로움이 있다.

    function sum() {
      if (!arguments.length) return 0;
    
      // arguments 객체를 배열로 변환
      var array = Array.prototype.slice.call(arguments);
      return array.reduce(function (pre, cur) {
        return pre + cur;
      });
    }
    
    // ES6
    // function sum(...args) {
    //   if (!args.length) return 0;
    //   return args.reduce((pre, cur) => pre + cur);
    // }
    
    console.log(sum(1, 2, 3, 4, 5)); // 15
    
### 7.2 caller 프로퍼티
caller 프로퍼티는 자신을 호출한 함수를 의미한다.

    function foo(func) {
      var res = func();
      return res;
    }
    
    function bar() {
      return 'caller : ' + bar.caller;
    }
    
    console.log(foo(bar)); // function foo(func) {...}
    console.log(bar());    // null (browser에서의 실행 결과)
    
### 7.3 length 프로퍼티
length 프로퍼티는 함수 정의 시 작성된 매개변수 갯수를 의미한다.

### 7.4 name 프로퍼티
함수명을 나타낸다. 기명함수의 경우 함수명을 값으로 갖고 익명함수의 경우 빈문자열을 값으로 갖는다.

    // 기명 함수표현식(named function expression)
    var namedFunc = function multiply(a, b) {
      return a * b;
    };
    // 익명 함수표현식(anonymous function expression)
    var anonymousFunc = function(a, b) {
      return a * b;
    };
    
    console.log(namedFunc.name);     // multiply
    console.log(anonymousFunc.name); // ''
    
### 7.5 \_\_proto\_\_ 프로퍼티
ECMAScript spec 에서는 모든 객체는 자신의 프로토타입을 가리키는 \[\[Prototype\]\]이라는 숨겨진 프로퍼티를 가진다 라고 되어있다. 크롬, 파이어폭스 등에서는 숨겨진 \[\[Prototype\]\] 프로퍼티가 \_\_proto\_\_ 프로퍼티로 구현되어 있다. 즉 \_\_proto\_\_과 \[\[Prototype\]\]은 같은 개념이다.

square() 함수 역시 객체이므로 \[\[Prototype\]\] 프로퍼티(\_\_proto\_\_ 프로퍼티)을 가지며 이를 통해 자신의 부모 역할을 하는 프로토타입 객체를 가리킨다.

함수의 프로토타입 객체는 Function.prototype 이며 이것 역시 함수이다.

    function square(number) {
      return number * number;
    }
    
    console.log(square.__proto__ === Function.prototype);
    console.log(Object.getPrototypeOf(square) === Function.prototype);
    
### 7.6 prototype 프로퍼티
함수 객체만이 가지고 있는 프로퍼티로 자바스크립트 객체지향의 근간이다.

*주의해야 할 것은 함수 객체만이 가지고 있는 prototype 프로퍼티는 프로토타입 객체를 가리키는 \[\[Prototype\]\] 프로퍼티(\_\_proto\_\_ 프로퍼티)와는 다르다는 것이다.*

prototype 프로퍼티와 \[\[Prototype\]\] 프로퍼티는 모두 프로토타입 객체를 가리키지만 관점의 차이가 있다.

- \[\[Prototype\]\] 프로퍼티

    - 모든 객체가 가지고 있는 프로퍼티이다.
    - *객체의 입장에서 자신의 부모 역할을 하는 프로토타입 객체을 가리키며 함수 객체의 경우 Function.prototype 를 가리킨다.*
    
- prototype 프로퍼티

    - 함수 객체만 가지고 있는 프로퍼티이다.
    - *함수 객체가 생성자로 사용될 때 이 함수를 통해 생성된 객체의 부모 역할을 하는 객체를 가리킨다.*
    - 함수가 생성될 때 만들어 지며 constructor 프로퍼티를 가지는 객체를 가리킨다. 이 constructor 프로퍼티는 함수 객체 자신을 가리킨다
    
<img src="http://poiemaweb.com/img/function_prototype.png" />

*\[\[Prototype\]\] 프로퍼티는 함수 객체의 부모 객체(Function.prototype)를 가리키며 prototype 프로퍼티는 함수객체가 생성자 함수로 사용되어 객체를 생성할 때 생성된 객체의 부모 객체 역할을 하는 객체를 가리킨다.*

## 8. 함수의 다양한 형태

### 8.1 즉시호출함수표현식 (IIFE, Immediately Invoke Function Expression)
함수의 정의와 동시에 실행되는 함수를 즉시호출함수라고 한다. 최초 한번만 호출되며 다시 호출할 수는 없다. 이러한 특징을 이용하여 최초 한번만 실행이 필요한 초기화 처리등에 사용할 수 있다.

    // 기명 즉시실행함수(named immediately-invoked function expression)
    (function myFunction() {
      var a = 3;
      var b = 5;
      return a * b;
    }());
    
    // 익명 즉시실행함수(immediately-invoked function expression)
    (function () {
      var a = 3;
      var b = 5;
      return a * b;
    }());
    
자바스크립트에서 가장 큰 문제점 중의 하나는 파일이 분리되어 있다하여도 글로벌 스코프가 하나이며 글로벌 스코프에 선언된 변수나 함수는 코드 내의 어디서든지 접근이 가능하다는 것이다.

따라서 다른 스크립트 파일 내에서 동일한 이름으로 명명된 변수나 함수가 같은 스코프 내에 존재할 경우 원치 않는 결과를 가져올 수 있다.

즉시실행함수 내에 처리 로직을 모아 두면 혹시 있을 수도 있는 변수명 또는 함수명의 충돌을 방지할 수 있어 이를 위한 목적으로 즉시실행함수를 사용되기도 한다.

### 8.2 내부 함수 (Inner function)
함수 내부에 정의된 함수를 내부함수라 한다.

아래 예제의 내부함수 child 는 자신을 포함하고 있는 부모함수 parent의 변수에 접근할 수 있다. 하지만 부모함수는 자식함수(내부함수)의 변수에 접근할 수 없다.

    function parent(param) {
      var parentVar = param;
      function child() {
        var childVar = 'lee';
        console.log(parentVar + ' ' + childVar); // Hello lee
      }
      child();
      console.log(parentVar + ' ' + childVar);
      // Uncaught ReferenceError: childVar is not defined
    }
    parent('Hello');
    
또한 내부함수는 부모함수의 외부에서 접근할 수 없다.

    function sayHello(name){
      var text = 'Hello ' + name;
      var logHello = function(){ console.log(text); }
      logHello();
    }
    
    sayHello('lee');  // Hello lee
    logHello('lee');  // logHello is not defined
    
### 8.3 콜백 함수 (Callback function)
콜백함수는 함수를 명시적으로 호출하는 방식이 아니라 특정 이벤트가 발생했을 때 시스템에 의해 호출되는 함수를 말한다.

콜백함수가 자주 사용되는 대표적인 예는 이벤트 핸들러 처리이다.

    <!DOCTYPE html>
    <html>
    <body>
      <button id="myButton">Click me</button>
      <script>
        var button = document.getElementById('myButton');
        button.addEventListener('click', function() {
          console.log('button clicked!');
        });
      </script>
    </body>
    </html>
    
콜백함수는 콜백 큐에 들어가 있다가 해당 이벤트가 발생하면 호출된다. 콜백 함수는 클로저이므로 콜백 큐에 단독으로 존재하다가 호출되어도 콜백함수를 전달받은 함수의 변수에 접근할 수 있다.

    function doSomething() {
      var name = 'Lee';
    
      setTimeout(function () {
        console.log('My name is ' + name);
      }, 100);
    }
    
    doSomething(); // My name is Lee
    
