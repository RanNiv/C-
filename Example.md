```csharp

     //stage 1
    //Base Class has no constructor
    public class Employee
    {
        public string Name { get; set; }
        public int Salary { get; set; }
    }

    //Derived class dont have to refer to base class
    public class Manager:  Employee
    {
        public readonly int Bonus;

        public Manager(int b) 
        {
            this.Bonus = b;
        }
    }
...


