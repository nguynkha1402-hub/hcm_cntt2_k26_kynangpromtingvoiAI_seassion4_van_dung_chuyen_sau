. Bài toán & Điều kiện Logic (I/O)
Input: Nội dung phản hồi, Mã đơn hàng, Hạng khách hàng.

- Xử lý ngoại lệ: Mã đơn bị trống  $\rightarrow$  Không tự tạo mã giả, bắt buộc xin lại mã.

- Khách VIP + Cảm xúc tiêu cực  $\rightarrow$  Nâng mức ưu tiên lên `CRITICAL`.

Output: Trình bày suy luận (CoT) và xuất file JSON.

2. Prompt thực thi



```Plaintext
Bạn là AI CSKH. Xử lý dữ liệu sau qua 2 bước:
Input: Phản hồi: "Máy hỏng, gọi không ai nghe máy. Đổi ngay!". Mã đơn: "". Hạng khách: "VIP".

Bước 1 - Suy luận (Chain-of-Thought): 
- Nếu Mã đơn trống -> Xử lý theo hướng xin lại mã.
- Nếu Cảm xúc Tiêu cực + Khách VIP -> Gắn nhãn CRITICAL.

Bước 2 - Xuất kết quả JSON với các trường:
{ 
  "Trang_thai": "Đầy đủ" | "Thiếu mã", 
  "Cam_xuc": "Tiêu cực" | "Tích cực", 
  "Muc_uu_tien": "Normal" | "CRITICAL", 
  "Hanh_dong_tiep_theo": "Mô tả ngắn", 
  "Tin_nhan_mau": "Soạn tin nhắn phù hợp" 
}
```
3. Kết quả trả về

Suy luận: Nhận thấy mã đơn bị trống và khách VIP đang bức xúc. Cần nâng mức ưu tiên và khéo léo xin lại thông tin.

```JSON
{
  "Trang_thai": "Thiếu mã",
  "Cam_xuc": "Tiêu cực",
  "Muc_uu_tien": "CRITICAL",
  "Hanh_dong_tiep_theo": "Chuyển Quản lý xử lý khẩn. Xin lại SĐT/Mã đơn.",
  "Tin_nhan_mau": "TechStore vô cùng xin lỗi anh/chị vì sự cố trải nghiệm. Để quản lý trực tiếp hỗ trợ đổi trả ngay lập tức cho anh/chị, phiền anh/chị cung cấp lại SĐT hoặc Mã đơn hàng ạ."
}
```