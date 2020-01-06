---
layout: post
title: Lesson 11-A - Custom module (import, function)
categories: [import, function, docstring, module, open()]
---

This is a two part lesson, in **Lesson 11-A** I will go over the new Python material needed to complete our project, and Lesson 11-B will be the implementation and complition of our project.

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>

In order to complete our project, writing a python module, we need to learn new Python concepts. Writing and formatting a script as a module, learn to open a text file, read its content, write a script importing the new module and making use of it.

* Custom functions.
* Writing a Python module.
* `open()` built-in function.
* Import a custom module.

## Custom function

Functions are the power house of most programming languages. They may go by different names in other programming languages but the 'function' is the same, a block of reusable code.

So far we have been writing sequential code, the script is executed in a linear fashion.

[<img src="{{ site.baseurl }}/images/secuential_code.svg" alt="sequential code" style="width: 400px;"/>]({{ site.baseurl }}/images/secuential_code.svg)

Functions allow us to write reusable code blocks. Functions are very flexible, as they allow us to use parameters further generalizing their use.

[<img src="{{ site.baseurl }}/images/function_order_of_execution.svg" alt="function execution" style="width: 400px;"/>]({{ site.baseurl }}/images/function_order_of_execution.svg)

> The function block is skipped until it is called, then the code in the function is executed.

We already have written much code that could be used as a function, writing a basic function is not difficult, just needs to be formatted properly.

* We first declare the function.
* We write the body of the function.
* And finally we call the function.

[<img src="{{ site.baseurl }}/images/quick_function.svg" alt="quick function" style="width: 500px;"/>]({{ site.baseurl }}/images/quick_function.svg)

### Declare a function

We must declare a function first. We do it by using the keyword `def`, follwed by a unique name, then parametric parenthesis and finish with colon. Function names have the same rules as variable names.

* `def` => **custom_name** => **Parenthesis** => **Colon**

```python
def function_name():
```

### Function code block

The code block belonging to a function is

* Right below the function definition.
* Indented (4 spaces).
* The return values must be presided by the keyword `return`.

```python
def function_name():
    return 'function name'
```

### Function call

You can call your function at any time by calling the function name, just as we call built-in functions.

```python
print(function_name())

function name # returned by hello()
```

### Function DocString

A function Docstring is a short description of what the function does, placed right below the function declaration in quotes.

* `""" returns the string function name """`

```python
def function_name():
    """ returns the string `function name` """
    return 'function name'
```

> Note: Function Docstrings are important as they help us remember what the function does when used at a later time, or when shared with other programmers. Most helpfull when importing a function from a module.

### Function positional arguments

As we make a function more flexible and general, we can pass arguments.

* Positional arguments are passed in the parenthesis of a function definition.
* A function can take these argument values and use them as needed to return a response.

```python
def str_multiply(s, i):
    """Takes a string and multiplies the value of
    multiplyer.
    s : must be a string
    i : must be an integer"""
    return str(s) * int(i)
```

As you can see from the Docstring above, the function takes two positional arguments, `s` (must be a string) and `i` (must be an integer).

We call the function and pass the two positional arguments inside the parenthesis, separated by a coma, as required.

They are **positional** because the must be `s` first and then `i` in the function call.

```python
s = 'string'
i = 4
sti = str_multiply(s, i)
print(sti)

stringstringstringstring # returns the string
```

> **Note:** If we were to first pass `i` and then `s` as arguments, our function would return an error, because it was expecting the second position to be an integer.

```python
s = 'string'
i = 4
sti = str_multiply(i, s)  # notice reversed order

"""
...
TypeError: can't multiply sequence by non-int of type 'str'
"""
```

### Function keyword arguments

Python also offers, other types of function arguments among them are the **keyword** arguments.

* `def func(foo, bar=None):`

Notice `bar` above has a default value of `None`.

> Notice the keyword (bar) argument, in the example below.

```python
>>> def keyword_func(foo, bar='default'):
...    """Returns the values for foo and the optional bar"""
...    return foo, bar
```

> Note: the code above is shown in the interpreter (`>>>`), but you might want to write it in your IDLE and save it as a script, then execute.

Below, lets call the `keyword_func()` function and passing two arguments.

```python
>>> keyword_func(45, bar='the weekend')  # pass your own bar value
(45, 'the weekend')
```

If we don't pass a keyword value for `bar`, then the function will return the **"default"** value for `bar`.

```python
>>> keyword_func(45)
(45, 'default')
```

There is a lot more to functions, you can call another function from with-in a function. I'll cover that topic as we move forward.

## Writing a Python module

As I stated before, all scripts in python are modules, but to properly use them we should learn how to format a file for better module deployment.

We can say a module has a header, body and footer.

[<img src="{{ site.baseurl }}/images/python_module.svg" alt="Python module" style="width: 400px;"/>]({{ site.baseurl }}/images/python_module.svg)

### The header

All scripts should begin with a description of what it does at the top.

> Note: Python 3.x uses utf-8 so it isn't necessary to specify it in the header.

```python
""" This is the module description,
and goes at the top of the file"""

# import <some_module> if needed
```

We can also import modules right after the description

### The body

Here we instantiate any code, set constants and write our module functionality.

```python
# ----------- Header -----------+
""" This is the module description,
and goes at the top of the file"""

# import <some_module> if needed

# ----------- Body -------------+
def func_a():
    """ Prints a string """
    print('function A')


def func_b():
    """ Prints a string """
    print('function B')
```

### The footer

This is particularly important as it changes the programming paradime a bit.

In python all scripts are modules, we can run them as stand alone (what we have done so far).

To write a modular script, we have to let the Python interpreter know weather is being run as a module or a stand alone, or it might execute some code we wrote for the stand alone version.

For this we write a footer, which is a line of Python code, anything below this line will make use of the functions in the body, if called.

But if we import the script into another script as a module, anything below this like will not execute.

* `if __name__ == '__main__':`

This means, if the name of the file is ran as the main script, then use the code below that line, if not, as in the case when imported into another script, don't use any of the code below that line.

> Notice the `:` at the end of the line, which means any code that follows below must be indented.

```python
# ----------- Header -----------+
""" This is the module description,
and goes at the top of the file"""

# import <some_module> if needed

# ----------- Body -------------+
def func_a():
    """ Prints a string """
    print('function A')


def func_b():
    """ Prints a string """
    print('function B')


# ----------- Footer -----------+
if __name__ == '__main__':
    func_a()
    func_b()
```

This code is not very different than what we have written before, but because we are using functions we can call them from anywhere in the script, so it can be formatted this way.

* Lets call this script `my_module.py`, go head, **save it** and **run it**.

If we import this script into another script, then the code below the line `if __name__ == '__main__':` would not be executed, leaving us the functions in the body available for our other code.

What it means, that this script serves a dual purpose as a stand alone script and as a module, as Python intended.

## Open() built-in function

As our applications expand, we will have to access other file formats, other than `.py` files, such as `.txt`, `.csv`, `.pdf`, `.db` and many other file formats.

[<img src="{{ site.baseurl }}/images/open_function.svg" alt="Open() file function" style="width: 400px;"/>]({{ site.baseurl }}/images/open_function.svg)

For this we can use the `open()` built-in function, notice they are the same as custom functions. Notice how the function takes a positional argument and the rest are keyword arguments.

```python
open(file, mode='r', buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None)
```

* where `file` is the file path.
* `mode` is the type of action we want on the file
  * `r` stand for **open for reading**.
* The rest of the keyword arguments don't have to be passed, the defaults are find for most uses.

Character | Meaning
----------|--------
'r' | open for reading (default)
'w' | open for writing, truncating the file first
'x' | open for exclusive creation, failing if the file already exists
'a' | open for writing, appending to the end of the file if it exists
'b' | binary mode
't' | text mode (default)
'+' | open a disk file for updating (reading and writing)

Lets write a short script that will open a text file.

* In the same directory as the `my_module.py` create a text file and name it `my_string.txt`.
  * Add some arbitrary text to the file, save it and close it.
* Create a new script file and name it `top_level.py` and save it in the same directory as the two other files.

```txt
DIRECTORY STRUCTURE
-------------------
|-- project_directory
    |-- my_module.py
    |-- my_string.txt
    |-- top_level.py
```

Lets write the script that will open `my_string.txt`, Open the `top_level.py` script file and write the following.

```python
""" This script will open a text file and print the contents"""

string_file = open('my_string.txt', 'r')
read_string = string_file.read()
```

* In the code above we open() the `'my_string.txt'` file in `r` mode and assign it to the `string_file` variable. It only opens the file in the selected mode.
* To read the file use the method `.read()` on `string_file` and we assign it to `read_string`.

To print `read_string` we can use the `print()` function.

```python
""" This script will open a text file and print the contents"""

string_file = open('my_string.txt', 'r')
read_string = string_file.read()

print(read_string)

string_file.close()

# prints:
'What ever your wrote in the file'
```

> **Notice:** above we close the `my_string.txt` file by using the `.close()` method.
> * `string_file.close()`

Opening an external file is relatively easy.

## Import a custom module

Importing a custom module is no different than importing a built-in module, with the exception we must be mindfull of the file path.

* But because we have all our files in the same folders, this should not be a problem*
* All we have to do is write import followed by the file name **with out** the **file extention**.
  * And because it is in the same directory as the file importing it, we don't have to worry about directory path.

* We can give the module name an alias to make it easier to write in the rest of out script by using `as` after the module name followed by the alias.

```python
import my_module as mm
```

Now that we have imported the module as mm we can start using it's functions. Remember what they are?.

If you don't member you can use the `help()` function and it will return the **Docstring** you wrote in your module.

```python
print(help(mm))

# oops we should write descriptive short descriptions.
# It as two functions, func_a() and func_b()
"""Help on module mm:

NAME
    my_module

DESCRIPTION
    This is the module description,
    and goes at the top of the file

-- More  --
"""
```

### Using the mm module

* Lets continue using our `top_level.py` script.
* import `my_module`
* After we open the txt file we are going to use `func_a()` and `func_b()`
* To call the functions in **mm** we have to use the prefix `mm`
  * `mm.func_a()`

```python
""" This script will open a text file,
based if a character is found in the text file
the script will print an imported function"""

# import module
import my_module as mm

string_file = open('my_string.txt', 'r')
read_string = string_file.read()

# call functions from mm
function_A = mm.func_a()
function_B = mm.func_b()

if 'a' in read_string:
    print(function_A)
else:
    print(function_B)

string_file.close()
```

* The script above will import `my_module` as `mm`
* Open `my_string.txt` in `r` mode assign to `string_file`
* Read `string_file` and assign to `read_string`
* Assign `mm.func_a()` and `mm.func_b()` to respective variables
* If the character `'a'` is found in `read_string`
* print `function_A` else print `function_B`
* close `string_file`

> Note: notice how the code we had below the line
> * `if __name__ == '__main__':` in `my_module.py` is not used at all when imported as a module into a script.

We learned to

* Write a custom functions
* Writing a Python module
* Use the open() built-in function
* Import a custom module

---

## Next tutorial

We are going to continue with **Lesson 11-B** and write our project based on what we learned here.

## Things to try

Can you research and find out what other types of parameters a function takes?, we cover positional and keyword.

Look up how to import a module found in a different directory other than where is being imported.

## Question

* If a function is not called, does it still execute?
* How would you go about calling a function from another function?

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>
