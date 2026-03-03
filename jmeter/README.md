Báo cáo bài tập test bằng jmeter
Công cụ: Apache JMeter 5.6.3 
Website kiểm thử:https://blazedemo.com
Mục tiêu:Đánh giá hiệu năng và khả năng chịu tải của hệ thống dưới các mức tải khác nhau.

- Kịch bản kiểm thử:
+ Kịch bản 1:  Thread Group 1 – Basic Load Test
Cấu hình:
- Threads (Users): 5
- Ramp-up Period: 5 giây
- Loop Count: 10
- Hành vi: HTTP GET trang chủ
Kết quả:
<img width="1446" height="311" alt="image" src="https://github.com/user-attachments/assets/1dbaf4b5-3d55-4feb-b9c1-c77ee69e773e" />
 Phân tích:
- Không có lỗi phát sinh.
- Hệ thống phản hồi ổn định khi tải thấp.

+ Kịch bản 2: Thread Group 2 – Heavy Load Test
Cấu hình:
- Threads (Users): 10
- Ramp-up Period: 5 giây
- Loop Count: 15
- Hành vi:
  + HTTP GET trang chủ `/`
  + HTTP GET trang đặt vé `/reserve.php`
 Kết quả:
<img width="1465" height="353" alt="image" src="https://github.com/user-attachments/assets/29536b75-9114-4445-b693-2f69a62ebc19" />
Phân tích:
- Thời gian phản hồi tăng nhẹ so với TG1.
- Không xuất hiện lỗi.
- Website vẫn hoạt động ổn định khi tải tăng gấp đôi.

+ Kịch bản 3: Custom Stress Test (60 giây)
Cấu hình:
- Threads (Users): 20
- Ramp-up Period: 10 giây
- Duration: 60 giây
- Loop Count: Infinite
- Hành vi: HTTP POST gửi form đặt vé `/purchase.php`
Kết quả:
<img width="1443" height="365" alt="image" src="https://github.com/user-attachments/assets/b787cda1-e2b1-4547-ba04-70588105c1b3" />
Phân tích:
- Không phát sinh lỗi trong suốt 60 giây.
- Response time ổn định ngay cả khi tải liên tục.
- Chứng tỏ hệ thống có khả năng chịu tải tốt ở mức trung bình.

+ Nhận xét tổng quan:
- Khi số lượng người dùng tăng, response time tăng nhưng vẫn trong mức chấp nhận được.
- Không xuất hiện lỗi trong cả 3 kịch bản.
- Throughput tăng tương ứng với số lượng user.
- Website duy trì được tính ổn định dưới tải liên tục 60 giây.
+ Đánh giá & Kết luận:
- Hệ thống hoạt động ổn định dưới tải thấp và trung bình  
- Không phát sinh lỗi (Error rate = 0%)  
- Thời gian phản hồi trung bình < 500ms  
- Khả năng xử lý request/giây tốt trong stress test  
