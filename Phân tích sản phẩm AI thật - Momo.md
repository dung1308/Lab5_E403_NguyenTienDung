#Phân tích sản phẩm AI thật
Phần 1: Khám phá: AI của Momo: Moni
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

Phần 2 — Phân tích 4 paths (10 phút)

Dùng framework 4 paths để mổ xẻ sản phẩm:
Path	Câu hỏi
1. Khi AI đúng	User thấy AI quản lý chi tiêu tốt vì AI có thống kê khoản chi của mình
AI cũng cho user thấy 1 khía cạnh của system prompt của nó
2. Khi AI không chắc	Hệ thống sẽ hỏi lại (VD: chỗ vừa tiền? AI hỏi nơi ở/chỗ đi/ và gợi ý ưu đãi)
Hệ thống sẽ bảo không có dữ liệu (Không có thông tin như ưu đãi của sinh viên VinUNI)
3. Khi AI sai	Gợi ý nhầm ưu đãi khi ưu đãi chưa cập nhật với thực tế. Thiếu sót chi tiết giao dịch khi hệ thống chưa đồng bộ dữ liệu. Và đôi lúc một số prompt mơ hồ, sai cú pháp AI sẽ bị overtime và thông báo thử lại
4. Khi user mất tin	Có 1 nút (bên phải trên cùng) nhờ hỗ trợ trực tuyến với người thật, 
Không thể kết nối với người thật bằng cách chat với Moni
Có manual kể cả trong khi chat Moni (Ko có Moni, manual ?) và bên Momo

- Path “Khi AI đúng” xử lý tốt nhất vì:
+ Xử lý thông tin về tài chính tốt, liệt kê rõ hành vi chi tiêu của người dùng.
+ Chỉ ra khía cạnh của Moni mà người dùng tò mò
- Path “Khi AI sai” yếu nhất vì: + Moni phụ thuộc vào hệ thống và không phụ thuộc vào dữ liệu trong thực tế. VD: Kiểm tra ưu đãi đãi ngộ dành cho sinh viên AI thực chiến ? Moni không biết
+ Những prompt mơ hồ như “bác tôi, mẹ tôi” hay những từ sai cú pháp “thanhg tón” làm Moni suy nghĩ lâu dẫn đến lỗi overtime hoặc trả lời không biết user nói gì

Phần 3 — Sketch "làm tốt hơn" (10 phút)


<img width="176" height="483" alt="as_is1" src="https://github.com/user-attachments/assets/d38c3d71-7e59-4dfd-9d37-712badfec805" />              <img width="211" height="572" alt="to_be" src="https://github.com/user-attachments/assets/72bcf95a-df25-4496-a0a8-17699b8bc380" />


                                                                



Thêm: 
1. Explain nhẹ (giải thích vì sao AI ra kết quả)
-Hiển thị transaction breakdown
-> User hiểu “AI nghĩ gì” (không còn black box)
2.Confirmation + reassurance
-“Đã cập nhật ” 
-“Moni sẽ ghi nhớ cho lần sau”
Bỏ: 1. Black-box behavior
-AI đưa kết quả nhưng: 
+Không explain 
+Không trace được nguồn
2. Silent failure
-Sai nhưng: 
+ Không cảnh báo 
+ Không hướng dẫn sửa 
Đổi: 1. Từ “AI đoán” → “AI + user đồng chỉnh”
Before:
- AI = nguồn duy nhất 
After:
- User = nguồn feedback trực tiếp
Chốt lại: “Chuyển failure từ điểm gãy thành điểm tương tác — nơi user không chỉ sửa dữ liệu mà còn huấn luyện lại AI.”

Phần 4: Vote



