## Câu hỏi 1: Một kết nối socket cần 4 thông tin nào? Tại sao phải cần đủ 4 thông tin đó? 
- Một kết nối socket cần 4 thông tin là : địa chỉ IP bên gửi, số hiệu cổng bên gửi, địa chỉ IP bên nhận, số hiệu cổng bên nhận.
- Cần đầy đủ 4 thông tin này vì phải có đủ 4 thông tin này thì hệ thống mới có thể tạo được kết nối, phân biệt được các kết nối với nhau.

## Câu hỏi 2: Tại sao giao thức yêu cầu-trả lời (request-reply) lại được coi là đồng bộ và tin cậy? 
Giao thức yêu cầu-trả lời (request-reply) lại được coi là đồng bộ và tin cậy vì :
- Khi client gửi 1 thông điệp đến server thì client sẽ tự block mình để chờ đến khi server xử lí xong và gửi thông điệp trả lời, khi nhận được thông điệp trả lời từ server thì client mới chạy tiếp (đồng bộ).
- Khi request gửi đi thì luôn có reply trả về như 1 thông điệp báo nhận (tin cậy).

## Câu hỏi 3: Hai vấn đề chính đối với giao thức RPC là gì? 
Hai vấn đề chính đối với giao thức RPC là: 
- Hệ thống không đồng nhất (không gian nhớ khác nhau, cách biểu diễn thông tin khác nhau)
- Có lỗi xảy ra (các khả năng khi có lỗi như thủ tục không thực thi, thủ tục thực thi 1 lần, thủ tục thực thi nhiều lần,...)

## Câu hỏi 4: Vấn đề đối với truyền tham biến  trong RPC là gì? Còn đối với truyền tham chiếu? Giải pháp đưa ra là gì? 
Vấn đề đối với truyền tham biến trong RPC: 
- Vấn đề khi biểu diễn dữ liệu khác nhau.
- Các dữ liệu không thuộc cùng 1 kiểu, các dữ liệu khác nhau được biểu diễn khác nhau.
Vấn đề đối với truyền tham chiếu trong RPC:
- Bộ nhớ phân tán.
Giải pháp: 
- Tham chiếu thay bằng Copy/Restoretuy nhiên giải pháp này có vấn đề: tốn băng thông.

## Câu hỏi 5: So sánh RMI và RPC. Nhược điểm của RMI so với RPC là gì?
- So sánh RMI và RPC:
  - RPC hỗ trợ các mô hình lập trình thủ tục, do đó dựa trên C, trong khi RMI hỗ trợ các mô hình lập trình hướng đối tượng và dựa trên java.
  - Các tham số được truyền cho các thủ tục từ xa trong RPC là các cấu trúc dữ liệu thông thường. Ngược lại, RMI chuyển các đối tượng làm tham số cho phương thức từ xa.
  - RPC có thể được coi là phiên bản cũ hơn của RMI và nó được sử dụng trong các ngôn ngữ lập trình hỗ trợ lập trình thủ tục và nó chỉ có thể sử dụng phương thức truyền qua giá trị. Đối với, cơ sở RMI được phát minh dựa trên phương pháp lập trình hiện đại, có thể sử dụng vượt qua giá trị hoặc tham chiếu. Một ưu điểm khác của RMI là các tham số được truyền bởi tham chiếu có thể được thay đổi.
  - Giao thức RPC tạo ra nhiều chi phí hơn RMI.
  - Các tham số được truyền trong RPC phải là ra vào trong ra, có nghĩa là giá trị được truyền cho thủ tục và giá trị đầu ra phải có cùng kiểu dữ liệu. Ngược lại, không có sự bắt buộc nào trong việc chuyển các tham số ra-ra-ra-ra trong RMI.
  - Trong RPC, các tham chiếu không thể có thể xảy ra do hai quy trình có không gian địa chỉ riêng biệt, nhưng có thể trong trường hợp RMI.

- Nhược điểm của RMI so với RPC là RMI chỉ giới hạn ở ngôn ngữ java

## Câu hỏi 6: Giải thích cơ chế trao đổi thông tin hướng thông điệp bất đồng bộ và bền vững.
Cơ chế trao đổi thông tin hướng thông điệp bất đồng bộ và bền vững:
- Sử dụng tầng MOM (Message-Oriented Middleware)
- Dùng cơ chế hàng đợi thông điệp trung gian để hỗ trợ trao đổi thông điệp không đồng bộ bền vững. (bên gửi cứ gửi thông điệp không quan tâm bên nhận nhận như thế nào, không cần nhận câu trả lời ngay).
- Bên gửi gửi thông điệp vào hàng đợi trung gian và bên nhận sẽ lấy thông điệp từ hàng đợi trung gian đó.

## Câu hỏi 7: Trong trao đổi thông tin hướng dòng, những cơ chế thực thi QoS được thực hiện ở tầng nào? Giải thích. Trình bày một số cơ chế thực thi QoS để chứng minh điều đó.
Trong trao đổi thông tin hướng dòng, những cơ chế thực thi QoS được thực hiện ở tầng IP. Rất ít hệ thống mạng có băng thông không giới hạn, do đó việc tắc nghẽn hay mất gói trong mạng luôn có thể xảy ra. QoS như một giải pháp giúp cho băng thông mạng được quản lý và sử dụng hiệu quả để dành sự ưu tiên cho những lưu lượng quan trọng hơn những lưu lượng khác và đảm bảo cho nó được truyền đi.
QoS thường được đánh giá qua các thông số chính sau:
- Latency: độ trễ khi truyền một gói tin qua mạng.
- Loss: độ mất gói.
- Jitter: độ biến động trễ (sự khác nhau về thời gian đến của các gói tin thuộc cùng một luồng lưu lượng).
- Throughput: thông lượng của mạng.
- Availability: độ khả dụng của mạng.

Cơ chế thực hiện QoS trong mạng có 4 bước cơ bản cần quan tâm như sau:
- Bước 1: Nhận diện lưu lượng và các yêu cầu của nó. Cần phải nắm rõ các loại lưu lượng đang tồn tại trong mạng và sau đó xác định các yêu cầu QoS cho các loại lưu lượng khác nhau này.
- Bước 2: Chia lưu lượng thành các lớp. Chẳng hạn như E-mail được phân vào lớp Best-efford, Voice được phân vào lớp Realtime...
- Bước 3: Định nghĩa các chính sách QoS cho mỗi lớp như đảm bảo băng thông cực tiểu, giới hạn băng thông cực đại, chỉ định độ ưu tiên cho mỗi lớp, sử dụng các kĩ thuật QoS như hàng đợi, tránh tắc nghẽn, quản lý tắc nghẽn...
- Bước 4: Áp đặt các chính sách QoS vào interface.
 QoS có thể giúp phân loại dữ liệu, quản lý hàng đợi, và ngăn ngừa mất dữ liệu.
