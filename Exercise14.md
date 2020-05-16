## Phân biệt OrderBy với ThenBy
ThenBy chỉ được sử dụng sau khi chuỗi đã sắp xếp theo một chuẩn nào đó. Còn OrderBy thì không cần.
Đối với ThenBy khi nó muốn thực hiện việc so sánh để sắp xếp thì nó sẽ kiểm trả xem 2 phần tử muốn so sánh đó có bằng nhau theo một phương thức so sánh gì không.

````cs
string[] fruits = { "grape", "passionfruit", "banana", "mango",
                      "orange", "raspberry", "apple", "blueberry" };
IEnumerable<string> query =
    fruits.OrderBy(fruit => fruit.Length).ThenBy(fruit => fruit);
/*
với lệnh OrderBy ban đầu nó sẽ đưa ra IEnumerable như sau {"grape","mango","apple","banana","orange","raspberry","blueberry","passionfruit"}, đối với orderBy mỗi phần tử phải so sánh với các phần tử khác trong tập hợp.
Còn đối với ThenBy nó chỉ cần quan tâm đến việc so sánh phần tử trước và sau nó. Nếu thỏa điều kiện bằng nhau theo tiêu chí so sánh sắp sếp ban đầu thì nó mới tiến hành thực hiện công việc so sánh phụ của nó.
Như ở trên phần tử grape chỉ cần quan tâm so sánh với thằng bên cạnh là mango không cần quan tâm đến các phần tử còn lại
*/
````