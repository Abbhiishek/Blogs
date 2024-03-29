## Python is an object-oriented programming language

## Is Python an object-oriented programming language?

Yes, Python is an objected oriented programming language. Everything in python is an object. Using python we can create classes and objects,for example, that functions are first-class objects. Functions, classes, strings, and even types are objects in Python: like any object, they have a type, they can be passed as function arguments, and they may have methods and properties. Therefore, **Python is object oriented programming language.**
   

## Main Concepts of Object-Oriented Programming

Object-oriented programming is a method of structuring a program by bundling related properties and behavior into individual objects. These objects are related to entities. Object-oriented programming language helps us in writing reusable code. It is a popular and widely used method of solving problems by creating objects.

For example let's take human as a class.The height , weight , colour are all the attributes of a object. The biological Processes like Breathing , Walking , Eating all are considered as Methods with data and logic.


Object-oriented Programming (OOP) is a computer programming model that helps one organize their software design around data, class, and object rather than functions and logic.

Let us think of a Clothing factory where each step of the line processes some material and transform it into a finished product.

Classes and objects are the two main building blocks of object-oriented programming. A class creates a new type of object where objects are instances of the class.

## Class
Class is the blueprint used to create a user-defined data structure. It holds the common attribute and behaviors of the object. For example, the class “Cloth” will hold objects “Shirt”, “Pant” and “Tshirt”.

For example, let us say that we want to store information on clothes, the general approach would be to store all the information on a list.

```python
# name = ["category" , size , "company" , price]
shirt = [ "Shirt", 34, "xyz-company", 2000 ]
pant = [ "Pant", 34, "xyz-company", 1500 ]
tshirt = [ "Tshirt", 34, 1200 ]
```
There are several issues with this approach.

First, it can make larger code files more difficult to manage. If you reference pant[0] several lines away from where the pant list is declared.
There may be a case when we forget the index for the required value.

Second, it can introduce errors if not every cloth has the same number of elements in the list. In the third list above, the company is missing, so the tshirt[2] will return 1200 instead of the t-shirt's company name.

A great way to make this type of code more manageable and more maintainable is to use classes.

All class definitions start with the class keyword, which is followed by the name of the class and a colon. Any code that is indented below the class definition is considered part of the class’s body.

Here's an example of a Cloth Class :
```python
#we define a class using the keyword class <name_of_class>:
class Cloth: 
    pass
```

> Note: Python class names are written in CapitalizedWords notation by convention. For example, a class for a specific brand of cloth like the John Players would be written as JohnPlayers.

Currently, our class doesn't do much. We need to manage the properties like size, price, name, and company name. We define those properties using a method called  **.__init__()**. Every time a new cloth object is created **.__init__()** sets the initial state of the object by assigning the values of the object's properties.

You can give .__init__() any number of parameters, but the first parameter will always be a variable called self. When a new class instance is created, the instance is automatically passed to the self parameter in .__init__() so that new attributes can be defined on the object.

Let's update the cloth class with **.__init__()** method that create .name , .size , .price , .company_name attributes:

```python
class Cloth:
    def __init__( self, name, size , price , company_name ):
        self.name = name
        self.size = size
        self.price = price
        self.company = company_name
```
Using such a Class creating and managing data seems quite easy

`shirt = Cloth("shirt", 25 , 1200 , "xyz")`
By using such a syntax we can retrieve each value as follows :
```python
shirt.name # returns the name 
shirt.size # returns the size
shirt.price # returns the price
shirt.company # returns the company name
```


## Object

An object is an instance of a class. It has both a property (variables) and behavior (methods). The python object “Cloth” will have properties; “buy”, “about”, “sell” and behaviors; “discount”, and “show”.


Everything in Python is an object, and almost everything has attributes and methods. All functions have a built-in attribute __doc__, which returns the docstring defined in the function source code.

```python
# Defining a class named Cloth
class Cloth:
    def __init__( self, name, size , price , company_name ):
        self.name = name
        self.size = size
        self.price = price
        self.company = company_name  
  
shirt = Cloth( "shirt", 25 , 1200 , "xyz" ) # creating object shirt
```

## Method

Methods are the functions that are defined inside a class and can only be called from an instance of that class. A method includes the operation and functionality of the object. These methods are defined inside a class. These methods are the reusable piece of code that can be invoked/called at any point in the program.

```python
# Defining a class named Cloth
class Cloth:
    def __init__( self, name, size , price , company_name ):
        self.name = name
        self.size = size
        self.price = price
        self.company = company_name
        
    def show( self ):  # Method 
        print( self.name, self.size, self.price, self.company )  
  
shirt = Cloth( "shirt", 25 , 1200 , "xyz" ) # Creating object shirt
shirt.show() # using a method over a object.

```

Here the show is a method or functionality to print all the data being passed at the time of object creation. 

## Inheritance

Inheritance is the process by which one class takes on the attributes and methods of another. Newly formed classes are called child classes, and the classes that child classes are derived from are called parent classes.

It specifies that the child object acquires all the properties and behaviours of the parent object.

Inheritance has many advantages some of them are :

* It provides the reusability of the code.
* It provides Transition and Readability.
* Real World Relationship.

```python
class Parent: # Parent class
    def parent_func( self ): # simple function
        print( 'This is a Parent Class' )
        
class Child( Parent ): # child class with Parent class as attribute
    def child_func( self ): # simple function
        print('This is Child class')
        

ob = Child()
ob.child_func()
ob.parent_func()
```
Here we can notice that despite creating an Object of child class we have access to the method from a different class. Since we know that methods are restricted to their instance, here we have access to them. This is due to inheritance as the Child class has the attribute of the Parent class.


```python
class Parent: # Parent class
    def __init__( self,name,wish ): # init func
        self.name = name
        self.wish = wish
        
    def parent_func(self): # simple function
        print('This is a Parent Class')
        
    def show( self ):
        print( self.name , self.wish )
        
class Child( Parent ): # child class with Parent class as attribute
    def __init__( self,name,wish,age ):# init function
        Parent.__init__( self,name,wish ) # using Parent init method for name and wish 
        self.age = age
        
    def child_func( self ): # simple function
        print( 'This is Child class' )
        
    def show( self ):
        print( self.name , self.wish , self.age )
        

ob = Child( "abhishek" , "Happy Reading" , 20 ) # passing all the three arguments.
ob.show() # calling the method
```

Inheritance also overrides the __init__ method. To avoid that we need to declare the Parent init function under the child __init__ Method.

`Parent.__init__(self,name,wish)`

This is how we can override the Parent init function in the child function.

## Polymorphism

Polymorphism contains two words "poly" and "morphs". Poly means many, and morph means shape. By polymorphism, we understand that one task can be performed in different ways. It's the ability to use a common interface for multiple forms or data.


Now in this example, we have created two classes “Cat” and “Dog”. They’re different animals and make different sounds. So, the make_sound() function should produce two different outputs based on the objects we pass through them. In this case, we have created two objects “cat1” and “dog1”.

[IMAGE {04} show that class Cat and Dog have the same method make_sound and method overload ]

```python
class Cat:
    def __init__( self, name, age ):
        self.name = name
        self.age = age
 
    def info(self):
        print(f"I am a cat. My name is {self.name}. I am {self.age} years old.")
 
    def make_sound( self ):
        print("Meow")
 
 
class Dog:
    def __init__( self, name, age ):
        self.name = name
        self.age = age
 
    def info(self):
        print( f"I am a Dog. My name is {self.name}. I am {self.age} years old." )
 
    def make_sound( self ):
        print( "Bark" )
cat1 = Cat( "Kitty", 2.5 )
dog1 = Dog( "Fluffy", 4 )
 
for animal in ( cat1, cow1 ):
    animal.make_sound()
    animal.info()
    animal.make_sound()
```

The make-sound() function is producing two different outputs- “Meow” and “Bark”.


This concept in Object Oriented Programming is called Polymorphism. We can also consider this as Method Overloading.

Let's Create two classes and have some similar properties associated with them:

```python
class Phone:
    def send_msg( self, x ): # send msg function
        print(f"Sending {x} as message ...")
        
    def switch_off( self ): # switch off function
        print("Turning it off")
        
class Watch:
    def send_msg( self,x ): # send msg function
        print("Cannot send the message")
    
    def switch_off( self ): # switch off function
        print("Removing the battery")
```
Here we can notice that we have two classes Phone and Watch which have two same methods send_msg and switch_off.
Now to call these methods we have to call them separately.This may look tedious to do, well we have an easy way to implement the solution of the above problem as follows:


```python
def try_send_msg( Gadget ): # creating a common interface
    Gadget.send_msg()
```
Now lets create two instance of Object class
```python
iphone = Phone()
iwatch = Watch()
```
Besides calling both the methods differ for different classes, we pass that into the common interface that we created above.

```python
try_send_msg( iphone ) # passing iphone instance
try_send_msg( iwatch ) # passing iwatch instance
```

So the final code goes as follows:

```python
class Phone:
    def send_msg( self ):
        print( "Sending as message ... from phone" )
        
    def switch_off( self ):
        print( "Turning phone off" )
        
class Watch:
    def send_msg( self ):
        print( "Cannot send the message from watch" )
    
    def switch_off( self ):
        print( "Removing the battery of watch" )
        
def try_send_msg( gadget ): # creating a common interface
    gadget.send_msg()
    

iphone = Phone() # creating instance of Phone
iwatch = Watch() # creating instance of Watch

try_send_msg(iphone) # passing iphone instance
try_send_msg(iwatch) # passing iwatch instance

```

With the following code the given output is as follows:

```python
Sending as the message ... from phone
Cannot send the message from watch
```

So we can see that besides calling the same method to a different class that is from a different instance, we wrap those methods into a common interface and pass the instance as parameters.

## Encapsulation

Encapsulation is also an essential aspect of object-oriented programming. It is used to restrict access to methods and variables.

Encapsulation refers to the wrapping up of data under a single unit. It acts as a protective shield for methods and function.

Encapsulation has some benefits, some of which are :

- Data Hiding
- Flexibility
- Reusability

```python
class Scaler():
    def __init__(self):
        self.blogname = "OOPS"
        self.language = "Python"
        
    def about(self):
        print(self.blogname , self.language)
        
        
ob = Scaler()
ob.about()
```
This gives the following as output :

`OOPS Python`
Till now everything seems working. Let's make the language attribute a private attribute by naming convention by using a double underscore at first like __attribute-name.



This makes the attribute only accessible within the scope of the class for the implementation.

Let's have a look at the code.

```python
class Scaler(): # defining the class 
    def __init__(self):
        self.blogname = "OOPS"
        self.__language = "Python"
        
    def about(self):
        print(self.blogname , self.__language)
        
        
ob = Scaler() # Creating Instance 
ob.__language  # this throws Attribute Error.
```

`__Language` makes the attribute language private to its scope. Also, there are ways to recall the value stored in `__language` Attribute by the following code:



```python
class Scaler(): # defining the class 
    def __init__(self):
        self.blogname = "OOPS"
        self.__language = "Python"
        
    def about(self):
        print(self.blogname , self.__language)
        
        
ob = Scaler() # Creating Instance 
print(ob._Scaler__language) # This works and print Python
```
The above code has the following output :
`Python`

Another use-case could be that we want to update a certain value in an attribute but we don't want to make that attribute accessible outside the scope.

Let's portray this by the following code :
```python
class Scaler(): # defining the class 
    def __init__(self):
        self.blogname = "OOPS"
        self.__language = "Python"
        
    def about(self):
        print(self.blogname , self.__language)
        
    def set_language(self , x): # function to set a new value to language attribute
        self.__language = x
        
    def get_language(self): # function to get the current value of langauge attribute.
        return self.__language
        
        
ob = Scaler() # Creating Instance 
print(ob._Scaler__language) # This works and print Python
ob.set_language("py") # setting py as new language
print(ob.get_language()) # getting py as new language
print(ob._Scaler__language)

```

## Data Abstraction

Data abstraction and encapsulation are often used as synonyms. Both are nearly synonyms because data abstraction is achieved through encapsulation.

Abstraction refers to hiding unnecessary details to focus on the whole product instead of parts of the project separately. It is a mechanism that represents the important features without including implementation details. Abstraction helps us in partitioning the program into many independent concepts so we may hide the irrelevant information in the code. It offers the greatest flexibility when using abstract data-type objects in different situations.

Let us take the example of a Mobile. It has a screen, camera, body, etc. All these things combine to form a fully functional mobile, which is an abstraction, and all the different parts are its layers of abstraction. Now a screen is composed of various parts such as a display, touch module, screen guard, etc. For these flayers, the screen is an abstraction. In simple words, abstraction can be achieved by hiding the background details and showing only the necessary ones. In programming, abstraction can not be achieved without Encapsulation.


 

- Abstract Class - Which has one or more Abstract Methods.
- Abstract Methods - Methods with the declaration but not the definition.
- Abstract classes can not be instantiated, and require subclasses to provide implementations for the abstract methods.
- Subclasses of an abstract class in Python are not required to implement abstract methods of the parent class.

```python
from abc import ABC, abstractmethod # predefined abstract Abc

class Parent(ABC):   # creating a class with ABC with 
    
    @abstractmethod  # changing the method to abstract one 
    def display(self): # not implemented method
        None
        
        
class Child(Parent):  # creating a child class that continues Parent class
     def display(self): # defining the abstract method here.
        print("this is display method from child class")
            
            

ob = Child()
ob.display()
```
Here when we create an instance of Child class and call a method over that it first goes to the child class display method which is extended from Parent class. Inside the parent class, we have displayed as an abstract class means the implementation is not present in the particular class. Therefore it's overridden by the child class.

This is how we implement a large codebase where the logic is separated into different classes for more organized and readable code.


Let's understand with another example :

Below we have made an abstract class named Mobile where we have an abstract method named switch_on. The method's implementation is not given in the class. Later on Another child class of Mobile named Screen with extended Mobile class, we have switch_on method implementation.
```python

from abc import ABC, abstractmethod

# creating a parent class
class Mobile(ABC):

    @abstractmethod  # specifing all the method as an abstract method
    def switch_on(self): # a method definition for turning the screen on.
        pass

class Screen(Mobile):
    def switch_on(self):
        print("switched on via Screen class")

power = Screen()
power.switch_on()
```

When the switch_on method is called over power instance, its points to the switch_on method from the Screen class where the implementation is executed. 


## Learn more 

[What is object-oriented programming ?](https://www.scaler.com/topics/what-is-object-oriented-programming-oop/)

[Object oriented programming concept in python](https://www.scaler.com/topics/oops-concepts-in-python/)


## Conclusion

- Class is the blueprint of an object. It is used to declare and create objects. Class is a logical entity. Example: Computer is a class.
- Object is an instance of the class. The object is a physical entity. And we can create as many objects as we want. Example: Mouse, Keyboard, Monitor, etc are objects of class Computer.
- Inheritance is an OOP concept, where existing classes can be modified or overridden by a new class. The existing class is called the base class or parent class and the new class is called the derived class or child class.
- Polymorphism in OOP allows an object to take many forms. Simply, polymorphism allows us to perform the same action in many different ways. It's the ability to use a common interface for multiple forms or data.
- Encapsulation in OOP is the process of restricting access to methods and variables. Encapsulation refers to the wrapping up of data under a single unit. It acts as a protective shield for methods and function.
- Abstraction refers to hiding unnecessary details to focus on the whole product instead of parts of the project separately. Abstraction is done by Encapsulation.