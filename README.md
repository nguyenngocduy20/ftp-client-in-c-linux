# ftp-client-in-c-linux

## Các hàm chức năng chính<br>
<i><b>bool command_handler(int sock, char* cmd);</b></i><br>
Mô tả: Hàm xử lý lệnh do người dùng nhập vào từ cmd (ls, put, get, exit, ....)<br>
Input: Socket điều khiển, command nhận từ người dùng<br>
Output: Kết quả thực hiện true/false<br>
<br>
<i><b>user (được viết trong hàm main)</i></b><br>
Mô tả: Giao tiếp bước đầu để login vào server.<br>
Input: User name và password người dùng nhập từ bàn phím.<br>
Output: Sau khi request lên server, nếu thành công chương trình cho phép người dùng thao tác tiếp, nếu thất bại người dùng phải nhập lại username và password.<br>
<br>
<i><b>void parseCode(int command_code);</b></i><<br>
Mô tả: Phân tích code thành thông báo và xuất ra màn hình.<br>
Input: mã số thông báo từ server.<br>
Output: Xuất thông báo tương ứng với command_code truyền vào.<br>
<br>
<i><b>void pwd(int sockfd);</b></i><br>
Mô tả: Request thư mục hiện hành lên server, nhận kết quả gán vào biến toàn cục cho biết current_dir và xuất ra màn hình.<br>
Input: socket giao tiếp với server.<br>
Output: biến toàn cục current_dir chứa đường dẫn thư mục đang làm việc tại remote ftp server.<br>
<br>
<i><b>int disconnect(int sockfd);</b></i><br>
Mô tả: disconnect kết nối hiện tại với server nhưng ftp client vẫn hoạt động.<br>
Input: socket điều khiển<br>
Output: 0 nếu disconnect không thành công, 1 nếu disconnect thành công.<br>
<br>
<i><b>void bye(int sock);</b></i>		//QUIT<br>
Mô tả: disconnect kết nối hiện tại với server và tắt ftp client<br>
Input: socket điều khiển.<br>
Output: không.<br>
<br>
//recv remote-file [local-file ]<br>
<i><b>int ftp_recv(int sock, char *arg1, char *arg2);	</b></i>//RETR<br>
Mô tả: hàm get file từ FTP server về máy<br>
Input: Socket điều khiển, arg1 là file trên server, arg2 là tên file mới sẽ ghi xuống tại ftp client<br>
Output: Return Code<br>
<br>
//ls [remote-directory ] [local-file ]<br>
<i><b>int ls(int sock, char *arg1, char *arg2);		</b></i>//LIST<br>
Mô tả: xử lý lệnh ls với 2 tham số truyền vô (nếu có), nếu không có tham số nào thì sẽ list các tập tin/thư mục con trong thư mục hiện tại<br>
Input: Socket điều khiển, arg1 là remote-diretory cần list, arg2 là local-file sẽ chép danh sách vừa list xuống.<br>
<br>
<i><b>int put(int sockfd, char filename[], char localPath[], int mode);</b></i><br>
Mô tả: Send/put một file lên server.<br>
Input: tên file, đường dẫn tại local host, mode hoạt động là active (mode = 0) hay passive (mode = 1).<br>
Output: Gửi file lên server thành công trả về 1, không thành công trả về 0.<br>
<br>
<i><b>void cd (int sock_fd, char* s1)</b></i><br>
Mô tả: hàm di chuyển tới thư mục<br>
Input: Socket điều khiển, đường dẫn tới thư mục mong muốn<br>
Output: Gửi lên server thành công và trả về dòng lệnh đã thực hiện  thành công từ server<br>
<br>
<i><b>void cdup (int sock_fd)</b></i><br>
Mô tả: hàm di chuyển tới thư mục cha<br>
Input: Socket điều khiển<br>
Output: Gửi lên server thành công và trả về dòng lệnh đã thực hiện  thành công từ server<br>
<br>
<i><b>void MKDIR (int sock_fd, char* s1)</b></i><br>
Mô tả: hàm tạo thu mục<br>
Input: Socket điều khiển, dường dẫn<br>
Output: Gửi lên server thành công và trả về dòng lệnh đã thực hiện  thành công từ server<br>
<br>
<i><b>void delete (int sock_fd, char* s1)</b></i><br>
Mô tả: hàm xóa 1 file<br>
Input: Socket điều khiển, đường dẫn<br>
Output: Gửi lên server thành công và trả về dòng lệnh đã thực hiện  thành công từ server<br>
<br>
<i><b>void RMDIR (int sock_fd, char* s1)</b></i><br>
Mô tả: hàm xóa thư mục<br>
Input: Socket điều khiển, đường dẫn đến thư mục<br>
Output: Gửi lên server thành công và trả về dòng lệnh đã thực hiện  thành công từ server<br>
<br>
<i><b>int Send_cmd (char* s1, char* s2, int sock_fd)</b></i><br>
Mô tả: Gửi lệnh lên Server<br>
Input: Socket điều khiển, s1 là lệnh, s2 là đường dẫn<br>
Output: nếu giá trị trả về nhỏ hơn 0 thì gửi không thành công, ngược lại thì thành công<br>
<br>
<i><b>int Reply_cmd(int sock_fd)</b></i><br>
Mô tả: Nhận Response từ Server<br>
Input: Socket điều khiển<br>
Output: trả về mã code<br>
<br>
<i><b>void Pasre (char s1[256], int sock_fd)</b></i><br>
Mô tả: Phân tích lệnh được nhập từ người dùng<br>
Input: chuỗi lệnh, Socket điều khiển<br>
Output: Phân tích thành công<br>
<br>
