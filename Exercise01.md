Là kiểu dữ liệu mà biến tạo ra từ nó tham chiếu tới phương thức.
Cú pháp : [access modifier] delegate [return type] [delegate name]([parameters])
Kiểu dữ liệu này dùng khá linh động và giảm thiểu code, đã được sử dụng trong Kotlin trong chỗ sử dụng GSON để đọc dữ liệu từ file json, từ đó tạo các đối tượng dữ liệu phù hợp.
Example:
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
namespace Voontv
{
    public delegate List<T> CreateList<T>(T param1);
    class main
    {
        static void Main()
        {
            CreateList<string> testString = createdListFromString;
            foreach (var i in testString("Read document and answer"))
            {
                Console.WriteLine(i);
            }

            CreateList<int> testInt = createdListInt;
            foreach (var i in testInt(12))
            {
                Console.WriteLine(i);
            }

            CreateList<Book> testBook = createdListBook;
            foreach (var i in createdListBook(new Book(45,"Tenis")))
            {
                Console.WriteLine(i.MaBook +"    "+i.NameBook);
            }
        }

        public static List<string> createdListFromString(string input)
        {

            return (from i in Enumerable.Range(0, input.Length)
                    select input.Substring(i)).ToList();
        }

        public static List<int> createdListInt(int n)
        {

            return Enumerable.Range(0, n).ToList();
        }

        public static List<Book> createdListBook(Book book)
        {
            var listbook = new List<Book> { new Book(12, "Sport"), new Book(122, "IT"),
                new Book(134, "Sex"), new Book(314, "Java")};

            return listbook.Where(x => x.MaBook > book.MaBook).ToList();
            return listbook.Where(x => x.MaBook > book.MaBook).ToList();
        }
    }

    public class Book
    {
        private int maBook;
        private string nameBook;
        public int MaBook
        {
            get { return maBook; }
            set { maBook = value; }
        }
        public string NameBook
        {
            get { return nameBook; }
            set { nameBook = value; }
        }

        public Book(int createMabook, string createdName)
        {
            this.maBook = createMabook;
            this.nameBook = createdName;
        }
    }

}
