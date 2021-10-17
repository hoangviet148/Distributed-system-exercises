```
Họ và tên: Ngọ Việt Hoàng
MSSV: 20183748
Mã lớp: 128745
Mã HP: IT4611
```

# Câu 1: 2 ví dụ về hệ phân tán
- HDFS (distributed filesystem): 
  - filesystem được lưu trên một cluster => các máy tính độc lập
  - các máy tính kết nối và chứa các bản sao của nhau
  - cung cấp đến users như là 1 filesystem duy nhất, người dùng không cần quan tâm file đang thao tác thuộc máy nào
- Mysql Replication: distributed database
  - data được lưu trên nhiều máy, ít nhất 2 máy (1 master và 1 slave)
  - các máy tính kết nối và đồng bộ dữ liệu (mỗi khi có transaction thì slave node sẽ đồng bộ dữ liệu từ master node)
  - data được ghi vào master và được đọc từ slave nhưng user không cần quan tâm đến điều này
# Câu 2: Tính chia sẻ tài nguyên
- Giảm chi phí: số lương các thiết bị ngoại vi đầu tư cho máy tính giảm => giảm suất đầu tư trên từng người sử dụng
- Tính sẵn sàng cao: Cho phép người sử dụng kết nối các tài nguyên ở xa và các máy khác nhau
- Hỗ trợ làm việc nhóm: các user có thể chia sẻ thông tin, tài liệu lẫn nhau
- Tăng rủi ro về an toàn thông tin
  - Chương trình có những kết nối mạng => có lỗ hổng bảo mật => giảm mức độ an toàn bảo mật của hệ thống
  - Khi quá trình chia sẻ thông tin kéo dài việc theo dõi tất cả thông tin được phép chia sẻ có thể tìm ra những thông tin ẩn, từ đó có những thông tin liên quan đến tính riêng tư có thể bị lộ.
# Câu 3: Tính trong suốt
- 
- Ví dụ
# Câu 4:
# Câu 5: DOS và NOS

|Property|NOS|DOS
|---|---|---|
|Definition|Là hệ điều hành được thiết kế để hỗ trợ máy trạm, máy tính cá nhân và kết nối các máy tính trong một mạng LAN|Là một hệ điều hành tập trung nhưng chạy trên nhiều CPU độc lập. Mỗi CPU chạy một phần của distriuted OS
|Goal|Cung cấp các local service đến người dùng từ xa|Che dấu và quản lý tài nguyên phần cứng
|Used for|Các máy tính không đồng nhất có ít liên kết|Các máy tính đồng nhất và liên kết mạnh
|Architecture|Tuân thủ theo kiến trúc 2 tầng client - server|Tuân thủ theo kiến trúc n tầng client - server
|Type|multi-computer và multiprocessor|Peer to peer và client/server
|Communication|Giao tiếp qua files|Giao tiếp bằng messages
|Transparency|low|hight
|Example|Windows 2000, Windows XP|Unix
||<image src="https://images.viblo.asia/5ebb6ed3-0f9b-460b-88f0-4f0768990051.png">|<image src="https://images.viblo.asia/c29b5a70-93aa-4b42-9766-617d852ab08d.png">|
<br>
- Middleware là sự kết hợp ưu điểm của cả 2 mô hình trên vì middleware thừa kế tính trong suốt của DOS và tính mở của NOS

  <image src="https://images.viblo.asia/5ebb6ed3-0f9b-460b-88f0-4f0768990051.png" width="500">
<br>

# Câu 6: Mô hình OSI
- Chức năng các tầng
  - Application layer: cung cấp phương tiện cho người dùng truy nhập các thông tin và dữ liệu trên mạng thông qua chương trình ứng dụng. Tầng này là giao diện chính để người dùng tương tác với chương trình ứng dụng, và qua đó với mạng
  - Presentation layer: biến đổi dữ liệu để cung cấp một giao diện tiêu chuẩn cho tầng ứng dụng. Nó thực hiện các tác vụ như mã hóa dữ liệu sang dạng MIME, nén dữ liệu, và các thao tác tương tự đối với biểu diễn dữ liệu để trình diễn dữ liệu theo như cách mà chuyên viên phát triển giao thức hoặc dịch vụ cho là thích hợp
  - Session layer: Khi dữ liệu đã được biến đổi thành định dạng chuẩn, máy gửi đi sẽ thiết lập một phiên – session với máy nhận. Đây chính là lớp sẽ đồng bộ hoá quá trình liên lạc của hai máy và quản lý việc trao đổi dữ liệu. Lớp phiên này chịu trách nhiệm cho việc thiết lập, quản lý và chấm dứt session với máy từ xa.
  - Transport layer: cung cấp dịch vụ chuyên dụng chuyển dữ liệu giữa các người dùng tại đầu cuối, nhờ đó các tầng trên không phải quan tâm đến việc cung cấp dịch vụ truyền dữ liệu đáng tin cậy và hiệu quả. Tầng này kiểm soát độ tin cậy của kết nối cho trước và cung cấp các cơ chế theo dõi gói tin
  - Network layer: cung cấp các chức năng và qui trình cho việc truyền các chuỗi dữ liệu có độ dài đa dạng, từ một nguồn tới một đích, thông qua một hoặc nhiều mạng, trong khi vẫn duy trì chất lượng dịch vụ (quality of service) mà tầng giao vận yêu cầu. Tầng mạng thực hiện chức năng định tuyến
  - Datalink layer: cung cấp các phương tiện có tính chức năng và quy trình để truyền dữ liệu giữa các thực thể mạng, phát hiện và có thể sửa chữa các lỗi trong tầng vật lý nếu có.
  - Physical layer: định nghĩa tất cả các đặc tả về điện và vật lý cho các thiết bị.
- Ví dụ: Khi tầng giao vận chuyển từ dùng giao thức TCP sang UDP thì các tầng khác vẫn hoạt động bình thường, dữ liệu vẫn được gửi đi bình thường, vấn đề xảy ra chỉ là tính toàn vẹn và an toàn của dữ liệu
# Câu 7: ví dụ về mô hình pushlish / subscrible
- Giao thức MQTT (Message Queuing Telemetry Transport)

    <image src="./images/theory/mqtt.png" width=500>

  - Sử sụng băng thông thấp, độ tin cậy cao và có khả năng hoạt động trong điều kiện đường truyền không ổn định
  - Hệ thống gồm nhiều node trạm (mqtt client) kết nối đến một MQTT server (broker)
  - Mỗi client sẽ đăng ký một vài kênh (topic), ví dụ như "/client1/channel1", "/client1/channel2". Quá trình đăng ký này gọi là "subscribe". Mỗi client sẽ nhận được dữ liệu khi bất kỳ trạm nào khác gửi dữ liệu vào kênh đã đăng ký.
  - Khi một client gửi dữ liệu tới kênh đó, gọi là "publish".

# Câu 8: khác nhau giữa phân tán dọc và phân tán ngang
  - *Phân tán dọc*: liên quan đến kiến trúc tập trung. Là kết quả của việc phân chia ứng dụng thành nhiều thành phần như giao diện, các thành phần xử lý và các thành phần cơ sở dữ liệu. Các thahf phần này có liên quan đến trực tiếp đến việc tổ chức logic ứng dụng
  - *Phân tán ngang*: Một client hay server có thể bị phân chia một cách vật lý thành các thành phần bằng nhau, mỗi phần hoạt động trên phần mà nó được chia sẻ từ một tập dữ liệu hoàn chỉnh

# Câu 9: Ưu nhược điểm của kiến trúc tập trung và phi tập trung
- Kiến trúc tập trung
- Kiến trúc phi tập trung
# Câu 10: Mạng overlay
# Câu 11: Kiến trúc client-server 
- Khi client không được báo nhận từ phía server thì client sẽ không biết là do server chưa nhận được yêu cầu hay thông điệp báo nhận bị mất trên đường truyền. Lúc này tùy thuộc vào tính chất của dịch vụ hay ứng dụng mà client có gửi lại yêu cầu không
# Câu 12: