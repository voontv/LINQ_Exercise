## Trong các hàm FirstOrDefault, SingleOrDefault, LastOrDefault, Default ở đây thực chất là gì
Nó thực chất giống như việc tạo giá trị default cho kết quả trả về khi không tìm thấy được phần tử đáp ứng điều kiện đầu vào.
Cụ thể ở đây nó là giá trị mặc định của loại dữ liệu của phần tử trong tập hợp đang thực hiện việc tìm kiếm. Tức Default = default(type);
## Exam
Nếu tìm kiếm tập hợp có kiểu dữ liệu là int ,float--> default là 0.
Nếu kiểu dữ liệu là tập string --> default là ""
