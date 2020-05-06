## Anonymous class là gì ?
Anonymous class là loại class mà các thuộc tính của nó là read-only. Nó không chứa bất kỳ
phương thức hoặc sự kiện hoặc bất kỳ thành viên nào khác.
Nó được khởi tạo bằng cách sử dụng từ khóa new và khởi tạo trực tiếp giá trị cho đối tượng.
Nó chỉ được sử dụng trong phạm vi phương thức nó được định nghĩa. Thông thường được sử dụng
trong các truy vấn của LINQ.

## Example:
```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
namespace Voontv
{

    class main
    {
        static void Main()
        {
            var Course = new
            {
                NameCourse = "Net Program",
                LengCourse = "five part",
                NameTeacher = "Vo Quang Hoa"
            };

            IList<Book> listbook = new List<Book> { new Book(12, "Sport"),
                new Book(122, "IT"),
                new Book(134, "Sex"),
                new Book(314, "Java"),
                new Book(512, "Tenis")};
            var books = from book in listbook
                        where book.NameBook.Length > 2
                        select new { Value = book.MaBook * 10, NewName = book.NameBook };

            foreach (var book in books)
            {
                Console.WriteLine(String.Join(" : ", book.NewName, book.Value));
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
}
```