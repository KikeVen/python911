---
layout: post
title: Lesson 12 - Code refactoring (List comprehencion)
categories: [cat 1, cat 2, cat 3]
---

In our previous lesson we wrote a custom module enabling us to extract key words from a block of text. At this point there is a block of code that could be rewritten (refactor) in order to streamline our code base, improve performance and legibility.

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>

We are going to rewrite a loop that appends a list, with an operation called **list comprehencion**. Allowing us to shorten from a few lines of codes to one.

* `open_file.py` code review.
* What is a list comprehencion?
* How does it work?
* Refactoring `open_file.py`.

## `open_file.py` code review

In our `open_file.py` file, we used our custom module to get a list of tuples with the top six words along with the frequency. We then passed the return value to a for loop, to unpack and only retrive the words, by appending a list.

```python
# where sorted_word_frequency is the variable holding
# the returned value from wordy.frequency()
wf_list = []
for k, v in sorted_word_frequency:
    wf_list.append(k)
```

We can **refactor** our code to one line of code, doing a similar operation inside the `wf_list` list, this type of operation is call a **list comprehencion**.

## List comprehencion

A comprehencion is a less verbose way of writing an operation, it is a bit more advance.

When ever you have an empty list, an iterable and appending the list with the results of the loop, then a list comprehencion can be written.

There are list comprehencions, dictionary comprehencions, set comprehencions and generator comprehencion. Today we are only covering list comprehencions.

## How it works

Lets use a generic loop example to illustrate our iterator.

```python
numbers = []
for number in range(1, 10):
    numbers.append(number)

print(numbers)
```

* `numbers = []` to be populated by the *for loop*
* `for loop` iterates through each number `in` a `range` of **1 to 10**
* We take each number and `.append` the `numbers` list with each `number`.

We get this:

```sql
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

A more unique way of writing the operation in python is to use a _list comprehencion_ which is written in the following format

* **[expression _for_ item _in_ iterable]**

We would write our `for` loop above the following way

* Create a list and assign it to a variable.
  * `list_comp = []`
* Inside the list, write the variable name for the expected returned value.
  * `[number]`
* Then followed by the for loop as we wrote it in the loop
  * `[number for number in range(1, 10)]`

When the line below is ran, it will create a list as indicated by the comprehencion.

> Notice we don't have to use the `.append()` method, because the comprehension is already inside the list.

```python
list_comp = [number for number in range(1, 10)]
```

It will return this:

```sql
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

> We went from three lines of code to just one.

A list comprehencion can also include an `if` condition

* **[expression _for_ item _in_ iterable _if_ condition]**

Going from this:

```python
even_steven = []
for number in range(1, 10):
    if number % 2 == 0:
        even_steven.append(number)
```

To this:

```python
even_steven = [number for number in range(1, 10) if number % 2 == 0]
```

> Going from four lines of code to just one.

And finally we can write a nested `for` loops in a comprehencion format.

```python
list_one = ['my', 'car', 'is', 'black']
list_two = ['the', 'car', 'is', 'brown']

list_app = []
for l1 in list_one:
    for l2 in list_two:
        if l1 == l2:
            list_app.append(l2)

print(list_app)
```

It can be written the following way:

**[expression _for_ item _in_ iterable _for_ item _in_ iterable _if_ condition]**

```python
list_one = ['my', 'car', 'is', 'black']
list_two = ['the', 'car', 'is', 'brown']

list_comp = [l2 for l1 in list_one for l2 in list_two if l1 == l2]

print(list_comp)
```

> Going from five lines of code to just one.

## Refactoring `open_file.py`

Now that we have learned about list comprehencion, lets _refactor_ our code in `open_file.py`.

Open and edit your `open_file.py`.

```python
wf_list = []
for k, v in sorted_word_frequency:
    wf_list.append(k)
```

To this:

```python
wf_list = [k for k, v in sorted_word_frequency]
```

You just refactored your code, to a fewer lines.

It takes some practice getting use to reading and writing list comprehencions, but once you learn the format, it gets easier.

---

## Next tutorial

TBA

## Things to try

Research other types of comprehencions and see if you can implement them.

## Question

* Can you come up with a script using list comprehencion?
* What is the first statement you add to the list comprehencion?

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>
