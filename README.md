# OOPS
**Object-Oriented Programming System (OOPS): Detailed Concepts with Examples**

---

### **1. Introduction to OOPS**

OOPS is a programming paradigm based on the concept of "objects," which can contain data and code. Data is in the form of fields (often known as attributes), and code is in the form of procedures (methods). It aims to implement real-world entities in programming.

Key Features of OOPS:
- **Encapsulation**
- **Inheritance**
- **Polymorphism**
- **Abstraction**

**Why OOPS?**
1. **Reusability:** Code can be reused through inheritance.
2. **Scalability:** Easy to manage and modify.
3. **Security:** Encapsulation provides data hiding.

---

### **2. Encapsulation**

Encapsulation is the mechanism of restricting direct access to some components of an object, which can be achieved through access modifiers.

#### **Key Notes:**
- **Access Modifiers:**
  - **Public:** Accessible from anywhere.
  - **Private:** Accessible only within the class.
  - **Protected:** Accessible within the package and subclasses.
  - **Default:** Accessible only within the package.

#### **Example:**
```python
class Student:
    def __init__(self, name, age):
        self.__name = name  # Private attribute
        self.__age = age    # Private attribute

    def get_details(self):
        return f"Name: {self.__name}, Age: {self.__age}"

    def set_age(self, age):
        if age > 0:
            self.__age = age
        else:
            print("Invalid age")

# Usage
student = Student("Srishti", 21)
print(student.get_details())
student.set_age(22)
print(student.get_details())
```

#### **Common Mistake:**
People try to directly access private variables.
```python
# Wrong Approach
print(student.__name)  # Raises AttributeError
```

**Solution:** Always use getter and setter methods for private variables.

---

### **3. Inheritance**

Inheritance allows one class (child class) to inherit the properties and methods of another class (parent class).

#### **Key Notes:**
- **Types of Inheritance:**
  - **Single Inheritance:** One child inherits from one parent.
  - **Multilevel Inheritance:** A child inherits from another child class.
  - **Multiple Inheritance:** A child inherits from multiple parents (not directly supported in some languages like Java but can be achieved via interfaces).

#### **Example:**
**Single Inheritance:**
```python
class Parent:
    def show_parent(self):
        print("This is the parent class")

class Child(Parent):
    def show_child(self):
        print("This is the child class")

# Usage
obj = Child()
obj.show_parent()
obj.show_child()
```

**Multilevel Inheritance:**
```python
class Grandparent:
    def show_grandparent(self):
        print("This is the grandparent class")

class Parent(Grandparent):
    def show_parent(self):
        print("This is the parent class")

class Child(Parent):
    def show_child(self):
        print("This is the child class")

# Usage
obj = Child()
obj.show_grandparent()
obj.show_parent()
obj.show_child()
```

**Multiple Inheritance:**
```python
class Parent1:
    def show_parent1(self):
        print("This is parent 1")

class Parent2:
    def show_parent2(self):
        print("This is parent 2")

class Child(Parent1, Parent2):
    def show_child(self):
        print("This is the child class")

# Usage
obj = Child()
obj.show_parent1()
obj.show_parent2()
obj.show_child()
```

#### **Common Mistake:**
- Confusion between "is-a" and "has-a" relationships.

**Solution:** Use inheritance only when the child "is-a" type of the parent. For "has-a," use composition.

---

### **4. Polymorphism**

Polymorphism means "many forms" and allows one interface to be used for a general class of actions.

#### **Types of Polymorphism:**
1. **Compile-time Polymorphism (Method Overloading):**
   - Same method name, different parameters.
   - Not directly supported in Python but can be achieved.

2. **Runtime Polymorphism (Method Overriding):**
   - A child class method overrides the parent class method.

#### **Example:**
**Method Overloading:**
```python
def add(a, b, c=0):
    return a + b + c

print(add(2, 3))        # 5
print(add(2, 3, 4))     # 9
```

**Method Overriding:**
```python
class Parent:
    def show(self):
        print("This is the parent class")

class Child(Parent):
    def show(self):
        print("This is the child class")

# Usage
obj = Child()
obj.show()  # This is the child class
```

#### **Common Mistake:**
- Forgetting to include `super()` in overriding methods when required.

**Solution:** Use `super()` to call the parent class method explicitly if needed.

---

### **5. Abstraction**

Abstraction is the process of hiding implementation details and showing only the functionality to the user.

#### **Key Notes:**
- **Achieved by:**
  - Abstract Classes (via `ABC` module in Python).
  - Interfaces (implemented in other languages).

#### **Example:**
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, length, breadth):
        self.length = length
        self.breadth = breadth

    def area(self):
        return self.length * self.breadth

# Usage
rectangle = Rectangle(10, 20)
print(rectangle.area())  # 200
```

#### **Common Mistake:**
- Trying to instantiate an abstract class.
```python
# Wrong Approach
shape = Shape()  # Raises TypeError
```

**Solution:** Always create objects of concrete subclasses, not abstract classes.

---

### **6. Class and Object**

#### **Key Notes:**
- **Class:** Blueprint for creating objects.
- **Object:** Instance of a class.

#### **Example:**
```python
class Car:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

    def details(self):
        return f"Brand: {self.brand}, Model: {self.model}"

# Creating Objects
car1 = Car("Toyota", "Corolla")
car2 = Car("Honda", "Civic")

print(car1.details())
print(car2.details())
```

#### **Common Mistake:**
- Forgetting to initialize attributes in the `__init__` method.

**Solution:** Always define and initialize attributes in the constructor.

---

### **7. Interfaces**

An interface is a blueprint for classes, specifying methods a class must implement.

#### **Key Notes:**
- Common in languages like Java and C#.
- Python achieves a similar concept via abstract classes.

#### **Example:**
```java
// Java Example
interface Animal {
    void makeSound();
}

class Dog implements Animal {
    public void makeSound() {
        System.out.println("Woof!");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal dog = new Dog();
        dog.makeSound();
    }
}
```

---

### **8. Design Principles**

#### **SOLID Principles:**
1. **Single Responsibility Principle (SRP):** A class should have one and only one reason to change.
2. **Open/Closed Principle (OCP):** Classes should be open for extension but closed for modification.
3. **Liskov Substitution Principle (LSP):** Subtypes should be substitutable for their base types.
4. **Interface Segregation Principle (ISP):** No client should be forced to depend on

