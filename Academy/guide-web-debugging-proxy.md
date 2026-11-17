# 🌐 GUIDE — Web Debugging Proxy (Charles & Fiddler)

> ⭐ Thu thập browser console log, Charles Proxy (Desktop + Mobile), Fiddler, FAQ troubleshooting
> Cập nhật lần cuối: **11/11/2026** · Style: EN = luật gốc · VN = tóm tắt thực chiến

---

## 1. Web Debugging Proxy là gì?

**EN:** A web debugging proxy is a program that works as a proxy server, enabling the user to view and capture all HTTP/HTTPS traffic between the user device and the testing website/application on the internet. Logs help developers diagnose and fix network-related problems.

### Công cụ phổ biến nhất

| Tool | Description |
|------|-------------|
| **Charles Proxy** | Monitoring HTTP/SSL traffic, mock requests, diagnose network issues |
| **Fiddler** | Same capabilities — Classic / Everywhere / Cap |

---

## 2. Yêu cầu về Log

**EN:** Logging requirements: decrypted log, correct testing website/app traffic, correct file format.

| Yêu cầu | Chi tiết |
|---------|----------|
| **Decrypted** | Tất cả traffic phải được decrypt |
| **Traffic đúng site** | Phải chứa traffic của website/app đang test |
| **Đúng format file** | Charles: `.chls` hoặc `.chlz` · Fiddler: `.saz` |

> 💡 Luôn upload **toàn bộ log**, không lọc trừ khi cycle yêu cầu.

---

## 3. Charles Proxy — Desktop Setup

### 3.1 Windows

1. Tắt VPN
2. Cấu hình Firewall/Antivirus → thêm Charles vào exception list (không cần tắt toàn bộ AV/Firewall)
3. Download/install **Charles Proxy 64-bit** (hoặc 32-bit nếu hệ điều hành 32 bit: Settings > System > About > xem System type)
4. Mở Charles Proxy
5. **Cài root certificate:** Help > SSL Proxying > Install Charles Root Certificate → Install Certificate → Browse chọn **Trusted Root Certification Authorities** → Next → Finish
6. Đóng Charles → restart máy tính
7. Mở lại → Proxy > đảm bảo **Windows Proxy** enabled
8. **SSL Proxy Settings:** Proxy > SSL Proxy Settings > Enable SSL Proxying > Add > Host=`*`, Port=`443` → OK
9. Click broom icon để dọn log cũ → đảm bảo recording ON
10. Mở browser → reproduce bug từ homepage
11. File > Save Session → lưu file `.chls` hoặc `.chlz`

### 3.2 macOS

Các bước tương tự Windows, khác ở phần cài cert:

- Help > SSL Proxying > Install Charles Root Certificate → Keychain Access mở ra → search "Charles" → double click "Charles Proxy CA" → mở trust → đổi thành **Always Trust** → nhập password Mac
- Restart máy
- Proxy > đảm bảo **macOS Proxy** enabled

### 3.3 Firefox Browser

Sau setup Charles cơ bản → Firefox Settings > Network Settings > Chọn **Use system proxy settings**.

### 3.4 Notes quan trọng

- Decrypt tất cả traffic: Host=`*`, Port=`443`
- Decrypt chỉ một site cụ thể: Host=`*domain.com*` (vd `*utest*`)
- Lưu ý license: dùng >30 phút mỗi lần → mua license theo EULA. Mỗi user chịu trách nhiệm tuân thủ.

---

## 4. Charles Proxy — Mobile Setup

### Preconditions (Android + iOS)

- ✅ Máy tính + điện thoại cùng WiFi network
- ✅ Không có VPN nào đang chạy trên cả 2 thiết bị
- ✅ Đã cấu hình Firewall cho Charles Proxy
- ✅ Charles Proxy đang chạy trên máy tính

### 4.1 Android

#### Step 1–8: Setup Charles Desktop trước (theo mục 3)

#### Step 9: Lấy IP của máy tính

Charles Proxy > Help > Local IP Address → note down IP (vd `192.168.8.111`)

#### Step 10: Configure Proxy Settings

Proxy > Proxy Settings → ensure HTTP Proxy port = **8888**

#### Step 11: Kết nối mobile với Charles

Mobile > WiFi Settings > Chọn WiFi hiện tại > Advanced options > Change proxy setting sang **Manual** → điền:
- Proxy hostname: `<IP máy tính>`
- Proxy port: **8888**

→ Khi mở trang web trong mobile → popup request xuất hiện trên Charles → phải **Allow** connection

#### Step 12: Cài root certificate trên mobile

Dùng Chrome (khuyến nghị): truy cập `http://chls.pro/ssl` hoặc `http://charlesproxy.com/getssl`

Authenticate lock screen → chọn cert name → **VPN và apps** → OK

⚠️ **Android 11+ phải làm thêm:**
- Settings > Security > Encryption & Credentials > Install a certificate > CA Certificate → Accept warning → Duyệt đến cert file vừa tải → Confirm install

Hoặc: Settings > Biometrics and security > Other security settings > Install from device storage > CA Certificate → Accept → Authenticate → Duyệt cert → Confirm

#### Step 13: Chỉ thu traffic mobile, không phải computer

Trong Charles Proxy > Proxy > TẮT Windows/macOS Proxy

Làm vậy sẽ không thu traffic PC, chỉ thu mobile. Quay lại bật sau khi finish mobile logging.

#### Step 14: Clear log + reproduce

Broom icon để clear → ensure recording ON → Mở browser trên mobile → reproduce bug từ homepage → Save Session `.chls` hoặc `.chlz`

#### Firefox mobile thêm bước

Settings > About Firefox > TAP LOGO 5 LẦN > quay lại Settings > Secret Settings > Bật **Use third party CA certificates** → Restart Charles + browser → mở trang test

### 4.2 iOS

Setup tương tự Android, khác chi tiết:

#### Connect proxy:
WiFi Settings > tap `(i)` cạnh WiFi > Configure Proxy > Manual > Server: `<IP PC>` / Port: **8888**

#### Cài certificate:
Mở Safari → `http://chls.pro/ssl` > Allow > Cài profile → General > VPN and Device Management (iOS 15+) HOẶC Profiles and Device Management (iOS cũ) > Select Charles Proxy CA profile > Install
- General > About > Certificate Trust Settings > **Bật ENABLE FULL TRUST FOR ROOT CERTIFICATES** cho Charles certificate

Sau đó các bước giống Android: tắt Windows/macOS Proxy trong Charles → clear logs → reproduce mobile → save session.

---

## 5. Charles Proxy Profile

**EN:** Profile là tập hợp các setting/cấu hình cho phép capture/save log CHỈ với traffic cần thiết. Mặc định Charles dùng default profile (capturing ALL traffic). Nếu cycle cung cấp custom profile (`*.xml`) → IMPORT để thu thập chính xác thông tin khách hàng muốn.

### Import Profile

Tools > Import/Export Settings > Tab Import > Choose File > Chọn file `*.xml` từ cycle > đảm bảo tất cả options được chọn > Import

### Switch Profile

Tools > Profiles > Tìm profile cần dùng > Tích checkbox **Activate** > Đóng window

### Delete Profile

Tools > Profiles > Switch sang profile khác (không phải cái muốn xóa) > Chọn tên profile cần xóa > Remove > OK

💡 Academy Charles Proxy practice cycle: dùng **default profile**, không filter.

---

## 6. Filter Traffic trong Charles

Đôi khi cần lọc bỏ traffic không liên quan để customer/developer dễ phân tích.

### Include specific traffic (chỉ include domain mong muốn)

Proxy > Recording Settings > Include tab > Add > Domain bọc `*`: `*utest*` → bao gồm utest.com, utest.net, utest.io (tất cả có chữ utest). `*utest.com*` → chỉ include duy nhất utest.com. OK > OK

### Exclude specific traffic (exclude domain không muốn)

Proxy > Recording Settings > Exclude tab > Add > Tương tự format như Include.

### ⚠️ Quan trọng

- Include/Exclude có thể dùng đồng thời
- **Exclude thắng Include** nếu trùng host
- Sau khi kết thúc testing → **update/remove** Include/Exclude options trước/sau phiên làm việc

### Focused Hosts

View > Focused Hosts (hoặc Ctrl+Shift+O) > Add button > Enter domain + port (vd `*academybugs*` / 443) → OK → OK

Traffic được chia làm 2 section: domain bạn focus + "Other Hosts". Remove bằng cách select host > Remove > OK.

---

## 7. Collecting Charles Logs without WiFi Router

Nếu không có WiFi router → dùng **Mobile Hotspot** từ điện thoại phụ.

1. Điện thoại phụ: bật Mobile Hotspot (Android: Network & Internet > Mobile Hotspot; iOS: Settings > Mobile Data > Personal Hotspot > Allow Others to Join) → note SSID/password
2. Kết nối máy tính vào hotspot đó
3. Cài + cấu hình Charles như hướng dẫn Desktop course
4. Kết nối máy test (điện thoại chính) vào cùng hotspot
5. Config proxy trên mobile → cài cert → reproduce → save session

---

## 8. Fiddler — Desktop Setup

### 8.1 Các phiên bản

| Phiên bản | OS | Ghi chú |
|-----------|-----|---------|
| **Fiddler Classic** | Windows only | Đủ tính năng, free |
| **Fiddler Everywhere** | Win/Mac/Linux | UI modern, advanced features — trial 10 ngày, commercial cần license |
| **Fiddler Cap** | Windows only | Simple version, trace capture only — dùng KHI TTL/yêu cầu |

*Xem kỹ Overview cycle để biết software nào cần dùng.*

### 8.2 Fiddler Everywhere — HTTPS Capture

1. Sign In/Sign Up account (hoặc dùng credential từ cycle)
2. Settings (gear icon) > HTTPS tab > Trust Fiddler CA > Yes (Windows) / Nhập admin credentials (Mac)
3. Enable Capture HTTPS traffic > Save > Đóng Settings
4. Close unnecessary tabs/apps > Clear stored logs > Remove All (Traffic pane)
5. System Proxy switch > Ensure ON
6. Clear browser cache trước khi capture
7. Reproduce issue từ homepage
8. Filter nếu cần: Filters button > Add Condition > Add URL/domain > Apply

### 8.3 Fiddler Classic — HTTPS Capture

1. Tools > Options > HTTPS tab > Enable Decrypt HTTPS traffic > Yes > Yes > Yes (trusting certificate)
2. Close all unnecessary browser tabs/apps in background
3. Clear logs > X icon (toolbar) > Remove all hoặc Ctrl+X
4. File menu > ensure Capture Traffic là ENABLED
5. Clear browser cache
6. Reproduce issue từ homepage
7. Filter: Filters tab > Use Filters > No Host Filter dropdown > Show only following Hosts > Enter domain > Actions > Run Filterset now

### 8.4 Export session

**Fiddler Everywhere:** One entry > Ctrl+A > Right-click > Export > Fiddler Archive (.SAZ) > Next > Save location + rename > Save > Save again

**Fiddler Classic:** File > Save > All Sessions > Location + rename > Save

### 8.5 Firefox Browser bổ sung

Nếu dùng Firefox với Fiddler:
1. Hamburger menu > Settings > Network Settings > **Use system proxy settings** > OK
2. Sau khi hoàn thành: Set back to No proxy
3. Với Fiddler Classic (Windows): Trong Firefox gõ `about:config` > Accept Risk > Search `security.enterprise_roots.enabled` > Toggle thành **TRUE**

### 8.6 Fiddler Cap

Download > cài đặt > Open > Decrypt HTTPS traffic > OK > Yes > Clear Cookies/Clear Cache > Start Capture (nút 1) → Reproduce issue > Stop Capture (nút 2) > Save Capture (nút 3) > Save.

Đóng app sẽ prompt delete certificate → chọn Yes rồi cài mới khi dùng lại.

---

## 9. Fiddler — Mobile Setup

### Preconditions

- Cùng network giữa máy tính + mobile
- Không VPN trên cả 2 devices
- Đã cấu hình Firewall cho Fiddler
- Fiddler đang chạy

### 9.1 Chuẩn bị trên máy tính

1. Settings > Connections > Bật "Allow remote computers to connect" > Port số **8866** > Save
2. Lấy IP máy tính:
   - Windows: Command Prompt `ipconfig /all` → IPv4 address
   - macOS: Network Utility > Info Tab > Network interface > IPv4

### 9.2 Android

Mobile > WiFi Settings > Chọn WiFi > Advanced options > Change proxy setting sang Manual:
- Proxy hostname: `<IP máy tính>`
- Proxy port: **8866**

Save.

Install Fiddler Root Certificate trên mobile: trình duyệt truy cập `http://ipv4.fiddler:8866/FiddlerRoot.cer` → authenticate > VPN và apps > OK.

Close browser/apps trên máy tính > Clear logs > Turn OFF Live Traffic toggle (không thu traffic PC) > Reproduce issue mobile > Save Archive > All Sessions > .SAZ format (không encryption)

### 9.3 iOS

Same setup step 1–2 trên máy tính.
Mobile: WiFi Settings > (i) > Configure Proxy > Manual > Proxy hostname: `<IP PC>` / Port: **8866** > Save.

Install cert: trình duyệt truy cập `http://ipv4.fiddler:8866/FiddlerRoot.cer` > Allow > General > VPN & Device Management (iOS 15+)/Profiles & Device Management (cũ hơn) > DO_NOT_TRUST_FiddlerRoot > Install
- General > About > Certificate Trust Settings > **Enable Full Trust For Root Certificates** cho Fiddler cert

Tiếp tục: close apps → clear logs → tắt Live Traffic → reproduce → save archive → .saz.

---

## 10. 🛠️ FAQ — Troubleshooting 16 câu

### Q1: Vấn đề khi cài Charles/Fiddler?

- Đảm bảo có quyền Admin trên máy tính
- Hệ điều hành 32-bit → download older version hỗ trợ 32-bit
- Cài JRE (Java Runtime Environment)
- Windows → cài Visual C++ redistributable

### Q2: Tại sao phải cài root certificate?

Để Charles/Fiddler có thể **decrypt HTTPS traffic**.

### Q3: Format file đúng cho log? Upload toàn bộ hay chỉ một phần?

Charles: `.chls`/`.chlz` · Fiddler: `.saz` → luôn upload **toàn bộ log**.

### Q4: "Installation failed, unable to read certificate" trên Android?

Settings > Security > Credential Storage > Install a Certificate > Chọn cert → Install

### Q5: "Page not found" sau khi kết nối mobile proxy?

- Kiểm tra Charles/Fiddler đang chạy trên máy tính
- Mobile + máy tính cùng mạng wireless
- VPN tắt (cả 2)
- Firewall cho phép Charles/Fiddler
- WiFi connection option trên máy tính đặt "Public" (không Private)

### Q6: "Your connection is not secure" khi cài cert mobile?

- Tap Advanced → Proceed → Install cert
- Thử gõ `chls.pro/ssl` hoăc `charlesproxy.com/getssl` (KHÔNG thêm http/https protocol)
- Đóng browser, Charles, thử lại hoặc restart máy + mobile
- Xóa cert cũ trên cả PC/mobile rồi cài lại

### Q7: Làm sao biết log đã decrypted?

**Charles Proxy log icons:**
| Icon | Ý nghĩa |
|------|---------|
| 🔵 Blue circle | Decrypted HTTP/1.1 |
| ⚡ Lightning icon | Decrypted HTTP/2.0 |
| ❌ Red cross | Cert chưa được cài hoặc sai |
| 🔒 Lock icon | Chưa decrypt (SSL settings sai) |

Chỉ có Lock icon + Red cross → **CHƯA ĐƯỢC DECRYPTED**.

**Fiddler:** Có ổ khóa đóng bên cạnh entries → chưa decrypt HTTPS.

### Q8: Tất cả đều có lock logo?

SSL proxy settings cấu hình sai → Charles > Proxy > SSL Proxy Settings > Enable SSL Proxying > Add > Host=`*` / Port=`443`

### Q9: Xóa root certificate khỏi device?

Tên cert: Charles = `Charles Proxy CA`; Fiddler = `DO_NOT_TRUST_FiddlerRoot`

| Device | Cách xóa |
|--------|----------|
| Windows | Win+R → `certmgr.msc` → Trusted Root Certification Authorities → Find by name → Delete |
| macOS | Keychain Access → Search → right click → Delete |
| Android 10+ | Settings > Security > Encryption & Credentials > Trusted credentials > User tab → Tap → Remove |
| Samsung Android 10+ | Settings > Biometrics and security > Other security settings > Users certificates → Tap → Remove |
| Xiaomi | Settings > Password & security > Privacy > Encryption & credentials > Trusted credentials > User tab → Tap → Remove |
| Android cũ | Settings > Security > View security certificates → Tap → Remove |
| Huawei | Settings > Security & Privacy > More > Trusted Credentials > User → Tap → Remove |
| iOS 15+ | Settings > General > VPN & Device Management → Select profile → Remove |
| iOS cũ | Settings > General > Profile & Device Management → Select → Remove |

### Q10: "Secure Connection Failed" / padlock with red strike?

Có thể cert hết hạn → kiểm tra:

Windows: `certmgr.msc` → tìm cert → mở → xem "Not valid after" date  
macOS: Keychain Access → Search → tìm cert → xem "Not valid after" date

Nếu hết hạn → Reset hoặc xóa cert.

**Giải pháp 1: Reset Certificate**
Charles > Help > SSL Proxying > "Reset Charles Root Certificate" > Reset > đóng + mở lại Charles > Reinstall cert trên máy + mobile

**Giải pháp 2: Remove Certificate**
Làm theo Q9 → Reinstall lại từ đầu.

> ⚠️ Sau giải pháp 1/2: khởi động lại Charles software + mobile browser.

### Q11: Không download được cert qua URL (mobile)?

1. Trên Charles máy tính: Help > SSL Proxying > Save Charles Root Certificate
2. Đổi file type từ `.pem` → `.cer` → lưu folder nhớ
3. Transfer `.cer` sang mobile (SD card, USB, email, Google Drive...)
4. Mở file trên mobile (iOS: download trên device, tap file)
5. Xác nhận PIN → Đặt tên cert → OK
6. Restart Charles → follow hướng dẫn từ Step 5 mobile course

### Q12: File log quá lớn, không upload lên report?

Clear traffic trước khi reproduce:
Charles > Broom icon > Reproduce bug > Stop Recording > Save session

### Q13: Không thấy pop-up/request "allow connection" trên Charles khi mở trang trên mobile?

- Kiểm tra WiFi connection option trên máy tính đặt "Public" (không Private)
- Restart cả 2 devices → mở website trên mobile sau khi connect proxy

### Q14: Không kết nối internet sau khi set proxy trên phone?

Thêm IP phone vào Access Control Settings của Charles:
Proxy > Access Control Settings > Add → Nhập IP local phone (trong Wi-Fi settings) > OK

### Q15: Lỗi certificate security trên Windows 11 bản mới nhất?

1. Mở Charles > đảm bảo Windows Proxy enabled (Proxy >> Windows Proxy)
2. Vẫn mở Charles > Truy cập `http://chls.pro/ssl` → download cert
3. Browser cảnh báo → Proceed anyway
4. Mở Windows Certificate Manager: Win+R → `certmgr.msc` > Enter
5. Right-click Trusted Root Certification Authorities > All Tasks > Import…
6. Next > Browse locate cert downloaded > Next > Next > Finish
7. Yes Security Warning > OK success confirmation
8. Restart máy (bắt buộc!)
9. Tiếp tục SSL Proxy settings trong Charles

### Q16: Traffic irrelevant từ PC hiển thị khi lấy logs mobile hoặc ngược lại?

| Cần capture traffic từ | Bật setting này trong Charles |
|----------------------|------------------------------|
| Chrome, Edge desktop | Proxy > Windows Proxy |
| Safari macOS | Proxy > macOS Proxy |
| Mobile device only | 1. Set proxy manual trên mobile (Wi-Fi settings) <br> 2. Trong Charles: disable Windows/macOS Proxy |
