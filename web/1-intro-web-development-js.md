# Week 1: Introduction to Web Development with JavaScript

## Preface

- Web development encompasses various languages, libraries, frameworks and tools.
- The fundamental unit of the web is the hyperlink, enabling web interconnectedness.

## Internet Architecture

- The Internet relies on communication protocols like IP (IPv4 and IPv6), domain names, DNS, HTTP and HTTPS.
- The World Wide Web (WWW) operates on the Internet using HTTP.
- The web is shaped by open standards such as HTML, HTTP and SVG.

## HTTP Requests and Responses

- HTTP follows a client-server model for sending requests and receiving responses.

```javascript
// Sending an HTTP request
const request = new XMLHttpRequest();
request.open('GET', 'https://example.com/api/data', true);
request.send();

// Handling an HTTP response
request.onreadystatechange = function () {
  if (request.readyState === 4 && request.status === 200) {
    const response = request.responseText;
    // Process the response data
  }
};
```

## Web Browsers

- Web browsers serve as the operating system for the web, implementing web standards like HTTP and DNS.

## Front-End Web Development: HTML5, CSS, JavaScript and Friends

- Front-end web development revolves around HTML5, CSS, JavaScript and related technologies.

```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
  <h1>Hello, World!</h1>
  <p>This is an example HTML page.</p>
  <script>
    // JavaScript
    const message = 'Welcome to web development!';
    alert(message);
  </script>
</body>
</html>
```

## Introduction to JavaScript

```javascript
// Declaring variables in JavaScript
let a = 10;
let b = 5;

// Basic arithmetic operations
let sum = a + b;  // sum is now 15
let product = a * b;  // product is now 50

// JavaScript supports string concatenation
let greeting = 'Hello, ';
let name = 'John';
let welcomeMessage = greeting + name;  // welcomeMessage is "Hello, John"
```

JavaScript statements can be stored in an external file with a .js file extension or embedded within HTML code via the HTML `<script>` element.

```javascript
// JavaScript code in an external file (script.js)
function sayHello() {
  alert('Hello from an external script!');
}

// HTML file
<!DOCTYPE html>
<html>
<head>
  <script src="script.js"></script>
</head>
<body>
  <button onclick="sayHello()">Click me</button>
</body>
</html>
```

## Common JavaScript Concepts

- JavaScript is case-sensitive; for example, `customerCount` and `CustomerCount` are different.
- It is recommended to use camelCase for naming variables, such as `customerCount`.

```javascript
let customerCount = 10;  // Camel case
```

- Semicolons are optional in JavaScript but highly recommended for code readability.

```javascript
// Using semicolons
let x = 5;
let y = 10;
```

- Single and multi-line comments.

```javascript
// This is a single-line comment

/*
  This is a multi-line comment,
  and can be as long as you need.
*/
```
