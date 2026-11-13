Phần 1: Phân tích nguyên nhân AI bị ảo giác (Hallucination)

Bản chất của LLM: Các mô hình ngôn ngữ lớn (như ChatGPT) hoạt động dựa trên xác suất thống kê từ dữ liệu huấn luyện khổng lồ trên Internet, chứ không có cơ sở dữ liệu nội bộ riêng tư của công ty MartX.

Nguyên nhân sai lệch: Khi nhân viên đặt câu hỏi không kèm tài liệu nguồn (Zero-Shot Prompting trực tiếp), mô hình không tìm thấy điều khoản thực tế. Do cơ chế sinh văn bản luôn cố gắng đưa ra câu trả lời thay vì bỏ trống, AI đã tự động "suy đoán" và bốc phét (hallucination) dựa trên các văn bản thương mại phổ biến ngoài xã hội, dẫn đến con số phạt 20% và đình chỉ 30 ngày sai lệch hoàn toàn với hợp đồng thực tế (chỉ phạt 5% và đổi hàng trong 24h).

Phần 2: Cấu trúc RAG Prompt hoàn chỉnh
Dưới đây là câu lệnh áp dụng kỹ thuật RAG Grounding (đưa tài liệu nguồn vào ngữ cảnh kết hợp khóa an toàn) để ép AI bám sát dữ liệu thực tế:


[VĂN BẢN HỢP ĐỒNG CHUẨN]
- Điều khoản chất lượng rau củ MartX: "Phạt 5% giá trị lô bị dập nát và yêu cầu đổi hàng trong 24h đối với trường hợp nhà cung cấp giao hàng bị dập nát trên 10%."

[CÂU HỎI NGHIỆP VỤ]

Theo quy định MartX, nhà cung cấp giao rau bị dập nát trên 10% thì bị phạt bao nhiêu?

[NEGATIVE CONSTRAINT - KHÓA AN TOÀN]

- Quy tắc bắt buộc: Chỉ được phép sử dụng thông tin có sẵn trong [VĂN BẢN HỢP ĐỒNG CHUẨN] ở trên để trả lời.

- Tuyệt đối không tự suy đoán, không bịa đặt thêm con số hoặc hình thức phạt ngoài văn bản.

- Nếu thông tin câu hỏi không có trong văn bản, phải trả lời chính xác: "Không có dữ liệu trong tài liệu".
