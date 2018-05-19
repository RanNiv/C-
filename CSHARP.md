  * [Chapter 1](#00_Basic string and debugging)
  * [Chapter 2](#06_loop exersice)



## Day 01 - 11.05.2018 <a id="Day 01 - 11.05.2018"></a>
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



## Day 01 - 11.05.2018 <a id="Day 01 - 11.05.2018"></a>
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



## 00_Basic string and debugging <a id="00_Basic string and debugging"></a>
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



## 01_Mul function example <a id="01_Mul function example"></a>
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



## 03_Short conditation <a id="03_Short conditation"></a>
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



## 04_switch case <a id="04_switch case"></a>
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



## 05_Foreach loop <a id="05_Foreach loop"></a>
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



## 06_loop exersice <a id="06_loop exersice"></a>
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



## 10_Nested loop exercise <a id="10_Nested loop exercise"></a>
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
