# ftp-client-in-c-linux

Các hàm chức năng chính
bool command_handler(int sock, char* cmd);
Mô tả: Hàm xử lý lệnh do người dùng nhập vào từ cmd (ls, put, get, exit, ....)
Input: Socket điều khiển, command nhận từ người dùng
Output: Kết quả thực hiện true/false

user (được viết trong hàm main)
Mô tả: Giao tiếp bước đầu để login vào server.
Input: User name và password người dùng nhập từ bàn phím.
Output: Sau khi request lên server, nếu thành công chương trình cho phép người dùng thao tác tiếp, nếu thất bại người dùng phải nhập lại username và password.

void parseCode(int command_code);
Mô tả: Phân tích code thành thông báo và xuất ra màn hình.
Input: mã số thông báo từ server.
Output: Xuất thông báo tương ứng với command_code truyền vào.

void pwd(int sockfd);
Mô tả: Request thư mục hiện hành lên server, nhận kết quả gán vào biến toàn cục cho biết current_dir và xuất ra màn hình.
Input: socket giao tiếp với server.
Output: biến toàn cục current_dir chứa đường dẫn thư mục đang làm việc tại remote ftp server.

int disconnect(int sockfd);
Mô tả: disconnect kết nối hiện tại với server nhưng ftp client vẫn hoạt động.
Input: socket điều khiển
Output: 0 nếu disconnect không thành công, 1 nếu disconnect thành công.

void bye(int sock);		//QUIT
Mô tả: disconnect kết nối hiện tại với server và tắt ftp client
Input: socket điều khiển.
Output: không.

//recv remote-file [local-file ]
int ftp_recv(int sock, char *arg1, char *arg2);	//RETR
Mô tả: hàm get file từ FTP server về máy
Input: Socket điều khiển, arg1 là file trên server, arg2 là tên file mới sẽ ghi xuống tại ftp client
Output: Return Code

//ls [remote-directory ] [local-file ]
int ls(int sock, char *arg1, char *arg2);		//LIST
Mô tả: xử lý lệnh ls với 2 tham số truyền vô (nếu có), nếu không có tham số nào thì sẽ list các tập tin/thư mục con trong thư mục hiện tại
Input: Socket điều khiển, arg1 là remote-diretory cần list, arg2 là local-file sẽ chép danh sách vừa list xuống.

int put(int sockfd, char filename[], char localPath[], int mode);
Mô tả: Send/put một file lên server.
Input: tên file, đường dẫn tại local host, mode hoạt động là active (mode = 0) hay passive (mode = 1).
Output: Gửi file lên server thành công trả về 1, không thành công trả về 0.

void cd (int sock_fd, char* s1)
Mô tả: hàm di chuyển tới thư mục
Input: Socket điều khiển, đường dẫn tới thư mục mong muốn
Output: Gửi lên server thành công và trả về dòng lệnh đã thực hiện  thành công từ server

void cdup (int sock_fd)
Mô tả: hàm di chuyển tới thư mục cha
Input: Socket điều khiển
Output: Gửi lên server thành công và trả về dòng lệnh đã thực hiện  thành công từ server

void MKDIR (int sock_fd, char* s1)
Mô tả: hàm tạo thu mục
Input: Socket điều khiển, dường dẫn
Output: Gửi lên server thành công và trả về dòng lệnh đã thực hiện  thành công từ server

void delete (int sock_fd, char* s1)
Mô tả: hàm xóa 1 file
Input: Socket điều khiển, đường dẫn
Output: Gửi lên server thành công và trả về dòng lệnh đã thực hiện  thành công từ server

void RMDIR (int sock_fd, char* s1)
Mô tả: hàm xóa thư mục
Input: Socket điều khiển, đường dẫn đến thư mục
Output: Gửi lên server thành công và trả về dòng lệnh đã thực hiện  thành công từ server

int Send_cmd (char* s1, char* s2, int sock_fd)
Mô tả: Gửi lệnh lên Server
Input: Socket điều khiển, s1 là lệnh, s2 là đường dẫn
Output: nếu giá trị trả về nhỏ hơn 0 thì gửi không thành công, ngược lại thì thành công

int Reply_cmd(int sock_fd)
Mô tả: Nhận Response từ Server
Input: Socket điều khiển
Output: trả về mã code

void Pasre (char s1[256], int sock_fd)
Mô tả: Phân tích lệnh được nhập từ người dùng
Input: chuỗi lệnh, Socket điều khiển
Output: Phân tích thành công

