# 1. Activation metric

Start event: Người trực ca gửi câu tìm đầu tiên trên dữ liệu camera thật của một vụ việc thật, sau khi chỉ mục của các camera liên quan đã sẵn sàng. Không dùng "đăng nhập" hay "hoàn thành hướng dẫn" làm mốc bắt đầu.

Activation event: Lần đầu tiên người dùng xác nhận một clip kết quả là khớp đối tượng cần tìm. Đây chính là first value: người dùng đã có đoạn cảnh thật kèm camera và mốc thời gian để báo lại.

Time window: Trong vòng 15 phút kể từ câu tìm đầu tiên, trong cùng một lượt tra cứu. Con số này suy ra từ core job ("vài phút thay vì vài giờ") và là mức tạm thời, cần hiệu chỉnh theo thời gian tua tay thực tế mà người trực ca đang mất ở khu đô thị đó.

# 2. Engagement metric

Chọn góc đo **Depth**: thời gian từ câu tìm đầu tiên đến lần xác nhận khớp đầu tiên, số lần phải chỉnh câu tìm, số clip phải xem trước khi xác nhận, và tỷ lệ clip khớp được xuất làm bằng chứng (value trọn vẹn là có thứ để báo lại). Với sản phẩm AI, xong việc nhanh và ít vòng chỉnh là tín hiệu tốt hơn dùng lâu. Đây là góc đo gần value nhất.

# 3. Retention Definition 

| Thành phần | Câu trả lời |
| :--- | :--- |
| **Unit** | Trung tâm VinSOC của một khu đô thị (account). Nhu cầu phát sinh theo sự việc của khu đô thị và nhân sự trực ca luân phiên, nên đo từng người sẽ bị méo: người nghỉ ca không có nghĩa là bỏ sản phẩm. Activation vẫn đo ở cấp người dùng mới, retention đo ở cấp trung tâm. |
| **Cohort entry** | Trung tâm vào cohort khi người dùng đầu tiên của trung tâm đạt activation (lần xác nhận khớp đầu tiên). Cohort chia theo tháng đạt activation. |
| **Return event** | Một vụ việc mới, khác vụ việc đã kích hoạt, kết thúc bằng việc người trực ca xác nhận clip khớp. Chỉ tính khi value xảy ra, không tính việc chỉ mở hệ thống hay chỉ gửi câu tìm. |
| **Window** | Khung tùy chỉnh theo từng nhóm khu đô thị, không dùng một window chung cho tất cả. Quy tắc: độ dài khung không ngắn hơn khoảng cách thường gặp giữa hai vụ việc cần tra camera, lấy từ sổ vụ việc của chính khu đô thị đó. Mức bắt đầu: khu đô thị nhiều vụ việc dùng khung 30 ngày liên tiếp; khu đô thị ít vụ việc dùng khung 90 ngày. Hai mức này là tạm thời và được chốt lại khi có số liệu thực. |
| **Threshold** | Mức cơ bản: ít nhất một vụ việc có xác nhận khớp trong khung, vì số vụ việc mỗi khung có thể rất ít. Mức mạnh hơn: trung tâm xử lý từ một nửa số vụ việc cần tra camera trở lên bằng hệ thống. |
| **Segment** | Các khu đô thị trong giai đoạn thí điểm đã có camera được lập chỉ mục và người dùng được cấp quyền. Chia thêm theo quy mô (số camera) và theo tần suất vụ việc (thấp/cao), vì tần suất vụ việc quyết định độ dài khung. |

So retention với ba mốc:

- Chu kỳ tự nhiên: so tỷ lệ quay lại với khoảng cách thực tế giữa các vụ việc của khu đô thị đó. Khu đô thị chỉ có vụ việc mỗi vài tháng thì tỷ lệ quay lại trong 30 ngày thấp là bình thường.
- Cohort đúng segment: so các khu đô thị cùng quy mô và cùng mức tần suất vụ việc với nhau.
- Benchmark category: hiện chưa có số liệu đáng tin về mức duy trì của công cụ tra cứu video an ninh cùng loại. Cần tìm nguồn trước khi so sánh, và trong lúc chờ thì không dùng con số lấy từ sản phẩm khác.

# 4. North Star + leading + counter

- North Star Metric: Số vụ việc mỗi tháng được tìm ra đúng đoạn clip làm bằng chứng trong vòng 15 phút, với clip được người trực ca xác nhận khớp và khuôn mặt chỉ được bỏ làm mờ khi có phân quyền điều tra.
- Leading indicators: Tỷ lệ trung tâm đạt activation mỗi tháng (người đã thấy hệ thống tìm đúng ngay lần đầu sẽ tin dùng nó cho vụ việc sau, thay vì quay lại tua tay).
- Counter-metrics: Số lần bỏ làm mờ khuôn mặt ngoài phân quyền điều tra do ràng buộc quyền riêng tư không được đổi lấy tốc độ.