---
layout: post
title: interpreter, IDLE and Interactive interpreter - Python Install - 04
categories: [interpreter, IDLE, Interpreter, Win, Mac, Linux]
---

Now that we have learned a few Python Basics we should install the Python interpreter in our system. This is relatively easy and fast. We are going to do a basic installation, at a later point if you have special needs, you may customize your installation.

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>

After installation we will quickly review some of the components installed.

* Downloading python
* Installation over view
  * Windows 10
  * MacOS
  * Linux
* Components
  * Interpreter
  * The interactive prompt
  * IDLE

## Downloading Python

We can get the Python interpreter from <http://www.python.org>

As we navigate to the site, with our browser, it should be able to recognize and recommend the appropriate interpreter. The page will also suggest the latest most stable version.

* Navigate to <http://www.python.org>
* On the **blue nav-bar** click on **Downloads**
* Click on the **yellow button** displying latest version on it.

This will start downloading the installer on to your computer.

> The screen shot below shows the laters version for Windows, but if you are using a Mac or Linux system it will show the appropriate installer for your system.

[<img src="{{ site.baseurl }}/images/python-org_download.png" alt="Python.org download page" style="width: 700px;"/>]({{ site.baseurl }}/)

The download page will also give you options if you want to download Python for a different OS and versions.

## Installation overview

Once you have downloaded the appropriate package, we need to install it.

### Windowns 10

Run the installer, it will ask you if you want to do a default installation or custom, **chose default**, at the bottom of that windown there should be a check box asking to **set your PATH variable to include Python’s directory**, go ahead and **check the box** and **press next/install**, follow the  instructions and **choose all the defaults** when asked.

> Now you should have the Python interpreter installed!

### MacOS

Although the MacOS comes with an older version of Python installed, Python 2.7, it isn't recommended for developing as it will be faced out later in 2019. **We need to get the most resent stable version of Python.**

There are different methods for installing python on the Mac OS, one by installing

* The same way as we did in Windows or
* using HomeBrew.

For the sake of continuity and simplicity we will install it similarly as described for windows.

Once you have downloaded the latest version of Python as described above in "**Downloading Python**" from <http://www.python.org>

* Run the Python installer to install the latest version of Python
  * If prompted for setting PATH variable, make sure to select it.
  * Follow instruction and accept the default settings

> Now you should have the Python interpreter installed!

### Linux

Similarly in Linux we could go to the same website as we did for Windows and MacOS, but it would take longer using that method.

Lets go for the simpler method.

We will use a method compatible with some Debian based Linux distributions. **The admin group password [sudo] is required**.

* Open the **"Ubuntu Software Center"** folder.
  * A list of popular software available for download will be visible.
  * From the **"All Software"** menu
    * Select **Development Tools**
  * Double click the latest Python version
    * Ubuntu will offer to install Python
    * **Select Install**
* Close the "Ubuntu Software Center" window
* You should see a **Python icon** on the **desktop**

> Now you should have the Python interpreter installed!

## Components

There are a number of components installed with your version of Python. We are going to briefly look at three of them.

* The Python interpreter
* The interactive prompt
* IDLE

### The Python interpreter

The python interpreter is the program that executes the scripts we write, The interpreter interprets your code into something the computer can understand. Python is an **interpreted language**, it needs that layer between the script and computer hardware. There are other interpreted languages, like Java, Java Script, PHP and so on.

[<img src="{{ site.baseurl }}/images/interpreted.svg" alt="Interpreted language by Enrique Bruzual" style="width: 700px;"/>]({{ site.baseurl }}/)

In contrast there are compiled languages like C, C++, Swift, Objective-C and others. For each program (Script) an executable needs to be created [compiled] into **Machine Code** for each OS, this is only done once and then needs to be distributed.

[<img src="{{ site.baseurl }}/images/compiled.svg" alt="Compile language by Enrique Bruzual" style="width: 700px;"/>]({{ site.baseurl }}/)

> There are some advantages and disadvantages between compiled and interpreted languages, we will cover this at a later point.

In Python you can write a Script and distrubute the same file to different Operating Systems, MacOS, Windos, Linux, Android, iOS and other devices, as long as they have the Python interpreter installed they can run the script file.

[<img src="{{ site.baseurl }}/images/multiple_os.svg" alt="Multiple OS by Enrique Bruzual" style="width: 700px;"/>]({{ site.baseurl }}/)

### The interactive prompt

Depending on you operating system this can be accessed through your **"system shell prompt"**

* **Windos:** In the DOS console window type `Python`
* **MacOS:** double-click on **Applications**→**Utilities**→**Terminal**, and then typing `python`
* **Linux:** On your shell/terminal window and type `python`

Your terminal will run a **Python Interactive Session** on the **same terminal windown**

[<img src="{{ site.baseurl }}/images/command_prompt.png" alt="command prompt" style="width: 700px;"/>]({{ site.baseurl }}/)

* When you see a screen similar to the one above, you are in a **Python Intereactive Session**.
* The `>>>` indicates, is ready for you to type any python command
  * `>>> print('Hello world!')`
  * Press `Enter`
  * The command will execute and return the results below the entered command

```python
>>> print('Hello world')
Hello world
>>>
```

Although we use the print() function in the above, in an interactive session is not needed. You can just type the string in quotes and it will return the string when you press `Enter`.

But it is very usufull for testing and quick execution of short programs.

* Type `round(34.654444, 2)`
* Press `Enter`

```python
>>> round(34.654444, 2)
34.65
>>>
```

* It will excute the function and display without using the print function. This is only possible with a **Python Intereactive Session**, if you write a program and save it to a python document you need to use the `print()` function if you want to display results to a screen

* Although it is a convenient way to test commands, modules and short scripts -- it isn't suitable for writing entire programs, for that we would use the included IDLE editor which allow us to **save our script** to a file and later **run them**.

> To exit a **Python Intereactive Session** simply type `quit()` and press `Enter`

### IDLE

IDLE **Integrated Development and Learning Environment** is a text editor designed to write Python programs (**scripts**). It has special tools and features allowing you to edit, run, browse, and debug Python programs.

To launch IDLE in any OS from a shell command window, type the following:

* `python -m idlelib.idle`

Or you can navigate to where your system installed Python and run the IDLE application.

* **In Windows**
  * Start menu
  * **Scroll** to the Python folder
  * **Expand** the Python folder and click on **IDLE**

* **In MacOS**
  * In the Applications folder find the Python folder
  * From the Python folder launch the `IDLE.app`

* **In Linux**
  * From the shell command window
    * `python -m idlelib.idle`

IDLE will launch an **Interactive Shell** running a **Python Intereactive Session**

It behaves in the same way as the **"system shell prompt"** we used before

[<img src="{{ site.baseurl }}/images/idle_shell.png" alt="IDLE shell" style="width: 700px;"/>]({{ site.baseurl }}/)

* To create a new script, under the `File` menu, select `New file`

* This will launch a **blank script document**. Here we can write our scripts and save them.

[<img src="{{ site.baseurl }}/images/untitled_idle_doc.png" alt="Untitled IDLE doc" style="width: 700px;"/>]({{ site.baseurl }}/)

**To save:** Under `File` menu, select `Save`

* Python script use the extention `.py`
  * `my_script.py`
  * You can save it at any location in your system.
* To run your first script
  * Under `Run`
    * Select `Run Module`
    * Python will return the results in the IDLE Shell

## Next tutorial

Using our new install we are going to review and expand on some of the topics we cover in the previews tutorials. Including keywords, other built-in functions, Strings

## Things to try

Try re-writing the temperature script using IDLE and saving it it.

* Exit the IDLE
* Re-open it
* Run the script you saved

## Question

* What is IDLE?
* What is the interactive prompt good for?

<a href="https://www.patreon.com/bePatron?u=15482170" data-patreon-widget-type="become-patron-button">Become a Patron!</a><script async src="https://c6.patreon.com/becomePatronButton.bundle.js"></script>
