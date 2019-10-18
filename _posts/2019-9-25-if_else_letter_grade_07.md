---
layout: post
title: Letter grade - if Conditional Statement - 07
categories: [if, Comparison operators, Boolean operators, Multiway branching]
---

In this tutorial we are going to edit the previews Grade Calculator adding the code needed to display a letter grade. We will use the **conditional statement** `if` and **comparison operators** greater than or equal to, `>=` and greater than `>`.

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>

In our previous tutorial, a teacher asked us to create a Grade Calculator application, now she asks if we could add a letter grade next to the final grade.

we are going to need to know the following to compleat this task.

* The `if` Conditional Statement.
  * Comparison Operators.
  * Boolean Operators.
  * Multiway Branching.
* Writing the logic.
* Integrating code block into Grade Calculator.

## The `if` Conditional statement

Conditional statements, such as `if`, allow us to make choices based on preconditioned criteria.

We can use other statements to check the validity of these criteria such a **comparison operators**, such as `==`, allowing us to test for validity.

* In the example below, we want to test `if True == True`
  * if the test returns `True`, then
    * print "`Condition is True`"
  * if the test returns `False`, then
    * print "`Condition is False`"

```python
condition = True
if condition: # <==> if condition == True:
    print('Condition is True')
else:
    print('Condition is False')
```

> Try changing the value of `condition` to `False` in the example above


### Comparison Operators

We used the **equality** `==` operator above to check if a `condition` was equal `==` to `True`.

> Notice **equality** is indicated by double `==`, but variable assignment is indicated by `=`, cause of common human error at times when not used properly.

| Name                  | symbol |
| --------------------- | ------ |
| equality              | `==`   |
| inequality            | `!=`   |
| less than             | `<`    |
| less than or equal    | `<=`   |
| greater than          | `>`    |
| greater than or equal | `>=`   |
| membership            | `in`   |

Lets look at some examples of other **comparison operators**.

* **Inequality** `!=`

```python
>>> 5 != 5
False
```

* **Less than** `<`

```python
>>> 5 < 8
True
```

* **Membership** `in`

```python
>>> 5 in (2, 4, 5)
True
```

### Boolean Operators

We can also do multiple comparisons by using a boolean operator, lets use `or`, boolean because when used, it will return ether `True` or `False`

> BTW: `True == 1` and `False == 0`, try it!

```python
>>> True + 1
2
```

* By using the boolean operator, `or`, we can test if any of the two comparative statements below are `True`.
  * It returns `True` because one condition passed the test, `n < 10`.

```python
>>> n = 5
>>> 5 < n or n < 10
True
```

* When we use `and` both comparative statements tested, need to pass, for the statements to be `True`.
* In this case is `False`.
  * Because `5 < 5` is `False`
    * Immediately returning `False`.

```python
>>> n = 5
>>> 5 < n and n < 10
False
```

* An alternative to using the comparison `and` above, remove the `and` comparison and one the variable `n`.
  * This `5 < n and n < 10` is the same as `5 < n < 10`

```python
>>> n = 5
>>> 5 < n < 10
False
```

### Multiway Branching

Multiway Branching allows to have multiple conditions tested in a sequence by the statement `elif`, between the `if` and the `else` statements.

* `elif` stands for **if else**.
* `elif` is used to tie multiple `if` statements together.
* You can have any number of `elif` statements as you like.
* It will execute the first test is passed, in the case `True`.
  * Below none of the conditions are met until it reaches `color == "yellow"`.

> Notice how we are using the **f-string** format to pass the `{color}` variable.

```python
color = "yellow"
if color == "red":
    print(f"Apples are  {color}")
elif color == "green":
    print(f"Lemons are {color}")
elif color == "yellow":
    print(f"Bananas are {color}")
else:
    print(f"I can not match the color {color}")
```

We covered some of the necessary topics to begin to write our script.

* The `if` Conditional Statement.
  * Comparison Operators.
  * Boolean Operators.
  * Multiway Branching.

## Letter grade script

We use a 100 points scale and normally in the US we use a seven letter grade to represent the numerical scale.

So our later grade ranges would be:

| Letter | Grade scale |
| ------ | ----------- |
| A      | 90 to 100   |
| B      | 80 to 89    |
| C      | 70 to 79    |
| D      | 60 to 69    |
| F      | < to 60     |

For these many conditions to be tested, we would have to use Multi Branching, `elif` between the first `if` and the `else` statements.

We are going to say `if` `grade_average` is between **100** and **86** then it needs to return the **letter A** and so on down the line, with all the letter grades.

* We could write it like this:
  * `if 100 >= grade_average and grade_average >= 90:`.

* But we can shorten the line above by writing:
  * `if 100 >= grade_average >= 90:`.
    * `letter_grade = "A"`.
* `elif` states.
  * if `grade_average` is less than 90 but equal or greater than 80 then:
    * `letter_grade = "B"`.

Lets write the full conditional block.

```python
if 100 >= grade_average >= 90:
    letter_grade = "A"
elif 90 > grade_average >= 80:
    letter_grade = "B"
elif 80 > grade_average >= 70:
    letter_grade = "C"
elif 70 > grade_average >= 60:
    letter_grade = "D"
elif 60 > grade_average >= 0:
    letter_grade = "F"
else:
    letter_grade = "OOR" # Out Of Range
```

## Add code block to Grade Calculator

* We need to do two things:
  1. Add the conditional code block to the **Grade Calculator script**.
  2. And the `letter_grade` variable to the **f-string**.

* Lets copy the code block and paste it to the **Grade Calculator** just above the `print()` function.

* We can add our variable to the **f-string** in the `print()` function, right next to `{grade_average}`.
* We can put it in parenthesis to separate it a bit from the `grade_average`.
  * `({letter_grade})`

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

# You are here: Conditional block
if 100 >= grade_average >= 90:
    letter_grade = "A"
elif 90 > grade_average >= 80:
    letter_grade = "B"
elif 80 > grade_average >= 70:
    letter_grade = "C"
elif 70 > grade_average >= 60:
    letter_grade = "D"
elif 60 > grade_average >= 0:
    letter_grade = "F"
else:
    letter_grade = "OOR"

print(f'''
+{separator}+
 Student Name: {student_name}
+{separator}+
 lg: {lowest_grade} | hg: {highest_grade} | Final grade: {grade_average} ({letter_grade})
+{separator}+
 Semester grades:
 {sorted_grades}
+{separator}+
''')
```

When we run the program, we should get the following.

> Notice the **letter grade** after the **Final grade**.

```sql
+------------------------------------------------+
 Student Name: Beth O'Brien
+------------------------------------------------+
 lg: 75.3 | hg: 95.0 | Final grade: 84.7 (B)
+------------------------------------------------+
 Semester grades:
 [75.3, 75.8, 80.3, 83.5, 87.9, 89.5, 90.5, 95.0]
+------------------------------------------------+
```

---

## Next tutorial

A shop (bodega) owner wants you to print a price list of fruits and vegetables, the challenge, he has the names list separate from the price list

## Things to try

Having learned about `if` statements, comparison operators and boolean operators.

* Write your own if statement.
* use different comparison operators.

## Question

* Can you shorten the following statement?
  * `8 <= n and n < 15`
* When is the `elif` statement used?

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>