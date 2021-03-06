# Mysql-DB-Replication-Master--Slave

### - Overview:

***https://quanph82.wordpress.com/2012/06/25/nguyen-ly-va-cau-hinh-replication-trong-mysql/***

- MySQL là một quá trình cho phép dữ liệu từ một Master được sao chép tự động sang một hoặc nhiều máy chủ cơ sở dữ liệu sl 



**Có 2 giải pháp cho việc replication:**

- `Master - Slave`: Là dạng replication trong đó data được ghi trên Master server và đồng bộ sang Slave server

- `Master - Master`: Là dạng replication trong đó dữ liệu có thể ghi trên cả các Mysql server chạy replication.

![image](https://user-images.githubusercontent.com/83824403/164149647-6bc9f3ad-56ac-46b0-8f5b-85fa14a093a2.png)






## Ưu điểm của replication trong mysql
- `Giảm tải cho cơ sở dữ liệu server master`, tải trọng của server được phân tải cho các con slave, cải thiện hiệu năng cho toàn hệ thống. Trong môi trường này, tất cả các quá trình ghi và cập nhật đều phải diễn ra trên server master, bên cạnh đó quá trình đọc được diễn ra trên một hoặc nhiều con slave. Chính vì vậy mô hình này giúp tăng đáng kể hiệu năng của toàn hệ thống.

- `Tính bảo mật dữ liệu cao` - vì dữ liệu được sao chép đến các slave, và các slave có thể tạm dừng quá trình sao chép, nó có thể chạy các dịch vụ sao lưu trên các slave mà không làm hư hỏng dữ liệu tổng thể tương ứng

- `Tính phân tích` - dữ liệu trực tiếp có thể được tạo ra trên master, trong khi phân tích các thông tin có thể xảy ra trên các slave mà không ảnh hưởng đến hiệu suất của master.

- `Tính phân phối dữ liệu từ xa` - bạn có thể sử dụng replication để tạo ra một bản sao của dữ liệu cho một trang web từ xa để sử dụng, mà không cần truy cập thường xuyên vào con master.






## `Mô hình và cách thức hoạt động`

- Replication dựa trên các con master lưu giữ theo dõi tất cả những thay đổi cơ sở dữ liệu của nó **(cập nhật, xóa, vv) trong bản ghi nhị phân của nó.** Các bản ghi nhị phân phục vụ như là các record của tất cả các sự kiện làm thay đổi cấu trúc cơ sở dữ liệu hoặc nội dung (dữ liệu) từ thời điểm các máy chủ đã bắt đầu thực thi. *`Thông thường, câu SELECT không được ghi lại bởi vì chúng không phải thay đổi cấu trúc cũng như nội dung của cơ sở dữ liệu.`*


- Mỗi slave kết nối đến các master **yêu cầu một bản sao của bản ghi nhị phân**. Đó là, **nó kéo các dữ liệu từ các master, chứ không phải là master đẩy dữ liệu đến các slave**. Các slave cũng thực hiện các sự kiện từ các bản ghi nhị phân mà nó nhận được. Quá trình này lặp đi lặp lại những thay đổi ban đầu cũng giống như nó đã được thực hiện trên master. Bảng được tạo ra hoặc cấu trúc thay đổi và dữ liệu đã chèn hay đã xóa và kể cả cập nhật thì đều giống hệt theo những thay đổi mà ban đầu đã được thực hiện trên master.







## NOW LETS GET STARTED IN NEXT PAGE!



`*AUTHOR: ĐOÀN VĂN PHÚC*`


*Reference*:

- https://hevodata.com/learn/mysql-master-slave-replication/

- https://vietcalls.com/xay-dung-he-thong-mysql-master-slave-replication/

- https://haysharing.com/cau-hinh-mysql-replication-master-slave.html

- https://cloudcraft.info/mysql-replication-master-slave/


giai phap thay the la galera db: https://blog.cloud365.vn/linux/pacemaker-haproxy-galera/
