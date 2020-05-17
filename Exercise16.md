## Phân biệt Count property và menthod
Count property là thuộc tính của các dẫn xuất từ ICollection. Còn Count() là một menthod mở rộng của LinQ, trong Count() nó sẽ kiểm tra đối tượng có phải là ICollection không, nếu đúng thì nó sẽ trả về property của ICollection, ngược lại nó sẽ trả về giá trị số phần tử dựa vào phương thức MoveNext() của IEnumerator. Chính vì vậy trong trường hợp vừa sử dụng được Count và Count() thì sử dụng Count property sẽ nhanh chóng hơn rất nhiều.

## Example
```cs
        var names = new List<string> { "Hartono, Tommy", "Adams, Terry", "Andersen, Henriette Thaulow", "Hedlund, Magnus", "Ito, Shu" };
        var countProperty = names.Count;
        var countMethod = names.Count();
        IEnumerable<string> namesIEnum = new List<string> { "Hartono, Tommy", "Adams, Terry", "Andersen, Henriette Thaulow", "Hedlund, Magnus", "Ito, Shu" };
        //sai vì nó ko phải là dẫn xuất của ICollection
        var countPropertyA = namesIEnum.Count;
        var CountMethodA = namesIEnum.Count();

        string[] fruits = { "grape", "passionfruit", "banana", "mango",
                "orange", "raspberry", "apple", "blueberry" };
        //sai vì nó ko phải là dẫn xuất của ICollection
        var countPropertyB = fruits.Count;
```