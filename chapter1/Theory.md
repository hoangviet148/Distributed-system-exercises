```
Họ và tên: Ngọ Việt Hoàng
MSSV: 20183748
Mã lớp: 128745
Mã HP: IT4611
```

# Câu 1:
- HDFS (distributed filesystem): 
  - filesystem được lưu trên một cluster => các máy tính độc lập
  - các máy tính kết nối và chứa các bản sao của nhau
  - cung cấp đến users như là 1 filesystem duy nhất, người dùng không cần quan tâm file đang thao tác thuộc máy nào
- Mysql Replication: distributed database
  - data được lưu trên nhiều máy, ít nhất 2 máy (1 master và 1 slave)
  - các máy tính kết nối và đồng bộ dữ liệu (mỗi khi có transaction thì slave node sẽ đồng bộ dữ liệu từ master node)
  - data được ghi vào master và được đọc từ slave nhưng user không cần quan tâm đến điều này
# Câu 2:
# Câu 3:
# Câu 4:
# Câu 5:
# Câu 6:
# Câu 7:
- Giao thức MQTT (Message Queuing Telemetry Transport)

    <image src="./images/theory/mqtt.png" width=500>

  - Sử sụng băng thông thấp, độ tin cậy cao và có khả năng hoạt động trong điều kiện đường truyền không ổn định
  - Hệ thống gồm nhiều node trạm (mqtt client) kết nối đến một MQTT server (broker)
  - Mỗi client sẽ đăng ký một vài kênh (topic), ví dụ như "/client1/channel1", "/client1/channel2". Quá trình đăng ký này gọi là "subscribe". Mỗi client sẽ nhận được dữ liệu khi bất kỳ trạm nào khác gửi dữ liệu vào kênh đã đăng ký.
  - Khi một client gửi dữ liệu tới kênh đó, gọi là "publish".
# Câu 8:
# Câu 9:
# Câu 10:
# Câu 11:
# Câu 12: