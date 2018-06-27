### Type Visibility

When defining a type at file scope (versus defining a type nested within another type), you can specify
the type’s visibility as being either public or internal. A public type is visible to all code within the
defining assembly as well as all code written in other assemblies. An internal type is visible to all
code within the defining assembly, and the type is not visible to code written in other assemblies. If
you do not explicitly specify either of these when you define a type, the C# compiler sets the type’s
visibility to internal (the more restrictive of the two).

### Member Accessibility

When defining a type’s member (which includes nested types), you can specify the member’s
accessibility. A member’s accessibility indicates which members can be legally accessed from referent
code. The CLR defines the set of possible accessibility modifiers, but each programming language
chooses the syntax and term it wants developers to use when applying the accessibility to a member.
For example, the CLR uses the term Assembly to indicate that a member is accessible to any code
within the same assembly, whereas the C# term for this is internal.

C# Term | Description 
--- | --- 
private |The member is accessible only by methods in the defining type or any nested type.
protected|The member is accessible only by methods in the defining type,any nested type, or one of its derived types, without regard to assembly.
internal |The member is accessible only by methods in the defining type, any nested type, or by any derived types defined in the same assembly.
protected internal| The member is accessible by any nested type, any derived type (regardless of assembly), or any methods in the defining assembly.
public|The member is accessible to all methods in any assembly.

### Access Modifiers (C# Programming Guide)
**public**
The type or member can be accessed by any other code in the same assembly or another assembly that references it.

**private**
The type or member can be accessed only by code in the same class or struct.

**protected**
The type or member can be accessed only by code in the same class, or in a class that is derived from that class.

**internal**
The type or member can be accessed by any code in the same assembly, but not from another assembly.

**protected internal**
The type or member can be accessed by any code in the assembly in which it is declared, or from within a derived class in another assembly.

**private protected**
The type or member can be accessed only within its declaring assembly, by code in the same class or in a type that is derived from that class.

Of course, for any member to be accessible, it must be defined in a type that is visible. For example,
if AssemblyA defines an internal type with a public method, code in AssemblyB cannot call the
public method because the internal type is not visible to AssemblyB.

In C#, if you do not explicitly declare a member’s accessibility, the compiler usually (but not always)
defaults to selecting private (the most restrictive of them all). The CLR requires that all members of
an interface type be public. The C# compiler knows this and forbids the programmer from explicitly
specifying accessibility on interface members; the compiler just makes all the members public for you.

### Static Classes

There are certain classes that are never intended to be instantiated, such as Console, Math,
Environment, and ThreadPool. These classes have only static members and, in fact, the classes
exist simply as a way to group a set of related members together. For example, the Math class defines a
bunch of methods that do math-related operations. C# allows you to define non-instantiable classes by
using the C# static keyword. This keyword can be applied only to classes, not structures (value types)
because the CLR always allows value types to be instantiated and there is no way to stop or prevent
this.
The compiler enforces many restrictions on a static class:
* The class must be derived directly from System.Object because deriving from any other base
class makes no sense since inheritance applies only to objects, and you cannot create an
instance of a static class.
* The class must not implement any interfaces since interface methods are callable only when
using an instance of a class.
* The class must define only static members (fields, methods, properties, and events). Any
instance members cause the compiler to generate an error.
* The class cannot be used as a field, method parameter, or local variable because all of these
would indicate a variable that refers to an instance, and this is not allowed. If the compiler 
detects any of these uses, the compiler issues an error.

### static constructor
In addition to instance constructors, the CLR also supports type constructors (also known as static
constructors, class constructors, or type initializers). A type constructor can be applied to interfaces
(although C# doesn’t allow this), reference types, and value types. Just as instance constructors are
used to set the initial state of an instance of a type, type constructors are used to set the initial state of
a type. By default, types don’t have a type constructor defined within them. If a type has a type
constructor, it can have no more than one. In addition, type constructors never have parameters. In C#,
here’s how to define a reference type and a value type that have type constructors:
```csharp
internal sealed class SomeRefType {
static SomeRefType() {
// This executes the first time a SomeRefType is accessed.
}
}
internal struct SomeValType {
// C# does allow value types to define parameterless type constructors.
static SomeValType() {
// This executes the first time a SomeValType is accessed.
}
}
```
You’ll notice that you define type constructors just as you would parameterless instance
constructors, except that you must mark them as static. Also, type constructors should always be
private; C# makes them private for you automatically. In fact, if you explicitly mark a type constructor
as private (or anything else) in your source code, the C# compiler issues the following error: "error
CS0515: 'SomeValType.SomeValType()': access modifiers are not allowed on static
constructors." Type constructors should be private to prevent any developer-written code from
calling them; the CLR is always capable of calling a type constructor.
### readonly fields

The CLR supports readonly fields and read/write fields. Most fields are read/write fields,
meaning the field’s value might change multiple times as the code executes. However, readonly fields
can be written to only within a constructor method (which is called only once, when an object is first
created). Compilers and verification ensure that readonly fields are not written to by any method
other than a constructor. Note that reflection can be used to modify a readonly field.

**Important** When a field is of a reference type and the field is marked as readonly, it is the
reference that is immutable, not the object that the field refers to. The following code demonstrates:

```csharp
public sealed class AType {
// InvalidChars must always refer to the same array object
public static readonly Char[] InvalidChars = new Char[] { 'A', 'B', 'C' };
}
public sealed class AnotherType {
public static void M() {
// The lines below are legal, compile, and successfully
// change the characters in the InvalidChars array
AType.InvalidChars[0] = 'X';
AType.InvalidChars[1] = 'Y';
AType.InvalidChars[2] = 'Z';
// The line below is illegal and will not compile because
// what InvalidChars refers to cannot be changed
AType.InvalidChars = new Char[] { 'X', 'Y', 'Z' };
}
}
```
### Instance Constructors and Structures (Value Types)

Value type (struct) constructors work quite differently from reference type (class) constructors. The
common language runtime (CLR) always allows the creation of value type instances, and there is no
way to prevent a value type from being instantiated. For this reason, value types don’t actually even
need to have a constructor defined within them, and the C# compiler doesn't emit default
parameterless constructors for value types. Examine the following code:
```csharp
internal struct Point {
public Int32 m_x, m_y;
}
internal sealed class Rectangle {
public Point m_topLeft, m_bottomRight;
}
```
To construct a Rectangle, the new operator must be used, and a constructor must be specified. In
this case, the default constructor automatically generated by the C# compiler is called. When memory
is allocated for the Rectangle, the memory includes the two instances of the Point value type. For
performance reasons, the CLR doesn’t attempt to call a constructor for each value type field contained
within the reference type. But as I mentioned earlier, the fields of the value types are initialized to
0/null.
The CLR does allow you to define constructors on value types. The only way that these constructors
will execute is if you write code to explicitly call one of them, as in Rectangle’s constructor, shown
here:
```csharp
internal struct Point {
public Int32 m_x, m_y;
public Point(Int32 x, Int32 y) {
m_x = x;
m_y = y;
}
}
internal sealed class Rectangle {
public Point m_topLeft, m_bottomRight;
public Rectangle() {
// In C#, new on a value type calls the constructor to
// initialize the value type's fields.
m_topLeft = new Point(1, 2);
m_bottomRight = new Point(100, 200);
}
}
```
A value type’s instance constructor is executed only when explicitly called. So if Rectangle’s
constructor didn’t initialize its m_topLeft and m_bottomRight fields by using the new operator to call
Point’s constructor, the m_x and m_y fields in both Point fields would be 0.
In the Point value type defined earlier, no default parameterless constructor is defined. However,
let’s rewrite that code as follows:
```csharp
internal struct Point {
public Int32 m_x, m_y;
public Point() {
m_x = m_y = 5;
}
}
internal sealed class Rectangle {
public Point m_topLeft, m_bottomRight;
public Rectangle() {
}
}
```
Now when a new Rectangle is constructed, what do you think the m_x and m_y fields in the two
Point fields, m_topLeft and m_bottomRight, would be initialized to: 0 or 5? (Hint: This is a trick
question.)
Many developers (especially those with a C++ background) would expect the C# compiler to emit
code in Rectangle’s constructor that automatically calls Point’s default parameterless constructor for
the Rectangle’s two fields. However, to improve the runtime performance of the application, the C#
compiler doesn’t automatically emit this code. In fact, many compilers will never emit code to call a
value type’s default constructor automatically, even if the value type offers a parameterless constructor.
To have a value type’s parameterless constructor execute, the developer must add explicit code to call
a value type’s constructor.
Based on the information in the preceding paragraph, you should expect the m_x and m_y fields in
Rectangle’s two Point fields to be initialized to 0 in the code shown earlier because there are no
explicit calls to Point’s constructor anywhere in the code.
The trick part is that C# doesn’t allow a value type to define a parameterless constructor. So the previous code won’t actually compile.
The C# compiler produces the following message when attempting to compile that code: "error
CS0568: Structs cannot contain explicit parameterless constructors."
C# purposely disallows value types from defining parameterless constructors to remove any
confusion a developer might have about when that constructor gets called. If the constructor can’t be
defined, the compiler can never generate code to call it automatically. Without a parameterless
constructor, a value type’s fields are always initialized to 0/null.
**Note** Strictly speaking, value type fields are guaranteed to be 0/null when the value type is a field
nested within a reference type. However, stack-based value type fields are not guaranteed to be
0/null. For verifiability, any stack-based value type field must be written to prior to being read. If
code could read a value type’s field prior to writing to the field, a security breach is possible. C# and
other compilers that produce verifiable code ensure that all stack-based value types have their fields
zeroed out or at least written to before being read so that a verification exception won’t be thrown at
run time. For the most part, this means that you can assume that your value types have their fields
initialized to 0, and you can completely ignore everything in this note.
Keep in mind that although C# doesn’t allow value types with parameterless constructors, the CLR
does.
Because C# doesn’t allow value types with parameterless constructors, compiling the following type
produces the following message: "error CS0573: 'SomeValType.m_x': cannot have instance
field initializers in structs."
```csharp
internal struct SomeValType {
// You cannot do inline instance field initialization in a value type
private Int32 m_x = 5;
}
```
In addition, because verifiable code requires that every field of a value type be written to prior to
any field being read, any constructors that you do have for a value type must initialize all of the type’s
fields. The following type defines a constructor for the value type but fails to initialize all of the fields:
```csharp
internal struct SomeValType {
private Int32 m_x, m_y;
// C# allows value types to have constructors that take parameters.
public SomeValType(Int32 x) {
m_x = x;
// Notice that m_y is not initialized here.
}
}
```
### Anonymous Types
Anonymous types provide a convenient way to encapsulate a set of read-only properties into a single object without having to explicitly define a type first. The type name is generated by the compiler and is not available at the source code level. The type of each property is inferred by the compiler.

You create anonymous types by using the new operator together with an object initializer.
```csharp
var v = new { Amount = 108, Message = "Hello" };  

// Rest the mouse pointer over v.Amount and v.Message in the following  
// statement to verify that their inferred types are int and string.  
Console.WriteLine(v.Amount + v.Message);
```
<p>Anonymous types typically are used in the select clause of a query expression to return a subset of the properties from each object in the source sequence.</p>

<p>Anonymous types contain one or more public read-only properties. No other kinds of class members, such as methods or events, are valid. The expression that is used to initialize a property cannot be null, an anonymous function, or a pointer type.
The most common scenario is to initialize an anonymous type with properties from another type. In the following example, assume that a class exists that is named Product. Class Product includes Color and Price properties, together with other properties that you are not interested in. Variable products is a collection of Product objects. The anonymous type declaration starts with the new keyword. The declaration initializes a new type that uses only two properties from Product. This causes a smaller amount of data to be returned in the query.</p>
<p>If you do not specify member names in the anonymous type, the compiler gives the anonymous type members the same name as the property being used to initialize them. You must provide a name for a property that is being initialized with an expression, as shown in the previous example. In the following example, the names of the properties of the anonymous type are Color and Price.</p>
<p>ypically, when you use an anonymous type to initialize a variable, you declare the variable as an implicitly typed local variable by using var. The type name cannot be specified in the variable declaration because only the compiler has access to the underlying name of the anonymous type. </p>

### Remarks (Anonymous Types)
Anonymous types are class types that derive directly from object, and that cannot be cast to any type except object. The compiler provides a name for each anonymous type, although your application cannot access it. From the perspective of the common language runtime, an anonymous type is no different from any other reference type.

If two or more anonymous object initializers in an assembly specify a sequence of properties that are in the same order and that have the same names and types, the compiler treats the objects as instances of the same type. They share the same compiler-generated type information.

You cannot declare a field, a property, an event, or the return type of a method as having an anonymous type. Similarly, you cannot declare a formal parameter of a method, property, constructor, or indexer as having an anonymous type. To pass an anonymous type, or a collection that contains anonymous types, as an argument to a method, you can declare the parameter as type object. However, doing this defeats the purpose of strong typing. If you must store query results or pass them outside the method boundary, consider using an ordinary named struct or class instead of an anonymous type.

Because the Equals and GetHashCode methods on anonymous types are defined in terms of the Equals and GetHashCode methods of the properties, two instances of the same anonymous type are equal only if all their properties are equal.

### var (C# Reference)

Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" var. An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type. The following two declarations of i are functionally equivalent:
```csharp
var i = 10; // Implicitly typed. 
int i = 10; // Explicitly typed. 
```
### Example
The following example shows two query expressions. In the first expression, the use of var is permitted but is not required, because the type of the query result can be stated explicitly as an IEnumerable<string>. However, in the second expression, var allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself. Use of var eliminates the requirement to create a new class for the result. Note that in Example #2, the foreach iteration variable item must also be implicitly typed.
```csharp
  // Example #1: var is optional because
// the select clause specifies a string
string[] words = { "apple", "strawberry", "grape", "peach", "banana" };
var wordQuery = from word in words
                where word[0] == 'g'
                select word;

// Because each element in the sequence is a string, 
// not an anonymous type, var is optional here also.
foreach (string s in wordQuery)
{
    Console.WriteLine(s);
}

// Example #2: var is required when
// the select clause specifies an anonymous type
var custQuery = from cust in customers
                where cust.City == "Phoenix"
                select new { cust.Name, cust.Phone };

// var must be used because each item 
// in the sequence is an anonymous type
foreach (var item in custQuery)
{
    Console.WriteLine("Name={0}, Phone={1}", item.Name, item.Phone);
}
```
