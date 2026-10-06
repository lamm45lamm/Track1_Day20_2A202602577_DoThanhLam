# 1. Phân biệt bốn khái niệm

| Khái niệm | Câu hỏi | Nội dung |
| :--- | :--- | :--- |
| **Dự án này Core job** | User đang cố hoàn thành việc gì? | Tìm ra đúng đoạn cảnh liên quan đến sự việc trong vài phút thay vì tua tay hàng giờ, và chắc chắn đó là cảnh thật. |
| **Core action** | User làm gì trong sản phẩm để tiến tới giá trị? | Gõ một câu tìm kiếm tiếng Việt, mở clip kết quả và xem để xác nhận đúng đối tượng cần tìm. |
| **Core value** | User nhận được lợi ích gì? | Có ngay đoạn clip và mốc thời gian làm bằng chứng để báo lại, mất vài phút thay vì vài giờ. |
| **Core value event** | Sự kiện nào chứng minh value đã xảy ra? | Người trực ca xác nhận một clip kết quả là đúng đối tượng cần tìm. |

# 2. Điền Core Action Card

| Thành phần | Câu trả lời |
| :--- | :--- |
| **Target user** | Nhân viên trực ca/điều tra viên tại trung tâm VinSOC của khu đô thị. |
| **Core job** | Tìm ra đúng đoạn cảnh liên quan đến sự việc trong vài phút thay vì tua tay hàng giờ, và chắc chắn đó là cảnh thật. |
| **Core action** | Gõ một câu tìm kiếm tiếng Việt, mở clip kết quả và xem để xác nhận đúng đối tượng cần tìm. |
| **Object** | Clip sự kiện từ camera trong chỉ mục (có camera, mốc thời gian và thuộc tính người/vật/xe/hành động). |
| **Preconditions** | (1) Edge agent đã trích xuất đặc trưng và lập chỉ mục video của các camera cần tra, chạy được offline. (2) Người dùng đã đăng nhập và có quyền xem camera đó. (3) Người dùng nêu được ít nhất một điều kiện tìm kiếm (đối tượng, thuộc tính, khu vực hoặc khung giờ). (4) Khuôn mặt trong kết quả được làm mờ mặc định; chỉ bỏ làm mờ khi có phân quyền điều tra. |
| **Completion rule** | Action hoàn tất khi người dùng đã mở ít nhất một clip kết quả, xem và đưa ra phán quyết "khớp" hoặc "không khớp". Chỉ phán quyết "khớp" mới chuyển thành value. |
| **Core value** | Có ngay đoạn clip và mốc thời gian thật làm bằng chứng để báo lại, mất vài phút thay vì vài giờ. |
| **Evidence of value** | Một clip được đánh dấu "khớp" kèm camera và mốc thời gian; thời gian từ lúc gửi truy vấn đến lúc xác nhận ngắn (mục tiêu: vài phút); clip có thể xuất làm bằng chứng. |
| **Candidate event** | Người trực ca xác nhận một clip khớp đối tượng cần tìm (ghi lại: câu truy vấn, clip/camera, mốc thời gian, thời gian phản hồi, số clip đã xem, trạng thái làm mờ mặt). Gửi truy vấn; hệ thống trả kết quả (độ trễ, dung lượng chỉ mục); mở xem một clip. |

# 3. Tự kiểm 5 tiêu chí

| # | Tiêu chí | Kết quả | Lý giải |
| :--- | :--- | :--- | :--- |
| 1 | Gần core value | Đạt | Core value là có đúng đoạn cảnh làm bằng chứng. Khi người trực ca xem clip và xác nhận khớp, họ đã có thứ cần báo lại, không còn bước nào đáng kể nữa. Hành vi không dừng ở thao tác giao diện như mở ứng dụng hay gõ câu hỏi, vì phải có bước xem và phán quyết. |
| 2 | Có thể lặp lại | Đạt | Mỗi sự việc mới (mất đồ, xe lạ, người khả nghi) đều kéo người trực ca quay lại tra cứu. Tần suất phụ thuộc số vụ việc, nên cần đo theo từng ca trực chứ không chỉ theo ngày. |
| 3 | Có thể quan sát | Đạt  | Mốc hoàn tất rõ: lúc người dùng bấm xác nhận "khớp" hoặc "không khớp". Rủi ro là người trực ca chỉ ghi lại mốc giờ rồi thoát mà không bấm xác nhận. Cách xử lý: gắn bước xác nhận vào thao tác xuất clip làm bằng chứng để họ có lý do dùng nó. |
| 4 | Có ý nghĩa | Đạt  | Số lần xác nhận tăng chưa chắc là sản phẩm tốt hơn, vì có thể chỉ do tháng đó nhiều sự việc hơn, hoặc do người dùng xác nhận nhầm. Vì vậy không đo số lượng đơn thuần mà đo tỷ lệ truy vấn kết thúc bằng một clip khớp và thời gian từ lúc gửi truy vấn đến lúc xác nhận. Nếu hai chỉ số này cải thiện thì sản phẩm thật sự tốt hơn. |
| 5 | Có thể tác động | Đạt | Team cải thiện được trực tiếp: độ chính xác và độ phủ của chỉ mục thuộc tính (màu áo, balo, phương tiện), khả năng hiểu truy vấn tiếng Việt, độ trễ truy vấn, và cách xếp thứ tự clip kết quả. |


Core action không phải "mở ứng dụng", "đăng nhập" hay "hỏi AI", vì giá trị chỉ xảy ra sau khi người dùng xem và xác nhận clip. Câu chữ cũng không mơ hồ kiểu "sử dụng sản phẩm" hay "có trải nghiệm tốt", vì có đối tượng (clip), mốc hoàn tất (phán quyết khớp) và bằng chứng (clip kèm mốc thời gian).

