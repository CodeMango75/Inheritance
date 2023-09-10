# Inheritance 
The English meaning of Inheritance is Inheritance refers to the *process of transmission of genes from parent to 
offspring.*

In **Python** Inheritance allows us to define a class that inherits all the methods and properties from another class.
* Inheritance is a fundamental concept in Object-Oriented Programming (OOP) that allows you to create a new class based on an existing class
* The new class, called the "subclass" or "derived class," inherits attributes and methods from the existing class, known as the "**Super Class**" or "**parent/base class**."
* In Python, inheritance is used to promote code reuse and to establish a hierarchy of classes.

### Super Class (Base Class or Parent Class):
* This is the existing class from which you want to inherit attributes and methods (class being inherited from).
* The base class defines the common characteristics and behaviors that can be shared among multiple classes.
```commandline
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        pass
```
* Any class can be a parent class, so the syntax is the same as creating any other class:
Create a class named <span style="color:red;">Person</span>, with <span style="color:red;">FirstName</span> and 
  <span style="color:red;">LastName</span>
```commandline
class Person:
  def __init__(self, fname, lname):
    self.firstname = fname
    self.lastname = lname

  def printname(self):
    print(self.firstname, self.lastname)

#Use the Person class to create an object, and then execute the printname method:

x = Person("John", "Doe")
x.printname()
```
### Subclass (Derived Class or Child Class)

**Subclass** is the class that inherits from another class, also called derived class or Child Class.
* This is the new class that inherits attributes and methods from the base class.
* The subclass can also have its own attributes and methods in addition to what it inherits.
```commandline
class Student(Person):
    def __init__(self, fname, lname, year):
        super().__init__(fname, lname)
        self.graduationyear = year

    def welcome(self):
        print("Welcome", self.firstname, self.lastname, "to the class of", self.graduationyear)
```
In this example, `Student` is a subclass of `Person`. It inherits attributes from `Person` and adds its own, like `graduationyear`.

**To create a class that inherits the functionality from another class, send the parent class as a parameter when 
creating the child class**

From Example 1 above, Create a class named <span style="color:red;">Student</span>, which will inherit the properties 
and methods from the Person class:
```
x = Student("Mike", "Olsen")
x.printname()
```
## Adding New Attributes and Methods
* Subclasses can also have their own attributes and methods in addition to what they inherit from the base class.
```
class Bird(Animal):
    def __init__(self, name, species):
        super().__init__(name)  # Call the constructor of the base class
        self.species = species

    def speak(self):
        return f"{self.name} chirps!"

    def fly(self):
        return f"{self.name} is flying!"
```
In this example, the `Bird` class inherits from `Animal` but also has its own `species` attribute and `fly` method.

**Note**: When you add the `__init__()` function, the child class will no longer inherit the parent's `__init__()` function.

### Method Overriding

* Subclasses can override methods inherited from the base class, providing their own implementations.
* This allows for **polymorphism**, where different objects can respond differently to the same method call. Here's an example with the `speak` method:
```
class Dog(Student):
    def speak(self):
        return f"{self.firstname} says Woof!"

class Cat(Student):
    def speak(self):
        return f"{self.firstname} says Meow!"
```
* Inheritance in Python helps in creating a more organized and efficient codebase by reusing and extending existing code. It also facilitates the modeling of real-world relationships between objects in a program.

**However**, To keep the inheritance of the parent's `__init__()` function, add a call to the parent's `__init__()` function:
```
class Student(Person):
  def __init__(self, fname, lname):
    Person.__init__(self, fname, lname)
```
Now we have successfully added the `__init__()` function, and kept the inheritance of the parent class, and we are ready to add functionality in the `__init__()` function.


## Using the `super()` Function
* Python also has a `super()` function that will make the child class inherit all the methods and properties from its parent. 
*  It simplifies the process of calling the superclass's constructor, especially when there are multiple levels of inheritance.
```
class Student(Person):
    def __init__(self, fname, lname, year):
        super().__init__(fname, lname)
        self.graduationyear = year

```
By using the `super()` function, you do not have to use the name of the parent element, it will automatically inherit the methods and properties from its parent.

## Add Properties
Add a property called <span style="color:red;">graduationyear</span> to the Student class:
```
class Student(Person):
  def __init__(self, fname, lname):
    super().__init__(fname, lname)
    self.graduationyear = 2019
```
In the example below, the year `2019` should be a variable, and passed into the Student class when creating student objects. To do so, add another parameter in the `__init__()` function:
Now, Add a <span style="color:red;">year</span> parameter, and pass the correct year when creating objects:
```
class Student(Person):
  def __init__(self, fname, lname, year):
    super().__init__(fname, lname)
    self.graduationyear = year

x = Student("Mike", "Olsen", 2019)
```

## Add Methods
Add a method called <span style="color: red;">welcome</span> to the Student class:
```
class Student(Person):
  def __init__(self, fname, lname, year):
    super().__init__(fname, lname)
    self.graduationyear = year

  def welcome(self):
    print("Welcome", self.firstname, self.lastname, "to the class of", self.graduationyear)
```
If you add a method in the child class with the same name as a function in the parent class, the inheritance of the parent method will be overridden.

