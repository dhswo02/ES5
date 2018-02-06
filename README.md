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
    
#### 기본 자료형(Primitive Data Type)
> 기본 자료형의 값은 변경 불가능한 값이며 pss-by-value(값으로 접근) 이다. 또한 이들 값은 메모리의 스택 영역(Stack Segment)에 고정된 메모리 영역을 점유하고 저장된다.

#### 객체형(Object type, 참조형)
> 객체는 데이터와 그 데이터에 관련되는 동작(절차,방법,기능)을 모두 포함할 수 있는 개념적 존재이다. 달리 말해, 이름과 값을 가지는 데이터를 의미하는 프로퍼티(property)와 동작을 의미하는 메소드(method)를 포함할 수 있는 독립적 주체이다.

> 자바스크립트는 객체(object)기반의 스크립트 언어로서 자바스크립트를 이루고 있는 거의 “모든 것”이 객체이다. 기본자료형(Primitives)을 제외한 나머지 값들(배열, 함수, 정규표현식 등)은 모두 객체이다. 또한 객체는 pass-by-reference(참조로 접근)이며 메모리의 힙 영역(Heap Segment)에 저장된다.

   
 


   