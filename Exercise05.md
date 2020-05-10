## Generis là gì ?
Là khi ta muốn khởi tạo ra các lớp, các hàm mà param và cách xử lý giống nhau nhưng chỉ khác
nhau ở kiểu dữ liệu và kiểu trả về (Trừ kiểu void).

## Tác dụng khi sử dụng Generis là gì ?
Giúp tái sử dụng mã nguồn, giúp code linh hoạt hơn. Có thể xử lý các phương thức xử lý 
giống nhau, cùng param chỉ khác kiểu dữ liệu.
#### Ví dụ bài toán tính độ dài của một input bất kỳ
Hướng giải quyết là ta viết hàm tham số đầu vào là input, sau đó chuyển sang kiểu string --> tính length, nhưng vấn đề đặt ra ở đây, mỗi input với mỗi kiểu khác nhau ta lại viết mỗi hàm với param
khác nhau, tới lúc này thì ta dùng generis là ổn nhất, code sẽ gọn gàng và linh hoạt.

## Các dạng Generis ?
Có 3 loại Generis
 a.Generis parameters
 b.Generis Class
 c.Generis Interface
 d.Generis Method

## Example:
````cs
using Microsoft.AspNetCore.Http;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Net.Http;
using System.Text;
namespace Voontv
{
    public delegate List<T> CreateList<T>(T param1);
    class main
    {
        static void Main()
        {
            Console.WriteLine("Length of input is string {0}", LengObject("Learn Java"));
            Console.WriteLine("Length of input is int {0}", LengObject(1234));
            Console.WriteLine("Length of input is double {0}", LengObject(12.787878787));

            BookGeneris<Book> bookGeneris = new BookGeneris<Book>();
            var book = bookGeneris.Save(new Book(123456, "Generis document"));
            Console.WriteLine("Id book : {0} , name book : {1}", book.MaBook, book.NameBook);
        }

        public static int LengObject<T>(T item)
        {
            return item.ToString().Length;
        }
    }

    interface BookBasic<T>
    {
        void Show(T item);
        T Save(T item);
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

    public class BookGeneris<T> : BookBasic<T>
    {
        public T Save(T item)
        {

            return item;
        }

        public void Show(T item)
        {
            Console.WriteLine("This book information {0} ", item);
        }
    }
}
````