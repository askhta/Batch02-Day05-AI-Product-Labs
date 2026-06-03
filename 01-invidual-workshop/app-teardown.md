# Workshop — Mổ App AI Thật

## Sản phẩm chọn phân tích: MoMo — Moni / Trợ thủ tài chính AI

## 1. Bối cảnh thử nghiệm

**Sản phẩm:** MoMo — Moni / Trợ thủ tài chính AI
**AI feature:** Trợ lý quản lý chi tiêu, ghi chép chi tiêu bằng chat, phân tích giao dịch, phân loại khoản chi, nhắc nhở khi chi tiêu quá tay.
**User được hứa sẽ được giúp:** Người dùng cá nhân có nhu cầu kiểm soát chi tiêu hằng ngày nhưng không muốn tự ghi chép thủ công, không muốn tự phân loại từng giao dịch, và cần một trợ lý giải thích tình hình tài chính cá nhân bằng ngôn ngữ dễ hiểu.

**Task tôi chọn để thử:**
Tôi đóng vai một người dùng bình thường muốn hiểu “chi tiêu linh tinh” trong tháng là gì, gồm những khoản nào, và nếu AI phân loại sai thì tôi có thể sửa lại được không.

---

## 2. Promise vs Reality

### 2.1. Product hứa gì?

MoMo định vị Moni/Trợ thủ tài chính AI như một trợ lý giúp người dùng quản lý tiền dễ hơn. Promise chính của sản phẩm gồm:

* Người dùng chỉ cần chat, AI có thể ghi chép khoản chi.
* AI tự động nhận diện và phân loại giao dịch.
* Người dùng có thể xem báo cáo chi tiêu theo tuần/tháng.
* AI hỗ trợ theo dõi, nhắc nhở để người dùng không chi tiêu quá tay.
* AI có thể đưa ra lời khuyên hoặc gợi ý chi tiêu hợp lý.

### 2.2. Tôi kỳ vọng AI làm được task nào?

Khi tôi hỏi một câu mơ hồ như:

> “Tháng này tôi chi tiêu linh tinh bao nhiêu?”

Tôi kỳ vọng AI không chỉ trả lời chung chung, mà phải hiểu rằng “linh tinh” là một khái niệm mơ hồ. AI nên làm một trong các việc sau:

1. Hỏi lại người dùng muốn hiểu “linh tinh” theo nghĩa nào: khoản nhỏ lẻ, khoản không thiết yếu, khoản chưa phân loại, hay khoản ngoài ngân sách.
2. Gợi ý 2–3 cách nhóm giao dịch để người dùng chọn.
3. Hiển thị danh sách giao dịch nghi ngờ là “linh tinh”.
4. Cho phép người dùng sửa lại danh mục ngay trong luồng chat.
5. Ghi nhớ correction để lần sau phân loại tốt hơn.

### 2.3. Khi dùng thật, điểm gãy xuất hiện ở đâu?

**Điểm gãy chính:** AI/product chưa có recovery path đủ rõ khi intent của user mơ hồ hoặc khi phân loại giao dịch chưa đúng.

Cụ thể, với câu hỏi kiểu:

> “Chi tiêu linh tinh của tôi tháng này là gì?”
> “Sao khoản ăn trưa lại bị xếp vào mua sắm?”
> “Tôi muốn sửa khoản này sang ăn uống thì làm thế nào?”

AI có thể đưa ra câu trả lời theo hướng giải thích chung hoặc hiển thị thông tin chi tiêu, nhưng chưa đủ rõ các bước để user sửa sai ngay tại điểm phát hiện lỗi. User phải tự đoán nên vào “Sổ chi tiêu”, “Danh mục”, “Lịch sử giao dịch” hay “Quản lý chi tiêu” để chỉnh lại.

### 2.4. Evidence

**Evidence 1 — Screenshot promise:**
[Chèn screenshot màn hình giới thiệu tính năng Moni/Quản lý chi tiêu trong app hoặc website MoMo]
Nội dung cần thể hiện: AI giúp ghi chép chi tiêu, phân loại tự động, báo cáo chi tiêu, nhắc nhở chi tiêu.

**Evidence 2 — Prompt/input đã thử:**

Prompt 1:

> “Tháng này tôi chi tiêu linh tinh bao nhiêu?”

Prompt 2:

> “Những khoản nào của tôi là chi tiêu không cần thiết?”

Prompt 3:

> “Khoản chuyển tiền ăn trưa hôm qua bị xếp sai danh mục, sửa thế nào?”

**Evidence 3 — Observation:**
Khi intent mơ hồ, AI chưa chủ động hỏi lại tiêu chí “linh tinh” là gì. Khi user nghi ngờ phân loại sai, luồng chưa làm nổi bật hành động sửa danh mục hoặc xác nhận lại với user. Điều này khiến người dùng không biết nên tiếp tục chat, tự tìm trong menu, hay bỏ qua lỗi phân loại.

**Evidence 4 — Screenshot reality:**
[Chèn screenshot câu trả lời của AI sau khi nhập prompt trên]
Đánh dấu vào ảnh phần: AI trả lời nhưng chưa có nút “Sửa danh mục”, “Xem giao dịch liên quan”, “Không đúng?”, “Hỏi lại tiêu chí”.

---

## 3. Phân tích 4 paths

| Path                | Câu hỏi cần trả lời                                                           | Quan sát hiện tại                                                                                                                                  | Đánh giá                                                                               |
| ------------------- | ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| Happy path          | Khi AI đúng và tự tin, user thấy gì?                                          | Nếu user hỏi rõ như “Tháng này tôi ăn uống hết bao nhiêu?”, AI có thể đưa ra tổng chi tiêu hoặc hướng người dùng tới báo cáo/danh mục chi tiêu.    | Path này tương đối ổn vì intent rõ, dữ liệu có cấu trúc, AI dễ trả lời.                |
| Low-confidence path | Khi AI không chắc, hệ thống có hỏi lại, show options hoặc chuyển người không? | Với từ mơ hồ như “linh tinh”, “không cần thiết”, “tiêu hơi nhiều”, AI chưa nên đoán ngay. Product cần hỏi lại hoặc gợi ý các cách hiểu.            | Đây là điểm thiếu quan trọng. Low-confidence path chưa rõ.                             |
| Failure path        | Khi AI sai, user biết bằng cách nào và sửa thế nào?                           | Nếu AI phân loại sai giao dịch, user khó biết lỗi nằm ở AI, dữ liệu giao dịch, hay danh mục. Chưa thấy cơ chế nổi bật để user báo “phân loại sai”. | Failure path yếu vì không có dấu hiệu đủ rõ để user phát hiện và sửa lỗi.              |
| Correction path     | Khi user sửa, correction có được lưu/log/học lại không hay biến mất?          | Product có thể cho phép sửa danh mục, nhưng trong luồng AI/chat, việc correction có được ghi nhớ cho lần sau chưa được thể hiện rõ.                | Correction path chưa minh bạch. User không biết lần sau AI có phân loại tốt hơn không. |

---

## 4. Finding viết thành product decision

### Finding chính

Khi user hỏi về một khái niệm chi tiêu mơ hồ như “chi tiêu linh tinh”, “khoản không cần thiết”, hoặc phản hồi rằng một giao dịch bị phân loại sai, AI/product có xu hướng xử lý như một truy vấn thông tin thông thường thay vì nhận diện đây là tình huống low-confidence hoặc correction.

Hậu quả là user không biết AI đang hiểu “linh tinh” theo tiêu chí nào, không biết danh sách giao dịch nào đang bị nghi ngờ, và không có đường đi rõ để sửa phân loại ngay trong workflow. Điều này làm giảm niềm tin vào tính năng quản lý chi tiêu bằng AI, vì người dùng cảm thấy AI có thể nói đúng/sai nhưng mình không kiểm soát được cách AI kết luận.

Lỗi thuộc layer: **Intent + Data/Tool + UX Recovery**.

Nên sửa bằng: bổ sung low-confidence path và correction path trong luồng chat Moni. Khi AI không chắc, hệ thống cần hỏi lại hoặc đưa lựa chọn. Khi user nói AI phân loại sai, hệ thống cần hiển thị giao dịch liên quan, cho phép sửa danh mục ngay, và thông báo rằng correction đã được ghi nhận để cải thiện phân loại sau này.

---

## 5. Product decision đề xuất

### Requirement 1 — Low-confidence clarification

Khi user dùng từ mơ hồ như “linh tinh”, “không cần thiết”, “tiêu quá tay”, “khoản vặt”, AI không được trả lời như thể đã chắc chắn. AI phải chuyển sang trạng thái hỏi lại.

Ví dụ response nên là:

> “Bạn muốn hiểu ‘chi tiêu linh tinh’ theo nghĩa nào?
>
> 1. Khoản nhỏ lẻ dưới 100.000đ
> 2. Khoản ngoài ngân sách đã đặt
> 3. Khoản không thuộc nhu cầu thiết yếu
> 4. Khoản chưa được phân loại rõ”

### Requirement 2 — Show evidence behind answer

Khi AI đưa ra kết luận “bạn chi nhiều vào khoản linh tinh”, AI phải hiển thị cơ sở:

* Tổng tiền
* Số giao dịch
* 3–5 giao dịch tiêu biểu
* Danh mục đang dùng để tính
* Nút “Không đúng?” hoặc “Sửa phân loại”

### Requirement 3 — Correction flow

Khi user nói:

> “Khoản này không phải mua sắm, đây là ăn uống.”

AI cần mở correction flow:

1. Xác nhận giao dịch cần sửa.
2. Cho user chọn danh mục đúng.
3. Lưu thay đổi.
4. Thông báo: “Đã ghi nhận. Các giao dịch tương tự sau này sẽ được ưu tiên phân loại vào Ăn uống.”

### Requirement 4 — Human/support fallback

Nếu AI không xác định được giao dịch hoặc user hỏi về vấn đề liên quan khiếu nại/tiền bị trừ nhầm, AI không nên tiếp tục trả lời chung chung. Cần chuyển sang flow hỗ trợ chính thức:

* “Xem lịch sử giao dịch”
* “Gửi yêu cầu hỗ trợ”
* “Liên hệ CSKH”
* “Tạo mã yêu cầu”

---

## 6. Sketch as-is / to-be

### As-is flow

```text
USER
  |
  | Hỏi: “Tháng này tôi chi tiêu linh tinh bao nhiêu?”
  v
AI/MONI
  |
  | Hiểu câu hỏi như một truy vấn chi tiêu thông thường
  | Có thể trả lời tổng quan hoặc gợi ý xem báo cáo
  v
USER
  |
  | Không biết “linh tinh” được AI hiểu là gì
  | Không thấy danh sách giao dịch liên quan
  | Không biết sửa phân loại ở đâu
  v
ĐIỂM GÃY
  |
  | User mất niềm tin / bỏ qua / tự tìm trong menu
```

**Điểm gãy trong as-is:** AI không xử lý rõ intent mơ hồ và không tạo đường recover khi user muốn sửa sai.

---

### To-be flow

```text
USER
  |
  | Hỏi: “Tháng này tôi chi tiêu linh tinh bao nhiêu?”
  v
AI/MONI
  |
  | Nhận diện low-confidence:
  | “Linh tinh” là khái niệm mơ hồ
  v
AI HỎI LẠI
  |
  | Bạn muốn hiểu “linh tinh” theo nghĩa nào?
  | [Khoản nhỏ lẻ] [Ngoài ngân sách] [Không thiết yếu] [Chưa phân loại]
  v
USER CHỌN TIÊU CHÍ
  |
  | Chọn: “Không thiết yếu”
  v
AI TRẢ KẾT QUẢ CÓ EVIDENCE
  |
  | Tổng tiền: ...
  | Số giao dịch: ...
  | Giao dịch tiêu biểu: ...
  | Danh mục được tính: ...
  | CTA: [Xem chi tiết] [Sửa phân loại] [Không đúng?]
  v
USER PHÁT HIỆN SAI
  |
  | “Khoản ăn trưa này không phải mua sắm”
  v
AI CORRECTION FLOW
  |
  | Chọn danh mục đúng: [Ăn uống]
  | Lưu correction
  | Ghi nhận rule cho lần sau
  v
KẾT QUẢ
  |
  | User hiểu AI tính thế nào
  | User sửa được lỗi
  | Product có dữ liệu feedback để cải thiện
```

---

## 7. SPEC thay đổi gì sau finding này?

Finding này sẽ đổi SPEC của Moni theo hướng: **không chỉ có “AI trả lời câu hỏi chi tiêu”, mà phải có đầy đủ low-confidence path, evidence display và correction loop cho các tình huống AI không chắc hoặc phân loại sai.**

Cụ thể, SPEC cần bổ sung:

1. **Intent confidence rule:** Nếu intent chứa từ mơ hồ về chi tiêu, AI phải hỏi lại thay vì đoán.
2. **Evidence requirement:** Mọi kết luận tài chính cá nhân phải có số liệu, danh mục và giao dịch minh họa.
3. **Correction requirement:** User có thể sửa phân loại ngay trong chat.
4. **Feedback logging:** Mọi correction phải được lưu để cải thiện phân loại sau.
5. **Fallback requirement:** Vấn đề liên quan giao dịch tiền thật/khiếu nại phải có đường chuyển CSKH hoặc tạo yêu cầu hỗ trợ.

---

## 8. Kết luận ngắn

MoMo Moni có promise mạnh: biến AI thành trợ thủ tài chính giúp người dùng kiểm soát chi tiêu dễ hơn. Tuy nhiên, trong workflow thật, điểm gãy không nằm ở UI đẹp hay xấu mà nằm ở khả năng recovery khi AI không chắc hoặc khi AI phân loại sai.

Product decision quan trọng là: **AI tài chính không được chỉ “trả lời”; AI phải biết hỏi lại, đưa bằng chứng, cho sửa sai và ghi nhận correction.** Đây là điều quyết định user có tin AI đủ để dùng lâu dài trong quản lý tiền cá nhân hay không.

---

## 9. Checklist tự kiểm

* [x] Có product được chọn rõ ràng: MoMo — Moni / Trợ thủ tài chính AI.
* [x] Có promise vs reality.
* [x] Có prompt/input đã thử.
* [x] Có observation cụ thể.
* [x] Có đủ 4 paths: Happy, Low-confidence, Failure, Correction.
* [x] Finding được viết thành product decision.
* [x] Có sketch as-is / to-be.
* [x] Có câu nêu rõ finding này sẽ đổi gì trong SPEC.
* [ ] Cần chèn screenshot thật từ app/web trước khi nộp.
