# 1. Điền Action Nature Card

| Thành phần | Câu trả lời |
| :--- | :--- |
| **Actor** | Một người dùng cá nhân: nhân viên trực ca/điều tra viên VinSOC, dùng tài khoản có quyền xem các camera liên quan. Chỉ tài khoản được phân quyền điều tra mới được bỏ làm mờ khuôn mặt. |
| **Intent** | Có một sự việc cần làm rõ (mất đồ, xe lạ, người khả nghi) và người trực ca phải trả lời nhanh cho người yêu cầu. Nhu cầu là tìm đúng đoạn cảnh liên quan, không phải xem video cho biết. |
| **Trigger** | Sự kiện bên ngoài: ban quản lý, cư dân hoặc một sự cố đặt ra yêu cầu tra cứu. Sau đó người dùng chủ động bắt đầu tìm. Hệ thống không tự kích hoạt tra cứu thay người dùng. |
| **Effort** | Thời gian: gõ một câu mất vài chục giây, xem vài clip mất vài phút; mục tiêu cả lượt tra cứu chỉ vài phút thay vì vài giờ.<br>Suy nghĩ: phải mô tả đối tượng theo lời kể của nhân chứng, thường mơ hồ nên có thể phải chỉnh câu tìm vài lần.<br>Dữ liệu: người dùng không phải nhập thêm gì, vì hệ thống dùng chỉ mục đã dựng sẵn. |
| **Value timing** | Value xuất hiện ngay trong lượt tra cứu, tại lúc người dùng thấy clip khớp. Tuy vậy value phụ thuộc vào công việc đã làm trước đó của hệ thống (chỉ mục dựng sẵn), và chỉ trọn vẹn khi người dùng báo lại hoặc xuất bằng chứng cho người yêu cầu. |
| **State** | Sau action, hệ thống giữ lại: câu truy vấn đã dùng, các clip đã xem, phán quyết khớp/không khớp, clip được đánh dấu làm bằng chứng và ghi chú. Hệ thống cũng ghi nhật ký ai đã xem clip nào và có bỏ làm mờ khuôn mặt hay không. Tất cả lưu trên thiết bị edge và không lưu danh tính nhận dạng. |
| **Dependency** | (1) Camera và edge agent phải hoạt động để chỉ mục có dữ liệu.<br>(2) Video của sự việc còn trong thời hạn lưu trữ.<br>(3) Chất lượng hình ảnh đủ để nhận ra màu áo, balo, phương tiện (ánh sáng, góc quay).<br>(4) Phân quyền điều tra, tức một bước phê duyệt, nếu cần xem rõ mặt.<br>(5) Người yêu cầu cung cấp mô tả đủ rõ về thời điểm và đối tượng. |
| **Repeat condition** | Có sự việc mới cần tra cứu. Ngoài ra còn lặp lại trong cùng một sự việc khi: kết quả lần trước không khớp nên cần chỉnh câu tìm; cần lần theo đối tượng sang camera khác; hoặc người yêu cầu bổ sung thêm chi tiết. |

# 2. Kết luận cadence

Đối với người trực ca/điều tra viên VinSOC, core action tìm bằng câu tiếng Việt rồi xem và xác nhận clip khớp thường xuất hiện theo từng vụ việc phát sinh, không đều theo ngày vì nhu cầu chỉ có khi một sự việc bên ngoài (mất đồ, xe lạ, người khả nghi) đặt ra yêu cầu tra cứu, và số vụ việc mỗi ngày không cố định. Do đó, nhịp đo phù hợp là mỗi vụ việc, tức mỗi lần có một yêu cầu tra cứu, ở cấp vụ việc, sau đó gộp theo ca trực và khu vực để so sánh.