## Decorators in Python

# Overview
Decorators are one of the most helpful and powerful tools of Python. These are used to modify the behavior of the particular function. Decorators provide the flexibility to wrap another function to expand the features and working of wrapped function, without modifying the original called function.

# Scope of the Article

In this article , we are going to learn the following about the Decorators in Python
# Introduction
Prerequisites for learning decorators
- Functions in python
- Decorators function with parameters
- Syntactic Decorator
- Reusing Decorator
- Decorator with arguments
- Returning Values from Decorated Functions
- Fancy Decorators
- Classes as decorators
- Chaining decorators

## Introduction
A decorator is a design pattern in Python that allows a user to add new functionality to an existing function without modifying its state. Decorators are usually called before the definition of a function you want to decorate.

*Decorators are also used to gather objects and classes together in a larger structure while keeping it well organized and flexible.*

> Just like a gift we decorate to add some nice perspective to it , we use Wrapper. In Case of Decorators we do the same with a piece of code using a function that takes another function.




## Prerequisites for learning decorators

In order to understand what are decorators and how they works , we first must be familiar with the following prerequisites to begin with

- Functions in Python
- First Class Citizen
- Higher Order Function

### Functions in python

Function in Python are First Class Citizen that means that :
They can be stored like variables.
They can be returned from functions as its values.
They can be passed as an argument inside Functions.
They just act like a variable in python.

Let’s create a Simple function for Greeting People:

```py
def greet(msg):
  print(f'Greeting:{msg}')
```


It's a simple function that takes msg as an argument and prints it in formatted string.

Now let's assume that we wanted to add some top layer functionality but don’t want to change the existing function for more readable code.We decide to make another function which shows user “Good Morning” “Good Evening” and “Good Afternoon” according to time of function call:

```py
from time import time
#Function to greet people
def greet(msg):
 print(f'Greeting:{msg}')
#function to show user the current state of the day
def greet with_state(greet, msg):
 currentTime=time.strftime('&H:&M')
  if currentTime.hour<12:
       print('Good morning')
  if currentTime.hour>12:
       print('Good afternoon')
  if currentTime.hour>6:
       print( 'Good evening')
 #greet function is called inside this function
greet(msg)
```

In the above code the greet function is called inside another function greet_with_state which is a Higher Order Function.



### Higher Order Functions
There are the function that can:

Accepts another function as argument
Return another Function 

> HOF are used by decorators to create those complex structures.

Let's take another example of Higher Order Function:
```py
#Function to add two numbers
def add(x, y):
  returnx+y
#Function to subtract two numbers
def sub(x, y):
  returnx-y
#Higher Order Function
def operate( func, x, y):
  result=func(x, y)
  return result
```


# Decorators

Decorators supercharge a function and add extra functionality to it. It is simply a function that wraps another function and enhances it or modifies it.

> In layman's perspective it is something that  decorates something. Exactly, here as well decorators are something which decorates our function and add extra functionality to it.



*Now it is the time to create our own decorator*
```py
#Adecortaor Function with func as argument
def make_decorator( func):
    def inner func():
        print("I amadecorated")
        func()
    #make_decorator function return the inner_func
    return inner_func
#Anormal Function in Python
def normal():
    print("I am normal Function in python")
```


Here we have created a decorator function or a higher order function named as **make_decorator** which takes a func as parameters, and returns** inner_func** and acts like a wrapper function.

There are many ways of passing the normal function into the **make_decorator** function. One of the common ways is to call the function simply as shown below:

```py
#A decorator Function with func as argument
def make_decorator( func):
    def inner_func():
        print("I am decorated")
        func()
    # make_decorator function return the inner_func
    return inner_func
#Anormal Function in Python
def normal():
    print("I am normal Function in python")

```

We can see that the decorator function added some new functionality to the original function. This is similar to packing a gift or present. The decorator acts as a wrapper. The nature of the object that got decorated (actual normal function) does not alter. But now, it looks decorated.


## Syntactic Decorator

In python we have another way of implementing this kind of higher order function using Syntactic Decorators. To make use of a Decorator function in python we can use the @ symbol along with the name of the decorator function and place it above the definition of the function to be decorated. 

*Syntactic is syntax within a programming language that is designed to make things easier to read or to express.*

For example:

```py
#Adecortaor Function with func as argument
def make_decorator(func):
    def inner_func():
        print("I amadecorated")
        func()
    #make_decorator function return the inner func
    return inner_func
#Anormal Function in Python with decortaor
@make_decorator
def normal():
    print("I am normal Function in python")
#Calling the normal function within make_decorator function
normal()
```


The decorator function seems to be very similar to other functions , but things change when we go with parameters in function calls.

## Decorators function with parameters

Till now all the examples and use cases we discussed are good for the function which has no passing parameters in it. 

What if we have some function which arguments?

```py
#additions function
def add(x,y):
  return x+y
#subtraction function
def add(x,y):
  return x-y
def calculator(func):
  def cal():
    print('Your are using a calculator')
    result=func()
    print(result)
  return cal
```

In this scenario the Calculator function would work as we are not passing the arguments here. For that we also have to pass the same arguments in cal function inside the calculator function.

```py
#additions function
@calculator
def add(x,y):
  return x+y
#subtraction function
@calculator
def sub(x,y):
  return x-y
def calculator(func):
 def cal(x, y):
    print('Your are usingacalculator')
    return func(x, y)
  return cal
sum=add(10,20)
Minus=sub( 20, 10)
```


This way one can pass parameters into a decorative function


There may be case when you don't know how many positional arguments is to be passed and in that case *args, **kwargs  are considered at that place.

Lets have an example to understand it more easily:

```py
#Adecortaor Function with func as argument
def my_decorator(func):
    %23 To deal with unknow number of positional arguments 
    def wrap_func(*args, **kwargs):
            print('***********')
            func(*args, **kwargs)
           print('***********')
    return wrap_func
@my_decorator
def hello(greeting,msg):
      #we are passing multiple arguments which may not be
defined in decorator function
      print(greeting, msg)
hello( 'Hey Learner! ', 'Welcome to HashNode')
```


## Reusing Decorator
Just like an ordinary function a Decorator function can be used multiple times.

Let's create a decorator function with the following code:

```py
def run_twice( func):
  def wrapper():
    #this wrapper runs twice
      func()
      func()
  return wrapper
@run_twice
def greet():
  print( 'Hello')
greet()
```


The decorator run_twice  runs whatever the function is passed twice. This simply suggests that A decorator can be reused just like any other function.

## Decorator with arguments

The same way a value is passed in function we can pass arguments to Decorator itself too.
Let's try to create a Decorator with arguments with same functionality as above:

```py
def run_multiple(num):
  def run(func):
    def wrapper( ):
      #this wrapper runs num times
      for-in range( num):
         func()
    return wrapper
  return run
@run_multiple(num=3)
def greet():
 print( 'Hello')
                  
greet()
```



## Returning Values from Decorated Functions

Same as ordinary functions we can return something out of the wrapper function.
Consider the following timing function, it prints a statement then returns the current time, we are decorating it with another function:

```py
from time import time
def my_decorator(func):
  def wrapper( 0:
    print("Time is ")
    result=func()
    return result
  return wrapper
@my_decorator
def timing():
 t1=time()
  return t1
time=timing()
print(time)
```
     

Here :

- Timing function :  It's getting decorated by my_decorator where the function is called and value is stored in the result variable which is again returned from the wrapper function.


- Return : The return in wrapper and my_decorator function is must otherwise the value is lost which was returned from the original timing Function.

## Fancy Decorators

Till now, you have seen how to implement decorators on functions. You can also use decorators with classes, these are known as fancy decorators in Python. 

There are two possible ways for doing this:

- Decorating the methods of a class.
- Decorating a complete class.

## Decorating the Methods of a Class

*Python provides the following built-in decorators to use with the methods of a class:*

- @classmethod: It is used to create methods that are bound to the class and not the object of the class. It is shared among all the objects of that class. The class is passed as the first parameter to a class method. Class methods are often used as factory methods that can create specific instances of the class.
- @staticmethod: Static methods can't modify object state or class state as they don't have access to cls or self. They are just a part of the class namespace.

```py
class Person:
     @staticmethod
     def hello( ):
          print( "Hello Reader! How much you are liking this topic ?")
per=Person(O
per.hello()
Person.hello()
```

- @property: It is used to create getters and setters for class attributes.
Let's see an example of all the three decorators:

```py
class Student:
    def _init_(self, name, level):
         self.name name
         self.level=level
    @property
    def info(self):
         return self.name+"Has Level"+self.level
stu=Student("Abhishek Kushwaha","10")
print( "Name:", stu.name)
print("Level:", stu.level)
print(stu.info)
```

## Decorating a Complete Class

You can also use decorators on a whole class.
Writing a class decorator is very similar to writing a function decorator. The only difference is that in this case the decorator will receive a class and not a function as an argument. Decorating a class does not decorate its methods. It's equivalent to the following:

```py
className = decorator(className)
```


Decorators can be used with the methods of a class or the whole class.

# Classes as Decorators

We can also use a class as a decorator also. Classes are the best option to store the state of data, so let's understand how to implement a decorator with a class that will record the number of Reader called a function.
There are two requirements to make a class as a decorator:
The __init__ function needs to take a function as an argument.
The class needs to implement the __call__ method. This is required because the class will be used as a decorator and a decorator must be a callable object.
Now, let's implement the class:

```py
class CountCalls:
  def _init_(self, func):
    self.func func
    self.num_reader=0
    ACallable Object
  def _call_(self, *args, **kwargs):
    self.num_reader +=1
    print(f"hello Reader {self.num_reader} of {self.func._name__!r}")
    return self.func(*args, **kwargs)
@CountCalls
def Scaler( ):
  print("Thanks For Reading!")
Scaler()
Scaler()
Scaler()
```


After decoration, the __call__ method of the class is called instead of the Scaler method.
Classes can also be used as decorators by implementing the __call__ method and passing the function to __init__ as an argument.






# Chaining decorators

Chaining the decorators means that we can apply multiple decorators to a single function. These are also termed as nesting decorators.
Consider the following two decorators:

```py
def split_string(func):
  def wrapper(*args, **kwargs):
    print("This is Split Decorator")
    return func(*args, **kwargs).split()
  return wrapper
def to_upper(func):
  def wrapper (*args, **kwargs):
    print("This is UpperCase Decorator")
    return func(*args, **kwargs).upper()
  return wrapper
@split_string
@to_upper
def greet(name ):
  return f"Hello, {name}!"
print(greet("Abhishek"))
```


- The first one takes a function that returns a string and then splits it into a list of words.
- The second one takes a function that returns a string and converts it into uppercase.

We have used both the decorator on the single function. This way of applying multiple decorator in a single function is often called as **Chaining**.

Output:

```py
This is Split Decorator
This is UpperCase Decorator
['HELLO,', 'ABHISHEK!']
```



**Explanation:**
In case of multiple decorator , the order matters as the one called first is executed first and so on.
Here :

- Split_string is applied first which prints the statement : This is Split Decorator , after which the main function i.e greet is returned.

- return func(*args, **kwargs).split() - This statement makes the pointer to enter the to_upper decorator , where it prints the statement : This is UpperCase Decorator , after which the main function where upperCase object is used and value is returned.


You can achieve this by also using statement like this

```py
greet=split_string(to_upper(greet))
print(greet)
```


- You can apply multiple decorators to a single function by stacking them on top of each other.