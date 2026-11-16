# Thiết kế prompt để xử lý đoạn email
```markdow
Context:Bạn là chuyên viên xử lý dữ liệu nhân sự cấp cao.
Request:Bạn cần trích xuất các trường(Họ và tên,số điện thoại,email,vị trí ứng tuyển,năm kinh nghiệm,kỹ năng chính).
Explanation:Dữ liệu cần để import trực tiếp vào data base nên cần làm chính xác 100%.
Action:
- Bước 1:Lập ra một bảng gồm các cột họ và tên,số điện thoại,email,vị trí ứng tuyển,năm kinh nghiệm,kỹ năng chính.
- Bước 2:Lọc ra các thông tin và đưa vào các cột tương ứng.

Tone:Khách quan,chính xác,không thêm thắt văn phong cảm xúc.
Extras:Xuất ra một bảng Markdow:
VD:
|Họ và tên|số điện thoại|email|vị trí ứng tuyển|năm kinh nghiệm |kỹ năng chính|
|:---:|:---:|:---:|
|Nguyễn Văn A|0999999999|demo@gmail.com|cyber sercurity|2 năm kinh nghiệm|Quản trị hệ thống và mạng máy tính|
Và một định dạng json:
Trích xuất và chuẩn hóa các thông tin sau:

- Họ tên: Chuyển về dạng viết hoa chữ cái đầu (Ví dụ: Nguyễn Văn A).

- Số điện thoại: Chuẩn hóa về định dạng đầu số quốc gia hoặc loại bỏ dấu cách dư thừa.

- Kỹ năng chính: Gom nhóm thành một danh sách không trùng lặp (ví dụ: \['Python', 'SQL', 'FastAPI'\]).

- Trả về định dạng JSON thuần túy theo cấu trúc:

  { "name": "...", "phone": "...", "email": "...", "position": "...", "experience_years": 2, "skills": \[...\] }
```
Ràng buộc:Không được tự ý thêm thắt hoặc ảo giác các thông tin không có trong email của ứng viên.

Nếu thông tin nào bị thiếu (ví dụ không ghi số điện thoại), phải để giá trị là null trong JSON, không được tự điền bừa.

Chỉ trả về dữ liệu kết quả, nghiêm cấm AI viết thêm các đoạn văn giải thích ở đầu hoặc cuối câu trả lời.

Kiểm tra tính đúng đắn của cấu trúc JSON bằng các công cụ Validate JSON.
