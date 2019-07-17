# Cách dữ liệu lưu thông qua các lớp OSI  
###### Để hiểu tốt hơn về chức năng của các tầng trong mô hình OSI, quan trọng là biết dữ liệu lưu thông giữa các tầng.Trong phần này, chúng tôi sẽ theo dấu dữ liệu khi nó lưu thông qua các tầng của mô hình OSI. Như ta thấy trong phần này, mỗi lớp thêm ( hoặc gói gọn ) một số dạng header hoặc đoạn giới thiệu. (Layer 2, tầng Data link layer, chịu trách nhiệm thêm đoạn dữ liệu).
### ![Imgur](https://i.imgur.com/fbzZHFG.png)
Hình 2.2 cho ta thấy luồng dữ liệu từ thiết bị A đến thiết bị B
###### Lưu ý: Ví dụ trong hình 2.2 cho ta thấy rằng gói tin người dùng cuối (tiêu đề và dữ liệu) truyền qua mô hình OSI. Hình giả định không có thiết bị trung gian.
###### Khi hệ thống cuối nhận được luồng bit không cấu trúc từ tầng vật lý , mỗi lớp loại bỏ thông tin tiêu đề được áp dụng với nó tới khi thiết bị nhận được dữ liệu. Phần sau miêu tả những gì xảy ra trong các tầng mô hình OSI khi gửi email từ thiết bị A đến thiết bị B.
1. Một ứng dụng, chẳng hạn như chương trình email, tạo dữ liệu sẽ được gửi bởi người dùng cuối. Lớp ứng dụng sẽ đặt trường header (đóng gói) trường chứa thông tin như kích thước màn hình và phông chữ, và chuyển dữ liệu đến tầng Presentation (tầng 6).
2. Lớp Presentation đặt thông tin header lớp 6. Ví dụ, văn bản trong tin nhắn có thể được chuyển đổi sang ASCII. Sau đó sẽ chuyển dữ liệu mới sang lớp Session (Lớp 5).
3. Lớp Session tương tự cũng thêm thông tin header lớp 5, chẳng hạn như thông tin lớp 5 sẽ quản lý luồng dữ liệu, và chuyển dữ liệu này tới lớp Transport (lớp 4) 
4. Lớp Transport đặt thông tin tiêu đề lớp 4, chẳng hạn như xác nhận rằng việc phân đoạn đã được thực hiện trong header, và chuyển nó đến lớp Network (lớp 3).
5. Lớp Network đặt thông tin Header lớp 3. Chẳng hạn như địa chỉ nguồn và đích để lớp Network có thể xác định tốt nhất đường dẫn cho các Packets, và chuyển nó xuống lớp Data link (Lớp 2).
6. Lớp Data link đặt thông tin Header và đoạn giới thiệu của lớp 2, chẳng hạn như Frame Check Sequence (FCS)- 'chuỗi kiểm tra frame' để đảm bảo rằng thông tin không bị hỏng, và chuyển dữ liệu mới này đến lớp Physical (Lớp 1) để truyền qua các phương tiện truyền thông.
7. Luồng Bit sau đó được truyền dưới dạng số 1 và 0 trên lớp Physical. Tại thời điểm này, lớp Physical đảm bảo đồng bộ bit. Đồng bộ bit sẽ đảm bảo dữ liệu người dùng cuối được lắp ráp theo đúng thứ tự  được gửi.
8. Bước 1 đến 7 xảy ra theo thứ tự ngược lại trên thiết bị đích. Thiết bị B thu thập các bit thô từ tầng Physical và chuyển chúng lên lớp Data link. Lớp Data link loại bỏ header và phần phần giới thiệu và chuyển thông tin còn lại cho lớp Network và tiếp tục cho đến khi lớp Application nhận được dữ liệu. Cuối cùng thiết bị sẽ nhận được thông báo email cho biết rằng đã nhận được thông báo email mới.
###### Làm quen với mô hình OSI và trách nhiệm của từng lớp. Bạn có thể nhận ra chức năng từng lớp của mô hình OSI. Bảy lớp của mô hình tham chiếu OSI thường được chia thành 2 loại: Lớp trên (Lớp 4 đến 7) và Lớp dưới (1-3).
###### Như bạn có thể xác định từ ví dụ về đóng gói, mô hình OSI cung cấp một dich vụ cho phép thông tin chảy một cách thông suốt từ lớp này sang lớp khác. Cuối cùng, thông tin sẽ được trình bày cho thiết bị cuối ở định dạng có thể đọc được. Bây giờ chúng ta đã xem xét mô hình OSI, phần tiếp theo sẽ xem xét cách các Packet được gửi qua mạng bằng thuật toán định tuyến.

