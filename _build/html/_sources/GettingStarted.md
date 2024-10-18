# Introduction
This part of the guide provides a quick overview of how to get Python running on one of the University PCs and a very short introduction to running python code.

## Starting a python session on Lab PCs.

Once you are logged in to a lab PC you can start a python session by using the Start Menu – Click on the Anaconda Folder and select the Spyder app. 

There is also a Python section in the Start Menu. This gives access to other versions, but it is much better to use the method above as it works reliably and you will get the same apps etc. on your own computer if you install Anaconda (see below).


### Make sure you have the right Python version

You might be inclined to use the search box to find/start python items. The problem is that this shows up items relating to another version of python (used by SPSS) that is not set up for general use. Worse, it uses an out of date version of python that is not compatible with much of the code used in this module.


## Python on you own computer
You can install Python on your own computer. The computers in the teaching labs use the Anaconda distribution <https://www.anaconda.com>. It contains a lot of useful python packages and a lot more. It is free for educations use and installers are available for Windows, MacOS, and Linux. If disk space is a premium for you then search on the Anaconda site for the 'miniconda' version which contains the basics and there is an easy way to add any extras that you need.

### Python for research
The Anaconda Python distribution is **NOT** free for research (or commercial) use. I use the conda-forge distribution instead, this provides a very similar experiance to the Anaconda distribution.

Other versions of python are available. If you do not use Anaconda/conda-forge then do make sure you are installing a one of the Python 3 variations (I advise using version 3.8 or higher). Python 2 is still available, but has some significant differences.

MacOS (and many Linux versions) come with a version of Python however these versions often lack the science libraries needed for this module and it is generally easier to install Anaconda/conda-forge.

Anaconda also comes with a range of tools for editing and running python code. Spyder is probably the best (free) choice for editing science/engineering code. You can install it separately or as part of the Anaconda installation. Another excellent choice is pyCharm.


# First steps in Python
The easiest way to get started with python is to launch the Anaconda Navigator app. You then have to choose whether to use the file based ('.py') or notebook approach. I recommend you take the time to try both.

## Notebook-based python

Follow the instructions here: [Jupyter notebooks](https://docs.anaconda.com/free/anaconda/getting-started/hello-world/#run-python-in-a-jupyter-notebook)

### Exercise:
Modify the example in the link above so that it gives the "Hello World!" greeting.

### Quick way to run cells
Clicking the Run cell button is fine, but you can save time by pressing the Shift key at the same time as pressing the Return key. This will run whichever cell the cursor is in.

This means that you can go back to a cell, edit it, and re-run just that cell. If you use a '.py' file approach then all the code has to be re-run when you make a modification.


## file-based python

Follow the instructions here: [Spyder](https://docs.anaconda.com/free/anaconda/getting-started/hello-world/#run-python-in-spyder)



### Hello World!
(in Spyder) In the console window (bottom left) you should see a prompt that looks something like this:

```
In[1]:
```

This is the current line and is where what you type appears. Type in the following, but do not press the return key:

```python
print('Hello world!')
```

What do you think this code does? Press the return key and find out if you were right...

The code calls the `print` function telling it you want 'Hello world!' to appear on the screen. In python anything inside quotes (single or double) are examples of strings and are just text information.

You can use the console view to enter python commands one line at a time. This is fine when you have a line or two to deal with, but in the long run a file based approach is needed and in most cases the Jupyter notebook is the best option.

## Simple maths in python
Python has a range of standard mathematical functions as sumarised in the table below. If you have used something like Excel for maths then you should be familiar with them. Try to predict the outcomes of the examples given before entering them into your python system. Do they give the results you expected?

| Symbol | operation | example |
|--------|-----------|---------|
| + | addition | 3+2 |
| - | substraction| 2-3 |
| * | multiplication | 3*2 |
| / | division | 2/3 |
| ** | exponent | 3**2 |

There are a range of other maths operators as well, but this is enough for now.

### Beyond simple maths
Given the similarity to Excel for the operators above, what do you think the following will produce?

```python
cos(0.0)
```
Try it in the Spyder console.

You probably got something like:

```
Traceback (most recent call last):
  File "<pyshell#6>", line 1, in <module>
    cos(0)
NameError: name 'cos' is not defined
```

Which is a longwinded way of the python system telling you it has no function `cos()`. One of the key features of python is that it is easily extendable. Try the following code snippet:

```python
import numpy as np
np.cos(0.0)
```
The first line in the block above tells python to use the module called numpy (often pronounced num–pie) and all references to its contents will be preceded by `np.` for example `np.sin(3.141)`. Numpy is an extensive maths library that is very well optimised and we will use it a lot in MPP001–along with a lot of other libraries. 

### `as library_name`

The `as np` can be neglected and then to access numpy's functions `numpy.` will need to be added instead of 'np'. However it is very common to use `as library_name` because the full library name can be quite long and this can make the card hard to read (and longer to type). Formally the `as` sets up an alias to the original name of the library so you.

`np` is used by convention for the numpy library, you can use any text identifier you like, but remember that you and others need to be able to follow the code so keep it simple. For instance you could use ```include numpy as Lb0r0R0cks``` at the start of your code and then, say 100 lines later, have ```Lb0r0R0cks.cos(XVal)``` which would be very difficult to follow and you would have to search for what it means.

In this module you'll meet a few other widely used libraries that, like numpy, have pretty much universally accepted, standard names:

| Library | Purpose | Standard short name |
|-----------|-------------|---------------|
|Scipy | A collection of scientific computing methods | `sp`|
| Pandas | Data manipulation and analysis | `pd` |
| Scikit Learn | A collection of machine learning methods | `sklearn`|

There are plenty of other examples - look out for them in your reading/learning for this module.


### Exercises
1. Investigate the operator precedence in python.
1. Experiment with the maths functions in numpy-are all the ones you expect there? Do they work the way you expect?
2. Modern python has a maths library called "math" that provides similar maths functions to numpy. Numpy provides a lot of extra functionality, but for most things there is not much to choose between them. Repeat your numpy maths experiments with the math module. Do you see any different answers?

## Read the docs
Whilst discussing the standard libraries, it is worth pointing out that they have excellent online documentation. For example, for Pandas look here: [https://pandas.pydata.org/pandas-docs/stable/user_guide/index.html](https://pandas.pydata.org/pandas-docs/stable/user_guide/index.html). Smaller libraries are likely to use the ReadTheDocs web system for their documentation e.g. [https://pytube.io/en/latest/index.html](https://pytube.io/en/latest/index.html). This system provides a standard look for documentation that makes it easier to find you way round new libraries.

