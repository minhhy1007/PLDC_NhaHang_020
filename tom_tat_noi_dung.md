# Tóm tắt dự án Restaurant Booking O2O

## Tổng quan

Restaurant Booking O2O (Res_Booking) là ứng dụng quản lý và đặt món nhà hàng, kết hợp hai hình thức phục vụ: khách dùng bữa tại nhà hàng bằng cách quét QR tại bàn và khách đặt giao hàng. Mục tiêu là hỗ trợ khách gọi món, thanh toán và trao đổi với nhân viên, đồng thời cung cấp công cụ quản lý hoạt động nhà hàng.

## Người dùng

- **USER (khách hàng):** xem thực đơn, gọi món tại bàn hoặc đặt giao hàng, thanh toán và chat với nhân viên.
- **STAFF (nhân viên):** hỗ trợ khách và xử lý hoạt động phục vụ, đơn hàng.
- **ADMIN (quản trị viên):** quản lý thực đơn, danh mục, khuyến mãi, bàn, nhân viên và đối soát.

## Chức năng chính

- Đăng ký, đăng nhập và xác thực OTP.
- Quét QR để xác định bàn và gọi món tại nhà hàng.
- Xem danh mục, sản phẩm và các phiên bản món; quản lý giỏ hàng và trạng thái đơn.
- Thanh toán qua VietQR, tải ảnh chuyển khoản và đối soát.
- Chat thời gian thực giữa khách hàng và nhân viên; gửi thông báo qua Telegram và email.
- Quản trị các món ăn, danh mục, khuyến mãi, bàn, nhân viên và hoạt động đối soát.
- Tính năng AI gồm gợi ý món, nhận diện ảnh món ăn và tư vấn bằng RAG.

## Kiến trúc và công nghệ

- **Ứng dụng di động:** React Native (Expo), Redux Toolkit, Axios, Socket.io-client.
- **Backend:** NestJS + Express, Prisma, MySQL, Socket.io, Cloudinary và JWT.
- **Thư mục tham khảo:** `backend/src`, `mobile/src`; các module backend gồm `auth`, `user`, `product`, `order`, `payment`, `vietQr`, `chat`, `ai` và `admin`.

## Chạy môi trường phát triển

Backend:

```bash
cd backend
npm install
npm run dev
```

Mobile:

```bash
cd mobile
npm install
npx expo start
```

Cần cấu hình biến môi trường, cơ sở dữ liệu và Cloudinary theo thiết lập trong `backend/src/config`.

## Những điểm cần xác minh

- VietQR được xử lý tự động hay cần nhân viên/quản trị viên xác nhận.
- Ảnh chuyển khoản được duyệt tự động hay duyệt thủ công.
- Phạm vi quyền CRUD cụ thể giữa STAFF và ADMIN.
- Tích hợp LLM (Ollama) là bản thử nghiệm hay đã sẵn sàng cho môi trường production.

## Hướng phát triển và bước tiếp theo

Các cơ hội được đề xuất gồm tự động đối soát thanh toán bằng OCR và ghép giao dịch, cải thiện gợi ý món, bổ sung dashboard quản trị thời gian thực, SSO cho nhân viên, audit log và phân quyền chi tiết.

Nên ưu tiên xác nhận quy tắc thanh toán và duyệt ảnh, kiểm tra schema Prisma, khảo sát luồng giao diện mobile, sau đó viết yêu cầu sản phẩm cho các tính năng QR dine-in, thanh toán và luồng đơn hàng.
