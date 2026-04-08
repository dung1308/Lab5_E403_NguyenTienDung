# Tìm lỗi trong spec trong Chủ đề: AI tóm tắt meeting "AI tóm tắt meeting cuộc họp thành bullet. Bắt action items, người chịu trách nhiệm và gửi email tự động".

Kịch bản 1 (processing sai trong thực tế): Trong cuộc họp, sếp nói: "Nam ơi, nhắc phía bên đối tác là chị Lan cần duyệt file thiết kế trước thứ Sáu nhé."
> AI xử lý: AI ghi nhận Action Item: "Chị Lan cần gửi file thiết kế cho đối tác trước thứ Sáu."
> Hậu quả: Email tự động gửi đi yêu cầu Chị Lan làm việc, trong khi thực tế chị ấy là người duyệt, còn Nam mới là người phải liên lạc.
> Nguyên nhân: AI chưa phân biệt được giữa đối tượng được nhắc đến (Target) và người chịu trách nhiệm thực thi (Assignee) trong cấu trúc câu phức tạp.
Kịch bản 2 (Hallucinate): Nhóm thảo luận: "Chúng ta nên xong dự án vào tháng 5, nhưng khách hàng muốn đẩy sớm lên cuối tháng 4. Chốt lại là giữ nguyên lịch cũ nhé."
> AI xử lý: Action Item: "Hoàn thành dự án vào 30/04."
> Hậu quả: Cả đội hoảng loạn vì deadline bị đẩy lên sớm một tháng một cách vô lý.
> Nguyên nhân: AI thường ưu tiên những thông tin đã được đặt trong rule mang tính "khẩn cấp" hoặc những con số xuất hiện sau cùng mà bỏ qua từ khóa phủ định hoặc > sự xác nhận (Confirmation) ở cuối đoạn hội thoại.
Kịch bản 3 (Không hiểu Idioms): Một thành viên phản đối ý tưởng tồi: "Vâng, cứ làm thế đi rồi để cả team đi bán muối hết à?"
> AI xử lý: Action Item: "Cả đội chuẩn bị kế hoạch kinh doanh muối."
> Hậu quả: Email gửi đi một yêu cầu ngớ ngẩn, làm giảm uy tín của hệ thống AI trong mắt nhân sự.
> Nguyên nhân: AI (đặc biệt là các model cũ hoặc chưa tối ưu tiếng Việt) rất kém trong việc hiểu sắc thái mỉa mai hoặc các câu thành ngữ, tục ngữ.
User Story Path bị thiếu: "Vòng lặp phê duyệt" (The Approval Loop) Hầu hết các quy trình tự động hóa đều đi thẳng từ: Họp -> AI Tóm tắt -> Gửi Email. Đây là con đường ngắn nhất dẫn đến thảm họa truyền thông. Path thiếu (The Missing Step): "Với tư cách là người chủ trì cuộc họp, tôi muốn xem lại và chỉnh sửa bản tóm tắt của AI trước khi nó được gửi đi tự động." Tại sao path này quan trọng? Sửa lỗi AI: Như 3 kịch bản trên, con người cần là "chốt chặn" cuối cùng để sửa tên, sửa ngày hoặc xóa những câu đùa vô nghĩa. Bổ sung ngữ cảnh: Đôi khi những quyết định quan trọng nhất lại nằm ở cái gật đầu hoặc cử chỉ hình thể mà AI (chỉ nghe tiếng) không thể bắt được. Gán tên chính xác: Trong cuộc họp, mọi người thường gọi "ông này, bà kia". Người dùng cần vào để gán đúng Email của người chịu trách nhiệm trước khi hệ thống Trigger gửi đi.

Phân tích sản phẩm AI thật
===================
## Phần 1: Khám phá: AI của Momo: Moni
- Trước khi dùng: Đưa ra AI Moni, 1 AI agent có nhiệm vụ trợ lý quản tài chính của chủ tài khoản dùng Momo với các vai trò:
·  Phân tích hành vi chi tiêu 
·  Gợi ý tiết kiệm 
·  Nhắc thanh toán 
·  Hỗ trợ thao tác trong app
·  AI chống fraud 
·  AI recommend dịch vụ 
·  AI hỗ trợ chuyển tiền
·  Scan hóa đơn bằng camera 
·  Gợi ý thao tác chuyển tiền
- Sau khi dùng: + Moni có phân tích dữ liệu  và đọc hành vi chi tiêu khi dùng Momo -> Thống kê chi tiết chi tiêu của mình
+ Đối với những câu từ mơ hồ như “TÌm mẹ tôi” hay “chuyển cho mẹ tôi” -> Moni vẫn tìm dữ liệu và chỉ kết quả là báo lỗi là không tìm thấy, không trả lời câu là một chatbot

## Phần 2 — Phân tích 4 paths (10 phút)


Dùng framework 4 paths để mổ xẻ sản phẩm:
Path	Câu hỏi
### 1. AI đúng
User thấy AI quản lý chi tiêu tốt vì AI có thống kê khoản chi của mình
AI cũng cho user thấy 1 khía cạnh của system prompt của nó
### 2. AI không chắc
Hệ thống sẽ hỏi lại (VD: chỗ vừa tiền? AI hỏi nơi ở/chỗ đi/ và gợi ý ưu đãi)
Hệ thống sẽ bảo không có dữ liệu (Không có thông tin như ưu đãi của sinh viên VinUNI)
### 3. AI sai
Gợi ý nhầm ưu đãi khi ưu đãi chưa cập nhật với thực tế. Thiếu sót chi tiết giao dịch khi hệ thống chưa đồng bộ dữ liệu. Và đôi lúc một số prompt mơ hồ, sai cú pháp AI sẽ bị overtime và thông báo thử lại
### 4. User mất niềm tin
Có 1 nút (bên phải trên cùng) nhờ hỗ trợ trực tuyến với người thật, 
Không thể kết nối với người thật bằng cách chat với Moni
Có manual kể cả trong khi chat Moni (Ko có Moni, manual ?) và bên Momo

- Path “Khi AI đúng” xử lý tốt nhất vì:
+ Xử lý thông tin về tài chính tốt, liệt kê rõ hành vi chi tiêu của người dùng.
+ Chỉ ra khía cạnh của Moni mà người dùng tò mò
- Path “Khi AI sai” yếu nhất vì: + Moni phụ thuộc vào hệ thống và không phụ thuộc vào dữ liệu trong thực tế. VD: Kiểm tra ưu đãi đãi ngộ dành cho sinh viên AI thực chiến ? Moni không biết
+ Những prompt mơ hồ như “bác tôi, mẹ tôi” hay những từ sai cú pháp “thanhg tón” làm Moni suy nghĩ lâu dẫn đến lỗi overtime hoặc trả lời không biết user nói gì

## Gap marketing vs thực tế
- Marketing: "Moni giúp quản lý chi tiêu thông minh"
- Thực tế: Ranh giới giữa "Chủ động" (Proactive) và "Làm phiền" (Intrusive) rất mong manh.
- Gap cảm giác của User: Thấy bị theo dõi và khai thác nỗi sợ hãi ngay lúc đang lo lắng.
# Phần 3 — Sketch "làm tốt hơn" (10 phút)


<img width="176" height="483" alt="as_is1" src="https://github.com/user-attachments/assets/d38c3d71-7e59-4dfd-9d37-712badfec805" />              <img width="211" height="572" alt="to_be" src="https://github.com/user-attachments/assets/72bcf95a-df25-4496-a0a8-17699b8bc380" />


                                                                



> Thêm: 
1. Explain nhẹ (giải thích vì sao AI ra kết quả)
-Hiển thị transaction breakdown
-> User hiểu “AI nghĩ gì” (không còn black box)
2.Confirmation + reassurance
-“Đã cập nhật ” 
-“Moni sẽ ghi nhớ cho lần sau”
> Bỏ:
1. Black-box behavior
-AI đưa kết quả nhưng: 
+Không explain 
+Không trace được nguồn
2. Silent failure
-Sai nhưng: 
+ Không cảnh báo 
+ Không hướng dẫn sửa
> Đổi:
- Từ “AI đoán” đến “AI + user đồng chỉnh”
Before: - AI = nguồn duy nhất : 
+ Before: - AI = nguồn duy nhất
+ After: - User = nguồn feedback trực tiếp


# Phần 4: Share + Vote
-Ý kiến riêng của cá nhân:
> "Mình chọn path yếu nhất là khi AI sai trong MoMo.
> Hiện tại, khi AI phân loại sai, user không biết sai ở đâu, cũng không có cách sửa rõ ràng → đây là điểm gãy khiến trust giảm dần.
>
> Sketch của mình biến insight từ thông tin tĩnh → thành interactive, cho phép user tap vào, xem chi tiết và sửa ngay trong 1–2 bước.
>
> Quan trọng nhất là thêm feedback loop, để mỗi lần user sửa là AI học và cải thiện lần sau.

Ý chính: biến lỗi AI từ điểm gãy thành điểm học."

## Data Flywheel của Momo:
<img width="4004" height="6342" alt="User Intent Analysis-2026-04-08-085727" src="https://github.com/user-attachments/assets/968be943-68be-4a83-a05b-dd297ff202ea" />


# Những sai lầm phá vỡ flywheel
1. Sai lầm "Memory Poisoning" (Nhiễm độc trí nhớ)
> Vấn đề: AI ghi nhận một Prompt nhất thời (ví dụ: "Tìm mua quà cưới") vào Memory dài hạn như một sở thích vĩnh viễn.

Hệ quả: Suốt 6 tháng sau, Moni liên tục báo cáo dữ liệu và gợi ý đồ cưới trong khi người dùng đã xong việc. Flywheel quay sai hướng, gây phiền nhiễu.

2. Sai lầm "Broken Tool Logic" (Lỗi phân nhánh công cụ)
> Vấn đề: Trong sơ đồ, nếu bước "Prompt có liên quan đến tools ko?" bị phân loại sai (ví dụ: yêu cầu báo cáo tài chính lại bị đẩy sang nhánh Overtime).

Hệ quả: Moni trả kết quả không liên quan. Người dùng mất niềm tin vào khả năng "hiểu" của Moni và ngừng nhập Prompt. Bánh đà dừng lại vì thiếu nhiên liệu (Input).

3. Sai lầm "Implicit-only bias" (Quá tin vào dữ liệu ngầm)
> Vấn đề: Hệ thống chỉ phân tích hành vi ngầm (Implicit) mà không cho người dùng sửa lỗi (Correction).

Hệ quả: AI tự suy diễn user đang "vung tay quá trán" chỉ vì họ mới thực hiện một giao dịch mua xe hộ người thân. Điểm Moni giảm oan mà user không biết vì sao.

# Dữ liệu Sửa lỗi (Correction) - Quan trọng nhất để "Cứu" Flywheel
Đây là chốt chặn cuối cùng khi AI dự đoán sai, tác động trực tiếp vào node "Củng cố Memory".
Dữ liệu cần:

Ghi đè danh mục: Nếu Moni báo cáo sai một khoản chi tiêu, user phải có nút "Không phải, đây là tiền Tiết kiệm".

Chỉnh sửa Prompt: Nếu Moni hiểu sai ý định, cho phép user nhấn "Ý tôi không phải vậy" để nhập lại. Hành động sửa lỗi này là "vàng ròng" để AI học được logic đúng của cá nhân đó.

# Dữ liệu Trực tiếp (Explicit) - Quan trọng thứ 2 - Để đánh giá "Dự đoán yêu cầu"
Dùng để kiểm chứng node "Moni dự đoán yêu cầu".

Dữ liệu cần:

Tháp đánh giá (Thumbs up/down): Ngay sau khi Moni trả dữ liệu, hãy hỏi: "Thông tin này có ích không?".

Khảo sát nhanh: "Bạn muốn tôi nhớ sở thích này trong bao lâu? (Chỉ hôm nay / Mãi mãi)". Điều này giải quyết sai lầm "Memory Poisoning".

# Dữ liệu Ngầm (Implicit) - Để "Củng cố Memory"
Đây là dữ liệu thu thập không làm phiền người dùng, dùng để tối ưu node "Phân tích hành vi".

Dữ liệu cần:

Thời gian dừng (Dwell time): User dừng lại bao lâu để đọc bản "Báo cáo dữ liệu". Nếu họ lướt qua cực nhanh -> Báo cáo chưa đủ hấp dẫn/đúng ý.

Tỷ lệ chuyển đổi: Sau khi Moni trả dữ liệu/gợi ý, user có thực hiện hành vi tiêu tiền (thanh toán) không?

Tần suất mở Moni: Đo lường độ "nghiện" của user với trợ lý này.



