---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Programming (in python)
If you are completely new to python then have a look through the syntax section on this page [https://realpython.com/python-first-steps/](https://realpython.com/python-first-steps/#the-basic-python-syntax). Syntax tells you about the rules for writing a computer language. When you begin programming you will probably spend most time getting this right. Do not worry about remembering details from that web link – you'll learn what you need through practice on this module. Hopefully you can see that python code is reasonably easy to read/understand. We are now going to look at how we can use python to "do stuff" i.e. write programs.

## Algorithms
There are two absolutely key steps in writing any computer program (this applies to any programming language):

1. Understanding what it is you want to do
2. Breaking this down into individual steps

If you can do these for the problem in hand then the process of writing the code is usually straightforward.

Put together these steps allow you to develop an algorithm for the problem you are working on. In formal computer science there is more to it than this, but we need to be pragmatic and get on with solving problems.

For MPP001 step 1 should be straightforward. As you get more ambitious with programming it can be tricky to define (and understand sufficiently well) what it is you want to do. Questions you should ask yourself include:

* What is the starting point (what information do I know)?
* What result(s) should be returned/output?
* What calculations etc are necessary
* Are there any limits on the input/output?

As you gain experience with programming you will develop you own list and learn to adjust it to the situation.

Step 2 is a vital step that has to happen before you begin to write the code. With a little practice you will be able to do this step in your head for simple problems. However, for anything involving more than a handful of lines of code it is best to write out the steps and refine them.

Of course, there are other stages – testing, optimisation/refinement, etc. but for now these are enough to get going.

### Example: how many cans of paint?
You are tasked with working out how many cans of paint are required to coat the sides and top of a tank of diameter $5m$ and height $8m$ if each can covers $2.5m^2$.

**Step one**:
Inputs: diameter, Height, coverage per can. (limits: all should be above zero)

Outputs: Number of cans (limits: should be an integer)

Equations:
the surface area of a cylinder is given by: 

$$ \pi\times \textrm{diameter}\times \textrm{height}$$

and the area of an end is:

$$ \frac{\pi\times \textrm{diameter}^2}{4}$$

the number of cans will be given by: 

$$N=\frac{\textrm{total surface area}}{\textrm{coverage per can}}$$



**Step two**
A first stage-wise step through of the process could be:

    1. Store input values in sensibly named variables
    2. Calculate number of cans
    3. Output results

This could usefully be refined to:

    1. Store input values in sensibly named variables
    	* Diameter = 5, Height = 8, Coverage = 2.5
    2. Calculate number of cans
    	* Ncans = (Surface area)/Coverage
    3. Output results
    	* Ncans needs to be rounded up

This is about ready to turn into python code:

```python
# code to calculate number of cans required to paint sides and top of cylinder
import math as math # provides math functions and constants
# define values. Names should be self explanatory
Diameter = 5.0
Height = 8.0
Coverage = 2.5
NumCans = 0. # make sure that start from zero (good practice)
# Now calculate the number of cans required
# divide surface area of cylinder side + top by coverage per can
NumCans = (math.pi*Diameter*Height + math.pi*Diameter**2/4.)/Coverage
# Output Result
print(f'You require {math.ceil(NumCans)} cans of paint') # ceil rounds to the next integer

```

Notice the use of comments (anything after a `#` is a comment and does nothing code wise). These are a way to annotate the code so that it is easier to follow. It is difficult to have too many comments in your code especially if it contains more than a couple of active lines of code.

Now more complex problems will require more stages and you may go through three or four refinement stages before starting to convert to code. It is tempting to shortcut this, but you'll be a better programmer for taking the extra time. In fact you'll probably take less time in the end as there'll be less wrong with your code when you write it. Also, you may find that more refinement still is needed as you start the coding – don't worry about this it is bound to happen. As you get more practiced you will get used to making the judgement.

You may feel that you want to jump into coding after Stage One and a lot of the time this will work OK for simple problems. However, it is good to get into the habit of doing both steps you will benefit in the medium term–especially if you want to evidence code development for your project.



## The building blocks of computer code
In order to get a program with a useful level of complexity there are a few key building blocks. These are common to most computer languages (there will be syntax differences–for instance, python uses indentation of code to separate blocks whilst many others use curly brackets i.e. {}. The ones key to introductory python programming are described below.

### Conditional statements
These check whether a condition is met and perform different code based on this check. The classic structure is the `if` statement which will execute the following code if the condition tested evaluates to TRUE. `if` statements can be extended in a number of ways: an `else` block adds code that is only run if the condition is not met. In python there is also an `elif` command that can be thought of as 'else if...'


### Loops
These are used to repeat a block of code either a fixed number of times (usually the `for` loop) or until some condition is met (`while` loop).

In most computer languages the for-loop increments/decrements a numeric variable through a range of values. Here is a C example

```c
// Loop in C language - DO NOT copy to python
for (int i = 1; i < 11; ++i)
  {
    printf("%d ", i);
  }
```
Do not try and run this code in Spyder (or any other python system)  Hopefully you can see that this would print out the integers from 1 to 10.

In python the loop goes through a list of values. The must all be the same type, but beyond that there are very few limits. So this example prints out the primary colours:

```{code-cell} ipython3
colours = ['red','green','blue']
for colour in colours:
    print(f'{colour}')
```

The C example above could be reproduced in python with something like:

```{code-cell} ipython3
for i in range(11):
    print(i)
```
range() is a function that returns a list of numbers. It defaults to starting at 0, but this can be changed (e.g. `range(1,11)` would give 1, 2, ..., 10).  

**Top tip** Loops are often used for calculating sums, products, etc. make sure the variable that you are storing the result in starts from where it is supposed to. For sums (`i = i+NextValue`) this will usually be zero. For products (`y = y*NextValue`) one is a better choice.


### Functions
These are blocks of code that you send values to and the block returns one or more values. `print()` is an example of a built-in function. You can add your own functions to python code either by importing them from another file/script or by defining them in the script you are working on.

A minimal python example would be:

```python
def HelloWorld():
	print('Hello world!')
```
Note the code after the `def` line is indented – this is how python tracks the extent of the current code block. You can see a similar use of indenting in the for loop above.

The brackets after `HelloWorld` can take the names of arguments (parameters) that are to be passed to the function. E.g.

```python
def Quotient(x,y):
	print(x/y)
```

which could be called by `Quotient(2,3)`. Note the order of arguments matters.

You can give arguments default values:

```python
def Sum(x,y=3):
	return(x+y)
```

Calling this with `Sum(4)` will return `7` whereas `Sum(4,2)` will return `6`. Note all arguments after the first with a default value must have default values.

## Finding out more about python

An excellent resource for getting started in python is week one of this online course: [introPy](https://lukas-snoek.com/introPy/index.html)

There are lots of other learning resources available via the internet. [LinkedIn Learning](https://www.linkedin.com/learning/) (for which you have access via the University) has lots of professionally created courses to choose from and Google and/or YouTube may have one or two things of interest as well.


## Exercises

### Coding challenges

For each of the following use the development process outlined above. You may need to ask for help and/or search for information on some of the coding needed.

1. Write a function that returns the volume of a pipe of length `l`, outer diameter `D`, and inner diameter `d`.
2. Adapt the above program so that it gives the result to three decimal places and to three significant figures.
3. Write  a function that calculates the sum of the first `N` odd integers. For example: if `N = 5` then the sum is `25` (i.e. 1 + 3 + 5 + 7 + 9 =25). 
4. Write a program that uses a loop to call the function you created for exercise 3 for values of N from one to ten. What do you notice about the sums?

### Spot the difference
The `numpy` library has a `ceil()` function that has a sublte difference to the one in the `math` library. Can you spot this difference? What impact might it have on your code?
