# Thời gian tự động Vinaphone

- Đồng bộ hóa thời gian trong OpenWrt bằng cách lấy dữ liệu thời gian từ miền đã chọn.

- Hỗ trợ đồng bộ thời gian khi có kết nối modem/internet.

- Trình kiểm tra kết nối (nếu sử dụng chế độ cron, tập lệnh sẽ kiểm tra kết nối, sau đó khởi động lại ứng dụng VPN nếu không có kết nối internet)

- Cài đặt múi giờ tự động tuân theo LuCI - System - System - Timezone.

- Hỗ trợ cài đặt múi giờ cho VPN: OpenClash ,Passwall, ShadowsocksR, ShadowsocksR++, V2ray, V2rayA, Xray, Libernet, Xderm Mini, Wegare STL

Sử dụng mặc định - Sử dụng cơ bản

Cài đặt các gói yêu cầu trước bằng cách mở terminal:
```
opkg update && opkg install curl wget
```

Dán lệnh bên dưới để cài đặt tập lệnh vinaphone

Dùng wget:
```
wget --no-check-certificate "https://raw.githubusercontent.com/vankhanh2001/vinaphone/main/vinaphone" -O /usr/bin/vinaphone && chmod +x /usr/bin/vinaphone
```

dùng curl:
```
curl -sL https://raw.githubusercontent.com/vankhanh2001/vinaphone/main/vinaphone > /usr/bin/vinaphone && chmod +x /usr/bin/vinaphone
```

Nhập lệnh bên dưới vào LuCI -> System -> Startup -> Local Startup hoặc tại rc.local nếu ở trong terminal

Ví dụ dùng mạng Viettel:
```
/usr/bin/vinaphone vinaphone.com.vn
```
Nếu sử dụng crontab (kiểm tra kết nối cứ sau 1 giờ, sau đó khởi động lại vpn nếu không có kết nối), sao chép lệnh bên dưới vào LuCI -> System -> Schedule Tasks Ví dụ:
```
0 * * * * /usr/bin/vinaphone vinaphone.com.vn cron
```
Lệnh trên cũng có thể được bao gồm trong tệp/etc/crontabs/root

Đối với các tùy chỉnh thời gian định kỳ khác, hãy xem crontab.guru

Để update tập lệnh hãy thực hiện lệnh bên dưới:
```
/usr/bin/vinaphone update
```
Cập nhật thành công ta được như sau:

time: Update tệp lệnh...

time: Đang tải tệp lệnh...

time: update thành công.

time: Đã xóa tệp update!

Cách dùng: Thêm tên miền sau tệp lệnh!.

time: Thiếu tên miền/URL!.
