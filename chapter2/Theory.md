```
Họ và tên: Ngọ Việt Hoàng
MSSV: 20183748
Mã lớp: 128745
Mã HP: IT4611
```
## Câu hỏi 1: Có cần thiết phải giới hạn số lượng các luồng trong một tiến trình server?
- Có bởi 2 lý do
  - Thread cần Ram cho private stack dẫn đến nếu có quá nhiều thread sẽ tốn quá nhiều bộ nhớ để server hoạt động bình thường.
  - Lý do thứ 2 quan trọng hươn là đối với hệ điều hành, các luồng độc lập 
  vận hành khá chồng chéo. Hệ điều hành sử dụng virtual memory từ đó mới ánh xạ vào memory vật lý, khí sinh ra nhiều luồng thì việc quản lý virtual memory trở nên phức tạp gây nên việc crash page từ đó làm giảm hiệu năng server và giảm hiệu quả hoạt động của cache
## Câu hỏi 2: Có nên chỉ gắn một luồng đơn duy nhất với một tiến trình nhẹ?
- Nên bởi vì
  - Khi luồng đó gọi một lời gọi hệ thống thì các tiến trình khác không bị block và vẫn được thực hiện liên tục do kernel sẽ lập lịch làm việc cho luồng này

## Câu hỏi 3: Có nên chỉ có một tiến trình nhẹ đơn gắn với 1 tiến trình?
- Không nên bởi:
  - Khi có 1 lời gọi hệ thống thì tiến trình nhẹ bị block và khi có lời gọi hệ thống thứ 2 trong tiến trình thì không thể thực hiện được

## Câu hỏi 4: Bài toán này yêu cầu bạn so sánh thời gian đọc một tệp (file) của một máy chủ tập tin (file server) đơn luồng và một máy chủ đa luồng. Phải mất tổng cộng 15 ms để nhận 1 yêu cầu (request) và thực hiện quá trình xử lý, giả định rằng các dữ liệu cần thiết nằm ở bộ nhớ đệm trong bộ nhớ chính. Nếu cần thiết phải thực hiện một thao tác truy cập ổ đĩa thì cần thêm 75 ms, biết rằng việc phải thực hiện thao tác này có xắc suất là 1/3. Hỏi máy chủ có thể nhận bao nhiêu yêu cầu/giây trong 2 trường hợp: máy chủ là đơn luồng và máy chủ là đa luồng (ngoài luồng nhận và xử lý request, sẽ có thêm 1 luồng để truy cập ổ đĩa nếu cần thiết)? Giải thích.
- Đơn luồng
  - Thời gian để nhận 1 yêu cầu: 15 x 2/3 + (15+75) x 1/3 = 40 (ms)
  - Số request / s xử lý được: 1000/40 = 25 request

- Đa luồng
  - Thời gian để nhận 1 yêu cầu: 15 x 2/3 + 75 x 1/3 = 35 (ms)
  - Số request / s xử lý được: 1000/35 ~ 29 request

## Câu hỏi 5: Với việc xây dựng một server đồng thời, hãy so sánh việc server này tạo một luồng mới và tạo một tiến trình mới khi nhận được yêu cầu từ phía client. 
|Đa luồng|Đa tiến trình|
|-|-|
|-	Xử lí song song nhiều công việc|-	Xử lí song song nhiều công việc|
|-	Chi phí lập trình cao|-	Chi phí lập trình thấp|
|-	Phải đảm bảo vấn đề xung đột giữa các luồng|-	Không cần quan tâm xung đột giữa các tiến trình, mỗi tiến trình được tạo có tài nguyên riêng có môi trường riêng. Hệ điều hành phải đảm bảo không xảy ra xung đột|
|- Các ngữ cảnh chuyển đổi dễ hơn do dùng chung tài nguyên|-	Chuyển đổi ngữ cảnh giữa các tiến trình chậm và tốn kém tài nguyên hơn do hệ điều hành tách riêng tài nguyên|

## Câu hỏi 6: Nếu bây giờ một webserver tổ chức lưu lại thông tin về địa chỉ IP của client và trang web client đó vừa truy cập. Khi có 1 client kết nối với server đó, server sẽ tra xem trong bảng thông tin, nếu tìm thấy thì sẽ gửi nội dung trang web đó cho client. Server này là có trạng thái (stateful) hay không trạng thái (stateless)?
- Server này là stateless bởi
  - Việc lưu thông tin về đại chỉ IP và trang web client truy cập là việc của DNS không phải do tiến trình httpd
  - Giao thức http là giao thức stateless

## Câu hỏi 7: Trong các giao thức phân tầng, mỗi tầng sẽ có một header riêng. Vậy có nên triển khai một hệ thống mà tất cả các header của các tầng đưa chung vào một phần (gọi là header chung), gắn vào đầu mỗi thông điệp để có thể xử lý chung? Giải thích.
- Không nên gộp header của các tầng lại bởi
  - Data di chuyển giữa các tầng sẽ chậm đi vì mất thời gian bóc tách và tìm ra đúng header
  - Mất đi tính trong suốt giữa các tầng
  - Việc phân tàng không còn ý nghĩa bởi lúc nào các tầng hoạt động như khối thống nhau và ảnh hưởng lẫn nhau khi update công nghệ


