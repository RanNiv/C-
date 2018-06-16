### stage 1
Base Class has no constructor
```csharp
     public class Employee
    {
        public string Name { get; set; }
        public readonly int Salary;
    }
```
Derived class dont have to refer to base class 
and can't change the readonly field
```csharp
   public class Manager:  Employee
    {
        public readonly int Bonus;

        public Manager(int b) 
        {
            this.Bonus = b;
        }
    }
```  

### stage 2
Base Class has  constructor 

recall that once you add a custom constructor to a class definition, the default constructor is
silently removed. Therefore, be sure to redefine the default constructor. For example:
```csharp
  public class SalesManager : Manager
    {
        public readonly int Sales;

        public SalesManager() : base(50)
        {
           
        }
    }
```


derived class must call base class constructor
derived class can update the readonly field implicitly only in the base constructor,
but can not access the base class private fields
private members can only be accessed by the class that defines it.

You may use the base keyword whenever a subclass wishes to access a public or protected member
defined by a parent class. Use of this keyword is not limited to constructor logic. You will see examples using base
in this manner during the examination of polymorphism, later in this chapter.

```csharp
   public class Employee
    {
        public string Name { get; set; }
        public readonly int Salary;

        public Employee(string name,int salary)
        {
            this.Name = name;
            this.Salary = salary;
        }
    }


    public class Manager:  Employee
    {
        public readonly int Bonus;

        public Manager(int b) : base("Test", 5000)
        {
            this.Bonus = b;
        }
    }
    ```
    ###The protected Keyword
 As you already know, public items are directly accessible from anywhere, while private items can only be
accessed by the class that has defined them. provides an additional keyword to define member accessibility: protected.
When a base class defines protected data or protected members, it establishes a set of items that can
be accessed directly by any descendent.
```charp
partial class Employee
{
// Derived classes can now directly access this information.
protected string empName;
protected int empID;
protected float currPay;
protected int empAge;
protected string empSSN;
}



