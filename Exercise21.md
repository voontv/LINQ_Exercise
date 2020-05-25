## Phân biệt Select và SelectMany
Select thì sử dụng để lựa chọn giá trị từ một collection. Trong khi đó SelectMany thì sử dụng để lựa chọn các giá trị từ một collection của collection (tức là nested collection).

## Example
```cs
namespace Voontv
{

    class main
    {
        static void Main(string[] args)
        {
            List<Employee> employees = new List<Employee>();
            Employee emp1 = new Employee { Name = "Deepak", Skills = new List<string> { "C", "C++", "Java" }, SalaryNears = new List<int> { 1000, 1200, 1400 } };
            Employee emp2 = new Employee { Name = "Karan", Skills = new List<string> { "SQL Server", "C#", "ASP.NET" }, SalaryNears = new List<int> { 1000, 1200, 1400 } };

            Employee emp3 = new Employee { Name = "Lalit", Skills = new List<string> { "C#", "ASP.NET MVC", "Windows Azure", "SQL Server" }, SalaryNears = new List<int> { 1000, 1200, 1400 } };

            employees.Add(emp1);
            employees.Add(emp2);
            employees.Add(emp3);

            // Query using Select()
            IEnumerable<List<String>> resultSkillsSelect = employees.Select(e => e.Skills);
            IEnumerable<List<int>> resultSalarySelect = employees.Select(e => e.SalaryNears);

            Console.WriteLine("**************** Select with employees ******************");
            foreach (List<String> skillList in resultSkillsSelect)
            {
                foreach (string skill in skillList)
                {
                    Console.WriteLine(skill);
                }
                Console.WriteLine();
            }

            foreach (List<int> SalaryNears in resultSalarySelect)
            {
                foreach (int skill in SalaryNears)
                {
                    Console.WriteLine(skill);
                }
                Console.WriteLine();
            }

            // Query using SelectMany()
            IEnumerable<string> resultSkillsSelectMany = employees.SelectMany(emp => emp.Skills);
            IEnumerable<int> resultSalarySelectMany = employees.SelectMany(emp => emp.SalaryNears);

            Console.WriteLine("**************** SelectMany with employees ******************");

            foreach (string skill in resultSkillsSelectMany)
            {
                Console.WriteLine(skill);
            }

            foreach (int skill in resultSalarySelectMany)
            {
                Console.WriteLine(skill);
            }

            var listBook = new List<Book> { new Book(1, "Java", "200"), new Book(3, "Python", "120"),
                                            new Book(4, "C#", "150"), new Book(5, "English", "210"),
                                            new Book(6, "C++", "600"), new Book(8, "Kotlin", "200")};

            IEnumerable<List<int>> resultRenewSelect = listBook.Select(book => book.Renew);

            Console.WriteLine("**************** Select with book ******************");
            foreach (List<int> Renews in resultRenewSelect)
            {
                foreach (int renew in Renews)
                {
                    Console.WriteLine(renew);
                }
                Console.WriteLine();
            }
            IEnumerable<int> resultRenewSelectMany = listBook.SelectMany(book => book.Renew);
            Console.WriteLine("**************** SelectMany with books ******************");
            foreach (int renew in resultRenewSelectMany)
            {
                Console.WriteLine(renew);
            }
        }
    }

    public class Book
    {
        public int MaBook { get; set; }
        public string NameBook { get; set; }

        public string Value { get; set; }
        public List<int> Renew { get; set; }
        public Book(int createMabook, string createdName, string value)
        {
            MaBook = createMabook;
            NameBook = createdName;
            Value = value;
            Renew = new List<int> { 2000, 2008, 2015, 2020 };
        }
    }


    class Employee
    {
        public string Name { get; set; }
        public List<string> Skills { get; set; }
        public List<int> SalaryNears { get; set; }
    }

}
```