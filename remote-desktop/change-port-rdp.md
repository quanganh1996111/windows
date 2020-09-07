# Đổi port quản trị Remote Desktop

Với port mặc định của Remote Desktop là 3389, để tăng cường việc bảo mật cho việc truy cập qua Remote Desktop, ta nên thay đổi port cho Remote Desktop.

Các bước thực hiện:

- Nhấn tổ hợp phím `Windows + R` để mở cửa sổ **Run**.

- Ta gõ `regedit` và nhấn `Enter` để mở cửa sổ **Registry Editor**

- Ta tìm đến đường dẫn `KEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TerminalServer\WinStations\RDP-Tcp\PortNumber`

<img src="https://imgur.com/tiYuAaL.png">

- Chuyển sang định dang `Decimal` để hiện giá trị theo số. Tại ô `Value data:` ta thay đổi thành giá trị port mà ta muốn.

<img src="https://imgur.com/dxCU5Lf.png">

- Sau đó chọn `OK` để lưu lại các thay đổi và khởi động lại máy.

**Lưu ý:** Ta cần phải để giá port tránh xung đột với các phần mềm được cài đặt khác (Ví dụ: port 80 cho HTTP, 443 cho port HTTPS, 3306 cho các phần mềm SQL) và mở kết nối qua Firewall.

Kiểm tra lại truy cập qua Remote Desktop. Để truy cập qua port đã đổi, ta cần phải truy cập theo cú pháp:

`<hostname>:<port>` hoặc `<địa chỉ IP>:<port>`

<img src="https://imgur.com/skQxOgO.png">

Truy cập thành công qua port `2234` ta vừa thiết lập:

<img src="https://imgur.com/1RIThVE.png">

## Chúc các bạn thành công