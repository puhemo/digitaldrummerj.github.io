---
title: "Python Part 05: Functions and Modules"
date: 2016-06-16
modified: 2016-09-10
categories:
  - Python
tags:
  - Python Syntax
  - Python 2.x
published: true
excerpt: |
  Taking segments of related code, wrapping it up in its own allocated code block, and attributing it with a name so that it can be called later at any point of the overarching program, thus treating it as its own separate, self contained, and individually existing entity. A "sub program" within your program, if you will.
series: "Intro to Python"	
---
{% include series.html %}

* TOC
{:toc}

# Functions

Taking segments of related code, wrapping it up in its own allocated code block, and attributing it with a name so that it can be called later at any point of the overarching program, thus treating it as its own separate, self contained, and individually existing entity. A "sub program" within your program, if you will.

> Functions in Python is a lot of code to reuse.

## Built-In Functions

Python has a number of built-in functions we can use without any knowledge of how its internal code actually works.

- `raw_input()`
- `type()`
- `int()`
- `float()`
- `str()`
- `max()`  
  The `max()` function takes any number of arguments and returns the largest one.   
- `len()`
- `abs()`  
  The `abs()` function returns the absolute value of the number it takes as an argument.

> When writing a function name, the opening and closing parentheses at the end identify it as the name of a function.

To see a full listing of Python's built-in functions, visit the [online Python documentation](https://docs.python.org/2/library/functions.html).

### The `dir( )` Function

The `dir()` built-in function returns a sorted list of strings containing the names defined by a module.

The list contains the names of all the modules, variables and functions that are defined in a module. Following is a simple example −

```python
# Import built-in module math
import math

content = dir(math)

print content
```

When the above code is  executed, it produces the following result −

```
['__doc__', '__file__', '__name__', 'acos', 'asin', 'atan', 
'atan2', 'ceil', 'cos', 'cosh', 'degrees', 'e', 'exp', 
'fabs', 'floor', 'fmod', 'frexp', 'hypot', 'ldexp', 'log',
'log10', 'modf', 'pi', 'pow', 'radians', 'sin', 'sinh', 
'sqrt', 'tan', 'tanh']
```

Here, the special string variable *__name__* is the module's name, and  *__file__* is the filename from which the module was loaded.

## User-Defined Functions

###  Function Definitions--`def`

In order to *define* a function we use the `def` **keyword**. This is followed by the unique name you wish to invoke your function with and a set of parentheses. You end the line with the `:` **colon character**. 


```python
# Define a function
def myFunction():
    # your code goes here...
```

A parameter acts as a variable name for a passed in **argument**. 

```python
# Function with parameters
def product(num1, num2):
    num3 = num1 * num2
```

A function can require as many parameters as you'd like, but when you call the function, you should generally pass in a matching number of arguments.

> Remember that inside the function the variable is temporary. When you return it then it can be assigned to a variable for later. 

###  Returns

If we want our calculations to have permanence then, we can "return" a value back to function call using the `return` keyword followed by a variable, constant, or expression.

```python
def product(num1, num2):
    num3 = num1 * num2    
    return num3
# somewhere in the middle of your code...
triangleArea = product(base, height) * 0.5
```

> The `return` statement should be placed at the bottom of your function code block. Anything after the `return` statement will not be executed since `return` force exits the function to give back the value to the calling expression

### Variable-length arguments

You may need to process a function for more arguments than you specified while defining the function. These arguments are called **variable-length** arguments.

Syntax for a function with non-keyword variable arguments is this −

```python
def functionname([formal_args,] *var_args_tuple ):
   "function_docstring"
   function_suite
   return [expression]
```

An asterisk (`*`) is placed before the variable name that holds the values of all nonkeyword variable arguments. This tuple remains empty if no additional arguments are specified during the function call. 

Following is a simple example −

```python
# Function definition is here
def printinfo( arg1, *vartuple ):
   "This prints a variable passed arguments"
   print "Output is: "
   print arg1
   for var in vartuple:
      print var
   return;

# Now you can call printinfo function
printinfo( 10 )
printinfo( 70, 60, 50 )
```

When the above code is  executed, it produces the following result −

```
Output is:
10
Output is:
70
60
50
```

### Lambda

One of the more powerful aspects of Python is that it allows for a style of programming called **functional programming**, which means that you're allowed to pass functions around just as if they were variables or values. Sometimes we take this for granted, but not all languages allow this!

Check out the code at the right. See the `lambda` bit? Typing

```python
lambda x: x % 3 == 0
```

Is the same as

```python
def by_three(x):
    return x % 3 == 0
```

Only we don't need to actually give the function a name; it does its work and returns a value without one. That's why the function the lambda creates is an **anonymous function**.

These functions are called **anonymous** because they are not declared in the standard manner by using the `def` keyword. You can use the `lambda` keyword to create small **anonymous functions**.

- **Lambda** forms can take any number of arguments but return just one value in the form of an expression. They cannot contain commands or multiple expressions.
- An **anonymous function** cannot be a direct call to print because lambda requires an expression
- Lambda functions have their own local namespace and cannot access variables other than those in their parameter list and those in the global namespace.
- Although it appears that lambda's are a one-line version of a function, they are not equivalent to inline statements in C or C++, whose purpose is by passing function stack allocation during invocation for performance reasons.

When we pass the `lambda` to `filter`, `filter` uses the `lambda` to determine what to filter, and the second argument is the list it does the filtering on.

```python
cubes = [x**3 for x in range(1, 11)]
filter(lambda x: x % 3 == 0, cubes)
```

# Modules

A [module](https://docs.python.org/2/tutorial/modules.html) is a file containing Python definitions and statements.  The file name is the module name with the suffix `.py` appended.  Within a module, the module’s name (as a string) is available as the value of the global variable`__name__`.  

A module is a file that contains definitions—including variables and functions—that you can use once it is imported.  

## Generic import

There is a Python module named `math` that includes a number of useful variables and functions, and sqrt() is one of those functions. 

```python
import math
print math.sqrt(25)
```

When you simply import a module this way, it's called a **generic import**.

## Function Imports

It's possible to import only certain variables or functions from a given module. Pulling in just a single function from a module is called a **function import**, and it's done with the from keyword:

```python
from module import function
```

## Universal Imports

What if we still want all of the variables and functions in a module but don't want to have to constantly type `math.`?

Universal import can handle this for you. The syntax for this is:

```python
from module import *
```

This provides an easy way to import all the items from a module into the current namespace; however, this statement should be used sparingly.

# Bringing It All Together

A example code that implements all of the above topics to demonstrate them in real-world application.

```python
# Caesar Cipher - A Python program to encrypt/decrypt messages
# Python v 2.x (Not Supported in v3.x)

# Import Declaration
import string

# Function Definition
def cipher(message, shift, encrypt):
   if encrypt == False: shift = 26 - shift
   return message.translate(
       string.maketrans(
           string.ascii_uppercase + string.ascii_lowercase,
           string.ascii_uppercase[shift:] + string.ascii_uppercase[:shift] +
           string.ascii_lowercase[shift:] + string.ascii_lowercase[:shift]
           )
       )

# Prompt user for encryption criteria
message = raw_input("Enter plain-text message: ")
shift = int(raw_input("Choose your cipher shift value: "))

# Encrypt message
message = cipher(message, shift, encrypt = True)
print "Encrypted cipher-text: " + message

# Prompt user for decryption
key = int(raw_input("Please enter cipher-key to decrypt your message: "))

# Attempt decryption
if key == shift:
    message = cipher(message, shift, encrypt = False)
    print "Decrypted cipher-text: " + message
else:
    message = None
    print "Invalid key. Your message has been deleted."
    print "This program will now self destruct!"
```

> This throws up an error:  
  AttributeError: 'str' object has no attribute 'translate' on line 10

This program utilizes the principles of a classic [Caesar Cipher](http://en.wikipedia.org/wiki/Caesar_cipher) in order to encrypt and decrypt messages. The textbook [briefly covers module imports and dot notation](http://www.pythonlearn.com/html-008/cfbook005.html#toc46), however if you have only watched the lecture videos on Coursera, just ignore the verbose minutia in the latter part of the function definition and take it on faith that `return message.translate()` is returning an encrypted/decrypted value back to the function call. 

The point to take away from this is that without the function definition, all of that [string manipulation logic](https://docs.python.org/2/library/string.html#module-string) happening would have to be implemented over and over in the code whenever the **message** variable needed to be encrypted or decrypted by the user. However, as the current implementation stands, every time **message** is manipulated, a simple `cipher()` call is made that only takes up one line. This drastically cleans up the code and makes debugging much less of a hassle since if you ever wanted to tweak some parameter in the algorithm, there is only one place you have to go to edit instead of several.

Function `cipher()` also utilizes *arguments* and *parameters* to pass in the user input **message**, the encryption **shift** value (i.e. the 'key'), and a `bool` value to determine whether to encrypt or decrypt **message** with that key.

Sample Output:

```
Enter plain-text message: Cryptography using Python!
Choose your cipher shift value: 17

Encrypted cipher-text: Tipgkfxirgyp ljzex Gpkyfe!

Please enter cipher-key to decrypt your message: 17
Decrypted cipher-text: Cryptography using Python!

```

# More Info

- [Pythonlearn:resources-week04](https://share.coursera.org/wiki/index.php/Pythonlearn:resources-week04#Lecture_Notes_-_Functions)
- [Defining Functions](https://docs.python.org/2/tutorial/controlflow.html#defining-functions)
- [Python Functions](http://www.tutorialspoint.com/python/python_functions.htm)

{% include series.html %}

