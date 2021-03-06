```
Họ và tên: Ngọ Việt Hoàng
MSSV: 20183748
Mã lớp: 128745
Mã HP: IT4611
```
## Câu hỏi 1: Tệp nào vừa xuất hiện trong thư mục ChatRoomApp? Nó được sử dụng để làm gì?
- Tệp vừa xuất hiện là package.json
- Package.json là file cấu hình của npm, giúp cho npm hiểu nó cần phải cài đặt cái gì, thông tin về ứng dụng, phiên bản, …
## Câu hỏi 2: Mở trình duyệt và gõ vào đó địa chỉ http://localhost:3000, bạn sẽ nhận được thông điệp gì?

<image src="./images/1/q1.png"><br>

## Câu hỏi 3: Bạn hãy thử reload (Ctrl-R) lại trình duyệt. Bạn có nhìn thấy gì mới xuất hiện trên cửa sổ không? Nếu không có gì xuất hiện hết thì là vì sao?
- Không có gì xuất hiện trên của sổ cả
- Bỏi vì ở client lúc này chưa khai báo socket.io
- Sau khi khai báo socket ở client thì mỗi làn reload ở terminal sẽ xuất hiện

<image src="./images/1/q3.png">

## Câu hỏi 4: Refresh trang localhost:3000, bạn nhìn thấy thông điệp nào?

<image src="./images/1/q4.png"><br>

## Câu hỏi 5: Bây giờ bạn hãy thử gõ gì đó lên một tab. Cùng lúc đó, nhìn sang tab khác của người dùng khác, bạn thấy gì?

|||
|-|-|
|<image src="./images/1/q5.png"><br> | <image src="./images/1/q5_2.png"><br>|

========================================================================================

## Câu hỏi 6: Đâu là đoạn code mà Server gán correlationID vào câu trả lời?

<image src="./images/2/q6.png"><br>

## Câu hỏi 7: Dựa vào cả code của Client và Server để giải thích đâu là đoạn code mà Client gửi yêu cầu lên cho Server thông qua hàng đợi rpc_queue và tạo ra một hàng đợi mới để chờ câu trả lời của Server.

- Gửi yêu cầu thông qua hàng đợi rpc_queue

<image src="./images/2/q7_1.png"><br> 
<image src="./images/2/q7_2.png"><br>

- Tạo hàng đợi mới để trả lời

<image src="./images/2/q7_3.png"><br>


## Câu hỏi 8: 

<image src="./images/2/q8_1.png"><br>
<image src="./images/2/q8_2.png"><br>

- Kết quả nhận được là có 3 queue được tạo ra: "rpc_queue" của server và 2 queue cò lại của client (do em tạo ra 2 client)
- messages_ready: message đang đợi để được xử lý
- messages_unacknowledged: message đã được đọc bởi consumer nhưng consumer chưa gửi lại ACK đến broker để thông báo là đã hoàn thành xử lý message 

========================================================================================

## Câu hỏi 9: Địa chỉ IP của 2 máy là gì? Làm sao để ping nhau?
- Server IP
<image src="./images/3/server-ip.png"><br>

- Client IP
<image src="./images/3/client-ip.png"><br>

- 2 máy thuộc cùng 1 mạng nên có thể ping nhau

## Câu hỏi 10: Bạn đã xem được video trên máy client chưa? Đánh giá chất lượng video mà bạn xem trên máy client.
- Em đã xem được video trên máy client
<image src="./images/3/q10.png"><br>


## Câu hỏi 11: Kết quả nhận được sau lệnh ping là gì? Bạn có thấy độ trễ đã tăng 100ms không?
- Độ trễ đã tăng 100ms

<image src="./images/3/before_delay.png"><br>
<image src="./images/3/after_delay.png"><br>

## Câu hỏi 13: Cũng như câu hỏi 7, hãy quan sát video ở Client và đưa ra đánh giá và kết luận về ảnh hưởng của độ biến đổi delay lên chất lượng dịch vụ truyền video.
- Không có thay đổi đáng kể khi truyền video với kết quả ở câu trên nhưng khi truyền nhiều lần thì độ trễ khi load video ở client là khác nhau
## Câu hỏi 14: Hãy xem video ở client và đánh giá về độ ảnh hưởng của packet loss lên chất lượng dịch vụ truyền video. Thử tăng giá trị của tỷ lệ mất gói tin lên để thấy độ ảnh hưởng rõ nét hơn.
- Với giá trị 0.1% thì chất lượng video ở Client vẫn khá ổn nhưng âm thanh có bị ngắt quãng
- Khi tăng giá trị của tỉ lệ mất gói tin thì tần suất âm thanh ngắt quãng nhiều hơn và chất lượng hình ảnh cũng giảm đi. Khi tăng giá trị đến gần 50% thì gần như không thể load được hình ảnh trên client

## Câu hỏi 15: Hãy xem video ở client và đánh giá về độ ảnh hưởng của việc biến đổi packet loss lên chất lượng dịch vụ truyền video. Thử tăng giá trị của tỷ lệ mất gói tin lên để thấy độ ảnh hưởng rõ nét hơn.
- Khi giá trị là 0.3% thì không có nhiều sự thay đổi so với câu trên nhưng khi tăng giá trị lên lớn hơn thì nhận thấy sự đứt quãng là không đều.
## Câu hỏi 16: Hãy xem video ở client và đánh giá về độ ảnh hưởng của việc lặp gói tin lên chất lượng dịch vụ truyền video. Thử tăng giá trị của tỷ lệ lặp gói tin lên để thấy độ ảnh hưởng rõ nét hơn.
- Tương tự như mất gói tin, Với giá trị 1% thì chất lượng video ở Client vẫn khá ổn nhưng âm thanh có bị ngắt quãng
- Khi tăng giá trị của tỉ lệ lặp gói tin thì tần suất âm thanh ngắt quãng nhiều hơn và chất lượng hình ảnh cũng giảm đi. 

## Câu hỏi 17: Hãy xem video ở client và đánh giá về độ ảnh hưởng của việc đảo thứ tự gói tin lên chất lượng dịch vụ truyền video.
- Chất lượng video kém đi. Âm thanh bị ngắt quãng liên tục, có tạp âm.