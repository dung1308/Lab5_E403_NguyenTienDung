Data Flywheel của Momo:
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
