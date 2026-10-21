# BÁO CÁO THIẾT KẾ PERSONA & BRAINSTORMING — CARESITTER
> **Tiêu chuẩn áp dụng:** [PRM393 Persona Guideline v1.0](https://prm393-material.web.app/persona-guideline)  
> **Dự án:** CareSitter — Nền tảng đồng hành và chăm sóc người cao tuổi phi y tế tại nhà  
> **Đánh giá tự chấm:** 100/100 điểm (10 tiêu chí đạt chuẩn)  
> **Chat Evidence:** [ChatGPT Rà soát & Phản biện Lab 2](https://chatgpt.com/s/cx_6ad371cf90308191ab53a511a2212c74)  
> **Figma:** [Figma LAB02_CareSystem](https://www.figma.com/design/Ph22SZvtVFwWzohuaia1UC/LAB02_CareSystem?node-id=0-1&t=y8TBlIsxnOdSbWSD-1)

---

## 1. NGUYÊN TẮC CỐT LÕI & ĐỊNH HƯỚNG

- **Persona không phải bản lý lịch cá nhân:** Tập trung vào hành vi, mục tiêu, hoàn cảnh sử dụng và rào cản thay vì chỉ liệt kê tuổi tác hay tính cách chung chung.
- **Phân loại nguồn dữ liệu khoa học:**
  - `Observed`: Quan sát trực tiếp tại hiện trường (nhật ký, hành vi thực địa).
  - `Reported`: Người tham gia thuật lại trải nghiệm qua phỏng vấn sâu.
  - `Inferred`: Nhóm thiết kế suy luận từ các mô hình và quy trình thực tế.
  - `Assumed`: Giả định ban đầu cần kiểm chứng bằng dữ liệu.
- **Quy mô 4 Persona cho hệ thống nhiều nhóm:** 1 Primary Persona (Gia đình chi trả), 2 Secondary Personas (Người cao tuổi thụ hưởng, Chăm sóc viên hiện trường), 1 Supporting Persona (Điều phối viên CSKH).

---

## 2. MILESTONE A — DISCOVERY

### 2.1. Problem Statement & Scope

#### Phát biểu vấn đề (Problem Statement)
> *“Những người con trong độ tuổi lao động tại các đô thị lớn cần một giải pháp tin cậy, minh bạch để người thân cao tuổi được bầu bạn và hỗ trợ sinh hoạt hàng ngày an toàn tại nhà; trong khi các dịch vụ giúp việc truyền thống thiếu kỹ năng giao tiếp và ứng xử với người già, còn các dịch vụ y tế tại nhà thì quá tốn kém và không đáp ứng nhu cầu đồng hành đời sống phi y tế.”*

#### Phạm vi sản phẩm (Product Scope)
- **Trong phạm vi (In-Scope)**:
  - Đồng hành sinh hoạt phi y tế: Trò chuyện, dạo bộ, đọc sách báo, nhắc nhở uống thuốc theo toa có sẵn, hỗ trợ ăn uống.
  - Hồ sơ sức khỏe người cao tuổi (`C-BEN`) và gợi ý thực đơn dinh dưỡng theo bệnh nền sinh hoạt (`C-NUT`).
  - Đặt lịch theo ca 6 bước minh bạch (`C-BOOK-01..06`).
  - Thanh toán PayOS với cơ chế đối soát tự động (`C-PAY`).
  - Giám sát ca trực thời gian thực qua GPS và nhật ký ảnh minh chứng (`C-SHIFT-LIVE`, `C-SHIFT-TIMELINE`).
  - Phục hồi ngoại tuyến khi mất sóng 4G (`C-SHIFT-OFFLINE`) và gửi khiếu nại (`C-SHIFT-DISPUTE`).
- **Ngoài phạm vi (Out-of-Scope)**:
  - Tuyệt đối không can thiệp thủ thuật y khoa xâm lấn (không tiêm truyền, không đặt ống sonde, không chẩn đoán bệnh).
  - Không thay thế cấp cứu khẩn cấp 115.
  - Không làm công việc dọn dẹp nhà cửa nặng (tổng vệ sinh công nghiệp).

---

### 2.2. Stakeholder & User Map

```
┌────────────────────────────────────────────────────────────────────────┐
│                   HỆ SINH THÁI NGƯỜI DÙNG CARESITTER                   │
├────────────────────────────────┬───────────────────────────────────────┤
│ 1. NGƯỜI ĐẶT LỊCH (PRIMARY)   │ 2. NGƯỜI THỤ HƯỞNG (SECONDARY)        │
│ • Con cái (28–45t), đi làm     │ • Cha mẹ già (65–85t) ở nhà một mình  │
│ • Người chi trả, đặt dịch vụ   │ • Cần bầu bạn, dạo bộ, ăn uống        │
│ • Nhu cầu: An tâm, minh bạch   │ • Rào cản: Mắt mờ, run tay, tự trọng  │
├────────────────────────────────┼───────────────────────────────────────┤
│ 3. CHĂM SÓC VIÊN (SECONDARY)   │ 4. VẬN HÀNH & CSKH (SUPPORTING)       │
│ • Điều dưỡng viên / SV Y tế    │ • Chuyên viên xử lý sự cố / Khiếu nại │
│ • Thao tác hiện trường di động │ • Cần log GPS, ảnh bằng chứng ca trực │
│ • Rào cản: Mất sóng 4G, bận tay│ • Mục tiêu: Công bằng, hòa giải nhanh │
└────────────────────────────────┴───────────────────────────────────────┘
```

---

### 2.3. Brainstorming & Affinity Clustering Board

Sau workshop 100 phút, các giả định và nhu cầu được phân thành 4 cụm trọng tâm:

1. **Cụm 1: Nỗi lo an toàn & Ranh giới pháp lý**  
   - Người nhà sợ người giúp việc làm ẩu, tiêm thuốc sai gây biến chứng.  
   - *Giải pháp:* Tách riêng màn hình cam kết dịch vụ phi y tế bắt buộc `C-BOOK-05`.
2. **Cụm 2: Nhu cầu giám sát & Minh bạch**  
   - Đi làm không thể gọi điện liên tục vì làm phiền giấc ngủ của cụ.  
   - *Giải pháp:* Timeline hình ảnh thời gian thực `C-SHIFT-TIMELINE` và định vị GPS.
3. **Cụm 3: Rào cản sức khỏe người cao tuổi**  
   - Mắt kém, tay run, bệnh nền tiểu đường kiêng khem phức tạp.  
   - *Giải pháp:* Cỡ chữ $\ge 14\text{sp}$, touch target $\ge 48\text{dp}$, ngắt gợi ý thực đơn khi bệnh lý bất thường `C-NUT-STATE-01`.
4. **Cụm 4: Rào cản hạ tầng kết nối di động**  
   - Chung cư cũ, thang máy, tầng hầm mất 4G khiến app bị lỗi lưu dữ liệu.  
   - *Giải pháp:* Màn hình và cơ chế lưu đệm ngoại tuyến `C-SHIFT-OFFLINE`.

---

### 2.4. Persona Coverage Matrix

| Nhóm | Persona đại diện | Vai trò | Ngữ cảnh sử dụng | Rào cản cốt lõi | Màn hình liên kết | Bằng chứng |
| :--- | :--- | :---: | :--- | :--- | :--- | :---: |
| **Gia đình** | **P01 · Hoàng Lan** (36t) | **Primary** | Văn phòng bận rộn | Thiếu thời gian, lo sợ pháp lý y tế | `C-BOOK-01..06`, `C-PAY` | Reported (`[EV-01]`) |
| **Người già** | **P02 · Bác Tuấn** (68t) | **Secondary** | Ở nhà một mình | Mắt kém, tay run, bệnh tiểu đường | `C-BEN-DETAIL`, `C-NUT-07` | Reported/Inferred (`[EV-02]`) |
| **Hiện trường** | **P03 · Nguyễn Hạnh** (24t) | **Secondary** | Nhà khách hàng, di chuyển | Mất sóng 4G, bận tay chăm sóc | `C-SHIFT-TIMELINE`, `C-SHIFT-OFFLINE` | Observed/Reported (`[EV-03]`) |
| **Vận hành** | **P04 · Quang Minh** (31t) | **Supporting** | Bàn làm việc CSKH | Khiếu nại thiếu bằng chứng thực tế | `C-PAY-REVIEW`, `C-SHIFT-DISPUTE` | Inferred (`[EV-04]`) |

---

### 2.5. Danh mục giả định & Kế hoạch kiểm chứng (Assumption Backlog)

- `Assumed-01`: Khách hàng sẵn sàng đọc kỹ điều khoản phi y tế thay vì lướt nhanh $\rightarrow$ Kiểm chứng bằng tỷ lệ dừng chân ở `C-BOOK-05` $\ge 5\text{s}$.
- `Assumed-02`: Thanh toán mã QR PayOS tiện lợi hơn tiền mặt đối với người bận rộn $\rightarrow$ Kiểm chứng qua tỷ lệ thanh toán PayOS thành công $\ge 85\%$.
- `Assumed-03`: Người cao tuổi thích xem hình ảnh khay cơm và món ăn dinh dưỡng trên điện thoại $\rightarrow$ Kiểm chứng qua thử nghiệm khả năng đọc hiểu của bác Tuấn $\ge 90\%$.
- `Assumed-04`: Caregiver sẵn sàng chụp ảnh khay cơm và hoạt động sau mỗi công việc mà không thấy phiền toái $\rightarrow$ Kiểm chứng qua thời gian ghi log $< 15\text{s}$.
- `Assumed-05`: Log GPS và ảnh timeline đủ tính pháp lý để giải quyết 100% tranh chấp ca trực $\rightarrow$ Kiểm chứng qua tỷ lệ hòa giải thành công $\ge 85\%$.

---

## 3. MILESTONE B — VALIDATION & HỒ SƠ 4 PERSONA

### 3.1. Bằng chứng nghiên cứu ẩn danh (Research Evidence)

- **`[EV-01]` (Chị L.H., 36t, kiểm toán viên tại TP.HCM):**  
  *“Tôi chỉ cần app có 3 thứ: Chăm sóc viên sạch sẽ có xác thực nhân thân, cam kết không tự ý tiêm thuốc hay làm thủ thuật y tế bậy bạ, và trưa gửi cho tôi 1 tấm ảnh cơm canh là tôi yên tâm họp đến chiều.”*
- **`[EV-02]` (Bác T.V.T., 69t, cựu công chức, bệnh tiểu đường Type 2):**  
  *“Tôi không cần ai phục vụ như người hầu. Cần đứa nào biết chuyện, nói năng lễ phép, nấu đồ mềm ít đường cho tôi ăn và dắt tôi đi bộ quanh công viên là quý lắm rồi.”*
- **`[EV-03]` (Bạn N.T.H., 23t, điều dưỡng viên bán thời gian):**  
  *“Nhiều nhà chung cư cũ vào tầng hầm hay thang máy là mất sạch sóng 4G. Nếu app bắt gửi ảnh ngay mới tính giờ thì em bị trễ giờ oan, rất cần app lưu tạm trên máy rồi tự gửi lại khi có mạng.”*
- **`[EV-04]` (Anh Q.M., 30t, quản lý dịch vụ gia đình):**  
  *“Xử lý khiếu nại sợ nhất là hai bên cãi suông. Phải có log GPS lúc đến/về và ảnh hiện trường từng mốc giờ thì mới phân định hoàn tiền công bằng được.”*

---

### 3.2. Bộ hồ sơ 4 Persona hoàn chỉnh (12 trường cốt lõi + Bắt buộc Lab 2)

#### 🧑‍💼 PERSONA 01 (PRIMARY) — HOÀNG THỊ LAN
1. **Identity & Archetype:** Hoàng Thị Lan (36 tuổi) · *Người con bận rộn đặt lịch chăm sóc từ xa (Remote Family Caregiver)* · Trưởng phòng Tài chính.
2. **Persona Priority:** **Primary Persona (Ưu tiên số 1)** · Người quyết định chi trả và điều hướng các luồng chính.
3. **Usage Context:** Mở app lúc 7h30 sáng hoặc 14h00 giữa các cuộc họp tại văn phòng; dùng iPhone 14/15; độ chú ý phân tán cao do công việc.
4. **Goals:** (1) Đặt được người đồng hành uy tín trong $< 5\text{ phút}$; (2) Nắm tiến độ thực tế của mẹ mà không cần gọi điện gián đoạn; (3) Minh bạch chi phí và an toàn pháp lý.
5. **Job to Be Done:** *“Khi tôi bận rộn họp hành ở công ty mà mẹ ở nhà một mình cần người trò chuyện, nhắc uống thuốc và nấu ăn, tôi muốn đặt một chăm sóc viên uy tín và theo dõi trực tiếp nhật ký ca trực trên điện thoại, để tôi có thể yên tâm tập trung công việc mà mẹ vẫn được chăm sóc chu đáo.”*
6. **Current Behaviors:** Đăng bài tìm người trên hội nhóm Facebook hoặc nhờ người quen; dùng camera giám sát gây phiền mẹ; tần suất đặt 3 buổi/tuần.
7. **Pain Points:** (1) Lo sợ người lạ ngược đãi hoặc trộm cắp; (2) Camera không biết mẹ đã ăn cơm chưa; (3) Mập mờ ranh giới y tế gây biến chứng.
8. **Motivations:** Sự an tâm tuyệt đối (Peace of mind) và tính minh bạch tài chính/pháp lý.
9. **Constraints:** Cực kỳ ít thời gian; cần bản cam kết dịch vụ phi y tế trước khi trả tiền.
10. **Key Scenarios:** Đặt lịch khẩn cấp 4 tiếng cho mẹ vào chiều mai, chọn Caregiver 5 sao, xác nhận điều khoản phi y tế và thanh toán PayOS trong 3 phút.
11. **Success Criteria:** Hoàn thành flow `C-BOOK-01..06` $< 3.5\text{ phút}$; Tỷ lệ hiểu lầm điều khoản phi y tế = $0\%$; Điểm an tâm $\ge 4.5/5$.
12. **Evidence & Status:** *Qualitative Finding (Reported)* · Mã nguồn `[EV-01]`, `[CS-INT-01]`.
* **Trường bắt buộc Lab 2**:
  - *Tuổi*: 36 tuổi · *Vai trò*: Khách hàng chính (Payer).
  - *Thói quen thiết bị*: Dùng iPhone 14 Pro Max 1 tay khi di chuyển, ưa chuộng thông báo đẩy ngắn gọn.
  - *Nhu cầu Accessibility*: Vùng chạm tập trung ở nửa dưới màn hình (thumb zone), độ tương phản cao $\ge 4.5:1$ để xem rõ dưới ánh sáng văn phòng.
  - *Problem Statement riêng*: *“Chị Lan cần phương thức đặt dịch vụ chăm sóc người già tin cậy, xác thực danh tính và có cam kết phi y tế minh bạch trong vòng dưới 5 phút, để vừa chu toàn việc gia đình vừa không bị gián đoạn công việc tại công ty.”*
  - *Tiêu chí thành công đo được*: Thời gian hoàn tất đặt lịch và quét PayOS $< 3\text{ phút } 30\text{ giây}$; tỷ lệ chấp thuận cam kết phi y tế = $100\%$.
  - *Bản chất bằng chứng*: **Reported** (`[EV-01]`).

---

#### 👴 PERSONA 02 (SECONDARY) — BÁC TRẦN VĂN TUẤN
1. **Identity & Archetype:** Bác Trần Văn Tuấn (68 tuổi) · *Người cao tuổi có bệnh nền, tự trọng cao (Dignified Senior)* · Giáo viên nghỉ hưu, góa vợ.
2. **Persona Priority:** **Secondary Persona** · Người trực tiếp thụ hưởng dịch vụ.
3. **Usage Context:** Ở nhà một mình cả ngày; dùng Samsung Galaxy A-series cỡ 6.5 inch, chữ phóng to; mắt viễn thị, tay run nhẹ.
4. **Goals:** (1) Có bạn cờ, bạn dạo bộ lễ phép; (2) Bữa ăn ngon miệng, đúng khẩu vị nhưng kiểm soát đường huyết; (3) Giữ gìn sự độc lập và tự tôn.
5. **Job to Be Done:** *“Khi tôi ở nhà một mình và thấy trống trải, buồn chán, tôi muốn có một người bạn đồng hành lịch sự, biết lắng nghe và nấu cho tôi bữa ăn thanh đạm phù hợp sức khỏe, để tôi cảm thấy vui vẻ, khỏe khoắn mà không làm phiền công việc của con cái.”*
6. **Current Behaviors:** Tự nấu mì hoặc ăn cơm nguội qua bữa; ngồi xem tivi cả ngày; thỉnh thoảng quên uống thuốc.
7. **Pain Points:** (1) Cảm giác bị theo dõi bởi camera; (2) Ăn uống sai chế độ làm đường huyết tăng vọt; (3) Chăm sóc viên cắm mặt bấm điện thoại.
8. **Motivations:** Sự lễ phép, tôn trọng và bữa ăn nóng sốt, vừa miệng.
9. **Constraints:** Giảm thị lực và phản xạ xúc giác; bệnh nền tiểu đường Type 2 $\rightarrow$ Không được gợi ý món nhiều đường bột.
10. **Key Scenarios:** Chăm sóc viên đến, mở màn `C-NUT-07` chọn canh cá nấu ngót ăn trưa; hệ thống ngắt gợi ý tự động (`C-NUT-STATE-01`) khi có chẩn đoán bệnh mới.
11. **Success Criteria:** Tỷ lệ đọc rõ màn hình không cần kính lúp $\ge 90\%$; Mức độ hài lòng nụ cười ở màn `C-SHIFT-REVIEW` đạt 5 sao.
12. **Evidence & Status:** *Qualitative Finding (Reported)* · Mã nguồn `[EV-02]`, `[CS-INT-02]`.
* **Trường bắt buộc Lab 2**:
  - *Tuổi*: 68 tuổi · *Vai trò*: Người thụ hưởng trực tiếp (Senior Beneficiary).
  - *Thói quen thiết bị*: Dùng Samsung màn hình lớn, chữ phóng to 125%, thao tác bằng ngón trỏ chậm rãi.
  - *Nhu cầu Accessibility*: WCAG 2.1 AA — Cỡ chữ nội dung $\ge 16\text{sp}$, tương phản $\ge 7:1$ (CareSitter đạt $11.4:1$), vùng chạm tối thiểu $48\times 48\text{dp}$ (nút thực tế $54\text{px}$) chống bấm trượt do run tay.
  - *Problem Statement riêng*: *“Bác Tuấn cần người đồng hành thấu hiểu, lễ phép và hỗ trợ bữa ăn đúng chỉ số đường huyết mà không bị tước đi quyền tự chủ hay cảm giác bị giám sát xâm phạm đời tư.”*
  - *Tiêu chí thành công đo được*: Bác Tuấn đọc đúng tên món và nguyên liệu tại `C-NUT-07` đạt $\ge 90\%$ không cần kính lão; tỷ lệ bấm nhầm nút $< 2\%$.
  - *Bản chất bằng chứng*: **Reported & Inferred** (`[EV-02]`).

---

#### 👩‍⚕️ PERSONA 03 (SECONDARY) — NGUYỄN THỊ HẠNH
1. **Identity & Archetype:** Nguyễn Thị Hạnh (24 tuổi) · *Chăm sóc viên chuyên nghiệp, trẻ tuổi (Junior Companion)* · Tốt nghiệp Trung cấp Điều dưỡng.
2. **Persona Priority:** **Secondary Persona** · Người thực thi công việc tại hiện trường.
3. **Usage Context:** Di chuyển bằng xe máy giữa các ca trực; dùng điện thoại Android tầm trung, 4G chập chờn; tay thường bận chăm sóc người già.
4. **Goals:** (1) Nhận ca trực gần nhà; (2) Cập nhật nhật ký ca trực nhanh bằng 1 tay; (3) Nhận thù lao minh bạch và không bị trừ tiền oan.
5. **Job to Be Done:** *“Khi tôi đang trong ca chăm sóc người già và hoàn thành các hoạt động như cho uống thuốc hay nấu ăn, tôi muốn ghi nhận nhanh nhật ký và hình ảnh bằng 1–2 chạm trên điện thoại, để con cái khách hàng nhìn thấy tiến độ tức thì mà tôi không bị phân tâm khỏi việc chăm sóc cụ.”*
6. **Current Behaviors:** Nhận việc qua trung tâm môi giới (mất phí 25%); nhắn tin Zalo riêng cho người nhà dễ bị hiểu nhầm.
7. **Pain Points:** (1) Khách đòi hỏi làm việc nặng ngoài hợp đồng; (2) Mất sóng 4G trong thang máy bị tính trễ giờ; (3) Bị đổ lỗi oan khi người già tự ngã.
8. **Motivations:** Thu nhập minh bạch và sự bảo vệ từ nền tảng bằng điều khoản rõ ràng.
9. **Constraints:** Mạng chập chờn $\rightarrow$ Cần chế độ lưu ngoại tuyến (`C-SHIFT-OFFLINE`); không thể gõ chữ dài.
10. **Key Scenarios:** Check-in định vị tại nhà khách; bấm chọn tag "Đã ăn trưa" và chụp ảnh khay cơm trong 10 giây; màn hình chuyển vàng báo lưu offline khi vào tầng hầm.
11. **Success Criteria:** Thời gian cập nhật 1 hành động $< 15\text{ giây}$; Tỷ lệ mất dữ liệu do rớt mạng = $0\%$; Tỷ lệ đồng thuận phạm vi việc làm $\ge 98\%$.
12. **Evidence & Status:** *Observed & Reported* · Mã nguồn `[EV-03]`, `[CS-INT-03]`.
* **Trường bắt buộc Lab 2**:
  - *Tuổi*: 24 tuổi · *Vai trò*: Người cung cấp dịch vụ tại chỗ (Caregiver Provider).
  - *Thói quen thiết bị*: Gắn điện thoại trên giá đỡ xe máy, dùng 1 tay bấm nhanh, thích chụp ảnh hiện trường hơn nhập văn bản.
  - *Nhu cầu Accessibility*: Tương phản tốt ngoài trời nắng, nút hành động dạng Tag/Chip lớn, Banner cảnh báo Offline màu vàng rõ ràng.
  - *Problem Statement riêng*: *“Hạnh cần công cụ ghi nhận nhật ký ca trực siêu tốc bằng hình ảnh và tag lựa chọn sẵn có khả năng hoạt động ngoại tuyến, để bảo vệ công sức lao động mà không làm ảnh hưởng đến thời gian chăm sóc cụ.”*
  - *Tiêu chí thành công đo được*: Thời gian ghi log + chụp ảnh $< 15\text{ giây}$; tỷ lệ đồng bộ dữ liệu sau khi có sóng đạt $100\%$.
  - *Bản chất bằng chứng*: **Observed & Reported** (`[EV-03]`).

---

#### 👨‍💼 PERSONA 04 (SUPPORTING) — LÊ QUANG MINH
1. **Identity & Archetype:** Lê Quang Minh (31 tuổi) · *Chuyên viên điều phối & hòa giải tranh chấp (Operations & Dispute Specialist)* · Trưởng nhóm CSKH.
2. **Persona Priority:** **Supporting Persona** · Định hình các màn hình xử lý biên và đối soát.
3. **Usage Context:** Bàn làm việc CSKH với 2 màn hình lớn, tai nghe trực tổng đài từ 7h00 đến 21h00.
4. **Goals:** (1) Phân loại khiếu nại $< 15\text{ phút}$; (2) Đối soát mở khóa thanh toán treo PayOS; (3) 100% ca sự cố được xử lý công bằng.
5. **Job to Be Done:** *“Khi khách hàng và chăm sóc viên có bất đồng về chất lượng hoặc thời gian ca trực, tôi muốn truy xuất được toàn bộ bằng chứng lịch sử ca trực và hình ảnh báo cáo, để tôi đưa ra quyết định xử lý khiếu nại công bằng, giữ được uy tín của nền tảng.”*
6. **Current Behaviors:** Đọc tin nhắn Zalo hai bên rất mất thời gian; xuất file Excel đối soát ngân hàng thủ công.
7. **Pain Points:** (1) Khách khiếu nại không có bằng chứng; (2) Giao dịch treo làm khách giận dữ; (3) Thông tin rải rác.
8. **Motivations:** Tính khách quan dựa trên log hệ thống và tỷ lệ giải quyết khiếu nại lần đầu (First Contact Resolution).
9. **Constraints:** Tuân thủ bảo mật thông tin cá nhân (PII); chính sách hoàn hủy tiền của công ty.
10. **Key Scenarios:** Nhận ticket khiếu nại từ `C-SHIFT-DISPUTE`, đối chiếu log GPS check-out lúc 11h45 thay vì 12h00, duyệt hoàn tiền 15% giờ thừa tự động.
11. **Success Criteria:** Tỷ lệ khiếu nại có đủ bằng chứng xử lý ngay $\ge 95\%$; Thời gian xử lý khiếu nại $< 30\text{ phút}$; CSAT sau hòa giải $\ge 85\%$.
12. **Evidence & Status:** *Inferred* · Mã nguồn `[EV-04]`, `[CS-OPS-01]`.
* **Trường bắt buộc Lab 2**:
  - *Tuổi*: 31 tuổi · *Vai trò*: Vận hành & CSKH (Internal Operations).
  - *Thói quen thiết bị*: Máy tính 2 màn hình, sử dụng phím tắt và bộ lọc trạng thái đơn hàng liên tục.
  - *Nhu cầu Accessibility*: Bảng đối soát có sọc tương phản rõ, trạng thái có cả Badge màu và Text label cho người mù màu.
  - *Problem Statement riêng*: *“Minh cần bảng điều phối hiển thị trọn vẹn lịch sử GPS, ảnh timeline và trạng thái thanh toán PayOS trên một giao diện thống nhất, để giải quyết khiếu nại khách quan trong dưới 30 phút.”*
  - *Tiêu chí thành công đo được*: Thời gian truy xuất đủ bằng chứng ca trực $< 2\text{ phút}$; tỷ lệ giải quyết khiếu nại lần đầu $\ge 85\%$.
  - *Bản chất bằng chứng*: **Inferred** (`[EV-04]`).

---

## 4. MA TRẬN TỪ PERSONA ĐẾN QUYẾT ĐỊNH THIẾT KẾ (UI DECISIONS MATRIX)

| Persona | Nhu cầu người dùng (User Need) | Ý tưởng thiết kế để thử nghiệm | Màn hình liên kết | Cách kiểm chứng (Test Method) |
| :--- | :--- | :--- | :--- | :--- |
| **P01** (Lan) | Sợ tranh chấp pháp lý và rủi ro người làm tự ý làm thủ thuật y tế. | Tách riêng màn hình cam kết dịch vụ phi y tế bắt buộc tích chọn trước khi thanh toán. | `C-BOOK-05` (Cam kết phi y tế) | Task test: 100% người dùng hiểu rõ dịch vụ không bao gồm tiêm truyền y tế. |
| **P01** (Lan) | Muốn nắm tiến độ ca trực mà không phải gọi điện làm phiền mẹ. | Thiết kế thanh tiến trình thời gian thực kèm card ảnh chụp từng hoạt động. | `C-SHIFT-LIVE`, `C-SHIFT-TIMELINE` | Đo Likert độ an tâm $\ge 4.5/5$. Thời gian xem tiến độ $< 10\text{s}$. |
| **P02** (Tuấn) | Mắt viễn thị, tay run, có bệnh nền tiểu đường nguy hiểm. | Cỡ chữ $\ge 14\text{sp} - 16\text{sp}$, touch target $\ge 48\text{dp}$. Tự động ngắt gợi ý thực đơn khi bệnh án bất thường. | `C-NUT-07`, `C-NUT-STATE-01` | Người cao tuổi đọc đúng tên món không cần trợ giúp $\ge 90\%$. Tỷ lệ bấm nhầm $< 2\%$. |
| **P03** (Hạnh) | Mất mạng 4G khi vào nhà kín hoặc tầng hầm chung cư. | Màn hình cảnh báo lưu đệm ngoại tuyến (Offline cache) và tự đồng bộ khi có sóng. | `C-SHIFT-OFFLINE` | Thử nghiệm ngắt mạng: Tỷ lệ mất dữ liệu báo cáo = $0\%$. Thời gian phục hồi $< 3\text{s}$. |
| **P04** (Minh) | Cần bằng chứng xác thực để giải quyết tranh chấp hoàn hủy tiền công bằng. | Tích hợp form đính kèm lý do khiếu nại đối soát trực tiếp với log GPS và ảnh timeline. | `C-SHIFT-DISPUTE`, `C-PAY-REVIEW` | Đo thời gian xử lý khiếu nại trung bình $< 30\text{ phút}$. CSAT hòa giải $\ge 85\%$. |

---

## 5. BẢNG TỰ ĐÁNH GIÁ THEO RUBRIC PERSONA (100/100 ĐIỂM)

| Tiêu chí đánh giá theo Guideline | Điểm tối đa | Minh chứng CareSitter | Tự đánh giá |
| :--- | :---: | :--- | :---: |
| 1. Xác định phạm vi sản phẩm, tác vụ trọng tâm & nhóm người dùng | 10 | Đầy đủ Problem Statement, In-Scope / Out-of-Scope phi y tế rõ ràng | **10/10** |
| 2. Có User/Stakeholder Map & cân nhắc người dễ bị bỏ sót | 10 | Sơ đồ 4 nhóm: Người đặt lịch, người già, caregiver và CSKH | **10/10** |
| 3. Số Persona phù hợp phạm vi, có phân hóa rõ rệt | 10 | 4 Persona: 1 Primary, 2 Secondary, 1 Supporting dựa trên hành vi | **10/10** |
| 4. Persona phân biệt bằng goals, behaviors, contexts, constraints | 10 | Ranh giới mục tiêu và rào cản khác biệt hoàn toàn giữa 4 nhóm | **10/10** |
| 5. Mỗi Persona đủ 12 trường cốt lõi + 4 trường bắt buộc của Lab 2 | 10 | 12 trường chuẩn mực kèm tuổi, vai trò, thói quen thiết bị, accessibility | **10/10** |
| 6. Nhu cầu mô tả theo kết quả mong muốn, không ngụy trang tính năng | 10 | Mục tiêu tập trung vào "Sự an tâm", "Bữa ăn an toàn", "Bảo vệ thù lao" | **10/10** |
| 7. Có bằng chứng nghiên cứu & phân loại Observed/Reported/Inferred/Assumed | 10 | 4 mã phỏng vấn `[EV-01..04]` và nhãn phân loại bằng chứng minh bạch | **10/10** |
| 8. Có Affinity Board chứng minh cách hình thành phân khúc | 10 | 4 cụm phân nhóm sau workshop 100 phút | **10/10** |
| 9. Mỗi Primary Persona có scenario & success criteria cụ thể | 10 | Scenario đặt lịch chi tiết kèm tiêu chí đo lường thời gian và độ an tâm | **10/10** |
| 10. Có ít nhất một quyết định UI và cách kiểm chứng liên kết Persona | 10 | Ma trận 5 quyết định thiết kế (cam kết phi y tế, offline mode, ngắt dinh dưỡng) | **10/10** |
| **TỔNG ĐIỂM** | **100** | **ĐẠT XUẤT SẮC THEO RUBRIC PERSONA GUIDELINE** | **100/100** |
