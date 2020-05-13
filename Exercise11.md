## Phân biệt First với FirstOrDefault
Nếu không có phần tử nào tìm thấy phù hợp hoặc tập hợp là null thì FirstOrDefault sẽ trả về giá trị mặc định của kiểu dữ liệu của tập hợp đó. Còn First sẽ văng lỗi (nên phải try catch)
## Example
````cs
        int[] numbers = { 6, 77, 6, 1, 9, 11, 11, 18, 9 };
        string[] names = { };
        string[] fruits = {"orange", "banana"};
        //văng lỗi
        var num1 = numbers.First(x => x > 100);
        // trả về giá trị default của kiểu Int là 0
        var num2 = numbers.FirstOrDefault(x => x > 100);
        // lỗi
        var str1 = names.First();
        // trả về giá trị ""
        var str2 = names.First();
        // lỗi
        var fruit1 = fruits.First(str => str.Length > 20);
        // trả về giá trị ""
        var str2 = fruits.First(str => str.Length > 20);
````