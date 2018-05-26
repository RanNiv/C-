# Table of Contents
* [Day_01_-_11.05.2018](#Day_01_-_11.05.2018)
* [Day_01_-_11.05.2018](#Day_01_-_11.05.2018)
* [00_Basic_string_and_debugging](#00_Basic_string_and_debugging)
* [01_Mul_function_example](#01_Mul_function_example)
* [02_Conditins](#02_Conditins)
* [03_Short_conditation](#03_Short_conditation)
* [04_switch_case](#04_switch_case)
* [05_Foreach_loop](#05_Foreach_loop)
* [06_loop_exersice](#06_loop_exersice)
* [07_Array](#07_Array)
* [08_Array](#08_Array)
* [09_Matrix](#09_Matrix)
* [10_Nested_loop_exercise](#10_Nested_loop_exercise)
* [00_function_overloading](#00_function_overloading)
* [01_div_int](#01_div_int)
* [02_named_params](#02_named_params)
* [03_default_parameters](#03_default_parameters)
* [04_params](#04_params)
* [05_ref_param](#05_ref_param)
* [06_out](#06_out)
* [07_out](#07_out)
* [08_check_conversion](#08_check_conversion)
* [00_try_catch](#00_try_catch)
* [01_try_catch](#01_try_catch)
* [02_array](#02_array)
* [03_array](#03_array)
* [04_generic_method](#04_generic_method)
* [05_generic_function](#05_generic_function)
* [06_generic_function](#06_generic_function)
* [07_collections](#07_collections)
* [08_fifo_and_lifo](#08_fifo_and_lifo)
* [09_collection](#09_collection)
* [00_basic_class](#00_basic_class)
* [00_basic_class](#00_basic_class)
* [01_Person_class](#01_Person_class)
* [01_Person_class](#01_Person_class)
* [02_Person_class](#02_Person_class)
* [02_Person_class](#02_Person_class)
* [03_Person_class](#03_Person_class)
* [03_Person_class](#03_Person_class)
* [04_Person_class](#04_Person_class)
* [04_Person_class](#04_Person_class)
* [05_static_class](#05_static_class)
* [05_static_class](#05_static_class)
* [06_Enum](#06_Enum)
* [06_Enum](#06_Enum)
* [Desktop](#Desktop)







## Day 01 - 11.05.2018 <a id="Day_01_-_11.05.2018"></a>
```csharp
using System;


//namespace עטיפה חיצונית כוללת של 
//אחד יכול להיות מפוצל לכמה קבצים namespace 
namespace _01_basic_types
{
    //זוהי המחלקה הראשית של הפרוייקט הנוכחי
    //מיד בתחילת הריצה תורץ הפונקציה
    //שבתוכה static void Main(string[] args) 
    class Program
    {
        static void Main(string[] args)
        {
            //press cw + TAB TAB to get 'Console.WriteLine()'
            Console.WriteLine("Hello, this is our first c# project");

            Console.WriteLine("please enter your name:");

            Console.ReadLine();
        }
    }
}

```



## Day 01 - 11.05.2018 <a id="Day_01_-_11.05.2018"></a>
```csharp
using System;

namespace _02_basic_types
{

    class Program
    {
        static void Main(string[] args)
        {
            //object - Supports all classes in the .NET Framework
            object myObject = 0;
            myObject = "Ishay";

            // string - Represents text as a series of Unicode characters.
            string myString = "Ori";

            //char - Represents a character as a UTF-16 code unit.
            char myChar1 = 'A';
            char myChar2 = (char)65;  //inside myChar2 we will get 'A' ('A' is 65 in ascii code)
            char myChar3 = (char)('A' + 32);  //inside myChar3 we will get 'a' ('a' is 65 + 32 in ascii code)

            //bool - Represents a Boolean (true or false) value.
            bool myBool = true;


            //******************************מספרים שלמים  - לא יכולים להיות עשרוניים
            //byte - Represents an 8-bit unsigned integer (0 to 255)
            byte myByte =255;

            //sbyte - Represents an 8-bit signed integer (-128 to 127)
            sbyte mySbyte = 0;

            //short - Represents a 16-bit signed integer. (-32,768 to 32,767)
            short myShort = 32760;

            //ushort - Represents a 16-bit unsigned integer (0 to 65,535)
            ushort myUshort = 32760;

            //int - Represents a 32-bit signed integer (-2,147,483,648 to 2,147,483,647)
            int myInt = 65539;

            //uint - Represents a 32-bit unsigned integer.
            uint myUint = 65539;


            long myLong = 66;
            ulong myUlong = 66;

            //****************************** מספרים עשרוניים
            // double  כל מספר עשרוני שנכתוב יהיה בצורה דיפולטיבית כטיפוס 

            //decimal - Represents a decimal number (-79228162514264337593543950335M to 79228162514264337593543950335M)
            decimal myDecimal =(decimal)0.99;
            myDecimal = 2.777M;
            myDecimal = Convert.ToDecimal(9.99);

            //double - Represents a double-precision floating-point number (15-16 digits after the point)
            double myDouble = 0.888;

            //float - Represents a single-precision floating-point number (7 digits after the point)
            float myFloat = (float)9.9;
            myFloat = 9.9F;
          


            //המרה של מחרוזת למספר
            int num1 = int.Parse("9");
            int num2 = Convert.ToInt32("9");

            //המרה של מחרוזת לערך בוליאני
            bool bool1 = bool.Parse("true");
            bool bool2 = Convert.ToBoolean("true");


            //המרה של מספר למחרוזת
            string str1 = (9).ToString();
            string str2 = Convert.ToString(9);

            Console.WriteLine("please enter your name:");

            string userName=Console.ReadLine();

            Console.WriteLine("please enter your age:");

            byte userAge=Convert.ToByte(Console.ReadLine());

            Console.WriteLine($"My name is {userName} , and I am {userAge} old");
        }
    }
}

```



## 00_Basic string and debugging <a id="00_Basic_string_and_debugging"></a>
```csharp
using System;


//DRY = Dont Repeat Yourself


namespace Basic_string_and_debugging
{
    class Program
    {

        static void PrintStr(string str1, string str2)
        {
            Console.WriteLine($" str1: {str1} \n str2: {str2} \n\n");
        }

        static void Main(string[] args)
        {

            string str1 = "I am str1", str2 = "I am str2";

            str1 = "Jerusalem is our capital city";
            str2 = str1;
            PrintStr(str1,str2);


            str1 = "Tel Aviv is an intresting city";
            PrintStr(str1, str2);

            Console.ReadLine();

        }
    }
}

```



## 01_Mul function example <a id="01_Mul_function_example"></a>
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Mul_function_example
{
    class Program
    {

        static int MulNum(int a, int b)
        {
            return a * b;
        }

        static void Main(string[] args)
        {
            int num1, num2, result;

            Console.WriteLine("please enter first number:");
            num1 = Convert.ToInt32(Console.ReadLine());

            Console.WriteLine("please enter second number:");
            num2 = Convert.ToInt32(Console.ReadLine());

            result = MulNum(num1, num2);

            Console.WriteLine($"the result of {num1}*{num2} is: {result}");
        }
    }
}

```



## 02_Conditins <a id="02_Conditins"></a>
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Conditins
{
    class Program
    {
        static void Main(string[] args)
        {
            int num1 = 2;
            int num2 = num1 * 6;



            //basic condition (<,>,==,!=,<=,>=)
            if (num1 > num2)
            {
                Console.WriteLine("num1 > num2");
            }

            else if (num1 < num2)
            {
                Console.WriteLine("num1 < num2");
            }

            else if (num1 >= num2)
            {
                Console.WriteLine("num1 >= num2");
            }

            else if (num1 <= num2)
            {
                Console.WriteLine("num1 <= num2");
            }

            else if (num1 == num2)
            {
                Console.WriteLine("num1 == num2");
            }

            else if (num1 != num2)
            {
                Console.WriteLine("num1 != num2");
            }





            //logical condition (<,>,==,!=,<=,>=)
            if (!(num1 == num2))
            {
                Console.WriteLine("!(num1 == num2)");
            }

            if ((num1 == num2) || (num1 < num2))
            {
                Console.WriteLine("(num1 == num2) || (num1 < num2)");

            }

            if ((num1 == num2) && (num1 < num2))
            {
                Console.WriteLine("(num1 == num2) && (num1 < num2)");

            }
        }
    }
}



/*
 
output:
--------------------    
num1 < num2
!(num1 == num2)
(num1 == num2) || (num1 < num2)
*/

```



## 03_Short conditation <a id="03_Short_conditation"></a>
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Short_conditation
{
    class Program
    {
        static void Main(string[] args)
        {
            int num1, num2, result;

            Console.WriteLine("please enter first number:");
            num1 = Convert.ToInt32(Console.ReadLine());

            Console.WriteLine("please enter second number:");
            num2 = Convert.ToInt32(Console.ReadLine());

            result = (num1 == num2) ? num1 * num2 : num1 + num2;

            Console.WriteLine($"the result is: {result}");
        }
    }
}

```



## 04_switch case <a id="04_switch_case"></a>
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Switch_Case
{
    class Program
    {
        static void Main(string[] args)
        {

            int temp = 19;

            //הערה חשובה
            //חובה לשים את המילה
            //brak / return
            //case אחרי כל 
            // brak / return ריק אפשר לוותר על case אבל אם נשאיר
            //אם יש אחריו אופציה נוספת - והיא זו שתתרחש עבורו
            switch (temp)
            {
                case 16: Console.WriteLine("please turn the heater on"); break;
                case 18:
                case 19:
                case 20: 
                case 21:
                case 22:
                case 23: Console.WriteLine("please turn the heater off"); break;

                default: Console.WriteLine("Do not touch the heater"); break;
            }
        }
    }
}

```



## 05_Foreach loop <a id="05_Foreach_loop"></a>
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Foreach_loop
{
    class Program
    {
        static void Main(string[] args)
        {

            string str = "c# is the best";

            for (int i = 0; i < str.Length; i++)
            {
                Console.WriteLine($"char number {i} is: {str[i]}");
            }

            foreach (char item in str)
            {
                Console.WriteLine(item);
            }
        }
    }
}


/*
 output:
 ----------------------------

 char number 0 is: c
char number 1 is: #
char number 2 is:
char number 3 is: i
char number 4 is: s
char number 5 is:
char number 6 is: t
char number 7 is: h
char number 8 is: e
char number 9 is:
char number 10 is: b
char number 11 is: e
char number 12 is: s
char number 13 is: t

c
#

i
s

t
h
e

b
e
s
t
 */

```



## 06_loop exersice <a id="06_loop_exersice"></a>
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _06_loop_exersice
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("please enter a string:");
            string str = Console.ReadLine();

            if (str.Length <= 5)
            {
                for (int i = 0; i < str.Length; i++)
                {
                    if(i%2==0)
                        Console.WriteLine(str[i]);
                }
            }
            else
            {
                foreach (char item in str)
                {
                    Console.WriteLine(item);
                }
            }
        }
    }
}

```



## 07_Array <a id="07_Array"></a>
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _07_Array
{
    class Program
    {
        static void Main(string[] args)
        {

  
            //משתנה רגיל -  value type
            //אסור להשתמש לפני שביצענו לתוכו השמה
            //איו לו ערך דיפולטיבי
            int simpleNum;
            //Console.WriteLine($"simpleNum is {simpleNum}");  //Use of unassigned local variable 'simpleNum' 



            //משתנה מצביע -  ref type
            // אחרי שהמשתנה מצביע לאובייקט אז לפני שביצענו למשתנים שבתוכו השמה
            //יהיה להם ערך דיפולטיבי
            /*
             bool --> false
             number (int or decimals) --> 0
             string --> null            
             */
            int[] numArray = new int[3];

            numArray[0] = 8;
            Console.WriteLine($"numArray[0] is { numArray[0]}");
            Console.WriteLine($"numArray[1] is { numArray[1]}");
            Console.WriteLine($"numArray[2] is { numArray[2]}");

            //numArray[8] = 3;  //--> System.IndexOutOfRangeException: Index was outside the bounds of the array.
        }
    }
}

```



## 08_Array <a id="08_Array"></a>
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _08_Array
{
    class Program
    {
        static void Main(string[] args)
        {
            //bool --> false
            Console.WriteLine("------------boolArray--------------");
            bool[] boolArray = new bool[2];
            foreach (bool item in boolArray)
            {
                Console.WriteLine(item);
            }

            //char --> `\0` (ascii code of 0)
            Console.WriteLine("------------charArray--------------");
            char[] charArray = new char[2];
            foreach (char item in charArray)
            {
                Console.WriteLine(item);
            }

            //int --> 0
            Console.WriteLine("------------intArray--------------");
            int[] intArray = new int[2];
            foreach (int item in intArray)
            {
                Console.WriteLine(item);
            }


            //string --> null
            Console.WriteLine("------------stringArray--------------");
            string[] stringArray = new string[2];
            foreach (string item in stringArray)
            {
                Console.WriteLine(item);
            }
        }
    }
}

```



## 09_Matrix <a id="09_Matrix"></a>
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _09_Matrix
{
    class Program
    {
        static void Main(string[] args)
        {
            int row = 2;
            int col = 2;

            int[][] matrix = new int[row][];

                for (int i = 0; i < matrix.Length; i++)
            {
                matrix[i] = new int[col];
                for (int j = 0; j < matrix[i].Length; j++)
                {
                    matrix[i][j] = i + j;
                }
            }

            foreach (int[] outer in matrix)
            {
                foreach (int inner in outer)
                {
                    Console.Write(inner+" ");
                }
                Console.WriteLine();
            }
        }
    }
}

```



## 10_Nested loop exercise <a id="10_Nested_loop_exercise"></a>
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _10_Nested_Loop_exercise
{
    class Program
    {
        static void Main(string[] args)
        {
    
            bool flag;
            string str;
            do
            {
                Console.WriteLine("please insert a number");
                str = Console.ReadLine();
                int i;
                for (i = 0; i < str.Length; i++)
                {
                    //check if current char is numeric
                    if(!(str[i] >= 48 && str[i] <= 57))
                    {
                        break;
                    }
                }

                flag = (i == str.Length);

            } while (!flag);

            int num = Convert.ToInt32(str);

            for (int outer = 0; outer < num; outer++)
            {
                for (int inner = 0; inner < outer+1; inner++)
                {
                    Console.Write("*");
                }
                Console.WriteLine();
            }

        }
    }
}

```



## 00_function overloading <a id="00_function_overloading"></a>
```csharp
using System;

/*
 העמסת פונקציות  - function overloading
_________________________________________________

1. כל הפונקציות חייבות להיות בעלות אותו שם
2. כל פונקציה חייבת לקבל מספר פרמטרים שונה או אותו מספר פרמטרים אבל טיפוסי פרמטרים שונים
3. ערך מוחזר מטיפוס שונה - לא עומד בתנאי ההעמסה
4. שמות פרמטרים שונים - לא משפיעים על ההעמסה   
     */
namespace _00_function_overloading
{
    class Program
    {
        static int GetAvg(int param1, int param2)
        {
            return (param1 + param2) / 2;
        }


        static decimal GetAvg(decimal param1, decimal param2)
        {
            return (param1 + param2) / 2;
        }

        static void Main(string[] args)
        {
            int grade1 = 100, grade2 = 95;
            decimal waterPrice1 = 12.5M, waterPrice2 = 7;

            decimal gradeAvg = GetAvg(grade1, grade2); 
            decimal priceAvg = GetAvg(waterPrice1, waterPrice2);

            Console.WriteLine($" grade1 is {grade1}\n grade2 is {grade2}");
            Console.WriteLine($" avg of grade1 & grade2 is {(grade1+grade2)/2}");
            Console.WriteLine($" avg of grade1 & grade2 is {(grade1 + grade2) / 2.0}");
            Console.WriteLine($" avg of grade1 & grade2 is {gradeAvg}");

            Console.WriteLine("---------------------------------------------");

            Console.WriteLine($" waterPrice1 is {waterPrice1}\n waterPrice2 is {waterPrice2}");
            Console.WriteLine($" avg of waterPrice1 & waterPrice2 is {(waterPrice1 + waterPrice2) / 2}");
            Console.WriteLine($" avg of waterPrice1 & waterPrice2 is {priceAvg}");
        }
    }
}


/*
 output:

__________________________________________

 grade1 is 100
 grade2 is 95
 avg of grade1 & grade2 is 97
 avg of grade1 & grade2 is 97.5
 avg of grade1 & grade2 is 97
---------------------------------------------
 waterPrice1 is 12.5
 waterPrice2 is 7
 avg of waterPrice1 & waterPrice2 is 9.75
 avg of waterPrice1 & waterPrice2 is 9.75
*/

```



## 01_div int <a id="01_div_int"></a>
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _01_div_int
{
    class Program
    {
        static void Main(string[] args)
        {
            int num1 = 3, num2 = 2;
            double res;

            res = num1 / num2;
            Console.WriteLine($"{num1} / {num2} = {res}");  //--> 3 / 2 = 1


            res = 1.0 *num1 / num2;
            Console.WriteLine($"{num1} / {num2} = {res}");  //--> 3 / 2 = 1.5

            res = (0.0 + num1) / num2;
            Console.WriteLine($"{num1} / {num2} = {res}");  //--> 3 / 2 = 1.5

            res =  num1 / num2 * 1.0;
            Console.WriteLine($"{num1} / {num2} = {res}");  //--> 3 / 2 = 1


            res = num1 / (num2 * 1.0);
            Console.WriteLine($"{num1} / {num2} = {res}");  //--> 3 / 2 = 1.5


            res = (double)num1/ num2;   //המרה מפורשת לטיפוס עשרוני ולא לטיפוס שלם

            Console.WriteLine($"{num1} / {num2} = {res}");  //--> 3 / 2 = 1.5


            res = (double)(num1 / num2);   // (num1 / num2) was implemented first - and gave an int result

            Console.WriteLine($"{num1} / {num2} = {res}");  //--> 3 / 2 = 1


        }
    }
}

```



## 02_named params <a id="02_named_params"></a>
```csharp
using System;

namespace _02_named_params
{
    class Program
    {

        static int divNum(int numInt)  //F1 סימן זיהוי לפונקציה 
        {
            return numInt / 2;
        }

        static double divNum(double numDouble)  //F2 סימן זיהוי לפונקציה 
        {
            return numDouble / 2;
        }

        static void Main(string[] args)
        {

            double res;

            res = divNum(3); // F1  תתבצע קריאה ל
            Console.WriteLine($"{res}");  //--> 1

            res = divNum(3.0); // F2  תתבצע קריאה ל
            Console.WriteLine($"{res}");  //--> 1.5

            int myNumber = 7;

            res = divNum(myNumber); // F1  תתבצע קריאה ל
            Console.WriteLine($"{res}");  //--> 3

            // first option to call F2 with int param : cast int to double

            res = divNum((double)myNumber); // F2 תתבצע קריאה ל
            Console.WriteLine($"{res}");  //--> 3.5

            // second option to call F2 with int param : named parameters

            res = divNum(numDouble:myNumber); // F2 תתבצע קריאה ל
            Console.WriteLine($"{res}");  //--> 3.5

        }
    }
}

```



## 03_default parameters <a id="03_default_parameters"></a>
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _03_default_parameters
{
    class Program
    {
   
        static void PrintStudentInfo(string name, int age, bool gender = true, int grade = 100)
        {
            Console.WriteLine($"{name} is {age} years old, isMale: {gender}, and grade is {grade}");
        }



        //**********************press "///" and get the following comment template:*****************
        /// <summary>
        /// this function prints the info of a specific person
        /// </summary>
        /// <param name="name">only first name</param>
        /// <param name="age">range 0-120</param>
        /// <param name="gender">male is true, female is false</param>
        static void PrintPersonInfo(string name, int age, bool gender=true)
        {
            Console.WriteLine($"{name} is {age} years old, isMale: {gender}");
        }

 

        static void Main(string[] args)
        {

            PrintPersonInfo("Alice", 20, false);
            PrintPersonInfo("Bob", );


            PrintStudentInfo("Tzahi", 18);
            PrintStudentInfo("Lera", 18,false);
            PrintStudentInfo("Meir", 18, true,99);
            PrintStudentInfo(age:18, grade:99, name: "Meir");
        }
    }
}


/*
 
output:
__________________________________
 
Alice is 20 years old, isMale: False
Bob is 23 years old, isMale: True
Tzahi is 18 years old, isMale: True, and grade is 100
Lera is 18 years old, isMale: False, and grade is 100
Meir is 18 years old, isMale: True, and grade is 99
Meir is 18 years old, isMale: True, and grade is 99
*/

```



## 04_params <a id="04_params"></a>
```csharp
using System;

namespace _04_params
{
    class Program
    {

        static void PrintStudenmtsName1(string[] arr)
        {
            foreach (string item in arr)
            {
                Console.WriteLine(item);
            }
        }


        static void PrintStudenmtsName2(params string[] arr)
        {
            foreach (string item in arr)
            {
                Console.WriteLine(item);
            }
        }


        static void Main(string[] args)
        {
            Console.WriteLine("---------------PrintStudenmtsName1-------------------");
            PrintStudenmtsName1(new string[]{"Ori","Asa","Victoria","Tal","Marina"});

            Console.WriteLine("---------------PrintStudenmtsName2-------------------");
            PrintStudenmtsName2("Ori", "Asa", "Victoria", "Tal", "Marina");
        }
    }
}


/*
 output:

_______________________________________________________


---------------PrintStudenmtsName1-------------------
Ori
Asa
Victoria
Tal
Marina
---------------PrintStudenmtsName2-------------------
Ori
Asa
Victoria
Tal
Marina     
*/

```



## 05_ref param <a id="05_ref_param"></a>
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _05_ref_param
{
    class Program
    {
        static void PrintArr(int[] arr)
        {
            foreach (int item in arr)
            {
                Console.Write(item + " ");
            }

            Console.WriteLine();
        }

        static void FindMinAndMax(int num1, int num2, int num3, ref int max, ref int min)
        {
            max = (num1 > num2 && num1 > num3) ? num1 : (num2 > num3) ? num2 : num3;

            min = (num1 < num2 && num1 < num3) ? num1 : (num2 < num3) ? num2 : num3;
        }

        static void UpdareArr(int[] arr)
        {
            arr[0] = 9;
        }

        static void InitArr(int[] arr)
        {
            arr = new int[] { 4,4 };
        }


        static void InitArrByRef(ref int[] arr)
        {
            arr = new int[] { 4, 4 };
        }

        static void Main(string[] args)
        {

            int num1 = 50, num2 = 17, num3 = 88, max=0, min=0;
            Console.WriteLine($"max: {max}, min: {min}");  //--> max: 0, min: 0
            FindMinAndMax(num1, num2, num3, ref max, ref min);
            Console.WriteLine($"max: {max}, min: {min}");  //--> max: 88, min: 17


            int[] arr = new int[] { 1, 2, 3 };

            PrintArr(arr);  //--> 1 2 3

            UpdareArr(arr);
            PrintArr(arr);  //--> 9 2 3

            InitArr(arr);
            PrintArr(arr);  //--> 9 2 3

            InitArrByRef(ref arr);
            PrintArr(arr);  //--> 4 4


        }


        
    }
}

```



## 06_out <a id="06_out"></a>
```csharp
using System;

namespace _06_out
{
    class Program
    {

        static void FilterArrayByEven(int[] src,out int[] target)
        {
            int oddCounter = 0;
            foreach (var item in src)
            {
                oddCounter += item%2;
            }

            target = new int[src.Length - oddCounter];

            int i = 0;
            foreach (var item in src)
            {
                if (item % 2==0)
                    target[i++] = item;
            }
        }

        static void Main(string[] args)
        {
            int[] numArray = new int[5];
            int[] evenNumFiltered;

            for (int i = 0; i < numArray.Length; i++)
            {
                Console.WriteLine($"please enter a number into elemnt {i+1}");
                numArray[i] = Convert.ToInt32(Console.ReadLine());
            }

            FilterArrayByEven(numArray, out evenNumFiltered);

            foreach (int item in numArray)
            {
                Console.Write(item +", ");
            }

            Console.WriteLine();
            foreach (int item in evenNumFiltered)
            {
                Console.Write(item + ", ");
            }
            Console.WriteLine();
        }
    }
}

```



## 07_out <a id="07_out"></a>
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _07_out
{
    class Program
    {

        static void InitNum(out int param)
        {
            param = 6;
        }

        static void Main(string[] args)
        {
            int num1;

            //Console.WriteLine($"num1: {num1}");  //COMPILATION ERROR - Use of unassigned local variable 'num1'

            InitNum(out num1);

            Console.WriteLine($"num1: {num1}");
        }
    }
}

```



## 08_check conversion <a id="08_check_conversion"></a>
```csharp
using System;

namespace _08_check_conversion
{
    class Program
    {
        static void Main(string[] args)
        {
            int num;
 
            // Converts the string representation of a number to its 32 - bit signed integer equivalent.
            //     A return value indicates whether the conversion succeeded.
            //
            // Parameters:
            //   s: A string containing a number to convert.
            //   num: Out parameter - will get the converted number - if the conversion succeeded, or zero if the conversion failed
            //
            // Returns:
            //     true if s was converted successfully; otherwise, false.
            bool isConvertSuccess = int.TryParse("12",out num);
            Console.WriteLine($"int.TryParse(\"12\",out num) gives:" );
            Console.WriteLine($"isConvertSuccess ={ isConvertSuccess}, num ={num}");
            Console.WriteLine();

            isConvertSuccess = int.TryParse("Alice", out num);
            Console.WriteLine($"int.TryParse(\"Alice\",out num) gives:");
            Console.WriteLine($"isConvertSuccess ={ isConvertSuccess}, num ={num}");
        }
    }
}


/*
output:
______________________________

int.TryParse("12",out num) gives:
isConvertSuccess =True, num =12

int.TryParse("Alice",out num) gives:
isConvertSuccess =False, num =0
*/

```



## 00_try catch <a id="00_try_catch"></a>
```csharp
using System;

namespace _00_try_catch
{
    class Program
    {
        static void Main(string[] args)
        {

            int[] arr = { 0, 1, 2, 3, 4 };

            int num1 = 9, num2, num3;

            try
            {
                Console.WriteLine("pls enter your number");
                num2 = int.Parse(Console.ReadLine());
                num3 = num1 / arr[num2];
            }
            catch(ArithmeticException)
            {
                Console.WriteLine("ArithmeticException");
            }

            /* //COMPILATION ERROR
             * // A previous catch clause already catches all exceptions of this or of a super type('ArithmeticException')
            catch (DivideByZeroException ex)  
            {
                Console.WriteLine("you are catched with DivideByZeroException");
            }
            */

            catch (FormatException)
            {
                Console.WriteLine("you are catched with FormatException");
            }
            catch (IndexOutOfRangeException)
            {
                Console.WriteLine("you are catched with IndexOutOfRangeException");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"you are catched with {ex.GetType()}");
            }
            finally
            {
                Console.WriteLine("finally MSG");
            }

            Console.WriteLine("after all try & catch");
        }
    }
}

```



## 01_try catch <a id="01_try_catch"></a>
```csharp
using System;

namespace _01_try_catch
{
    class Program
    {


        static int divNum()
        {
            int num1 = 9, num2=0, num3=0;

            try
            {
                num3 = num1 /num2;
                return num3;
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
                return num3;
            }
           //the code in the "finally" block will run
           //alsoafter we had a "return" statment in the try / catch
            finally
            {
                //אין השפעה של השורה הזו על קידום הערך המוחזר
                //return כיוון שתוכן הערך המוחזר כבר נקבע למעלה בפקודת
                //finally ורק מתעכב עד שיסתיים ביצוע ה
                ++num3;
                Console.WriteLine("finally MSG");
            }

            Console.WriteLine("after all try & catch");
        }

        static void Main(string[] args)
        {

            int res = divNum();
            Console.WriteLine("divNum returned " +res);
        }
    }
}


/*
OUTPUT:
____________________________


Attempted to divide by zero.
finally MSG
divNum returned 0
Press any key to continue . . . 
 */

```



## 02_array <a id="02_array"></a>
```csharp
using System;

namespace _02_array
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] list = { 1,4,2,3 };
            Console.Write("Original Array: ");

            foreach (int i in list)
            {
                Console.Write(i + " ");
            }
            Console.WriteLine();

            // reverse the array
            Array.Reverse(list);
            Console.Write("Reversed Array: ");

            foreach (int i in list)
            {
                Console.Write(i + " ");
            }
            Console.WriteLine();

            //sort the array
            Array.Sort(list);
            Console.Write("Sorted Array: ");

            foreach (int i in list)
            {
                Console.Write(i + " ");
            }
            Console.WriteLine();
            Console.ReadKey();
        }
    }
}


/*
OUTPUT:
_________________________________

Original Array: 1 4 2 3
Reversed Array: 3 2 4 1
Sorted Array: 1 2 3 4
 
     
*/

```



## 03_array <a id="03_array"></a>
```csharp
using System;

namespace _03_array
{
    class Program
    {
        static void Main(string[] args)
        {

            int[,] mat = { { 1, 4, 2, 3 }, { 1, 4, 2, 3 } };
            Console.WriteLine($"list rank is:{mat.Rank}");

            int[] list = { 1, 4, 2, 3 };
            int[] listCopy = new int[4];

            Console.WriteLine( $"list rank is:{list.Rank}");
            Console.Write("Original Array: ");

            foreach (int i in list)
            {
                Console.Write(i + " ");
            }

            Console.WriteLine();

            list.CopyTo(listCopy, 0);
            // reverse the array
            Array.Reverse(listCopy);
            Console.Write("Reversed Array: ");

            foreach (int i in listCopy)
            {
                Console.Write(i + " ");
            }
            Console.WriteLine();

            //sort the array
            Array.Sort(listCopy);
            Console.Write("Sorted Array: ");

            foreach (int i in listCopy)
            {
                Console.Write(i + " ");
            }
            Console.WriteLine();


            Console.Write("Original Array: ");

            foreach (int i in list)
            {
                Console.Write(i + " ");
            }
            Console.ReadKey();
        }
    }
}

/*

OUTPUT:
_____________________________

list rank is:2
list rank is:1
Original Array: 1 4 2 3
Reversed Array: 3 2 4 1
Sorted Array: 1 2 3 4
Original Array: 1 4 2 3  
     
 */

```



## 04_generic method <a id="04_generic_method"></a>
```csharp
using System;

namespace _04_generic_method
{
    class Program
    {

        static string Sub(string s1,string s2)
        {
            return s1 + s2;
        }


        static int Sub(int s1, int s2)
        {
            return s1 + s2;
        }


        static double Sub(double s1, double s2)
        {
            return s1 + s2;
        }


        static void Main(string[] args)
        {
            Console.WriteLine($"static string Sub(\"Bob\",\"Alice\") returned: {Sub("Bob", "Alice")} ");
            Console.WriteLine($"static int Sub(2,3) returned: {Sub(2,3)} ");
            Console.WriteLine($"static double Sub(3.25, 7.55) returned: {Sub(3.25, 7.55)} ");
        }
    }
}


/*
OUTPUT:
_____________________________

static string Sub("Bob","Alice") returned: BobAlice
static int Sub(2,3) returned: 5
static double Sub(3.25, 7.55) returned: 10.8
     
*/

```



## 05_generic function <a id="05_generic_function"></a>
```csharp
using System;

namespace _05_generic_method
{
    class Program
    {

        static void ShowParam<T,K>(T param1,K param2)
        {
            Console.WriteLine($"param1: {param1}, param2: {param2}");
        }

        static  void NonReturnedVal<T>()
        {
            return;
        }

        static void Main(string[] args)
        {
            ShowParam("Bob", "Alice");
            ShowParam("Bob", 3);
            ShowParam(true, 4.88);
            ShowParam(9, false);

            NonReturnedVal<int>( );
        }
    }
}


/*
OUTPUT:
_____________________________

param1: Bob, param2: Alice
param1: Bob, param2: 3
param1: True, param2: 4.88
param1: 9, param2: False
     
*/

```



## 06_generic function <a id="06_generic_function"></a>
```csharp
using System;

namespace _06_generic_method
{
    class Program
    {

        static T ReturnMySelf<T>(T s1)
        {
            return s1;
        }
        
        static void Main(string[] args)
        {
            Console.WriteLine($"static string ReturnMySelf(\"Bob\") returned: {ReturnMySelf("Bob")} ");
            Console.WriteLine($"static int ReturnMySelf(2) returned: {ReturnMySelf(2)} ");
            Console.WriteLine($"static double ReturnMySelf(3.25) returned: {ReturnMySelf(3.25)} ");
        }
    }
}


/*
OUTPUT:
_____________________________

static string ReturnMySelf("Bob") returned: Bob
static int ReturnMySelf(2) returned: 2
static double ReturnMySelf(3.25) returned: 3.25
     
*/

```



## 07_collections <a id="07_collections"></a>
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _07_collections
{
    class Program
    {

        static void PrintList(string arrayName,List<string> collection)
        {

      
            Console.WriteLine($"{arrayName} Capacity: {collection.Capacity}");
            foreach (string str in collection)
            {
                Console.Write(str+" ,");
            }
            Console.WriteLine();

        }

        static void Main(string[] args)
        {

            //---------------------------מערך רגיל - בעל אורך קבוע-------------------------
            string[] names1 = { "A", "B", "C" };
            PrintList("names1",names1.ToList());  //List המרה ממערך ל

            //System.IndexOutOfRangeException:
            //names1[3] = "D";  --> runtime Exception

            //---------------------------מערך דינמי - בעל אורך משתנה-------------------------
            List <string> names2 = new List<string>();  //we can send to the constructor of "List" capacity

            

            names2.AddRange(names1);


            names2.Add("D");
            PrintList("names2",names2);

            names2.Add("F");
            PrintList("names2", names2);

            names2.AddRange(names1);
            PrintList("names2", names2);

            names2.RemoveAt(2);
            PrintList("names2", names2);

            string str = names2[names2.Count / 2];
            names2.Remove(str);
            PrintList("names2", names2);


        }
    }
}

```



## 08_fifo and lifo <a id="08_fifo_and_lifo"></a>
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _08_fifo_and_lifo
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("\n---------------------------Queue------------------");

            Queue <string> names1 = new Queue<string>();  //FIFO -> First In First Out
            names1.Enqueue("A1");
            names1.Enqueue("A2");
            names1.Enqueue("A3");
            names1.Enqueue("A4");
            foreach (string item in names1)
            {
                Console.Write(item + " ,");
            }

            Console.WriteLine();


            string str1 = names1.Dequeue();  
            Console.WriteLine($"\nnames1 is serving now element {str1}");

            foreach (string item in names1)
            {
                Console.Write(item + " ,");
            }
            str1 = names1.Peek();
            Console.WriteLine($"\nnames1 will serve soon element {str1}");
            Console.WriteLine("after peek:");
            foreach (string item in names1)
            {
                Console.Write(item + " ,");
            }


            Console.WriteLine("\n---------------------------Stack------------------");

            Stack<string> names2= new Stack<string>();  //LIFO -> Last In First Out
            names2.Push("A1");
            names2.Push("A2");
            names2.Push("A3");
            names2.Push("A4");
            foreach (string item in names2)
            {
                Console.Write(item + " ,");
            }

            Console.WriteLine();


            string str2 = names2.Pop();
            Console.WriteLine($"\nnames2 is serving now element {str2}");

            foreach (string item in names2)
            {
                Console.Write(item + " ,");
            }
            str2 = names2.Peek();
            Console.WriteLine($"\nnames2 will serve soon element {str2}");
            Console.WriteLine("after peek:");
            foreach (string item in names2)
            {
                Console.Write(item + " ,");
            }
        }
    }
}

```



## 09_collection <a id="09_collection"></a>
```csharp
using System;
using System.Collections.Generic;

namespace _09_collection
{
    class Program
    {
        static void Main(string[] args)
        {
            Dictionary<string, string> countriesCapitals = new Dictionary<string, string>();
            countriesCapitals.Add("Israel", "Jerusalem");
            countriesCapitals.Add("Germany", "Berlin");
            countriesCapitals.Add("UK", "London");
            countriesCapitals.Add("France", "Paris");

            foreach (KeyValuePair<string,string> item in countriesCapitals)
            {
                Console.WriteLine(item.Key+" "+item.Value);
            }

            Console.WriteLine($"Israel capital is: {countriesCapitals["Israel"]}");
            

            Dictionary<string,int> countriesPopulation = new Dictionary<string, int>();
            countriesPopulation.Add("Israel", 8527400);
            countriesPopulation.Add("Germany", 4527400);
            countriesPopulation.Add("UK", 28527400);
            countriesPopulation.Add("France", 1527400);


            foreach (KeyValuePair<string, int> item in countriesPopulation)
            {
                Console.WriteLine(item.Key + " " + item.Value);
            }

            Console.WriteLine($"Israel Population is: {countriesPopulation["Israel"]}");

            Dictionary<KeyValuePair<string, string>, int> countriesCapitalPopulation = new Dictionary<KeyValuePair<string, string>, int>();
            countriesCapitalPopulation.Add(new KeyValuePair<string, string>("Israel", "Jerusalem"), 3327400);
            countriesCapitalPopulation.Add(new KeyValuePair<string, string>("Germany", "Berlin"), 72400);
            countriesCapitalPopulation.Add(new KeyValuePair<string, string>("UK", "London"), 77400);
            countriesCapitalPopulation.Add(new KeyValuePair<string, string>("France", "Paris"), 127400);

            foreach (KeyValuePair<KeyValuePair<string, string>, int> item in countriesCapitalPopulation)
            {
                Console.WriteLine($"Country {item.Key.Key}, Capital: {item.Key.Value}, Population {item.Value}");
            }


            KeyValuePair<string, string> index = new KeyValuePair<string, string>("Israel", "Jerusalem");
            Console.WriteLine($"Israel Population is: {countriesCapitalPopulation[index]}");

        }
    }
}



/*
 
OUTPUT:
____________________

Israel Jerusalem
Germany Berlin
UK London
France Paris
Israel capital is: Jerusalem
Israel 8527400
Germany 4527400
UK 28527400
France 1527400
Israel Population is: 8527400
Country Israel, Capital: Jerusalem, Population 3327400
Country Germany, Capital: Berlin, Population 72400
Country UK, Capital: London, Population 77400
Country France, Capital: Paris, Population 127400
Israel Population is: 3327400
*/

```



## 00_basic class <a id="00_basic_class"></a>
```csharp
/*
  ctor + tab tab        --> auto generates constructor

  prop + tab tab        --> auto generates public property

  propfull + tab tab    --> auto generates public+private property

  control + k + s       --> to add region
 */

using System;


namespace _00_basic_class
{
    class Flight
    {
        //---------------------constructors--------------------
        public Flight(){}

        public Flight(int price)
        {
            FlightPrice = price;
        }

        //---------------------functions--------------------
        #region bool CheckFlightPrice(int flightPrice)
        public bool CheckFlightPrice(int flightPrice)
        {
            return this.flightPrice == flightPrice;
        } 
        #endregion



        //---------------------properties--------------------
        #region FlightNumber prop
        public int FlightNumber { get; set; } 
        #endregion

        #region FlightPrice propfull
        private int flightPrice;

        public int FlightPrice
        {
            get { return flightPrice; }
            set
            {

                flightPrice = Math.Abs(value);
            }
        } 
        #endregion


    }
}

```



## 00_basic class <a id="00_basic_class"></a>
```csharp
using System;

namespace _00_basic_class
{
    class Program
    {
        static void Main(string[] args)
        {
            Flight flight1 = new Flight();
            Flight flight2 = new Flight(-400);
            flight1.FlightPrice = -500;
            bool isCorrectPrice=flight1.CheckFlightPrice(500);

            Console.WriteLine(isCorrectPrice);  // --> true
        }
    }
}

```



## 01_Person class <a id="01_Person_class"></a>
```csharp
namespace _01_Person_class
{
    class Person
    {

        //----------------------------------constructor-----------------------------

        public Person()
        {
            Age = 19;
            PersonName = "Unknown";
        }

        public Person(string name)
        {
            Age = 18;
            PersonName = name;
        }


        public Person(int age, string name)
        {
            Age = age;
            PersonName = name;
        }


        //-----------------------------------functions------------------------------
        public string GetFullDetails()
        {
            return $"Person age: {Age}, Person Name:{PersonName}";
        }

        //-----------------------------------properties-----------------------------

        private int age;

        public int Age
        {
            get { return age; }
            set { age = (value>=0 && value<=120)?value:18; }
        }


        private string personName;

        public string PersonName
        {
            get { return personName;; }
            set { personName = (value.Length>=2 && value.Length<=10)?value:"Unknown"; }
        }


    }
}

```



## 01_Person class <a id="01_Person_class"></a>
```csharp
using System;

namespace _01_Person_class
{
    class Program
    {
        static void Main(string[] args)
        {
            Person person1 = new Person();
            Person person2 = new Person("Bob");
            Person person3 = new Person(16,"Alice");

            Console.WriteLine(person1.GetFullDetails());
            Console.WriteLine(person2.GetFullDetails());
            Console.WriteLine(person3.GetFullDetails());
        }
    }
}



/*
OUTPUT:
____________________________________

Person age: 19 , Person Name:Unknown
Person age: 18, Person Name:Bob
Person age: 16, Person Name:Alice    
     
 */

```



## 02_Person class <a id="02_Person_class"></a>
```csharp
namespace _02_Person_class
{
    class Person
    {

        //----------------------------------constructor-----------------------------

        public Person():this(19, "Unknown"){  }

        public Person(string name) : this(18, name){ }

        public Person(int age, string name)
        {
            Age = age;
            PersonName = name;
        }


        //-----------------------------------functions------------------------------
        public string GetFullDetails()
        {
            return $"Person age: {Age}, Person Name:{PersonName}";
        }

        //-----------------------------------properties-----------------------------

        private int age;

        public int Age
        {
            get { return age; }
            set { age = (value>=0 && value<=120)?value:18; }
        }


        private string personName;

        public string PersonName
        {
            get { return personName;; }
            set { personName = (value.Length>=2 && value.Length<=10)?value:"Unknown"; }
        }


    }
}

```



## 02_Person class <a id="02_Person_class"></a>
```csharp
using System;

namespace _02_Person_class
{
    class Program
    {
        static void Main(string[] args)
        {
            Person person1 = new Person();
            Person person2 = new Person("Bob");
            Person person3 = new Person(16,"Alice");

            Console.WriteLine(person1.GetFullDetails());
            Console.WriteLine(person2.GetFullDetails());
            Console.WriteLine(person3.GetFullDetails());
        }
    }
}



/*
OUTPUT:
____________________________________

Person age: 19, Person Name:Unknown
Person age: 18, Person Name:Bob
Person age: 16, Person Name:Alice    
     
 */

```



## 03_Person class <a id="03_Person_class"></a>
```csharp
using System;

namespace _03_Person_class
{
    class Person
    {

        //----------------------------------constructor-----------------------------

        public Person():this(19, "Unknown"){
            Console.WriteLine("I AM CTOR THAT TAKES NO ARUMENTS");
        }


        public Person(string name) : this(18, name){
            Console.WriteLine("I AM CTOR THAT TAKES (string name) ARUMENT");
        }

        public Person(int age, string name)
        {
            Console.WriteLine("I AM CTOR THAT TAKES (int age, string name) ARUMENTS");
            Age = age;
            PersonName = name;
        }


        //-----------------------------------functions------------------------------
        public string GetFullDetails()
        {
            return $"Person age: {Age}, Person Name:{PersonName}";
        }

        //-----------------------------------properties-----------------------------

        private int age;

        public int Age
        {
            get { return age; }
            set { age = (value>=0 && value<=120)?value:18; }
        }


        private string personName;

        public string PersonName
        {
            get { return personName;; }
            set { personName = (value.Length>=2 && value.Length<=10)?value:"Unknown"; }
        }


    }
}

```



## 03_Person class <a id="03_Person_class"></a>
```csharp
using System;

namespace _03_Person_class
{
    class Program
    {
        static void Main(string[] args)
        {
            Person person1 = new Person();
            Console.WriteLine("------------------------------");

            Person person2 = new Person("Bob");
            Console.WriteLine("------------------------------");

            Person person3 = new Person(16,"Alice");
            Console.WriteLine("------------------------------");

            Console.WriteLine(person1.GetFullDetails());
            Console.WriteLine(person2.GetFullDetails());
            Console.WriteLine(person3.GetFullDetails());
        }
    }
}



/*
OUTPUT:
____________________________________

I AM CTOR THAT TAKES (int age, string name) ARUMENTS
I AM CTOR THAT TAKES NO ARUMENTS
------------------------------
I AM CTOR THAT TAKES (int age, string name) ARUMENTS
I AM CTOR THAT TAKES (string name) ARUMENT
------------------------------
I AM CTOR THAT TAKES (int age, string name) ARUMENTS
------------------------------
Person age: 19, Person Name:Unknown
Person age: 18, Person Name:Bob
Person age: 16, Person Name:Alice  
     
 */

```



## 04_Person class <a id="04_Person_class"></a>
```csharp
using System;

namespace _04_Person_class
{
    class Person
    {

        //----------------------------------constructor-----------------------------

        public Person(int age, string name)
        {
            Age = age;
            PersonName = name;

            counter++;

            if(counter>=3 && counter <= 5)
            {
                Console.WriteLine($"{PersonName} is second generation");
            }
            
        }


        //בנאי סטטי שנקרא פעם אחת בלבד בשימוש הראשון במחלקה - בצורה אוטומטית - אי אפשר לקרוא לו בצורה יזומה
        static Person()
        {
            Console.WriteLine("The first person in the world was created now");
        }


        //-----------------------------------functions------------------------------
        public string GetFullDetails()
        {
            return $"Person age: {Age}, Person Name:{PersonName}";
        }

        //-----------------------------------properties-----------------------------

        private static int counter=0;

        private int age;

        public int Age
        {
            get { return age; }
            set { age = (value>=0 && value<=120)?value:18; }
        }


        private string personName;

        public string PersonName
        {
            get { return personName;; }
            set { personName = (value.Length>=2 && value.Length<=10)?value:"Unknown"; }
        }


    }
}

```



## 04_Person class <a id="04_Person_class"></a>
```csharp
using System;

namespace _04_Person_class
{
    class Program
    {
        static void Main(string[] args)
        {
           
            Person person1 = new Person(0, "Adam");

            Person person2 = new Person(0, "Eve");

            Person person3 = new Person(0, "Cain");

            Person person4 = new Person(0, "Abel");

            Person person5 = new Person(0, "Seth");

           
        }
    }
}






/*
OUTPUT:
____________________________________

The first person in the world was created now
Cain is second generation
Abel is second generation
Seth is second generation
     
 */

```



## 05_static class <a id="05_static_class"></a>
```csharp
using System;

namespace _05_static_class
{
    class Program
    {
        static void Main(string[] args)
        {

            Console.WriteLine(TimeChecker.getFullDate());

            Console.WriteLine(TimeChecker.DiffDate.TotalSeconds);

            for (int i = 0; i < Math.Pow(10,11); i++)
            {

            }
            Console.WriteLine(TimeChecker.DiffDate.TotalSeconds);
        }
    }
}






/*
OUTPUT:
____________________________________

12:36:31
0.0050034
0.0090054
     
 */

```



## 05_static class <a id="05_static_class"></a>
```csharp
using System;


namespace _05_static_class
{
    static class TimeChecker
    {

        //-------------------------------properties--------------------------

        //משתנה שיאותחל פעם אחת בלבד בבנאי הסטטי ויאחסן את הזמן בו בוצעה לראשונה פניה למחלקה
        private static DateTime startDate;

        //משתנה סטטי
        //מחזיר את ההפרש בין הזמן הנוכחי לזמן בו בוצעה לראשונה קריאה למחלקה
        public static TimeSpan DiffDate
        {
            get { return (DateTime.Now)- (startDate); }
        }


        //--------------------------------constructor-------------------------

        //בנאי סטטי שרץ בפעם הראשונה שפנינו למחלקה
        //בבנאי זה נאתחל את שעת ההתחלה לתאריך הנוכחי בו ארע הבנאי
        static TimeChecker()
        {
            startDate = DateTime.Now;
        }


        //-------------------------------functions--------------------------

        public static string getFullDate()
        {
            return DateTime.Now.ToLongTimeString();
        }
    }
}

```



## 06_Enum <a id="06_Enum"></a>
```csharp
using System;

namespace _06_Enum
{
    class Program
    {
        static void Main(string[] args)
        {
            WeekendHobies myWeekendHobies = WeekendHobies.Learning;
            Console.WriteLine($"this weekend I am planning {myWeekendHobies} and {WeekendHobies.Coding}");
        }
    }
}


/*
OUTPUT:
_____________________________________

this weekend I am planning Learning and Coding    
*/

```



## 06_Enum <a id="06_Enum"></a>
```csharp
namespace _06_Enum
{
    //by default every enum is represented by an int type
    //we can change it to ant whole number (not decimal)
    enum WeekendHobies:byte
    {
        Traveling=4,
        Coding,
        TV,
        Sleeping,
        Learning,
        Eating

    }
}

```



## Desktop <a id="Desktop"></a>
```csharp
using System;

/*
 ����� ��������  - function overloading
_________________________________________________
1. �� ��������� ������ ����� ����� ���� ��
2. �� ������� ����� ���� ���� ������� ���� �� ���� ���� ������� ��� ������ ������� �����
3. ��� ����� ������ ���� - �� ���� ����� ������
4. ���� ������� ����� - �� ������� �� ������   
     */
namespace _00_function_overloading
{
    class Program
    {
        static int GetAvg(int param1, int param2)
        {
            return (param1 + param2) / 2;
        }


        static decimal GetAvg(decimal param1, decimal param2)
        {
            return (param1 + param2) / 2;
        }

        static void Main(string[] args)
        {
            int grade1 = 100, grade2 = 95;
            decimal waterPrice1 = 12.5M, waterPrice2 = 7;

            decimal gradeAvg = GetAvg(grade1, grade2); 
            decimal priceAvg = GetAvg(waterPrice1, waterPrice2);

            Console.WriteLine($" grade1 is {grade1}\n grade2 is {grade2}");
            Console.WriteLine($" avg of grade1 & grade2 is {(grade1+grade2)/2}");
            Console.WriteLine($" avg of grade1 & grade2 is {(grade1 + grade2) / 2.0}");
            Console.WriteLine($" avg of grade1 & grade2 is {gradeAvg}");

            Console.WriteLine("---------------------------------------------");

            Console.WriteLine($" waterPrice1 is {waterPrice1}\n waterPrice2 is {waterPrice2}");
            Console.WriteLine($" avg of waterPrice1 & waterPrice2 is {(waterPrice1 + waterPrice2) / 2}");
            Console.WriteLine($" avg of waterPrice1 & waterPrice2 is {priceAvg}");
        }
    }
}


/*
 output:
__________________________________________
 grade1 is 100
 grade2 is 95
 avg of grade1 & grade2 is 97
 avg of grade1 & grade2 is 97.5
 avg of grade1 & grade2 is 97
---------------------------------------------
 waterPrice1 is 12.5
 waterPrice2 is 7
 avg of waterPrice1 & waterPrice2 is 9.75
 avg of waterPrice1 & waterPrice2 is 9.75
*/
```
