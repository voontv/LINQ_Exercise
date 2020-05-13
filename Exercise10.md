## Aggregate
Được sử dụng khi ta gặp các dạng tính toán tích lũy.

## Method
``` cs
Aggregate<TSource,TAccumulate,TResult>(IEnumerable<TSource>, TAccumulate, Func<TAccumulate,TSource,TAccumulate>, Func<TAccumulate,TResult>)	
Aggregate<TSource,TAccumulate>(IEnumerable<TSource>, TAccumulate, Func<TAccumulate,TSource,TAccumulate>)	
Aggregate<TSource>(IEnumerable<TSource>, Func<TSource,TSource,TSource>)
```
## Example
``` cs
 class main
    {
        static void Main()
        {
            var listNumber = new List<int> { 1, 5, 8, 9, 12, 34, 43, 17, 656, 232, 264, 18, 95, 19 };

            int numEven = listNumber.Aggregate(0, (countEven, next) => (next % 2 == 0) ? (countEven + 1) : countEven);

            Console.WriteLine("Count Even int listNumber {0}", numEven);

            int maxdivi5 = listNumber.Aggregate(listNumber[0],
                (max5, next) => (next > max5 && next % 5 == 0) ? next : max5,
                max => max * 1);

            Console.WriteLine("The number max and divisibility for 5", maxdivi5);

            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape" };

            string longestName = fruits.Aggregate(fruits[0], (longestStr, next) => next.Length > longestStr.Length ? next : longestStr,
                                fruit => fruit.ToUpper());
            //out put
            //Count Even int listNumber 7
            //The number max and divisibility for 5
        }
    }
```

## All
Dùng để xác định tất cả các element trong 1 tập dữ liệu có cùng thỏa mãn một điều kiện nào đó mà ta muốn kiểm tra hay không.

## Method
```cs
public static bool All<TSource> (this System.Collections.Generic.IEnumerable<TSource> source, Func<TSource,bool> predicate);
```

## Example
```cs
        static void Main()
        {
            var listNumber = new List<int> { 1, 5, 8, 9, 12, 34, 43, 17, 656, 232, 264, 18, 95, 19 };

            var allEven = listNumber.All(x => x % 2 == 0);

            Console.WriteLine("Check all number is number even {0}", allEven);

            var allDivi10 = listNumber.All(x => x % 10 != 0);

            Console.WriteLine("Check all number not divisibility for 10 {0}", allDivi10);

            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape" };

            var isStartChar = fruits.All(x => x.StartsWith("a"));
            var isContainsChar = fruits.All(x => x.Contains("a"));

            Console.WriteLine("Check all string start with char a {0}", isStartChar);
            Console.WriteLine("Check all string have character a {0}", isContainsChar);
            //out put
            //Check all number is number even False
            //Check all number not divisibility for 10 True
            //Check all string start with char a False
            //Check all string have character a True
        }
````

## Any
Dùng để xác định xem có 1 element trong 1 tập dữ liệu có cùng thỏa mãng một điều kiện nào đó mà ta muốn kiểm tra hay không.

Check 1 tập dữ liệu có chứa nội dung không (không null) ta dùng :
## Method
```` cs
public static bool Any<TSource> (this System.Collections.Generic.IEnumerable<TSource> source);
````

Check 1 tập dữ liệu có nội dung thỏa mãn điểu kiện nào đó ta muốn kiểm tra

```` cs
public static bool Any<TSource> (this System.Collections.Generic.IEnumerable<TSource> source, Func<TSource,bool> predicate);
````

## Example
````cs    
        static void Main()
        {
            var listA = new List<int> { };
            var listNumber = new List<int> { 1, 5, 8, 9, 12, 34, 43, 17, 656, 232, 264, 18, 95, 19 };

            var anyEven = listNumber.Any(x => x % 2 == 0);
            var checkListNumber = listNumber.Any();
            var checkListA = listA.Any();

            Console.WriteLine("Check listAr is not null {0}", checkListA);
            Console.WriteLine("Check listNumber is not null {0}", checkListNumber);
            Console.WriteLine("Check any number is number even {0}", anyEven);

            var allDivi10 = listNumber.Any(x => x % 10 == 0);

            Console.WriteLine("Check any number divisibility for 10 {0}", allDivi10);

            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape" };

            var isStartChar = fruits.Any(x => x.StartsWith("a"));

            Console.WriteLine("Check any string start with char a {0}", isStartChar);
            /*Out put
            Check listAr is not null False
            Check listNumber is not null True
            Check any number is number even True
            Check any number divisibility for 10 False
            Check any string start with char a True
             */
        }
````
## Append
Thêm phần tử vào cuối của tập hợp nhưng không làm thay đổi giá trị ban đầu của tập dữ liệu mà nó thêm vào.
(cái này đọc hiểu, nhưng không biết giải thích vậy đúng không)
## Method
```` cs
public static System.Collections.Generic.IEnumerable<TSource> Append<TSource> (this System.Collections.Generic.IEnumerable<TSource> source, TSource element);
````
## Example
````cs
        static void Main()
        {
            var listNumber = new List<int> { 1, 5, 8, 9};
            listNumber.Append(10);
            // Still same listNumber { 1, 5, 8, 9}
            Console.WriteLine(string.Join(",", listNumber));

            //Appear value 10 , but it is change a copy of listNumber
            Console.WriteLine(string.Join(",", listNumber.Append(10)));

            //listNewNumber is  { 1, 5, 8, 9, 10}
            var listNewNumber = listNumber.Append(10);
            Console.WriteLine(string.Join(",", listNewNumber));
        }
````

## Average
Tính trung bình cộng của 1 tập dữ liệu các giá trị số.

## Example
````cs
        static void Main()
        {
            var listNumber = new List<int> { 1, 5, 8, 9};
           
            Console.WriteLine("Average element listNumber {0}", listNumber.Average());

            var listDouble = new List<Double> { 1.9, 5.7, 8.4, 9.2 };

            Console.WriteLine("Average element listDouble {0}", listDouble.Average());

            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape" };
            Console.WriteLine("Average of length in fruits {0}", fruits.Average(s => s.Length));
        }
````

## Casts 
Chuyển các element trong tập dữ liệu sang kiểu được chỉ định.

## Example
````cs
        static void Main()
        {
            System.Collections.ArrayList fruits = new System.Collections.ArrayList();
            fruits.Add("mango");
            fruits.Add("apple");
            fruits.Add("lemon");

            IEnumerable<string> fruitsConvert = fruits.Cast<string>().OrderBy(str => str);
            Console.WriteLine("\n\rContent fruitsConvert");
            foreach (var str in fruitsConvert)
            {
                Console.WriteLine(str);
            }

            System.Collections.ArrayList numbers = new System.Collections.ArrayList();
            numbers.Add(1);
            numbers.Add(21);
            numbers.Add(4);
            numbers.Add(3);
            numbers.Add(43);
            IEnumerable<int> numbersConvert = numbers.Cast<int>().OrderBy(x => x);
            Console.WriteLine("\n\rContent numbersConvert");
            foreach (var i in numbersConvert)
            {
                Console.WriteLine(i);
            }

            System.Collections.ArrayList chars = new System.Collections.ArrayList();
            chars.Add('c');
            chars.Add('h');
            chars.Add('a');
            chars.Add('r');
            chars.Add('s');

            Console.WriteLine("\n\rContent charsConvert");
            IEnumerable<char> charsConvert = chars.Cast<char>().OrderBy(ch => ch);
            foreach (var ch in charsConvert)
            {
                Console.WriteLine("{0}", ch);
            }
            /*Out put
            Content fruitsConvert
            apple
            lemon
            mango

            Content numbersConvert
            1
            3
            4
            21
            43

            Content charsConvert
            a
            c
            h
            r
            s
             */
        }

````

## Concat
Dùng để nối 2 tập dữ liệu tương đương nhau

## Example
````cs
                static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape" };
            string[] drinks = { "coca", "pepsi", "orange", "milk", "alcohol" };

            IEnumerable<string> alls = fruits.Concat(drinks);
            Console.WriteLine("\n\rConcat fruits and drinks");
            foreach (var str in alls)
            {
                Console.WriteLine(str);
            }

            int[] numberEven = { 0, 2, 4, 6, 8 };
            int[] numberDivi5 = { 0, 5, 10, 60, 85 };

            IEnumerable<int> allNumbers = numberEven.Concat(numberDivi5);
            Console.WriteLine("\n\rConcat numberEven and numberDivi5");
            foreach (var number in allNumbers)
            {
                Console.WriteLine(number);
            }

            char[] charLower = { 'a', 'b', 'c', 'd', 'e' };
            char[] charUpper = { 'A', 'B', 'C', 'D', 'E' };

            Console.WriteLine("\n\rConcat charLower and charUpper");
            IEnumerable<char> allChars = charLower.Concat(charUpper);
            foreach (var ch in allChars)
            {
                Console.WriteLine(ch);
            }
            /*
            Concat fruits and drinks
            apple
            mango
            orange
            passionfruit
            grape
            coca
            pepsi
            orange
            milk
            alcohol

            Concat numberEven and numberDivi5
            0
            2
            4
            6
            8
            0
            5
            10
            60
            85

            Concat charLower and charUpper
            a
            b
            c
            d
            e
            A
            B
            C
            D
            E
             */
        }
````

## Contains
Dùng để xác định xem 1 tập dữ liệu có chứa một nội dung cần xác định không.

Xác định trong tập hợp có chứa một nội dung cần xác định không, bằng các bộ so sánh mặt định có sẵn ta dùng :
````cs
public static bool Contains<TSource> (this System.Collections.Generic.IEnumerable<TSource> source, TSource value);
````

Xác định trong tập hợp có chứa một nội dung cần xác định không, bằng các bộ so sánh do ta định nghĩa :
````cs
public static bool Contains<TSource> (this System.Collections.Generic.IEnumerable<TSource> source, TSource value, System.Collections.Generic.IEqualityComparer<TSource> comparer);
````
## Example
````cs
namespace Voontv
{
    class main
    {
        static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape" };           
            int[] numberEven = { 0, 2, 4, 6, 8 };

            Console.WriteLine(fruits.Contains("orange"));
            Console.WriteLine(numberEven.Contains(9));

            var listBook = new List<Book> { new Book(1, "Java", "200"), new Book(3, "Python", "120"),
                                           new Book(4, "C#", "150"), new Book(8, "English", "210")};

            var bookA = new Book(1, "JAVA", "600");
            var bookB = new Book(8, "javaa", "200");
            var mydefineCompare = new BookCompare();
            Console.WriteLine("Use contain find bookA appear in listboook is {0}", listBook.Contains(bookA, mydefineCompare));
            Console.WriteLine("Use contain find bookB appear in listboook is {0}", listBook.Contains(bookB, mydefineCompare));
            /*Out put
            true
            false
            true
            false
            */
        }
    }


    public class Book
    {
        public int MaBook { get; set; }
        public string NameBook { get; set; }

        public string Value { get; set; }
        public Book(int createMabook, string createdName, string value)
        {
            MaBook = createMabook;
            NameBook = createdName;
            Value = value;
        }
    }

    class BookCompare : IEqualityComparer<Book>
    {
        public bool Equals(Book x, Book y)
        {
            if(Object.ReferenceEquals(x, y))
            {
                return true;
            }

            if(Object.ReferenceEquals(x, null) || Object.ReferenceEquals(y, null))
            {
                return false;
            }

            return x.MaBook == y.MaBook && x.NameBook.ToLower().Equals(y.NameBook.ToLower());
        }

        public int GetHashCode([DisallowNull] Book obj)
        {
            throw new NotImplementedException();
        }
    }
   
}
````

## Count
Điếm số phần tử trong 1 tập hợp, có thể có điều kiện đi cùng.

Nếu chỉ điếm số phần tử trong 1 tập hợp sử dụng :
````cs
public static int Count<TSource> (this System.Collections.Generic.IEnumerable<TSource> source);
````
Điếm kèm theo một điều kiện nào đó sử dụng :
````cs
public static int Count<TSource> (this System.Collections.Generic.IEnumerable<TSource> source, Func<TSource,bool> predicate);
````
## Example
````cs
namespace Voontv
{
    class main
    {
        static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape" };
            int[] numbers = { 0, 16, 7, 2, 41, 63, 8 };
            //out put 5
            Console.WriteLine("Count elemnt in fruits {0}", fruits.Count());
            //out put 2
            Console.WriteLine("Count elemnt in fruits have length more 5 {0}", fruits.Count(fruit => fruit.Length > 5));
            //out put 7
            Console.WriteLine("Count elemnt in numbers {0}", numbers.Count());
            //out put 4
            Console.WriteLine("Count elemnt is Number Even in numbers {0}", numbers.Count(x => x % 2 == 0));

            var listBook = new List<Book> { new Book(1, "Java", "200"), new Book(3, "Python", "120"),new Book(4, "C#", "150"), new Book(8, "English", "210")};
            //out put 4
            Console.WriteLine("Count element in listbook is {0}", listBook.Count());
            //out put 2
            Console.WriteLine("Count element in listbook have id > 3 is {0}", listBook.Count(book => book.MaBook > 3));
        }
    }


    public class Book
    {
        public int MaBook { get; set; }
        public string NameBook { get; set; }

        public string Value { get; set; }
        public Book(int createMabook, string createdName, string value)
        {
            MaBook = createMabook;
            NameBook = createdName;
            Value = value;
        }
    }
}
````

## DefaultIfEmpty
trả về giá trị của các phần tử trong 1 tập hợp hoặc trả về giá trị mặc định chỉ định hoặc giá trị mặc định của tham số có trong tập hợp nếu tập hợp là null

## Example
````cs
    class main
    {
        static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape" };
            int[] numbers = { 0, 16, 7, 2, 41, 63, 8 };
            int[] numberCreat = new int[] { };
            float[] floatCreat = new float[] { };
            //display all elemnt in fruits
            foreach (var str in fruits.DefaultIfEmpty("not fruit"))
            {
                Console.WriteLine(str);
            }
            //display all elemnt in numbers
            foreach (var i in numbers.DefaultIfEmpty(-1))
            {
                Console.WriteLine(i);
            }
            //out put -1
            foreach (var i in numberCreat.DefaultIfEmpty(-1))
            {
                Console.WriteLine(i);
            }
            //out put 0
            foreach (var ch in floatCreat.DefaultIfEmpty())
            {
                Console.WriteLine(ch);
            }
        }
    }
````
## Distinct
Trả về một tập hợp mới bằng cách các phần tử giống nhau chỉ giữ lại 1 phần tử.
Nếu so sánh để giữ lại 1 phần tử đối với các phần tử giống nhau bằng các so sánh mặc định sử dụng :
````cs
public static System.Collections.Generic.IEnumerable<TSource> Distinct<TSource> (this System.Collections.Generic.IEnumerable<TSource> source);
````
Nếu so sánh để giữ lại 1 phần tử đối với các phần tử giống nhau bằng so sánh do mình định nghĩa sử dụng :
````cs
public static System.Collections.Generic.IEnumerable<TSource> Distinct<TSource> (this System.Collections.Generic.IEnumerable<TSource> source, System.Collections.Generic.IEqualityComparer<TSource> comparer);
````

## Example
````cs
namespace Voontv
{
    class main
    {
        static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape", "apple", "orange" };
            int[] numbers = { 0, 2, 1, 16, 8, 8, 0, 1, 16 };
            //out put { "apple", "mango", "orange", "passionfruit", "grape"};
            foreach(var str in fruits.Distinct())
            {
                Console.WriteLine(str);
            }
            //out put { 0, 2, 1, 16, 8};
            foreach (var i in numbers.Distinct())
            {
                Console.WriteLine(i);
            }
            var listBook = new List<Book> { new Book(1, "Java", "200"), new Book(3, "Python", "120"),
                                            new Book(4, "C#", "150"), new Book(8, "English", "210"),
                                            new Book(1, "Java", "600"), new Book(8, "java", "200")};
            var bookCompare = new BookCompare();
            var listBookDistinct = listBook.Distinct(bookCompare);

            foreach (var book in listBookDistinct)
            {
                Console.WriteLine("Book have id {0} - name {1} - value {2}", book.MaBook, book.NameBook, book.Value);
            }
        }
    }


    public class Book
    {
        public int MaBook { get; set; }
        public string NameBook { get; set; }

        public string Value { get; set; }
        public Book(int createMabook, string createdName, string value)
        {
            MaBook = createMabook;
            NameBook = createdName;
            Value = value;
        }
    }

    class BookCompare : IEqualityComparer<Book>
    {
        public bool Equals(Book x, Book y)
        {
            if (Object.ReferenceEquals(x, y))
            {
                return true;
            }

            if (Object.ReferenceEquals(x, null) || Object.ReferenceEquals(y, null))
            {
                return false;
            }

            return x.MaBook == y.MaBook && x.NameBook.Equals(y.NameBook);
        }

        public int GetHashCode(Book book)
        {
            if(Object.ReferenceEquals(book, null))
            {
                return 0;
            }

            return book.MaBook;
        }
    }

}
````

## ElementAt
Trả về giá trị của 1 phần tử tại 1 vị trí trong tập hợp, (tính từ index 0).

## Example
````cs
namespace Voontv
{
    class main
    {
        static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape", "apple", "orange" };
            int[] numbers = { 0, 2, 1, 16, 8, 8, 0, 1, 16 };
            var listBook = new List<Book> { new Book(1, "Java", "200"), new Book(3, "Python", "120"),
                                            new Book(4, "C#", "150"), new Book(8, "English", "210"),
                                            new Book(1, "JAVA", "600"), new Book(8, "java", "200")};

            //out put passionfruit
            Console.WriteLine("name fruit at index 3 {0}", fruits.ElementAt(3));
            //out put 0
            Console.WriteLine("number at index 6 {0}", numbers.ElementAt(6));
            //out put Book(4, "C#", "150")
            Console.WriteLine("book at index 2 have id {0} - name {1} - value {2}", listBook.ElementAt(2).MaBook,
                listBook.ElementAt(2).NameBook, listBook.ElementAt(2).Value);
        }
    }


    public class Book
    {
        public int MaBook { get; set; }
        public string NameBook { get; set; }

        public string Value { get; set; }
        public Book(int createMabook, string createdName, string value)
        {
            MaBook = createMabook;
            NameBook = createdName;
            Value = value;
        }
    }
}
````

## Except 
Dùng để trả về phần tử của một tập hợp này không xuất hiện trong tập kia.

Nếu so sánh các phần tử trong các tập để tìm ra kết quả bằng các so sánh mặc định sử dụng :
````cs
public static System.Collections.Generic.IEnumerable<TSource> Except<TSource> (this System.Collections.Generic.IEnumerable<TSource> first, System.Collections.Generic.IEnumerable<TSource> second);
````
Nếu so sánh các phần tử trong các tập để tìm ra kết quả bằng so sánh do mình định nghĩa sử dụng :
````cs
public static System.Collections.Generic.IEnumerable<TSource> Except<TSource> (this System.Collections.Generic.IEnumerable<TSource> first, System.Collections.Generic.IEnumerable<TSource> second, System.Collections.Generic.IEqualityComparer<TSource> comparer);
````
## Example
````cs
namespace Voontv
{
    class main
    {
        static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape", "apple", "orange" };
            string[] fruitSelects = { "apple", "mango" };
            int[] numbers = { 0, 2, 1, 16, 8, 8, 0, 1, 16 };
            int[] numbersA = { 0, 1, 16 };
            var listBook = new List<Book> { new Book(1, "Java", "200"), new Book(3, "Python", "120"),
                                            new Book(4, "C#", "150"), new Book(8, "English", "210"),
                                            new Book(1, "JAVA", "600"), new Book(8, "java", "200")};
            var listBookCompare = new List<Book> { new Book(1, "JavA", "600") };

            Console.WriteLine("element don't appears in fruitSelect");
            //out put  { "orange", "passionfruit", "grape"};
            foreach(var fruit in fruits.Except(fruitSelects))
            {
                Console.WriteLine(fruit);
            }

            Console.WriteLine("element don't appears in numbersA");
            //out put  {2, 8}
            foreach (var number in numbers.Except(numbersA))
            {
                Console.WriteLine(number);
            }

            Console.WriteLine("element don't appears in listBookCompare");
            /*out put
            {Book(3, "Python", "120"),Book(4, "C#", "150"), new Book(8, "English", "210"), new Book(8, "java", "200")};
            */ 
            foreach(var book in listBook.Except(listBookCompare, new BookCompare()))
            {
                Console.WriteLine("book have id {0} - name {1} - value {2}", book.MaBook, book.NameBook, book.Value);
            }
        }
    }


    public class Book
    {
        public int MaBook { get; set; }
        public string NameBook { get; set; }

        public string Value { get; set; }
        public Book(int createMabook, string createdName, string value)
        {
            MaBook = createMabook;
            NameBook = createdName;
            Value = value;
        }
    }

    class BookCompare : IEqualityComparer<Book>
    {
        public bool Equals(Book x, Book y)
        {
            if (Object.ReferenceEquals(x, y))
            {
                return true;
            }

            if (Object.ReferenceEquals(x, null) || Object.ReferenceEquals(y, null))
            {
                return false;
            }

            return x.MaBook == y.MaBook && string.Equals(x.NameBook.ToLower(), y.NameBook.ToLower());
        }

        public int GetHashCode(Book book)
        {
            if (Object.ReferenceEquals(book, null))
            {
                return 0;
            }

            return book.MaBook;
        }
    }
}
````

## First
Trả về phần tử đầu tiên của một tập hợp, hoặc trả về phần tử đầu tiên trong tập hợp thỏa mản một điều kiện nào đó.

## Example
````cs
        static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape", "apple", "orange" };
            int[] numbers = { 0, 2, 1, 16, 8, 8, 0, 1, 16 };
            //out put "apple"
            Console.WriteLine("First element of fruits {0} ", fruits.First());
            //out put "orange"
            Console.WriteLine("First element of fruits have length > 5 {0} ", fruits.First(x => x.Length > 5));
            //out put 0
            Console.WriteLine("First element of numbers {0} ", numbers.First());
            //out put 16
            Console.WriteLine("First element of numbers and > 10 {0} ", numbers.First(x => x > 10));
        }
````

## FirstOrDefault 
Có chức năng như **First** , nhưng khi kết quả trả về là null thì nó sẽ trả về giá trị mặc định của kiểu dữ liệu tập hợp đó.

```cs
        static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape", "apple", "orange" };
            int[] numbers = { 0, 2, 1, 16, 8, 8, 0, 1, 16 };
            int[] numbersCreated = { };
            Console.WriteLine("First element of fruits {0} ", fruits.FirstOrDefault());
            Console.WriteLine("First element of fruits have length > 30 {0} --", fruits.FirstOrDefault(x => x.Length > 30));
            //out put 0
            Console.WriteLine("First element of numbersCreated {0} ", numbersCreated.FirstOrDefault());
            Console.WriteLine("First element of numbers and > 10 {0} ", numbers.FirstOrDefault(x => x > 10));
        }
```

## Intersect
Trả về các phần tử chung của 2 tập hợp.
## Example
````cs
    class main
    {
        static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape", "apple", "orange" };
            string[] fruitsAndDrink = { "coca", "mango", "pepsi", "passionfruit", "alcohol", "apple", "orange" };
            int[] numbersB = { 0, 2, 1, 16, 8, 8, 0, 1, 16 };
            int[] numbersA = { 0, 3,65, 89, 12, 82 };

            Console.WriteLine("Intersect elements of fruits and fruitsAndDrink");
            //out put { "apple", "mango", "orange", "passionfruit" };
            foreach(var ele in fruitsAndDrink.Intersect(fruits))
            {
                Console.WriteLine(ele);
            }

            Console.WriteLine("Intersect elements of numbersA and numbersB");
            //out put {0}
            foreach (var ele in numbersA.Intersect(numbersB))
            {
                Console.WriteLine(ele);
            }
        }
    }
````
## Last
Trả về phần tử cuối cùng của một tập hợp, hoặc trả về phần tử cuối cùng của tập hợp thỏa mản một điều kiện nào đó.

## Example
````cs
        static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape", "apple", "orange" };
            int[] numbers = { 0, 2, 1, 16, 8, 8, 0, 1, 16 };
            //out put orange
            Console.WriteLine("Last element of fruits {0} ", fruits.Last());
            //out put orange
            Console.WriteLine("Last element of fruits have length > 5 {0} ", fruits.Last(x => x.Length > 5));
            //out put 16
            Console.WriteLine("Last element of numbers {0} ", numbers.Last());
            //out put 16
            Console.WriteLine("Last element of numbers and > 10 {0} ", numbers.Last(x => x > 10));
        }
````

## LastOrDefault 
Có chức năng như **Last** , nhưng khi kết quả trả về là null thì nó sẽ trả về giá trị mặc định của kiểu dữ liệu của tập hợp đó.

```cs
        static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape", "apple", "orange" };
            int[] numbers = { 0, 2, 1, 16, 8, 8, 0, 1, 16 };
            int[] numbersCreated = { };
            Console.WriteLine("Last element of fruits {0} ", fruits.LastOrDefault());
            //out put ""
            Console.WriteLine("Last element of fruits have length > 30 {0} --", fruits.LastOrDefault(x => x.Length > 30));
            //out put 0
            Console.WriteLine("Last element of numbersCreated {0} ", numbersCreated.LastOrDefault());
            Console.WriteLine("Last element of numbers and > 10 {0} ", numbers.LastOrDefault(x => x > 10));
        }
```

## Max
Xác định giá trị lớn nhất trong một tập hợp
## Min
Xác định giá trị nhỏ nhất trong một tập hợp
## Sum
Tổng các giá trị trong tập hợp
## Example
````cs
        static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape", "apple", "orange" };
            int[] numbers = { 0, 2, 1, 16, 8, 8, 0, 1, 16 };
            //out put max 16, min 0, sum 52
            Console.WriteLine("In numbers max is {0} - Min is {1} - Sum is {2}", numbers.Max(), numbers.Min(),numbers.Sum());
            //out put max length 12, min length 5, sum Length 44
            Console.WriteLine("In fruits , name fruits have max Length is {0} - Min Length is {1} - Sum Length is {2}",
                fruits.Max(str=>str.Length), fruits.Min(str => str.Length), fruits.Sum(str => str.Length));          
        }
````

## OfType
Chọn các phần tử tùy theo khả năng chuyển dữ liệu của nó sáng một kiểu dữ liệu nào đó.
## Example
````cs
        static void Main()
        {
            ArrayList item = new ArrayList();
            item.Add("102103061151");
            item.Add("102103061152");
            item.Add("102103061153");
            item.Add("102103061154");
            item.Add(18);
            item.Add(18);
            item.Add(19);
            item.Add(20);

            Console.WriteLine("Code Student is a string in list item, this is list code student");
            //out put {"102103061151", "102103061152","102103061153","102103061154"}
            foreach(var str in item.OfType<string>())
            {
                Console.WriteLine(str);
            }

            Console.WriteLine("Age Student is a int in list item, this is list age student");
            //out put {18, 18,19,20}
            foreach (var str in item.OfType<int>())
            {
                Console.WriteLine(str);
            }
        }
````

## OrderBy
Sắp xếp các phần tử của 1 tập hợp tăng dần theo một khóa nào đó.
## OrderByDescending
Sắp xếp các phần tử của 1 tập hợp giảm dần theo một khóa nào đó.
## Example
````cs
    class main
    {
        static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape", "apple", "orange", "123", "456" };
            IEnumerable<string> fruitsAscending = fruits.OrderBy(x => x);
            IEnumerable<string> fruitsDescending = fruits.OrderByDescending(x => x);

            Console.WriteLine("Ascending");
            foreach(var fruit in fruitsAscending)
            {
                Console.WriteLine(fruit);
            }

            Console.WriteLine("\n\rDescending");
            foreach (var fruit in fruitsDescending)
            {
                Console.WriteLine(fruit);
            }
        }
    }
````

## Repeat
Tạo ra một tập dữ liệu từ một giá trị được lặp lại n lần.
## Example
````cs
//create IEnumerable have 10 string orange
IEnumerable<string> fruitsRepeat = Enumerable.Repeat("orange", 10);
````

## Select
Tham chiếu các giá trị dựa vào 1 hàm biến đổi nào đó.
## Example
````cs
        static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape", "apple", "orange", "123", "456" };

            IEnumerable<bool> fruitsCheckStart = fruits.Select(x => x[0] == 'a');
            foreach (var fruit in fruitsCheckStart)
            {
                Console.WriteLine(fruit);
            }
        }
````

## Single
Trả về giá phần tử duy nhất thỏa mãn một điều kiện nào đó. Nếu không có phần tử thỏa mãn hoặc nó không phải duy nhất sẽ trả về Exception
## Example
````cs
class main
    {
        static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape", "apple", "orange", "123", "456" };
            try
            {
                //out put "passionfruit"
                var fruit = fruits.Single(str => str.Length > 10);
                Console.WriteLine(fruit);
            }
            catch(Exception)
            {
                Console.WriteLine("Not have element same request");
            }
            //"Not have element same request" vì có nhiều hơn 1 phần tử thỏa mãn
            try
            {
                var fruit = fruits.Single(str => str.Length > 5);
                Console.WriteLine(fruit);
            }
            catch (Exception)
            {
                Console.WriteLine("Not have element same request");
            }
            
        }
    }
````

## SingleOrDefault
Giống như Single nhưng khác với Single ở 1 điểm đó là nếu nếu tập hợp null thì trả về giá trị mặc định của kiểu dữ liệu của phần tử trong tập hợp.
## Example
````cs
        static void Main()
        {
            int[] numbers = { 2, 3, 5, 7, 9, 11 };
            int[] numberAs = {};
            //out put "Not have element same request" vì có nhiều hơn 1 phần tử thỏa mãn
            try
            {
                var number = numbers.SingleOrDefault(x => x > 5);
                Console.WriteLine(number);
            }
            catch(Exception)
            {
                Console.WriteLine("Not have number same request");
            }

            //out put "Not have element same request" vì có nhiều hơn 1 phần tử thỏa mãn
            try
            {
                var numberA = numberAs.Single(x => x > 5);
                Console.WriteLine(numberA);
            }
            catch(Exception)
            {
                Console.WriteLine("Not have number same request");
            }

            var numberB = numberAs.SingleOrDefault(x => x > 5);
            Console.WriteLine(numberB);
        }
````

## Skip
Bỏ qua n phần tử từ phần tử tính từ phần tử tiên, trả về các phần tử còn lại có trong tập hợp. (n là tham số đầu vào của method)
## Example
````cs
        static void Main()
        {
            int[] numbers = { 2, 3, 5, 7, 9, 11 };
            int[] numberAs = { };

            foreach (var number in numbers.Skip(2))
            {
                Console.WriteLine(number);
            }

            //out put
            //5
            //7
            //9
            //11
        }

````
## Take
Trả về n phần tử kể từ phần tử đầu tiên của tập hợp (n là tham số đầu vào của method)
## Example
````cs
        static void Main()
        {
            int[] numbers = { 2, 3, 5, 7, 9, 11 };
            int[] numberAs = { };

            foreach (var number in numbers.Take(2))
            {
                Console.WriteLine(number);
            }

            //out put
            //2
            //3
        }
````

## ThenBy
Thực hiện sắp xếp phụ theo thứ tự tăng dần
## Example
````cs
namespace Voontv
{
    class main
    {
        static void Main()
        {
            var listBook = new List<Book> { new Book(1, "Java", "200"), new Book(3, "Python", "120"),
                                            new Book(4, "C#", "150"), new Book(8, "English", "210"),
                                            new Book(1, "JAVA", "600"), new Book(8, "java", "200")};
            var booksThenBy = listBook.OrderBy(book => book.NameBook.Length).ThenBy(book => book.MaBook);
            /*out put
                book have id 4 - name C# - value 150
                book have id 1 - name Java - value 200
                book have id 1 - name JAVA - value 600
                book have id 8 - name java - value 200
                book have id 3 - name Python - value 120
                book have id 8 - name English - value 210
             */
            foreach (var book in booksThenBy)
            {
                Console.WriteLine("book have id {0} - name {1} - value {2}", book.MaBook, book.NameBook, book.Value);
            }
        }
    }


    public class Book
    {
        public int MaBook { get; set; }
        public string NameBook { get; set; }

        public string Value { get; set; }
        public Book(int createMabook, string createdName, string value)
        {
            MaBook = createMabook;
            NameBook = createdName;
            Value = value;
        }
    }
}
````

## ThenByDescending
Thực hiện sắp xếp phụ theo thứ tự giảm dần
## Example
````cs
namespace Voontv
{
    class main
    {
        static void Main()
        {
            var listBook = new List<Book> { new Book(1, "Java", "200"), new Book(3, "Python", "120"),
                                            new Book(4, "C#", "150"), new Book(8, "English", "210"),
                                            new Book(1, "JAVA", "600"), new Book(8, "java", "200")};
            var booksThenByDes = listBook.OrderBy(book => book.NameBook.Length).ThenByDescending(book => book.MaBook);
            /*out put
                book have id 4 - name C# - value 150
                book have id 8 - name java - value 200
                book have id 1 - name Java - value 200                
                book have id 1 - name JAVA - value 600                
                book have id 3 - name Python - value 120
                book have id 8 - name English - value 210
             */
            foreach (var book in booksThenByDes)
            {
                Console.WriteLine("book have id {0} - name {1} - value {2}", book.MaBook, book.NameBook, book.Value);
            }
        }
    }


    public class Book
    {
        public int MaBook { get; set; }
        public string NameBook { get; set; }

        public string Value { get; set; }
        public Book(int createMabook, string createdName, string value)
        {
            MaBook = createMabook;
            NameBook = createdName;
            Value = value;
        }
    }
}
````
## ToArray
Tạo một mảng từ 1 IEnumerable
## Example
````cs
    string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape", "apple", "orange" };
    var fruitsArray = fruits.Distinct().ToArray();
````

## ToDictionary 
Tạo một **````cs Dictionary<key, value> ````** từ một IEnumerable
## Example
````cs
        static void Main()
        {
            var listBook = new List<Book> { new Book(1, "Java", "200"), new Book(3, "Python", "120",
                                            new Book(4, "C#", "150"), new Book(5, "English", "210"),
                                            new Book(6, "C++", "600"), new Book(8, "Kotlin", "200")};
            Dictionary<int, Book> bookDictionary = listBook.Distinct().ToDictionary(x => x.MaBook);
            foreach (var book in bookDictionary)
            {
                Console.WriteLine(book.Key + "  name  " + book.Value.NameBook +" value "+book.Value.Value);
            }
        }
````

## Union
Tạo ra 1 tập hợp gồm có các phần tử phải tồn tại ở 1 trong 2 tập hợp ban đầu.
## Example
````cs
    int[] numbers1 = { 6, 77, 6, 1, 9, 11, 11, 18, 9 };
    int[] numbers2 = { 6, 8, 77, 12, 18, 7 };
    var numbers = numbers1.Union(numbers2);
    //numbers = {6, 77, 1, 9, 11, 18, 8, 12, 7}
````

## Where
Lọc phần tử cho 1 tập hợp dựa thỏa 1 điều kiện nào đó.
## Example
````cs
    int[] numbers1 = { 6, 77, 6, 1, 9, 11, 11, 18, 9 };

    var numbers = numbers1.Where(x => x > 10);
    //numbers = {77, 11, 11, 18, 12}
````
