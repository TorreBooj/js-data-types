# Data Types, Variables, and Arrays

<!--WDI5 9:25 -->
<!--9:49 WDI4 -->
<!--9:50 10 minutes -->

<!-- HOOK
  - So one of the big jobs of a computer is to be a calculator.  So let's say I want to get my computer to multiply two big numbers like 24 and 24 together.  How could I do that?
  - Now how about 32 and 32?
  - What are we doing here?  (Squaring) So this is where variables come in.  Instead of writing all these numbers over and over again, the computer can save us time with: var side = 32; side*side;
  - What if I want to make a cube?
-->

### Objectives
*After this lesson, students will be able to:*

- **Describe** the concept of a "data type" and how it relates to variables
- **Describe** use cases of different "data types"
- **Declare**, **assign** to, and **manipulate** data stored in a variable
- **Explore** and **use** a programming or markup language's standard library and built-in functions (iterators, datatype/array methods)
- **Iterate** over and **manipulate** values in an array
- **Describe** how arrays are used to store data

### Preparation
*Before this lesson, students should already be able to:*

- **Describe** briefly what javascript is
- **Be comfortable** with a text editor

<!-- CFU: Fist-to-five? -->

## What is a data type? Intro

From [Wikipedia](https://en.wikipedia.org/wiki/Data_type):


In computer science and computer programming, a data type is a classification identifying one of various types of data that determines: 
* the possible values for that type 
* the operations that can be done on values of that type 
* the meaning of the data and the way values of that type can be stored.

Data types are really similar across many different languages:

| Data Type | Description | Example |
| --- | --- | --- |
| Strings | Single words or sentences, surrounded by double or single quotes | `"lots of kittens"`, `'lots of kittens'` |
| Integers | Whole numbers, with no delimiter. Can optionally have underscores to make large numbers easier to read | `42`, `1024`, `1\_000\_000` |
| Floats | Decimals, with no delimiter | `3.14`, `3.0` |
| Booleans | A binary data type representing true or false | `true`, `false` |

We'll elaborate on all of these - except Booleans - talk about how they differ in JavaScript, show you some built-in methods for each type and then give you time to practice some of the methods to manipulate data.

#### Working with data in JavaScript

From the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Introduction): "JavaScript contains a standard library of objects, such as Array, Date, and Math, and a core set of language elements such as operators, control structures, and statements.... Client-side JavaScript extends the core language by supplying objects to control a browser and its Document Object Model (DOM). For example, client-side extensions allow an application to place elements on an HTML form and respond to user events such as mouse clicks, form input, and page navigation."

<!--9:33 WDI5 -->
<!--ACtually 10:03-->
<!--WDI4 9:55 -->
<!--10:00 <10 minutes-->

<!--Code-along -->

#### What are we working with? Demo

<!--We will cover dev tools in more detail later -->

For this lesson, we're going to use the Chrome Developer Tools Console shell.  Open a Chrome window and type `cmd+alt+j` to open the console.

#### typeof()

To get an idea of the type of data we're working with, we can use [`typeof()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof).  Let's try it out in the console with the following:

```javascript
typeof(37) === 'number';
=> true

typeof({}) === 'object';
=> true

typeof('hi there') === 'string';
=> true

```

<!--Half-mast -->

`typeof()` returns a string with the type of the operand, or expression of the object you're looking at.  

<!--
[CFU]: Show of fingers for number, pull out string for string, hold up laptops for object...what type is...
-"Hello!"
-42
-43.576
-{color: red, size: big}
-'Yellow'
-"432"
-->

#### Numbers

In more low-level languages, numbers are divided into two classes or objects:

* Integers

  ```javascript
   ..., -1,0, 1, 2, 3, 4, 5, ...
  ```

* Floats (or Decimal numbers)

  ```javascript
   2.718, 3.14, .5, .25, etc
  ```

All numbers in JavaScript are **"double-precision 64-bit format IEEE 754 values"** - read this as "There's really no such thing as an integer in JavaScript."

In JavaScript, these data points are the same **type** of object, which it calls *Numbers*, so if you know floats and integers do not go looking for them.


#### Arithmetic Operators

Operators are used to work with data in JavaScript. The standard [arithmetic operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators#Arithmetic_operators) - that you've been learning since grade school - are supported, including addition, subtraction, modulus (or remainder), and so forth.  Check it out:

```javascript
1 + 2
=> 3

2 - 5
=> -3

5 / 2
=> 2.5

6 * 2
=> 12
```

#### Special Number Operators

JavaScript can be a little cheap with the number of operations it allows you to do. For example, how is someone supposed to square a number or cube a number easily? Luckily there is a special `Math` object with some very useful methods.

* Taking a number to some `power`? Then just use `Math.pow`

```javascript
// 3^2 becomes
Math.pow(3,2)
=> 9
// 2^4 becomes
Math.pow(2,4)
=> 16
```
* Taking a square root

```javascript
// √(4) becomes
Math.sqrt(4)
=> 2
```
* Need a `random` number? Then use `Math.random`.

```javascript
// The following only returns a random decimal
Math.random()
=> .229375290430
/**
  The following will return a
  random number between 0 and 10
*/
Math.random()*10
```

* Since Numbers can be **Floats** or **Integers** we often want to get rid of remaining decimal places, which can be done using `Math.floor`.

```javascript
// Remove the decimal
Math.floor(3.14)
=> 3
Math.floor(3.9999)
=> 3
```

<!--Actually 10:13 -->
<!--WDI4 -->
<!--WDI5 9:43 -->
<!--10:10 - 5 minutes -->

#### Challenge

Try the following operations in your Chrome Developer tools:

1. Show the solution of `(1 + 43) * 26 - (37 / 2)`
2. Show the square root of `123456`
3. Show a random number between 0 and 20

<!--9:46 WDI5 -->
<!-- 10:15 5 minutes -->

#### Strings

Strings are collections of letters and symbols known as *characters*, and we use them to deal with words and text in JavaScript. Strings are just another type of **value** in Javascript.

```javascript
"John"
"Jane"
"123"
```

#### String helper methods

To find the length of a string, access its [`length`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/length) property:

```
"hello".length;
=> 5
```

There's our first brush with JavaScript objects! Did I mention that you can use strings like objects, too?

Strings have other [methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#Methods) as well that allow you to manipulate the string and access information about the string:

```
"hello".charAt(0);
=> "h"

"hello, world".replace("hello", "goodbye");
=> "goodbye, world"

"hello".toUpperCase();
=> "HELLO"
```

<!--WDI5 9:5 -->

Types of values like `Number` or `String` are not very useful without being able to form **Expressions** or **Combinations**.

Try your favorite number operators as expressions:

```javascript
  1 + 1
  => 2
  2 - 1
  => 1
```

You can also create expressions with strings using the plus operator `+`:

```javascript
  "Hello, " + "world!"
  => "Hello, world!"
```

This is not the same thing as addition. It is another operation called **String Concatentation** using the same symbolic operator.


#### Converting Strings to Integers with parseInt() and parseFloat()

You can convert a string to an integer using the built-in [`parseInt()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt) function. This takes the base for the conversion as an optional second argument, which you should always provide:

```javascript
parseInt("123", 10);
=> 123

parseInt("010", 10);
=> 10
```

This will be important later when we're taking user input from the web and using it on our server or in our browser to do some type of numeric calculation.

<details>
  <summary>
    Try calling `parseInt` to interpret a binary or hexadecimal value or string.
  </summary>

```javascript
parseInt("fa4542", 16);
=> 16401730

parseInt("111", 2);
=> 7
```
</details>


Similarly, you can parse floating point numbers using the built-in [`parseFloat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseFloat) function which uses base 10 always unlike its `parseInt()` cousin.

```
parseFloat("11.2");
=> 11.2

parseFloat("1" + Math.PI);
=> 13.141592653589793

```

<!--WDI5 10:0  -->
<!--Actually 10:30-->
<!--10:20 5 minutes -->

#### NaN

The `parseInt()` and `parseFloat()` functions parse a string until they reach a character that isn't valid for the specified number format, then return the number parsed up to that point.

A special value called [`NaN`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN) (short for "Not a Number") is returned if the string is non-numeric:

```javascript
parseInt("hello", 10);
=> NaN
```

**`NaN` is toxic**: if you provide it as an input to any mathematical operation the result will also be `NaN`:

```javascript
NaN + 5;
=> NaN
```

You can test for `NaN` using the built-in [`isNaN()`](ttps://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/isNaN) function:

```javascript
isNaN(NaN);
=> true
```

<!--Actually 10:32 -->

#### Null and Undefined

JavaScript distinguishes between:

- `null` a value that indicates a deliberate non-value
- `undefined` indicates an uninitialized value — that is, a value that hasn't even been assigned yet

<!-- CFU: Show-of-hands: which will you see more: null / undefined -->

<!--10:05 WDI5 -->
<!--10:25 5 minutes -->

## Variables and Keywords - Demo

Variables are used to store data types into the memory of the computer so that they can be referenced later.

#### Always use var (unless you are using ES6, aka ES2015)

New variables in JavaScript are declared using the [`var`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var "/en/JavaScript/Reference/Statements/var") keyword.

If you declare a variable without assigning any value to it, its type is `undefined`.

```javascript
var a;
=> undefined
```

So lets try assigning a value to variable:

```javascript
var name = "Alex";
=> undefined

name
=> "Alex"
```

Having made some expressions it becomes evident we want to store these values.

```javascript
var myNumber = 1;
// or also

var myString = "Greetings y'all!";
```

It is worth reiterating that these variables should always have the `var` keyword and use `camelCase`

#### Assignment Operators

Values are assigned using `=`, and there are also compound assignment statements such as `+=` and `-=`:

```javascript
var x = 1;
=> 1

x += 5
=> 6
```

You can use `++` and `--` to increment and decrement, respectively.

In Javascript we just discussed two types of values we can use. We call these values objects, which for now just means that in addition to storing some data you also get to use some helpful methods when you are working with them.

<!--WDI5 10:13 -->

* If you want to turn a number into a string you can use a helpful method called `toString`.

```javascript
(1).toString()
=> "1"
```

<!-- CFU And who remembers how to convert strings to numbers? -->

<!--ACtually 10:40 -->
<!-- 10:30 5 minutes -->
<!--10:43 WDI4 lots of questions on assignment and memory -->

## Arrays - Demo

Unfortunately, strings and numbers are not enough for most programming purposes.
What is needed are collections of data that we can use efficiently, like **Arrays**.

Arrays are great for:

* Storing data
* Enumerating data, i.e. using an index to find them
* Quickly reordering data

Arrays, ultimately, are a data structure that is similar in concept to a list. Each item in an array is called an element, and the collection can contain data of the same or different types. In JavaScript, they can dynamically grow and shrink in size.


```javascript
var friends = ['Moe', 'Larry', 'Curly'];
=> ['Moe', 'Larry', 'Curly']
```

Items in an array are stored in sequential order, and indexed starting at `0` and ending at `length - 1`.

```javascript
// First friend
var firstFriend = friends[0];
 => 'Moe'
// Get the last friend
var lastFriend = friends[2]
=> 'Curly'
```

<!-- 10:35 5 minutes -->
## Working with Arrays - Demo

Javascript arrays are usually created with an array literal:

```javascript
var a = ["dog", "cat", "hen"];

a[1];
=> "cat"

a.length;
=> 3
```

#### Length method

The `length` method works in an interesting way in Javascript. It is always one more than the highest index in the array.

So `array.length` isn't necessarily the number of items in the array. Consider the following:

```javascript
var a = ["dog", "cat", "hen"];
a[100] = "fox";
a.length; // 101
```

**Remember**: the length of the array is one more than the highest index.

#### Getting data from an array

If you query a non-existent array index, you get `undefined`:

```javascript
var a = ["dog", "cat", "hen"];
=> undefined

typeof a[90];
=> undefined
```

#### Array helper methods

Arrays come with a number of methods. Here's a list of some popular helpers:

- `a.toString()` - Returns a string with the `toString()` of each element separated by commas.

- `a.pop()` - Removes and returns the last item.

- `a.push(item1, ..., itemN)` - `Push` adds one or more items to the end.

- `a.reverse()` - Reverse the array.

- `a.shift()` - Removes and returns the first item.

- `a.unshift([item])` - Prepends items to the start of the array.

Remember, though, you'll never remember _every_ method.  Explore the the [full documentation for array methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) and other helper methods given to you for different objects (like Math, Date, String, et c).

<!--Actually 10:45 -->
<!--10:40 5 minutes -->

#### Challenge

Try the following operations in your Chrome Developer tools:

1. Create an array with the strings "Rick", "Morty", and "Jerry" inside.  Save this array as a variable.
2. Show how many elements are inside the array.
3. Reverse the array.
4. Remove the last element from the array.
5. Show the contents of the array.

<!--WDI5 10:26 -->
<!--11:01 WDI4 -->
<!--10:45 5 minutes -->

## Iterating through an array - Demo

Iterating through the elements of an array, one at a time, is a very common practice in programming.

We can use a `for` loop to iterate over the elements of an array like this:

```javascript
var teams = ['Bruins', 'Cal Bears', 'Ravens', 'Ducks'];
for (var i = 0; i < teams.length; i++) {
    console.log(teams[i]);
}
```

JavaScript arrays have several advanced _iterator methods_.

Several of these methods require a function be supplied as an argument, and the code you write in the function will be applied to _each_ item in the array, individually.

As an example, let's look at the `forEach` method that we can use instead of a `for` loop to iterate the elements:

```javascript
var teams = ['Bruins', 'Broncos', 'Ravens', 'Ducks'];
teams.forEach(function(el) {
    console.log(el);
});
```

<!-- CFU: What do you think will print out from this code? -->

This function would return:

```javascript
Bruins
Broncos
Ravens
Ducks
undefined
```

Notice how much cleaner this syntax is than that of the `for` loop?

Here are some other iterator methods for you to research and practice with:

- `Array.every()`
- `Array.some()`
- `Array.filter()`
- `Array.map()`

<!--Actually 10:54 -->
<!--WDI5 10:33 turning over to devs-->
<!--11:07 WDI4 -->
<!--10:50 20 minutes -->

## Independent Practice

> ***Note:*** _This can be a pair programming activity or done independently._

Take a look at the [starter-code](starter-code) and work through each exercise using the comments provided to console log the correct information.  

<!--WDI5 coming back 10:52 -->
<!--Actually 11:13, skipped conclusion and just went through objectives-->
<!--11:10 5 minutes -->
<!--11:27 WDI4 after objectives run-through -->

## Conclusion

- Describe use cases of different "data types".
- Why is iterating important when working with stored data?

<!--WDI5 10:56 -->

Feel free to read more from [Mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript) about JavaScript fundamentals.

## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.
