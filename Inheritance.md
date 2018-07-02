### Class Inheritance

<p>Inheritance allows you to define a new class that incorporates and extends an already declared class.</p>
<p>inheritance is the aspect of OOP that facilitates code reuse. Specifically
speaking, code reuse comes in two flavors: inheritance (the “is-a” relationship) and the
containment/delegation model (the “has-a” relationship). Let’s begin this chapter by examining the
classical inheritance model of the “is-a” relationship.
When you establish “is-a” relationships between classes, you are building a dependency between
two or more class types.</p>

• You can use an existing class, called the base class, as the basis for a new class,
called the derived class. The members of the derived class consist of the following:
− The members in its own declaration
− The members of the base class
<p> To declare a derived class, you add a class-base specification after the class name.
The class-base specification consists of a colon, followed by the name of the class
to be used as the base class.</p>
<p>A derived class is said to extend its base class, because it includes the members of
the base class plus any additional functionality provided in its own declaration.<p>

<p>Inherited members are accessed just as if they had been declared in the derived class itself.</p>
         
* All Classes Are Derived from Class object

All classes, except the special class object, are derived classes, even if they don’t have a class-base
specification. Class object is the only class that is not derived, since it is the base of the inheritance
hierarchy.
Classes without a class-base specification are implicitly derived directly from class object.
* Other important facts about class derivation are the following
  * A class declaration can have only a single class listed in its class-base specification.
    This is called single inheritance.
  * Although a class can directly inherit from only a single base class, there is no limit
  to the level of derivation. That is, the class listed as the base class might be derived
from another class, which is derived from another class, and so forth, until you
eventually reach object.
  * Inheritance preserves encapsulation. private members can only be accessed by the class that defines them.

* Masking Members of a Base Class
<p>A derived class cannot delete any of the members it has inherited; it can, however, mask a base class
member with a member of the same name. This is extremely useful, and one of the major features of
inheritance.
For example, you might want to inherit from a base class that has a particular method. That method,
although perfect for the class in which it is declared, may not do exactly what you want in the derived
class. In such a case, what you want to do is to mask the base class method with a new member declared
in the derived class. Some important aspects of masking a base class member in a derived class are the
following:</p>
To mask an inherited data member, declare a new member of the same type and
with the same name.
   * To mask an inherited function member, declare a new function member with the
same signature. Remember that the signature consists of the name and parameter
list, but does not include the return type.
   * To let the compiler know that you’re purposely masking an inherited member, use
the new modifier. Without it, the program will compile successfully, but the
compiler will warn you that you’re hiding an inherited member.
   * You can also mask static members.
   <p>In the following code, OtherClass derives from SomeClass but hides both its inherited members.</p>
   
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp2
{
    class SomeClass // Base class
    {
        public string Field1 = "SomeClass Field1";
        public void Method1(string value)
        { Console.WriteLine("SomeClass.Method1: {0}", value); }
    }
    class OtherClass : SomeClass // Derived class
    {
    

new public string Field1 = "OtherClass Field1"; // Mask the base member.
        new public void Method1(string value) // Mask the base member.
 { Console.WriteLine("OtherClass.Method1: {0}", value); }
}

class Program
{
    static void Main()
    {
        OtherClass oc = new OtherClass(); // Use the masking member.
        oc.Method1(oc.Field1); // Use the masking member.
    }
}
}
```
<p>This code produces the following output:</p>
OtherClass.Method1: OtherClass Field1

* Base Access
If your derived class absolutely must access a hidden inherited member, you can access it by using a
base access expression. This expression consists of the keyword base, followed immediately by a period
and the name of the member, as shown here:
```csharp
Console.WriteLine("{0}", base.Field1);
```
* Using References to a Base Class
An instance of a derived class consists of an instance of the base class plus the additional members of the
derived class. A reference to the derived class points to the whole class object, including the base class
part.
If you have a reference to a derived class object, you can get a reference to just the base class part of
the object by casting the reference to the type of the base class by using the cast operator.
The next few sections cover accessing an object by using a reference to the base class part of the
object. We’ll start by looking at the two lines of code that follow, which declare references to objects.
```csharp
class MyBaseClass
{
  public void Print()
  {
    Console.WriteLine("This is the base class.");
  }
}
 class MyDerivedClass : MyBaseClass
 {
   new public void Print()
 {
   Console.WriteLine("This is the derived class.");
 }
}
class Program
{
  static void Main()
  {
    MyDerivedClass derived = new MyDerivedClass();
    MyBaseClass mybc = (MyBaseClass)derived;
    //Cast to base class
  derived.Print(); // Call Print from derived portion.
  mybc.Print(); // Call Print from base portion.
  }
}
```
<p>This code produces the following output:</p>
<p>This is the derived class.</p>
<p>This is the base class.</p>

### Virtual and Override Methods

Virtual methods allow a reference to the
base class to access “up into” the derived class.
You can use a reference to a base class to call a method in the derived class if the following are true:
* The method in the derived class and the method in the base class each have the
same signature and return type.
* The method in the base class is labeled virtual.
* The method in the derived class is labeled override.
* ##### `virtual or abstract members cannot be private`

For example, the following code shows the virtual and override modifiers on the methods in the
base class and derived class:
```csharp
class MyBaseClass
{
  virtual public void Print()
}

 class MyDerivedClass : MyBaseClass
{
 override public void Print()
}
```
When the Print method is called by using the reference to the base class (mybc),
the method call is passed up to the derived class and executed, because
* The method in the base class is marked as virtual.
* There is a matching override method in the derived class.

The following code is the same as in the previous section, but this time, the methods are labeled
virtual and override. This produces a result that is very different from that of the previous example. In
this version, calling the method through the base class invokes the method in the derived class.
```charp
class MyBaseClass
{
virtual public void Print()
{
Console.WriteLine("This is the base class.");
}
}
class MyDerivedClass : MyBaseClass
{
override public void Print()
{
Console.WriteLine("This is the derived class.");
}
}
class Program
{
static void Main()
{
MyDerivedClass derived = new MyDerivedClass();
MyBaseClass mybc = (MyBaseClass)derived;
↑
derived.Print(); Cast to base class
mybc.Print();
}
}
```
<p>This code produces the following output:</p>
<p>This is the derived class.</p>
<p>This is the derived class.</p>

Other important things to know about the virtual and override modifiers are the following:
* The overriding and overridden methods must have the same accessibility. In other
words, the overridden method cannot be, for example, private, and the overriding
method public.
* You cannot override a method that is static or is not declared as virtual.
* Methods, properties, and indexers (which I covered in the preceding chapter), and
another member type, called an event, can all be declared virtual and override.

* When you use a reference to the base class part of an object to call an overridden
method, the method call is passed up the derivation hierarchy for execution to the
most-derived version of the method marked as override.
* If there are other declarations of the method at higher levels of derivation that are
not marked as override, they are not invoked.

For example, the following code shows three classes that form an inheritance hierarchy:
MyBaseClass, MyDerivedClass, and SecondDerived. All three classes contain a method named Print, with
the same signature. In MyBaseClass, Print is labeled virtual. In MyDerivedClass, it’s labeled override. In
class SecondDerived, you can declare method Print with either override or new
```csharp
class MyBaseClass // Base class
{
virtual public void Print()
{ Console.WriteLine("This is the base class."); }
}
class MyDerivedClass : MyBaseClass // Derived class
{
override public void Print()
{ Console.WriteLine("This is the derived class."); }
}
class SecondDerived : MyDerivedClass // Most-derived class
{
... // Given in the following pages
}
```
If you declare the Print method of SecondDerived as override, then it will override both the less-derived
versions of the method, as shown in Figure 7-9. If a reference to the base class is used to call Print, it gets
passed all the way up the chain to the implementation in class SecondDerived.

The following code implements this case. Notice the code in the last two lines of method Main.
* The first of the two statements calls the Print method by using a reference to the
most-derived class—SecondDerived. This is not calling through a reference to the
base class portion, so it will call the method implemented in SecondDerived.
* The second statement, however, calls the Print method by using a reference to the
base class—MyBaseClass.

```csharp
class SecondDerived : MyDerivedClass
{
 override public void Print() {
 Console.WriteLine("This is the second derived class.");
}
}
class Program
{
 static void Main()
 {
  SecondDerived derived = new SecondDerived(); // Use SecondDerived.
  MyBaseClass mybc = (MyBaseClass)derived; // Use MyBaseClass.
  derived.Print();
  mybc.Print();
 }
}
```
The result is that regardless of whether Print is called through the derived class or the base class, the
method in the most-derived class is called. When called through the base class, it’s passed up the
inheritance hierarchy. This code produces the following output:

This is the second derived class.
This is the second derived class.

If instead you declare the Print method of SecondDerived as new, the result is as shown in Figure 7-10.
Main is the same as in the previous case.

```csharp
class SecondDerived : MyDerivedClass
{
 new public void Print()
 {
 Console.WriteLine("This is the second derived class.");
 }
}
class Program
{
 static void Main() // Main
 {
 SecondDerived derived = new SecondDerived(); // Use SecondDerived.
 MyBaseClass mybc = (MyBaseClass)derived; // Use MyBaseClass.
 derived.Print();
 mybc.Print();
 }
}
```
The result is that when method Print is called through the reference to SecondDerived, the method
in SecondDerived is executed, as you would expect. When the method is called through a reference to
MyBaseClass, however, the method call is passed up only one level, to class MyDerived, where it is
executed. The only difference between the two cases is whether the method in SecondDerived is declared
with modifier override or modifier new.
This code produces the following output:
This is the second derived class.
This is the derived class.

### Overriding Other Member Types

In the previous few sections, you’ve seen how the virtual/override designations work on methods.
These work exactly the same way with properties, events, and indexers. For example, the following code
shows a read-only property named MyProperty using virtual/override.

```csharp
class MyBaseClass
{
 private int _myInt = 5;
 virtual public int MyProperty
 {
  get { return _myInt; }
 }
}
 class MyDerivedClass : MyBaseClass
 {
 private int _myInt = 10;
 override public int MyProperty
 {
 get { return _myInt; }
 }
 }
class Program
 {
 static void Main()
 {
 MyDerivedClass derived = new MyDerivedClass();
 MyBaseClass mybc = (MyBaseClass)derived;
 Console.WriteLine( derived.MyProperty );
 Console.WriteLine( mybc.MyProperty );
 }
}
```
This code produces the following output:
10
10

### Another Example using virtual Methods 
```csharp
public class Groceries
    {
        public List<string> ItemList = new List<string>();
        public virtual void CreateList()
        {
            ItemList.Add("Items");
            ItemList.Add("---------");
            ItemList.Add("Item1");
            ItemList.Add("Item2");
            ItemList.Add("Item3");
        }
    }


    public class Fruits : Groceries
    {
        public override void CreateList()
        {
            ItemList.Add("Fruits");
            ItemList.Add("---------");
            ItemList.Add("Apple");
            ItemList.Add("Orange");
            ItemList.Add("Lemon");
        }
    }

    public class SumerFruits : Fruits
    {
      new  public  void CreateList()
        {
            ItemList.Add("SumerFruits");
            ItemList.Add("---------");
            ItemList.Add("Watermelon");
            ItemList.Add("Peach");
            ItemList.Add("Melon");
        }
    }



    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private void DisplayGroceries(Groceries G)
        {
            G.CreateList();
            l1.ItemsSource = G.ItemList;

        }

        private void Window_Loaded(object sender, RoutedEventArgs e)
        {
            //Groceries Gr = new Groceries();
            SumerFruits Gr = new SumerFruits();
            DisplayGroceries(Gr);
        }
    }
}
```
The class thats create the list is - Fruits class

### Constructor Execution

Constructor executes code that prepares a class for use.This
includes initializing both the static and instance members of the class.
* To create the base class part of an object, a constructor for the base class is
implicitly called as part of the process of creating the instance.
* Each class in the inheritance hierarchy chain executes its base class constructor
before it executes its own constructor body.
For example, the following code shows a declaration of class MyDerivedClass and its constructor.
When the constructor is called, it calls the parameterless constructor MyBaseClass() before executing its
own body.
```csharp
class MyDerivedClass : MyBaseClass
{
MyDerivedClass() // Constructor uses base constructor MyBaseClass()
    {
    ...
    }
}
```
When an instance is being created, one of the first
things that’s done is the initialization of all the instance members of the object. After that, the base class
constructor is called. Only then is the body of the constructor of the class itself executed.

For example, in the following code, the values of MyField1 and MyField2 would be set to 5 and 0,
respectively, before the base class constructor is called.
```csharp
class MyDerivedClass : MyBaseClass
{
int MyField1 = 5; // 1. Member initialized
int MyField2; // Member initialized
public MyDerivedClass() // 3. Body of constructor executed
{
...
}
}
class MyBaseClass
{
public MyBaseClass() // 2. Base class constructor called
{
...
}
}
```
### Constructor Initializers

By default, the parameterless constructor of the base class is called when an object is being constructed.
But constructors can be overloaded, so a base class might have more than one. If you want your derived
class to use a specific base class constructor other than the parameterless constructor, you must specify
it in a constructor initializer.
There are two forms of constructor initializers:
* The first form uses the keyword base and specifies which base class constructor to
use.
* The second form uses the keyword this and specifies which other constructor
from this class should be used.

A base class constructor initializer is placed after a colon following the parameter list in a class’s
constructor declaration. The constructor initializer consists of the keyword base and the parameter list
of the base constructor to call.
For example, the following code shows a constructor for class MyDerivedClass.
* The constructor initializer specifies that the construction process should call the
base class constructor with two parameters, where the first parameter is a string
and the second parameter is an int.
* The parameters in the base parameter list must match the intended base
constructor’s parameter list in type and order.
```csharp
public MyDerivedClass( int x, string s ) : base( s, x )
{ 
}
```
When you declare a constructor without a constructor initializer, it’s a shortcut for the form with
a constructor initializer consisting of base(), as illustrated in Figure 7-12. The two forms are
semantically equivalent.
```csharp
public MyDerived : MyBase
{ 
    //constructor implicitly using base constructor MyBase ()
    MyDefivedClass
    {

    }
}


public MyDerived : MyBase
{ 
    //constructor Explicitly using base constructor MyBase ()
    MyDefivedClass :base()
    {

    }
}
```
The other form of constructor initializer instructs the construction process (actually, the compiler)
to use a different constructor from the same class. For example, the following shows a constructor with a
single parameter for class MyClass. That single-parameter constructor, however, uses a constructor from
the same class, but with two parameters, supplying a default parameter as the second one.
```csharp
public MyClass(int x): this(x, "Using Default String")
{ ↑
... Keyword
}
```
Another situation where this comes in particularly handy is where you have several constructors for
a class, and they have common code that should always be performed at the beginning of the object
construction process. In this case, you can factor out that common code and place it in a constructor
that is used as a constructor initializer by all the other constructors. In fact, this is a suggested practice
since it reduces code duplication.
You might think that you could just declare another method that performs those common
initializations and have all the constructors call that method. This isn’t as good for several reasons. The
first is that the compiler can optimize certain things when it knows a method is a constructor. The
second is that there are some things that can be done only in a constructor and not elsewhere. For
example, in the previous chapter you learned that readonly fields can be initialized only inside a
constructor. You will get a compiler error if you attempt to initialize a readonly field in any other
method, even if that method is called by a constructor only.

initializes everything in the class that needs to be initialized, then it’s perfectly fine to leave it as a
public constructor.
What if, however, it doesn’t completely initialize an object? In that case, you mustn’t allow that
constructor to be callable from outside the class, since it would then create incompletely initialized
objects. To avoid that problem, you can declare the constructor private instead of public, and only have
it be used by the other constructors. The following code illustrates this usage:
```csharp
class MyClass
{
readonly int firstVar;
readonly double secondVar;
public string UserName;
public int UserIdNumber;
private MyClass( ) // Private constructor performs initializations
{ // common to the other constructors
firstVar = 20;
secondVar = 30.5;
}
public MyClass( string firstName ) : this() // Use constructor initializer
{
UserName = firstName;
UserIdNumber = -1;
}
public MyClass( int idNumber ) : this( ) // Use constructor initializer
{
UserName = "Anonymous";
UserIdNumber = idNumber;
}
}

