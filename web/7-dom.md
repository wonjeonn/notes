# Week 7: From HTML to the DOM

## DOM Tree
- The DOM Tree is a live representation of an HTML page.
- It consists of DOM Nodes, which represent elements, attributes and text within the document.
- Nodes can be elements (HTML tags), text nodes (text content within elements) or attribute nodes (key/value pairs).
- Browsers parse HTML into a DOM Tree structure.

## Programming the DOM

### Interaction with the DOM
- The Document Object Model (DOM) is a programming interface that allows scripts, mainly in JavaScript, to interact with and modify documents, such as HTML and XML.

### Core Tasks with the DOM
1. **Finding Elements**: Locate and get references to elements within the document.
    - Methods: `getElementById(id)`, `querySelector(selectors)` and `querySelectorAll(selectors)` are commonly used.

2. **Creating and Modifying Elements**: Generate new elements and manipulate the DOM.
    - Methods: `createElement(name)`, `createTextNode(text)`, `appendChild(new)`, `insertBefore(new, old)` and `removeChild(child)` are used to add, insert and remove elements.

    ### Adding a New Heading to a Document
    ```javascript
    let newHeading = document.createElement('h2');
    let textNode = document.createTextNode('This is a heading');
    newHeading.appendChild(textNode);
    document.body.appendChild(newHeading);
    ```

    ### Adding New Paragraph Elements to a Div
    ```javascript
    let pElem = document.createElement('p');
    pElem.innerHTML = 'This is a paragraph';
    let demoDiv = document.querySelector('#demo');
    demoDiv.appendChild(pElem);
    ```

3. **Inspecting and Modifying Elements**: Examine and change element properties and content.
    - Properties: `id`, `innerHTML`, `parentNode`, `nextSibling`, `className`, etc.
    - Methods: `querySelector()` and `querySelectorAll()` are used to search within an element.

    ### Adding New Paragraph Elements to a Div
    ```javascript
    let pElem = document.createElement('p');
    pElem.innerHTML = 'This is a paragraph';
    let demoDiv = document.querySelector('#demo');
    demoDiv.appendChild(pElem);
    ```

4. **Running Code in Response to Events**: Execute JavaScript code based on events triggered by users, browsers or other code components.

## Event-Driven Programming

### Event Handling
- Event-driven programming is fundamental in the DOM.
- Events include user actions (clicks, mouse movements), browser actions and timers.
- Event handlers are functions that respond to specific events.
- Two ways to register event handlers: `element.onevent` and `element.addEventListener()`.

    ### Handling Events
    ```javascript
    let saveBtn = document.querySelector('#btn-save');
    saveBtn.onclick = function(e) {
        // Handle the click event
        save();
    };
    ```

### Event Object
- Event handlers often receive an Event Object (usually referred to as `e` or `event`) as an argument.
- The Event Object provides information about the event and allows developers to control its behavior.

    ### Event Handling with Event Object
    ```javascript
    let btn = document.querySelector('#btn');
    btn.addEventListener('click', function(e) {
        e.preventDefault();
        e.stopPropagation();
        btn.innerHTML = 'You clicked Me!';
    });
    ```

### Common Events
- Common DOM events include `load`, `beforeunload`, `focus`, `blur`, `click`, `dblclick`, `contextmenu`, `keypress`, `change`, `mouseout`, `mouseover` and `resize`.
- These events can be handled using either the `element.onevent` property or `addEventListener()` method.

## Timers
- Timers enable scheduling tasks in the future.
- `setTimeout(function, delayMS)` schedules a task to run after a specified delay.
- `setInterval(function, delayMS)` schedules a task to run repeatedly at a specified interval.

    ### Using Timers
    ```javascript
    let currentDate = document.querySelector('#current-date');
    let timerId;

    startButton.onclick = function(e) {
        if (timerId) {
            return;
        }

        currentDate.removeAttribute('hidden');
        timerId = setInterval(function() {
            let now = new Date();
            currentDate.innerHTML = now.toLocaleString();
        }, 1000);
    };

    endButton.onclick = function(e) {
        if (!timerId) {
            return;
        }

        clearInterval(timerId);
        timerId = null;
    };
    ```
