## Đề xuất 5 cách để chương trình thực hiện đúng như ý muốn
```cs
        static void Main()
        {
            var badwords = new[] { "dkm", "tsbm", "dbrr", "dm" };

            IEnumerable<string> words = "Hello dbrr, nice you see you dm"
                                .Split(' ', ',');

            // Loại bỏ các từ trong danh sách badword

            //C1
            words = words.Where(x => !(badwords.FirstOrDefault(y => y == x) == x));            

            //C2
            words = words.Where(x => !badwords.Contains(x));

            //C3
            words = words.Except(badwords);

            words = words.Where(x => !(badwords.Count(y => y == x) >= 1));
            //C5

            words = words.Where(x => !(badwords.Any(y => y == x))) ;


            Console.WriteLine(string.Join(" ", words));
            //C6
            string word = string.Join(" ", words);
            // Loại bỏ các từ trong danh sách badword
            for (var i = 0; i < badwords.Length; i++)
            {
                word = word.Replace(badwords[i],"");
            }

            //c7
            var listWord = words.ToList();
            // Loại bỏ các từ trong danh sách badword
            listWord.RemoveAll(x => badwords.Contains(x));
        }
```