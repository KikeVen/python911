---
layout: post
title: Using Python numbers - the temperature converter script - 02
categories: [intergers, decimals, addition, multiplication, subtraction, order of operations]
---

In our last tutorial we learned to **print** a **string** to screen by using the built-in function `print()`

For our next project we are going to build a temperature converter, by using the print function and math in Python

## Temperature converter project list

* [x] Find the equation to convert **Fahrenheit** to **Celsius**
* [x] How do numbers work in Python
* [x] What is the order of operation
* [x] Launch and write the script
* [x] Print the results

## Temperature convertion equation

Ok, for this we will have to do a little research, we need to find the equation to convert Fahrenheit to Celsius and viseversa if needed. (You don't have to be a math wiz to be a programmer)

* Search the internet
* Copy the equation
* Save it

**Fahrenheit to Celsius:**

* (F - 32) x 5/9 = C

**Celsius to Fahrenheit:**

* (C x 9/5) + 32 = F

## How do numbers work in Python

There are a couple of things we need to know about numbers in Python to begin this project (more later). One: they are categorized (**typed**) and Two: operators execute in a particular order.

### Number types (categories)

From this point on, we will reffer to number categories as **types**

These are the two most common number **Types**, **Intergers** and **Floats**, there are more but those will come later.

Literal | Type | Python
---|---|---
1234, -24, 0, 999999 | **Integer** | int(x)
1.23, 1. , 3.14e | **Float** | float(x)
51924361L, 0122L | Long | long(x)
45.j, 3.14j | Complex | complex(x)

There is a **built-in function** in python called `type()` Try it in your Online Interpreter, Trinket.

```python
print(type(1.76))
# returns <class 'float'>
```

### Operators

There are a multitude of operators, today we are going to list the must commonly used.

Operator | expression | description
---------|-----|------------
`+` | x + y | Addition
`-` | x - y | Subtraction
`*` | x * y | Multiplication
`/` | x / y | Division
`**` | x ** y | Power (exponentiation)

---

```python
# The following would execute in Python but you
# would not be able to see the result in Trinket
# Why? think about it, lets keep going

32 + 4
```

There is a list of numbers and operators available in the Python documentation, see the links below.

* [Numeric types and operators](https://docs.python.org/3/library/stdtypes.html?highlight=operators#numeric-types-int-float-complex)

## Order of operationos in Python

It is important to know Python follow an order of operation, there is a hierarchy in they way numbers are processed during execution. The good thing, the order Python operators are executed in, is governed by the operator precedence and follow the same rules.

1. Parenthesis `( )` first
2. Exponent next `x ** y`
3. Multiplication or Division next `x * y` or `x / y`
4. Addition or Subtraction next `x + y` or `x - y`

## Launch the interpreter and write the script

To write our application lets launch our Online Python Interpreter, **Trinket**.

* [Trinket.io](https://trinket.io/embed/python3/c0a3e920df)
* Equation: (F - 32) x 5/9 = C

Write the equation in Python, we are looking for C (Celsius) and we must keep in mind how numbers and operators are written in Python.

* In this case there isn't much to change
* Lets say we want to know what **75 Fahrenheit** is in **Celsius**
* In Trinket write the following code and execute it.

```python
(75 - 32) * 5/9
```

> let me guess, **"nothing happened"**, actually it did, but is not showing, do you know why?

You need to tell Python to print the result to the screen, by using the `print()` function

> Keep track of your parenthesis

```python
print((75 - 32) * 5/9)
```

If you run the code again, you will see it automatically just print the result on the computer screen

> You did it, you wrote a temperature converter!

## Things to try

* Try finding and adapting a different equation, such as finding the volume of a water tank.
* find out the type of your results by using the `type()` function

## Question

* What are the two most commun number types used in Python?
* What are two built-in functions you have learned up to now?
