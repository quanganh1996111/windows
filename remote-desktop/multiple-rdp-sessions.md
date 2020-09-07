# Mở nhiều Sessions Remote Desktop

Mặc định Windows Server chỉ cho phép một phiên Remote Desktop. Nếu như ta cố gắng đăng nhặp Remote Desktop thì phiên đang sử dụng sẽ bị văng ra, có thể làm gián đoạn công việc đang được tiến hành.

Topic này sẽ hướng dẫn việc Bật/Tắt việc mở nhiều phiên làm việc cho Remote Desktop.

## 1. Cho phép nhiều phiên truy cập vào máy chủ qua Remote Desktop

#### Bước 1: Truy cập vào Local Group Policy

Sử dụng tổ hợp phím `Windows + R` để mở cửa sổ `Run` sau đó gõ `gpedit.msc`

<img src="https://imgur.com/FcWzams.png">

#### Bước 2: Truy cập đến phần quản lý Chính sách của Remote Desktop

Truy cập vào theo đường dẫn `Computer Configuration > Administrative Templates > Windows Components > Remote Desktop Services > Remote Desktop Session Host > Connections.`

Trong này sẽ có các chính sách trong việc quản lý Remote Desktop.

<img src="https://imgur.com/Xv3AFCg.png">

#### Bước 3: Thay đổi Chính sách

Phần `Restrict Remote Desktop Services user to a single Remote Desktop Services session` quản lý việc cho phép một hoặc nhiều phiên đăng nhập vào Remote Desktop. 

<img src="https://imgur.com/Y1JOXcO.png">

Ta Click đúp chuột vào để hiện lên cửa sổ cấu hình. Ta chọn `Disabled` để tắt tính năng chỉ có một Session Remote Desktop. Sau đó `Apply` và chọn `OK` để xác nhận thay đổi.

<img src="https://imgur.com/KTJG16a.png">

#### Bước 4: Thay đổi số lượng Sessions cho phép

Ta Click đúp vào `Limit number of connections` để thay đổi số lượng Sessions ta muốn.

<img src="https://imgur.com/gni4ikm.png">

Tại đây ta chọn `Enabled` và chỉnh sửa giá trị của `RD Maximum Connections allowed`:

<img src="https://imgur.com/nqFzYwX.png">

Giá trị của `RD Maximum Connections allowed` từ 1 - 999999, trong đó khi ta để giá trị là `999999` sẽ mặc định là không có giới hạn Sessions.

Sau đó ta `Apply` và `OK` để xác nhận thay đổi. Ta cần khởi động lại Windows Server để hoàn tất các thay đổi trên.

Kiểm tra lại đăng nhập. Cùng lúc đăng nhập qua Remote Desktop nhiều Sessions:

<img src="https://imgur.com/zYtRGXu.png">

## 2. Chỉ cho phép một phiên đăng nhập máy chủ qua Remote Desktop

Ngược lại với việc cho phép kết nối nhiều phiên đăng nhập qua Remote Desktop. Ta chỉ cần truy cập vào đường dẫn `Computer Configuration > Administrative Templates > Windows Components > Remote Desktop Services > Remote Desktop Session Host > Connections.`

Ta cấu hình `Restrict Remote Desktop Services user to a single Remote Desktop Services session` sang `Enabled` sau đó khởi động lại Windows Server là hoàn thành.

## Chúc các bạn thành công !

## Tài liệu tham khảo

https://support.managed.com/kb/a1816/how-to-enable-disable-multiple-rdp-sessions-in-windows-2012.aspx