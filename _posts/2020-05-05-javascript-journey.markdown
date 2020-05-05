---
layout: post
title: JavaScript - Intro
author: Gökhan Özeloğlu
date: 2020-05-05 15:25:09 +0300
categories: general
tags: [javascript]
permalink: /:categories/javascript-intro
---

I have started to learn JavaScript from scratch and I decided to write a blog to share what I learned in this process. 

## What is JavaScript? 

JavaScript is a programmin language that gives behavior to the programs. We give some functionalities to the web pages or mobile application with JavaScript.

## Printing output

We start programming with "Hello World!" message. To print out something on the screen is important to write "Hello World" message. We use `console.log()` function to print out some messages on the screen. We can write "Hello World" message like this:

`console.log("Hello World");`

## Comments

JavaScript comments are similar to C-like languages. There are 2 options to write comments in our codes. 

#### **Inline Comments**

Any text between `//` is ignored by JavaScript and does not affect the program.

{% highlight JavaScript %}
console.log("This message will be visible");
// This line will not be visible
{% endhighlight JavaScript %}

#### **Block Comments**

Any text between `/*` and `*/` is ignored by JavaScript and does not affect the program.

{% highlight JavaScript %}
console.log("This message will be visible");
/*
* This block will not be visible
* console.log("This block will be ignored);
*/
{% endhighlight JavaScript %}

## Identifiers

Simply, identifiers are the variable that we defined and is being used in the program. There are some rules that we follow to write proper code. They should be start with letters, underscore(\_), or dollar sign(\\$). Subsequent characters can be letters, underscore(\_), or digits(from $0$ to $9$). Also, there are some *keywords* and *reserved words*. These are pre-defined names that defined by JavaScript and you cannot use them as a variable. 

## Semicolon

Like most of the other programming languages, there is semicolon(;) in JavaScript. At the end of the statement, you put semicolon to identify statement is end. But, you do not need to put semicolon. It is optional as long as the statements are written separate lines. 
{% highlight javascript %}
var a = 12;
var b = 15
// Both of them are valid
{% endhighlight javascript %}

## Data Types

Like in other programmin languages, there are some data types which grouped into primitives and objects. All primitives are **immutable** meaning that they cannot be changed after defined them. These primitive data types are:
- Number
- String 
- Boolean
- Symbol
- Null
- Undefined

### Number Data Type

It represents both integer and float numbers. 

`MAX_VALUE`: The highest number in the JavaScript. Its value is `1.7976931348623157e+308`. `Number.MAX_VALUE` gives you this number. \
`MIN_VALUE`: The smallest number in the JavaScript. Its value is `5e-324`. `Number.MIN_VALUE` gives you this number.

#### Symbolic Numbers

`Infinity`: This is any number divided by 0 or an attempt to multiply `MAX_VALUE` by an Integer which is bigger than 1. \
`-Infinity`: This is any number divided by -0 or an attemp to multiply `MAX_VALUE` by an Integer which is smaller than -1. \
`NaN`: **Not-a-Number**. It is a number which denotes the unrepresentable number like *complex numbers*. 

### String Data Type

String is similar to other languages. You can use `""` or `''` for string. 

{% highlight javascript %}
var a = "Sample String";
var b = 'Other string';
// Both of them are valid
{% endhighlight javascript %}

Also, you can print out the single or double quotations. `"'"` evaluates `'` and `'"'` evaluates `"`. 

{% highlight javascript %}
console.log('"Hello" World');   // "Hello" World
console.log("'Hello' World");   // 'Hello' world
{% endhighlight javascript %}

Moreover, string is immutable in JavaScript. So, you cannot modify the string after declaration. However, you can do some operations over the strings like substring or concatenation.

### Boolean Data Type

Like other programming languages, there are two boolean value, `true` and `false`.

### Symbol Data Type

It is new to JavaScript. A Symbol is a unique and immutable primitive value.

### Null Data Type

It is a primitive data type that represents the absence of any object value. If a variable contains no valid number, string, boolean, array, or object, it contains null.

### Undefined Data Type

If a variable does not exists, or has been declared but has never had a value assigned to it, the undefined value is returned.

## *typeof* Operator

We can use the `typeof` operator to learn a variable's type.

{% highlight javascript %}
var a = "sample string";
console.log(typeof(a));     // prints out "string"

var b = 12;
console.log(typeof(b));     // prints out "number"

var c = true;
console.log(typeof(c));     // prints out "boolean"
{% endhighlight javascript %}

## Dynamic Typing

Sometimes we want to change the variable's type during the program. We use dynamic typing for this purpose. Once we defined a variable, we can change the value with different type.

{% highlight javascript %}
var a = 1;
console.log("a is: " + a);
console.log("a's type is: " + typeof(a));
// a is: 1
// a's type is: number

a = "sample string";
console.log("a is: " + a);
console.log("a's type is: " + typeof(a));
// a is: sample string
// a's type is: string
{% endhighlight javascript %}

## Naming

JavaScript is a case-sensitive language which means that `sampleVariable` and `samplevariable` are not the same variables. Also, you cannot use **reserved word**.

## Coercion

In other languages, there is type casting. But, in JavaScript, there is not such a feature and you need to use *coercion*. It means that one of the data type is being converted or coerced and performs the operation. The rules are:

- `Number + String = String` 
- `Booelan + String = String` 
- `Number + Boolean = Number` 

## Unary Operator

It is the same as in C-like languages. `++a` or `a++` is valid.

## Binary Operator

There must be two operands and one operator. For example, `a + b = c`.

## Ternary Operator

It is conditional opeator. `a ? b : c` is a basic form. It means that if `a` is true, `b` is returned, if not true, `c` is returned. 

## Arithmetic Operators

Addition(+), subtraction(-), multiplication(*), division(/), remainder(%), exponention(**) are the same as in the other languages.

## Equality Operator (==)

It compares two operands and return `true` if they are equal. Otherwise, it returns `false`. But, there is a different rule apart from other languages. If you try to compare two operands which has the different types, JavaScript applies the strict comparison. For example,

{% highlight javascript %}
console.log(1 == 1);                // True
console.log(1 == "1");              // True
console.log(1 == '1');              // True
console.log(1 == true);             // True
console.log(1 == null);             // False
console.log(1 == undefined);        // False
console.log(undefined == null);     // True
{% endhighlight javascript %}

## Inequality Operator (!=)

It compares two operands and return `true` if they are not equal. Otherwise, it returns `false`. If you try to compare two operands which has the different types, JavaScript applies the strict comparison. It converts the appropriate type. For example,

{% highlight javascript %}
console.log(1 != 1);                // False
console.log(1 != "1");              // False
console.log(1 != '1');              // False
console.log(1 != true);             // False
console.log(1 != null);             // True
console.log(1 != undefined);        // True
console.log(undefined != null);     // False
{% endhighlight javascript %}

## Object Comparision

While comparing two objects, JavaScript looks at the memory address of the objects. If the adresses are different, so objects are different. 

{% highlight javascript %}
class SampleObject {

    constructor(a) {
        this.a = a;
    }
}

// These are different object
// Their memory addresses are different
var object1 = new SampleObject(12);
var object2 = new SampleObject(12);

// object1 reference set to the object2
object1 = object2;
{% endhighlight javascript %}

## Strict Equality (===)

If the operands are strictly equal and has the same type, it returns `true`.

{% highlight javascript %}
console.log(1 === 1);               // True
console.log(1 === "1");             // False
console.log('1' === 1);             // False
console.log(0 === false);           // False
console.log(0 === null);            // False
console.log(0 === undefined);       // False
console.log(null === undefined);    // False
{% endhighlight javascript %}

## Strict Inequality (!==)

If the operands are strictly not equal and has not the same type, it returns `true`.

{% highlight javascript %}
console.log(1 !== 1);               // False
console.log(1 !== "1");             // True
console.log('1' !== 1);             // True
console.log(0 !== false);           // True
console.log(0 !== null);            // True
console.log(0 !== undefined);       // True
console.log(null !== undefined);    // True
{% endhighlight javascript %}

## Functions

Functions are similar to other languages, but there are some differents in some usages. Functions are declared with `function` keyword and it is a `Function` object property. By default, functions return the value `undefined`. If you want to return something different, you need to return any other statement with `return` keyword. A function example,

{% highlight javascript %}
function multiply(x, y) {
    return x * y;
}
{% endhighlight javascript %}

Also, we can define function expressions like *anonymous function*. Function names are omitted. Here is a example,

{% highlight javascript %}
function main() {

    var addition = function(x, y) {
        return x + y;
    }

    console.log(addition(12));
}
{% endhighlight javascript %}

Also, we can define named functions. These can be property of the variable or reference of the variable. Example,

{% highlight javascript %}
function main() {

    // Named function --> As a property of the math variable
    var math = {
        divide:
            function divide(x, y) {
                if (y != 0) {
                    return x / y;
                } else {
                    return 0;
                }
            }
    };

    console.log(math.divide(10,5));

    // Named function --> Referenced by the div variable
    var div = function divide(x, y)  {
        if (y != 0) {
            return x / y;
        } else {
            return 0;
        }
    }

    console.log(div(10, 5));
}
{% endhighlight javascript %}

## var, let, and const

There some different ways to define variables in JavaScript and there are some minor differences between them.

#### **var**

We use `var` to define variable. It creates a local variable that is accessible in declared scope. It will 
not be visible out of the declared scope. Also we can change its value after defined it.

{% highlight javascript %}
function main(input) {

    var a = input;

    if (a % 2 == 0) {
        var a = input + 1;
        console.log(a);     // a = 12
    }

    console.log(a);         // a = 12
}

// input = 11
{% endhighlight javascript %}

In this example, `input` is 11 and we defined `a` in function scope. When if block is executed, we initialized the `a` again and incremented by 1. `a` value is still 12 after if block because if block is in function scope. Function includes if block.

#### **let**

We can also use `let` keyword to define a variable with limited scope. Once we defined the variable, it is only accessable from this scope. When we try to access the variable from out of the scope, we cannot access.

{% highlight javascript %}
function main(input) {

    let a = input;

    if (a % 2 == 0) {
        let a = input + 1;
        console.log(a);     // a = 12
    }

    console.log(a);         // a = 11
}
// input = 11
{% endhighlight javascript %}

In this example, firstly, we created `a` and assigned to `input`. In if-block, we declared again and assigned `input+1`. So, our output is `12` for the first one. When we go out of the if-block, `a` is still 11 and output will be `11`. That's because our `a` variable which has `12` is defined in if-block and it is valid in if scope. Also, we cannot re-define a variable in the same scope. If we try to define a variable again, it will cause an *Error*. Below example is invalid and error will be occurred.

{% highlight javascript %}
function main(input) {
    let a = 12;

    // This line will be caused error
    let a = 13;
}
{% endhighlight javascript %}

#### **const**

We can only define once and cannot be reassigned with another value in `const` variables. Also, `const` variable should always be initialized. Otherwise, error will be occurred.

{% highlight javascript %}
function main() {
    const a = 12;

    const b;    // This wrong because it not initialized
}
{% endhighlight javascript %}