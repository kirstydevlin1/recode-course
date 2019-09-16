# Anatomy of a JavaScript program

A JavaScript program is essentially a list of instructions for the computer to follow to in order to achieve whatever useful thing the program is required to do.

## Statements

Each instruction in a program is called a **statement**

In JavaScript, statements are composed of **values**, **operators**, **expressions** and **keywords**, and end with a semicolon.

The following is a statement:
```js
const foo = 3 + 4;
```

In the above statement a *variable value* `foo` is created using the `const` *keyword*, and assigned a value using the *assignment operator*. This value is determined by *evaluating* the *expression* `3 + 4`, which combines the *literal values* `3` and `4` using the *addition operator*.

Most programs contain lots and lots of statements, which get executed consecutively, in the order they are written down.


### Values
There are actually two types of values in JavaScript, **literal** values, and **variable** values.

#### Literal values
A literal value is exactly what it sounds like - a value that is written down in it's literal, raw form.

In JavaScript this raw data comes in 5 main forms:
 - **Numbers**
 - **Strings** (aka text)
 - **Booleans**
 - **Arrays**
 - **Objects**

Numbers, strings and booleans are known as **primitives**
Arrays and objects are known as **data structures**

Some examples of literal values:

```js
6;
'Hello';
true;
[1, 2, 3];
{ name: 'Fred', age: 79 };
```

#### Variable values
A variable is like a container used to store a literal value or a **function**. It provides a reference to a value, and can give a more semantic meaning to a value, so that code becomes both easier to read, easier to write and less repetitive.

JavaScript uses the *keywords* `var`, `const` and `let` to declare (create) variables, and the `=` *operator* to assign values to variables.

`var`, `const` and `let` are each slightly different. The primary difference is semantic rather than functional:
- `let` represents a variable that will be reassigned and change it's value;
- `const` represents a constant value that will not change.
- `var` pre-dates the introduction of `const` and `let`, and doesn't have any semantic connotations. It's use is still quite common, but is not recommended in modern JavaScript.

The following code declares a variable `foo`, and assigns it the literal value `'bar'` (a string).

```js
let foo;
foo = 'bar';
```

### Keywords
Keywords are basically reserved words that perform special actions and cannot be used as variable names.
For example, the keyword `const` creates a new variable.  
Trying to create a variable called `let` is a not valid JavaScript syntax.
```js
const let = 10;
```

### Operators
Operators are special symbols that are used to combine two values and create a new one.

The main types of operator are:
- Arithmetic operators - used on numbers (e.g. `*` for multiplication)
- String operators  - used on strings (e.g. `+` for concatination)
- Logical operators - used on booleans (e.g. `||`, the OR operator)
- Comparison operators - used assess a relationship between values (e.g. `===`, the equality operator)
- Assignment operators - used to set or alter the value of a variable (e.g. `+=`, the addition-assignemnt operator)

### Expressions
An expression is a combination of literal values, variables, and operators, which evaluates to a single value.

```js
1 + 2;
```
The above code is an expression that evaluates to `3`

## Blocks
JavaScript statements can be grouped together in **blocks** using curly braces (`{}`).

This is useful because it allows you to define statements that should be executed together.

Blocks are normally found in **functions**, **if-statements** and **loops**
