# NHẬT KÝ MINH CHỨNG ĐỐI THOẠI AI VỀ THIẾT KẾ UI & REDESIGN (CARESITTER)

> **Dự án:** CareSitter Customer App  
> **Phiên làm việc (Session):** Antigravity AI Pair Programming  
> **Conversation ID:** `36c7e87d-5e59-40da-9e5d-7944c3e0a5e0`  
> **Mục tiêu:** Rà soát và Redesign UI theo Google Stitch & Figma LAB02_CareSystem  
> **Mã nguồn liên quan:** `frontend/customer-app/lib/features/settings/` và `features/nutrition/`

---

## 1. TỔNG HỢP CÁC PHIÊN ĐỐI THOẠI THIẾT KẾ UI

### Phiên 1: Redesign Màn hình "Hồ sơ của tôi / Cài đặt" (Settings & Profile)
* **Yêu cầu của người dùng:**
  > *“truy cập stitch vào Giao Diện Trang Web trên stitch sau đó dựa vào màn hình 'Hồ sơ của tôi - CareSitter Redesign' và sửa lại màn hình mình gửi”*
* **Phân tích vấn đề UI cũ:**
  1. Giao diện cũ chia tách rời rạc, màu sắc chưa đồng bộ với bảng màu CareSitter Green (`#0D6E57`).
  2. Vùng thông tin người thân thụ hưởng (`Beneficiaries`) chưa làm nổi bật được bệnh nền và lưu ý chăm sóc.
  3. Thiếu các trạng thái tương tác phản hồi (visual feedback) và nút bấm chưa đạt chuẩn touch target $\ge 48\text{dp}$.
* **Giải pháp thiết kế & Hiện thực:**
  - Tái cấu trúc thành 7 widgets module hóa:
    - [settings_screen.dart](file:///d:/EXE/CareSitter/frontend/customer-app/lib/features/settings/presentation/screens/settings_screen.dart): Khung trang cuộn mượt mà với RefreshIndicator.
    - [settings_profile_card.dart](file:///d:/EXE/CareSitter/frontend/customer-app/lib/features/settings/presentation/widgets/settings_profile_card.dart): Thẻ hồ sơ cá nhân với gradient xanh thương hiệu, avatar bo tròn và badge "Đã xác thực danh tính".
    - [settings_beneficiaries_section.dart](file:///d:/EXE/CareSitter/frontend/customer-app/lib/features/settings/presentation/widgets/settings_beneficiaries_section.dart): Danh sách người thân cần chăm sóc với tag bệnh nền nổi bật.
    - [settings_account_section.dart](file:///d:/EXE/CareSitter/frontend/customer-app/lib/features/settings/presentation/widgets/settings_account_section.dart): Quản lý thông tin tài khoản và địa chỉ đã lưu.
    - [settings_security_section.dart](file:///d:/EXE/CareSitter/frontend/customer-app/lib/features/settings/presentation/widgets/settings_security_section.dart): Cài đặt sinh trắc học và đổi mật khẩu.
    - [settings_support_section.dart](file:///d:/EXE/CareSitter/frontend/customer-app/lib/features/settings/presentation/widgets/settings_support_section.dart): Trung tâm trợ giúp, hotline và điều khoản dịch vụ phi y tế.
    - [settings_settings_item.dart](file:///d:/EXE/CareSitter/frontend/customer-app/lib/features/settings/presentation/widgets/settings_settings_item.dart): Item cài đặt chuẩn touch target $48\times 48\text{dp}$.
  - Kết quả kiểm tra Dart Analyze: **0 issues found**.

---

### Phiên 2: Xử lý giao diện Chế độ Ngoại Tuyến (Offline Mode UI)
* **Yêu cầu & Bài toán:**
  > *Xử lý rào cản Persona 03 (Caregiver Hạnh): Khi vào thang máy hoặc tầng hầm chung cư mất kết nối 4G, giao diện cần phản hồi thế nào để không gây hoang mang và không làm mất dữ liệu.*
* **Quyết định UI:**
  - Thiết kế `C-SHIFT-OFFLINE`: Banner vàng hổ phách (`#FEF3C7`, chữ `#92400E`) cố định dưới AppBar báo rõ "Đang lưu ngoại tuyến".
  - Chuyển toàn bộ dữ liệu ảnh chụp khay cơm và timestamp hoạt động vào bộ nhớ cache thiết bị.
  - Tự động hiển thị SnackBar xanh thông báo đồng bộ thành công ngay khi phát hiện có mạng trở lại.

---

### Phiên 3: Rà soát & Tinh chỉnh luồng Dinh dưỡng (Nutrition Flow UI)
* **Yêu cầu & Bài toán:**
  > *Đảm bảo ranh giới phi y tế: Màn hình gợi ý bữa ăn `C-NUT-07` chỉ dựa trên thông tin bệnh nền gia đình khai báo, không được tự ý chẩn đoán hoặc kê đơn.*
* **Quyết định UI:**
  - Thiết kế card món ăn hiển thị rõ các thành phần nguyên liệu cần tránh (ví dụ: ít đường, giảm muối).
  - Tích hợp trạng thái ngắt gợi ý tự động `C-NUT-STATE-01`: Khi phát hiện hồ sơ bệnh lý lạ chưa được xác minh, giao diện dừng gợi ý thực đơn và khuyến cáo tham vấn chuyên gia y tế.

---

## 2. BẢNG TỔNG HỢP LIÊN KẾT MINH CHỨNG AI CHAT

| STT | Phiên đối thoại minh chứng | Nền tảng / Định danh | Nội dung trọng tâm |
| :-: | :--- | :--- | :--- |
| 1 | [ChatGPT Rà soát & Phản biện Lab 2](https://chatgpt.com/s/cx_6ad371cf90308191ab53a511a2212c74) | ChatGPT Public Share | Rà soát rubric Lab 2, trích xuất yêu cầu, phản biện Persona và rubric 100đ |
| 2 | **Antigravity AI Pair Programming Session** | ID: `36c7e87d-5e59-40da-9e5d-7944c3e0a5e0` | Trực tiếp đối thoại Redesign UI Settings/Profile, Offline Mode và Handoff Flutter |
| 3 | [Figma LAB02_CareSystem Design](https://www.figma.com/design/Ph22SZvtVFwWzohuaia1UC/LAB02_CareSystem?node-id=0-1&t=y8TBlIsxnOdSbWSD-1) | Figma 6 Page | Kết quả triển khai 8 màn hình Mobile, 9 nhóm component và prototype 3 luồng |
| 4 | [Stitch UI Generation Project](https://stitch.withgoogle.com/projects/16914427060621528532) | Google Stitch | Khởi tạo giao diện gốc và 3 vòng lặp tinh chỉnh mục tiêu |
