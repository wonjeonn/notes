# Week 2: JavaScript Functions, Built-ins/Globals, Scope and Closures

## Functions

A function in JavaScript is a subprogram that can be invoked by other parts of the program, other functions or in response to actions. Functions can take arguments and may return values.

### Function Declarations

```javascript
function noop() {
  // Empty function
}

function square(n) {
  return n * n;
}

function add(a, b) {
  return a + b;
}
```

### Function Expressions

```javascript
let noop = function() {
  // Empty function
};

let square = function(n) {
  return n * n;
};

let add = function(a, b) {
  return a + b;
};
```

### Arrow Functions (ES6)

```javascript
let noop = () => {
  // Empty function
};

let square = n => n * n;

let add = (a, b) => a + b;
```

### Parameters and Arguments

- Functions can accept any number of arguments, including none and access arguments using the "arguments" object.

```javascript
function log(a) {
  console.log(a);
}

log("correct");          // logs "correct"
log("also", "correct");  // logs "also"
log();                   // logs undefined
```

### Rest Parameters (ES6)

- Rest parameters allow specifying that all final arguments should be available as an array.

```javascript
function sum(...numbers) {
  let total = 0;
  for (let i = 0; i < numbers.length; i++) {
    total += numbers[i];
  }
  return total;
}

sum(1);          // 1
sum(1, 2);       // 3
sum(1, 2, 3, 4); // 10
```

### Default Parameters (ES6)

- Default parameters can specify values when declaring functions.

```javascript
function updateScore(currentScore, value, bonus = 1) {
  return currentScore + value * bonus;
}
```

### Return Value

- Functions in JavaScript always return a value, either explicitly or implicitly. If "return" is omitted, the function returns "undefined."

```javascript
function explicitReturn() {
  return 1;
}

function explicitReturn2() {
  return "Hello" + " World!";
}
```

## Function Naming

Functions are named using camelCase and the names should avoid using reserved keywords.

## Scope

- JavaScript variables can be declared using "var" (historical) or "let" and "const" (modern).
- "var" has function scope.
- "let" and "const" have block scope.
- Nested functions can access variables in their parent's scope.

```javascript
var x = 7;

function parent() {
  var x = 2;

  function child() {
    return x * 2;
  }

  return child();
}
```

## Closures

A closure is a function that retains access to variables in its outer scope even after that scope has exited.

```javascript
function createAccumulator(value) {
  return function(n) {
    value += n;
    return value;
  };
}

var add = createAccumulator(10);
add(1); // returns 11
add(2); // returns 13
```
