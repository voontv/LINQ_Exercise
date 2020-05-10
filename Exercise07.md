## Từ khóa yield dùng để làm gì ?
Dùng để thông báo cho trình biên dịch biết rằng phương thức mà nó có mặt là một khối lặp. Nó được dùng với từ khóa break để báo kết thúc lặp hoặc sử dụng với từ khóa return để trả về giá trị mà khối lặp muốn thực hiện.

## Example:
```` cs
class main
    {
        static void Main()
        {
            var listnumber = new List<int> { 1, 5, 8, 9, 12, 34, 43, 17, 656, 232, 264, 18, 92, 19 };

            Console.WriteLine("Numbers Even in list");
            foreach (var i in NumberEven(listnumber))
            {
                Console.WriteLine(i);
            }

            Console.WriteLine("Three element first Divisibility 4 in list");
            foreach (var i in ThreeElementDivisibility(listnumber))
            {
                Console.WriteLine(i);
            }

            Console.WriteLine("Display string and break when char is Upper");
            foreach (var i in BreakWhenCharUpper("toi la toi, toi Muon mai la toi"))
            {
                Console.Write(i);
            }
        }

        public static IEnumerable<int> NumberEven(List<int> listnumber)
        {
            foreach (var i in listnumber)
            {
                if (i % 2 == 0)
                {
                    yield return i;
                }
            }
        }
        public static IEnumerable<char> BreakWhenCharUpper(string stringInput)
        {
            foreach (var i in stringInput)
            {
                if (Char.IsUpper(i))
                {
                    yield break;
                }
                yield return i;
            }
        }

        public static IEnumerable<int> ThreeElementDivisibility(List<int> listnumber)
        {
            var count = 0;
            foreach (var i in listnumber)
            {
                if (count >= 3)
                {
                    yield break;
                }

                if (i % 4 == 0)
                {
                    count++;
                    yield return i;
                }
            }
        }
    }
````