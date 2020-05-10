## Generic constrains là gì ?
Là điều kiện ràng buộc kèm theo khi ta sử dụng Generic. Trong C# có :
where T : struct  – Type argument phải là một value type
where T : class – Type argument phải là một reference type
where T : new() – Type argument phải là một public constructor không có tham số (có thể là default constructor).
where T : <base class> – Type argument phải kế thừa từ <base class> class.
where T : <interface> –  Type argument phải implement từ <interface> interface.
where T : U – Có 2 type arguments T và U. T phải inherit hoặc implement từ U.

## Example
````cs
public class GenericClass<T> where T : struct
{
}

GenericClass<int> genericInt = new GenericClass<int>();    //true, not error
GenericClass<string> genericString= new GenericClass<string>(); //false, error
````
````cs
public class GenericClass<T> where T : class
{
}

GenericClass<int> genericInt = new GenericClass<int>();    //false,  error
GenericClass<string> genericString= new GenericClass<string>(); //true, not error
````