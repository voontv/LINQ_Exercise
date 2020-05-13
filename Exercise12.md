## Phân biệt Single và SingleOrDefault
Nếu kết quả tìm kiếm không có phần tử nào thỏa mãn hoặc tập hợp là null thì SingleOrDefault sẽ trả về kết quả là giá trị mặc định của kiểu dữ liệu của tập hợp đó. Còn Single thì văng lỗi.
## Example
````cs
        int[] numbers = { 6, 77, 6, 1, 9, 11, 11, 18, 9 };
        string[] names = { };
        string[] fruits = {"orange", "banana"};
        //văng lỗi
        var num1 = numbers.Single(x => x > 100);
        // trả về giá trị default của kiểu Int là 0
        var num2 = numbers.SingleOrDefault(x => x > 100);
        // lỗi
        var str1 = names.Single();
        // trả về giá trị ""
        var str2 = names.SingleOrDefault();
        // lỗi
        var fruit1 = fruits.Single(str => str.Length > 20);
        // trả về giá trị ""
        var str2 = fruits.SingleOrDefault(str => str.Length > 20);
````