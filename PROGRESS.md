# Tiến độ học tập PayFlow

## Tuần hiện tại: Tuần 0 — Kiểm tra thị trường & Dựng khung dự án

## Checklist Tuần 0
- [x] Xác định bài toán thực tế & ngành mục tiêu (ghi chép vào `docs/discovery.md`).
- [x] Tìm hiểu cơ chế Webhook của cổng thanh toán (SePay/VietQR sandbox).
- [x] Khởi tạo Git repo, cấu hình `.gitignore`, `README.md`. (Đã đẩy lên remote `main`)
- [x] Dựng khung solution Clean Architecture theo chuẩn .NET:
  - `PayFlow.Domain`
  - `PayFlow.Application`
  - `PayFlow.Infrastructure`
  - `PayFlow.Api`
  - `PayFlow.Worker`
  - Các project test tương ứng.
- [x] Verify build solution thành công (`dotnet build` & `dotnet test` xanh).

## Chỗ chưa hiểu (hỏi lại buổi sau)
*(Đã giải tỏa các thắc mắc về Webhook, Push/Event-driven, Redis SET NX và Unique Constraint)*

## Nhật ký buổi học
- **24/11/2026**: Buổi 0 — Khởi động lộ trình, làm rõ bài toán PayFlow và bắt đầu Tuần 0.
- **26/11/2026**: Hoàn thành thảo luận kiến trúc Webhook vs Polling vs WebSocket, cơ chế cổng trung gian SePay, hoàn tất dựng khung solution Clean Architecture và đẩy code lên GitHub.
