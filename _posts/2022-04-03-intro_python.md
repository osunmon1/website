---
layout: post
title: You're up and running!
---


```python

```


```python
<div id="container" style="position:relative;">
<div style="float:left"><h1> Intro to Python II </h1></div>
<div style="position:relative; float:right"><img style="height:65px" src ="https://drive.google.com/uc?export=view&id=1EnB0x-fdqMp6I5iMoEBBEuxB_s7AmE2k" />
</div>
</div>
```

Now that we know the basic data types in Python, we can learn how to use those data types to write some functional code. We will look at 
* Control Flow
* Conditionals (if/else)
* Loops
* Functions
* Try/Except 


### Control Flow 
Control flow allows us to make decisions in our code based on the result of a specific evaluation. These evaluations boil down to a `True` or `False` value and based on that value we can execute a specific piece of code.

It is the combination of comparison, logical and boolean operators that helps us build complex expressions. We can write our code in such a way that once an expression evaluates to `True`, a particular section of our program will run.



```python
# Basic conditionals
5 > 3 # True
```




    True




```python
0 > (3 + 5) * 2 # False
```




    False




```python
'hi' == 'hello' # False 
```




    False



### Comparison Operators

<img src='https://drive.google.com/uc?export=view&id=1bWWPF4sw_Jvk9z7iqBv_UebHzaXqV0x_' width = 700>

### Logical Operators

<img src='https://drive.google.com/uc?export=view&id=13kQlzsPoJJyCiXKkPJv5laHvANwmMVeR' width = 700>

Logical operators are used to chain expressions together allowing us to create more complex operations. The expressions on either side of a logical operator is known as an operand. Each operand is evaluated to Boolean context which will result in a `True` or `False` value. The result of the overall statement is dependent on the logical operator being used. Refer to the examples in the Logical Operators chart above to determine how each operator can produce a result of `True`. 

Determine what the result will be for the following:


```python
x = False
y = True

print(x and y)
```

    False



```python
print(x or y)
```

    True



```python
print(not y)
```

    False


It is important to know that all non-boolean operands are evaluated based on its boolean context to determine if its "truthy" or "falsy". There are several non-boolean values that will result in a False evaluation. These values include:
- Any numerical operation that results in zero
- An empty string
- An empty list or dictionary
- Python's `None` keyword

### If / Else Statements

Based on the outcome of a conditional, we can have our code "make decisions" or execute a specific block of code with the use of an if / else statement.


```python
x = 5

if x > 3:
    print('running True block of code')
else:
    print('running False block of code')

```

    running True block of code


Try altering the value of `x` to have the `else` block of code run.

If we want to test multiple conditions, we can make use of the `elif` statement coupled with a normal if / else statement. It is important to know that the `else` statement is used to execute code when none of our conditions match our `if` or `elif` statements.


```python
grade = 85
 
if grade >= 90:
    print("Above Average")
elif grade < 90 and grade >= 70:
    print("Average")
else:
    print("Below")


```

    Average


Try altering the `grade` value to produce a result in each portion of our if statement.

### For Loops

For loops let us iterate a specific number of times where each iteration executes code. For loops are very useful when we want to iterate through a list data type or execute code a specific number of iterations using the `range` function. The syntax for writing a `for` loop is as followed: 

```python
for x in iterable:
    # execute code
```

Lets unpack the `for` loop syntax. First, we declare a for loop by using the `for` keyword. Next, we specific the variable name that we want to use to keep track of the step or current iteration we are on when our for loop runs. In our example we used the variable name of `x`. Proceeding our iteration variable we declare the `in` keyword followed by the name of the list or range we want to loop through.  


```python
# Loop through a list 
grocery_list = ['salad', 'milk', 'corn']

for item in grocery_list:
    print(item)
  
```

    salad
    milk
    corn



```python

```

### Range

For loops can iterate over a sequence of numbers using `range` (for now we will treat `range` as a function, and explore it in more detail later on). This sequence of numbers can either be positive or negative and the range will begin at zero unless a specific starting position is declared using its parameters. The range function can take in three values (parameters) which are separated by commas.

#### Range Parameters 
- The first parameter is the starting position
- The second parameter is the end position 
- The third parameter is the step after each iteration (optional, 1 by default)


```python
# range function using two arguments
for x in list(range(0, 5)):
    print(x)
```

    0
    1
    2
    3
    4


**Note**: the end position is not inlcuded in the enumeration, we stop before reaching that element.


```python
# range function using a third agrument which specifies step size
for x in range(0, 10, 2):
    print(x)
```

    0
    2
    4
    6
    8


Lets unpack the range function in the example above. Using the range function we instructed our for loop to start at index 0 and to continue looping for as long as our `x` variable is less than ten. During each iteration of our loop, we increased the value of x by two resulting in the print out of all even numbers less than ten. What do you think will happen if we changed the starting position of our range function to begin at one?


```python
for x in range(1, 10, 2):
    print(x)
```

    1
    3
    5
    7
    9


What is a range? We can check the type:


```python
r = range(0, 10, 2)
type(r)
```




    range




```python
# What is inside a range?
print(r)
```

    range(0, 10, 2)



```python
# To see what's inside a range we much make it a list type
print(list(r))
```

    [0, 2, 4, 6, 8]


### Using The Range Function to Loop a List

There may come a time when you need to use the iteration number to index a list. This can be accomplished by combining the `range` function with the `len` function. The `len` function will return the "length" or number of items in a particular list. 


```python
numbers_list = [1, 3, 5, 9, 12]
list_length = len(numbers_list)

print('The length of the numbers_list is', list_length)
```

    The length of the numbers_list is 5


Now that we know how to get the length of a list, we can loop the list by passing that number in as the end position in our range function.


```python
numbers_list = [1, 3, 5, 9, 12]
list_length = len(numbers_list)

for i in range(0, list_length):
    print(numbers_list[i])
```

    1
    3
    5
    9
    12


If you are feeling confused by the example above, that is okay as it is very syntax heavy. The main purpose of this example is to give you exposure to different ways to solving one problem. The above example leverages the understanding of lists and how they are indexed starting at zero. By using the `len` and `range` function we preserve the value of `i` as the iteration value and not the value of item in the list.

### Nested For Loops

A nested loop is a loop that is executed inside of another loop. The iteration of the outer loop will trigger the inside loop to execute for its entire life-cycle. Nested for loops gives us the ability to access data from more complex data types. 

Take a look at the example below, we will use a nested for loop to access data from a list where each item is another list.


```python
main_list = [[63, 88, 73],
             [75, 77, 73],
             [80, 85, 68]]

for inner_list in main_list:
    for value in inner_list:
        print(value)
```

    63
    88
    73
    75
    77
    73
    80
    85
    68


Time to unpack the example above. First, when iterating over the `main_list` with the outer `for` loop we gain access to the three inner lists. The `inner_list` is just a variable that will hold the value at each iteration which in this case is another list.


```python
main_list = [[63, 88, 73],
             [75, 77, 73], 
             [80, 85, 68]]

for inner_list in main_list:
    print(inner_list)
```

    [63, 88, 73]
    [75, 77, 73]
    [80, 85, 68]


Now having access to the inner lists, we create a second `for` loop that will iterate through the entirety of each list. 


```python
for value in inner_list:
    print(value)
```

    80
    85
    68


>Note: Notice that our inner for loop only printed out three numbers. The example above only was to show what happens at each iteration of the outer for loop.

--- 
#### Exercise 1
Create a loop, which loops over a list to calculate a polynomial given the following input:

```python
x = 5
factors = [5, 7, 1]
```

So the loop should calculate $5\cdot 5^0 + 7\cdot 5^1 + 1\cdot 5^2$ and thus result in $5+35+25=65$.

Make it work with `x = 8` and `factors = [1, 4, 2, 8, 5, 7, 1, 4]`

---


```python
x = 8
y =0
sum_ =0
factors = [1,4,2,8,5,7,1,4]
for factor in factors:
    sum_ = sum_ + factors*(x)**y
    y = y+ 1
print(sum_1)

```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    /var/folders/t7/bv9tdw3j3jq_b1f5xzyl_w5r0000gn/T/ipykernel_21172/3196477350.py in <module>
          4 factors = [1,4,2,8,5,7,1,4]
          5 for factor in factors:
    ----> 6     sum_ = sum_ + factors*(x)**y
          7     y = y+ 1
          8 print(sum_1)


    TypeError: unsupported operand type(s) for +: 'int' and 'list'


### While Loops

`While` loops rely on a condition to determine how many iterations the loop should execute. For as long as the condition is `True`, the loop will continue to run. At each iteration of the loop, the condition is checked. If the condition evaluates to `False`, the loop will terminate.


```python
i = 0
while i < 4:
    pria= 1

```

Lets unpack our while loop example. 

Initially, we declare a variable `i` and set its value to zero. Next, we declare a while loop using the `while` keyword and set a condition stating that we want our `while` loop to run for as long as our `i` variable is less than four. Through each iteration we increase `i` by one in order for our condition to eventually evaluate to `False`. What will happen if we do not increase our `i` or our condition is never met?

An issue with `while` loops is if the condition always evaluates to `True`, the loop will never stop. This is known as an **infinite loop**. Having an infinite loop will cause major issues in your code and potentially crash your program.


```python

```


```python

```

### Combining Loops with Control Flow

Loops are great for iterating through a list but what if we are looking for a particular item in a list or only want to execute a block of code if some condition is met? To accomplish these needs, we can use `if` statements within a loop.

Lets combine a `for` loop with an `if / else` statement to print if a number is even or odd. Our if statement will contain a condition checking if the modulo operation of the current value has a remainder of zero. If the condition is `True`, the number is even. Otherwise it is odd. 


```python
numbers = [10, 6, 3, 9, 8]

for i in numbers:
    if i % 2 == 0:
        print(i, "is even")
    else:
        print(i, "is odd")
```

    10 is even
    6 is even
    3 is odd
    9 is odd
    8 is even


---
#### Exercise 2
1. The FizzBuzz Challenge: Write some code that prints the numbers from 1 to 15. But for multiples of three print "Fizz" instead of the number and for the multiples of five print "Buzz". For numbers which are multiples of both three and five print "FizzBuzz".

2. Create a for loop that will iterate through the “sports_stats” list of  dictionaries. Each dictionary represents a player. At each iteration, calculate the player's goal percentage. If a player's goal percentage is greater than 50%, print their name. 


```python
15 % 3 == 0
```




    True




```python
numbers = range(1,16)
for i in numbers:
    if i % 5 == 0 == i % 3 ==0 :
        print('Fizzbuzz')
    elif i % 3 == 0:
        print('buzz')
    elif i % 5 == 0:
        print('fizz')
    else :
        print(i)
        
```

    1
    2
    buzz
    4
    fizz
    buzz
    7
    8
    buzz
    fizz
    11
    buzz
    13
    14
    Fizzbuzz



```python
sports_stats = [{
    "name": "Alan Johnson",
    "shots": 73,
    "goals": 45
    },
    {
        "name": "Spencer Woods",
        "shots": 55,
        "goals": 26
    },
    {
        "name": "Hayleigh Weeks",
        "shots": 87,
        "goals": 25
    },
    {
        "name": "Ian Smith",
        "shots": 90,
        "goals": 38
    },
    {
        "name": "Jessica Jeon",
        "shots": 21,
        "goals": 19
    }]
```


```python
for i in sports_stats:
    for x in i:
        print(i[x])
```

    Alan Johnson
    73
    45
    Spencer Woods
    55
    26
    Hayleigh Weeks
    87
    25
    Ian Smith
    90
    38
    Jessica Jeon
    21
    19


3. What does enumerate do here?

```python
my_str = "hello"
for i,j in enumerate(my_str):
    print(j)
    print(my_str[i])
```


---

### `` Break`` / ``Continue`` / ``Pass`` Statements

We can alter the flow of a loop with the use of a `break`, `continue` or ``pass`` statement. `break` will terminate the loop from executing any further. This statement can be useful when you are searching for a particular item in a list. To save on computation time, the `break` statement will stop the loop from executing any further as we do not need to continue searching for an item once it has be located.

Let's search for the number three in a list of numbers to demonstrate the `break` statement.


```python
numbers = [10, 6, 3, 9, 8]

for i in numbers:
    if i == 3:
        print(i)
        break
    print(i)

```

    10
    6
    3


The `continue` statement will halt the execution of any code within the current iteration of the loop while preserving the for loop life-cycle. This statement can be useful when you want to avoid executing a block of code if a certain condition is `True`. 

Let's use our example from above to skip printing a number instead of terminating the loop completely.


```python
numbers = [10, 6, 3, 9, 8]

for i in numbers:
    if i == 3:
        continue
        print(i)
    print(i)
```

    10
    6
    9
    8


>Note: Notice that the continue statement halted to execution of the `print` within the if statement and within the for loop iteration. 

The ``pass`` statement does nothing. When added, it doesn't change anything about the flow. 


```python
numbers = [10, 6, 3, 9, 8]

for i in numbers:
    if i == 3:
        pass
        print(i)
    print(i)
```

    10
    6
    3
    3
    9
    8


Why would we use it? Sometimes we like setting up code that will be filled in later, in order to organize the flow of the code we're writing. Imagine if you knew what you want to happen in the else part of a conditional statement but not in the if part:


```python
# you cannot leave an empty if statement
x = 3
if x > 5:
else: 
    print('I know what should happen if x is not larger than 5')
```


      File "<ipython-input-27-bce5b5011a79>", line 4
        else:
           ^
    IndentationError: expected an indented block




```python
x = 3
if x > 5:
    pass
else: 
    print('I know what should happen if x is not larger than 5')
```

### Functions

A function is a named block of code that can be called for reuse. Functions are key to creating efficient code as they give us the ability to reuse code and make our code more flexible with the use of parameters. Before we discuss the use of parameters, lets look at how we can write a function.

The structure of a function has four main parts:
- The definition keyword: `def`
- The information you want to pass in: parameters
- The code you want to execute
- The `return` keyword

After we create a function, it can be executed by "calling" or "invoking" the function name. To do this, you simply write the name of the function followed by a set of parentheses `()`. If the function requires parameters, you place them inside the parentheses separating each with a comma.

#### A Simple Function

The following simple function combines several print statements to execute together when they are called


```python
# define the function: "This is what I want you to do every time I call this function"
def print_introduction():
    print("This is a simple function")
    print("It doesn't do much except printing")
    print("But whenever you want to call these print statements together you can just call this function")
```


```python
# call the function: "Now do what I asked you to do every time I call this function"
print_introduction()
```


```python
# call the function again!
print_introduction()
```

#### Sending parameters into a function

Generally, we might want a function to change its behavior every time we call it, and can define that change using parameters. For example, we can define a function which converts kilometers to meters, and prints the result nicely


```python
# define the function
def km_to_meters(kilometers):
    print(f"You've entered {kilometers} as the input")
    meters = kilometers * 1000
    print(f"{kilometers} km is {meters} meters")
```


```python
# call the functions with 1 km
km_to_meters(1)
```


```python
# call the function with 3.4 km
km_to_meters(3.4)
```

Notice the function prints a slightly different output every time, based on the input it was given

#### Returning a result from a function calculation

Functions are actually really useful to encapsulate a computation we have to do many times. If we want to calculate a value from one or more inputs, we usually write a function for that.

The example below shows a function which takes in someone's height in meters, and their weight in kilograms, and returns their [BMI (Body Mass Index)](https://en.wikipedia.org/wiki/Body_mass_index).


```python
# define the function
def calculate_BMI(height, weight):
    
    my_BMI = weight/(height**2)
    
    return my_BMI
```


```python
# Calculate BMI for person A
person_A_BMI = calculate_BMI(1.78, 70)
print(person_A_BMI)
```


```python
# Calculate BMI for person B
person_B_BMI = calculate_BMI(1.90, 75)
print(person_B_BMI)
```

The difference between returning a value, and printing it, is that when a value is returned, we can perform more actions with it later in our program. For example, we can use it in a condition as follows:


```python
if person_A_BMI < 20:
    print("Person A's BMI is less than 20")
else:
    print("Person A's BMI is greater than, or equal to, 20")
```

#### Putting it all together

Now we can write a function which accepts some parameters, and returns a value. Let's write a function which takes in the name and age of a dog, puts the two numbers into a nicely formatted string, and then returns the string for us to print out


```python
# Creating a function
def formatToDogYears(name, age):
    formattedAge = name + " is " + str(age * 7) + ' years old in dog years.'
    return formattedAge

# Invoking a function
nicely_formatted_string = formatToDogYears('Spike', 5)
print(nicely_formatted_string)
```

#### Anatomy of a Function

<img src='https://drive.google.com/uc?view=export&id=1q-hVGi-3jCwqwjCmUvpwmbcEVkM84A2b' />

#### Parameters vs Arugments
A `parameter` refers to a variable that can be found within our function definition code. Parameters gives us the ability to pass information into a function where it is essential to produce a particular result. Think of a parameter as a placeholder, it contains no actual value. Once a parameter contains a value, it is known as an `argument`. The term parameter and argument is sometimes used interchangeably but is useful to know that a parameter only becomes an argument once a value is passed to the function.

If we refer to the function example above, "name" is the parameter while "Spike" is the argument. When the function is invoked, "Spike" replaces the name parameter on line two.

#### The return Statement
The caller passes information to a function via parameters / arguments in order to run some computation on those values. Once that computation is complete, the function should pass information back to the caller. The `return` statement is used to pass information "out" of a function or back to the caller. To capture that returned value, a function invocation is assigned to a variable. If the `return` statement is **not** used, the function will return a default value of `None`. To correctly return a value from a function, the value must be on the same line, directly after the return statement.


```python
# Correctly returns the passed value multiplied by five back to the caller
def multipleOfFive(num):
    return num * 5

correct_use = multipleOfFive(5)
print(correct_use)
```


```python
# No return statment - returns a value of None
def multipleOfFive(num):
    num * 5

no_return_statement = multipleOfFive(5)
print(no_return_statement)
```


```python
# Incorrect placement of the return statement - returns a value of None
def multipleOfFive(num):
    num * 5
    return

wrong_return_placement = multipleOfFive(5)
print(wrong_return_placement)
```

#### Docstrings
Docstrings are very important in documenting your function. A docstring should include information about what your function does and to be really specific, you can include information on what the inputs and outputs are. 


```python
# simple doctring
def my_adder(x, y):
    '''
    Adds two numerics and returns the output
    '''
    
    #inline comments can help if we have a tricky piece of logic
    #and are denoted by a # in front of the line
    out = x + y
    
    return out
```


```python
# detailed docstring
def my_adder(x, y):
    '''
    Adds two numerics and returns the output
    
    Parameters
    ----------
    x: A numeric input
    y: A numeric input
    
    Returns
    -------
    ret: A numeric output, the sum of x and y
    
    Examples
    --------
    >>>> x, y = 4, 5
    >>>> my_adder(4, 5)
    9
    '''

    
    #inline comments can help if we have a tricky piece of logic
    #and are denoted by a # in front of the line
    ret = x + y
    
    return ret
```

Our docstring is printed when we use the help function:


```python
help(my_adder)
```

    Help on function my_adder in module __main__:
    
    my_adder(x, y)
        Adds two numerics and returns the output
        
        Parameters
        ----------
        x: A numeric input
        y: A numeric input
        
        Returns
        -------
        ret: A numeric output, the sum of x and y
        
        Examples
        --------
        >>>> x, y = 4, 5
        >>>> my_adder(4, 5)
        9
    


This helps a lot when reading back through code some time later, (though it is a little bit of overkill for our adder).

#### Setting Default Values for Function Parameters

One very useful python feature is the ability to include default values for function arguments.

Here, the value `y` is given a default of 10. This means that we don't necessarily need to provide a second argument to the function when we call it. (Although we can if we'd like to override the default value.)


```python
def my_adder(x, y=10):

    ret = x + y
    
    return ret
```


```python
print(my_adder(11))
```

    21



```python
print(my_adder(1, 2))
```

    3


#### Scoping
Functions are 'scoped' locally. We don't modify anything outside them unless we try.


```python
x = 55

def my_func(z):
    #global x
    #probably don't do this.....
    x = 12
    
    return z + x

print(my_func(33))
```

    45



```python
# you can check if the variable x changed or not
print(x)
```

    55


However, watch out for mutable objects:


```python
def my_func(mylist):
    mylist.append(5)
    
    return 12

x = [1, 2, 3, 4]

my_func(x)
print(x)
```

    [1, 2, 3, 4, 5]


We can nest arbitrary code inside functions! Writing functions is the best way to make sure your analysis is reproducible, and that you can reuse common parts without retyping.

---
#### Exercise 3 - Functions

1. Create a function to convert miles to kilometers.

2. Add documentation to the function: include information about the inputs, outputs and examples of using the function.

3. Modify your function to work to convert miles to km as default, but km to mile if given `units = 'km'` as an argument.

4. Update the documentation.


```python

def Convert_(m):
    mf =1.6
    return str(m*mf) + (' km')

Convert_(1)

```




    '1.6 km'




```python

```


```python

def Convert_(m):
    mf =1.6
    return m*mf

print(f"{Convert_(1) }km")

```

    1.6km


#### Exercise 3 - Loops, Conditionals, Containers

5. Write a function that takes in a list of numbers and returns a list where each element has been squared.

6. Write a function that takes in a list of strings and returns a list containing only the elements that begin with a vowel.

7. Write a function that takes in a dictionary and returns a dictionary with the keys and values swapped.



```python

```

---

## (Supplementary) Function Assertions 

Sometimes, we want to control what kind of arguments are coming into our function. For this, we need to add assertions to our functions. Let's look at an example. 


```python
def my_adder(x, y):
    '''
    adds two numbers together and returns the output
    '''
    
    return x + y

print(my_adder(1, 2))
```

    3



```python
# my_adder works even for strings
print(my_adder('a', 'b'))
```

    ab


That's probably not what we meant to happen! Recall that python looks at how an operation is implemented for a particular data type, and applies it.

We might want our function to be a little more restrictive.


```python
# assertion to check the input types

def my_adder2(x, y):
    '''
    adds two numbers together and returns the output
    '''
    assert isinstance(x, (float, int)), 'x must be numeric'
    assert isinstance(y, (float, int)), 'y must be numeric'

    return x + y
```


```python
my_adder2('a', 'b')
```


    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-40-3637e68d5379> in <module>
    ----> 1 my_adder2('a', 'b')
    

    <ipython-input-39-735a8610a7e1> in my_adder2(x, y)
          5     adds two numbers together and returns the output
          6     '''
    ----> 7     assert isinstance(x, (float, int)), 'x must be numeric'
          8     assert isinstance(y, (float, int)), 'y must be numeric'
          9 


    AssertionError: x must be numeric


Assertions tell Python to throw an error if we get an unexpected input, which is better than returning us unexpected output, like 'ab'.

This kind of programming is often referred to as 'defensive programming'. In a lot of cases it is easier to prevent a misuse of a function than to catch the bug later.

---
#### Exercise 4

1. Add assertions to the miles-to-kilometers conversion function from Exercise 3 to ensure that the arguments input by the user are appropriate.


---

#### `Try`/`Except` Blocks

Many Python statements will throw an error if incorrectly used. "Throwing an exception" or "Throwing an error" are the phrases used to describe the following behaviour:


```python
x = 5/0
```


    ---------------------------------------------------------------------------

    ZeroDivisionError                         Traceback (most recent call last)

    <ipython-input-41-fc2abf138dd5> in <module>
    ----> 1 x = 5/0
    

    ZeroDivisionError: division by zero


Sometimes we want to ignore an error so it doesn't stop the execution of a block of code. We can use ``try`` and ``except`` to avoid these errors.


```python
try: 
    'a' + [1, 2, 3]
except Exception:
    print('I cheated the system')
    
print('After try except')
```

    I cheated the system
    After try except


Most of the time, it's useful to have Python tell us we have a problem, but crashing our entire program isn't always something we want to see. Consider the following code:


```python
number_list = []
for i in range(-10000000, 5, 1):
    number_list.append(5/i)
```


    ---------------------------------------------------------------------------

    ZeroDivisionError                         Traceback (most recent call last)

    <ipython-input-43-2356e7e9cbc0> in <module>
          1 number_list = []
          2 for i in range(-10000000, 5, 1):
    ----> 3     number_list.append(5/i)
    

    ZeroDivisionError: division by zero


We had to wait quite a while before the code crashed. Moreover, maybe we have a way to deal with zero division. This is where the `try`/`except` block comes into play. We can "try" to run the code we want to run, and if an error comes up, we can catch it and perform the appropriate operations, if anything.

**Case 1**: We want to skip over the case which is causing the problem.


```python
number_list = []
for i in range(-10000000, 5, 1):
    try:
        number_list.append(5/i)
    except ZeroDivisionError:
        pass
```

**Case 2**: We have some way of dealing with the problem.


```python
number_list = []
for i in range(-10000000, 5, 1):
    try:
        number_list.append(5/i)
    except ZeroDivisionError:
        number_list.append(float("inf"))
```

There is a wide range of different error types that we can catch using `except` statements. 

If we think with some foresight while developing our code, we can use assertions and `try`/`except` blocks to prevent a lot of undesirable behavior before it occurs.

---
#### Exercise 5

1. The function below throws an `AssertionError` if either of the assertions are violated. Write a `for` loop which runs the function for the pairs `[(0,1), ('a', 'b'), (3.5, 4.6), ('z', 30)]` but creates a new list with only the sums of the valid pairs (i.e. `[1, 8.1]`)


```python
def my_adder2(x, y):
    '''
    adds two numbers together and returns the output
    '''
    assert isinstance(x, (float, int)), 'x must be numeric'
    assert isinstance(y, (float, int)), 'y must be numeric'

    return x + y

```


```python

```

<div id="container" style="position:relative;">
<div style="position:relative; float:right"><img style="height:25px""width: 50px" src ="https://drive.google.com/uc?export=view&id=14VoXUJftgptWtdNhtNYVm6cjVmEWpki1" />
</div>
</div>
