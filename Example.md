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
derived class must call base class constructor
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


