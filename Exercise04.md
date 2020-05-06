###Extension method là gì ?
Extension method đã giống như trong kotlin đã được giới thiệu, nó là phần mở rộng của 1 class 
nào đó, như trong kotlin ta có thể mở rộng thêm vài phương thức mới cho String nếu ta muốn
(trong trường hợp một xử lý nào đó thường được dùng lặp đi lặp lại, nhưng không có trong
phương thức có sẵn của lớp string), tương tự như kotlin nhưng trong C# nó khác nhau ở chỗ nó phải là
static Class, static method và sử dụng từ khóa this trước đối tượng muốn Extension method:

###Example:
```Cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Text.RegularExpressions;

namespace Voontv
{

    class main
    {
        static void Main()
        {
            string s = "teacher is very hard. i must be carefully";
            string s2 = "Toi la toi. Khong ai 123dfdhh a,fhđfhkd 3343hdhfdfha 32";
            int num = 5;
            Console.WriteLine(s.ExtendsionMethod());
            Console.WriteLine(s2.SumInt());
            Console.WriteLine("Method pow for type int {0}", num.PowInt(3));
        }

    }

    public static class ExtendsionClass
    {
        public static string ExtendsionMethod(this string s)
        {

            return Regex.Replace(s, @"((^\w)|(\.\s\w))", m =>
            {
                string s = m.ToString();
                foreach (char ch in s)
                {
                    if (Char.IsLetter(ch))
                    {
                        s = s.Replace(ch, Char.ToUpper(ch));
                    }
                }
                return s;
            });
        }

        public static int SumInt(this string s)
        {
            var test = Regex.Match(s, @"(\d+)");
            return Regex.Matches(s, @"(\d+)").Sum(x => int.Parse(x.ToString()));
        }

        public static int PowInt(this int n, int m)
        {
            var pow = 1;

            for (var i = 0; i < m; i++)
            {
                pow *= n;
            }

            return pow;
        }
    }
}
```