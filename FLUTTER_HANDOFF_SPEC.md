# ĐẶC TẢ KỸ THUẬT FLUTTER HANDOFF — CARESITTER

> **Môn học:** PRM323 — Lập trình ứng dụng di động  
> **Dự án:** CareSitter Customer App  
> **Tiêu chuẩn:** Flutter 3.x / Dart 3.x  
> **Font chữ:** Be Vietnam Pro (Google Fonts)  
> **Grid hệ thống:** 8-point Spacing Grid  
> **Thiết bị mục tiêu:** Mobile Viewport 390×844 dp (tương thích 360–412 dp)

---

## 1. HỆ THỐNG DESIGN TOKENS TRÊN FLUTTER

### 1.1. Bảng mã màu sắc (Color Tokens)

```dart
class AppColors {
  // Brand Colors
  static const Color primary = Color(0xFF0D6E57);       // Xanh ngọc đậm chủ đạo
  static const Color primaryLight = Color(0xFF138A6E);  // Trạng thái hover/active
  static const Color secondary = Color(0xFF00B4A0);     // Xanh teal thứ cấp
  static const Color secondaryLight = Color(0xFFE0F7F4);// Nền tag/chip phụ

  // Neutral & Surfaces
  static const Color background = Color(0xFFF6F9F8);    // Nền ứng dụng mát dịu
  static const Color surface = Color(0xFFFFFFFF);       // Nền Card, Sheet trắng
  static const Color surfaceMuted = Color(0xFFEDF3F1);  // Nền phân tách nhẹ
  static const Color border = Color(0xFFDCE5E0);        // Viền input/card

  // Typography
  static const Color textPrimary = Color(0xFF182724);   // Chữ tiêu đề & nội dung chính (11.4:1 contrast)
  static const Color textSecondary = Color(0xFF60716D); // Chữ mô tả phụ, gợi ý
  static const Color textDisabled = Color(0xFF9EABA6);  // Chữ vô hiệu hóa

  // Feedback & Status
  static const Color success = Color(0xFF10B981);       // Thành công / Hoàn thành
  static const Color warning = Color(0xFFF59E0B);       // Cảnh báo / Offline banner
  static const Color danger = Color(0xFFEF4444);        // Lỗi / Nguy hiểm / Vi phạm
  static const Color info = Color(0xFF3B82F6);          // Thông tin điều hướng
}
```

### 1.2. Kiểu chữ (Typography Tokens — Be Vietnam Pro)

| Token Name | Font Size | Line Height | Font Weight | Letter Spacing | Flutter TextStyle |
| :--- | :---: | :---: | :---: | :---: | :--- |
| `displayLarge` | 28 sp | 34 dp | Bold (700) | -0.5 px | `GoogleFonts.beVietnamPro(fontSize: 28, fontWeight: FontWeight.w700)` |
| `heading1` | 22 sp | 28 dp | SemiBold (600) | -0.3 px | `GoogleFonts.beVietnamPro(fontSize: 22, fontWeight: FontWeight.w600)` |
| `heading2` | 18 sp | 24 dp | SemiBold (600) | -0.2 px | `GoogleFonts.beVietnamPro(fontSize: 18, fontWeight: FontWeight.w600)` |
| `bodyLarge` | 16 sp | 24 dp | Regular (400) | 0.0 px | `GoogleFonts.beVietnamPro(fontSize: 16, fontWeight: FontWeight.w400)` |
| `bodyMedium` | 14 sp | 20 dp | Regular (400) | 0.0 px | `GoogleFonts.beVietnamPro(fontSize: 14, fontWeight: FontWeight.w400)` |
| `bodyBold` | 14 sp | 20 dp | SemiBold (600) | 0.0 px | `GoogleFonts.beVietnamPro(fontSize: 14, fontWeight: FontWeight.w600)` |
| `caption` | 12 sp | 16 dp | Medium (500) | +0.2 px | `GoogleFonts.beVietnamPro(fontSize: 12, fontWeight: FontWeight.w500)` |

### 1.3. Khoảng cách & Bán kính bo góc (Spacing & Radius)

```dart
class AppSpacing {
  static const double xxs = 4.0;
  static const double xs  = 8.0;
  static const double sm  = 12.0;
  static const double md  = 16.0;
  static const double lg  = 24.0;
  static const double xl  = 32.0;
}

class AppRadius {
  static const double sm = 8.0;
  static const double md = 12.0;
  static const double lg = 16.0;
  static const double xl = 24.0;
  static const double full = 999.0;
}
```

---

## 2. BẢNG ÁNH XẠ 9 NHÓM COMPONENT SANG FLUTTER WIDGETS

| Nhóm Component | Figma Component | Flutter Widget Đề xuất | Ghi chú kỹ thuật |
| :--- | :--- | :--- | :--- |
| **1. Buttons** | Primary, Secondary, Outline, Text | `ElevatedButton`, `OutlinedButton`, `TextButton` | Chiều cao cố định $\ge 48\text{dp}$ (chuẩn $54\text{px}$ cho Primary), bo góc 12px |
| **2. Text Fields** | Input text, Search, Date picker | `TextFormField` với `InputDecoration` | Viền `#DCE5E0`, label floating, hỗ trợ validation text rõ ràng |
| **3. Cards** | Service Card, Caregiver Card, Nutrition Card | `Container` hoặc `Card` với `BoxDecoration` | Nền trắng `#FFFFFF`, đổ bóng nhẹ `0 2px 8px rgba(12,43,33,0.06)`, bo góc 16px |
| **4. Navigation** | Top App Bar, Bottom Nav Bar | `AppBar`, `NavigationBar` (Material 3) | 4 mục: Trang chủ, Lịch hẹn, Dinh dưỡng, Tài khoản |
| **5. Selection Controls** | Checkbox, Radio, Switch, Chip | `Checkbox`, `RadioListTile`, `FilterChip` | Touch target tối thiểu $48\times 48\text{dp}$ |
| **6. Dialogs & Sheets** | Modal Sheet, Alert Dialog | `showModalBottomSheet`, `AlertDialog` | Dùng cho cam kết phi y tế `C-BOOK-05` và chọn giờ ca trực |
| **7. Loading States** | Shimmer, Circular Progress | `Shimmer.fromColors`, `CircularProgressIndicator` | Animation mượt mà, màu chuyển tiếp `#E2E8F0` sang `#F1F5F9` |
| **8. Empty States** | No Bookings, No Nutrition Data | `CustomEmptyStateWidget` | Hình minh họa SVG, tiêu đề rõ ràng và nút Call-to-Action |
| **9. Error & Offline** | Offline Banner, Dispute Alert | `MaterialBanner`, `SnackBar` | Màu vàng cảnh báo `#F59E0B` khi mất mạng, màu đỏ `#EF4444` khi lỗi |

---

## 3. ĐẶC TẢ GIAO DIỆN CHI TIẾT 8 MÀN HÌNH CHÍNH (6-POINT UI SPECS)

### 3.1. `C-HOME` (Trang chủ khách hàng)
1. **Cấu trúc:** Header lời chào (`Text`) + Avatar người dùng (`CircleAvatar`), Card ca trực sắp diễn ra (`UpcomingShiftCard`), Danh mục dịch vụ dạng lưới (`GridView.count`), Thanh điều hướng (`BottomNavigationBar`).
2. **Dữ liệu & Trạng thái:** Initial $\rightarrow$ Loading (Shimmer) $\rightarrow$ Has upcoming shift / Empty upcoming shift (`C-BOOK-EMPTY`).
3. **Bố cục:** Padding 16 dp hai bên, khoảng cách giữa các block 20 dp, vùng chạm nút bấm $\ge 48\text{dp}$.
4. **Màu sắc & Chữ:** Nền `#F6F9F8`, tiêu đề chính 20 sp `#182724`, card viền `#DCE5E0`.
5. **Tương tác:** Bấm dịch vụ chuyển sang `C-BOOK-01`, bấm card ca trực mở `C-SHIFT-LIVE`.
6. **Accessibility:** Text scaling an toàn đến 150% không vỡ layout; sematics label cho icon thông báo.

### 3.2. `C-BOOK-01` (Chọn gói dịch vụ)
1. **Cấu trúc:** Thanh tiến trình 6 bước (`BookingStepIndicator`), danh sách 3 gói đồng hành (`RadioListTile` lồng trong Card), Footer thanh toán tạm tính (`BookingWizardFooter`).
2. **Dữ liệu & Trạng thái:** Danh sách gói: Đồng hành 2 giờ, Ca nửa ngày 4 giờ, Ca cả ngày 8 giờ; tổng tiền tính theo gói được chọn.
3. **Bố cục:** Card dịch vụ cách nhau 12 dp; Footer cố định đáy màn hình với SafeArea.
4. **Màu sắc & Chữ:** Card được chọn có viền xanh `#0D6E57` dày 2px và nền nhẹ `#E0F7F4`.
5. **Tương tác:** Chạm chọn radio card thay đổi giá trị tạm tính tức thì, bấm "Tiếp tục" chuyển `C-BOOK-02`.
6. **Accessibility:** Touch target mỗi card $\ge 72\text{dp}$ giúp người lớn tuổi bấm dễ dàng.

### 3.3. `C-BOOK-02` (Chọn người được chăm sóc)
1. **Cấu trúc:** Header chọn hồ sơ, danh sách người thân đã lưu (`BeneficiaryCard`), nút thêm hồ sơ mới (`OutlinedButton.icon`), box ghi chú lưu ý y tế đặc biệt.
2. **Dữ liệu & Trạng thái:** Đọc danh sách hồ sơ từ local state/API; hiển thị avatar, quan hệ, tuổi, bệnh nền chính.
3. **Bố cục:** Spacing 12 dp giữa các card, padding 16 dp.
4. **Màu sắc & Chữ:** Thẻ bệnh nền dùng tag màu cam nhạt (`#FEF3C7`, chữ `#B45309`).
5. **Tương tác:** Chọn card người thân kích hoạt trạng thái checked, bấm tiếp tục sang `C-BOOK-03`.
6. **Accessibility:** Tương phản nhãn bệnh nền $\ge 4.5:1$.

### 3.4. `C-BOOK-03` (Thời gian & Địa điểm)
1. **Cấu trúc:** Bộ chọn lịch ngang (`HorizontalDatePicker`), lưới chọn khung giờ sáng/chiều (`TimeSlotGrid`), ô nhập địa chỉ nhà (`TextFormField`) kèm nút định vị GPS.
2. **Dữ liệu & Trạng thái:** Ngày hiện tại mặc định; kiểm tra logic: không cho chọn giờ trong quá khứ.
3. **Bố cục:** Grid chọn giờ 3 cột, khoảng cách 8 dp.
4. **Màu sắc & Chữ:** Giờ đã kín chỗ hiển thị màu xám mờ `#9EABA6`, không thể bấm.
5. **Tương tác:** Chọn ngày $\rightarrow$ lọc danh sách slot giờ khả dụng; bấm nút GPS điền tự động địa chỉ.
6. **Accessibility:** Thông báo trạng thái qua TalkBack/VoiceOver khi chuyển ngày.

### 3.5. `C-BOOK-04` (Chọn chăm sóc viên)
1. **Cấu trúc:** Bộ lọc nhanh (Khoảng cách, Đánh giá), danh sách Caregiver Card (ảnh chân dung, tên, số sao, số ca hoàn thành, kỹ năng nổi bật).
2. **Dữ liệu & Trạng thái:** Danh sách Caregiver sắp xếp theo khoảng cách gần nhất; trạng thái đang chọn.
3. **Bố cục:** Mỗi card có avatar kích thước $64\times 64\text{dp}$, thông tin xếp dọc với Auto Layout.
4. **Màu sắc & Chữ:** Sao đánh giá màu vàng `#F59E0B`, nhãn kỹ năng dùng Chip màu `#EDF3F1`.
5. **Tương tác:** Bấm vào avatar xem hồ sơ chi tiết, bấm nút "Chọn" để gán vào đơn đặt lịch.
6. **Accessibility:** Alt text mô tả đầy đủ cho ảnh đại diện chăm sóc viên.

### 3.6. `C-BOOK-05 & 06` (Cam kết phi y tế & Xác nhận)
1. **Cấu trúc:** Hộp thoại cam kết phi y tế nổi bật với biểu tượng khiên bảo vệ (`Icons.shield_outlined`), checkbox bắt buộc xác nhận: "Tôi hiểu rằng CareSitter chỉ cung cấp dịch vụ đồng hành sinh hoạt phi y tế", tóm tắt chi phí và voucher giảm giá.
2. **Dữ liệu & Trạng thái:** Nút "Tiến hành thanh toán" bị vô hiệu hóa (disabled) cho đến khi người dùng tích chọn cam kết.
3. **Bố cục:** Hộp cảnh báo bo góc 12 dp, viền xanh `#0D6E57`, padding bên trong 16 dp.
4. **Màu sắc & Chữ:** Văn bản cam kết in đậm, màu chữ tương phản $11.4:1$.
5. **Tương tác:** Tích checkbox $\rightarrow$ Nút chuyển từ xám `#9EABA6` sang xanh đậm `#0D6E57` $\rightarrow$ bấm mở cổng PayOS.
6. **Accessibility:** Rung nhẹ haptic feedback khi tích checkbox thành công.

### 3.7. `C-PAY-RESULT` (Kết quả thanh toán PayOS)
1. **Cấu trúc:** Icon trạng thái lớn (Check xanh thành công / Đồng hồ vàng chờ xử lý / Chấm than đỏ hủy), mã đơn hàng, số tiền đã trừ, nút "Xem ca trực" và "Về trang chủ".
2. **Dữ liệu & Trạng thái:** Polling API đối soát PayOS: Pending $\rightarrow$ Success hoặc Cancelled.
3. **Bố cục:** Căn giữa toàn màn hình (Center Column), khoảng cách giữa icon và chữ là 16 dp.
4. **Màu sắc & Chữ:** Icon thành công màu `#10B981`, tiêu đề 22 sp SemiBold.
5. **Tương tác:** Bấm "Theo dõi ca trực" chuyển ngay sang `C-SHIFT-LIVE`.
6. **Accessibility:** Đọc to kết quả thanh toán cho người khiếm thị ngay khi màn hình hiển thị.

### 3.8. `C-SHIFT-OFFLINE` (Chế độ lưu ngoại tuyến)
1. **Cấu trúc:** Banner cảnh báo ngoại tuyến màu vàng ở đầu trang, icon mất sóng (`Icons.wifi_off`), hộp hướng dẫn "Dữ liệu và ảnh chụp đang được lưu trên thiết bị", nút "Thử kết nối lại".
2. **Dữ liệu & Trạng thái:** Tự động kích hoạt khi `ConnectivityResult.none`; lưu cache vào SQLite/Hive cục bộ.
3. **Bố cục:** Banner cao 44 dp cố định dưới AppBar; nội dung hướng dẫn ở trung tâm màn hình.
4. **Màu sắc & Chữ:** Nền banner vàng hổ phách `#FEF3C7`, chữ cảnh báo màu `#92400E`.
5. **Tương tác:** Khi có mạng trở lại, tự động đẩy hàng đợi request lên server và hiển thị SnackBar xanh báo "Đã đồng bộ dữ liệu".
6. **Accessibility:** Cảnh báo âm thanh nhẹ và thông báo hệ thống khi rớt mạng để chăm sóc viên không bị giật mình.
