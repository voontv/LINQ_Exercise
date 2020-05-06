## Delegate là gì ?
Là kiểu dữ liệu mà biến tạo ra từ nó tham chiếu tới phương thức. Nó có thể được sử dụng
để có thể tham chiếu tới bất cứ phương thức nào có cùng kiểu trả về và cùng cấu trúc các
parameters sử dụng.
Cú pháp : [access modifier] delegate [return type] [delegate name]([parameters])


## Example:
````cs
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
            foreach (var i in createdListBook(new Book(45, "Tenis")))
            {
                Console.WriteLine(i.MaBook + "    " + i.NameBook);
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
            var listbook = new List<Book> { new Book(12, "Sport"),
                new Book(122, "IT"), new Book(134, "Sex"),
                new Book(314, "Java")};

            return listbook.Where(x => x.MaBook > book.MaBook).ToList();
        }
    }

    public class Book
    {
        public int MaBook { get; set; }
        public string NameBook { get; set; }

        public Book(int createMabook, string createdName)
        {
            MaBook = createMabook;
            NameBook = createdName;
        }
    }

}
````