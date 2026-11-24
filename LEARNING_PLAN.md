# LEARNING_PLAN.md — Kế hoạch học .NET Backend qua dự án PayFlow

> Tài liệu này dành cho **trợ lý AI trong IDE** (vai trò: người hướng dẫn) và cho **người học**.
> Bắt đầu mỗi buổi học bằng câu: *"Đọc LEARNING_PLAN.md và PROGRESS.md, rồi bắt đầu buổi học hôm nay."*
> Bắt đầu: 24/11/2026 (Tuần 0). Sửa ngày nếu khác. Thời lượng: khoảng 10-12 giờ mỗi tuần.

---

## 1. Dành cho AI: vai trò và quy tắc dạy

### 1.1 Người học là ai
- Dev .NET mức Mid đang nhắm Mid/Senior tại Việt Nam.
- Đã biết: Clean Architecture, ASP.NET Core Web API, .NET Framework (MVC, Web API), Apache Kafka (consumer, DLT, retry), C#, SQL, MongoDB, JavaScript (jQuery), HTML/CSS, Bootstrap.
- Còn thiếu: Docker, CI/CD, unit/integration test, Redis, cloud, observability, microservices thực hành, DDD/CQRS, hiểu sâu Kafka (producer/consumer/idempotence).
- Giao tiếp bằng **tiếng Việt**. Thuật ngữ kỹ thuật giữ tiếng Anh.

### 1.2 Mục tiêu thật sự
Không phải "làm xong project". Mục tiêu là người học **giải thích được vì sao**, **biết nó hỏng thế nào**, và **trả lời được câu hỏi phỏng vấn lắt léo**. Project chỉ là phương tiện.

### 1.3 Cách giải thích (bắt buộc theo)
1. **Đi từ sự cố/vấn đề trước, khái niệm sau.** Ví dụ: "ghi DB xong nhưng publish Kafka lỗi, chuyện gì xảy ra?" rồi mới giới thiệu Outbox.
2. **Đi theo hành trình của một message/request**: nó bắt đầu ở đâu, đi qua trạm nào, ở mỗi trạm có thể hỏng thế nào. Có thể vẽ sơ đồ ASCII.
3. **Dùng ví dụ đời thường ngắn** (quán trà sữa, sổ ghi chép, bạn chạy bàn...) rồi quay lại code thật.
4. **Nói thẳng đánh đổi.** Không có công nghệ nào "tốt hơn" tuyệt đối; luôn nêu khi nào dùng, khi nào không.
5. **Mỗi khái niệm trả lời đủ 6 câu hỏi:**
   1. Nó giải quyết vấn đề gì? Không có nó thì đau chỗ nào?
   2. Nó hoạt động thế nào ở mức đủ để dự đoán hành vi?
   3. Khi nào nên dùng, khi nào không?
   4. Nó hỏng theo những cách nào? *(quan trọng nhất)*
   5. Có lựa chọn thay thế nào, đánh đổi ra sao?
   6. Trong PayFlow nó dùng ở đâu, đo được gì?

### 1.4 Cách hướng dẫn (không làm hộ)
- **Người học tự gõ code.** Không đưa toàn bộ lời giải ngay. Thứ tự: đặt câu hỏi gợi mở, gợi ý hướng, đưa khung (skeleton) có chỗ trống, và chỉ đưa code hoàn chỉnh khi người học đã thử ít nhất 2 lần hoặc yêu cầu rõ.
- Sau khi người học viết xong: **review** (đúng, sai, rủi ro), hỏi "vì sao bạn chọn cách này?".
- **Kiểm tra hiểu**: cuối mỗi chủ đề, yêu cầu người học tự giải thích lại bằng lời của mình trong 5-8 câu, rồi chỉ ra chỗ thiếu hoặc sai.
- Mỗi chủ đề kết thúc bằng: **1 bài "phá hệ thống"** (xem từng tuần) và **3 câu hỏi phỏng vấn** (lưu vào `INTERVIEW_QA.md`).
- Khi người học hỏi câu "lắt léo", dạy khung trả lời: làm rõ đề, nêu giả định, so 2 phương án, nói rủi ro và cách phát hiện, gắn với kinh nghiệm thật.

### 1.5 Trung thực
- Không chắc thì nói "mình chưa chắc" và chỉ vào tài liệu chính thức để kiểm tra. Không bịa số liệu, tên API, hay hành vi mặc định.
- Giá trị mặc định và API của thư viện thay đổi theo phiên bản. Trước khi dạy chi tiết về cấu hình (Kafka client, MediatR, Testcontainers...), **kiểm tra phiên bản đang dùng trong repo** và tài liệu hiện hành.
- **MediatR**: kiểm tra điều khoản giấy phép hiện hành trước khi dùng; nếu có vướng mắc thì tự viết dispatcher đơn giản hoặc dùng thư viện thay thế. Hãy để người học so sánh các lựa chọn.
- Với dịch vụ bên ngoài (SePay, Zalo): điều kiện đăng ký, giới hạn, giá có thể đổi. Người học phải đọc tài liệu chính thức; AI không đoán.

### 1.6 Cấu trúc một buổi học (90-120 phút)
1. Mở `PROGRESS.md`, tóm tắt buổi trước và việc dang dở (2 phút).
2. Hỏi nhanh 2-3 câu ôn bài tuần trước (5 phút).
3. Học khái niệm theo mục 1.3 (20-30 phút).
4. Người học code (45-60 phút), AI hướng dẫn và review.
5. Bài phá hệ thống (15 phút), người học ghi lại: chuyện gì xảy ra, vì sao, sửa thế nào.
6. Người học tự giải thích lại + ghi 3 câu hỏi phỏng vấn (10 phút).
7. Cập nhật `PROGRESS.md` (tick checklist, ghi "chỗ chưa hiểu").

### 1.7 File trong repo
- `LEARNING_PLAN.md`: file này.
- `PROGRESS.md`: checklist tiến độ + "chỗ chưa hiểu" + nhật ký ngắn mỗi buổi.
- `NOTES/`: ghi chú theo chủ đề (người học tự viết).
- `INTERVIEW_QA.md`: câu hỏi phỏng vấn + câu trả lời của người học, AI chấm và góp ý.
- `docs/decisions/`: ADR ngắn (1 trang) cho mỗi quyết định kỹ thuật lớn.

---

## 2. Dự án PayFlow

### 2.1 Là gì
Dịch vụ cho doanh nghiệp nhỏ: nhận thông báo tiền về tài khoản ngân hàng (qua webhook của cổng như SePay), khớp với đơn hàng, tự cập nhật trạng thái/kích hoạt dịch vụ và gửi thông báo cho khách qua Zalo. "PayFlow" là tên tạm.

**Phạm vi:** chỉ nhận thông báo giao dịch từ cổng thanh toán, **không giữ hay chuyển tiền**.

### 2.2 Vì sao chọn dự án này
Nó buộc người học đụng đủ các vấn đề thật: webhook gửi lặp hoặc bị lỡ (idempotency, đối soát), ghi DB + phát event (Outbox), gửi tin hàng loạt có giới hạn (queue, retry, DLT, rate limit), nhiều khách (đa tenant, phân quyền), vận hành (log, trace, health).

### 2.3 Công nghệ
- .NET bản LTS mới (.NET 8 hoặc .NET 10; chọn một và ghi vào README), ASP.NET Core Web API, Clean Architecture.
- SQL Server (giao dịch, đơn hàng), MongoDB (lưu payload webhook thô để audit), Redis (dedup, cache, rate limit), Kafka (sự kiện), RabbitMQ (một luồng nhỏ để so sánh).
- Docker + docker-compose, GitHub Actions, Azure (Container Apps hoặc App Service).
- xUnit, NSubstitute hoặc Moq, FluentAssertions, Testcontainers, Serilog, OpenTelemetry.

### 2.4 Cấu trúc solution gợi ý
```
src/
  PayFlow.Domain/          # Entity, Value Object, Domain Event (không phụ thuộc gì)
  PayFlow.Application/     # Use case (command/query), interface, validation
  PayFlow.Infrastructure/  # EF Core, Mongo, Redis, Kafka, SePay client, Zalo sender
  PayFlow.Api/             # Controller/Minimal API, middleware, auth
  PayFlow.Worker/          # BackgroundService: Outbox publisher, Kafka consumers, reconciler
tests/
  PayFlow.Domain.Tests/
  PayFlow.Application.Tests/
  PayFlow.IntegrationTests/   # Testcontainers
docker/  docs/  .github/workflows/
```

### 2.5 Luồng nghiệp vụ chính
```
Khách chuyển khoản ──► Ngân hàng ──► Cổng (SePay) ──POST webhook──► PayFlow API
                                                                       │
   1) xác thực (API key)  2) lưu payload thô (Mongo)  3) chống trùng (Redis + unique DB)
   4) khớp đơn (mã đơn trong nội dung CK, số tiền)    5) cập nhật đơn + ghi OutboxMessage (CÙNG transaction)
                                                                       │
                                  Worker (Outbox publisher) ──► Kafka topic payment.confirmed
                                                                       │
                       Consumer: kích hoạt dịch vụ  +  gửi thông báo Zalo (retry, DLT)
Định kỳ: Reconciler gọi API giao dịch của cổng, so với DB, bù giao dịch webhook bị lỡ.
```

### 2.6 Mô hình dữ liệu tối thiểu
- `Tenant(Id, Name, ApiKeyHash, ...)`: mỗi shop một tenant.
- `Order(Id, TenantId, Code, Amount, Status[Pending|Paid|Underpaid|Overpaid|Expired], CreatedAt, ...)`.
- `BankTransaction(Id, TenantId, GatewayTransactionId UNIQUE, ReferenceCode, Amount, Content, TransactionDate, MatchedOrderId?, Status)`.
- `OutboxMessage(Id, Type, Payload, CreatedAt, ProcessedAt?, Attempts, LastError?)`.
- `ProcessedMessage(ConsumerName, MessageId, ProcessedAt)`: PK/UNIQUE `(ConsumerName, MessageId)`.
- Mongo: `raw_webhooks` (payload thô + header + thời điểm nhận).

### 2.7 Sự kiện Kafka
- `payment.confirmed` (key = `orderId` để giữ thứ tự theo đơn).
- `notification.requested`, `notification.retry.1`, `notification.retry.2`, `notification.dlt` (retry/DLT do ứng dụng tự cài; Kafka không có DLT sẵn).

### 2.8 Giao diện thay thế được
- `INotificationSender`: `FakeNotificationSender` (mặc định trong lúc học/test) và `ZaloNotificationSender` (khi đã có OA/template được duyệt).
- `IPaymentGatewayClient`: `FakeGatewayClient` và `SePayClient`.
Nhờ vậy học và test không phụ thuộc dịch vụ ngoài.

### 2.9 Quy tắc an toàn (không thương lượng)
- Webhook phải xác thực (API key hoặc cơ chế cổng cung cấp) trước khi xử lý; không tin payload.
- Không log dữ liệu nhạy cảm (số tài khoản đầy đủ, số điện thoại) ở dạng thô.
- Dữ liệu mỗi tenant tách biệt; mọi truy vấn phải có `TenantId`.
- Secret không nằm trong code hay git.

---

## 3. Lộ trình

> Mỗi tuần có: **Hiểu được**, **Làm**, **Phá hệ thống**, **Tự kiểm tra**, **Xong khi**.
> AI dạy theo mục 1.3-1.6. Người học tự code.

### Tuần 0 (3-4 ngày): kiểm tra thị trường và dựng khung
**Hiểu được:** mình đang giải bài toán cho ai, họ đang làm thủ công thế nào.
**Làm:**
- [ ] Nói chuyện với 3-5 chủ shop/cơ sở dịch vụ: đối soát tiền và báo khách hiện làm sao, mất bao lâu mỗi ngày, có sẵn lòng trả tiền không. Ghi vào `docs/discovery.md`.
- [ ] Chọn **một** ngành mục tiêu.
- [ ] Đọc tài liệu chính thức của SePay (webhook, đối soát, môi trường thử) và đăng ký môi trường thử.
- [ ] Tạo repo, solution theo mục 2.4, README rỗng, `.gitignore`.
**Xong khi:** có file discovery, chọn xong ngành, solution build được.

### Tuần 1: Docker căn bản
**Hiểu được:** image vs container, layer và cache, volume, network, vì sao multi-stage, vì sao không chạy root.
**Làm:**
- [ ] Viết `Dockerfile` multi-stage cho `PayFlow.Api` (build/runtime, image nhỏ, user không phải root).
- [ ] `.dockerignore`.
- [ ] Chạy SQL Server, MongoDB, Redis bằng image có sẵn (volume để không mất dữ liệu).
- [ ] Endpoint `GET /health` trả 200.
**Phá hệ thống:** xóa container DB khi chưa gắn volume rồi gắn volume và so sánh; build lại sau khi sửa một dòng code và quan sát layer nào được cache.
**Tự kiểm tra:** container khác máy ảo ở đâu? Vì sao copy `*.csproj` và restore trước khi copy toàn bộ code? Dữ liệu trong container đi đâu khi container bị xóa?
**Xong khi:** `docker run` chạy API, health trả 200, giải thích được từng dòng Dockerfile.

### Tuần 2: docker-compose, cấu hình và Kafka bằng thực nghiệm
**Hiểu được:** compose network, `depends_on` và healthcheck, cấu hình theo môi trường; Kafka producer và consumer ở mức cơ chế (xem bên dưới).
**Làm:**
- [ ] `docker-compose.yml` dựng API + SQL Server + MongoDB + Redis + Kafka (KRaft hoặc kèm Zookeeper) + Kafka UI.
- [ ] Cấu hình qua biến môi trường, `appsettings.{Env}.json`, user-secrets cho local.
- [ ] Healthcheck cho từng service; API chờ DB sẵn sàng.
- [ ] **Kafka mini-lab**: viết producer và consumer console đơn giản gửi/nhận `payment.confirmed` giả.
**Kafka cần hiểu (AI dạy theo "hành trình một message"):**
- Producer: lấy metadata, chọn partition bằng hash của key (cùng key vào cùng partition, giữ thứ tự), gom batch, `acks` (0/1/all), retry.
- Broker: leader/follower, ISR, sao chép; "vì sao `acks=all` chậm hơn nhưng an toàn hơn".
- Consumer: consumer group, mỗi partition chỉ một consumer trong group, offset, commit.
**Phá hệ thống (Kafka):**
- Gửi 10 message cùng key và khác key, xem chúng nằm ở partition nào, thứ tự ra sao.
- Chạy 2 consumer cùng group rồi tắt một, quan sát rebalance.
- Tắt consumer giữa chừng khi đang xử lý, bật lại, xem có đọc lại message không.
**Tự kiểm tra:** vì sao cùng key vào cùng partition? Vì sao thêm consumer vượt số partition không tăng thông lượng? Điều gì xảy ra nếu commit offset trước khi xử lý?
**Xong khi:** `docker compose up` là chạy cả hệ thống; trả lời được 3 câu trên bằng lời của mình.

### Tuần 3: Git flow và CI/CD với GitHub Actions
**Hiểu được:** vì sao PR + CI, pipeline gồm những bước nào, vì sao bắt test pass mới merge.
**Làm:**
- [ ] Quy ước nhánh (`main`, `develop`, `feature/*`), quy ước commit.
- [ ] Workflow: restore, build, test, build Docker image, push lên GHCR (hoặc Docker Hub).
- [ ] Cache NuGet; chạy trên PR; bật branch protection (bắt buộc CI xanh).
- [ ] Badge CI trong README.
**Phá hệ thống:** cố tình commit một test fail rồi mở PR, xem CI chặn thế nào; làm hỏng Dockerfile và xem lỗi hiện ở bước nào.
**Tự kiểm tra:** CI khác CD ở đâu? Vì sao không nên để secret trong workflow dạng thô? Khi nào nên cache, khi nào cache gây lỗi khó hiểu?
**Xong khi:** mỗi PR tự build + test; người lạ clone repo chạy được bằng một lệnh.

### Tuần 4: Unit test
**Hiểu được:** test cái gì, mock cái gì, vì sao không test controller mỏng, vì sao không mock thứ mình sở hữu quá sâu (ví dụ `DbContext`).
**Làm:**
- [ ] Domain: `Order.ApplyPayment(...)` xử lý đủ/thiếu/thừa tiền, đơn đã hết hạn, thanh toán lặp.
- [ ] Application: use case "xử lý giao dịch" khớp đơn theo mã trong nội dung chuyển khoản.
- [ ] xUnit (`Fact`, `Theory`, `InlineData`), mock bằng NSubstitute/Moq, assert bằng FluentAssertions.
- [ ] Coverlet đo coverage, đưa vào CI. Mục tiêu tham khảo: trên 70% ở Domain/Application (đừng chạy theo con số).
**Phá hệ thống:** đảo một điều kiện trong `ApplyPayment` và xem test nào bắt được; xóa một test và xem lỗi lọt đi đâu (mutation thủ công).
**Tự kiểm tra:** test tốt khác test "chạy qua cho có" ở đâu? Khi nào mock làm test vô nghĩa? Arrange-Act-Assert là gì và vì sao tách rõ?
**Xong khi:** test chạy trong CI, bắt được lỗi khi cố tình phá logic.

### Tuần 5: Integration test với Testcontainers
**Hiểu được:** integration test khác unit test ở đâu, vì sao dùng DB thật trong container thay vì in-memory.
**Làm:**
- [ ] `WebApplicationFactory` gọi API thật trong bộ nhớ.
- [ ] Testcontainers: SQL Server, MongoDB, Redis, Kafka.
- [ ] Test: gửi webhook hợp lệ thì tạo `BankTransaction` và cập nhật đơn.
- [ ] Test: **gửi cùng một webhook 2 lần thì chỉ 1 giao dịch** (idempotency).
- [ ] Test luồng Kafka: produce, consume, consumer lỗi thì retry rồi vào DLT.
- [ ] Chạy tất cả trong CI.
**Phá hệ thống:** ngắt kết nối DB giữa request, xem API trả gì và dữ liệu có nhất quán không; gửi webhook sai API key, sai định dạng, thiếu trường.
**Tự kiểm tra:** vì sao EF Core in-memory provider dễ cho kết quả sai so với DB thật? Làm sao test không phụ thuộc thứ tự và dữ liệu cũ?
**Xong khi:** ít nhất 5 integration test xanh trong CI, trong đó có test idempotency và test retry/DLT.

### Tuần 6: EF Core sâu và tối ưu SQL
**Hiểu được:** change tracking, N+1, index và execution plan, transaction và isolation level.
**Làm:**
- [ ] Migrations; index cho `GatewayTransactionId`, `(TenantId, Code)`, `(TenantId, TransactionDate)`.
- [ ] Concurrency token (`RowVersion`) cho `Order` để hai webhook đồng thời không ghi đè nhau.
- [ ] Báo cáo doanh thu theo ngày/tháng: viết bằng EF Core rồi viết lại bằng Dapper, so sánh.
- [ ] Seed 100.000+ giao dịch, tìm ít nhất 2 truy vấn chậm, đo trước/sau (ms, số query, execution plan). Ghi vào README.
**Phá hệ thống:** cố tình tạo N+1 rồi bắt nó bằng log SQL; gửi 2 webhook cho cùng một đơn đồng thời (dùng script) và xem điều gì xảy ra khi có/không có concurrency token.
**Tự kiểm tra:** N+1 là gì và phát hiện thế nào? Tracking vs no-tracking? Vì sao index có thể làm ghi chậm đi? `OFFSET` lớn có vấn đề gì?
**Xong khi:** có bảng "trước/sau" với số liệu thật.

### Tuần 7: Redis và caching
**Hiểu được:** cache-aside, TTL, invalidation, stampede; Redis như công cụ chống trùng và giới hạn tốc độ.
**Làm:**
- [ ] Khóa chống xử lý trùng cho webhook: `SET key value NX EX ttl` theo `GatewayTransactionId`. Hiểu vì sao **vẫn cần unique constraint ở DB** (Redis chỉ là lớp nhanh phía trước).
- [ ] Cache trạng thái đơn cho endpoint tra cứu; invalidate khi đơn đổi trạng thái.
- [ ] Rate limiting cho API tra cứu (tự cài bằng Redis hoặc dùng middleware có sẵn, rồi so sánh).
- [ ] Đo latency và số truy vấn DB trước/sau.
**Phá hệ thống:** tắt Redis giữa chừng, hệ thống có còn đúng không (fail-open hay fail-closed, vì sao)? Cho TTL hết đồng loạt và quan sát stampede.
**Tự kiểm tra:** khi nào KHÔNG nên cache? Cache invalidation khó ở đâu? Điều gì xảy ra khi Redis chết, DB chịu nổi không? Vì sao dedup bằng Redis một mình là chưa đủ?
**Xong khi:** có số liệu trước/sau, và giải thích được hành vi khi Redis chết.
**Mốc thị trường:** tìm khách thử đầu tiên (miễn phí một tháng) và chạy với tài khoản ngân hàng thật nếu được.

### Tuần 8: CQRS và độ bền vững của service
**Hiểu được:** vì sao tách command/query, pipeline behavior, retry/timeout/circuit breaker.
**Làm:**
- [ ] CQRS cho các use case chính (kiểm tra giấy phép MediatR trước, xem mục 1.5; có thể tự viết dispatcher).
- [ ] Pipeline behavior: validation (FluentValidation), logging, transaction.
- [ ] Result pattern; xử lý lỗi toàn cục bằng `IExceptionHandler` và ProblemDetails.
- [ ] Polly hoặc `Microsoft.Extensions.Resilience`: retry có backoff + jitter, timeout, circuit breaker cho lời gọi `IPaymentGatewayClient` và sender thông báo.
**Phá hệ thống:** làm client giả trả lỗi ngẫu nhiên/chậm, quan sát retry và circuit breaker mở/đóng; thử retry không backoff và xem nó "đập" dịch vụ ra sao.
**Tự kiểm tra:** retry nguy hiểm khi nào (thao tác không idempotent)? Circuit breaker giải quyết gì mà retry không giải quyết được? CQRS có làm code phức tạp thừa khi nào?
**Xong khi:** use case chạy qua pipeline; có test cho retry và circuit breaker.

### Tuần 9: Outbox, idempotent consumer, retry/DLT, RabbitMQ (trọng tâm)
**Hiểu được:** vì sao "ghi DB và publish event" không thể atomic nếu làm trực tiếp; Outbox; at-least-once; idempotent consumer; Kafka idempotent producer và transaction.
**Làm:**
- [ ] Khi xử lý giao dịch: cập nhật `Order` + insert `OutboxMessage` **trong cùng một transaction DB**.
- [ ] `OutboxPublisher` (`BackgroundService`): đọc các bản ghi chưa gửi (SQL Server dùng `UPDLOCK, READPAST` để nhiều worker không giành nhau), publish Kafka, đánh dấu `ProcessedAt`, tăng `Attempts` khi lỗi.
- [ ] Bật idempotent producer rõ ràng trong cấu hình (kiểm tra giá trị mặc định của client đang dùng, đừng đoán).
- [ ] Consumer idempotent: bảng `ProcessedMessage` với UNIQUE `(ConsumerName, MessageId)`, ghi **cùng transaction** với tác dụng nghiệp vụ.
- [ ] Commit offset thủ công **sau** khi xử lý xong (at-least-once).
- [ ] Retry topics (`retry.1`, `retry.2`) và `dlt`, kèm header ghi số lần thử và lỗi cuối.
- [ ] Reconciler định kỳ gọi API giao dịch của cổng (lọc theo thời gian hoặc `since_id`), so với DB, bù giao dịch bị lỡ; tôn trọng giới hạn tốc độ của API.
- [ ] Một luồng nhỏ dùng RabbitMQ (exchange, queue, routing key, ack, dead-letter queue) để so sánh với Kafka.
- [ ] Ôn Saga ở mức khái niệm (choreography vs orchestration) và eventual consistency; viết ADR "vì sao Outbox".
**Phá hệ thống (bắt buộc làm hết, ghi lại kết quả):**
1. Tắt Kafka khi đang nhận webhook, bật lại: không mất event nào, không trùng.
2. Giết Worker giữa lúc publish: xem event có bị gửi lặp không và consumer xử lý ra sao.
3. Cho consumer ném exception thường xuyên: theo dõi message đi qua retry.1, retry.2 rồi vào dlt.
4. Gửi cùng message hai lần vào consumer: kết quả nghiệp vụ chỉ một lần.
5. Làm hỏng commit offset (commit trước khi xử lý) và chứng minh message bị mất.
**Tự kiểm tra:** vì sao idempotent producer **không đủ** để "không mất, không trùng" xuyên suốt? Outbox giải quyết chặng nào, idempotent consumer giải quyết chặng nào? Khi nào chọn Kafka, khi nào chọn RabbitMQ? Exactly-once thật sự có không, hay là at-least-once + idempotency?
**Xong khi:** thực hiện đủ 5 thí nghiệm, vẽ được sơ đồ luồng và giải thích bằng lời.

### Tuần 10: Bảo mật API
**Hiểu được:** authentication vs authorization, JWT, refresh token, vì sao webhook dùng cơ chế khác (API key/chữ ký).
**Làm:**
- [ ] Đăng nhập cho chủ shop bằng JWT + refresh token; phân quyền theo role/policy.
- [ ] Mỗi tenant một dữ liệu riêng: bộ lọc `TenantId` bắt buộc (global query filter) và test để chứng minh không rò dữ liệu giữa tenant.
- [ ] Rate limiting, API versioning, Swagger/OpenAPI.
- [ ] Secret qua biến môi trường / user-secrets / Key Vault, không nằm trong git.
- [ ] Đọc OAuth2/OpenID Connect (authorization code + PKCE) ở mức hiểu luồng.
**Phá hệ thống:** thử đăng nhập tenant A rồi gọi dữ liệu tenant B; thử token hết hạn, token bị sửa; thử bỏ qua API key của webhook.
**Tự kiểm tra:** JWT lưu ở đâu là an toàn, vì sao access token nên ngắn hạn? Global query filter có điểm yếu nào?
**Xong khi:** có test chứng minh cách ly tenant.

### Tuần 11: Deploy lên cloud (Azure)
**Hiểu được:** container chạy ở cloud khác máy local thế nào, cấu hình và secret, CD.
**Làm:**
- [ ] Deploy lên Azure Container Apps hoặc App Service; dùng gói miễn phí/credit; **ghi nhớ xóa tài nguyên khi xong** để tránh tốn tiền.
- [ ] Azure SQL (hoặc dịch vụ DB tương đương), Key Vault cho secret.
- [ ] CD trong GitHub Actions: merge vào `main` thì tự deploy, có bước kiểm tra health sau deploy.
- [ ] Làm quen khái niệm Infrastructure as Code (Bicep hoặc Terraform), viết được một file đơn giản.
**Phá hệ thống:** deploy một bản lỗi và thực hành rollback; đổi sai connection string và xem triệu chứng.
**Tự kiểm tra:** vì sao cần health check trước khi chuyển traffic? Rollback thế nào? Khác biệt giữa cấu hình local và cloud nằm ở đâu?
**Xong khi:** có URL public chạy, deploy tự động khi merge.

### Tuần 12: Observability
**Hiểu được:** log, metric, trace khác nhau thế nào; vì sao cần correlation xuyên service.
**Làm:**
- [ ] Serilog log có cấu trúc (JSON), correlation ID đi từ API qua Kafka (header) sang consumer.
- [ ] OpenTelemetry: trace và metrics; truyền trace context qua header Kafka để **một trace** đi từ API đến consumer; xem bằng Jaeger/Grafana (chạy trong compose) hoặc Application Insights.
- [ ] Health checks `/health/live` và `/health/ready` (kiểm tra DB, Redis, Kafka).
- [ ] Metrics đáng theo dõi: số webhook nhận, số trùng bị chặn, độ trễ xử lý, kích thước hàng đợi Outbox, số message vào DLT.
**Phá hệ thống:** làm DB chậm cố ý và tìm ra nguyên nhân chỉ bằng log/trace; kể lại cách bạn phát hiện.
**Tự kiểm tra:** log, metric, trace dùng khi nào? Vì sao không log dữ liệu nhạy cảm? Làm sao tìm một request chậm trên production?
**Xong khi:** theo dõi được một request qua API, Outbox, Kafka, consumer trên một trace.

---

## 4. Tiêu chí hoàn thành dự án
- [ ] `docker compose up` chạy toàn bộ hệ thống.
- [ ] CI xanh, test (unit + integration) chạy trong pipeline.
- [ ] Webhook lặp hoặc lỡ không làm sai dữ liệu (idempotency + đối soát).
- [ ] Luồng Kafka có Outbox, retry, DLT, consumer idempotent.
- [ ] Có bảng số liệu tối ưu SQL/Redis trước và sau.
- [ ] Dữ liệu tenant tách biệt, có test chứng minh.
- [ ] Đã deploy lên cloud, có URL chạy được và CD.
- [ ] Có log, trace, health check.
- [ ] Ít nhất một khách thật đã dùng thử và cho phản hồi (nếu thị trường cho phép).
- [ ] README có sơ đồ kiến trúc, cách chạy một lệnh, badge CI, bảng quyết định thiết kế, số liệu đo.

Nếu sau Tuần 7 chưa ai chịu dùng thử, đổi ngành mục tiêu hoặc dùng PayFlow như project minh chứng; phần học và CV vẫn đủ giá trị.

---

## 5. Sau Tuần 12: hướng lên Senior (mỗi mảng 3-4 tuần)
1. **System design**: ước lượng tải, chọn DB/cache/queue, phân tích đánh đổi, luyện vẽ và giải thích.
2. **DDD**: Aggregate, Entity, Value Object, Domain Event, Bounded Context; áp dụng vào Domain của PayFlow.
3. **Kubernetes cơ bản**: Pod, Deployment, Service, Ingress, ConfigMap/Secret, Helm.
4. **Hiệu năng .NET**: `async/await` sâu, `Channel<T>`, BenchmarkDotNet, `dotnet-trace`.
5. **Elasticsearch**: index, mapping, full-text, aggregation (ví dụ tìm kiếm giao dịch).
6. **Dùng và tích hợp AI**: dùng trợ lý AI trong công việc, gọi API LLM, RAG cơ bản (ví dụ gợi ý khớp đơn khi nội dung chuyển khoản sai).
7. **Frontend hiện đại**: TypeScript + React hoặc Angular ở mức đọc và sửa được.

Kỹ năng mềm luyện song song: viết ADR/RFC một trang, review code người khác, giải thích đánh đổi bằng lời, nhận một phần việc end-to-end.

---

## 6. Phụ lục

### 6.1 Khung trả lời câu hỏi phỏng vấn lắt léo
1. Làm rõ đề trước ("ưu tiên nhất quán hay thông lượng? quy mô khoảng bao nhiêu?").
2. Nêu giả định rồi trả lời theo giả định.
3. Đưa 2 phương án và đánh đổi, chọn một và nói vì sao.
4. Nói rủi ro và cách phát hiện nếu nó sai.
5. Gắn với kinh nghiệm thật (PayFlow). Nếu chưa làm ở quy mô đó, nói thẳng và nêu bạn đã thử gì ở quy mô nhỏ.
6. Khi không biết: "chỗ này mình chưa gặp, nhưng mình suy luận thế này", rồi suy luận lộ rõ từng bước.

### 6.2 Câu hỏi phỏng vấn nên luyện (người học tự trả lời trong `INTERVIEW_QA.md`)
- Clean Architecture khác kiến trúc nhiều tầng truyền thống thế nào? Bạn đặt ranh giới ở đâu?
- Làm sao tránh mất hoặc xử lý trùng message với Kafka? (Outbox, idempotency, offset commit)
- Idempotent producer chống được gì và không chống được gì?
- Vì sao cùng key vào cùng partition? Điều gì xảy ra khi rebalance?
- At-least-once vs at-most-once vs exactly-once; trong thực tế bạn chọn gì?
- Kafka và RabbitMQ khác nhau thế nào, khi nào chọn cái nào?
- Thiết kế retry và DLT với Kafka (Kafka không có DLT sẵn) như thế nào?
- EF Core vs Dapper; làm sao phát hiện và sửa N+1?
- Cache invalidation xử lý thế nào? Điều gì xảy ra khi Redis chết?
- Vì sao dedup bằng Redis một mình là chưa đủ?
- Debug một request chậm trên production bằng cách nào?
- Webhook bị gửi lặp hoặc bị lỡ: bạn thiết kế thế nào để dữ liệu vẫn đúng?
- Làm sao đảm bảo dữ liệu tenant A không bị tenant B thấy?

### 6.3 Mẫu ghi chú sau mỗi chủ đề (`NOTES/<chủ-đề>.md`)
```
# <Chủ đề>
- Vấn đề nó giải quyết:
- Cơ chế (vẽ hoặc mô tả hành trình một message/request):
- Khi nào dùng / không dùng:
- Nó hỏng thế nào (từ bài phá hệ thống): chuyện gì xảy ra, vì sao, sửa ra sao
- So sánh với lựa chọn khác:
- Dùng ở đâu trong PayFlow, số liệu đo:
- 3 câu hỏi phỏng vấn + câu trả lời của mình:
- Chỗ mình còn chưa hiểu:
```

### 6.4 Mẫu `PROGRESS.md`
```
# Tiến độ
## Tuần hiện tại: <số>
## Checklist: (copy các mục "Làm" của tuần, tick khi xong)
## Chỗ chưa hiểu (hỏi lại buổi sau):
## Nhật ký buổi học
- <ngày>: học gì, làm gì, phá gì, ghi gì
```

### 6.5 Câu lệnh mẫu để bắt đầu buổi học
- "Đọc LEARNING_PLAN.md và PROGRESS.md, bắt đầu buổi học hôm nay."
- "Giải thích <chủ đề> theo hành trình một message, rồi hỏi mình để kiểm tra."
- "Mình vừa viết xong <phần>, hãy review và chỉ ra rủi ro, đừng sửa hộ."
- "Phỏng vấn thử mình 5 câu lắt léo về <chủ đề>, rồi chấm câu trả lời."
- "Mình đã làm bài phá hệ thống số <n>, đây là kết quả: <dán>. Giải thích vì sao nó xảy ra."
