# Khảo sát bài toán & Ngành mục tiêu (Discovery)

## 1. Bài toán thực tế
- **Đối tượng người dùng**: Các shop bán hàng online, kinh doanh khóa học số hoặc dịch vụ SaaS quy mô vừa và nhỏ tại Việt Nam.
- **Hiện trạng xử lý**:
  - Khách quét mã VietQR chuyển khoản ngân hàng.
  - Khách gửi ảnh chụp màn hình (bill) qua Zalo/Facebook.
  - Chủ shop/nhân viên đối soát thủ công bằng cách mở app ngân hàng, kiểm tra số dư và mã đơn trong nội dung chuyển khoản.
- **Nỗi đau (Pain points)**:
  - Nguy cơ bị lừa đảo bằng hình ảnh bill giả (Photoshop / web tạo bill giả).
  - Tắc nghẽn vào ban đêm hoặc các đợt flash sale: khách thanh toán nhưng không được kích hoạt ngay, dẫn đến phàn nàn và đòi hủy đơn.
  - Mất từ 1-2 tiếng mỗi ngày chỉ để ngồi soi sao kê và duyệt đơn thủ công.

## 2. Ngành mục tiêu lựa chọn cho PayFlow
- **Ngành**: Bán tài khoản / Khóa học trực tuyến (Digital Goods).
- **Lý do**:
  - 100% thanh toán trước qua chuyển khoản.
  - Khách hàng yêu cầu nhận tài khoản/kích hoạt khóa học **ngay lập tức** sau khi thanh toán thành công.
  - Dễ kiểm chứng luồng tự động: Nhận Webhook -> Khớp mã đơn -> Kích hoạt tài khoản -> Gửi tin nhắn xác nhận qua Zalo.
