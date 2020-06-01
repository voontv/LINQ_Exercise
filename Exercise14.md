## Phân biệt OrderBy với ThenBy
ThenBy chỉ được sử dụng sau khi chuỗi đã sắp xếp theo một chuẩn nào đó. Còn OrderBy thì không cần.
Đối với ThenBy khi nó muốn thực hiện việc so sánh để sắp xếp thì nó sẽ kiểm trả xem 2 phần tử muốn so sánh đó có bằng nhau theo một phương thức so sánh gì không.

Khi sắp xếp khi gặp trường hợp chúng ta cần một so sánh phụ để so sánh sắp xếp tiếp khi các phần tử nối tiếp nhau bằng nhau theo tiêu chí sắp xếp bang đầu chúng ta không thể sử dụng OrderBy bởi vì OrderBy sẽ chỉ sắp xếp theo tiêu chí sắp xếp đang sử dụng, bỏ đi các tiêu chí sắp xếp trước đó. Còn đối với ThenBy sau khi được gọi nó sẽ căng cứ theo tiêu chí sắp xếp trước đó để sắp xếp lại, tức ThenBy chỉ so sanh các phần tử bằng nhau trong IEnumerable hiện tại và sắp xếp lại vị trí của các phần tử này, nên chúng ta có thể sử dụng nhiều ThenBy lồng nhau.

````cs
var listDate = new List<Date> { new Date(1990,02,14), new Date(1990,08,12), new Date(1990,07,11), new Date(1990,06,10), new Date(1990,03,10),
            new Date(1990,08,14), new Date(1990,08,24), new Date(1990,08,1), new Date(1990,08,14), new Date(1990,08,22),
            new Date(1890,08,14), new Date(1870,08,24), new Date(2001,08,1), new Date(1988,08,14), new Date(2003,08,22)};
var listdateOrderBy = listDate.OrderBy(x => x.Year).OrderBy(x => x.Month).OrderBy(x => x.Day);
var listdateThenBy = listDate.OrderBy(x => x.Year).ThenBy(x => x.Month).ThenBy(x => x.Day);
/*
Với ví dụ trên thì listdateOrderBy sẽ sắp xếp theo tiêu chí OrderBy cuối cùng mà ko quan tâm tới bất kỳ tiêu chí nào trước đó.
listdateThenBy sau khi sắp xếp theo tiêu chí lưu trữ đầu tiên là compare theo Year, thì ở ThenBy sau đó nó theo tiêu chi sắp xếp là Month thì việc đầu tiên đó là nó căn cứ theo tiêu chí cũ là Year, chỉ so sánh để sắp xếp lại ở những vị trí Year bằng nhau, nó tiến hành compare với tiêu chí Month... tương tự với các ThenBy sau.
*/
````