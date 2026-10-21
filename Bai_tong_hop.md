# BÀI LÀM IT101: TỔ CHỨC HỆ THỐNG FILE VÀ XỬ LÝ SỰ CỐ TRƯỚC KHI NỘP BÀI

## Phần 1. Kiến trúc hệ điều hành

### 1.1. Chức năng cốt lõi của hệ điều hành

Đây là chức năng quản lý tiến trình và quản lý tài nguyên của hệ điều hành.

- Word, Chrome, VS Code và Portal là các chương trình đang hoạt động, thường được hệ điều hành quản lý dưới dạng các tiến trình.
- Hệ điều hành phân chia thời gian CPU, quản lý RAM và điều phối việc truy cập các thiết bị.
- Với máy có RAM 8 GB, hệ điều hành quản lý lượng bộ nhớ mà từng tiến trình sử dụng. Nếu thiếu RAM, Windows có thể sử dụng bộ nhớ ảo trên ổ đĩa, nhưng tốc độ thường chậm hơn RAM.

Bốn phần mềm có thể chạy cùng lúc vì hệ điều hành điều phối tài nguyên, cô lập không gian bộ nhớ của các tiến trình và quản lý quyền truy cập. Tuy nhiên, chúng vẫn có thể chậm hoặc xung đột nếu thiếu tài nguyên hay có lỗi phần mềm.

### 1.2. Khi double-click vào file báo cáo

Trong thao tác thông thường trên Windows, Shell là lớp người dùng tương tác trước.

- Shell: cung cấp giao diện File Explorer, nhận thao tác double-click và yêu cầu mở file bằng ứng dụng phù hợp, chẳng hạn Microsoft Word.
- Kernel: quản lý tài nguyên cốt lõi, bộ nhớ, tiến trình, thiết bị và các thao tác hệ thống cần thiết để ứng dụng hoạt động.

Người dùng thường tương tác qua Shell vì giao diện này dễ sử dụng hơn. Kernel hoạt động ở mức đặc quyền cao, nên ứng dụng và người dùng thông thường không trực tiếp điều khiển nó bằng thao tác hằng ngày.

## Phần 2. Cây thư mục và ổ đĩa

### 2.1. Phân tích cây thư mục hiện tại

Đường dẫn được cung cấp:

`D:\Nam1\HocKy1\MonHoc\CongNgheThongTin\BaiTapLon\Session02\BaoCaoCuoiKy\Chuong1\Hinh anh\anh 1.jpg`

- Root Directory: `D:\`
- Parent Directory trực tiếp của `anh 1.jpg`: `D:\Nam1\HocKy1\MonHoc\CongNgheThongTin\BaiTapLon\Session02\BaoCaoCuoiKy\Chuong1\Hinh anh`
- Vai trò của `anh 1.jpg`: là lá trong mô hình cây thư mục vì đây là file, không phải thư mục chứa các mục con.

### 2.2. Vì sao không nên lưu toàn bộ dự án trong Desktop hoặc Downloads?

Có hai lý do kỹ thuật chính:

1. Khó quản lý và dễ thất lạc: Downloads là nơi chứa file tải về tạm thời, còn Desktop thường có nhiều tệp rời. Khi cần nộp bài gấp, việc tìm đúng phiên bản sẽ khó hơn.
2. Rủi ro khi xử lý sự cố hệ điều hành: Desktop và Downloads thường nằm trong User Profile trên ổ C. Nếu Windows cần cài lại hoặc phân vùng hệ thống gặp sự cố, dữ liệu tại đây có thể bị mất nếu không được sao lưu.

Nơi lưu đề xuất: lưu dự án trên ổ `D:\02_Projects\BaiTapLonIT101\` nếu ổ D có sẵn và đủ dung lượng. Đồng thời sao lưu một bản độc lập ra thiết bị hoặc dịch vụ lưu trữ khác.

Lưu ý: ổ D không mặc nhiên an toàn hơn ổ C. Nếu C và D cùng thuộc một ổ cứng vật lý, chúng vẫn có thể cùng bị ảnh hưởng khi ổ cứng hỏng hoặc mã độc tác động lên cả hai phân vùng.

## Phần 3. Đường dẫn Path

### 3.1. Absolute Path của file `anh 1.jpg`

Đường dẫn tuyệt đối đầy đủ là:

```
D:\Nam1\HocKy1\MonHoc\CongNgheThongTin\BaiTapLon\Session02\BaoCaoCuoiKy\Chuong1\Hinh anh\anh 1.jpg
```

Giải thích: Absolute Path bắt đầu từ gốc ổ đĩa `D:\` và chỉ rõ toàn bộ đường dẫn đến file, nên không phụ thuộc vào thư mục làm việc hiện tại.

### 3.2. Relative Path để chèn `logo.png` vào `report.html`

Cấu trúc dự án:

```
BaiTapLonIT101/
├── report.html
├── pages/
│   └── appendix.html
└── assets/
    └── logo.png
```

Relative Path từ `report.html` đến `logo.png` là:

```
assets/logo.png
```

Ví dụ chèn ảnh trong HTML:

```
<img src="assets/logo.png" alt="Logo dự án">
```

Cũng có thể viết `./assets/logo.png`, trong đó `.` biểu thị thư mục hiện tại.

Lợi ích: Khi nén toàn bộ thư mục `BaiTapLonIT101` và gửi cho giảng viên, đường dẫn tương đối vẫn hoạt động nếu giữ nguyên cấu trúc thư mục. Ngược lại, đường dẫn tuyệt đối phụ thuộc vị trí lưu trên máy ban đầu và có thể không tồn tại trên máy giảng viên.

## Phần 4. Quy tắc đặt tên chuẩn

Tên file ban đầu:

`Báo cáo bài tập lớn IT101 (bản cuối) v2.docx`

Tên file theo kebab-case:

```
bao-cao-bai-tap-lon-it101-ban-cuoi-v2.docx
```

Giải thích:

- Viết thường toàn bộ tên.
- Các từ được ngăn cách bằng dấu gạch ngang `-`.
- Bỏ dấu tiếng Việt và loại bỏ dấu ngoặc không cần thiết.
- Giữ phần mở rộng `.docx` để nhận biết định dạng file.

## Phần 5. Tổ chức và dọn dẹp ổ đĩa

### 5.1. Đếm số cấp thư mục hiện tại

Đường dẫn ban đầu có 9 cấp thư mục, không tính ổ đĩa và file:

`Nam1 → HocKy1 → MonHoc → CongNgheThongTin → BaiTapLon → Session02 → BaoCaoCuoiKy → Chuong1 → Hinh anh`

Cấu trúc này vi phạm Quy tắc 3 Cấp Thư Mục, vì có quá nhiều cấp lồng nhau, khiến đường dẫn dài và khó tìm kiếm.

### 5.2. Thiết kế lại theo 4 trụ cột và 3 cấp

Vì `anh 1.jpg` là hình ảnh phục vụ bài tập lớn IT101, có thể lưu theo cấu trúc:

```
D:\
└── 04_Media/                 (Cấp 1: Trụ cột)
    └── it101/                (Cấp 2: Môn học)
        └── images/           (Cấp 3: Nhóm nội dung)
            └── anh-1.jpg     (File)
```

Đường dẫn mới:

```
D:\04_Media\it101\images\anh-1.jpg
```

Cách đặt này tuân thủ quy tắc 3 cấp: cấp 1 là trụ cột, cấp 2 là môn học hoặc dự án, cấp 3 là nhóm nội dung. File nằm trong cấp 3.

Bốn trụ cột được tổ chức như sau:

| Trụ cột       | Mục đích                                     |
| ------------- | -------------------------------------------- |
| `01_HocTap`   | Bài giảng, ghi chú và bài tập môn học        |
| `02_Projects` | Mã nguồn và tài liệu dự án                   |
| `03_Personal` | Tài liệu cá nhân                             |
| `04_Media`    | Hình ảnh, video và tài nguyên đa phương tiện |

Trong tình huống còn 30 phút, nên ưu tiên đổi tên file báo cáo, kiểm tra nội dung, lưu đúng vị trí và nộp bài trước. Việc dọn dẹp toàn bộ file cũ có thể thực hiện sau khi đã xác nhận nộp bài thành công.

## Phần 6. Đuôi file và file ẩn

### 6.1. Cạm bẫy có thể xảy ra

File đang hiển thị:

```
de-thi-dap-an.pdf
```

Do Windows đang ẩn phần mở rộng của các loại file đã biết, tên thật có thể là:

```
de-thi-dap-an.pdf.exe
```

Trong trường hợp này, `.pdf` chỉ là phần nằm trong tên file, còn `.exe` mới là phần mở rộng thực sự. Đây có thể là một file thực thi giả dạng tài liệu PDF để dụ người dùng mở file.

Không thể kết luận file chắc chắn là mã độc chỉ từ tên, nhưng vì file được tải từ đường link lạ trên Zalo nên cần xem là đáng ngờ và không được mở thử.

### 6.2. Cách kiểm tra trong Windows File Explorer

1. Nhấn Windows + E để mở File Explorer.
2. Chọn tab View.
3. Đánh dấu File name extensions để hiện phần mở rộng thật của file.
4. Quan sát lại tên file, nhưng không nhấp đôi để mở file đáng ngờ.

Sau khi bật tùy chọn này, file có thể hiện thành `de-thi-dap-an.pdf.exe`. Nếu đúng như vậy, phần mở rộng thực tế là `.exe`, không phải `.pdf`.

Cách xử lý an toàn: Không mở file, không cho phép chạy và không tải thêm nội dung từ liên kết đó. Báo nhân viên phòng Lab hoặc người phụ trách kỹ thuật để kiểm tra bằng công cụ bảo mật. Nếu đã mở file hoặc chạy chương trình, hãy ngắt kết nối mạng và báo ngay cho người phụ trách để xử lý sự cố.

## Kết luận

Bài tập cho thấy việc tổ chức hệ thống file không chỉ là sắp xếp thư mục mà còn liên quan đến quản lý tài nguyên của hệ điều hành, tính di động của đường dẫn, quy chuẩn đặt tên và an toàn thông tin. Áp dụng cấu trúc 3 cấp, 4 trụ cột, Relative Path và hiển thị đuôi file giúp sinh viên tìm dữ liệu nhanh hơn, giảm lỗi khi chuyển dự án sang máy khác và nhận diện các file có dấu hiệu đáng ngờ trước khi mở.