# 04 — Charles Proxy Testing

> ⚪ Trạng thái: CHƯA MỞ (phải pass Mobile Device Testing trước)

## Mục tiêu học tập (sẽ điền khi mở cycle)
- [ ] Bắt/giải mã traffic HTTP(S) bằng Charles Proxy
- [ ] (điền sau khi đọc overview)

## Ghi chú từ Academy (Charles logs — khi cycle yêu cầu)
- Log phải **giải mã hết** (decrypt), chỉ truy cập test website khi bắt log
- Root certificate phải cài đúng trên máy + mobile (sai sẽ thấy `<unknown>`)
- Cấu hình SSL: host `*` port `443`
- Sau khi reproduce → File → **Save Session** → upload `.chls` / `.chlsz`
- URL test phải hiện trong log; bắt log trên đúng device reproduce bug

## Ghi chú từ overview
(điền sau)

## FAQ
(điền sau)
