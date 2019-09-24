---
layout: post
title: Temperature converter - by using numbers - 02
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
* [x] Temporary container for feeding different temperatures to be converter

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

From this point on we will reffer to number categories as **types**

These are the three most common number **Types**, there are more, they will be introduced at a later point

Literal | Type | Python
---|---|---
1234, -24, 0, 999999 | Integer | int
1.23, 1. , 3.14e | Floating-point | float
True, False | Boolean type | bool

There is a built-in function in python called `type()` Try it in your Online Interactive Consul

```python
print(type(1.76))
# returns <class 'float'>
```

### Operators

There are a multitude of operators, today we are going to list the must commonly used.

Operator | use | description
---------|-----|------------
`+` | x + y | Addition
`-` | x - y | Subtraction
`*` | x * y | Multiplication
`/` | x / y | Division
`**` | x ** y | Power (exponentiation)

```python
# The following would execute in Python but you
# would not be able to see the result in Trinket
# Why?

32 + 4
```

As I mentioned, there are more but these are the ones we are going to use today. There is a list of numbers and operators available in the Python documentation I will put the links below.

## Order of operationos in Python

It is important to know Python follow an order of operation, there is a hierarchy in they way numbers are processed during execution. The good thing, the order Python operators are executed in, is governed by the operator precedence and follow the same rules.

1. Parenthesis `( )` first
2. Exponent next `x ** y`
3. Multiplication or Division next `x * y` or `x / y`
4. Addition or Subtraction next `x + y` or `x - y`

## Launch interpreter and write the script

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

## Not done yet, we want to add a temporary container

So we would like to isolate the changing Fahrenheit number so it is easier to convert different numbers.

A temporary container in Python is called a **variable**

We can **assign** different **values** to a **variable**.

Lets say we have the temperature 75 degrees Fahrenheit and we want to assign it to a variable

We can write any variable name, there are a few restrictions, which I'll list below. For now we could use a descriptive word to represent the variable

* We will call our variable `temp_f`
  * Representing "temperature in Fahrenheit"
  * To the variable we will assign the temperature in Fahrenheit we want to convert

This can be red as: the value of 75 was assigned to the temp_f variable or the current value of temp_f is 75

* `temp_f = 75`

We now have to modify our current program to include our variable

```python
temp_f = 75
print((temp_f - 32) * 5/9)
```

We removed the 75 from the previous program and added the variable name in its place, also included the variable with it's assignment above the equation.

Run your program, it should give you the same result as before. If you want to convert a different temperature, just change the value in your variable and run the program again.

## Things to try

* Can you `type()` the `temp_f` variable?
* Can you come up with a different calculator (equation)?

## Question

* What happens to the variable type if you change the value of `temp_f` from a 75 to 75.5?
