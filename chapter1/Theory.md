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
- Cần cân bằng giữa hiệu năng hệ thống và độ trong suốt, bởi nếu server không có khả năng tự khắc phục được lỗi, mà độ trong suốt cao, sẽ khiến người sử dụng không thể phát hiện ra lỗi và tìm cách khắc phục khác.
- Ví dụ: dịch vụ xem phim online, khi người dùng đang xem mà máy chủ gặp lỗi, vì độ trong suốt cao nên người dùng không thể biết -> mất kiên nhẫn -> sử dụng dịch vụ của nhà quản trị hệ thống khác -> mất khách hàng. Thay vào đó, nhà quản tri nên giảm độ trong suốt xuống để người dùng thấy được server này đang gặp lỗi, đồng thời đưa ra các server khác để người sử dụng chọn lựa

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

||Kiến trúc tập trung|Kiến trúc phi tập trung|
|-|---|---|
|Ưu điểm|- Khả năng kiểm soát tài nguyên được tích hợp sẵn. Tất cả thông tin cần thiết đều được đặt tại một vị trí duy nhất<br>- Dữ liệu được bảo vệ tốt do kiến trúc tập trung của mạng. Có thể áp dụng các biện pháp kiểm soát truy cập và khôi phục dữ liệu dễ dàng<br>- Có khả năng mở rộng tốt, cóthể tăng số lượng tài nguyên khi cần => dễ dàng tăng kích thước mà không bị gián đoạn nhiều<br>- Không có sự phân biệt giữa các nền tảng khác nhau, mọi client đều có thể truy cập vào hệ thống|<!--separate row-->- Tất cả các máy tính tham gia mạng lưới đều có thể đóng góp thông tin bao gồm băng thông, dữ liệu và khả năng tính toán. Càng nhiều máy tham gia thì càng nhiều thông tin cho người dùng<br>- Nhờ tính chất phân tán giúp các mạng khác vẫn hoạt động tốt khi một máy trong mạng lưới gặp sự cố<br>- Dễ dàng cài đặt và sử dụng. Không cần phân quyền, phân cấp, quản lý máy trung tâm phức tạp<br>- Không yêu cầu phải có quản trị viên mạng. Bất cứ thành viên nào cũng có thể là người quản lý cho hệ thống<br>- Chi phí đầu tư không lớn. Không cần phải đầu tư máy chủ cũng như các loại phần cứng và phần mềm có giá trị cao.<br><!--separate column-->
|Nhược điểm|- Tắc nghẽn lưu lượng: nếu có quá nhiều request từ cùng một server, nó có thể làm chậm kết nối, hoặc tệ hơn là dẫn đến crash<br>- Nếu server xảy ra sự cố hay bị nhiễu, toàn bộ hệ thống mạng sẽ bị gián đoạn => thiếu tính ổn định và độ bền<br>- Chí phí thiết lập và bảo trì thường cao vì hệ thống có sức mạnh lớn thường đắt<br>- Công tác bảo trì đòi hỏi cần phải có một nhà quản lý mạng chuyên biệt để duy trì hoạt động của server<br>- Không phải tất cả tài nguyên hiện có trên server đều có thể hoạt động được|<!--separate row-->- Hệ thống ngang hàng, không có sự phân cấp. Điều này dẫn đến khó khăn trong việc quản lý các máy với nhau<br>- Thiếu an ninh, an toàn trong quá trình sử dụng vì bất cứ máy nào cũng có thể truy cập vào khi dữ liệu. Nếu có người ngoài đột nhập thì thông tin sẽ không được bảo mật.<br>- Các link trong hệ thống mạng P2P là loại gang hàng hoàn toàn vì thế mà độ tin cậy không cao.<br>- Các tệp và thư mục không thể được sao lưu tập trung.<br>- Các tài nguyên sẽ biến mất vì node cung cấp tài nguyên bị ngắt kết nối bất cứ lúc nào.

<br>

# Câu 10: Mạng overlay
- Việc quản lý cấu trúc của topo mạng gặp khó khăn, đặc biệt trong những trường hợp tỉ lệ vào/ra của các nút mạng cao
- Vấn đề cân bằng tải trong mạng
- Sự khác biệt về topology trên mạng overlay và mạng liên kết vật lý dẫn đến thời gian trễ truy vấn trung bình cao

# Câu 11: Kiến trúc client-server 
- Khi client không được báo nhận từ phía server thì client sẽ không biết là do server chưa nhận được yêu cầu hay thông điệp báo nhận bị mất trên đường truyền. Lúc này tùy thuộc vào tính chất của dịch vụ hay ứng dụng mà client có gửi lại yêu cầu không

# Câu 12: