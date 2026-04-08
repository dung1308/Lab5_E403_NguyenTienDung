1.Tìm lỗi trong spec trong Chủ đề:
AI tóm tắt meeting "AI tóm tắt meeting cuộc họp thành bullet. Bắt action items, người chịu trách nhiệm và gửi email tự động".

- Kịch bản 1 (processing sai trong thực tế): Trong cuộc họp, sếp nói: "Nam ơi, nhắc phía bên đối tác là chị Lan cần duyệt file thiết kế trước thứ Sáu nhé."
+ AI xử lý: AI ghi nhận Action Item: "Chị Lan cần gửi file thiết kế cho đối tác trước thứ Sáu."
+ Hậu quả: Email tự động gửi đi yêu cầu Chị Lan làm việc, trong khi thực tế chị ấy là người duyệt, còn Nam mới là người phải liên lạc.
+ Nguyên nhân: AI chưa phân biệt được giữa đối tượng được nhắc đến (Target) và người chịu trách nhiệm thực thi (Assignee) trong cấu trúc câu phức tạp.
- Kịch bản 2 (Hallucinate): Nhóm thảo luận: "Chúng ta nên xong dự án vào tháng 5, nhưng khách hàng muốn đẩy sớm lên cuối tháng 4. Chốt lại là giữ nguyên lịch cũ nhé."
+ AI xử lý: Action Item: "Hoàn thành dự án vào 30/04."
+ Hậu quả: Cả đội hoảng loạn vì deadline bị đẩy lên sớm một tháng một cách vô lý.
+ Nguyên nhân: AI thường ưu tiên những thông tin đã được đặt trong rule mang tính "khẩn cấp" hoặc những con số xuất hiện sau cùng mà bỏ qua từ khóa phủ định hoặc sự xác nhận (Confirmation) ở cuối đoạn hội thoại.
- Kịch bản 3 (Không hiểu Idioms): Một thành viên phản đối ý tưởng tồi: "Vâng, cứ làm thế đi rồi để cả team đi bán muối hết à?"
+ AI xử lý: Action Item: "Cả đội chuẩn bị kế hoạch kinh doanh muối."
+ Hậu quả: Email gửi đi một yêu cầu ngớ ngẩn, làm giảm uy tín của hệ thống AI trong mắt nhân sự.
+ Nguyên nhân: AI (đặc biệt là các model cũ hoặc chưa tối ưu tiếng Việt) rất kém trong việc hiểu sắc thái mỉa mai hoặc các câu thành ngữ, tục ngữ.
2. User Story Path bị thiếu: "Vòng lặp phê duyệt" (The Approval Loop)
Hầu hết các quy trình tự động hóa đều đi thẳng từ: Họp -> AI Tóm tắt -> Gửi Email. Đây là con đường ngắn nhất dẫn đến thảm họa truyền thông.
Path thiếu (The Missing Step):
"Với tư cách là người chủ trì cuộc họp, tôi muốn xem lại và chỉnh sửa bản tóm tắt của AI trước khi nó được gửi đi tự động."
Tại sao path này quan trọng?
Sửa lỗi AI: Như 3 kịch bản trên, con người cần là "chốt chặn" cuối cùng để sửa tên, sửa ngày hoặc xóa những câu đùa vô nghĩa.
Bổ sung ngữ cảnh: Đôi khi những quyết định quan trọng nhất lại nằm ở cái gật đầu hoặc cử chỉ hình thể mà AI (chỉ nghe tiếng) không thể bắt được.
Gán tên chính xác: Trong cuộc họp, mọi người thường gọi "ông này, bà kia". Người dùng cần vào để gán đúng Email của người chịu trách nhiệm trước khi hệ thống Trigger gửi đi.

