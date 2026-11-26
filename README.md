# Dice Analytics AI (Android Studio & Tự động biên dịch APK qua GitHub Actions)

Ứng dụng Android viết bằng **Kotlin, Jetpack Compose, MVVM, Foreground Service, MediaProjection API và Room Database** hỗ trợ phân tích xúc xắc giáo dục thời gian thực với lớp phủ nổi di chuyển, thay đổi kích thước và thu gọn.

## 1. Cách tạo tệp `.apk` tự động qua GitHub Actions (KHÔNG cần cài Android Studio)
Dự án đã tích hợp sẵn quy trình CI tại `.github/workflows/build-apk.yml`. Bạn chỉ cần làm 4 bước:

1. Giải nén `DiceAnalyticsAI-Android.zip`.
2. Tạo một kho lưu trữ (Repository) mới trên [GitHub](https://github.com/new) (chế độ Public hoặc Private đều được).
3. Tải toàn bộ các tệp và thư mục bên trong `DiceAnalyticsAI-Android` (nhớ bao gồm thư mục `.github/workflows/build-apk.yml`) lên nhánh `main` của kho lưu trữ (qua `git push` hoặc kéo thả trực tiếp trên web GitHub).
4. Mở tab **Actions** trên GitHub → chọn workflow **Build Android APK** → chờ khoảng 2–3 phút hoàn tất → kéo xuống mục **Artifacts** và nhấn tải **DiceAnalyticsAI-debug-apk** (giải nén ra tệp `app-debug.apk` và cài trực tiếp lên điện thoại Android).

> **Lưu ý khi tải bằng giao diện web GitHub**: Một số trình duyệt ẩn thư mục bắt đầu bằng dấu chấm (`.github`) khi kéo thả. Nếu bạn dùng trình duyệt web thay vì `git push`, hãy nhấn **Add file > Create new file**, đặt tên chính xác là `.github/workflows/build-apk.yml` rồi dán nội dung tệp workflow vào là GitHub Actions sẽ tự động chạy ngay.

## 2. Cách biên dịch thủ công bằng Android Studio (Tùy chọn)
- **Android Studio**: Ladybug (2024.2.1) trở lên, **JDK 17**, **Compile SDK 35**, **Min SDK 26**.
- Mở thư mục `DiceAnalyticsAI-Android` bằng `File > Open`, chờ Gradle Sync hoàn tất, rồi chọn **Build > Build Bundle(s) / APK(s) > Build APK(s)**.

## 3. Quy trình cấp quyền minh bạch khi sử dụng trên điện thoại
1. Mở tab **Quyền & Dịch vụ** trong ứng dụng.
2. Đọc và tích chọn xác nhận **chỉ sử dụng trong môi trường mô phỏng xúc xắc giáo dục được ủy quyền**.
3. Cấp quyền **Hiển thị trên ứng dụng khác (`SYSTEM_ALERT_WINDOW`)** và **Thông báo (`POST_NOTIFICATIONS`)**.
4. Nhấn **Bắt đầu** và chấp thuận hộp thoại hệ thống Android **MediaProjection**.
5. Chuyển sang tab **Mô phỏng** và nhấn **Tung xúc xắc** hoặc **Tự tung** để lớp phủ nổi tự động nhận diện và cập nhật biểu đồ thống kê mô tả.

## 4. Cam kết quyền riêng tư & Miễn trừ trách nhiệm
- Xử lý 100% cục bộ trên thiết bị, không khai báo quyền `INTERNET`.
- Tôn trọng tuyệt đối `FLAG_SECURE` của Android; không vượt cơ chế bảo mật.
- Chỉ phục vụ thống kê mô tả giáo dục, **không** cung cấp dự đoán cá cược hoặc tín hiệu đặt cược.
