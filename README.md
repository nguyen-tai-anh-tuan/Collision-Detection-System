# Hệ Thống Cảnh Báo Va Chạm
<p align="justify">
Dự án này triển khai một **hệ thống phát hiện và cảnh báo va chạm** dựa trên vi điều khiển STM32F103C8T6.  
Hệ thống đo khoảng cách bằng cảm biến siêu âm, đánh giá nguy cơ va chạm tiềm ẩn, và đưa ra cảnh báo thông qua đèn LED và còi báo.  
Ngoài ra, toàn bộ dữ liệu được xử lý và truyền qua **bus CAN** sử dụng bộ thu phát MCP2551 để tích hợp với các hệ thống ô tô khác.
</p>

# **🚗 Tính Năng**

Phát hiện va chạm theo thời gian thực bằng 3 cảm biến siêu âm JSN-SR04
Điều khiển trung tâm với STM32F103C8T6 (Blue Pill)
Cảnh báo trực quan và âm thanh bằng đèn LED và còi
Truyền dữ liệu qua bus CAN (bộ thu phát MCP2551)
Chu kỳ đo ổn định 1 Hz
Hoạt động tin cậy với lọc nhiễu và phát hiện ngưỡng (giới hạn an toàn 3.5 m)


# **🔧 Linh Kiện Phần Cứng**

STM32F103C8T6 (MCU ARM Cortex-M3)
Cảm biến siêu âm JSN-SR04 × 3
Bộ thu phát CAN MCP2551
Đèn LED báo hiệu × 2
Còi báo × 1
Linh kiện hỗ trợ: điện trở, tụ điện, IC ổn áp, PCB


# **💻 Phần Mềm**

Phát triển bằng ngôn ngữ C sử dụng ArduinoIDE
Các chức năng được triển khai:

Kích hoạt cảm biến siêu âm tuần tự
Thu nhận và xử lý tín hiệu Echo
Tính toán khoảng cách bằng phương pháp thời gian bay (time-of-flight)
So sánh với ngưỡng an toàn (3.5 m)
Kích hoạt đèn LED và còi cảnh báo
Gửi gói dữ liệu qua bus CAN (giao thức CAN 2.0)




# **📐 Thiết Kế Hệ Thống**

Khối Xử Lý Trung Tâm: Lõi STM32 xử lý toàn bộ logic cảm biến và điều khiển
Khối Truyền Thông: Bộ thu phát MCP2551 cho giao tiếp bus CAN
Khối Cảnh Báo: Đèn LED và còi báo cảnh báo theo thời gian thực


# **⚙️ Cài Đặt & Sử Dụng**

Lắp ráp phần cứng theo sơ đồ mạch và layout PCB được cung cấp.
Kết nối ST-Link programmer để nạp firmware vào STM32.
Cấp nguồn 5V (đã ổn áp) cho hệ thống.
Đặt vật cản trong phạm vi 2.5 – 3.5 m để kiểm tra phát hiện va chạm.
Quan sát hoạt động của đèn LED và còi báo, đồng thời xác minh các gói tin CAN bằng thiết bị phân tích CAN.

Lưu ý: Trong thư mục /lib có file thư viện nhỏ cho bus CAN. Bạn có thể tải xuống và import file đó vào code.
Cách thêm thư viện trong ArduinoIDE:
Bước 1: ArduinoIDE -> Sketch -> Include Library -> Add .ZIP Library
<img width="560" height="560" alt="image" src="https://github.com/user-attachments/assets/5c8d1dea-0039-4d2e-960a-6528d86a70b2" />  
Bước 2 (chọn file zip):  
<img width="560" height="102" alt="image" src="https://github.com/user-attachments/assets/ac72b799-3f64-46e8-a3a8-660aa5f1173c" />  
Bước 3: và chờ đợi  

# **📊 Kết Quả**

Hoạt động ổn định với tần số đo 1 Hz
Thời gian xử lý trung bình: <200 ms
Cảnh báo rõ ràng và đáng tin cậy khi phát hiện vật thể dưới ngưỡng an toàn
Gói tin CAN được truyền thành công và xác thực bằng công cụ phân tích CAN


# **🚀 Hướng Phát Triển Trong Tương Lai**

Mở rộng phạm vi phát hiện cho các tình huống tốc độ cao hơn
Thêm nhiều cảm biến hơn để giám sát 360°
Tích hợp bộ lọc nâng cao (Kalman, phát hiện đối tượng dựa trên AI)
Cung cấp giao diện đồ họa (màn hình LCD hoặc bảng điều khiển PC)
Cho phép các hành động tự động (phanh tự động, hỗ trợ lái)


# **📷 Hình Ảnh Dự Án **   
Phần Cứng  
<img width="560" height="560" alt="image" src="https://github.com/user-attachments/assets/81023ccd-2d6b-4269-b37c-a41cdb7bfdd6" />  
Kiểm Thử Phần Mềm  
<img width="560" height="560" alt="image" src="https://github.com/user-attachments/assets/7edf0383-636f-4830-82ea-abc735444d48" />  
