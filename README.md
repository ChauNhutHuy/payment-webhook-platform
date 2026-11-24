# PayFlow — Payment Webhook Platform

Hệ thống xử lý webhook thanh toán tự động (SePay / VietQR) cho doanh nghiệp vừa và nhỏ, đối soát đơn hàng, phát sự kiện và gửi thông báo.

## 🚀 Công nghệ sử dụng
- **Nền tảng**: .NET 10 / ASP.NET Core Web API
- **Kiến trúc**: Clean Architecture, CQRS, Outbox Pattern
- **Cơ sở dữ liệu**: SQL Server (giao dịch, đơn hàng), MongoDB (raw webhook audit), Redis (distributed lock, dedup, cache, rate limit)
- **Message Broker**: Apache Kafka (KRaft), RabbitMQ
- **Kiểm thử**: xUnit, FluentAssertions, Testcontainers
- **Vận hành & Quan sát**: Docker, GitHub Actions, OpenTelemetry, Serilog

## 📂 Tài liệu & Lộ trình
- [LEARNING_PLAN.md](LEARNING_PLAN.md): Lộ trình học tập chi tiết 12 tuần.
- [PROGRESS.md](PROGRESS.md): Nhật ký tiến độ và checklist từng buổi học.
