# Type script

<li>Microsoft에서 version 0.8 (October, 2012)릴리즈 되어었으며 version 1.0 (February, 2014)에 릴리즈</li>
<li>처음에는 Visual Studio를 지원하였으나 2013년 부터 다른 IDE를 지원하기 시작</li>
<li>July, 2014에 새로운 TypeScript 컴파일러 발표와 함께 소스코드를 GitHub로 이전.</li>
<li>ECMAScript 2015 support</li>

## Why Type Script?

>We love TypeScript for many things… With TypeScript, several of our team members have said things like I now actually understand most of our own code! because they can easily traverse it and understand relationships much better. And we’ve found several bugs via TypeScript’s checks.”
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
notSure.toFixed(); // okay, toFixed exists (but the compiler doesn`t check)

// error occurs when it compilation
let prettySure: Object = 4;
prettySure.toFixed(); // Error: Property `toFixed` doesn`t exist on type `Object`.
```
> opt-in : 정보를 이용하기 이전에 미리 동의를 얻어야 한다는 것  
> opt-out : 동의 절차가 없이 일단 이용자의 정보를 처리하는 것

다른 타입과 함께 사용하여 전혀다른 타입으로 사용가능.  
(단, 모든 타입과 함께 사용할 수 있는 것은 아님.)
```JavaScript
let list: any[] = [1, true, "free"];

list[1] = 100;
```

### Void
`any` 와 유사하며, 그 어떤 타입도 갖고 있지 않는 상태.  
주로 return 값을 갖지 않는 function 을 정의할 때 사용.
```JavaScript
function warnUser(): void {
    alert("This is my warning message");
}
```

### Null And Undefined

when using the `--strictNullChecks` flag, `null` and `undefined` are only assignable to void and their respective types. This helps avoid many common errors. In cases where you want to pass in either a `string` or `null` or `undefined`

>As a note: we encourage the use of --strictNullChecks when possible, but for the purposes of this handbook, we will assume it is turned off.  

without --strictNullChecks option.
```JavaScript
let m: Object = undefined; // ok
let n: Object = null; // ok
```
with --strictNullChecks option.
```JavaScript
let m: Object = undefined; // Any.ts(15,5): error TS2322: Type `undefined` is not assignable to type `Object`.
let n: Object = null; // Any.ts(16,5): error TS2322: Type `null` is not assignable to type `Object`.
```

### Never
The `Never` type represents the type of values that never occur.

```JavaScript
// Function returning never must have unreachable end point
function error(message: string): never {
    throw new Error(message);
}

// Inferred return type is never
function fail() {
    return error("Something failed");
}

// Function returning never must have unreachable end point
function infiniteLoop(): never {
    while (true) {
    }
}
```

### Type Assertions

Type assertions are a way to tell the compiler “trust me, I know what I’m doing.” A type assertion is like a type cast in other languages, but performs no special checking or restructuring of data. It has no runtime impact, and is used purely by the compiler.

Type assertions have two forms. One is the “angle-bracket” syntax:

```Javascript
let someValue: any = "this is a string";

let strLength: number = (<string>someValue).length;
```
And the other is the as-syntax:

```JavaScript
let someValue: any = "this is a string";

let strLength: number = (someValue as string).length;
```

The two samples are equivalent. Using one over the other is mostly a choice of preference; however, when using TypeScript with JSX, only `as-style` assertions are allowed.


## Variable Declarations
[see - Chapter 16. Variables: Scopes, Environments, and Closures](http://speakingjs.com/es5/ch16.html)

### Background
#### Static and Dynamic
<li>statically(or lexically)</li>

```JavaScript
// 'f' function 내부에 'g' function을 정적으로 선언.
function f(){
    function g(){

    }
}
```

> lexical (= static)

<li>Dynamically</li>

```JavaScript
// 'f' function 호출 시 'g' function이 동적으로 연결됨.
function g(){

}

function f(){
    g();
}
```
#### The Scope of a Variable
<li>The scope of a variable</li>

```JavaScript
// 변수 'x'의 `direct scope`는 function 'f'
function f(){
    var x;
}
```
<li>Lexical scoping</li>

JavaScript의 변수는 `lexical scope` 방식으로 할당.  

> lexical scope (= static scope) - In languages with lexical scope (also called static scope), name resolution depends on the location in the source code and the lexical context, which is defined by where the named variable or function is defined.

<li>Nested scopes</li>

```JavaScript
function a(arg){
    function b(){
        console.log('arg' + arg);
    }
    b();
}
console.log(a('hello'));
```
변수 `arg`는 function 'a'의 scope이지만 function 'b' 에서 참조 가능.  
Nested scope에서 function 'b'의 scope은 `inner scope` 이고 function 'a'의 scope을 `outer scope`  

nested scoping  
![nested scoping](http://speakingjs.com/es5/images/spjs_2001.png)

<li>Shadowing</li>

```JavaScript
var x = "global";
function f() {
    var x = "local";
    console.log(x); // local
};
f();
console.log(x); // global
```
function 'f' 에서 global 변수 x는 local 변수 x에 의해 shadowing됨.
즉, 여러 scope에 동일한 변수 명이 존재할 경우(inner scope와 그것의 nested scope) outer scope의 변수 블록됨.  
또한, inner scope 의 변수는 outer scope의 변수에 아무런 영향을 끼치지 않음.

#### Variables Are Function-Scoped
Javascript의 변수는 `function scope`을 사용.
이와 반대로 TypeScript의 let변수는 `block scope`를 사용.

#### Variable Declarations Are Hoisted
Javascript의 변수 선언은 `hoist`방식을 따름.


### Variable Declarations
`let` and `const` are two relatively new types of variable declarations in JavaScript. As we mentioned earlier, `let` is similar to `var` in some respects, but allows users to avoid some of the common “gotchas” that users run into in JavaScript. `const` is an augmentation of `let` in that it prevents re-assignment to a variable.

#### var declarations
Declaring a variable in JavaScript has always traditionally been done with the var keyword.
```JavaScript
var a = 10;
```
As you might’ve figured out, we just declared a variable named a with the value 10.

We can also declare a variable inside of a function:

```JavaScript
function f() {
    var message = "Hello, world!";

    return message;
}
return b;
```
and we can also access those same variables within other functions:

```JavaScript
function f() {
    var a = 10;
    return function g() {
        var b = a + 1;
    }
}

var g = f();
g(); // returns '11'
```

In this above example, g captured the variable a declared in f. At any point that g gets called, the value of a will be tied to the value of a in f. Even if g is called once f is done running, it will be able to access and modify a.

```JavaScript
function f() {
    var a = 1;

    a = 2;
    var b = g();
    a = 3;

    return b;

    function g() {
        return a;
    }
}

f(); // returns '2'
```

##### Scoping rules

`var` declarations have some odd scoping rules for those used to other languages. Take the following example:
```JavaScript
function f(shouldInitialize: boolean) {
    if (shouldInitialize) {
        var x = 10;
    }

    return x;
}

f(true);  // returns '10'
f(false); // returns 'undefined'
```

##### Variable capturing quirks

Take a quick second to guess what the output of the following snippet is:
```JavaScript
for (var i = 0; i < 10; i++) {
    setTimeout(function() { console.log(i); }, 100 * i);
}
```

Let’s take a minute to consider what that means. setTimeout will run a function after some number of milliseconds, but only after the for loop has stopped executing.


A common work around is to use an [IIFE](http://chanlee.github.io/2014/01/11/understand-javascript-iife/) - an Immediately Invoked Function Expression - to capture i at each iteration:
```JavaScript
for (var i = 0; i < 10; i++) {
    // capture the current state of 'i'
    // by invoking a function with its current value
    (function(i) {
        setTimeout(function() { console.log(i); }, 100 * i);
    })(i);
}
```

#### let declarations

By now you’ve figured out that `var` has some problems, which is precisely why `let` statements were introduced. Apart from the keyword used, `let` statements are written the same way `var` statements are.
```JavaScript
let hello = "Hello!";
```

##### Block Scoping
When a variable is declared using `let`, it uses what some call `lexical-scoping` or `block-scoping`. Unlike variables declared with `var` whose scopes leak out to their containing function, block-scoped variables are not visible outside of their nearest containing block or for-loop.

```JavaScript
function f(shouldInitialize: boolean) {
    if (shouldInitialize) {
        //var x = 10      // ok
        let x = 10;
    }
    return x; // test.ts(5,12): error TS2304: Cannot find name 'x'.
}
```

```JavaScript
a++; // illegal to use 'a' before it's declared;
let a;
```

##### Re-declarations and Shadowing
With `var` declarations, we mentioned that it didn’t matter how many times you declared your variables; you just got one.
```JavaScript
function f(x) {
    var x;
    var x;

    if (true) {
        var x;
    }
}
```
In the above example, all declarations of x actually refer to the same x, and this is perfectly valid. This often ends up being a source of bugs. Thankfully, let declarations are not as forgiving.
```JavaScript
let x = 10;
let x = 20; // error: can't re-declare 'x' in the same scope
```
The variables don’t necessarily need to both be block-scoped for TypeScript to tell us that there’s a problem.
```JavaScript
function f(x) {
    let x = 100; // error: interferes with parameter declaration
}

function g() {
    let x = 100;
    var x = 100; // error: can't have both declarations of 'x'
}
```
That’s not to say that block-scoped variable can never be declared with a function-scoped variable. The block-scoped variable just needs to be declared within a distinctly different block.
```JavaScript
function f(condition, x) {
    if (condition) {
        let x = 100;
        return x;
    }

    return x;
}

f(false, 0); // returns '0'
f(true, 0);  // returns '100'
```
The act of introducing a new name in a more nested scope is called shadowing. It is a bit of a double-edged sword in that it can introduce certain bugs on its own in the event of accidental shadowing, while also preventing certain bugs. For instance, imagine we had written our earlier sumMatrix function using let variables.
```JavaScript
function sumMatrix(matrix: number[][]) {
    let sum = 0;
    for (let i = 0; i < matrix.length; i++) {
        var currentRow = matrix[i];
        for (let i = 0; i < currentRow.length; i++) {
            sum += currentRow[i];
        }
    }

    return sum;
}
```

##### Block-scoped variable capturing

When we first touched on the idea of variable capturing with var declaration, we briefly went into how variables act once captured. To give a better intuition of this, each time a scope is run, it creates an “environment” of variables. That environment and its captured variables can exist even after everything within its scope has finished executing.
```JavaScript
function theCityThatAlwaysSleeps() {
    let getCity;

    if (true) {
        let city = "Seattle";
        getCity = function() {
            return city;
        }
    }

    return getCity();
}
```
Because we’ve captured city from within its environment, we’re still able to access it despite the fact that the if block finished executing.

Recall that with our earlier setTimeout example, we ended up needing to use an IIFE to capture the state of a variable for every iteration of the for loop. In effect, what we were doing was creating a new variable environment for our captured variables. That was a bit of a pain, but luckily, you’ll never have to do that again in TypeScript.

let declarations have drastically different behavior when declared as part of a loop. Rather than just introducing a new environment to the loop itself, these declarations sort of create a new scope per iteration. Since this is what we were doing anyway with our IIFE, we can change our old setTimeout example to just use a let declaration.
```JavaScript
for (let i = 0; i < 10 ; i++) {
    setTimeout(function() { console.log(i); }, 100 * i);
}
```

## Functions
### Function Types
#### Typing the function

Let’s add types to our simple examples from earlier:

```JavaScript
function add(x: number, y: number): number {
    return x + y;
}

let myAdd = function(x: number, y: number): number { return x+y; };
```

We can add types to each of the parameters and then to the function itself to add a return type. TypeScript can figure the return type out by looking at the return statements, so we can also optionally leave this off in many cases.

#### Writing the function type

Now that we’ve typed the function, let’s write the full type of the function out by looking at the each piece of the function type.

```JavaScript
let myAdd: (x: number, y: number)=>number =
    function(x: number, y: number): number { return x+y; };
```

`function type`을 정의하기위해서 두 가지가 필요하다.  
첫번째. 파라메터의 변수명과 타입을 기술. 단, 변수이름을 가독성을 돕기위한 것이며 동일할 필요는 없음.
두번째. 리턴 타입을 기술 => .  

```JavaScript
let myAdd: (baseValue:number, increment:number) => number =
    function(x: number, y: number): number { return x + y; };
```

### this and arrow functions

일반 function 은 invoke 되는 시점에서 변수를 캡처.
Arrow function 은 define 되는 시점에서 변수를 캡처. 

```JavaScript

let deck = {
    suits: ["hearts", "spades", "clubs", "diamonds"],
    cards: Array(52),
    createCardPicker: function() {
        return function() {
            let pickedCard = Math.floor(Math.random() * 52);
            let pickedSuit = Math.floor(pickedCard / 13);

            return {suit: this.suits[pickedSuit], card: pickedCard % 13};
        }
    }
}

let cardPicker = deck.createCardPicker();
let pickedCard = cardPicker();

alert("card: " + pickedCard.card + " of " + pickedCard.suit);
```

Notice that createCardPicker is a function that itself returns a function. If we tried to run the example, we would get an error instead of the expected alert box. This is because the this being used in the function created by createCardPicker will be set to window instead of our deck object. That’s because we call cardPicker() on its own. A top-level non-method syntax call like this will use window for this. (Note: under strict mode, this will be undefined rather than window).

We can fix this by making sure the function is bound to the correct this before we return the function to be used later. This way, regardless of how it’s later used, it will still be able to see the original deck object. To do this, we change the function expression to use the ECMAScript 6 arrow syntax. Arrow functions capture the this where the function is created rather than where it is invoked:

```JavaScript
let deck = {
    suits: ["hearts", "spades", "clubs", "diamonds"],
    cards: Array(52),
    createCardPicker: function() {
        // NOTE: the line below is now an arrow function, allowing us to capture 'this' right here
        return () => {
            let pickedCard = Math.floor(Math.random() * 52);
            let pickedSuit = Math.floor(pickedCard / 13);

            return {suit: this.suits[pickedSuit], card: pickedCard % 13};
        }
    }
}

let cardPicker = deck.createCardPicker();
let pickedCard = cardPicker();

alert("card: " + pickedCard.card + " of " + pickedCard.suit);

```

Even better, TypeScript will warn you when you make this mistake if you pass the --noImplicitThis flag to the compiler. It will point out that this in this.suits[pickedSuit] is of type any
