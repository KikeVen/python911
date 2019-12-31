---
layout: post
title: Lesson 10 - Language processing (Strings, Lists, Dictionaries)
categories: [import, .maketrans(), .translate(), Counter(), .most_common()]
---

As part of a larger NLP (Natural Language Processing) project, we have been ask to clean up some text, by converting Strings to Lists, and do some basic language classification.

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>

> **Important**: This is not an NLP tutorial, this is an introductory Python lesson.

Although most NLP research, projects and products rely on pre-built libraries and can be very complex in nature, I am going to introduce some basic NLP consepts to illustrata how we can apply, what we are learning, to real world scenarios.

One of the biggest challenges in data analysis, is getting the data to a state that can be useful. In our particular case, we have been ask to write some code to pre-process some text and do some basic calculations.

> With what we know and what we will learn in this lesson, we can already do some pretty powerfull things, I hope this is enough incentive for you to continue learning Python.

* Project description
* Understanding the requirements
* Learning required Python concepts
  * Module import
    * string
      * .maketrans()
      * .translate()
    * collections
      * Counter()
        * Dictionaries
      * .most_common()
        * lists
  * string methods
    * .lower()
    * .split()
    * .remove()
* Logic outline
* Writing the script

## Project description

Write a script that can take a given, arbitrary string, 'clean it up' and return a **Word Frequency** (term for word count). It should return a list with pair tuples of word paired with frequency. Should be unpackable to be use with other operations.

## Understanding the requirements

Before we can begin programming, we need to understand the project description.

If we search the internet, we could find all the elements necessary to compleat this project, the challenge is, putting together all the fragmented information into a coherent algorithm and working script.

Having a code outline is very important, as it provides, an initial road map to our application.

Here is a diagram of what we are looking to accomplish.

[<img src="{{ site.baseurl }}/images/word_frequency.svg" alt="alt" style="width: 700px;"/>]({{ site.baseurl }}/images/word_frequency.svg)

* We need to normalize the input string, we can do this by turning the string to all lower case.

* We need to remove none critical characters, such as punctuations.

* We also need to remove common words that don't add value to this project, these are reffered as **Stop words**, such as **in**, **to**, **do**, **a**, **it**, **get** and so on.

* In order to do a word count, we need to be able to iterate through a list of words, but we are given a string, and we can only iterate through each character. We need to learn how to convert a string to a group of words or (**Tokenize** the string)

* Once we have pre-processed the text, we will have to get the actual word count (**Word Frequency**) from our input string.

* We have to format the return values for displaying

> We will write a more detailed outline or algorithm, after we learn some new Python concepts.

## Learning required Python concepts

As usual, I will introduce some new Python concepts, in order to complete our new project.

### Module import

One of the more powerfull Python features is the ability to make use of other scripts, as a matter of fact, all scripts in Python are considered modules. This means they can be imported and used in other scripts.

Python comes with a built-in library, by importing them into our script, we can extend the capabilities of Python.

[<img src="{{ site.baseurl }}/images/import.svg" alt="alt" style="width: 700px;"/>]({{ site.baseurl }}/images/import.svg)

At the top of our script we write `import`, followed by the module name.

There are a few ways to import modules into our own programs, bellow are two examples.

```python
import <module>
from <module> import <function, class or method>
```

We can then access it's functionality through our script.

> We can also install and import libraries made by others, third party libraries. We will cover these at a later point.

#### string module

The string module is built-in and we have to import it before we can use its functionalities.

```python
import string
```

* `str` Creates a new string object from the given object.
* `.maketrans("","","")` creates a **translation table**, takes three arguments, if the first two are left blank, then the third will map to none, resulting in the removal of the set characters in the third argument.

```python
translation_table = str.maketrans("","","-!.,")
```

---

> Python offers a constant listing the most commun characters in a string with `string.punctuation`

```python
>>> import string
>>> string.punctuation
'!"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~'
```

If we want to add another character not found in `string.punctuation` we could _concantenate_ it with the missing characters for instance `A`.

```python
import string
punctuation = string.punctuation + '•'
print(punctuation)
# !"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~•
```

We can then use the new `punctuation` string with our `str.maketrans()` method

```python
import string
punctuation = string.punctuation + '•'
translation_table = str.maketrans("","", punctuation)
```

---

* `string.translate(translation_table)`, "Replace each character in the string using the given translation table. Characters mapped to None are deleted." - _Python documentation_

```python
>>> string = "the@ man@ on@ the@ moon@!"
>>> translation_table = str.maketrans("","",translation_table)
>>> translated_string = string.translate(translation_table)
>>> translated_string
'the man on the moon!'
```

#### Collections module

From the `collections` module, another built in library , we'll use the `Counter()` function and the `.most_common()` method to count word frequency, sort and return the most commun values.

* `Counter()` Elements are stored as **dictionary** keys and their counts are stored as dictionary values. count elements from a string.

> **A dictionary:** is similar to a tuple, but a dictionary is mutable. Is defined by `{ }`. Dictionaries hold a pairs of `key`, `value`. Represented as {k1: v1, k2: v2, k3: v3}

```python
>>> from collections import Counter
>>> string_x = 'xnnabxbtynxax'
>>> Counter(string_x)
Counter({'x': 4, 'n': 3, 'a': 2, 'b': 2, 't': 1, 'y': 1})
# Above sample of a dictionary { }
```

> **A list:** much like tuples, lists are sequences of anything. Unlike tuples lists are mutable. they can be modified. They can have from zero to more elements. They can hold objects of any type. List are normally represented by `[]` or `list()`. Later I'll have a tutorial about lists and dictionaries.

* `.most_common()` List the `n` most common elements and their counts from the most common to the least. If n is `None`, then list all element counts.

```python
>>> from collections import Counter
>>> string_x = 'xnnabxbtynxax'
>>> Counter(string_x).most_common(3) # <== method
[('x', 4), ('n', 3), ('a', 2)]
# Returns the three most common inside a list [ ]
```

> Above we can see a list of tuples. Tuples are not mutable, but the list holding them is mutable.

### string methods

As per our **_String Tutorial_**, they perform a procedure on a specific string object.

#### .lower()

It returns a string with all lower case.

```python
>>> y = 'ReaDAbiLity CouNts.'
>>> y.lower()
'readability counts.'
```

#### .split()

The `.split()` method, splits a string into a list.

> We can specify the separator, by default any white space is the separator.

```python
>>> str_txt = "Today the temperature was 85, when normally is in the low 70s"
>>> str_txt.split()
['Today', 'the', 'temperature', 'was', '85,', 'when', 'normally', 'is', 'in', 'the', 'low', '70s']
```

#### .remove()

The `.remove()` method removes a given object from a list. This method does not return any value.

```python
>>> split = str_txt.split()
>>> remove = split.remove('the')
>>> print(remove)
['Today', 'temperature', 'was', '85,', 'when', 'normally', 'is', 'in', 'the', 'low', '70s']
```

> Notice in `split` the first 'the' has been removed, if we want others remove, we would have to iterate through 'split' and remove each instance of the word.

## Logic outline

To further manipulate strings we can make use of the `string` build-in library. We first need to import it. We will also make use of another build-in library called `collections` to help us sort our results

1. `import` `string` and `collections`
2. Assign given string to variable, `input_string`
3. Turn `input_string` to all lower case, using `.lower()` method and assign to `lower_str`
4. Create a list of unnecessary characters by using the `str.maketrans()` method, assign to `char_template`
5. Remove unnecessary characters from `lower_str` using `.translate()` method and `char_template` as argument
6. Turn the new string into a list by using `.strip()` method
7. Create a tuple to hold a list of stopwords, `stopwords = ()`
8. Write loop to remove stop words from `word_list`
9. Use subclass `Counter()` to count frequency of words
10. Use `.most_common()` to list only the n most common elements
11. `for` loop to unpack and format the tuple list from sorted list

## Writing the script

We now have all wee need to write our script.

1. A project description
2. An understanding of what is required
3. An outline

Lets begin by importing our modules.

> Lets continue describing our script by using inline comments inside the script. In line comments start with `# <comment>`.

```python
import string
from collections import Counter

# The import string is assign to a variable using
# triple quotes, as it is a long string, it may
# have single and double quotes.
input_string """

"""

# We can normalize our string by using the
# .lower() method
lower_str = input_string.lower()

# Create a translation table, to be use with the
# .translate() method
remove_string = string.punctuation + '•'
char_template = str.maketrans("", "", remove_string)

# We'll use the .translate() method to remove unnecessary
# characters defined in our translation table.
cleanned_str = lower_str.translate(char_template)

# Convert our string to a list by using the
# .split() method returning a list of words
# sparated by comas
word_list = cleanned_str.split()

# We create a tuple with our stop words
stopwords = ('they', 'for', 'she', 'is', 'to', 'it', 'get', 'you', 'by', 'any', 'your', 'all',
            'be', 'do', 'does', 'in', 'a', 'of', 'at', 'if', 'with', 'was', 'we', 'to', 'or',
            'are', 'one', 'the', 'not', 'its', 'and', 'have', 'has', 'been', 'our', 'did',
            'my', 'this', 'am', 'as', 'dont', 'where', 'lot', 'had', 'but', 'that',
            'will', 'what', 'may', 'when', 'can', 'try', 'them', 'some', 'know')

# A for loop iterating through each stopword in stopwords list
# A for nested loop to iterate through each word in word_list
# if statement comparing each word in word list to each stopword
# in stopwords, if the stopword is equal to the word
# then it will be removed. returns word_list with out stopwords
for stopword in stopwords:
    for word in word_list:
        if word == stopword:
            word_list.remove(word)

# To get word frequency, use the Counter() function
# with .most_common() method
# We pass word_list as an argument for Counter() and
# request the six most common words by passint a 6
# as argument to .most_common(6)
sorted_word_frequency = Counter(word_list).most_common(6)

# Unpack the returned sorted_word_frequency with a
# for loop. we create two variables k, v to hold
# the returned keys 'word', values 'word count`
print()
print('Word frequency')
print('+------------+')
for k, v in sorted_word_frequency:
    print(f'{k:<10}:{v:>3}')
print()

"""
Word frequency
+------------+
bootstrap : 10
license   :  6
twitter   :  5
use       :  5
source    :  3
copyright :  3
"""
```

With the knowledge you have gained from this mini-course, we are able to write a pretty useful programs. Python offers many tools enableing programmers to focus on logic and implementation. As we write more complex the challenge will be in understanding requirements, writing a good program outline and finding the timely solutions for our problems.

## Next tutorial

We have been asked to turn our program into a module, write a new program that can import a text file and our new woe frequency module to process the text file.

## Things to try

This project offers many opportunities to experiment with, we could use our results to generate other analysis.

* Try other strings, and see if there are other stop words and characters you can add to improve your Word Frequency.
* Try converting `lower_str` to sentences, then based on your Word Frequency results, choose the top three sentences that contain the top Word Frequency

## Question

* Did you understand this lesson?
* Did you understand the logic outline? Could you make it more clear?

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>
