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

#### Để kiểm tra IP đã Remote Desktop thất bại tới Máy chủ Windows

Trong Event Viewer chọn `Applications and Services Logs > Microsoft > Windows > RemoteDesktopServices-RdpCoreTS > Operational` ở cửa sổ bên trái.

<img src="https://imgur.com/uIrGxpE.png">

Ở cửa sổ bên phải -> Nhấn chuột chọn trường `Filter Current Log`.

Ta thêm Event ID `140`:

<img src="https://imgur.com/suZ8Ruy.png">

Bây giờ, Trình xem sự kiện (Event Viewer ) sẽ chỉ hiển thị các sự kiện liên quan đến Remote Desktop thất bại:

<img src="https://imgur.com/9vs4lm6.png">

<img src="https://imgur.com/KE8AQm2.png">

Trong đó:

- Event ID: 140

- Log Name: Microsoft-Windows-RemoteDesktopServices-RdpCoreTS/Operational

- phần bản tin: A connection from the client computer with an IP address of 192.168.182.1 failed because the user name or password is not correct.

- logged: 12/24/2019 5:02:36 PM

- level: Warning

- Computer: Tên máy tính được đăng nhập

#### Tìm tên User được nhập lúc Remote Desktop thất bại tới máy Chủ Windows Server

Trong Event Viewer chọn `Windows Logs -> Security` ở cửa sổ bên trái

Ở cửa sổ bên phải -> Nhấn chuột chọn trường `Filter Current Log`.

Trong hộp thoại tiếp theo, nhập Event ID `4625`

<img src="https://imgur.com/SLImOVE.png">

Ta Click đúp vào một Event bất kỳ để theo dõi chi tiết Event đó:

<img src="https://imgur.com/DhUenQu.png">

Trong đó: 

- Event ID: là ID sự kiện

- Log Name: Tên bản tin log

- Account Name: Tên user

- phần bản tin: là bản tin log

- logged: thời gian xuất hiện sự kiện

- level: mức độ cảnh báo

- Computer: Tên máy tính được đăng nhập

- Chú ý: Có thêm phần Account Name

## Kết luận

Như vậy trong bài viết này chúng ta đã cùng nhau tìm hiểu và cách thức sử dụng công cụ Event Viewer để tìm nhật ký Remote Desktop đối với những lần Remote thất bại , Remote Sai User hoặc password trong Windows, quan trọng hơn là cách tìm địa chỉ ip đã đăng nhập sai để tiến hành khoanh vùng thực hiện các biện pháp xử lý.

## Tài liệu tham khảo

https://news.cloud365.vn/huong-dan-kiem-tra-log-remote-desktop-tren-windows/