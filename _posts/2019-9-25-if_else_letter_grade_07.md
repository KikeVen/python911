---
layout: post
title: Letter grade - if Conditional Statement - 07
categories: [if, Comparison operators, Boolean operators, Multiway branching]
---

In this tutorial we are going to edit the previews grade calculator and add letter grades to be display right next to final grade average. We will use the **conditional statement** `if` and **comparison operators** `>=` and `>`.

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>

Our teacher now asked if we could add the letter grade next to the final grade and for that we are going to need to know the following.

* The `if` Conditional Statement.
  * Comparison Operators.
  * Boolean Operators.
  * Multiway Branching.
* Writing the logic.
* Integrating code block into Grade Calculator.

## The `if` Conditional statement

Conditional statements allow us to make choices based on preconditioned criteria. We can use other statements to check the validity of these criteria such a **comparison operators** in order to return the correct response.

```python
condition = True
if condition == True:
    print('Condition is True')
else:
    print('Condition is False')
```

* Assign value to variable, `condition = True`.
* Write conditional statement
`if condition == True:`.
  * Notice `:` above, denotes end of statement.
  * Anything indented below the condition statement will be executed if the condition is met.
    * `print('Condition is True')`.
  * Python indentation is standard to 4 spaces.
* The `else` statement executes if the conditions above were `not` met.
  * Again `:` signify end of statement.
  * And the code to execute for the `else` statement is indented four spaces.
    * `print('Condition is False')`.

### Comparison Operators

We used the equality `==` operator above to check if a `condition` was equal `==` to `True`.

>Notice **equality** is dented by double `==`, but variable assignment is dentoed by `=`, cause of human error at times when not used properly.

| Name                  | symbol |
| --------------------- | ------ |
| equality              | `==`   |
| inequality            | `!=`   |
| less than             | `<`    |
| less than or equal    | `<=`   |
| greater than          | `>`    |
| greater than or equal | `>=`   |
| membership            | `in`   |

Lets look at some example using other **comparison operators**.

* Inequality `!=`

```python
>>> n = 5
>>> n != 5
False
```

* Less than `<`

```python
>>> n = 5
>>> n < 8
True
```

### Boolean Operators

We can also do multiple comparisons by using a boolean operator lets use `or` remember your keyword list?

* by using `or` we are comparing if any of ether are statements are `True`.

```python
>>> n = 5
>>> 5 < n or n < 10
True
```

* When we use `and` we are comparing both statements on ether side of the `and` are `True`.

```python
>>> n = 5
>>> 5 < n and n < 10
False
```

* Another way of using the `and` comparison above, remove the `and` comparison and the variable `n`.

```python
>>> n = 5
>>> 5 < n < 10
False
```

### Multiway Branching

Multiway Branching allows to have multiple conditions tested in a sequence tied by the statement `elif` between the `if` and the `else` statements.

* `elif` stands for **if else**.
* `elif` is used to tie multiple `if` statements together.
* You can have any number of `elif` statements as you like.
* It will execute the first test is passed, in the case `True`.
  * Below none of the conditions are met until it reaches. `color == "yellow"`

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

This covers the necessary material to move on to our letter grade script.

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

So to write the if statements, we would use Multi Branching.

We are going to say `if` `grade_average` is between 100 and 86 then it needs to return the letter A and so on down the line with all the letter grades.

* We could write it like this:
  * `if 100 >= grade_average and grade_average >= 90:`.

* But we can shorten the line above by writing:
  * `if 100 >= grade_average >= 90:`.
    * if `grade_average` is between 90 and 100.
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

We need to do two things, add the conditional code block to the Grade Calculator script and the `letter_grade` variable to the **f-string**.

* lets copy the code block and paste it to the Grade Calculator just above the `print()` function.

* We can add our variable to the f-string in the print() function, right next to the grade.
  * `({letter_grade})`
  * We can put it in parenthesis to separate it a bit from the `grade_average`.

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

When we run the program, we should get the following, notice the **letter grade** after the **Final grade**.

```python
'''
+------------------------------------------------+
 Student Name: Beth O'Brien
+------------------------------------------------+
 lg: 75.3 | hg: 95.0 | Final grade: 84.7 (B)
+------------------------------------------------+
 Semester grades:
 [75.3, 75.8, 80.3, 83.5, 87.9, 89.5, 90.5, 95.0]
+------------------------------------------------+
'''
```

---

## Next tutorial

TBA (multiplication table?)

## Things to try

Having learned about `if` statements, comparison operators and boolean operators.

* Write your own if statement.
* use different comparison operators.

## Question

* Can you shorten the following statement?
  * `8 <= n and n < 15`
* When is the `elif` statement used?

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>