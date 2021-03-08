---
layout: post
date: 2021-03-08 16:29:54 +0000
category: note
tags:
- education
- programming
title: An overview on Object Oriented Programming

---
# Object-Oriented Programming (OOP)

## What is OOP

* Capture, group info, data and related functionality into 'objects'
* OOP world viewed as a collection of objects
* Abstract data like unique data structures, user accounts etc
* Each object responsible for its own data and operations performed in that data (scope)
* Objects _can_ interact with each other

In the real world, OOP is being phased out for functional and procedural programming. OOP is seen as inefficient and complicated, making maintaining work more of a hassle- although it's a great thing to learn and understand.

I plan on writing about functional programming soon, but this is a great place to start.

These documents are going to be short and provide keynotes on the topics in question.

## What's in a class/object

* A class
  * Class name
  * Attribute
    * All of the information share by any object of this class type
  * Methods
    * Code associated with the class that allows you to access or change it's attributes
* A class is not an object itself.
* Very easy to reuse a class and create multiple objects of that class
* Classes are in themselves not an object, more of a template for one
* To create an object from a class, we go through a process called instantiation (initialising a class into an object)

```none

ClassName() 
    --> Constructor
        --> Attributes set (variables local to the class and any instantised objects from this class)
            --> SomeAttribute(String)
            --> AnotherAttribute(Integer)
    --> Methods
        --> myMethod()
        --> anotherMethod()
```

Above is an example of a class, a class itself does not serve much of a purpose, it's like a 'template' for an object

```none
new ClassName(SomeAttribute, AnotherAttribute) -> something
```

Above is an example of us using that class to create an object called 'something'. We can call methods and set attributes of something based on the attributes and methods defined in the class, ClassName.

## OOP in practice

* Implementation varies from language to language (surprise)
* Similar structure between all languages
  * Languages class keyword then the class name
  * Break out of the indentation or a marker that indicates the end of the class
  * Attributes for the class
  * Parameters and code for the instantiation of the class (e.g. __init__ in python)
    * Called a "constructor" method
    * Can be used to set local attributes before methods used

### Example implementation in python

Example of a class without any parameters in Python:

```python

"""
Example of a class being implemented in python
"""

class SomeClass(object): #A class is pretty much a template of an object

    def __init__(self):
        #self in python is the local scope of an object after instantised
        self.somevar = "Something"
```

Example of a class with parameters in Python:

```python

class SomeClass(object):

    def __init__(self,somePassedVariable):
        self.somevar = somePassedVariable # This variable is now locally available in any instantised object made from this class
```

Example of a class with a single method being instantiated into its own object:

```python

class SomeClass(object):
    
    def __init__(self,somePassedVariable):
        self.somevar = somePassedVariable

    def myMethod(self):
        print(self.somevar)

myObject = SomeClass()
>> Parameter error
# You must always try to initialise a class with all required parameters inside of it's constructor method, unless the constructor provides a default

myObject = SomeClass("A string")
>> myObject -> new SomeClass ("A string")
# We now have an object stored inside myObject which represents a copy of SomeClass

myObject.myMethod()
>> "A string"
# Thanks to our class, the object has a single method which uses a variable stored locally inside the class when we initialised it, here we call a method which utilises that variable
```

## Static methods/functions

A static function is a function that never leaves the scope of this, the local scope to that instance of an object (from a class).

```python
class SomeClass(object):
    def __init__(self,someVar):
        self.somevar = someVar
    
    @staticmethod
    def myStaticMethod():
        return "I never interact with anything in the local scope"

    def myNoneStaticMethod(self):
        return self.somevar

example = SomeClass("I do!")
example.myStaticMethod()
>> "I never interact with anything in the local scope"

example.myNoneStaticMethod()
>> "I do!"
```

## Extending a class

For examples in this section I'll extend from the class here:

```none

myClass() 
    --> Constructor
        --> SomeAttribute(String)
        --> AnotherAttribute(Integer)
    --> Methods
        --> myMethod()
            > return "Hello, world!"
        --> anotherMethod(varPassedIntoMethod)
            > return varPassedIntoMethod + self.AnotherAttribute

#Implementation of the above class
new myClass(
    SomeAttribute = "hello"
    AnotherAttribute = 2
) -> something

something.myMethod()
>> "Hello, world!"

something.anotherMethod(3)
>> 5
```

### Inheritance

One can extend an existing class, using a class as a template for another class.

This decreases code replication and allows for a simpler implementation of objects. Having a generic class makes it easier to implement multiple similar classes- we can reuse an existing class, using it's attributes and methods, without affecting the original code.

```none

anotherClass(myClass)
    # This extends myClass - we need a class with the same methods as myClass, which also carries another method for something else we may need to do
    --> Constructor
        --> VeryImportantAttribute(String)
    --> Methods
        --> veryImportantExtraMethod()
            > return self.VeryImportantAttribute + ", world!"

#Implementation of the above class
new anotherClass(
    SomeAttribute = "hello"
    AnotherAttribute = 2
    VeryImportantAttribute = "goodbye"
) -> something

something.myMethod()
>> "Hello, world!"

something.anotherMethod(3)
>> 5

something.veryImportantExtraMethod()
>> "Goodbye, world!"
```

Here `anotherClass` has inherited the same methods and attributes of myClass, we only add the new parts of the class we require.
This is called a `subclass`- a child which extends another class. Whereas `myClass` (in context of `anotherClass`), is a `superclass`- a parent to a, or multiple, child classes.

A subclass and superclass is always context-related, we could have more classes inherited from `anotherClass`, these classes would see `anotherClass` as it's superclass.

There is no limit<sup id="a1">[1](#f1)</sup> to how far you may branch a class.

<b id="f1">1</b> Theoretically in implementation, there may be limits in specific languages, or proposed by system resources [↩](#a1)

### Overriding

We can override standard inheritance by simply having an attribute or method which is identified the same way in a `subclass` as it's `superclass`

For example if `anotherClass.myMethod` was defined when creating the extension of `myClass`, the implementation of `myClass.myMethod` would not be inherited by `anotherClass`.

```none

anotherClass(myClass)
    # This extends myClass - we need a class with the same methods as myClass, which also carries another method for something else we may need to do
    --> Constructor
        --> VeryImportantAttribute(String)
    --> Methods
        --> veryImportantExtraMethod()
            > return self.VeryImportantAttribute + ", world!"
        --> myMethod()
            > return "This is completely unrelated to myClass"

#Implementation of the above class
new anotherClass(
    SomeAttribute = "hello"
    AnotherAttribute = 2
    VeryImportantAttribute = "goodbye"
) -> something

something.myMethod()
>> "This is completely unrelated to myClass"

something.anotherMethod(3)
>> 5

something.veryImportantExtraMethod()
>> "Goodbye, world!"
```

An original method can still be obtained in most object-oriented programming languages. This is done by called the `superclass` inside the `subclass`, as the original structure of the parent should always be stored.

```none
something.super.myMethod()
>> "Hello, world!"
```

### Example implementation in python

```python

class myClass(object):
    def __init__(self,SomeAttribute,AnotherAttribute) -> None: # A superclass to the other classes
        self.SomeAttribute = SomeAttribute
        self.AnotherAttribute = AnotherAttribute
    
    @staticmethod
    def myMethod()
        return "Hello, world!"

    def anotherMethod(varPassedIntoMethod):
        return varPassedIntoMethod + self.AnotherAttribute

class anotherClass(myClass): # A subclass showing inheritance
    def __init__(self,SomeAttribute,AnotherAttribute,VeryImportantAttribute):
        super().__init__() # In python to avoid rewriting the superclass constructor method, we can call it
        self.VeryImportantAttribute = VeryImportantAttribute

    def veryImportantExtraMethod(self):
        return self.VeryImportantAttribute + ", world!"

class myOverrideClass(myClass): # A subclass showing overridden methods
    def __init__(self,SomeAttribute,AnotherAttribute): # A superclass to the other classes
        super().__init__()

    @staticmethod
    def myMethod(self):
        return "This is completely unrelated to myClass"


exampleStandardClass = myClass("Something",123)
myClass.myMethod()
>> "Hello, world!"

myClass.anotherMethod(3)
>> 125

exampleInheritedClass = anotherClass("Something",321,"Goodbye")
exampleInheritedClass.myMethod()
>> "Hello, world!"

exampleInheritedClass.anotherMethod(2)
>> 323

exampleInheritedClass.veryImportantMethod("aaaa", 1337)
>> "Goodbye, world!"

overrideClass = myOverrideClass()
overrideClass.myClass()
>> "This is completely unrelated to myClass"

overrideClass.super().myClass()
>> "Hello, world!"

overrideClass.anotherMethod(1)
>> 1338
```

## Encapsulation

Encapsulation is about protecting certain contents of an initialised class, an **_object_**.

* The "bundling of data with the methods that operate on and restrict the direct access to it"
* Is used to hide the values or states of an object
* Encapsulated attributes should only be accessible or changeable by the methods provided by the **object**
* Keeps data related to an **object** safe- can't be accidentally modified by other methods
* Protected attributes act like a variable/attribute stored locally somewhere else, attempting to access it will return an error/exception in the implementation like it doesn't exist (unless accessed through the method required)

Implementation:

* You must supply methods if you want an objects internal attributes to be read/written
* An object's methods are usually public, not private
* The methods are the part of the same object, so it's private attributes are available
* Every language has it's own unique way to implement protected members

```python

class Person:
  def __init__(self): 
    self.name = 'Some'
    self.__lastname = 'Person'
    
  def PrintName(self):
    return self.name +' ' + self.__lastname#Inside the class, or once instantised an object, we can view and edit __lastname
    
#Outside class    
P = Person()
print(P.name)
>> "Some"
print(P.PrintName())
>> "Some Person"
print(P.__lastname)#When accessing this outside the object however, not going through a method, we get an error as if the attribute does not exist
>> Exception: AttributeError: 'Person' object has no attribute '__lastname'
```

## Polymorphism

* Polymorphism just means many forms
* You're likely to of used it before
  * Example in Python

    ```python
    a = "Hello"
    b = ", world!
    print(a+b) # String concatentation
    >> "Hello, world!"
    
    a = 1
    b = 2
    print(a+b) # Math operator
    >> 3
    ```
  * As you can see above, in both cases of `print(a+b)` we had completely different operations
* OOP has two types of polymorphism
  * Static
    * Multiple methods of the same name, with different parameters in the same class
    * Also known as "method overloading"
    * In order for this to work it must differ in at least one of the following ways:
      * They need to have a different number of parameters
      * The types of parameters are different
      * They expect the parameters in a different order (bad practice)
  * Dynamic
    * Some things to remember
      * A subclass can override a superclass
      * An overridden superclass means we can completely replace or customise the behaviour of that specific method we override, acting like a completely new method
    * Overriding a method of a superclass in a subclass is a form of polymorphism
      * This is as they share the same name and parameters, but have different functionality depending on how they're implemented

## Key questions

### **What are the differences between an object and a class?**

A class is more of a template for an object which could be instantiated in the future.

### **What is inheritance and how can it be used?**

Inheritance is where you create a class as a subclass of another class, allowing it to have similar attributes and methods, which can be reused or altered.

### **How can overriding be used in object-oriented programming?**

To replace a method that is unfit for the use case of a more specific/specialised implementation of a class.

### **What is encapsulation and how does it help to create a robust program?**

Encapsulation allows us to protect attributes inside of an instantiated class (an object) and therefore means we can not accidentally modify an attribute we wish to protect or of high importance, forcing us to interact with it through a method.

### **What is polymorphism and how can it be used?**

Polymorphism allows us to have different use-cases of a single method, allowing us to implement some code in the same way for all uses, but run different operations on fed data.