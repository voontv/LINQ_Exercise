## Phân biệt OfType và Cast
Cast sẽ xảy ra InvalidCastException nếu có một phần tử nào trong mảng không thể cast tới kiểu dữ liệu mong muốn. Còn OfType thì bình thường.

Ở đây 2 liên quan đến việc thực hiện để ra kết quả dẫn tới khác nhau ở trên. Trong quá trình duyệt các phần tử trong IEnumerable ở OfType sẽ có hành động kiểm tra đối tượng đó có đúng là kiểu cần hay không. Sau đó mới tiến hành ép kiểu.
````cs
//Ở OfType
public IEnumerable<T> OfType<T>(this IEnumerable source)
{
  foreach(object o in source)
  {
        if(o is T) 
        {
                yield return (T) o;
        }
  }
    
}

public IEnumerable<T> Cast<T>(this IEnumerable source)
{
  foreach(object o in source)
        yield return (T) o;
}
````

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