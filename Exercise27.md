## Let dùng để làm gì
Dùng để lưu trữ kết quả của biểu thức con trong biểu thức truy vấn để xử dụng tiếp trong mệnh đề tiếp theo.

## Example
```cs
        static void Main(string[] args)
        {
            string[] strings =
            {
                "A penny saved is a penny earned.",
                "The early bird catches the worm.",
                "The pen is mightier than the sword."
            };

           //tim tu bat dau bang nguyen am
            var earlyBirdQuery =
                from sentence in strings
                let words = sentence.Split(' ')
                from word in words
                let w = word.ToLower()
                where w[0] == 'a' || w[0] == 'e'
                    || w[0] == 'i' || w[0] == 'o'
                    || w[0] == 'u'
                select word;

            var upperWord =
                from sentence in strings
                let words = sentence.Split(' ')
                from word in words
                where (Char.IsUpper(word[0]) == true)
                select word;

            // Execute the query.
            foreach (var v in earlyBirdQuery)
            {
                Console.WriteLine("\"{0}\" starts with a vowel", v);
            }

            Console.WriteLine("\r\n Word is upper in list string");
            foreach (var str in upperWord)
            {
                Console.WriteLine(str);
            }

            var listBook = new List<Book> { new Book(1, "Java", 200), new Book(3, "Python", 120),
                                            new Book(4, "C#", 150), new Book(8, "English", 210),
                                            new Book(1, "Java", 600), new Book(8, "Java", 300)};
            var letbook = from book in listBook
                          group book.Value by book.NameBook into groupBook
                          let countGroup = groupBook.Count()
                          select new
                          {
                              name = groupBook.Key,
                              numberBook = countGroup
                          };
            foreach(var gr in letbook)
            {
                Console.WriteLine("group {0} number in group {1} ", gr.name, gr.numberBook);
            }
            
        }
```
