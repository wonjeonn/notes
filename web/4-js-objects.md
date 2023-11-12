# Week 4: Objects in JavaScript

## Objects

An **object** is a data structure consisting of key-value pairs known as properties. Objects serve as dynamic containers for data, with each key being a unique string that can have properties added or removed at any time. Objects are created using **object literals** enclosed in curly braces `{}`.

```javascript
// An empty object
let o = {};

// A "person" object with a "name" property
let person = { name: 'John Doe' };

// A "campus" object with multiple properties
let campus = {
    name: 'MyCampus',
    lat: 43.1234,
    lng: -78.5678
};

// A "menu" object with lists of items for different meals
let menu = {
    breakfast: ['eggs', 'toast', 'banana', 'coffee'],
    lunch: ['salad', 'chicken', 'apple', 'milk'],
    dinner: ['salmon', 'rice', 'green beans']
};
```

### Accessing Properties

- Object properties can be accessed using the **dot operator** (e.g., `object.property`) or the **bracket operator** (e.g., `object['property']`). The dot operator is commonly used, while the bracket operator is useful for dynamic property names or reserved keywords.

```javascript
let person = { name: 'John Doe' };

// Access the "name" property using the dot operator
console.log(person.name);

// Access the "name" property using the bracket operator
console.log(person['name']);
```

### Destructuring Objects

- Destructuring allows the extraction of object properties into separate variables.

```javascript
let user = {
    name: 'Alice',
    age: 30,
    email: 'alice@example.com'
};

// Destructure the "name" and "age" properties
let { name, age } = user;
```

### Modifying Object Properties

- Properties can be added, updated or removed from objects. Care should be taken when accessing non-existent properties to avoid errors.


```javascript
let data = {};

data.score = 17;
data.level = 3;
data.health = '***';

let currentScore = data.score;  // Accessing the "score" property
let inventory = data.inventory; // Accessing a "inventory" property (which does not exist)
```

### Using Objects for Optional Parameters

- Instead of dealing with numerous arguments, an options object can be used, which may contain function parameters.

```javascript
function initializeGame(options = {}) {
    let score = options.score || 0;
    let level = options.level || 1;
    let inventory = options.inventory || [];

    // Start the game with the specified values
    startGame(score, level, inventory);
}

let gameOptions = {
    score: 25,
    level: 2
};
initializeGame(gameOptions);
```

### Constructor Functions

- Constructor functions allow the creation of multiple objects with the same structure. The `new` keyword is used to create object instances.

```javascript
function User(id, name) {
    this.id = id;
    this.name = name;
}

let user1 = new User(1, 'Alice');
let user2 = new User(2, 'Bob');
```

### Object Prototypes

- Objects in JavaScript have prototypes, which are objects to which the object's `.prototype` property points. JavaScript first looks for properties on the object itself and then in the prototype chain.

### JavaScript's `class` Keyword

- The`class` keyword for defining classes in an object-oriented programming (OOP) style. Classes can inherit from others and define methods.

Example:

```javascript
class User {
    constructor(id, name) {
        this.id = id;
        this.name = name;
    }

    toString() {
        return `${this.name} (#${this.id})`;
    }
}

class Student extends User {
    constructor(id, name, email) {
        super(id, name);
        this.email = email;
    }

    toString() {
        return `"${this.name}" <${this.email}>`;
    }
}

let student = new Student(1, 'Carol', 'carol@example.com');
```

## Practice Problem
### Morse Code Translator

- Define Morse code mappings for the alphabet and symbols using objects.

```javascript
let morseCode = {
    'A': '.-',
    'B': '-...',
    // ... (continue with other letters)
    ' ': '/',
};
```

- Create a `Message` class to represent messages in Morse code or alphabetic characters. This class should translate messages based on their content.

```javascript
class Message {
    constructor(text) {
        // code to initialize the message
    }

    toMorse() {
        // code to translate the message to Morse code
    }

    toAlpha() {
        // code to translate the message to alphabetic characters
    }
}

let msg1 = new Message('HELLO WORLD');
console.log(msg1.toMorse()); // translates and prints the message in Morse code
console.log(msg1.toAlpha()); // prints the original message

let msg2 = new Message('-- --- .-. ... ./-.-. --- -.. .');
console.log(msg2.toAlpha()); // translates and prints the message in alphabetic characters
console.log(msg2.toMorse()); // prints the original message in Morse code
```
