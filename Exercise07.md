## Từ khóa yield dùng để làm gì ?
Dùng khi giá trị phương thức mà chúng ta muốn trả về là IEnumerable. 

Nó được dùng với từ khóa break để báo kết thúc lặp hoặc sử dụng với từ khóa return để trả về giá trị mà khối lặp muốn thực hiện.

Khi ta sử dụng return thì ngay tại giá trị return về phương thức đó sẽ stop và không thực hiện bất kỳ lệnh nào phía sau. Còn đối với yield return thì ngược lại, nó trả về giá trị của đối tượng đang liệt kê và các lệnh phía sau nó vẫn tiếp tục thực hiện nếu có.

Khi sử dụng yield return thì nó rất có lợi khi runtime thì chương trình sẽ nhảy qua nhảy lại giữa phương thức "sử dụng yield return" và chỗ gọi phương thức đó. Đối với cách cũ khi muốn tạo ra 1 collection nào đó thì hầu hết ta cần phải tạo 1 biến local với kiểu dữ liệu mà mình muốn trả về, còn khi sử dụng yield return thì không cần nên cũng đỡ tốn bộ nhớ.
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