
# if-else 
An `if` statement identifies which statement to run based on the value of a `Boolean` expression. In the following example, the `Boolean` variable `result` is set to `true` and then checked in the `if` statement. The output is `The condition is true`.  

An `if` statement example: 
```csharp 
// if statement without an else  
if (condition)  
{  
    then-statement;  
}  
// Next statement in the program.  
```  
  
An `if-else` statement example:
  
```csharp  
// if-else statement  
if (condition)  
{  
    then-statement;  
}  
else  
{  
    else-statement;  
}  
// Next statement in the program.
```  

 In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs. 
 If `condition` is false, the `else-statement` runs. 
 Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run. 
 After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.  
  
 In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs. If `condition` is false, control is transferred to the next statement after the `if` statement.  
  
 Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`). 
 For a single statement, the braces are optional but recommended.  



 # logical operators
  
  
```csharp  
// NOT  
bool result = true;  
if (!result)  
{  
    Console.WriteLine("The condition is true (result is false).");  
}  
else  
{  
    Console.WriteLine("The condition is false (result is true).");  
}  
  
// AND  
int m = 9;  
int n = 7;  
int p = 5;  
if (m >= n && m >= p)  
{  
    Console.WriteLine("Nothing is larger than m.");  
}  
  
// AND and NOT  
if (m >= n && !(p > m))  
{  
    Console.WriteLine("Nothing is larger than m.");  
}  
  

// NOT and OR  
m = 4;  
if (!(m >= n || m >= p))  
{  
    Console.WriteLine("Now m is the smallest.");  
}  
// Output:  
// The condition is false (result is true).  
// Nothing is larger than m.  
// Nothing is larger than m.  
// Now m is the smallest.  
```  
 
 
 
---

# switch
`switch` is a selection statement that chooses a single *switch section* 
to execute from a list of candidates based on a pattern match with the *match expression*. 
  

The `switch` statement is often used as an alternative to an `if-else` construct if a single expression is 
tested against three or more conditions. 

 
## The switch section
 

 Only one switch section in a switch statement executes. 
 C# does not allow execution to continue from one switch section to the next. 
 Because of this, the following code generates a compiler error, 
 CS0163: "Control cannot fall through from one case label (<case label>) to another."  

```csharp  
switch (caseSwitch)  
{  
    // The following switch section causes an error.  
    case 1:  
        Console.WriteLine("Case 1...");  
        // Add a break or other jump statement here.  
    case 2:  
        Console.WriteLine("... and/or Case 2");  
        break;  
}  
```  
This requirement is usually met by explicitly exiting the switch section by using a `break`  or `return` statement. 
However, the following code is also valid, because it ensures that program control cannot fall through to the `default` switch section.


 
## The `default` case

The `default` case specifies the switch section to execute if the match expression does not match any other `case` label. If a `default` case is not present and the match expression does not match any other `case` label, program flow falls through the `switch` statement.

The `default` case can appear in any order in the `switch` statement. Regardless of its order in the source code, it is always evaluated last, after all `case` labels have been evaluated.


---
# Single-Dimensional Arrays (C# Programming Guide)
You can declare a single-dimensional array of five integers as shown in the following example:  
  
```csharp  
 int[] array = new int[5];
 ```
  
 This array contains the elements from `array[0]` to `array[4]`. The `new` operator is used to create the array and initialize the array elements to their default values. In this example, all the array elements are initialized to zero.  
  
 An array that stores string elements can be declared in the same way. For example:  
```csharp  
string[] stringArray = new string[6];
 ```
  
## Array Initialization  
 It is possible to initialize an array upon declaration, in which case, the rank specifier is not needed because it is already supplied by the number of elements in the initialization list. For example:  

```csharp 
int[] array1 = new int[] { 1, 3, 5, 7, 9 };
``` 

 A string array can be initialized in the same way. The following is a declaration of a string array where each array element is initialized by a name of a day:  
  ```csharp 
string[] weekDays = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
  ``` 
 When you initialize an array upon declaration, you can use the following shortcuts:  
    ```csharp 
int[] array2 = { 1, 3, 5, 7, 9 };
string[] weekDays2 = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
    ``` 
 It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable. For example: 
 
```csharp  
int[] array3;
array3 = new int[] { 1, 3, 5, 7, 9 };   // OK
//array3 = {1, 3, 5, 7, 9};   // Error
```
  

---
# Multidimensional Arrays 
Arrays can have more than one dimension. For example, the following declaration creates a two-dimensional array of four rows and two columns.  
 ```csharp 
 int[,] array = new int[4, 2];
  ```
 The following declaration creates an array of three dimensions, 4, 2, and 3.  
   ```csharp 
  int[, ,] array1 = new int[4, 2, 3];
   ```
    
## Array Initialization  
 You can initialize the array upon declaration, as is shown in the following example.  
  ```csharp
  // Two-dimensional array.
        int[,] array2D = new int[,] { { 1, 2 }, { 3, 4 }, { 5, 6 }, { 7, 8 } };
        // The same array with dimensions specified.
        int[,] array2Da = new int[4, 2] { { 1, 2 }, { 3, 4 }, { 5, 6 }, { 7, 8 } };
        // A similar array with string elements.
        string[,] array2Db = new string[3, 2] { { "one", "two" }, { "three", "four" },
                                                { "five", "six" } };

        // Three-dimensional array.
        int[, ,] array3D = new int[,,] { { { 1, 2, 3 }, { 4, 5, 6 } }, 
                                         { { 7, 8, 9 }, { 10, 11, 12 } } };
        // The same array with dimensions specified.
        int[, ,] array3Da = new int[2, 2, 3] { { { 1, 2, 3 }, { 4, 5, 6 } }, 
                                               { { 7, 8, 9 }, { 10, 11, 12 } } };

        // Accessing array elements.
        System.Console.WriteLine(array2D[0, 0]);
        System.Console.WriteLine(array2D[0, 1]);
        System.Console.WriteLine(array2D[1, 0]);
        System.Console.WriteLine(array2D[1, 1]);
        System.Console.WriteLine(array2D[3, 0]);
        System.Console.WriteLine(array2Db[1, 0]);
        System.Console.WriteLine(array3Da[1, 0, 1]);
        System.Console.WriteLine(array3D[1, 1, 2]);

        // Getting the total count of elements or the length of a given dimension.
        var allLength = array3D.Length;
        var total = 1;
        for (int i = 0; i < array3D.Rank; i++) {
            total *= array3D.GetLength(i);
        }
        System.Console.WriteLine("{0} equals {1}", allLength, total);

        // Output:
        // 1
        // 2
        // 3
        // 4
        // 7
        // three
        // 8
        // 12
        // 12 equals 12
   ```
 You also can initialize the array without specifying the rank.  
    ```csharp
   int[,] array4 = { { 1, 2 }, { 3, 4 }, { 5, 6 }, { 7, 8 } };
    ```
 If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable. The use of `new` is shown in the following example.  
 ```csharp
int[,] array5;
array5 = new int[,] { { 1, 2 }, { 3, 4 }, { 5, 6 }, { 7, 8 } };   // OK
//array5 = {{1,2}, {3,4}, {5,6}, {7,8}};   // Error 
```
 The following example assigns a value to a particular array element.  
  ```csharp 
array5[2, 1] = 25;
```
 Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.  
  ```csharp 
 int elementValue = array5[2, 1];
  ```
 The following code example initializes the array elements to default values (except for jagged arrays).  
  ```csharp 
 int[,] array6 = new int[10, 10]; 
  ```


# Jagged Arrays 
A jagged array is an array whose elements are arrays. 
The elements of a jagged array can be of different dimensions and sizes. 
A jagged array is sometimes called an "array of arrays." The following examples show how to declare, initialize, and access jagged arrays.  
  
 The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:  
   ```csharp 
 int[][] jaggedArray = new int[3][];
   ```
 Before you can use `jaggedArray`, its elements must be initialized. You can initialize the elements like this:  
  
  ```csharp 
        jaggedArray[0] = new int[5];
        jaggedArray[1] = new int[4];
        jaggedArray[2] = new int[2];
  
```
  
 Each of the elements is a single-dimensional array of integers. The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.  
  
 It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size. For example:  
  
  ```csharp 
        jaggedArray[0] = new int[] { 1, 3, 5, 7, 9 };
        jaggedArray[1] = new int[] { 0, 2, 4, 6 };
        jaggedArray[2] = new int[] { 11, 22 };
   ``` 
  
 You can also initialize the array upon declaration like this:  
  

   ```csharp 
    int[][] jaggedArray2 = new int[][] 
    {
        new int[] {1,3,5,7,9},
        new int[] {0,2,4,6},
        new int[] {11,22}
    };
   ```
  
 You can use the following shorthand form. Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:  
  
   ```csharp 
    int[][] jaggedArray3 = 
    {
        new int[] {1,3,5,7,9},
        new int[] {0,2,4,6},
        new int[] {11,22}
    };
   ``` 
  
 A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.  
  
 You can access individual array elements like these examples:  
 ```csharp
        // Assign 77 to the second element ([1]) of the first array ([0]):
        jaggedArray3[0][1] = 77;

        // Assign 88 to the second element ([1]) of the third array ([2]):
        jaggedArray3[2][1] = 88;
  ``` 
  
 It is possible to mix jagged and multidimensional arrays. The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes. For more information about two-dimensional arrays,  
   ```csharp 
        int[][,] jaggedArray4 = new int[3][,] 
        {
            new int[,] { {1,3}, {5,7} },
            new int[,] { {0,2}, {4,6}, {8,10} },
            new int[,] { {11,22}, {99,88}, {0,9} } 
        };
   ``` 
  
 You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):  
   ```csharp 
       System.Console.Write("{0}", jaggedArray4[0][1, 0]);
   ``` 
 
  
 The method `Length` returns the number of arrays contained in the jagged array. For example, assuming you have declared the previous array, this line:  
  
   ```csharp 
        System.Console.WriteLine(jaggedArray4.Length);
   ``` 
  
 returns a value of 3.  
  
## Example  
 This example builds an array whose elements are themselves arrays. Each one of the array elements has a different size.  
  
   ```csharp 
class ArrayTest
{
    static void Main()
    {
        // Declare the array of two elements:
        int[][] arr = new int[2][];

        // Initialize the elements:
        arr[0] = new int[5] { 1, 3, 5, 7, 9 };
        arr[1] = new int[4] { 2, 4, 6, 8 };

        // Display the array elements:
        for (int i = 0; i < arr.Length; i++)
        {
            System.Console.Write("Element({0}): ", i);

            for (int j = 0; j < arr[i].Length; j++)
            {
                System.Console.Write("{0}{1}", arr[i][j], j == (arr[i].Length - 1) ? "" : " ");
            }
            System.Console.WriteLine();            
        }
        // Keep the console window open in debug mode.
        System.Console.WriteLine("Press any key to exit.");
        System.Console.ReadKey();
    }
}
/* Output:
    Element(0): 1 3 5 7 9
    Element(1): 2 4 6 8
*/
   ``` 

---
# Using foreach with Arrays
C# also provides the foreach statement. This statement provides a simple, clean way to iterate through the elements of an array or any enumerable collection. The `foreach` statement processes elements in the order returned by the array or collection type’s enumerator, which is usually from the 0th element to the last. For example, the following code creates an array called `numbers` and iterates through it with the `foreach` statement:  
 
   ```csharp 
       int[] numbers = { 4, 5, 6, 1, 2, 3, -2, -1, 0 };
        foreach (int i in numbers)
        {
            System.Console.Write("{0} ", i);
        }
        // Output: 4 5 6 1 2 3 -2 -1 0
   ```
  
 With multidimensional arrays, you can use the same method to iterate through the elements, for example:  

   ```csharp 
      int[,] numbers2D = new int[3, 2] { { 9, 99 }, { 3, 33 }, { 5, 55 } };
        // Or use the short form:
        // int[,] numbers2D = { { 9, 99 }, { 3, 33 }, { 5, 55 } };

        foreach (int i in numbers2D)
        {
            System.Console.Write("{0} ", i);
        }
        // Output: 9 99 3 33 5 55
   ```  
 However, with multidimensional arrays, using a nested for loop gives you more control over the array elements.  
  

  
  ---

# Passing Arrays as Arguments
Arrays can be passed as arguments to method parameters. Because arrays are reference types, the method can change the value of the elements.  
  
## Passing Single-Dimensional Arrays As Arguments  
 You can pass an initialized single-dimensional array to a method. For example, the following statement sends an array to a print method.  
 
   ```csharp 
        int[] theArray = { 1, 3, 5, 7, 9 };
        PrintArray(theArray);
   ``` 
   
  
 The following code shows a partial implementation of the print method.  
  
   ```csharp 
    void PrintArray(int[] arr)
    {
        // Method code.
    }
   ``` 
  
 You can initialize and pass a new array in one step, as is shown in the following example.  
  
  ```csharp 
           PrintArray(new int[] { 1, 3, 5, 7, 9 });
   ``` 
  
## Example  
  
### Description  
 In the following example, an array of strings is initialized and passed as an argument to a `PrintArray` method for strings. The method displays the elements of the array. Next, methods `ChangeArray` and `ChangeArrayElement` are called to demonstrate that sending an array argument by value does not prevent changes to the array elements.  
  
### Code  
  ```csharp 
class ArrayClass
{
    static void PrintArray(string[] arr)
    {
        for (int i = 0; i < arr.Length; i++)
        {
            System.Console.Write(arr[i] + "{0}", i < arr.Length - 1 ? " " : "");
        }
        System.Console.WriteLine();
    }

    static void ChangeArray(string[] arr)
    {
        // The following attempt to reverse the array does not persist when
        // the method returns, because arr is a value parameter.
        arr = (arr.Reverse()).ToArray();
        // The following statement displays Sat as the first element in the array.
        System.Console.WriteLine("arr[0] is {0} in ChangeArray.", arr[0]);
    }

    static void ChangeArrayElements(string[] arr)
    {
        // The following assignments change the value of individual array 
        // elements. 
        arr[0] = "Sat";
        arr[1] = "Fri";
        arr[2] = "Thu";
        // The following statement again displays Sat as the first element
        // in the array arr, inside the called method.
        System.Console.WriteLine("arr[0] is {0} in ChangeArrayElements.", arr[0]);
    }

    static void Main()
    {
        // Declare and initialize an array.
        string[] weekDays = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };

        // Pass the array as an argument to PrintArray.
        PrintArray(weekDays);

        // ChangeArray tries to change the array by assigning something new
        // to the array in the method. 
        ChangeArray(weekDays);

        // Print the array again, to verify that it has not been changed.
        System.Console.WriteLine("Array weekDays after the call to ChangeArray:");
        PrintArray(weekDays);
        System.Console.WriteLine();

        // ChangeArrayElements assigns new values to individual array
        // elements.
        ChangeArrayElements(weekDays);

        // The changes to individual elements persist after the method returns.
        // Print the array, to verify that it has been changed.
        System.Console.WriteLine("Array weekDays after the call to ChangeArrayElements:");
        PrintArray(weekDays);
    }
}
// Output: 
// Sun Mon Tue Wed Thu Fri Sat
// arr[0] is Sat in ChangeArray.
// Array weekDays after the call to ChangeArray:
// Sun Mon Tue Wed Thu Fri Sat
// 
// arr[0] is Sat in ChangeArrayElements.
// Array weekDays after the call to ChangeArrayElements:
// Sat Fri Thu Wed Thu Fri Sat
   ``` 
  
## Passing Multidimensional Arrays As Arguments  
 You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.  
  
   ```csharp 
    int[,] theArray = { { 1, 2 }, { 2, 3 }, { 3, 4 } };
    Print2DArray(theArray);
   ``` 
  
 The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.  
  
  ```csharp 
    void Print2DArray(int[,] arr)
    {
        // Method code.
    }
   ``` 
  
 You can initialize and pass a new array in one step, as is shown in the following example.  
  
  ```csharp 
    Print2DArray(new int[,] { { 1, 2 }, { 3, 4 }, { 5, 6 }, { 7, 8 } });
   ``` 
  
## Example  
  
### Description  
 In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method. The method displays the elements of the array.  
  
### Code  
   ```csharp 
class ArrayClass2D
{
    static void Print2DArray(int[,] arr)
    {
        // Display the array elements.
        for (int i = 0; i < arr.GetLength(0); i++)
        {
            for (int j = 0; j < arr.GetLength(1); j++)
            {
                System.Console.WriteLine("Element({0},{1})={2}", i, j, arr[i, j]);
            }
        }
    }
    static void Main()
    {
        // Pass the array as an argument.
        Print2DArray(new int[,] { { 1, 2 }, { 3, 4 }, { 5, 6 }, { 7, 8 } });

        // Keep the console window open in debug mode.
        System.Console.WriteLine("Press any key to exit.");
        System.Console.ReadKey();
    }
}
    /* Output:
        Element(0,0)=1
        Element(0,1)=2
        Element(1,0)=3
        Element(1,1)=4
        Element(2,0)=5
        Element(2,1)=6
        Element(3,0)=7
        Element(3,1)=8
    */
   ```  



