## Phân biệt OfType và Cast
Cast sẽ xảy ra InvalidCastException nếu có một phần tử nào trong mảng không thể cast tới kiểu dữ liệu mong muốn. Còn OfType thì bình thường
## Example
````cs
        var items = new ArrayList();
        items.Add("Java");
        items.Add("Pythong");
        items.Add("C#");
        items.Add(12);
        items.Add(23);
        items.Add(34);
         //bình thường
        var OffTypeString = items.OfType<string>();
        //sử dụng sẽ văng lỗi InvalidCastException
        var CastString = items.Cast<string>();
        //bình thường
        var OffTypeChar = items.OfType<char>();
        //sử dụng sẽ văng lỗi InvalidCastException
        var CastChar = items.Cast<char>();
        //bình thường
        var OffTypeFloat = items.OfType<float>();
        //sử dụng sẽ văng lỗi InvalidCastException
        var CastFloat = items.Cast<float>();
````