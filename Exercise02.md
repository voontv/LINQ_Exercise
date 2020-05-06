###Anonymous method là gì ?
Anonymous method là một loại phương thức không có tên chỉ có thân phương thức, nó được khai báo bởi từ khóa delegate

###Example :
```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
namespace Voontv
{
    public delegate int Sum(int param1);
    class main
    {
        static void Main()
        {
            Sum sumInt = delegate (int x) { return x * 3; };
            Func<int, double> func = (i) => (i * 1.0) / 10;

            Action test = () => Console.WriteLine("Anoymous Method");
            Action<string> testString = (s) => Console.WriteLine(s);
            Predicate<int> testInt = (i) => i > 20;

            Console.WriteLine(sumInt(5));
            Console.WriteLine(func(5));
            Console.WriteLine(testInt(5));
            test();
            testString("Learn Net Program");

        }

        public static int MulInt(Sum sum, int x)
        {
            return sum(x) * sum(x);
        }
    }
}
```