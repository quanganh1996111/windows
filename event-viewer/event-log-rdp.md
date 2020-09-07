# Kiểm tra truy cập Remote Desktop

Để kiểm tra việc truy cập qua Remote Desktop đến Máy chủ Hệ điều hành Windows, ta kiểm tra thông qua **Event Viewer** với các Event ID liên quan đến Remote Desktop.

Các trường hợp khi Remote Desktop tới máy chủ Windows có thể sảy ra như sau:

- Khi Remote Desktop đúng User đúng Password.

- Khi Remote Đúng User sai Password.

- Khi Remote sai User.

- Remote sai User hoặc Password.

## 1. Cách mở Event Viewer

- Để mở **Event Viewer** đối với tất cả các HĐH Windows (Windows 10, Windows Server 2012, 2016,...) ta ấn tổ hợp phím `Windows + R` để truy cập vào Hộp thoại `Run`. Sau đó ta gõ `eventvwr.msc`:

<img src="https://imgur.com/LeyeV5X.png">

- Đối với các Hệ điều hành Windows Server, ta có thể bật **Event Viewer** từ **Server Manager**.

<img src="https://imgur.com/DrbXQAL.png">

## 2. Kiểm tra Event Remote Desktop

### Trường hợp 1: Remote Desktop đúng User đúng Password (đăng nhập thành công)

#### Kiểm tra IP đã truy cập Remote Desktop

- Event ID `4648`: Để xem IP đã Remote Desktop.

- Event ID `4624`: Để xem các thông tin liên quan đến Remote Desktop.

Trong Event Viewer chọn `Windows Logs -> Security` ở cửa sổ bên trái. Sau đó ta chọn `Filter Current Log.`

<img src="https://imgur.com/m9h09o4.png">

Ta thêm bộ lọc Event ID `4648` sau đó chọn `OK`.

<img src="https://imgur.com/iFZCKJN.png">

<img src="https://imgur.com/EHBk0mB.png">

Tại đây ta Click đúp chuột vào một Event bất kỳ, cửa sổ ghi thông tin chi tiết về Event đó sẽ hiện lên, ta kéo xuống dưới sẽ thấy được địa chỉ IP vừa truy cập Remote Desktop vào Máy chủ Windows Server.

<img src="https://imgur.com/GmTUvGn.png">

#### Kiểm tra các thông tin khác về Remote Desktop

Trong Event Viewer chọn `Windows Logs -> Security` ở cửa sổ bên trái. Sau đó ta chọn `Filter Current Log.` với thêm bộ lọc Event ID `4624`.

<img src="https://imgur.com/Xfdw3B2.png">

Ta Click đúp chuột vào một Event bất kỳ ta sẽ thấy một số thông tin sau:

- Event ID: 4624

- Log Name: Security

- phần bản tin: An account was successfully logged on.

- logged: 12/24/2019 4:35:34 PM

- level: Infomation

- Computer: Tên máy tính được đăng nhập.

<img src="https://imgur.com/AzKl0xb.png">

### Trường hợp 2: Remote Desktop sai User hoặc Password (hoặc sai cả hai)

- Event ID `140`: Để xem IP đã Remote Desktop thất bại.

- Event ID `4625`: Để xem các thông tin liên quan khác