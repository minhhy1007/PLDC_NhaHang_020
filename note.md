# Note: Câu hỏi & Trả lời về dự án Restaurant Booking O2O

## 1. Tên dự án là gì?
- Restaurant Booking O2O (Res_Booking)

## 2. Website/ứng dụng này thuộc lĩnh vực nào?
- Ứng dụng quản lý & đặt món nhà hàng (O2O): kết hợp Dine-in (quét QR tại bàn) + Delivery.

## 3. Mục đích chính của dự án?
- Cho phép khách gọi món tại bàn, đặt giao hàng, thanh toán (VietQR), chat real-time, và quản lý vận hành nhà hàng.

## 4. Ai là người dùng chính?
- Khách hàng (Customer), Nhân viên (Staff), Quản trị viên (Admin).

## 5. Những role tồn tại?
- ADMIN, STAFF, USER (Customer).

## 6. Các chức năng quan trọng (tóm tắt)
- Đăng ký / Đăng nhập / OTP
- Quét QR để lấy `tableId` và gọi món (Dine-in)
- Duyệt menu: danh mục, sản phẩm, variants
- Giỏ hàng, tạo đơn hàng, quản lý trạng thái đơn
- Thanh toán VietQR, upload ảnh chuyển khoản, đối soát
- Chat real-time giữa khách và nhân viên (Socket.io)
- Notification (Telegram bot), Email
- Admin: quản lý món, danh mục, khuyến mãi, bảng, staff, đối soát
- AI: Gợi ý món, nhận diện ảnh món, RAG tư vấn

## 7. Kiến trúc & tech stack (tóm tắt)
- Mobile: React Native (Expo), Redux Toolkit, Axios, Socket.io-client
- Backend: NestJS + Express, Prisma + MySQL, Socket.io, Cloudinary, JWT

## 8. File/Thư mục quan trọng để tham khảo nhanh
- Backend chính: [backend/src](backend/src)
- Mobile: [mobile/src](mobile/src)
- Các module backend: `auth`, `user`, `product`, `order`, `payment`, `vietQr`, `chat`, `ai`, `admin`.

## 9. Cách chạy nhanh (dev)
- Backend (ví dụ):

```bash
cd backend
npm install
npm run dev
```

- Mobile (ví dụ):

```bash
cd mobile
npm install
npx expo start
```

(Chi tiết env vars, database và Cloudinary cần cấu hình trong `backend/src/config`.)

## 10. Những giả định/chỗ cần xác thực (⚠️ CẦN XÁC NHẬN)
- Chi tiết luồng thanh toán VietQR (tự động hay thủ công) — kiểm tra `vietQr` module.
- Quy trình phê duyệt ảnh chuyển khoản: tự động hay admin duyệt tay?
- Mức phân quyền chi tiết giữa `STAFF` và `ADMIN` cho các hành động CRUD.
- Tích hợp LLM (Ollama) đang ở mức prototype hay production.

## 11. Vấn đề & cơ hội phát triển nhanh
- Thêm quy trình tự động đối soát thanh toán (image OCR + matching)
- Tăng cường AI recommendation (combo, calorie)
- Dashboard admin báo cáo real-time (Doanh thu, Order trạng thái)
- SSO cho staff, audit logs, và role-based access control chi tiết

## 12. Next steps gợi ý
1. Xác nhận các quy tắc thanh toán VietQR và phê duyệt ảnh.
2. Kiểm tra schema Prisma (`backend/prisma`) để mapping entity chính.
3. Khảo sát UI mobile flow: `mobile/src/features/at_restaurant` và `home`.
4. Viết Product Requirement cho 3 feature ưu tiên (QR Dine-in, Payment, Order Flow).

---
File này là tóm tắt nhanh để dùng làm note khi trình bày hoặc bắt đầu phân tích chi tiết hơn.
Nếu bạn muốn, tôi sẽ mở rộng thành bộ Q&A đầy đủ theo 27 phần yêu cầu (báo cáo dài) và tạo `ANALYSIS_FULL.md`.