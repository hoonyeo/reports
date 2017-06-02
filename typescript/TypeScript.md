# Type script

<li>Microsoft에서 version 0.8 (October, 2012)릴리즈 되어었으며 version 1.0 (February, 2014)에 릴리즈</li>
<li>처음에는 Visual Studio를 지원하였으나 2013년 부터 다른 IDE를 지원하기 시작</li>
<li>July, 2014에 새로운 TypeScript 컴파일러 발표와 함께 소스코드를 GitHub로 이전.</li>
<li>ECMAScript 2015 support</li>

## Why Type Script?

>We love TypeScript for many things… With TypeScript, several of our team members have said things like 'I now actually understand most of our own code!' because they can easily traverse it and understand relationships much better. And we’ve found several bugs via TypeScript’s checks.”
>
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;— Brad Green, Engineering Director - AngularJS  
>
>“One of Ionic's main goals is to make app development as quick and easy as possible, and the tooling support TypeScript gives us with autocompletion, type checking and source documentation really aligns with that.”
>
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;— Tim Lancina, Tooling Developer - Ionic


## Basic Types

[see link - Typescript Basic types.](https://www.typescriptlang.org/docs/handbook/basic-types.html)

### Boolean ... String
omitted
### Tuple
Tuple types allow you to express an array where the type of a fixed number of elements is known, but need not be the same.
```JavaScript
// Declare a tuple type
let x: [string, number];
// Initialize it
x = ["hello", 10]; // OK
// Initialize it incorrectly
x = [10, "hello"]; // Error
```

### Enum
An enum is a way of giving more friendly names to sets of numeric values.
```JavaScript
enum Color {Red, Green, Blue}
let c: Color = Color.Green;
```

### Any
어플리케이션을 작성하는 단계에서는 알 수 없는 타입을 정의할때 사용.  
실제 인스턴스 또는 값이 할당될 때 동적으로 타입이 결정됨.
```JavaScript
let test: any = 1;
console.log(typeof (test)); //number
test = "stirng instead";
console.log(typeof (test)); //string
test = new Object();
console.log(typeof (test)); //object
```
기존 JavaScript로 작업 할 수있는 강력한 방법으로 컴파일하는 동안 점진적으로 유형 확인을 opt-in하거나 opt-out 가능.
```JavaScript
let notSure: any = 4;
notSure.ifItExists(); // okay, ifItExists might exist at runtime
notSure.toFixed(); // okay, toFixed exists (but the compiler doesn't check)

// error occurs when it compilation
let prettySure: Object = 4;
prettySure.toFixed(); // Error: Property 'toFixed' doesn't exist on type 'Object'.
```
> opt-in : 정보를 이용하기 이전에 미리 동의를 얻어야 한다는 것
> opt-out : 동의 절차가 없이 일단 이용자의 정보를 처리하는 것

다른 타입과 함께 사용하여 전혀다른 타입으로 사용가능.  
(단, 모든 타입과 함께 사용할 수 있는 것은 아님.)
```JavaScript
let list: any[] = [1, true, "free"];

list[1] = 100;
```
