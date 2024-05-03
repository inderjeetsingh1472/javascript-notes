# JavaScript Notes

## Basics

### Variables:-
-Variables are symbolic names that represent values stored in computer memory.<br>
-In JavaScript, there are three keywords used to declare variables: var, let, and const.<br>
1. Var:-<br>

• <u>Function Scope or Global Scope</u>: Variables declared with var have function scope if declared inside a function. If declared outside any function, they become global variables.
```javascript
var globalVar = "I'm a global variable";

function example() {
    var localVar = "I'm a local variable";
    console.log(localVar); // Outputs: I'm a local variable
}

example();
console.log(globalVar); // Outputs: I'm a global variable
```

• <u>Hoisting</u>: Variables declared with var are hoisted to the top of their containing function or script. This means they can be accessed before their actual declaration.
``` javascript
console.log(inder); // Outputs: undefined
var inder = "I've been hoisted!";
console.log(inder); // Outputs: I've been hoisted!
```

• <u>No Block Scope</u>: Unlike let and const, variables declared with var do not have block scope. They are accessible throughout the function in which they are declared, regardless of block boundaries.
``` javascript
function example() {
    if (true) {
        var localVar = "I'm a local variable within a block";
    }
    console.log(localVar); // Outputs: I'm a local variable within a block
}

example();
```

• <u>Reassignment and Redefinition</u>: Variables declared with var can be both redeclared and reassigned within the same scope without throwing errors. This can lead to unintended consequences and difficult-to-trace bugs.
```javascript
var myVar = "Original value";
console.log(myVar); // Outputs: Original value

var myVar = "Redeclared with var";
console.log(myVar); // Outputs: Redeclared with var

myVar = "Reassigned";
console.log(myVar); // Outputs: Reassigned
```
2. Let :- <br>
• <u>Block Scope:</u> Variables declared with let have block scope, meaning they are limited in visibility to the block, statement, or expression they are declared in.<br>
```javascript
function example() {
    if (true) {
        let localVar = "I'm a local variable within a block";
        console.log(localVar); // Outputs: I'm a local variable within a block
    }
    console.log(localVar); // Error: localVar is not defined
}

example();
```
• <u>No Hoisting:</u> Unlike variables declared with var, variables declared with let are not hoisted to the top of their containing block. They are only accessible after the declaration point.<br>
```javascript
console.log(myVar); // Error: Cannot access 'myVar' before initialization
let myVar = "I'm not hoisted!";
```
• <u>Cannot be Redeclared:</u> Variables declared with let cannot be redeclared within the same block scope. Attempting to do so will result in a SyntaxError.<br>
```javascript
let x = 10;
let x = 20; // Error: Identifier 'x' has already been declared
```
• <u>Can be Reassigned:</u> Variables declared with let can be reassigned new values within the same block scope. However, they retain block scope and cannot be accessed outside of it.<br>
```javascript
let y = 10;
y = 20; // Valid, reassigning the value of y
console.log(y); // Outputs: 20
```

3. Const :-<br>
• <u>Constant Value:</u> Variables declared with const are constants, meaning their values cannot be reassigned once they are initialized.<br>
```javascript
const PI = 3.14;
PI = 3.14159; // Error: Assignment to constant variable
```
• <u>Block Scope:</u> Like let, variables declared with const have block scope, meaning they are limited in visibility to the block, statement, or expression they are declared in.<br>
```javascript
if (true) {
    const localVar = "I'm a local constant within a block";
    console.log(localVar); // Outputs: I'm a local constant within a block
}
console.log(localVar); // Error: localVar is not defined
```
• <u>No Hoisting:</u> Similar to let, variables declared with const are not hoisted to the top of their containing block. They are only accessible after the declaration point.<br>
```javascript
console.log(myConst); // Error: Cannot access 'myConst' before initialization
const myConst = "I'm not hoisted!";
```
• <u>Must be Initialized:</u> Variables declared with const must be initialized with a value at the time of declaration. Attempting to declare a const variable without initialization will result in a SyntaxError.<br>
```javascript
const myConst; // Error: Missing initializer in const declaration
```
• <u>Cannot be Redeclared:</u> 
```javascript
const x = 10;
const x = 20; // Error: Identifier 'x' has already been declared
```
•<u>Cannot be Reinitialized:</u>
```javascript
const y = 10;
y = 20; // Error: Assignment to constant variable
```




***

### Data Types:-<br>
1. **<u>Primmitive data types</u>**:-*Primitive data types are those fundamental data types that cannot rely on or be composed of other data types. They stand on their own and are the building blocks for more complex data structures.<br>*

**• <u>Boolean</u>**:-*Represents a binary value, either true or false. It's commonly used for logical operations and conditions.*
```javascript

let isLoggedIn = "inder"

let booleanIsLoggedIn = Boolean(isLoggedIn)
 console.log(booleanIsLoggedIn);//output:true

//note:-(argument=>output)
 1 => true; 0 => false
 "" => false
 "inder" => true

 //typeof operator is used to find type of data type:-
 console.log(typeof(booleanIsLoggedIn))//output:boolean

```
**• <u>Number</u>**:- *Represents numeric data, including integers and floating-point numbers.<br>*
```javascript
let score='inder'
let valueInNumber = Number(score)
console.log(typeof valueInNumber);//output:number
console.log(valueInNumber);//output: NAN (stands for not a number)

// if score =
"33" => 33(output)
"33abc" => NaN(output)
 true => 1(output); false => 0(output)
```
**<u>• String</u>:-** *Represents textual data enclosed within single or double quotes.*
```javascript
let name = "inderjeet Singh";
let address = 'vill:golewala';
console.log(typeof name,typeof adress)//output:string string

let someNumber = 33
let stringNumber = String(someNumber)
console.log(stringNumber);//33
console.log(typeof stringNumber);//string
console.log(typeof someNumber);//number

```
**<u>• Undefined</u>:-**
*Represents a variable that has been declared but not assigned a value.*
```javascript
let inder;
console.log(typeof inder)//undefined

console.log(typeof undefined); // undefined
```
**<u>• null</u>:-**
 *Represents the absence of any value.*
 ```javascript

 let phoneNumber = null;
 console.log(typeof phoneNumber)//object

 console.log(phoneNumber)//null

 ```
 **<u>• Symbol</u>:-**
 *Represents a unique identifier introduced in ECMAScript 6 (ES6).*
 ```javascript

 let id = Symbol('uniqueId');
 const id = Symbol('123')
const anotherId = Symbol('123')
console.log(id === anotherId);//false
console.log(typeof id);//symbol

console.log(id);//Symbol('123')
console.log(anotherId);//Symbol('123')

 ```
 **<u>• Bigint</u>:-**
 *Represents integers of arbitrary precision, allowing for working with very large numbers beyond the safe integer limit of regular numbers.*
 ```javascript

 const bigNumber = 9007199254740991n;//note- use n after ending

 ```

### Operators

- Control Structures

## Advanced

- Functions
- Arrays
- Objects
- Classes

## Tips and Tricks

- Debugging
- Best Practices
- Common Mistakes
- Useful Resources
