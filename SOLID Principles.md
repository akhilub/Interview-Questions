
## SOLID Principles 

  
The SOLID principles are a set of design principles aimed at promoting cleaner, more robust, and maintainable code. They consist of:  

- **S** - Single Responsibility Principle (SRP): A class should have only one reason to change.
  
- **O** - Open/Closed Principle (OCP): A class should be open for extension but closed for modification.
  
- **L** - Liskov Substitution Principle (LSP): Subtypes should be substitutable for their base types.
  
- **I** - Interface Segregation Principle (ISP): Clients should not be forced to depend on interfaces they do not use.
  
- **D** - Dependency Inversion Principle (DIP): High-level modules should not depend on low-level modules, but both should depend on abstractions.


### Single Responsibility Principle (SRP)

```python
# Bad practice: Multiple responsibilities in one class
class Employee:
    def save_employee(self):
        # save to database
        pass

    def calculate_salary(self):
        # calculate salary
        pass

# Good practice: Separate responsibilities into different classes
class EmployeeRepository:
    def save_employee(self):
        # save to database
        pass

class SalaryCalculator:
    def calculate_salary(self):
        # calculate salary
        pass
```


### Open/Closed Principle (OCP)


```python
# Bad practice: Not open for extension, closed for modification
class Shape:
    def area(self, shape_type):
        if shape_type == "circle":
            # calculate circle area
            pass
        elif shape_type == "rectangle":
            # calculate rectangle area
            pass

# Good practice: Open for extension, closed for modification
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Circle(Shape):
    def area(self):
        # calculate circle area
        pass

class Rectangle(Shape):
    def area(self):
        # calculate rectangle area
        pass
```