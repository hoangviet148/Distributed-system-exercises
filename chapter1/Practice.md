# 1. Webserver Apache
- Câu hỏi 1: Đường dẫn đến file html chứa nội dung mặc định của trang web các bạn vừa xem là gì
  - /var/www/html/index.html
- Câu hỏi 2: Cổng mặc định của dịch vụ www
  - 80
- Câu hỏi 3: Hãy giải thích quyền mang số 755 
  - 755 = rwxr-xr-x
    - 7: root được quyền đọc, ghi, thực thi
    - 5: group X sở hữu file này thì những người thuộc group X chỉ có quyền đọc và thực thi
    - 5: những user khác chỉ có quyền đọc và thực thi
- Câu hỏi 4: Nội dung quan sát thấy khi vào 2 địa chỉ example.com và test.com
  - example.com

    <image src="./images/1/local-example.png" width=500>

  - test.com

    <image src="./images/1/local-test.png" width=500>

  - Giải thích: khi truy cập example.com hoặc test.com thì dns sẽ đọc file /etc/hosts trước và phân giải 2 doamin này ra 127.0.0.1 và mặc định sẽ truy cập vào port 80. Lúc này apache sẽ đọc các file cấu hình virtual host và các virtual host đều có cấu hình *:80 (chấp nhận kết nối từ mọi IP đến cổng 80) nên apache sẽ tiếp tục đọc ServerName và lúc này sẽ tìm ra đúng cấu hình virtual host ứng với domain và truy cập vào thư mục được định nghĩa và trả về file html, php, ...

- Câu hỏi 5: Truy cập từ máy tính khác cùng mạng lan
  - Không thể truy cập được do example.com và test.com chỉ là local domain

# 2. Interface trong java
- Câu hỏi 6: Viết vòng lặp để gửi array đến người dùng

    <image src="./images/2/Screenshot 2021-10-12 225023.png" width=500>

- Câu hỏi 7: Vai trò của phương thức run
  - Phương thức run có tác dụng nhận đầu vào từ client, sắp xếp lại mảng và trả lại kết quả là mảng dã sắp xếp về phía client
  - Phương thức run là phương thức callback được gọi mỗi khi client gửi message đến server 

- Triển khai các giải thuật sắp xếp khác
  - Shell Sort 

    <image src="./images/2/ShellSort.png" width=500>

  - Insertion Sort 

    <image src="./images/2/InsertionSort.png" width=500>

  - Bubble Sort

    <image src="./images/2/BubbleSort.png" width=500>

# 3. Kiến trúc microservices
- Câu hỏi 1: Mô phỏng lại lệnh build image

    <image src="./images/3/build-image.png" width=500>

- Câu hỏi 2: Push image lên Dockerhub

    <image src="./images/3/dockerhub.png" width=500>

- Câu hỏi 3: Trạng thái của Pod khi mới tạo và sau một thời gian
  - Vừa mới tạo

  <image src="./images/3/before.png" width=500>

  - Sau một thời gian

  <image src="./images/3/after.png" width=500>

# 4. Kiến trúc JMS và DDS
- Câu 1: Vai trò của application server glassfish
  - Ở đây glassfish đóng vài trò như một Event broker, là trung gian để các component trao đổi dữ liệu với nhau thông qua cơ chế pulisher và subscriber
- Câu 2: Tại sao phải tạo 2 JNDI như trên
  - TopicConnectionFactory: là nơi đưa ra kết nối trên server đến chỗ lưu trữ message để từ đó có thể gửi và nhận dữ liệu
  - Topic: Là nơi tiếp nhận, lưu trữ messages
  - Listener: đưa ra cơ chế bất đồng bộ trong việc gửi nhận message
- Câu 3: Giải thích cơ chế chuyền và nhận thông điệp của Sender và Receiver
- Câu 4: So sánh JMS và DDS
  - JMS: 
    - Là chuẩn messages cho phép các thành phần của ứng dụng dựa trên JAVA EE có thể tạo, gửi, nhận, đọc message
    - Cho phép sự truyền thông tin một cách không đồng bộ, đáng tin cậy giữa các thành phần khác nhau, lỏng lẻo của một ứng dụng phân tán.
    - Hỗ trợ cả mô hình point-to-point và publish/subscribe.
    - Tập trung chủ yếu cho các hệ thống Java.
    - Không đảm bảo tính tương thích giữa các publisher và subscriber sử dụng những ứng dụng JMS khác nhau
  - DDS
    - Là chuẩn middleware cho phép trao đổi dữ liệu với hiệu năng cao, mang tính thời gian thực, tương thích giữa publisher và subscriber.
    - Độc lập cả về mặt ngôn ngữ và hệ điều hành. DDS đã được triển khai với nhiều ngôn ngữ lậptrình khác nhau như C++, Java, Ruby, ...
- Cài đặt DDS
  - Publisher

  <image src="./images/4/dds-pub.png" width=500>

  - Subscriber 

  <image src="./images/4/dds-sub.png" width=500>