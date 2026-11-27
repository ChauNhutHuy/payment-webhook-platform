# Tiến độ học tập PayFlow

## Tuần hiện tại: Tuần 1 — Docker căn bản (Chuẩn bị sang Tuần 2)

## Checklist Tuần 0
- [ ] Xác định bài toán thực tế & ngành mục tiêu (ghi chép vào `docs/discovery.md`). *(Đã chọn: Sân cầu lông; hiện `docs/discovery.md` đang là bản mẫu Digital Goods từ remote)*
- [ ] Tìm hiểu cơ chế Webhook của cổng thanh toán (SePay/VietQR sandbox).
- [x] Khởi tạo Git repo, cấu hình `.gitignore`, `README.md`. (Đã đẩy lên remote `main`)
- [x] Dựng khung solution Clean Architecture theo chuẩn .NET:
  - `PayFlow.Domain`
  - `PayFlow.Application`
  - `PayFlow.Infrastructure`
  - `PayFlow.Api`
  - `PayFlow.Worker`
  - Các project test tương ứng.
- [x] Verify build solution thành công.

## Checklist Tuần 1
- [x] Viết `Dockerfile` multi-stage cho `PayFlow.Api` (build/runtime, user non-root `app`, port `8080`).
- [x] Tạo `.dockerignore`.
- [x] Endpoint `GET /health` trả 200 (`Healthy`).
- [x] Thực nghiệm Volume với Redis (`payflow_redis_data`) — kiểm chứng mất dữ liệu khi không gắn volume và giữ nguyên dữ liệu khi gắn volume.
- [ ] Chạy SQL Server, MongoDB bằng container *(sẽ dựng chung trong `docker-compose.yml` ở Tuần 2)*.

## Chỗ chưa hiểu (hỏi lại buổi sau)
*(Chưa có)*

## Nhật ký buổi học
- **24/11/2026**: Buổi 0 — Khởi động lộ trình, làm rõ bài toán PayFlow và bắt đầu Tuần 0.
- **27/11/2026**: Buổi 1 — Dựng xong khung solution .NET 10, học sâu cơ chế Docker (Image vs Container, Registry, Layer Cache, Volume, Non-root & cổng 8080), viết `Dockerfile` multi-stage + `GET /health` + `.dockerignore`, và chạy test thực nghiệm Volume với Redis.
