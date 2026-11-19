**Bước 1: Thiết kế giải pháp (I/O)**

Xác định rõ Input của bài toán gồm những gì, và cấu trúc Output mong muốn.
```
Input: 
- Tự động hóa quy trình xử lý thông tin liên quan đến Feynman Prompt gia sư, Rubric chấm bài tự động.
Output: 
- Xác định rõ các thông tin cần đưa vào và cấu trúc kết quả mong muốn. 
- Xử  lý các trường hợp dữ liệu bị trống hoặc sai lệch để không dẫn đến việc sai kết quả.
```

**Bước 2: Viết prompt và chạy thử**

Viết prompt hoàn chỉnh theo định dạng chuyên nghiệp và copy kết quả phản hồi của AI.

**Prompt:**
```
# Context:
- Bạn la 1 chuyên gia trong lĩnh vực tự động hóa quy trình xử lý thông tin cho các cửa hàng liên quan đến Feynman Prompt gia sư, Rubric chấm bài tự động.
# Request: 
- Bạn phải xác định rõ thông tin được đưa vào, kiểm tra thông tin và dữ liệu đầu vào thật kỹ sau đó mới tiến hành xử lý thông tin.
# Explanation: 
- Nếu dữ liệu có các trường bị trống thì để trống kết quả đầu ra của dữ liệu đó, Nếu trong quá trình xử lý thông tin phát hiện ra dữ liệu bị sai lệch thì hãy hiển thị thông báo "Phát hiện có lỗi ở dữ liệu, hãy kiểm tra lại" để người đọc tiện kiểm tra và biết được chỗ sai xót.
- Tuyệt đối không được bịa ra dữ liệu không xác thực hoặc không có. 
- Đi vào thẳng vấn đề, không chào hỏi và không trả lời bất cứ câu hỏi ngoài lề dù trong bất kỳ hoàn cảnh nào.
# Action:  
- Hãy làm theo từng bước:
1. Nhận thông tin từ người đọc
2. Tiến hành phân tích và xử lý thông tin cho cửa hàng
3. Gửi kết quả lại cho người đọc dưới dạng bảng để người đọc có thể dễ hiểu
4. Nếu trường hợp có lỗi trong dữ liệu thì in ra thông báo để người đọc có thể tiện kiểm tra và sửa lại.
# Tone:
- Dùng văn phong lịch sự, chuyên nghiệp, gần gũi với người đọc và tôn trọng người đọc
# Extras:
- Sau khi hoàn tất quy trình xử lý thông tin, gửi lại cho người đọc kết quả dưới dạng Markdown.
```
**Dữ liệu test:**
```
Trường hợp 1 dữ liệu hợp lệ môn Giải tích 1 chủ đề đạo hàm tại một điểm và ý nghĩa hình học với mã sinh viên SV 2026 014 có nội dung giải thích của người học như sau: đạo hàm của hàm số tại x0 giống như tốc độ thay đổi tức thời của y khi x nhích một chút, trên đồ thị nó chính là hệ số góc của tiếp tuyến tại điểm x0 và f của x0, tức là độ dốc của đường thẳng chạm nhẹ vào đường cong đúng tại chỗ đó mà không cắt xuyên qua theo kiểu đường cát tuyến; bộ tiêu chí rubric gồm tiêu chí C1 nắm bản chất tốc độ thay đổi tức thời tối đa 4 điểm yêu cầu giải thích được giới hạn tỉ số biến thiên khi delta x tiến về 0 hoặc tốc độ thay đổi tức thời, tiêu chí C2 ý nghĩa hình học tiếp tuyến tối đa 3 điểm yêu cầu liên hệ đúng với hệ số góc của tiếp tuyến và phân biệt được với cát tuyến, tiêu chí C3 ngôn ngữ đời thường dễ hiểu theo tinh thần Feynman tối đa 3 điểm yêu cầu dùng ví dụ hoặc ẩn dụ trực quan và tránh nhồi nhét thuật ngữ sáo rỗng. Trường hợp 2 bẫy dữ liệu trống môn Học máy chủ đề overfitting và cách phòng tránh với mã sinh viên SV 2026 029 có phần giải thích của người học chỉ chứa khoảng trắng trống và danh sách tiêu chí rubric hoàn toàn trống không có tiêu chí nào. Trường hợp 3 bẫy dữ liệu sai lệch và mâu thuẫn môn Kinh tế vĩ mô chủ đề lạm phát do cầu kéo và chi phí đẩy với mã sinh viên SV 2026 042 có nội dung giải thích sai kiến thức như sau: lạm phát xảy ra khi ngân hàng trung ương giảm lãi suất xuống 0 phần trăm đồng thời tăng thuế VAT lên 50 phần trăm làm giá cả giảm mạnh và sức mua của đồng tiền tăng gấp đôi, cầu kéo là khi nhà máy thiếu điện nên phải đóng cửa; bộ tiêu chí rubric gồm tiêu chí C1 phân biệt cầu kéo và chi phí đẩy tối đa 5 điểm yêu cầu nêu đúng nguyên nhân tổng cầu tăng cho cầu kéo và chi phí sản xuất tăng cho chi phí đẩy, tiêu chí C2 độ chính xác kinh tế học tối đa 6 điểm yêu cầu không nhầm lẫn chiều hướng tác động của lãi suất, thuế và lạm phát. Khi kiểm thử prompt bạn cần chú ý trường hợp 1 đánh giá khả năng chấm đúng thang điểm và nhận diện tinh thần Feynman khi dữ liệu đầy đủ, trường hợp 2 kiểm tra nhánh xử lý khi phần giải thích trống và rubric trống để hệ thống không chấm điểm khống, trường hợp 3 kiểm tra khả năng phát hiện sai lệch kiến thức kinh tế và dữ liệu gây nhiễu như tổng điểm 11 thay vì chấm chiếu lệ, đồng thời ở bước 1 cần xác định rõ trường bắt buộc, trường ngữ cảnh, cấu trúc đầu ra và cờ cảnh báo lỗi, còn ở bước 2 cần cài đặt câu lệnh điều kiện rõ ràng để phân tách lỗi dữ liệu đầu vào và lỗi nhận thức của người học.
```

**Kết quả:**
```
BƯỚC 1: XÁC ĐỊNH VÀ KIỂM TRA DỮ LIỆU ĐẦU VÀO

Cấu trúc trường dữ liệu

Loại trường	Tên trường	Vai trò
Bắt buộc	Mã sinh viên	Định danh bài làm
Bắt buộc	Nội dung giải thích của người học	Đối tượng chấm
Bắt buộc	Danh sách tiêu chí Rubric (mã, tên, điểm tối đa, yêu cầu)	Căn cứ chấm
Ngữ cảnh	Môn học, chủ đề	Xác định phạm vi kiến thức
Đầu ra	Điểm từng tiêu chí, tổng điểm, nhận xét, cờ cảnh báo	Kết quả trả về
Cờ cảnh báo	HỢP LỆ / TRỐNG / LỆCH DỮ LIỆU	Phân loại trạng thái

Kiểm tra tổng quát đầu vào

Trường hợp	Mã SV	Giải thích	Rubric	Tổng điểm tối đa Rubric	Trạng thái
1	SV 2026 014	Có nội dung	3 tiêu chí (4+3+3)	10	HỢP LỆ
2	SV 2026 029	Chỉ khoảng trắng	Trống	Không có	TRỐNG
3	SV 2026 042	Có nội dung	2 tiêu chí (5+6)	11	LỆCH DỮ LIỆU
BƯỚC 2: XỬ LÝ THEO ĐIỀU KIỆN

Logic phân nhánh đã áp dụng:

NẾU giải thích rỗng/chỉ khoảng trắng HOẶC rubric rỗng → để trống điểm, không chấm.
NẾU tổng điểm tối đa Rubric ≠ 10 → cờ lỗi dữ liệu đầu vào, hiển thị cảnh báo.
NẾU nội dung người học sai kiến thức → ghi nhận lỗi nhận thức của người học (tách biệt với lỗi dữ liệu) và chấm theo yêu cầu Rubric.
Trường hợp 1: SV 2026 014 – Giải tích 1 (Đạo hàm tại một điểm và ý nghĩa hình học)
Tiêu chí	Điểm tối đa	Điểm chấm	Căn cứ
C1 – Bản chất tốc độ thay đổi tức thời	4	3	Có nêu “tốc độ thay đổi tức thời của y khi x nhích một chút”. Chưa nêu rõ giới hạn của tỉ số biến thiên khi Δx → 0
C2 – Ý nghĩa hình học tiếp tuyến	3	3	Liên hệ đúng với hệ số góc của tiếp tuyến tại (x0, f(x0)) và phân biệt được với cát tuyến
C3 – Ngôn ngữ đời thường (Feynman)	3	2	Có hình ảnh trực quan “đường thẳng chạm nhẹ vào đường cong”; tuy nhiên chưa có ví dụ đời thường cụ thể (như vận tốc xe)
Tổng	10	8	

Nhận xét: Bài giải thích đúng bản chất và phân biệt tốt tiếp tuyến với cát tuyến. Để đạt điểm tối đa, bạn nên bổ sung khái niệm giới hạn khi Δx tiến về 0 và thêm một ví dụ đời thường (ví dụ: đồng hồ tốc độ của xe tại một thời điểm).

Trường hợp 2: SV 2026 029 – Học máy (Overfitting và cách phòng tránh)
Tiêu chí	Điểm tối đa	Điểm chấm	Căn cứ
(Không có tiêu chí)			
Tổng			

⚠️ Phát hiện có lỗi ở dữ liệu, hãy kiểm tra lại:

Phần giải thích của người học chỉ chứa khoảng trắng (không có nội dung).
Danh sách tiêu chí Rubric hoàn toàn trống.

→ Hệ thống không chấm điểm và để trống kết quả để tránh chấm khống.

Trường hợp 3: SV 2026 042 – Kinh tế vĩ mô (Lạm phát do cầu kéo và chi phí đẩy)

⚠️ Phát hiện có lỗi ở dữ liệu, hãy kiểm tra lại:

Loại lỗi	Mô tả	Nhóm lỗi
Lỗi Rubric	Tổng điểm tối đa là 5 + 6 = 11, không phải thang 10	Lỗi dữ liệu đầu vào
Lỗi kiến thức	Cho rằng lạm phát xảy ra khi giá cả giảm mạnh và sức mua tăng gấp đôi (đó là biểu hiện của giảm phát, ngược với lạm phát)	Lỗi nhận thức của người học
Lỗi kiến thức	Định nghĩa cầu kéo là “nhà máy thiếu điện phải đóng cửa” (đây là cú sốc nguồn cung, gần với chi phí đẩy, không phải tổng cầu tăng)	Lỗi nhận thức của người học
Lỗi kiến thức	Cho rằng giảm lãi suất xuống 0% cùng tăng thuế VAT 50% dẫn tới giá giảm; thực tế tăng thuế gián thu thường đẩy giá lên, hướng tác động bị nhầm	Lỗi nhận thức của người học

Kết quả tạm tính (chỉ mang tính tham khảo do Rubric lệch thang):

Tiêu chí	Điểm tối đa	Điểm chấm	Căn cứ
C1 – Phân biệt cầu kéo và chi phí đẩy	5	0	Không nêu đúng nguyên nhân tổng cầu tăng cho cầu kéo, cũng không nêu chi phí sản xuất tăng cho chi phí đẩy
C2 – Độ chính xác kinh tế học	6	0	Nhầm lẫn chiều hướng tác động của lãi suất, thuế và lạm phát
Tổng	11	0	Cần quy đổi sau khi Rubric được sửa về thang 10
BƯỚC 3 & 4: TỔNG HỢP KẾT QUẢ VÀ CẢNH BÁO
markdown
| Trường hợp | Mã SV | Môn | Trạng thái | Tổng điểm | Cảnh báo |
|---|---|---|---|---|---|
| 1 | SV 2026 014 | Giải tích 1 | Hợp lệ | 8/10 | Không |
| 2 | SV 2026 029 | Học máy | Dữ liệu trống | (để trống) | Phát hiện có lỗi ở dữ liệu, hãy kiểm tra lại |
| 3 | SV 2026 042 | Kinh tế vĩ mô | Dữ liệu lệch | 0/11 (tạm tính) | Phát hiện có lỗi ở dữ liệu, hãy kiểm tra lại |

Đề nghị kiểm tra lại:

Trường hợp 2: bổ sung nội dung giải thích và danh sách tiêu chí Rubric.
Trường hợp 3: điều chỉnh tổng điểm Rubric về 10 (ví dụ C1 = 4, C2 = 6, hoặc C1 = 5, C2 = 5) và xác nhận lại nội dung bài làm của người học trước khi chấm chính thức.
```