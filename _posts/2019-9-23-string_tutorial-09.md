---
layout: post
title: Lesson 9 - Strings (Tutorial)
categories: [Strings, indexing, slicing, operators, methods]
---

Strings are among the most popular types in Python, we have used them extensively in our course. We are going a bit more in depth to describe and show many of the things that can be done with strings.

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>

For this lesson we won't have a project, as there is too much to cover. In future projects we will be covering what we will learn in this lesson.

As mentioned before, **strings** are immutable primitive types, they can be defined as a **sequence of characters**.

[graphic]

For this lesson the following topics will be covered.

* String characters in Python
* Creating a string
* Removing and "editing" strings
* Strings indexing and slicing
* String iteration
* String Operators
* String Methods
* String formatting

## String characters in Python

In Python, **strings** are represented as a **sequence of immutable Unicode characters**. Unicode includes every character in all languages

`string = "Sparse is better than dense."`

Each character has a numerical value. We will have to elicit the help of a couple of built in function, `ord()` and `chr()`

* `ord()` : Converts character to an integer. **Encoding**

```python
>>> ord('n')
110
>>> ord('N')
78
```

* `chr()` : Converts an integer to a number. **Decoding**

```python
>>> chr(56)
'8'
>>> chr(123)
'{'
```

### The string object

We can turn an object into a string by using the built in function `str()`

```python
>>> type(45)
<class 'int'>
>>> type(str(45))
<class 'str'>
>>> '4' in str(45)
True
```

## Creating a string

String are created by wrapping characters in single, double or triple quotes

> Notice, the quotes must be the same at the start and end of the string.

```python
str_single = 'This is a string'
str_double = "This is a string"
str_triple = """ This is a string """
```

## Removing and "editing" strings

**Strings can not be edited** as they are immutable, but we can **reassign** a new string **to the same variable**.

```python
>>> string = 'aeio'
>>> string
'aeio'

>>> string = 'aeiou'
>>> string
'aeiou'
```

We can delete an entire string by using the keyword `del`, but we can not remove an individual character from a string.

```python
>>> del string

>>> string # no longer exists
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'string' is not defined 
```

## Strings indexing and slicing

Strings as a series of positional characters are indexed from left to right starting with the number 0. and right to left with negative numbers starting with -1

| P   | Y   | T   | H   | O   | N   |
| --- | --- | --- | --- | --- | --- |
| 0   | 1   | 2   | 3   | 4   | 5   |
| -6  | -5  | -4  | -3  | -2  | -1  |

We can count the number of characters in a string by using the `len()` function.

```python
>>> len('python')
6
```

We can access a character by specifying it's string index. We write the string followed by  square brackets `[n]` where `n` is the index number of the character we want to access.

```python
>>> 'python'[2]
't'
```

Inversely we can access the character from right to left using negative numbers, indexing backwards.

```python
>>> 'python'[-4]
't'
```

### String slicing

Is a more general form of indexing, designed to  extract an entire section in a single action, crating a new object with the result.

```python
>>> 'python'[1:4]
'yth'
```

In the example above, we sliced from index 1 up to (but not including) index 4. `[1:4]`

| Y   | T   | H   |     |
| --- | --- | --- | --- |
| 1   | 2   | 3   | 4   |

Lets assign the string `"python"` to the variable `f` to simplify our examples.

* `f = 'python'`

If we omit the first index, Python assumes it starts at `0`

```python
>>> f[:3]
'pyt'
>>> f[0:3]
'pyt'
```

If we omit the second index `[n:]`, Python will slice from `n` to the end of string, we don't have to know how long the string is.

```python
>>> f[2:]
'thon'
>>> f[-4:]
'thon'
>>> f[2:len(f)]
'thon'
```

To return the compleat string we can indicated as follow

```python
>>> f[:]
'python'
```

To get an empty string, you can pass two indexes of equal value `[n:n]` or overlaping indexes.

```python
>>> f[2:2]
''
>>> f[2:-4]
''
```

Python slicing has a third index used to indicate `stepping` or by increments of `n`
[x:y:n]

```python
>>> f[::2]
'pto'
```

We can also give a negative index for stepping [x:y:-n]. Python will step backwards through the string.

```python
>>> f[5:0:-2]
'nhy'
```

When there is no first or second index, the string indexes are reversed. To reverse a string we can use the following format `[::-1]`

```python
>>> f[::-1]
'nohtyp'
```

## String iteration

We can iterate through each character of a string by using a `for` loop.

```python
>>> f = 'python'
>>> for l in f:
...     print(l)
...
p
y
t
h
o
n
```

## String Operators

There are a number of operators that can be used with strings adding even more flexibility to strings.

| Operator | Description                            |
| -------- | -------------------------------------- |
| `+`      | Joins two or more strings together     |
| `*`      | Creates multiple copies of string      |
| `in`     | Membership of string in another string |
| `not in` | bla, bla                               |

### The `+` operator

The `+` is able to join two or more strings together.

```python
>>> st1 = 'The first string'
>>> st2 = 'The second string'
>>> new_st = st1 + st2
>>> print(new_st)
The first stringThe second string
```

we can add another string to add space between the `st1` and `st2`

```python
>>> st1 + ' ' + st2
'The first string The second string'
```

### The `*` Operator

The `*` generates multiple copies of a string, it works on any string.

```python
>>> '-' * 8
'--------'
>>> '123' * 4
'123123123123'
```

### The `in` Operator

Test membership of s string in another string. It returns a bulian `True` or `False`

```python
>>> master_st = 'Beautiful is better than ugly.'
>>> 'ugly' in master_st
True
```

### The `not in` Operator

The `not in` Operator is the opposite as the `in` operator.

```python
>>> 'ugly' not in master_st
False
>>> 'apple' not in master_st
True
```

## String Methods

Just as python has built-in functions, procedures which can be called to perform specific tasks on an object, ie. `len('hello')`.

Python also offers built-methods, much like functions perform a procedure on a specific object. Methods are part of class, they can be written specifically for an object type, hence "string method" these are written to perform tasks on string objects.

The way to call an object (string) method, is to write the object followed by `.method_name()`.

Because strings are immutable when we use a method, it returns a copy of the original string with the result.

There are over 40 built-in string methods available, we are just going to cover a few. For a full list, please see the Python documentation.

### `.capitalize()`

This method capitalizes a string.

```python
>>> x = 'hello '
>>> x.capitalize()
'Hello'
```

### `.upper()`

Use the this method to turn a string to all upper case.

```python
>>> x.upper()
'HELLO MAN'
```

### `.lower()`

It returns a string with all lower case.

```python
>>> y = 'ReaDAbiLity CouNts.'
>>> y.lower()
'readability counts.'
```

### `.title()`

It will turn a string in to a title.

```python
>>> t = 'Beautiful is better than ugly.'
>>> t.title()
'Beautiful Is Better Than Ugly.'
```

Python also offers a number of Methods specifically for searching for a substring in a string 

### `.count()`

Returns the number of occurrences of a substrings in a string.

```python
>>> 'Now is better than never'.count('e')
4
>>> 'Now is better than never'.count('tt')
1
```

We can also limit the count to a specific range by passing a starting and ending index.

```python
>>> x = 'Now is better than never'
>>> x.count('e', 9, 24)
3
```

### `.startswith()` and `.endswith()`

These two methods determin if a target string starts or ends with a particular substring. The methods will returtn `True` or `False`

#### `.startswith()`

```python
>>> x = 'Now is better than never'
>>> x.startswith('Now')
True
>>> x.startswith('is')
False
```

#### `.endswith()`

```python
>>> x.endswith('ever')
True
```

There are a number of very useful formatting methods. They allow us to enhance a string.

### `.center()`

We can center a strings on a given field of spaces

```python
>>> 'Beautiful'.center(15)
'   Beautiful   '
```

We can also assign a fill character by passing the character as an argument.

```python
>>> 'Beautiful'.center(15, '~')
'~~~Beautiful~~~'
```

### `.ljust()` and `.rjust()`

Aside fom centering a string we can also left and right justify it.

```python
>>> 'Beautiful'.ljust(15)
'Beautiful      '
>>> 'Beautiful'.rjust(15)
'      Beautiful'
```

we can also fill the range with a character

```python
>>> 'Beautiful'.ljust(15, '-')
'Beautiful------'
>>> 'Beautiful'.rjust(15, '-')
'------Beautiful'
```

### `.strip()`, `.lstrip()` and `.rstrip()`

Another useful string method are the `.strip()`, `.lstrip()` and `.rstrip()`

When we don't specify an argument, Python will strip all the leadding and trailling spaces depending on the type of strip method we use.

```python
>>> n = '   Beautiful   '
>>> n.strip()
'Beautiful'
>>> n.lstrip()
'Beautiful   '
>>> n.rstrip()
'   Beautiful'
```

We can specify the characters to strip.

```python
>>> 'purity/?'.rstrip('/?')
'purity'
>>> 'Mr. Brown'.lstrip('Mr. ')
'Brown'
```

### `.replace()`

We can use the `.replace()` method to replace an **'old'** substring for a **'new'** one. Since strings are immutables, Python just creates a copy with the new changes.

```python
>>> 'Mr. Sophie Brown'.replace('Mr.', 'Mrs.')
'Mrs. Sophie Brown'
```

We can also specify the number of times we can replace a substring, from left to right.

If we don't specify the count, it would replace every instance of the 'old' word.

```python
>>> 'right.move.right.now'.replace('right','left', 1)
'left.move.right.now'
```

## String formatting

Python has three types of string formatting, expression, method and fstring.

> **Note:** variables for example in table below
>
> * `var_1 = 'Easy'`
> * `var_2 = 'Python'`

| Syntax                                | type       |
| ------------------------------------- | ---------- |
| print('%s = %s' % (var_1, var_2))     | Expression |
| print('{} = {}'.format(var_1, var_2)) | Method     |
| print(f'{var_1} = {var_2}')           | fstring    |
|                                       |
| **Easy = Python**                     | <= prints  |

### String formatting expression

Is the oldest type of formatting available since the start of the language based on the programming language C. You still will see this type of formatting around.

```python
>>> xx = 'her'
>>> 'I spoke to %s yesterday' % xx
'I spoke to her yesterday'
```

With the formatting expression one must specify the type of object being replaced, in the case above we used `%s` where `s` stands for string. Here is a partial list of types that can be used.

| Code | Meaning                                |
| ---- | -------------------------------------- |
| s    | String (or any object’s str(X) string) |
| c    | Character (int or str)                 |
| d    | Decimal (base-10 integer)              |
| i    | Integer                                |
| f    | Floating-point decimal                 |

You may look at the Python documentation for more information on formatting expressions

### String formatting method

The formatting method, uses a method call to format an string object. The string becomes a template and the format method argument to pass values to the template.

The values passed as arguments in the formatting method are positional.

```python
>>> string_template = '{} is {} than {}.'
>>> string_template.format('Beautiful', 'better', 'ugly')
'Beautiful is better than ugly.'
```

Likewise you can assign the order in which the values are placed in the string by specifying the method's argument index.

```python
>>> string_template = '{1} is {0} than {2}.'
>>> string_template.format('Beautiful', 'better', 'ugly')
'better is Beautiful than ugly.'
```

The format method also allow us to format different number types integers, floats, binary as well as arranging a string in a given space.

```python
>>> 'pi with three decimals {:.3f}'.format(3.14159265)
'pi with three decimals 3.142'
```

We can also arrange a string in a given space for better display by using the format method.

```python
"|{:<12}|{:^12}|{:^12}|".format('Name','Date','Price')
'|Name        |    Date    |   Price    |'
```

There are many string formatting available to use with the `.format()` method. Please see the documentation for more detailed use.

### Formatted String Literal (f-string)

The `fstring` was introduced with Python version 3.6. It is probably the most intuitive of the ways to format strings. 

By simply prefixing the string with the letter `f'sample {var}'` you can add curly brackets inside the strings call variables and execute some operations.

```python
>>> a = 24
>>> b = 45
>>> f'The result for {a} + {b} = {a + b}'
'The result for 24 + 45 = 69'
```

The **f-string** format is very extensive and requires its own tutorial. But you can see more in the Python documentation.

As you can see Python provides an extensive toolbox to handle string from starting at a very granular level. We covered the most relevant aspect of strings, but there is more that can be found in the reference documentation and others I will introduce at a later point.

---

## Next tutorial

TBA: most definitely will have something to do with strings.

## Things to try

Read through the tutorial, and find some of the topics I asked to search in the documentation

* More on **f-strings**
* Other formmating expression codes
* Find other string methods we didn't cover here

## Question

* How do you reverse the order of a string? so it prints backwards
* What are the three types of string formatting?
* What string method would you use to create a copy of string all lower case?

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>
