# Xây dựng uy tín và giao tiếp chuyên nghiệp trên uTest

> Ghi chú thực hành về thói quen làm việc đáng tin cậy, chất lượng report và cách xử lý bất đồng trong cycle.

## 1. Uy tín tester được xây dựng như thế nào?

Project team có thể tin tưởng và mời lại tester khi người đó thường xuyên:

- Đọc và làm đúng hướng dẫn trong Overview, thông báo và tin nhắn của cycle.
- Chủ động tham gia sau khi accept, hoàn thành test case và công việc đúng hạn.
- Gửi bug report có giá trị, đúng scope và đủ thông tin.
- Phản hồi TTL/TE kịp thời, lịch sự và chuyên nghiệp.

## 2. Lỗi thường gặp trong bug report

Trước khi gửi, kiểm tra các lỗi dễ làm report khó hiểu hoặc không đạt yêu cầu:

- Title ghi sai trang/khu vực xảy ra lỗi, hoặc mô tả quá chung chung.
- Chọn sai issue type.
- Một bước Actions Performed chứa nhiều hành động, sai thứ tự hoặc dùng URL không hợp lệ.
- Thiếu precondition cần thiết.
- Expected Result và Actual Result không rõ hoặc không phân biệt được.
- Thiếu attachment, sai định dạng, hoặc video không khớp với các bước đã viết.

### Lưu ý thêm cho Academy Challenge

- Đánh số các bước liên tục và đúng thứ tự.
- Nếu lỗi phát sinh khi thực hiện test case, report qua luồng test case khi có thể; chọn **Source** theo cách phát hiện lỗi và hướng dẫn của cycle.
- Chỉ đính kèm Charles log khi được yêu cầu. Nếu cần log, bắt đầu ghi trước khi reproduce và làm theo yêu cầu về điểm bắt đầu, chẳng hạn từ homepage.
- Điền custom fields theo đúng hướng dẫn và format được yêu cầu.
- Trước khi report, kiểm tra Issues và Known Issues. Các lỗi có cùng nguyên nhân gốc có thể bị xem là duplicate dù thao tác hoặc dữ liệu đầu vào khác nhau.
- Đọc kỹ Out of Scope riêng của cycle; không áp dụng giả định từ cycle khác.

## 3. Giữ bình tĩnh và xử lý bất đồng

Nếu kết quả review hoặc phản hồi làm bạn bực bội:

1. Tạm dừng, tránh gửi tin nhắn hoặc thực hiện hành động khi đang nóng giận.
2. Khi đã bình tĩnh, đọc lại rejection reason, Overview, slot instructions, test case và các thông tin liên quan.
3. Nếu bất đồng về issue report, dùng quy trình **Dispute** của uTest và cung cấp lý do cùng bằng chứng phù hợp.
4. Nếu vấn đề liên quan đến test case, slot hoặc cách vận hành cycle, làm theo escalation/contact rules trong cycle; chỉ chuyển cấp khi hướng dẫn cho phép hoặc cần thiết.
5. Viết ngắn gọn, tập trung vào sự việc và giữ thái độ tôn trọng. Không dùng chat công khai hoặc report messages để gây áp lực hay tranh cãi.

Kết quả dispute có thể không như mong muốn. Đọc kỹ phản hồi, rút kinh nghiệm và tiếp tục làm theo quy định của cycle.

## 4. Viết và trao đổi hiệu quả

- **Cụ thể:** Mô tả điều đã xảy ra, thao tác dẫn đến vấn đề và ảnh hưởng quan sát được. Tránh chỉ viết “không hoạt động” nếu có thể nêu hành vi chính xác hơn.
- **Có trình tự:** Sắp xếp sự việc theo thứ tự để người đọc dễ theo dõi.
- **Chuyên nghiệp:** Dùng giọng điệu lịch sự, khách quan; không xúc phạm, đổ lỗi hoặc yêu cầu người khác chấp thuận kết luận của mình.
- **Đủ ý, không lan man:** Chỉ đưa thông tin liên quan và bằng chứng cần thiết.
- **Soát lại trước khi gửi:** Kiểm tra chính tả, ngữ pháp, định dạng và bảo đảm nội dung phản ánh đúng điều đã quan sát.

## Checklist nhanh

- [ ] Đã làm theo hướng dẫn và đúng scope của cycle?
- [ ] Title, loại lỗi, steps, preconditions và kết quả đã rõ ràng?
- [ ] Attachment đúng nội dung, định dạng và yêu cầu?
- [ ] Đã kiểm tra Known Issues/duplicate?
- [ ] Tin nhắn hoặc dispute đã được viết bình tĩnh, lịch sự và có bằng chứng?
