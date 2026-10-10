# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)

> Nhật ký được tổng hợp dựa trên mã nguồn hiện có (`index.html`, `style.css`) và yêu cầu trong đề. Các prompt dưới đây là bản mô tả lại, không phải bản chép nguyên văn lịch sử trò chuyện.

- **Họ và tên:** Khoa LaDang
- **MSSV:** 526000154
- **Tên đề tài Website:** GameHub — Thế giới game của bạn
- **Công cụ AI đã sử dụng:** GitHub Copilot trong VS Code

## 1. Yêu cầu ban đầu (System/Initial Prompt)

> Hãy xây dựng giao diện trang chủ cho website cửa hàng game trực tuyến tên GameHub bằng HTML và CSS. Thiết kế theo phong cách gaming hiện đại, nền tối, điểm nhấn màu xanh ngọc và xanh dương. Trang cần có thanh điều hướng, khu vực game nổi bật, danh mục thể loại, danh sách game, khuyến mãi, game bán chạy/game mới, lời kêu gọi theo dõi và chân trang. Nội dung bằng tiếng Việt, bố cục rõ ràng, hoạt động tốt trên máy tính và điện thoại. Dùng HTML ngữ nghĩa, CSS variables để dễ chỉnh sửa và chú ý khả năng truy cập.

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iteration Iterations)

### Lần 1: Dựng khung Semantic HTML & CSS Variable

- **Prompt đã dùng:** Tạo trang chủ GameHub theo yêu cầu ban đầu; chia nội dung thành các section hợp lý bằng semantic HTML, khai báo màu sắc/khoảng cách/kích thước dùng chung bằng CSS variables và bổ sung responsive cho các kích thước màn hình khác nhau.
- **Kết quả AI tạo ra:** Khung trang gồm header và navigation, hero giới thiệu game, danh mục thể loại, lưới game nổi bật, banner ưu đãi, khu vực game bán chạy và game mới, newsletter và footer. CSS dùng các biến trong `:root`, bố cục co giãn theo màn hình và có các trạng thái tương tác.
- **Nhận xét & Tinh chỉnh của SV:** Yêu cầu nội dung tiếng Việt, thứ bậc tiêu đề và điều hướng rõ ràng; bổ sung mô tả ảnh/nhãn truy cập, liên kết bỏ qua điều hướng và trạng thái focus để trang dễ sử dụng hơn. Chỉnh các breakpoint để nội dung không bị tràn trên màn hình nhỏ.

### Lần 2: Rà soát chuyển động và khả năng tích hợp Animate.css & AOS

- **Prompt đã dùng:** Kiểm tra giao diện hiện tại và đề xuất cách bổ sung hiệu ứng Animate.css/AOS cho hero, thẻ game và các section khi cuộn; bảo đảm hiệu ứng không làm giảm khả năng truy cập và có phương án khi người dùng yêu cầu giảm chuyển động.
- **Kết quả AI tạo ra:** Khi rà soát, trang đã có transition/hover và hỗ trợ `prefers-reduced-motion`, nhưng chưa nạp hoặc khởi tạo Animate.css/AOS. Phần thiếu này được xử lý ở lần tinh chỉnh tiếp theo.
- **Thách thức gặp phải:** AOS cần được nạp và khởi tạo bằng JavaScript thì hiệu ứng xuất hiện khi cuộn mới hoạt động; đồng thời cần tránh để nội dung bị ẩn nếu thư viện không tải được hoặc người dùng bật giảm chuyển động.
- **Cách sửa prompt (Debug prompt):** Yêu cầu kiểm tra cả phần nạp thư viện, khởi tạo AOS, hiệu ứng trên các thành phần chính và hỗ trợ `prefers-reduced-motion`; chỉ thêm thuộc tính AOS khi có thể khởi tạo thư viện.

### Lần 3: Tích hợp hiệu ứng Animate.css & AOS

- **Prompt đã dùng:** Tích hợp Animate.css cho phần Hero và AOS cho các section, thẻ thể loại, thẻ game và danh sách bán chạy. Khởi tạo hiệu ứng khi cuộn, chạy một lần, và không kích hoạt hiệu ứng khi người dùng bật chế độ giảm chuyển động.
- **Kết quả AI tạo ra:** Animate.css được dùng cho nội dung Hero; AOS được nạp và khởi tạo cho các phần nội dung khi cuộn với độ trễ nhẹ theo nhóm. Thuộc tính AOS chỉ được thêm sau khi kiểm tra hỗ trợ giảm chuyển động và thư viện đã tải; hiệu ứng CSS hover/focus sẵn có vẫn được giữ.
- **Nhận xét & Tinh chỉnh của SV:** Kiểm tra lại trên trình duyệt, cuộn qua các section và thử bật chế độ giảm chuyển động; nội dung cần hiển thị bình thường ngay cả khi AOS không tải được.

## 3. Đánh giá cá nhân về quá trình Vibe Coding

- **AI đã giúp bạn tiết kiệm thời gian ở giai đoạn nào nhất?** AI hỗ trợ lên nhanh cấu trúc trang, gợi ý cách chia section, viết CSS variables và tạo các breakpoint responsive; nhờ đó có thể tập trung rà soát nội dung và trải nghiệm sử dụng.
- **Bài học rút ra khi đặt câu hỏi (Prompt) cho AI trong thiết kế web?** Prompt nên nêu rõ mục tiêu website, phong cách giao diện, nội dung cần có, công nghệ/giới hạn kỹ thuật và yêu cầu responsive, truy cập. Sau khi AI tạo mã, cần kiểm tra lại mã nguồn thực tế, chạy thử trên nhiều kích thước màn hình và không ghi nhận tính năng/thư viện chưa được triển khai.