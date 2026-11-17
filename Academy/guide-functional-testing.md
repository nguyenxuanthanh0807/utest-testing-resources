# Hướng dẫn Functional Testing

## Functional Testing là gì?

Functional testing kiểm tra xem tính năng của sản phẩm có hoạt động theo yêu cầu và kỳ vọng đã xác định hay không. Tester thực hiện thao tác, quan sát kết quả thực tế (**Actual Result**) rồi so sánh với kết quả mong đợi (**Expected Result**). Sai lệch có thể là bug nếu phù hợp với yêu cầu và phạm vi của cycle.

## Hai phương pháp thường gặp trong uTest

### Test Case / Scripted Testing

Tester làm theo các bước và kết quả mong đợi đã được định trước:

- Kết quả khớp Expected Result → đánh dấu **Pass**.
- Có sai lệch → đánh dấu **Fail** và làm theo hướng dẫn báo issue của cycle.

### Exploratory / Unscripted Testing

Tester tự khám phá sản phẩm, không bị giới hạn bởi một bộ bước cố định. Cách này có thể phát hiện vấn đề ở những luồng hoặc khu vực chưa được bao phủ bởi test case.

Một cycle có thể dùng một hoặc cả hai phương pháp. Luôn làm theo yêu cầu cụ thể của project.

## Một số loại functional testing

| Loại | Mục tiêu | Ví dụ |
|------|----------|-------|
| **Unit Testing** | Kiểm tra một đơn vị nhỏ như function hoặc method | Xác minh hàm kiểm tra mật khẩu chấp nhận và từ chối đúng loại mật khẩu |
| **Component Testing** | Kiểm tra một module gồm các chức năng liên quan | Kiểm tra luồng đăng nhập xử lý đúng thông tin hợp lệ và không hợp lệ |
| **Smoke Testing** | Kiểm tra nhanh các chức năng cốt lõi sau build/update để biết hệ thống có thể test tiếp không | Mở ứng dụng, đăng nhập, thêm sản phẩm vào giỏ |
| **Sanity Testing** | Kiểm tra tập trung thay đổi hoặc bản sửa gần đây | Xác minh lỗi thêm sản phẩm vào giỏ đã được sửa |
| **Regression Testing** | Đảm bảo thay đổi mới không làm hỏng chức năng cũ trong các khu vực liên quan | Sau khi sửa tìm kiếm, kiểm tra lại đăng nhập, trang sản phẩm và giỏ hàng |
| **Ad-hoc Testing** | Khám phá không theo test case định sẵn để tìm lỗi khó dự đoán | Thử từ khóa tìm kiếm dài hoặc thao tác lặp nhanh |
| **Integration Testing** | Kiểm tra các module kết hợp và trao đổi dữ liệu đúng | Xác minh dữ liệu sản phẩm được chuyển đúng từ danh mục sang giỏ hàng |
| **System Testing** | Kiểm tra hệ thống hoàn chỉnh theo yêu cầu | Thực hiện hành trình từ đăng nhập, tìm sản phẩm đến checkout |
| **User Acceptance Testing (UAT)** | Xác nhận sản phẩm đáp ứng nhu cầu người dùng và yêu cầu nghiệp vụ trước khi phát hành | Nhân viên khách sạn kiểm tra luồng đặt phòng và email xác nhận |
| **Interface Testing** | Kiểm tra giao tiếp giữa các hệ thống hoặc thành phần | Xác minh ứng dụng gửi đúng dữ liệu tới cổng thanh toán và xử lý phản hồi |
| **User Interface (UI) Testing** | Kiểm tra phần tử giao diện có hiển thị đúng thiết kế và dùng được trên kích thước màn hình khác nhau | Kiểm tra nút Checkout không bị che và nội dung không tràn khỏi màn hình |

Các loại kiểm thử có thể khác nhau về cấp độ và mục tiêu. Chỉ thực hiện những gì phù hợp với môi trường, quyền truy cập và phạm vi cycle được giao.

## Cách áp dụng khi test

1. Đọc yêu cầu, test case và phạm vi cycle.
2. Xác định thao tác người dùng cần thực hiện cùng Expected Result.
3. Thực hiện thao tác trong đúng environment và ghi nhận Actual Result.
4. So sánh kết quả thực tế với kỳ vọng; nếu có sai lệch, kiểm tra khả năng tái hiện và Known Issues.
5. Đánh dấu Pass/Fail hoặc báo issue theo đúng quy trình của cycle.

## Functional Testing trong SDLC

**Software Development Life Cycle (SDLC)** mô tả các giai đoạn phát triển và duy trì phần mềm:

1. **Planning:** Xác định mục tiêu, phạm vi, yêu cầu, rủi ro và nguồn lực.
2. **Analysis:** Làm rõ yêu cầu và hành vi hệ thống cần có.
3. **Design:** Thiết kế giao diện, kiến trúc, dữ liệu và cách các thành phần tương tác.
4. **Implementation:** Xây dựng sản phẩm theo thiết kế.
5. **Testing:** Đánh giá sản phẩm theo yêu cầu và tìm lỗi.
6. **Deployment:** Phát hành sản phẩm cho người dùng.
7. **Maintenance:** Theo dõi, sửa lỗi, cập nhật và cải tiến sản phẩm.

Functional testing xác nhận tính năng hoạt động theo yêu cầu. Phát hiện lỗi sớm giúp giảm chi phí sửa, cải thiện chất lượng và tạo cơ sở để đánh giá các khía cạnh khác. Việc kiểm thử cũng xác nhận các thành phần phối hợp đúng và giúp nhóm hiểu sản phẩm có đáp ứng nhu cầu dự kiến hay không.

## Manual Testing và Automation Testing

| Phương pháp | Đặc điểm và điểm mạnh | Hạn chế thường gặp |
|-------------|-----------------------|--------------------|
| **Manual Testing** | Tester tự thao tác như người dùng; phù hợp với exploratory testing, đánh giá trải nghiệm và tình huống cần quan sát, phán đoán của con người | Tốn thời gian ở tác vụ lặp lại; có thể bỏ sót lỗi; khó mở rộng coverage hoặc mô phỏng tải lớn |
| **Automation Testing** | Script và công cụ tự chạy các bước có thể lặp lại; hữu ích cho regression, kiểm tra ổn định và dữ liệu lớn | Cần đầu tư ban đầu và bảo trì script; kém phù hợp với đánh giá chủ quan hoặc giao diện thay đổi liên tục |

Automation thường phù hợp với kịch bản ổn định, lặp lại và quan trọng. Manual testing vẫn cần thiết cho khám phá và nhận xét cần góc nhìn thực tế. Tester cộng đồng uTest thường tham gia manual functional testing, trừ khi project nêu rõ yêu cầu khác.

## Functional và Non-functional Testing

- **Functional testing** kiểm tra **sản phẩm làm gì**: thao tác và chức năng có trả về kết quả đúng yêu cầu không?
- **Non-functional testing** đánh giá **sản phẩm hoạt động như thế nào**: ví dụ tốc độ, khả năng chịu tải, bảo mật, độ tin cậy và mức dễ sử dụng.

Hai nhóm bổ trợ cho nhau. Chỉ kiểm tra trong phạm vi, environment và quyền hạn được cycle cho phép.

## Một số kỹ thuật functional testing

### Equivalence Class Partitioning

Chia dữ liệu đầu vào thành các nhóm được kỳ vọng xử lý giống nhau, rồi chọn đại diện từ mỗi nhóm thay vì thử mọi giá trị. Ví dụ, nếu số lượng hợp lệ từ 1 đến 100, có thể kiểm tra một giá trị hợp lệ và các giá trị đại diện ở dưới 1 hoặc trên 100.

### Boundary Value Analysis

Tập trung kiểm tra tại và sát biên hợp lệ, nơi lỗi xử lý giới hạn thường dễ xuất hiện. Với khoảng 1–100, các giá trị đáng thử gồm 0, 1, 2, 99, 100 và 101.

### Decision Table Testing

Liệt kê các tổ hợp điều kiện và kết quả mong đợi trong bảng. Kỹ thuật này hữu ích khi kết quả phụ thuộc vào nhiều quy tắc, chẳng hạn loại thành viên kết hợp với thời hạn đăng ký để xác định ưu đãi.

### State Transition Testing

Kiểm tra trạng thái thay đổi ra sao theo hành động hoặc chuỗi sự kiện. Ví dụ, xác minh tài khoản chuyển từ hoạt động sang khóa sau số lần nhập PIN sai theo quy định.
