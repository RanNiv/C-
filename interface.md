
# Interface

An interface defines a contract. Any class or struct that implements that contract must provide an implementation of the members defined in the interface. Beginning with C# 8.0, an interface may define a default implementation for members. It may also define static members in order to provide a single implementation for common functionality.

```csharp
public interface ITranslate
{
     string? EnglishTerm { get; set; }
     string? HebrewTranslate { get; set; }
     void SetTranslate();
}

public class Vocabulary : ITranslate
{

    public string? EnglishTerm { get; set; }
    public string? HebrewTranslate { get; set; }
    public void SetTranslate() 
    {
      switch(EnglishTerm){
      case "shrugged":
      this.HebrewTranslate="משך בכתפיו";
      break;
      case "ambient":
      this.HebrewTranslate="מקיף סובב אופף";
      break;
      default:
      this.HebrewTranslate="Unknown";
      break;
      }

    }
} 
```


* Interface members are always implicitly **public** and cannot declare an access modifier.
* Implementing an interface means providing a public implementation for all its members
* If a class is derived from a base class and also implements interfaces, the name of
  the base class must be listed in the base class list before any interfaces


An interface declaration can contain declarations (signatures without any implementation) of the following members:
* Methods
* Properties
* Indexers
* Events



## Extending an Interface
Interfaces may derive from other interfaces. For instance:
public interface IUndoable { void Undo(); }
public interface IRedoable : IUndoable { void Redo(); }
IRedoable “inherits” all the members of IUndoable. In other words, types that
implement IRedoable must also implement the members of IUndoable.



When a class or struct implements an interface, the class or struct must provide an implementation for all of the members that the interface declares but doesn't provide a default implementation for. However, if a base class implements an interface, any class that's derived from the base class inherits that implementation.

## Implementing Interface Members Virtually

An implicitly implemented interface member is, by default, sealed. It must be
marked virtual or abstract in the base class in order to be overridden. For
example:

```csharp
public interface IUndoable { void Undo(); }
public class TextBox : IUndoable
{
  public virtual void Undo() => Console.WriteLine ("TextBox.Undo");
}
public class RichTextBox : TextBox
{
  public override void Undo() => Console.WriteLine ("RichTextBox.Undo");
}
```

Calling the interface member through either the base class or the interface calls the
subclass’s implementation:

```csharp
RichTextBox r = new RichTextBox();
r.Undo(); // RichTextBox.Undo
((IUndoable)r).Undo(); // RichTextBox.Undo
((TextBox)r).Undo(); // RichTextBox.Undo
```


In the following example we get a warning message:
'VocabularyInfo.SetTranslate()' hides inherited member 'Vocabulary.SetTranslate()'. Use the new keyword if hiding was intended.

```csharp
public class VocabularyInfo : Vocabulary 
{

    public string EnglishTranslate { get; set; }

    public void SetTranslate () 
    { 
      this.EnglishTranslate="Unknown";
    }


}
```

## Explicit Interface Implementation

Implementing multiple interfaces can sometimes result in a collision between member
signatures. You can resolve such collisions by explicitly implementing an interface
member. Consider the following example:

```csharp
interface I1 { void Foo(); }
interface I2 { int Foo(); }
public class Widget : I1, I2
{
public void Foo()
{
  Console.WriteLine ("Widget's implementation of I1.Foo");
}
int I2.Foo()
{
  Console.WriteLine ("Widget's implementation of I2.Foo");
  return 42;
}
}
```

