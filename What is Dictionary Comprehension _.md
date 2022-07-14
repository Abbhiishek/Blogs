# What is Dictionary Comprehension ?

Dictionaries are very important data structures in Python and are used in many cases. Dictionary comprehensions will make you feel comfortable when working with and creating new dictionaries.
 
Dictionary comprehension is one way to create a dictionary in Python. Using dictionary Comprehension makes it easy to deal with or with the creation of a dictionary. A dictionary comprehension allows you to run a for loop on a dictionary and do something on each item like transforming or filtering and returns a new dictionary.

Unlike a for loop, dictionary comprehension python offers a more expressive and concise syntax when we use it correctly. It returns a dictionary with a set of Key-Value pairs.

It creates a dictionary by merging different inputs or collections of data that may be from lists or arrays into a **Key: Value pair**
 
 
---
 
## Syntax
 
The data from any one of the two arrays/lists will act as the key for the dictionary while the data from another list/array will be assigned as values.
Each value or key from the first list or array would act as the **Unique identifier** for each key-value pair. Hence it’s really important to make sure the length of both the lists or arrays is the same.
 
* **Unique Identifiers:** In Dictionary every key is unique. If we want to add a new key: or value pair to a dictionary we have to use a new unique key. If the key already exists, the value is simply changed to a new assignment. Also, we can’t change an existing key, rather it will create a new one.
 
***General Syntax for Dictionary Comprehension Python:***
 
```python
{key:value for (key,value) in dict.items() if condition}
```
There are two types of merging. **Simple** and **Conditional** merging.
 
 
---
 
## Simple merging
 
The type of merging where two lists or arrays are combined without any restriction or conditions. It’s like unconditional merging.
 
 
***The general syntax is as follows:***
```python
NewDictionary={key:value for(key,value)in iterable}
```
 
* Iterable is a collection of objects like arrays or lists.
* Key:values are the pairs for the dictionary.
* key, values are the individual elements from different lists which may not be in order.
 
 
---
 
## Conditional merging
 
Conditional merging on the other hand is merging the two data i.e, key value pair on a specific event or condition which returns a Bool value.
 
The value is only inserted in place of its key if the given condition is fulfilled.Otherwise , it will just omit that key value pair and proceed to next pairs.
 
 
 
***The general syntax is as follows:***
 
```python
NewDictionary=(key:value for list in iterable if(condition)}
```
 
 
* Iterable is a collection of objects like arrays or lists.
* Key:values are the pairs for the dictionary.
* key, values are the individual elements from different lists which may not be in order.
* Conditions are the deciding factor for that value pair to merge.Conditions tend to return a bool value that's 0 OR 1.
 
 
 
 
Here , in addition to simple merging, we have extended the `if(condition)` part for defining the condition by an if keyword.
 
***Let's take a simple example for Conditional Merging :***
 
Suppose we want to create a dictionary where for every key value is stored as its cube only if the cube is completely divisible by 4.
 
 
[IMAGE {1} Create a img showing the conditional part of (`if x **3 % 4 == 0`)  START SAMPLE]
 
![simple conditional](https://hackmd.io/_uploads/HJ6paCrv9.png)
 
 
[IMAGE {1} FINISH SAMPLE]
```python
newdict = {x: x**3 for x in range(10) if x**3 % 4 == 0}
print(newdict)
```
 
Output we Get:
```python
{0: 0, 8: 512, 2: 8, 4: 64, 6: 216}
 
```
 
Here in the range of 10 only 5 key value pairs are merged and that's because of Conditional Merging as we are only checking for the values which are completely divisible by 4.
 
 
 
 
---
 
 
## Components of Dictionary Comprehension
 
[IMAGE {2} {Change the `x**2` to `x**3` }  START SAMPLE]
 
![components of dictionary Merging](https://hackmd.io/_uploads/H1md6dMw9.png)
 
 
[IMAGE {2} FINISH SAMPLE]
 
Lets try to understand the parameters mentioned above.
 
The dictionary comprehension basically consists of four parameters.
 
* **Output expression**: Defines the output (Key Value pair ) of the dictionary. This parameter is required as it defines the output structure.
 
* **List/Input**: Defines the list from which element is to be traversed.There can be two or more lists to be traversed.It's also required parameter as the new dictionary would be taking values from this.
 
* **Conditional/predicate**: Defines a condition on variable x. *This is an optional parameter*.As there may be cases when we just want to merge the whole list of data.
 
* **NewDictionary**: Saves the result of list expression depending on the condition and creates a dictionary. It's a necessary parameter if we want to store the new merged dictionary to a variable.
 
 
 
---
 
 
## Examples
 
Lets now explore some of the examples that would help us understand more about Dictionary Comprehension
 
### Using Dictionary Comprehension
 
Before going into the Comprehension Syntax , let's try to add elements into dict using for Loop.
 
Code :
```python
dict = dict() # creating an empty Dictionary
for num in range(1, 11): # keys are in range of 1 to 11 excluding 11.
    dict[num] = num+10 # setting the value for each key in iternation
print(dict) # Printing the dictionary
 
```
 
Output :
 
```python
{1: 11, 2: 12, 3: 13, 4: 14, 5: 15, 6: 16, 7: 17, 8: 18, 9: 19, 10: 20}
```
 
Now let's take a look at precise syntax which offers us the same functionality in less code.
 
Comprehensive code :
```python
# dictionary comprehension example
dict = {num: num+10 for num in range(1, 11)}
print(dict)
 
```
Through this syntax we can see that the entire for loop is replaced into the `{ }` which denotes a dictionary.
 
###  If Conditional Dictionary Comprehension
 
In this scenario , rather than using a simple List merging we would go with a condition which decides the merging to take place or not.
 
Suppose we want to filter some key value pairs from an existing dictionary to a new dictionary.
 
Code :
```python
 
stock_dict = {'Apple': 15, 'Mango': 8, 'Peer': 10, 'Watermelons': 3}
# Creating a new Dictionary for items in stock_dict if the value i,e. v is less than 10.
refill_dict = {k: v for (k, v) in stock_dict.items() if v <10}
print(refill_dict)
 
```
Output:
 
`{'Mango': 8, 'Watermelons': 3}`
 
* **items():** We access each key-value pair within a dictionary using the items() method.
 
[IMAGE {3} create a image showing the accepted and rejected entries from the items() separately.  ]
 
 
 
Through this example we can understand how conditional merging works. We are only storing those key value pairs whose value is less than 10 so that we can refill the stock.
 
### Multiple if Conditional Dictionary Comprehension
 
The above implementation is only applicable if we are dealing with a single condition.But in the real world we may have many directions of flow toward dictionary merging. Here comes the Multiple if Conditional Comprehension.
 
Code :
 
```python
# Raw Dictionary Containing Fruits Stock
stock_dict = {'Apple': 15, 'Mango': 8, 'Peer': 10, 'Watermelons': 3}
# considering the key values pairs where the stock for fruit is not divisible by 2 and less than 10.
# Storing the created dictionary into new_dict.
new_dict = {k: v for (k, v) in stock_dict.items() if v % 2 != 0 if v < 10}
print(new_dict)
 
 
```
 
Output:
 
```python
{'Watermelons': 3}
 
```
 
In this case , we have two conditions :
 
* if v % 2 != 0
* if v < 10
 
These conditions are the deciding factor for which element to be inserted or not. In this scenario , the values which are not completely divisible by 2 and less than 10 are inserted.
 
It is because of the multiple if syntax in the dictionary comprehension. They are equivalent to ***`and`*** operation where both conditions have to be true.
 
so only those key value pairs are accepted where both the conditions are met true.
 
### if-else Conditional Dictionary Comprehension
 
There may be cases when we have to modify the value according to its previous values to insert into a new dictionary. For this kind of implementation the if-else clause condition is used.
 
 
Let's take an example where we have a dictionary with name and their age.We check if the person is Applicable whose age is equal or more than 18.Then we create a new dictionary to store the information.
 
Code :
 
```python
# Raw dictionary containing Name and age
age_dict = {'Abhishek': 18, 'Aditya': 21, 'Aishik': 17, 'Abhisan':10}
# Checking for age and replacing it with Applicable
# if the age is greater or equal to 18.
new_dict = {k: ("Applicable" if v >=18 else "Not Applicable") for (k, v) in age_dict.items()}
print(new_dict)
 
 
```
 
Output:
 
```python
{'Abhishek': 'Applicable', 'Aditya': 'Applicable', 'Aishik': 'Not Applicable', 'Abhisan': 'Not Applicable'}
 
```
 
In this case we are not filtering out the key value pair rather we are modifying the value in it on the basis of previous value its stored.We can notice that how the condition is shifted from end of the Comprehensions to the part where we define the structure as we are only modifying not filtering.
 
 
## Nested Dictionary with Two Dictionary Comprehensions
 
Nesting is a programming concept where data is organized in layers, or where objects contain other similar objects. You must have often seen a nested 'if' structure, which is an if condition inside another if condition.
 
Similarly, dictionaries can be nested and thus their comprehensions can be nested as well.
 
[IMAGE {3} START SAMPLE]
 
 
![Nested Dictionary](https://hackmd.io/_uploads/SJmfSJLPc.png)
 
 
 
[IMAGE {3} FINISH SAMPLE]
 
In the above image we have a dictionary with a key named `nested_dict` for which the value itself is a dictionary where we have two keys named `Abhishek Kushwaha` and `Aditya`.
Also they have a value which is again a dictionary containing some data.This type of format is layer type which stores the data in a very friendly format as a layer of different objects.
 
We can implement dictionary comprehensions to dictionary comprehensions themselves to create nested dictionaries.
In other words , to implement a nested dictionary using python comprehensions we have to make a normal comprehensions. while defining the structure in place of value we again implement a comprehension which results in nested layer of dictionary containing data. 
 
Let's look at an example, where we nest the previously used Age dictionary inside the new dictionary with age as another dictionary in it.
 
 
Code :
 
```python
# dictionary containing some data
name_dict = {'Abhishek': 18, 'Aditya': 21, 'Aishik': 17, 'Abhisan':10}
 
# nested dictionary comprehension where the value for each key is separate dictionary comprehension.
dict = {x: {'age': v for (k ,v) in name_dict.items() if k==x } for x in name_dict.keys()}
print(dict)
```
 
Output:
 
```python
{'Abhishek': {'age': 18}, 'Aditya': {'age': 21}, 'Aishik': {'age': 17}, 'Abhisan': {'age': 10}}
```
* **keys()**: This method only returns all the keys present in the dictionary.
 
Whenever nested dictionary comprehension is used, Python first starts from the outer loop and then goes to the inner one.
The above code is a little bit different from the previous one as we have nested two dictionary comprehensions.
 
We can unfold the code as follows:
 
 
Code :
 
```python
name_dict = {'Abhishek': 18, 'Aditya': 21, 'Aishik': 17, 'Abhisan':10}
 
dict = dict() # Creating an empty dictionary
for x in name_dict.keys(): # Looping through all the keys in name_dict using keys() method.
    # for every key instance we have dictionary comprehension
    dict[x] = {'age': v for (k ,v) in name_dict.items() if k==x }
 
print(dict) # printing the dictionary
 
```
 
We can still unfold into lower level dictionary comprehensions as well.
 
Code :
 
 
```python
name_dict = {'Abhishek': 18, 'Aditya': 21, 'Aishik': 17, 'Abhisan':10}
 
dict = dict() # Creating an empty dictionary
for x in name_dict.keys(): # Looping through all
    #the keys in name_dict using keys() method.
    for (k , v) in name_dict.items():
        # Looping for second time to have key and
        # value pairs from name_dict with items() method.
        if k == x: # checking if the key from
            # first loop and second loop are the same or not.
            dict[x] = {'age': v} # filling the new dictionary with
            #key and value as another dictionary
print(dict)# printing the dictionary
 
```
 
 
## Warnings of dictionary comprehensions
 
Even though dictionary comprehensions are great for writing elegant code that is easy to read, they are not always the right choice.
 
We must be careful while using them as :
 
* They can sometimes make the code run slower and consume more memory.This is because in the dictionary for every set of data a unique key is set which requires additional time.
* They can also decrease the readability of the code as we implement more nested comprehension.
* We must not try to execute a difficult logic or a large number of dictionary comprehension inside them just for the sake of making the code single lined. In these cases, It is better to choose other alternatives like loops.
 
 
## Advantages of Dictionary Comprehension
 
Dictionary comprehension shortens the process of dictionary initialization by a lot. It makes the code more readable for small comprehension.
 
Using dictionary comprehension in our code can shorten the lines of code while keeping the logic same as before.
 
 ## Learn More
To learn more refer  [Python Comprehensions](https://www.scaler.com/topics/python/comprehensions-in-python/) 
 
## Conclusion
 
* Dictionary comprehensions are a powerful tool to create dictionaries.
* They are used to create dictionaries in a very simple way.
* It iterates over items of a dictionary and allows us to create a new dictionary by transforming or filtering each item with or without conditioning.
* The type of merging where two lists or arrays are combined without any restriction or conditions. It's like unconditional merging.
* Conditional merging on the other hand is merging the two data i.e, key value pair on a specific event or condition which returns a Bool value.
* items(): We access each key-value pair within a dictionary using the items() method.
* keys(): This method only returns all the keys present in the dictionary.
* Multiple if syntax in the dictionary comprehension are equivalent to `AND` operation where both conditions have to be true.
* If - else conditional merging is used to modify the flow depending on the condition returning boolean value.
* Comprehensions can be nested within another comprehension to form nested dictionaries.
* Dictionary comprehension shortens the process of dictionary initialization by a lot. It makes the code more readable for small comprehension.
 
 
 



