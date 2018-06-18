### Class Inheritance

<details>
<summary>Main Info</summary>
<p>Inheritance allows you to define a new class that incorporates and extends an already declared class.</p>
• You can use an existing class, called the base class, as the basis for a new class,
called the derived class. The members of the derived class consist of the following:
− The members in its own declaration
− The members of the base class
<p> To declare a derived class, you add a class-base specification after the class name.
The class-base specification consists of a colon, followed by the name of the class
to be used as the base class. The derived class is said to directly inherit from the
base class listed.</p>
<p>A derived class is said to extend its base class, because it includes the members of
the base class plus any additional functionality provided in its own declaration.<p>

<p>Inherited members are accessed just as if they had been declared in the derived class itself.</p>
 </details>
         
* All Classes Are Derived from Class object

All classes, except the special class object, are derived classes, even if they don’t have a class-base
specification. Class object is the only class that is not derived, since it is the base of the inheritance
hierarchy.
Classes without a class-base specification are implicitly derived directly from class object. Leaving
off the class-base specification is just shorthand for specifying that object is the base class. The two
forms are semantically equivalent.

* Other important facts about class derivation are the following
  * A class declaration can have only a single class listed in its class-base specification.
    This is called single inheritance.
  * Although a class can directly inherit from only a single base class, there is no limit
to the level of derivation. That is, the class listed as the base class might be derived
from another class, which is derived from another class, and so forth, until you
eventually reach object.

* Masking Members of a Base Class
<p>A derived class cannot delete any of the members it has inherited; it can, however, mask a base class
member with a member of the same name. This is extremely useful, and one of the major features of
inheritance.
For example, you might want to inherit from a base class that has a particular method. That method,
although perfect for the class in which it is declared, may not do exactly what you want in the derived
class. In such a case, what you want to do is to mask the base class method with a new member declared
in the derived class. Some important aspects of masking a base class member in a derived class are the
following:</p>
   * To mask an inherited data member, declare a new member of the same type and
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
the object by casting the reference to the type of the base class by using the cast operator. The cast
operator is placed in front of the object reference and consists of a set of parentheses containing the
name of the class being cast to. 
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
//↑
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
* `virtual or abstract members cannot be private`

For example, the following code shows the virtual and override modifiers on the methods in the
base class and derived class:
```charp
class MyBaseClass // Base class
{
virtual public void Print()
↑
...
class MyDerivedClass : MyBaseClass // Derived class
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
another member type, called an event, can all be
declared virtual and override.



