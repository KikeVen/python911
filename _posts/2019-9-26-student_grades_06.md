---
layout: post
title: Student Grade Calculator, Tuples, f-string, built-in function - 06
categories: [Tuples, f-string, sorted (), min (), max (), sum (), len ()]
---

In this tutorial we are going to write an application allowing us to calculate the lowest, highest and average grade of a student, then displaying the results with some formatting for better visual representation.

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>

We will do this by providing you with two variables, the **student's name** and **her/his grades**. We will continue to use built-in functions to calculate the results and then use some basic string formatting to show (echo) the results.

> Although we are using built-in functions for these examples. We will have to learn to do what some of these basic built-in functions accomplish by using conditional statements, loops, none-primitives.

What we need in order to write the program

* Tuples
* Built-in functions: `sorted()`, `min()`, `max()`, `sum()` and `len()`
* Output formatting
* Write the program

You work at a school's IT departament, a teacher asked you to write a simple program that will calculate the lowest, highest, average grade and return the grades sorted of a given students. The grades are final, so they don't have to be edited.

* Go!

>Student information:
>
> * **Student's grades:** 89.5, 80.3, 90.5, 75.8, 95.0, 75.3, 83.5, 87.9
> * **Student's name:** Beth O'Brien

## Tuples

Up until now we have assigned a single value to a variable but we need to assign all the student grades to one variable, we do this by using a non-primitive type container, there are several as you can see by our diagram, in this case we are going to use a **Tuple** since we don't have to manipulate each grade and **Tuple** is non-mutable.

* **Non-primitive types** are containers or "lists" for multiple objects
* All **except Tuples** are mutable, meaning they can be updated
* Any non-primitive can have multiple types in it `int`, `str`, `float` and so on

[<img src="{{ site.baseurl }}/images/non-primitives.svg" alt="alt" style="width: 700px;"/>]({{ site.baseurl }}/images/non-primitives.svg)

So we can use a **Tuple** to host all the student's grades. A tuple can be represented by all the values, separated by commas`,`, inside parenthesis `()`

If we open an **Interactive session** in **IDLE** and type the following we can see this "list" of grades is typed as a `tuple`

```python
>>> student_grades = (89.5, 80.3, 90.5, 75.8, 95.0, 75.3, 83.5, 87.9)
>>> type(student_grades)
<class 'tuple'>
```

* If you assign the "list" of grades to a variable without the parenthesis, **Python** will **automaticall** type them as **Tuples**.

* Python is a **dynamic type** language, you can assign a value to a variable and Python will automatically type the value.

* This is unique to Python, in other programming languages the programmer has to specify the type.

> In comparison Python is like an automatic car, where you don't have to press the clutch to shift gears

Try it in your IDLE interactive session:

* Notice there are no parenthesis in our tuple below

```python
>>> student_grades = 89.5, 80.3, 90.5, 75.8, 95.0, 75.3, 83.5, 87.9
>>> type(student_grades)
<class 'tuple'>
```

> **Tuples** can contain all primitives, non-primitives and any other type of object. Remember if you have a list of names (strings) they must be in quotes and separated by commas `,`.

```python
students_name = ("Andy", "Mary", "Jesse", "Steven")
```
## Built-in functions

We are going to introduce a few new **built-in functions** and combine them with others we have used before to write our application.

These functions are little **code packages** allowing us to do sertain tasks with out having to write the entire logic our selves, we will start writing our own detailed logic in the next tutorial

If we use the following built-in functions on a Tuple they would do as described below.

| Function   | Description                                         |
| ---------- | --------------------------------------------------- |
| `len()`    | Returns Length of an Object                         |
| `min()`    | Returns the smallest Object                         |
| `max()`    | Returns the largest Object                          |
| `sum()`    | Returns the sum from a given non-primitive ("list") |
| `sorted()` | Returns a sorted "list" from a given iterable       |

### len()

As mentioned the `len()` function will return the length of a non-primitive iterable Object in our case a **Tuple**.

* the `len()` function will try to iterate though each object inside our `Tuple` or anyother non-primitive.

Our grades must have the correct **Data Type** for the functions to work properly.

If we try to use a function like `len()` with a single value it would give us an error.

```python
>>> grade = 89
>>> len(grade)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: object of type 'int' has no len()
```

Notice the last line of the error `TypeError: object of type 'int' has no len()`. It is clear Python was looking for the correct type object.

If we convert that single value variable into a **Tuple** containing a single value, then the `len()` built-in function will work.

* We can do this by putting the single value inside parenthesis `()`
* This tells python you are passing a "list", in this case a **Tuple** of a single object
* The `len()` built-in function will accept it now.

```python
>>> grade = (89)
>>> len(grade)
1
```

> You can also write a single value Tuple in the following form `grade = 89,` - notice the comma `,` after the single value. Reffer to the Tuple example above with no parenthesis

But more specifically to our case, we want the length of our grades.

```python
>>> student_grades = (89.5, 80.3, 90.5, 75.8, 95.0, 75.3, 83.5, 87.9)
>>> len(student_grades)
8
```

### min() and max ()

These two functions will return the **highest** and **lowest** grades respectivley.

```python
>>> student_grades = (89.5, 80.3, 90.5, 75.8, 95.0, 75.3, 83.5, 87.9)
>>> min(student_grades)
75.3
>>> max(student_grades)
95.0
```

> If we were to "open the hood" of each of these built-in functions, we would see a lot of code and calls to other functions.

### sum()

The sum() built-in function cycles or (loops) through each of the grades adding them all up and returning the total.

```python
>>> student_grades = (89.5, 80.3, 90.5, 75.8, 95.0, 75.3, 83.5, 87.9)
>>> sum(student_grades)
677.8000000000001
```

> What built-in function would you use to shorten the number of decimals to one place?.

If you weren't using a built-in function to get the sum of a "list", it might look something like this to get the sum of a "list". It would require something call a `loop` and proper indentation which we will cover in our next tutorial.

```python
>>> student_grades = (89.5, 80.3, 90.5, 75.8, 95.0, 75.3, 83.5, 87.9)
>>> grade_sum = 0
>>> for grade in student_grades:
...     my_sum = grade_sum + grade
>>> my_sum
677.8000000000001
```

### sorted()

The `sorted()` built-in function will return a copy of the Tuple with sorted grades, from the smallest to the largest grade.

```python
>>> student_grades = (89.5, 80.3, 90.5, 75.8, 95.0, 75.3, 83.5, 87.9)
>>> sorted(student_grades)
[75.3, 75.8, 80.3, 83.5, 87.9, 89.5, 90.5, 95.0]
```

## Output format

We have to think how we are going to visually represent the data to the user. We are going to use something relatively new in Python called the **f-string** (formatted string literals), introduced with Python 3.6, to format the output of our program.

There are two other types of older string formatting  you will encounter and should know. `%-formatting` and `str.format()` we will see these two at a later point.

F-strings allow us to imbed an expression inside a string.

* f-string embed expressions inside a string literel using **brackets** `{}`.
* f-string are easier to use.
* f-strings execute faster than the other two types of string formatting.


```python
>>> student_name = "Beth O'Brien"
>>> f"Student name: {student_name}"
```

So the code above would print to screen as follow, where the variable in **brackets** `{student_name}` gets replaced by its value.

```tex
Student name: Beth O'Brien
```

That is it for the theory portion, lets start coding our program.

## Student Grade Calculator (SGC)

Lets open a new document in IDLE. Under **File**, select **New document**. You might want to save it to a projects folder. IDLE should put the correct file extention at the end of you document `.py`

### Program Description

At the top of your document you want to write a short description of your application within triple quotes.

```python
"""
Calculate the lowest, highest and average grade of a student
"""
```

### Assign given values

Assign the values I gave you to variables, **Student's name** and **Grades**.

```python
"""
Calculate the lowest, highest and average grade of a student
"""
student_grades = (89.5, 80.3, 90.5, 75.8, 95.0, 75.3, 83.5, 87.9)
student_name = "Beth O'Brien"
```

### Calculate requested values

Now lets calculate some of the requested values, **highest grade**, **lowest grade**, **sorted grades** and **the sum of the grades** to calculate the **average** which will give us the **final grade**.

1. Start by writing variable names which will represent the **returned value**.
2. **Assign** the the **built-in function** to the **variable** at the same time **passing** the appropriate **value as parameters** to the functions.
   1. `lowest_grade = min(student_grades)`.

```python
"""
Calculate the lowest, highest and average grade of a student
"""
student_grades = (89.5, 80.3, 90.5, 75.8, 95.0, 75.3, 83.5, 87.9)
student_name = "Beth O'Brien"

# You are here: built-in function assignment
lowest_grade = min(student_grades)
highest_grade = max(student_grades)
sum_grade = sum(student_grades)
number_of_grades = len(student_grades)
sorted_grades = sorted(student_grades)
```

### Calculate grade average

Now lets write the expression to calculate the grade average.

1. We need to take the **sum_grade** and divide it by **total number of grades**.
   1. `sum_grade/number_of_grades`.
2. We need to round it to a single decimal point.
   1. `round(sum_grade/number_of_grades, 1)`.
3. We need to assign it to a variable.
   1. `grade_average`.

```python
"""
Calculate the lowest, highest and average grade of a student
"""
student_grades = (89.5, 80.3, 90.5, 75.8, 95.0, 75.3, 83.5, 87.9)
student_name = "Beth O'Brien"

lowest_grade = min(student_grades)
highest_grade = max(student_grades)
sum_grade = sum(student_grades)
number_of_grades = len(student_grades)
sorted_grades = sorted(student_grades)

# You are here: expression calculating grade average
grade_average = round(sum_grade/number_of_grades, 1)
```

### Format output

Lets format and print the results to screen, we would like it to look like this:

```pre
+------------------------------------------------+
 Student Name: Beth O'Brien
+------------------------------------------------+
 lg: 75.3 | hg: 95.0 | Final grade: 84.7
+------------------------------------------------+
 Semester grades:
 [75.3, 75.8, 80.3, 83.5, 87.9, 89.5, 90.5, 95.0]
+------------------------------------------------+
```

#### First lets make our horizontal separator

```pre
+------------------------------------------------+
```

We can use the **total number of characters** in the `sorted_grades` variable as a guide to create the correct legnth horizontal line.

In order to get a total count of all characters, first we convert `sorted_grades` to a string and then getting the count by using the `len()` function.

* `len(str(student_grades))`.

Lets assign it to a variable.

* `line_length = len(str(student_grades))`.
  * For this number set it will produce `48`.

> The number of grades in the Tuple, will determine the size of the horizontal line.

```python
"""
Calculate the lowest, highest and average grade of a student
"""
student_grades = (89.5, 80.3, 90.5, 75.8, 95.0, 75.3, 83.5, 87.9)
student_name = "Beth O'Brien"

lowest_grade = min(student_grades)
highest_grade = max(student_grades)
sum_grade = sum(student_grades)
number_of_grades = len(student_grades)
sorted_grades = sorted(student_grades)

grade_average = round(sum_grade/number_of_grades, 1)
# You are here: line_length
line_length = len(str(student_grades))
```

We can use this variable to draw the horizontal line. If we multiply a string, i.e `-`, by `line_length` it will output that string multiplied by the value of our variable, `line_length`.

This is **unique to Python**, because it knows is **a string** and when you **multiply** by a **given interger**, instead of giving you an error, it will take the string and print it that many times.

```python
>>> '-' * line_length
------------------------------------------------
```

We can assign all this to a variable.

* `separator = '-' * line_length`.

Lets add it to our program.

```python
"""
Calculate the lowest, highest and average grade of a student
"""
student_grades = (89.5, 80.3, 90.5, 75.8, 95.0, 75.3, 83.5, 87.9)
student_name = "Beth O'Brien"

lowest_grade = min(student_grades)
highest_grade = max(student_grades)
sum_grade = sum(student_grades)
number_of_grades = len(student_grades)
sorted_grades = sorted(student_grades)

grade_average = round(sum_grade/number_of_grades, 1)

line_length = len(str(student_grades))
# You are here: line separator
separator = '-' * line_length
```

#### Printing formatted results to screen

We are going to use the f-string to format our output.

* We will use triple quoats for multiple lines
* we will add the `+` character inside the **f-string** to the front and end of f-string parameter `+{separator}+` .

Lets add the `print()` to the **f-string**.

```python
"""
Calculate the lowest, highest and average grade of a student
"""
student_grades = (89.5, 80.3, 90.5, 75.8, 95.0, 75.3, 83.5, 87.9)
student_name = "Beth O'Brien"

lowest_grade = min(student_grades)
highest_grade = max(student_grades)
sum_grade = sum(student_grades)
number_of_grades = len(student_grades)
sorted_grades = sorted(student_grades)

grade_average = round(sum_grade/number_of_grades, 1)

line_length = len(str(student_grades))
separator = '-' * line_length

# You are here: print formatting
print(f'''
+{separator}+
 Student Name: {student_name}
+{separator}+
 LG: {lowest_grade} | HG: {highest_grade} | Final Grade: {grade_average}
+{separator}+
 Semester Grades:
 {sorted_grades}
+{separator}+
''')
```

When you run the program it should print the results as formatted.

```txt
+------------------------------------------------+
 Student Name: Beth O'Brien
+------------------------------------------------+
 LG: 75.3 | HG: 95.0 | Final Grade: 84.7
+------------------------------------------------+
 Semester Grades:
 [75.3, 75.8, 80.3, 83.5, 87.9, 89.5, 90.5, 95.0]
+------------------------------------------------+
```

That is it for our grade calculator program, it is very basic, but I got a chance to introduce some new programming concepts.

---

## Next tutorial

We are going to assign a letter grade to the student based on their `grade_average`, I will introduce `for loop` and `while loop`.

## Things to try

* In the line generator portion, change the width of the line by adding or removing grades from the Tuple.

## Question

* Why did we put the student_name string in double quotes? What if you changed it to single quotes and ran the program?
* What would happen if we didn't convert the `student_grades` to a string in `line_length`?

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>