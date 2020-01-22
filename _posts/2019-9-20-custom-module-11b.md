---
layout: post
title: Lesson 11b - Word frequency module (import)
categories: [custom module, functions, open()]
---

Our client wants a module to generate word tags for blog posts and other types of articles. It is time to write our word frequency module, we will implement what we learned last week.

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>

Looking back at what we learned last week, and understading, our client wants a module, that can generate a list with most frequently used words from any text, it is probably good practice to first setup our module file structure and then begin to program.

* Project directory
* The `string_file.txt` file
* The `wordy.py` file
* The `open_file.py` file

## Project directory

To ensure our project works properly, I will setup the simplest file structure to minimize any file path errors.

For this project we are going to create a folder, in your preferred location, name it **module_project**. Inside we can create three files.

* Inside the **module_project** folder create the following files.

[<img src="{{ site.baseurl }}/images/11b_project_structure.png" alt="alt" style="width: 400px;"/>]({{ site.baseurl }}/images/11b_project_structure.png)

| File name       | File description                                              |
| --------------- | ------------------------------------------------------------- |
| open_file.py    | Our top script importing wordy.py and opening string_file.txt |
| string_file.txt | text file holding text string                                 |
| wordy.py        | The word frequency module                                     |

With the file structure in place, we should be able to compleat our project.

## The `string_file.txt` file

Instead of writing our test string in one of the actual scripts, as they can be very long, we are going to place our test string in it's own file, `string_file.txt`.

I would suggest to find a nice article of interest to you, copy the text and paste it in `string_file.txt`, as is. Save it and close the file.

## The `wordy.py` file

This will be the actual module that will be imported into `open_file.py`, first we are going to format the document and then we will write the script.

1. First we write a module description
2. Right after, we leave space for imports and body
3. Lastly we write the footer

```python
""" Word frequency module, count number of word instances
in a string, returning a list of tuples with
world and count """

# imports here

# script body here

if __name__ == '__main__':
    # local script
```

### imports

right after our module description we will import any necessary modules. As we import this script into another modules, all imports here will be available to the script being imported into.

1. We will import `string`
2. and `from collections import Counter`

```python
""" Word frequency module, count number of word instances
in a string, returning a list of tuples with
world and count """

import string
from collections import Counter

# script body here

if __name__ == '__main__':
    # local script
```

### functions

We are adapting our word frequency script from before into a module, for this we are going to write two functions. An utilitarian function to manage the stopwords and another function to handle the string processing.

| Function    | Description                                                                                                                            |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| stp_words() | Utilitarian function to be used by frequency(), takes one argument returns a list with default stop words and additional words if any. |
| frequency() | Returns a list of tuples, each tuple holds word with count, depending on most frequent value.                                          |

#### stp_words()

The `stp_words()` function will be use by `thefrequency()` function. The `stp_words()` is able to take additional stop words and add them to the stopwords already stored in `stp_words()`.

If there aren't any extra stopwords passed as a function argument, the function returns the list of stopwords already stored in the function.

If there are extra words passed as a function argument (string separated by commas), then function takes the string argument, turns the string to lower case, it then splits the string in every `", "` found.

Finally, the function returns a list with all the stored stopwords combined with any additional stopwords the user may have passed.

> Notes: The code below reflects the description above. Everything below the function definition is indented four spaces.

```python
def stp_words(ext_stw):
    """
    Utilitarian function used by frequency(), takes one argument
    returns a list with default stopwords and additional stopwords if any
    """

# abrivated stop word list
    stopwords = ['they', 'for', 'she', 'is', 'to', 'it', 'get', 'you', 'by', 'any', 'your', 'all']

    if ext_stw == """""":
        return stopwords
    else:
        extra_words = ext_stw.lower().split(", ")
        return stopwords + extra_words
```

#### frequency()

Lets write our primary function, by defining it and calling it `frequency()`. It will take one positional argument and three keyword arguments. This function will return a list of tuples based on the most frequent words.

| Arguments      | Description                                                        |
| -------------- | ------------------------------------------------------------------ |
| InputString    | This is the raw string that will be analyzed.                      |
| extraChr       | Any extra character to parse out.                                  |
| extraStopwords | Any extra stop words to be added and removed.                      |
| mstCommon      | number of most common words to returned by `.most_common()` method.|

```python
def frequency(InputString, extraChr="", extraStopwords="", mstCommon=6):
    """Returns a list of tuples, each tuple holds word with count,
    depending on most frequent value"""

    stop_words = stp_words(extraStopwords)  # (1.)
    lower_str = InputString.lower()  # (2.)
    char_template = str.maketrans("", "", string.punctuation + extraChr)  # (3.)
    cleanned_str = lower_str.translate(char_template)  # (4.)
    word_list = cleanned_str.split()  # (5.)

    for stopword in stop_words:  # (6.)
        for word in word_list:
            if word == stopword:
                word_list.remove(word)

    return Counter(word_list).most_common(mstCommon)  # (7.)


if __name__ == '__main__':
    pass  # temporary pass
```

Above, `(1.)` we first call our utilitarian function, `stp_words()`, Notice the argument, `extraStopwords` we take it through `frequency()` and pass it to `stp_words()`

* `stop_words = stp_words(extraStopwords)`

Much like in our original word frequency script, `(2.)` here we take the `InputString` and pre process it, by turning it into lower case.

We create text character template `(3.)` by calling the `str.maketrans()` method. we pass the `string.punctuation` plus any extra characters through `extraChr`, these are combined by the `+` sign. All of this is assigned to the  `char_template` variable.

We remove any string punctuation `(4.)` by calling our `lower_str` string through the `translate(char_template)` method using `char_template` as an argument. We assign this to `cleanned_str`

We can create a list of words `(5.)` from `cleanned_str` string by using the `split()` method. By default it splits on any space.

---

For example a string with the split method.

* `"word1 word2 word3".split()`

Will return the following list.

* `['word1', 'word2', 'word3']`

---

We assign the newly created list, `cleanned_str.split()`, to the `word_list`

* `word_list = cleanned_str.split()`

We will use our nested loop `(6.)` to iterate through each `stopword`, and a nested loop to iterate through each `word` in `word_list`. If a `word` is equal to a `stopword` then we remove that word from `word_list`. We are left with a list without any of the stop words.

And finally we return `(7.)` the `Counter()` function with the `.most_common()` method. passing `word_list` as an argument.

* Returning a list of ordered tuples, with the word and count.
  * `[('word1', 6), ('word2', 4), ('word3', 2), ('word4', 2), ('word5', 2)]`

The returned list can be unpacked and formated.

### Scope condition

To run our script as a stand alone program or a module we need to add the scope condition line at the bottom of the script.

* `if __name__ == '__main__':`

If the scope of the script is equal to the name of the file, run any code below the condition, if the scope of the file is used as a module, don't run the code below the conditional line.

We can test our code by writing our script below the conditional line.

We can write the logic by first assigning string arguments to variables. `(8.)`

Then we can pass the variables to the `frequency()` function, as arguments. `(9.)`

* `test_str` as the first positional argument.
* `extra_chr` as keyword argument for `extraChr`
* `ext_stopwords` as keyword argument for `extraStopwords`
* integer, `5`, as keyword argument for `mstCommon`

We can then `print()` the return values for the `frequency()` function. `(10.)`

```python

# I truncated the script to save space.
    return Counter(word_list).most_common(mstCommon)  # (7.)


if __name__ == '__main__':

    test_str = """It forbids you to:
    Hold the authors  and license owners liable for damages as Bootstrap is provided without warranty
    Hold the creators or copyright holders of Bootstrap liable
    Redistribute any piece of Bootstrap without proper attribution
    Use any marks owned by Twitter in any way that might state or imply that Twitter endorses your distribution
    Use any marks owned by Twitter in any way that might state or imply that you created the Twitter software in question"""  # (8.)

    ext_stopwords = "Use, piece"  # (8.)
    extra_chr = ""  # (8.)

    word_frequency = frequency(test_str,
                               extraChr=extra_chr,
                               extraStopwords=extra_stw,
                               mstCommon=5)  # (9.)

    print()
    print(word_frequency)  # (10.)
```

When we run the script above as a main, we will get the following

* `[('twitter', 4), ('bootstrap', 3), ('hold', 2), ('liable', 2), ('without', 2)]`

> Alternativley: if we are ok with the default keyword arguments, we just pass the first positional argument. `frequency(test_string)` and omit the ones we don't want to change.

We can also import this script/module into another script and use the `frequency()` function. I will show you in our next file.

## The `open_file.py` file

Now we are going to write a script where we import the custom module, `wordy.py` and open our text file.

[<img src="{{ site.baseurl }}/images/11b_file_structure.svg" alt="alt" style="width: 400px;"/>]({{ site.baseurl }}/images/11b_file_structure.svg)

Open `open_file.py` `(1.)`

We can start by importing our module `wordy`. Notice we don't type the `.py` file extention.

```python
import wordy  # (1.)

string_file = open('string_file.txt', 'r')  # (2.)
test_string = string_file.read()  # (3.)
string_file.close()  # (4.)

extra_stw = ""  # (5.)
extra_chr = "•"  # (6.)

word_frequency = wordy.frequency(test_string,
                                 extraChr=extra_chr,
                                 extraStopwords=extra_stw,
                                 mstCommon=5)  # (7.)

print()

wf_list = []  # (8.)
for k, v in word_frequency:  # (9.)
    wf_list.append(k)

print(wf_list)  # (10.)
```

Above, We then want to open `string_file.txt` in **read** mode. `(2.)`

Read the file into memory `(3.)` by using the `.read()` method.

* `string_file.read()` assigning it to `test_string`

Close the `string_file` with the `.close()` method. `(4.)`

Create two variables to hold additional stopwords and punctuations

* `extra_stw = ""` - `(5.)`
* `extra_chr = ""` - `(6.)`

To call the `frequency()` function `(7.)` we must preside it by the module name separated by a `.`

* `wordy.frequency()`

We can pass our arguments,`test_string`, `extraChr`, `extraStopwords`, `mstCommon`. `(7.)`

We can assign the `wordy.frequency()` function to the `word_frequency` variable `(7.)`. The function will return a list of tuples.

We want a list with just the words sorted by most common `(8.)`. In order to get this we have to iterate `(9.)` through the returned list of tuples and append the empty list with just the words.

We can then pass the list `(10.)` to another operation, `print()`.

You will get a list of most frequent words, in the same format as the one below but with words reflecting your text file.

```sql
['python', 'language', 'says', 'van', 'rossum', 'programming']
```

As you can see we can call our module from any script, pass a string and with the return value we can do other operations.

With that we end our lesson on custom modules, import and opening files.

---

## Next tutorial

An introduction to list comprehencion

## Things to try

* Try modifying the arguments in `wordy.frequency()`
* Find a different way to use the returnned value. Try unpacking values and formatting them differently.

## Question

* Can you think of a problem `stp_words()` may have? if so how would you fix it?
* Can your shorten the following code to one line?

```python
wf_list = []
for k, v in word_frequency:
    wf_list.append(k)
```

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>
