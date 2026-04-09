# 1. Role
Người tạo các test cases và hỗ trợ tìm các tiêu chí đánh giá AI (eval metrics) để kiểm đo chất lượng của chatbot.

# 2. Đóng góp
## Thiết kế bộ câu hỏi
Tạo ra bộ test cases mẫu để kiểm đo chất lượng chatbot. Một test case sẽ có các thông tin như: nội dung câu hỏi của người dùng, vấn đề mà người dùng hỏi thuộc vào loại nào, câu trả lời kỳ vọng sẽ như thế nào, nguồn ở đâu? Sau đây là ví dụ cụ thể:
- "id": "TC_001",
- "category": "Quy định hành lý",
- "question": "Tôi đặt Xanh Bike nhưng mang theo một thùng hàng cồng kềnh phía sau. Tài xế có quyền từ chối chở tôi không?",
- "expected_answer": "Có. Đối tác (Tài xế) có quyền từ chối cung cấp Sản Phẩm nếu Người dùng mang theo đồ vật quá khổ mà Đối tác đánh giá là có khả năng vi phạm quy định pháp luật về giao thông hoặc không đảm bảo nguyên tắc an toàn.",
- "source": "6_quy_chế_sử_dụng_sản_phẩm_xanh_bike.md, Mục 3.3"

## 3. Xác định tiêu chí đánh giá AI (Eval metrics)
- Chính xác về số liệu, thứ ngày tháng (số liệu đưa ra phải đúng thì mới xét đến ngữ nghĩa, nếu số liệu sai thì đánh gái là không đạt luôn, không cần xét đến ngũ nghĩa)
- Về ngữ nghĩa: nếu câu trả lời của chatbot và câu trả lời kỳ vọng giống nhau trên 60% là đạt yêu cầu.

Sau khi có bộ test case và bộ chỉ số đánh giá này thì người triển khai hệ thống kiểm thử sẽ xây dựng hệ thống kiểm trử dựa trên 1 mô hình LLM khác để đánh giá chất lượng chatbot.

# 4. Phần nào mạnh nhất, phần nào yếu nhất, vì sao?

## Điểm mạnh
Hiểu đúng bản chất vấn đề để đưa ra lựa chọn là agumentation thay vì automation. Lý do côt lõi là phục vụ các tình huống liên quan trực tiếp đến tiền bạc, pháp luật, phúc lợi, thưởng, phạt, sự cố v.v... Vì nếu AI đưa ra kết qua sai và dẫn dắt người dùng làm theo sẽ gây ra kết quả không thể chấp nhận được.

## Điểm yếu
Thiếu chi tiết về evaluation implementation. Nhóm đã có test cases và eval metrics nhưng chưa đề cập đến cách triển khai đánh giá Chatbot tự động trong specs.

# 5. 1 điều học được trong hackathon mà trước đó chưa biết
Lần này tôi đã học được cách đánh giá tự động một mô hình LLM - chatbot thực sự như thế nào. Đó là sử dụng LLM kết hợp rule-based để kiểm tra LLM. Cùng với đó là rất nhiều chỉ số để đánh giá độ tin cậy của chatbot.

# 6. Nếu được làm lại
Tôi sẽ khắc phục điểm yếu của nhóm đó là chưa có mô tả chi tiết cho phần triển khai kiểm đo Chatbot. Tôi sẽ làm phần đó chi tiết hơn, nói rõ là sẽ kiểm đo tự động như thế nào, dùng những chỉ số gì v.v...

# 7. AI giúp gì/ AI sai gì
## AI giúp gì
- Tạo test case nhanh hơn, tôi không phải gõ phím nữa, AI đưa ra câu hỏi và gợi ý câu trả lời kỳ vọng cùng trích dẫn nguồn.
- Gợi ý cách thức test tự động như thế nào và các eval metrics phù hợp.
## AI sai gì
- Dùng AI để tạo test case phải kiểm tra rất kỹ vì nó rất hay bị lỗi ảo giác.