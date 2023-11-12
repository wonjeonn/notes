# Week 3: JavaScript Built-in Objects String, Array, RegExp

## Strings in JavaScript

```javascript
let s = 'some text';  // single-quotes
let s1 = "some text"; // double-quotes
let s2 = `some text`; // template literal using back-ticks
let unicode = "中文 español Deutsch English देवनागरी العربية português বাংলা русский 日本語 ਪੰਜਾਬੀ 한국어 தமிழ் עברית"; // non-ASCII characters

let s3 = new String("Some Text");
let s4 = new String('Some Text');
```

Converting other types to strings:

```javascript
let x = 17;
let s = '' + x;        // concatenate with a string (the empty string)
let s2 = String(x);    // convert to String
let s3 = x.toString(); // use a type's .toString() method
```

### String Properties and Methods

- `s.length`: Length of the string (UTF-16 code units).
- `s.charAt(1)`: Returns the character at the given position.
- `s.concat()`: Concatenates the original string with given arguments.
- `s.padStart(2, '0')`: Pads the string with the given substring until the length meets the minimum length given.
- `s.includes("tex")`: Returns true if the search string is found within the string.
- `s.startsWith("some")`: Returns true if the string starts with the given substring.
- `s.endsWith("text")`: Returns true if the string ends with the given substring.
- `s.indexOf("t")`: Returns the first index position of the given substring within `s` or -1 if not found.
- `s.match(regex)`: Tries to match a regular expression against the string, returning the matches.
- `s.replace(regex, "replacement")`: Returns a new string with the first occurrence of a matched RegExp replaced by the replacement text.
- `s.slice(2, 3)`: Returns a new string extracted from within the original string.
- `s.split()`: Returns an Array of substrings by splitting the original string based on the given separator.
- `s.toLowerCase()`: Returns a new string with all characters converted to lower case.
- `s.toUpperCase()`: Returns a new string with all characters converted to upper case.
- `s.trim()`: Returns a new string with leading and trailing whitespace removed.

### Array in JavaScript

Declaring Arrays:

```javascript
let arr = new Array(1, 2, 3); // array constructor
let arr2 = [1, 2, 3]; // array literal
```

Accessing Elements:

```javascript
let arr = [1, 2, 3];
let len = arr.length; // len is 3
let item0 = arr[0]; // item0 is 1
```

Array Methods:

- `arr.push(element)`: Adds element(s) to the end of the array.
- `arr.pop()`: Removes the last element and returns it.
- `arr.concat([4, 5], 6)`: Returns a new array with the original array joined together with other arrays or values provided.
- `arr.includes(element)`: Returns true if the array includes the given element, otherwise false.
- `arr.indexOf(element)`: Returns the index of the given element in the array or -1 if not found.
- `arr.join("\n")`: Returns a string created by joining all elements in the array with the given delimiter.
- `arr.forEach()`: Calls the provided function on each element in the array.
- `arr.map()`: Creates and returns a new array constructed by calling the provided function on each element of the original array.
- `arr.find()`: Finds and returns an element from the array which matches a condition is defined.
- `arr.filter()`: Creates and returns a new array containing only those elements that match a condition is defined.
- `arr.every()`: Returns true if all elements in the array meet a condition is defined.

### Iterating over Strings and Arrays

```javascript
let s = 'Hello World!';
for (let char of s) {
    console.log(char);
}

let arr = [10, 20, 30, 40];
for (let elem of arr) {
    console.log(elem);
}
```

### Regular Expressions (RegExp)

Regular expressions are patterns used for matching or searching within strings.

#### Character Matching and Repetition

- `?`: Matches something once or none.
- `*`: Matches zero or more occurrences.
- `+`: Matches one or more occurrences.
- `{n}`: Matches exactly n times.
- `{n,}`: Matches at least n times.
- `{n,m}`: Matches at least n times and no more than m times.

#### Positional Match Parameters and Alternatives

- `^`: Matches at the beginning of the input string.
- `$`: Matches at the end of the string.
- `|`: Matches one of several patterns (alternative).

#### Using RegExp with Strings

- `RegExp.test(string)`: Tests whether the string matches the pattern.
- `String.match(regexp)`: Finds all matches of the RegExp in the source string.
- `String.replace(regexp, replacement)`: Replaces all matches for the given RegExp.
- `String.split(RegExp)`: Breaks the string into an array of substrings based on the RegExp pattern.
