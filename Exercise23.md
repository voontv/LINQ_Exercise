## Để lấy phần tử đầu tiên thỏa mãn điều kiện, ta có 2 giải pháp sau
- list.Where(x=>x.Valid == true).First()
- list.First(x=>x.Valid == true)
Dùng First sẽ tốt hơn, vì nó sẽ dừng lại khi gặp phần tử thỏa điều kiện. Còn Where sẽ lọc ra 1 tập hợp thỏa điều kiện và sau đó lấy phần tử đầu tiên tron tập hợp đó.
Nên First nhanh và tiết kiệm thời gian tìm kiếm hơn.