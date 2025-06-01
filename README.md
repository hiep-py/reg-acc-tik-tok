# TikTok Account Registration Tool v2.19

**Tác giả**: Hồ Hiệp x HVHTOOL  
**Mô tả**: Công cụ đăng ký tài khoản TikTok tự động bằng Selenium, hỗ trợ proxy và đa luồng.  
**Phiên bản**: 2.19 – Cải tiến logic xác nhận đăng ký từ `loginfb copy 2.py`.

---

## ✅ Tính năng chính

- Đăng ký tài khoản TikTok tự động bằng trình duyệt thật (Chrome)    
- Hỗ trợ proxy (dạng `ip:port`, không xác thực)
- Hỗ trợ đa luồng (multithread)
- Ghi log chi tiết, lưu tài khoản đã tạo
- Tự động kiểm tra và đánh dấu proxy lỗi
- Tự tạo các file cần thiết nếu chưa có

---

## 📦 Cấu trúc thư mục

```
/
├── regtiktok_multithread.py     # File script chính
├── chrome-win64/                # Thư mục chứa trình duyệt Chrome portable
│   └── chrome.exe
├── data/
│   ├── proxy.txt                # Danh sách proxy
│   ├── domain_names.txt         # Tiền tố tên email
│   ├── passwords.txt            # Danh sách mật khẩu email
│   └── useragents-desktop.txt   # Danh sách User-Agent
├── logs/
│   ├── regtiktok.log            # Log chính
│   └── proxy_log.txt            # Thống kê proxy
└── accounts.txt                 # Lưu thông tin tài khoản TikTok đã tạo
```

---

## ⚙️ Cài đặt

1. **Cài đặt Python:**  
   Yêu cầu Python 3.8 trở lên.  
   Tải từ: https://www.python.org/downloads/

2. **Cài thư viện cần thiết:**
   ```bash
   pip install -r requirements.txt
   ```
   Nếu chưa có `requirements.txt`, bạn có thể tự cài:
   ```bash
   pip install selenium requests
   ```

3. **Tải trình duyệt Chrome portable:**  
   - Đặt `chrome.exe` vào thư mục `chrome-win64` ngang hàng với file script.

---

## 🛠️ Cấu hình dữ liệu

- **proxy.txt:** danh sách proxy dạng `ip:port`, mỗi dòng một proxy.
- **domain_names.txt:** tiền tố email tạm (ví dụ: `mailtest`, `emailgen`, ...)
- **passwords.txt:** danh sách mật khẩu để dùng cho email tạm.
- **useragents-desktop.txt:** danh sách User-Agent giả lập trình duyệt.

Khi chạy lần đầu, các file trên sẽ được tự động tạo nếu chưa có.

---

## ▶️ Cách sử dụng

Chạy file chính:

```bash
python regtiktok_multithread.py
```

Sau đó nhập:

- Số **luồng**: số trình duyệt chạy song song
- Số **tài khoản**: số lượng tài khoản cần tạo

> ⚠️ Nếu không có proxy, tool sẽ tự động chuyển sang chế độ **không dùng proxy**.

---

## 📋 Kết quả

- Tài khoản thành công được lưu tại `accounts.txt` dạng:
  ```
  email|email_pass|tiktok_pass|Worker-ID|Thời gian
  ```
- Proxy lỗi sẽ được đánh dấu trong `data/proxy.txt`
- Thống kê proxy thành công/thất bại nằm ở `logs/proxy_log.txt`
- Log chi tiết toàn bộ quá trình tại `logs/regtiktok.log`

---

## ❗ Lưu ý

- Không hỗ trợ proxy có xác thực
- Cần kết nối Internet ổn định
- API của mail.tm đôi lúc có thể bị rate limit
- Nếu CAPTCHA xuất hiện, tool sẽ chờ `600s` rồi tiếp tục

---

## 👨‍💻 Liên hệ

> Tác giả: Hồ Hiệp  
> Tool hỗ trợ phát triển bởi: HVHTOOL  
> Phiên bản: 2.19 – Cập nhật logic đăng ký, xử lý lỗi tốt hơn

---