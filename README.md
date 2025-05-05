# Week1_NhanHoa
[Nội dung tìm hiểu trong 7 ngày]https://docs.google.com/spreadsheets/d/1iC78JEq1cWD1TDFqY9dPF4lb9XruDijOywf8AmDAmpg/edit?gid=0#gid=0
## Tìm hiểu về github ##
- Tạo repository trên github  
- Syntax của github  
## Tìm hiểu về markdown ##
- Syntax của markdown

## Tìm hiểu về phần mềm SSH ##
- Cài đặt putty
- Cách sử dụng putty
## Tìm hiểu về DNS ##
- DNS: là hệ thống phân giải tên miền.DNS đóng vai trò như một "biên dịch viên" giữa domain và địa chỉ IP
### Cách hoạt động của DNS ###
- Khi người dùng muốn tải một trang web, một bản dịch phải xảy ra giữa những gì người dùng nhập vào trình duyệt web của họ (example.com) và địa chỉ thân thiện với máy cần thiết để định vị trang web example.com.  
- Nếu máy chủ DNS cục bộ không có địa chỉ IP của website, nó sẽ hỏi máy chủ DNS gốc. Máy chủ DNS gốc sẽ trả về địa chỉ IP của máy chủ DNS cấp cao nhất cho website.  
- Máy chủ DNS cấp cao nhất sẽ trả về địa chỉ IP của máy chủ DNS quản lý website. Máy chủ DNS quản lý sẽ trả về địa chỉ IP của trang web cho máy chủ DNS cục bộ.  
- Cuối cùng, máy chủ DNS cục bộ sẽ trả về địa chỉ IP của trang web cho máy tính của người dùng. Máy tính của người dùng sẽ sử dụng địa chỉ IP này để kết nối với website.  
### Cấu trúc hệ thống DNS ###  

- Root DNS server: Máy chủ gốc , phân giải cấp cao nhất  
- Top-Level Domain(TLD) server: máy chủ miến cao cấp như .com, .vn, .org
- Authorative DNS server: Máy chủ có thẩm quyền - chứa thông tin chính xác nhất về tên miền (thường do nhà cung cấp tên miền hoặc chủ website quản lý)
- Recursive DNS server: Máy chủ đệ quy -trung gian đi hỏi các máy chủ khác để trả lời cho người dùng (VNPT, Viettel...)

### Các bản ghi của DNS ###  
- CNAME record: là bản ghi tên tiêu chuẩn. Đây là một dạng bản ghi tài nguyên trong hệ thống tên miền
- A record: dùng để trỏ tên miền website đến địa chỉ ip cụ thế
- MX record:Bản ghi này bạn có thể sử dụng để trỏ tên miền đến mail server. MX Record chỉ định server nào quản lý các dịch vụ Email của tên miền đó.
- AAAA record: Dùng để trỏ tên miền đến địa chỉ IPv6 và cho phép thêm host mới, TTL và IPv6.
- TXT record: Ngoài ra, có thể thêm giá trị TXT, Host mới, TTL và Point To để chứa các thông tin định dạng văn bản domain.
- SRV record: Đây là bản ghi DNS đặc biệt, dùng để xác định chính xác dịch vụ nào đang chạy Port nào. Và thông qua bản ghi này bạn có thể thêm Priority, Port, Weight, TTL, Point to Point.
- NS record: Bản ghi này có thể chỉ định Name Server cho từng tên miền phụ và bên cạnh đó có thể tạo tên Name Server, TTL hay host mới.

### Các loại DNS server ###
- Rootname server
- Localname server




