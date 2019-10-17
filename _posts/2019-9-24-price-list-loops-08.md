---
layout: post
title: Price list - loops, zip() - 08
categories: [for/while loops, zip()]
---

We have a new challenge, a shop (bodega) owner wants you to print a price list of fruits, the challenge, he has the names list separate from the price list, he will provide you with both.

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>

You will have to write a program to store all the names and prices, then loop though them to combine them and get the list the customer ones.

We are going to learn the following in order to complete our challenge

* `while`/`for` loops
* `zip()` (built-in function)
* Writing the price list

* Our lists:
  * fruits: 'Bananas', 'Apples', 'Lemons', 'Grapes', 'Nectarines', 'Oranges'
  * prices: 3.25, 3.0, 3.10, 2.50, 4.90, 3.80

## while and for loops

Are expressions allowing use to repeat other expressions over and over. Python has two main type of loops, `while` and `for` loops. `while` loops are used for general purpose and `for` loops are mainly use to execute blocks of codes on iterable items like lists, Tuples, dictionaries etc.

### while loops

As the most general of the iterating tools, with a test statement at the top, the `while` loop will continue to execute the code block beneath it until the test at the top of the `while` loop condition's changes.

> Note: To execute a loop in a **Python Interactive Seesion**, you need to add four spaces for indentation below the header and press the `Enter` key twice after the last line of the loop.

```python
>>> counter = 1
>>> while counter <= 10: # until counter is equal/less than 10
...    print('^' * counter)
...    counter += 1
...
^
^^
^^^
^^^^
^^^^^
^^^^^^
^^^^^^^
^^^^^^^^
^^^^^^^^^
^^^^^^^^^^
```

* In the example above, the loop starts with:
  * `while`.
* And the test is:
  * `counter <= 10`.
* And the colon signifies end test statement:
  * `:`
* Any indented code below this line is part of the loop.
  * The `print()` function will print an asterisk, `*`, will be multipled by the value of `counter`:
    * `print('*' * counter)`.
  * Then the value of `counter` will be updated by a count of 1.
    * `counter += 1`.
* It will continue to execute updating `counter` until the value of counter is less than or equal to 10.

#### while infinite loop

There are times where we could write an infinite loop and without any methods to stop the loop it will continue to run for ever. We don't want this unless we use other loop statements to stop the loop, like `brake` we will cover these later.

> To stop an infinite loop, press the `Ctrl-C` keys

```python
>>> while True:
...     print('I am an infinite loop')
I am an infinite loop
I am an infinite loop
I am an infinite loop
# ... and so on
```

### for loop

for loops are iterators used to go through items in any sequence, they work with **Tuples**, **Lists**, **Dictionaries**, **Strings**, **Files** and other iterables.

The `for` line is the **header**, in it we create a new variable. In this case `fruit`, it is use to assign each item in the `all_fruits` Tuple, as the loop iterates through the tuple.

Each item, `fruit`, is tested in the `if` statement, if the condition is met, it will print something, `else` it will print something else.

```python
all_fruits = ('Bananas', 'Apples', 'Lemons', 'Grapes', 'Nectarines', 'Oranges')

for fruit in all_fruits:
    if fruit == 'Grapes':
        print(f'* {fruit} Out of stock!')
    else:
        print(f'{fruit}')
'''
Bananas
Apples
Lemons
* Grapes Out of Stock!
Nectarines
Oranges
'''
```

> `for` loops can also use loop statements, explained below.

### Loop statements

`break`, `continue` and the Loop `else` statements specific to loops in Python.

| Statement  | Description                                                       |
| ---------- | ----------------------------------------------------------------- |
| `break`    | Jumps out of the loop ~ "quits" the loop statement                |
| `continue` | Jumps to the top of the loop ~ to the loop’s header line          |
| `else:`    | Only if the loop is exited normally ~ i.e., without using `break` |

#### continue

We may write a loop that counts to ten but we only want it to print the even numbers.

```python
n = 0
while n <= 10:                  # test for n
    n += 1                      # adds 1 to n and reassigns
    if n % 2 != 0:              # if n is not even
        continue                # go to the top
    print(f'{n}', end = ' ')    # else print even number
                                # end=' ' prints n horizontally
# 2 4 6 8 10
```

#### break and else

We may want a loop that test `n` to be less than or equal to `20`, if `n` is an even number `and` greater than `17`, then print something and `break`. If the condition is not met, that is unable to find/reach an even number greater than 17, then `else` statement will be printed.

> Look at the comments in the code below, prefixed by #, for a line by line explanation.

```python
n = 0
while n <= 20:
    n += 1
    if n % 2 == 0 and n > 17:   # the first n divisible by 2 greater than 17
        print(f'{n} is 18!')    # will print
        break                   # and beak (not execute else)
else:                           # If the test in while were less than 18
    print(f'{n} is not 17')     # then this would print

# 18 is 18!
```

## The zip() built-in function

The `zip()` function is very useful for combining items in two separate list, specially if they are paired by position.

Lets create a "static multiplication" table for the number seven, static because I am going to hard code all the numbers in the tuples, there are ways of creating these list dynamically, we will learn more about that later. Right now we are just going to focus on the `zip()` function.

The two tuples have the same amount of objects, 10.

```python
tuple_1 = (1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
tuple_2 = (7, 7, 7, 7, 7, 7, 7, 7, 7, 7)
```

We are going to create a for loop and use the `zip()` function in the header.

* The `zip()` will return each positional pair, and the for loop will assign each object from the pair to `n1` and `n2` showned below.
* In the code block we can take each number, `n1` and `n2`, returned by the iteration and print it as well as create an expression.
* The loop will execute each pair until the tuples are exhausted.

> If the lists are not the same length, the `zip()` function will truncate the results to the shortest of the lists.

```python
for (n1, n2) in zip(tuple_1, tuple_2):
    print(f'{n1} x {n2} = {n1 * n2}')
```

The for loop, above, will print the follwing to the screen.

```cmd
1 x 7 = 7
2 x 7 = 14
3 x 7 = 21
4 x 7 = 28
5 x 7 = 35
6 x 7 = 42
7 x 7 = 49
8 x 7 = 56
9 x 7 = 63
10 x 7 = 70
```

* We were able to scan both tuples simultaneously with the `zip()` function.

* We can `zip()` more than two lists.

* If we wanted to do the same thing with out the `zip()`, it would have taken us more code using a `while` loop.

## Writing the Price List script

We learned to write loops and the zip function. Now we have to write our fruits price list.

* We need to write two Tuples.
* Write a for loop.
  * Include `zip()` function.
* Write the output format.

### The Tuples

We were given two "final lists", they don't need any modification for this project, the shop owner was very clear.

We should use a Tuple since the 'lists' don't need any modification. Lets create the Tuples

> This list of names and prices are paired by position

```python
  * fruits = ('Bananas', 'Apples', 'Lemons', 'Grapes', 'Nectarines', 'Oranges')
  * prices = (3.25, 3.0, 3.10, 2.50, 4.90, 3.80)
```

### Write the `for` loop

* In the header line of our `for` loop, we need to create two variables, `fruit` and `price`, these will hold each item of the pair returned by the `zip()` function during each iteration.

* In the same line, we write the zip() function, including each tuple name to be zipped.
  * `zip(fruits, prices)`

* The code block will print each returned pair until the tuples are done iterating.

```python
for (fruit, price) in zip(fruits, prices):
    print(f"{fruit}: \t ${price}")
```

### Write output format

We have most of the script done, we are just going to add a header and footer for better presentation.

#### Header

Instead of printing the header directly to the final display, we are going to assign it to a variable for flexability

```python
header = "-- Fruit Price List --"
```

#### Footer

The footer is just a count of the `header` multiplied by a dash `-`, we can modify the header and the footer will adjust.

```python
footer = len(header) * '-'
```

---

In the script below we have a couple of new expressions

* **Concatenation**: joining two string with a + sign into a new string.
* **Tab**: in a string `\t` expression, adds a tab

```python
fruits = ('Bananas', 'Apples', 'Lemons', 'Grapes', 'Nectarines', 'Oranges')
prices = (3.25, 3.0, 3.10, 2.50, 4.90, 3.80)

header = "-- Fruit Price List --"
footer = len(header) * '-'

print()
print(header + '+') # concatenation
print(footer + '+')
for (vegetable, price) in zip(vegetables, prices):
    print(f"{vegetable}: \t ${price}") # tab: \t
print(footer + '+')
```

The script will display

```cmd
-- Fruit Price List --+
----------------------+
Bananas:         $3.25
Apples:          $3.0
Lemons:          $3.1
Grapes:          $2.5
Nectarines:      $4.9
Oranges:         $3.8
----------------------+
```

This concludes our commissioned script for the Bodega owner, we will able to get $10.00 worth store credit. We get to move on now.

---

## Next tutorial

With our new found knowledge, we move on to the next town... TBA

## Things to try

* Try creating a for loop with `break` and `else` statements in the loop.
* Try adding more items to one of the Tuples and see what happens.

## Question

* What is string concatenation?
* What is the main use of a for loop?

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>