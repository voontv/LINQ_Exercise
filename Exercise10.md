## Aggregate
Được sử dụng khi ta gặp các dạng tính toán tích lũy.

## Method
```` cs
Aggregate<TSource,TAccumulate,TResult>(IEnumerable<TSource>, TAccumulate, Func<TAccumulate,TSource,TAccumulate>, Func<TAccumulate,TResult>)	
Aggregate<TSource,TAccumulate>(IEnumerable<TSource>, TAccumulate, Func<TAccumulate,TSource,TAccumulate>)	
Aggregate<TSource>(IEnumerable<TSource>, Func<TSource,TSource,TSource>)
````
## Example
```` cs
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
        }
    }
````

## All
Dùng để xác định tất cả các element trong 1 tập dữ liệu có cùng thỏa mãn một điều kiện nào đó mà ta muốn kiểm tra hay không.

## Method
```` cs
public static bool All<TSource> (this System.Collections.Generic.IEnumerable<TSource> source, Func<TSource,bool> predicate);
````

## Example
````cs
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
            foreach(var str in fruitsConvert)
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
            IEnumerable<char> charsConvert = chars.Cast<char>().OrderBy(ch => ch);
            foreach (var ch in charsConvert)
            {
                Console.WriteLine("{0}",ch);
            }
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
            foreach (var str in alls)
            {
                Console.WriteLine(str);
            }

            int[] numberEven = { 0, 2, 4, 6, 8 };
            int[] numberDivi5 = { 0, 5, 10, 60, 85 };

            IEnumerable<int> allNumbers = numberEven.Concat(numberDivi5);
            foreach (var number in allNumbers)
            {
                Console.WriteLine(number);
            }

            char[] charLower = { 'a', 'b', 'c', 'd', 'e' };
            char[] charUpper = { 'A', 'B', 'C', 'D', 'E' };

            IEnumerable<char> allChars = charLower.Concat(charUpper);
            foreach (var ch in allChars)
            {
                Console.WriteLine(ch);
            }
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

            Console.WriteLine("Count elemnt in fruits {0}", fruits.Count());
            Console.WriteLine("Count elemnt in fruits have length more 5 {0}", fruits.Count(fruit => fruit.Length > 5));
            Console.WriteLine("Count elemnt in numbers {0}", numbers.Count());
            Console.WriteLine("Count elemnt is Number Even in numbers {0}", numbers.Count(x => x % 2 == 0));

            var listBook = new List<Book> { new Book(1, "Java", "200"), new Book(3, "Python", "120"),
                                           new Book(4, "C#", "150"), new Book(8, "English", "210")};

            Console.WriteLine("Count element in listbook is {0}", listBook.Count());
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