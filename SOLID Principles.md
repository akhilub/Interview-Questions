
## SOLID Principles 

  
The SOLID principles are a set of design principles aimed at promoting cleaner, more robust, and maintainable code. They consist of:  

- **S** - Single Responsibility Principle (SRP): A class should have only one reason to change.
  
- **O** - Open/Closed Principle (OCP): A class should be open for extension but closed for modification.
  
- **L** - Liskov Substitution Principle (LSP): Subtypes should be substitutable for their base types.
  
- **I** - Interface Segregation Principle (ISP): Clients should not be forced to depend on interfaces they do not use.
  
- **D** - Dependency Inversion Principle (DIP): High-level modules should not depend on low-level modules, but both should depend on abstractions.


### Single Responsibility Principle (SRP)

::: tabs

@tab Python
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

@tab Java
```java
// Bad practice: Multiple responsibilities in one class
public class Employee {
    public void saveEmployee() { /* save to database */ }
    public void calculateSalary() { /* calculate salary */ }
}

// Good practice: Separate responsibilities into different classes
public class EmployeeRepository {
    public void saveEmployee() { /* save to database */ }
}

public class SalaryCalculator {
    public void calculateSalary() { /* calculate salary */ }
}
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

### Liskov Substitution Principle (LSP)

```python
# Bad practice: Subtype not substitutable for base type
class Bird:
    def fly(self):
        pass

class Eagle(Bird):
    def fly(self):
        # eagle flies
        pass

class Penguin(Bird):
    def fly(self):
        raise NotImplementedError("Penguin cannot fly")

# Good practice: Subtype substitutable for base type
class Bird:
    pass

class FlyingBird(Bird):
    def fly(self):
        pass

class Eagle(FlyingBird):
    def fly(self):
        # eagle flies
        pass

class Penguin(Bird):
    # Penguin-specific behavior
    pass

```


### Interface Segregation Principle (ISP)

```python
# Bad practice: Client forced to depend on unused interface methods
from abc import ABC, abstractmethod

class Printer(ABC):
    @abstractmethod
    def print(self):
        pass

    @abstractmethod
    def fax(self):
        pass

    @abstractmethod
    def scan(self):
        pass

class BasicPrinter(Printer):
    def print(self):
        # print
        pass

    def fax(self):
        raise NotImplementedError("BasicPrinter cannot fax")

    def scan(self):
        raise NotImplementedError("BasicPrinter cannot scan")

# Good practice: Client not forced to depend on unused interface methods
class Printer(ABC):
    @abstractmethod
    def print(self):
        pass

class Fax(ABC):
    @abstractmethod
    def fax(self):
        pass

class Scanner(ABC):
    @abstractmethod
    def scan(self):
        pass

class BasicPrinter(Printer):
    def print(self):
        # print
        pass

class AdvancedPrinter(Printer, Fax, Scanner):
    def print(self):
        # print
        pass

    def fax(self):
        # fax
        pass

    def scan(self):
        # scan
        pass
```


### Dependency Inversion Principle (DIP)

```python
# Bad practice: High-level module depends on low-level module
class Database:
    def save_payment(self):
        # save payment to database
        pass

class PaymentProcessor:
    def __init__(self):
        self.database = Database()

    def process_payment(self):
        self.database.save_payment()

# Good practice: High-level module depends on abstraction
from abc import ABC, abstractmethod

class PaymentRepository(ABC):
    @abstractmethod
    def save_payment(self):
        pass

class Database(PaymentRepository):
    def save_payment(self):
        # save payment to database
        pass

class PaymentProcessor:
    def __init__(self, repository: PaymentRepository):
        self.repository = repository

    def process_payment(self):
        self.repository.save_payment()
```




::: tabs


:::tabs
@tab Python
```python
def hello():
    print("Hello World")
```

tab JavaScript
```javascript
function hello() {
    console.log("Hello World");
}
```
