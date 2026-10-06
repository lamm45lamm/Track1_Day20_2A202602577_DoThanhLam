# 1. Product Loop
- Loại loop chính: event-response
- Loop qua hai chu kỳ: Sự việc bên ngoài → tìm và xác nhận clip → có bằng chứng ngay → hồ sơ vụ việc và tên gọi địa điểm được lưu → sự việc kế tiếp → tìm lại, nhanh hơn → lặp lại.
- Metric hypothesis: Nếu loop này hoạt động, tỷ lệ vụ việc cần tra camera được người trực ca xử lý bằng hệ thống sẽ tăng trong 90 ngày đầu thí điểm, vì người đã nhận được clip làm bằng chứng nhanh ở lần đầu sẽ chọn mở hệ thống trước khi tua tay ở sự việc kế tiếp, và tên gọi địa điểm đã lưu làm lần sau nhanh hơn.

# 2. Tracking nhanh

## 2.1. Liệt kê 4–8 core events, mỗi event ghi 4 trường

| Tên event | Ý nghĩa | Thời điểm ghi nhận | Metric sử dụng |
| :--- | :--- | :--- | :--- |
| **search_submitted** | Người trực ca đã gửi một câu tìm hợp lệ và hệ thống đã nhận xử lý. | Khi hệ thống nhận câu tìm hợp lệ và bắt đầu xử lý, không phải lúc người dùng đang gõ. | Mốc bắt đầu của activation; số lần chỉnh câu tìm mỗi vụ việc; tỷ lệ gửi câu tìm đầu tiên sau khi được cấp quyền. |
| **results_returned** | Hệ thống đã trả danh sách kết quả cho một câu tìm. Đây là output của hệ thống, chưa phải value. | Khi danh sách kết quả đầu tiên đã hiển thị cho người dùng. Kèm độ trễ truy vấn, số kết quả, số kết quả thiếu clip hoặc mốc thời gian, và dung lượng chỉ mục hiện tại. | Độ trễ truy vấn và dung lượng chỉ mục; tỷ lệ kết quả bị bỏ qua; số kết quả không có clip thật. |
| **clip_viewed** | Người trực ca đã thực sự xem một clip kết quả. | Khi clip phát đủ một ngưỡng thời gian tối thiểu (mức bắt đầu: 3 giây) hoặc người dùng tua qua đoạn khớp, không phải lúc bấm mở. | Số clip phải xem trước khi xác nhận; tỷ lệ kết quả bị bỏ qua. |
| **match_confirmed** | Core value event. Người trực ca xác nhận một clip khớp đối tượng cần tìm. | Khi phán quyết "khớp" đã được lưu thành công trên thiết bị edge, không phải lúc bấm nút. | Activation; depth và retention; North Star; chỉ báo dẫn dắt về vị trí clip đúng trong danh sách và số người dùng đã activation. Ghi kèm vị trí của clip trong danh sách kết quả. |

## 2.2. Ít nhất 2 tiêu chí nghiệm thu

- Chỉ ghi khi hành vi thật sự hoàn tất. Với match_confirmed  event chỉ được ghi khi dữ liệu đã được lưu thành công trên thiết bị edge. Bấm nút mà lưu lỗi thì không ghi event, và người dùng phải thấy thông báo lỗi.
- Mỗi câu tìm chỉ có một results_returned. Cuộn, phân trang hoặc tải lại trang kết quả không ghi lại. Độ trễ truy vấn đo từ lúc nhận câu tìm đến lúc kết quả đầu tiên hiển thị