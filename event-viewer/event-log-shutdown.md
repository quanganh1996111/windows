# Kiểm tra nhật ký Máy chủ Windows bị shutdown

Trong quá trình quản trị Windows Server, có thể chúng ta sẽ gặp hiện tượng Máy chủ đột nhiên bị Shutdown hoặc bị Restart. Để biết được chính xác nguyên nhân do đâu ta có thể kiểm tra quá trình Shutdown hoặc Restart thông qua **Event Viewer**.

**Event Viewer** là một tính năng của Windows Server nói riêng và Hệ điều hành Windows nói chung. **Event Viewer** ghi lại toàn bộ nhật ký về các hoạt động diễn ra trong Hệ điều Windows mà ta sử dụng.

Một số Event ID được kết nối đến việc Shutdown và Restart lại Máy chủ:

- Event ID 1074: Chỉ ra rằng quá trình tắt được bắt đầu bởi một ứng dụng hoặc một User nào đó. Ví dụ, nó có thể là Windows Update.

- Event ID 6006 : Sự kiện đóng sạch sẽ. Điều này có nghĩa là Windows 10 đã bị tắt một cách chính xác.

- Event ID 6008 : Cho biết tắt máy đột ngột,không đúng cách. Xuất hiện trong nhật ký khi bạn tắt máy trước đó là bất ngờ, ví dụ như: do mất điện, ...

## 1. Cách mở Event Viewer

- Để mở **Event Viewer** đối với tất cả các HĐH Windows (Windows 10, Windows Server 2012, 2016,...) ta ấn tổ hợp phím `Windows + R` để truy cập vào Hộp thoại `Run`. Sau đó ta gõ `eventvwr.msc`:

<img src="https://imgur.com/LeyeV5X.png">

- Đối với các Hệ điều hành Windows Server, ta có thể bật **Event Viewer** từ **Server Manager**.

<img src="https://imgur.com/DrbXQAL.png">

## 2. Kiểm tra Event Viewer xem nguyên nhân bị Shutdown hoặc Restart.

- Cửa sổ **Event Viewer** khi mở lên:

<img src="https://imgur.com/HUm23mT.png">

- Để kiểm tra nguyên nhân bị Shutdown hoặc Restart, ta vào theo đường dẫn `Event Viewer (Local) -> Windows Logs -> Setup`

<img src="https://imgur.com/jnFCyR9.png">

- Tại đây sẽ hiện lên thông tin Logs của toàn bộ các Events về các thay đổi trong Windows. Để kiểm tra các Events về việc Shutdown hoặc Restart, ta phải lọc ra các Event ID liên quan đến các Events này. 

- Ta chọn `Filter Current Log`, một cửa số mới sẽ hiện ra, ta thêm vào các Event ID `1074, 6006, 6008` liên quan đến việc Shutdown hoặc Restart mà vừa được mô tả ở trên.

<img src="https://imgur.com/tMAoxMf.png">

<img src="https://imgur.com/Kbz7VP1.png">

- Sau khi lọc xong các Event Logs, giờ cửa sổ của **Event Viewer** sẽ chỉ hiện các Events liên quan đến Event ID mà ta vừa lọc.

- Ngay bến dưới ô của các Event sẽ là việc mô tả chi tiết nguyên nhân Event đó xảy ra. Ta có thể kiểm tra nguyên nhân Hệ điều hành Windows tại sao bị Shutdown hoặc Restart.

<img src="https://imgur.com/mxGDwVM.png">

## Chúc các bạn thành công !

## Tài liệu tham khảo

https://winaero.com/blog/find-shutdown-log-windows-10/

https://news.cloud365.vn/event-viewer-log-ly-thuyet-cach-tim-nhat-ky-shutdown-trong-windows-10windows-server-20122016/