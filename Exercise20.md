## Phân biệt Any với Contains
Any là kiểm tra 1 điều kiện cụ thể, còn Contans kiểm tra sự tồn tại của một đối tượng.

## Example
```cs
namespace Voontv
{
    class main
    {
        static void Main()
        {
            string[] fruits = { "apple", "mango", "orange", "passionfruit", "grape" };
            var anyLength = fruits.Any(x => x.Length > 5);
            var containsApple = fruits.Contains("apple");

            var numbers = new[] { 1, 3, 5, 12, 8, 19, 22 };
            var anyNotNull = numbers.Any();
            var contain12 = numbers.Contains(12);

            var listBooks = new List<Book> { new Book(1, "Java", "200"), new Book(3, "Python", "120"), new Book(4, "C#", "150"), new Book(8, "English", "210") };
            var anyBookId = listBooks.Any(x => x.MaBook > 18);
            var containsBook = listBooks.Contains(new Book(1, "Java", "200"), new BookCompare());
            Console.WriteLine(anyBookId + "  " + containsBook);
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
            if (Object.ReferenceEquals(book, null))
            {
                return 0;
            }

            return book.MaBook;
        }
    }
}
```