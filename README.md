# Zing Account Generator

Tool tự động tạo tài khoản Zing ID hàng loạt với hỗ trợ đa luồng, proxy và giải CAPTCHA tự động.

---

## Yêu cầu

- Windows 10/11 64-bit
- Tài khoản [Capsolver](https://capsolver.com) (để giải reCAPTCHA)
- Máy tính đã được admin cấp phép (xem phần Kích hoạt)

---

## Cài đặt

1. Tải `ZingBot.exe` từ [Releases](https://github.com/truongair/zing-bot-data/releases/latest)
2. Đặt vào thư mục bất kỳ (ví dụ: `C:\ZingBot\`)
3. Chạy lần đầu để tạo file cấu hình

---

## Kích hoạt

Tool sử dụng xác thực theo máy tính. Mỗi máy cần được admin cấp phép riêng.

**Bước 1** — Chạy `ZingBot.exe`, tool sẽ hiển thị Machine ID của máy bạn:

```
[✗] machine not authorized

  Send your Machine ID to the admin to get access:
  Machine ID: 4ECFB67E0CCEB9FE834B811838AB0566A4D29EF53F74C502AA5554D6F85B3EF9
```

**Bước 2** — Gửi Machine ID đó cho admin để được cấp phép.

**Bước 3** — Sau khi admin xác nhận, chạy lại `ZingBot.exe`:

```
[✓] License valid!
```

---

## Cấu hình

Lần đầu chạy thành công, file `config.json` được tạo tự động. Mở file đó để chỉnh:

```json
{
  "capsolverkey": "CAP-...",
  "threads": 5,
  "accounts": 10,
  "prefixusername": "user_",
  "minusernamelength": 8,
  "maxusernamelength": 12,
  "useproxy": false,
  "proxytype": "http",
  "requesttimeout": 90,
  "retrycount": 2,
  "retrydelay": 1000,
  "verbose": false,
  "showstep": false
}
```

| Trường | Mô tả |
|--------|-------|
| `capsolverkey` | API key từ [capsolver.com](https://capsolver.com) — **bắt buộc** |
| `threads` | Số luồng chạy song song (khuyến nghị 1–10) |
| `accounts` | Số tài khoản muốn tạo mỗi lần chạy |
| `prefixusername` | Tiền tố username (ví dụ `user_` → `user_abc123`) |
| `minusernamelength` | Độ dài tối thiểu username |
| `maxusernamelength` | Độ dài tối đa username |
| `useproxy` | `true` để dùng proxy, `false` để dùng IP thật |
| `proxytype` | Loại proxy: `http`, `https`, `socks5`, `socks4` |
| `requesttimeout` | Timeout mỗi request (giây), mặc định 90 |
| `retrycount` | Số lần thử lại khi thất bại (mặc định 2) |
| `retrydelay` | Thời gian chờ giữa các lần retry (milliseconds) |
| `verbose` | `true` để bật log debug chi tiết |
| `showstep` | `true` để hiển thị từng bước đăng ký |

---

## Cài đặt Proxy (tuỳ chọn)

Tạo file `proxies.txt` cùng thư mục với `ZingBot.exe`, mỗi proxy một dòng:

```
192.168.1.1:8080
user:pass@192.168.1.2:8080
socks5://192.168.1.3:1080
http://user:pass@192.168.1.4:3128
```

Sau đó bật `"useproxy": true` trong `config.json`.

---

## Sử dụng

1. Chạy `ZingBot.exe`
2. Tool tự động kiểm tra update và license
3. Bot bắt đầu tạo tài khoản theo cấu hình
4. Kết quả được lưu vào `accounts.txt`:

```
username|password|UIN|2026-04-21 13:00:00
```

---

## Cập nhật

Tool tự động kiểm tra phiên bản mới mỗi lần chạy:

```
[!] New version available: 1.1.0
    What's new: Cải thiện tốc độ tạo tài khoản

Download and install update? (y/n):
```

Nhập `y` để tải và cài đặt tự động, sau đó mở lại tool.

---

## Lưu ý

- Không chia sẻ tool cho người khác — mỗi máy cần được cấp phép riêng
- Không chạy quá nhiều luồng cùng lúc để tránh bị chặn IP
- File `accounts.txt` chứa thông tin nhạy cảm, giữ bảo mật

---

## Liên hệ

Để được hỗ trợ hoặc cấp phép máy mới, liên hệ admin.
