# Role
Người tạo các test cases để kiểm tra và đánh giá sự chính xác và ổn định của chatbot.

# Đóng góp
Tạo ra hơn 100 test cases để kiểm tra xem chatbot có đưa ra câu trả lời đúng không. Một test case sẽ có các thông tin như: nội dung câu hỏi của người dùng, vấn đề mà người dùng hỏi thuộc vào loại nào, câu trả lời kỳ vọng sẽ như thế nào, nguồn ở đâu? Sau đây là ví dụ cụ thể:
- "id": "TC_001",
- "category": "Quy định hành lý",
- "question": "Tôi đặt Xanh Bike nhưng mang theo một thùng hàng cồng kềnh phía sau. Tài xế có quyền từ chối chở tôi không?",
- "expected_answer": "Có. Đối tác (Tài xế) có quyền từ chối cung cấp Sản Phẩm nếu Người dùng mang theo đồ vật quá khổ mà Đối tác đánh giá là có khả năng vi phạm quy định pháp luật về giao thông hoặc không đảm bảo nguyên tắc an toàn.",
- "source": "6_quy_chế_sử_dụng_sản_phẩm_xanh_bike.md, Mục 3.3"
Sau khi có bộ test case này thì người triển khai hệ thống kiểm thử sẽ xây dựng hệ thống kiểm trử dựa trên 1 mô hình LLM khác để đánh giá xem câu trả lời của chatbot có giống với câu trả lời kỳ vọng không.

# Reflection

Tham gia dự án xây dựng trợ lý AI cho tài xế XanhSM, tôi phụ trách tạo **test cases**. Ban đầu, tôi nghĩ đây chỉ là một công việc nhàm chán là viết câu hỏi và kiểm tra xem AI trả lời đúng với tài liệu hay không. Tuy nhiên, trong quá trình làm, tôi nhận ra bản chất của bài toán này phức tạp hơn rất nhiều: đây không phải là bài toán “AI trả lời hay”, mà là bài toán **AI có đáng tin hay không** trong một môi trường có ràng buộc rất cao và không cần nhiều sự linh hoạt.

Thay đổi lớn nhất trong tư duy của tôi là chuyển từ việc chỉ kiểm tra độ đúng (accuracy) sang kiểm tra độ an toàn và độ tin cậy (safety & reliability).. Vì vậy, tôi bắt đầu thiết kế test cases không chỉ để xác nhận câu trả lời đúng, mà còn để phát hiện các lỗi tiềm ẩn như AI bịa thông tin (hallucination), trả lời khi không chắc chắn (overconfidence), và không biết khi nào cần từ chối trả lời hoặc chuyển sang hotline.

Một điều tôi học được là test cases không chỉ dùng để “chấm điểm” hệ thống, mà còn đóng vai trò định hình hành vi của AI. Khi tôi bổ sung các test dạng “negative case” (câu hỏi không có trong tài liệu) và “trap case” (câu hỏi dễ khiến AI bị dẫn dắt), tôi đang buộc hệ thống phải tuân theo nguyên tắc: chỉ trả lời khi có căn cứ, và phải trung thực khi không biết. Điều này giúp tôi hiểu rõ hơn rằng evaluation không phải là bước sau cùng, mà là một phần quan trọng trong quá trình thiết kế sản phẩm AI.

Một hạn chế của tôi trong dự án là chưa xây dựng được một bộ test cases đủ lớn và đa dạng ngay từ đầu, đặc biệt là các tình huống edge cases từ thực tế tài xế. Nếu có thêm thời gian, tôi sẽ mở rộng test set theo các nhóm rõ ràng (happy path, ambiguous, out-of-scope, hallucination traps) và kết hợp với dữ liệu thực tế từ người dùng để cải thiện chất lượng đánh giá.