## Dùng Any hay Count
Để kiểm tra 1 tập hợp có tồn tại phần tử theo điều kiện, ta có thể dùng
list.Any(x=>x.Id == 2)
list.Count(x=>x.Id == 2) == 0

Trong 2 cách trên ta nên dùng Any bởi vì, any duyệt khi gặp phần tử thỏa điều kiện thì nó dừng lại và trả về kết quả. Còn Count thì sẽ duyệt hết tập hợp. Do đó dùng Any nhanh hơn và tốt hơn.