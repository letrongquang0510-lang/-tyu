# Yêu cầu đầu ra
## Phần 1. Phân tích : Chỉ ra ít nhất 2 sai lầm trong tư duy của Nam về việc dùng file Rich Text cho lưu trữ mã nguồn. Giải thích tại sao Markdown lại an toàn và nhẹ hơn.
### 1. Hai sai lầm trong tư duy của Nam
-   Lầm tưởng Rich Text là Plain Text : File .docx thực chất là một tập tin nén ZIP chứa cấu trúc XML phức tạp. Khi sửa dù chỉ một dấu phẩy, toàn bộ cấu trúc file bị xáo trộn khiến Git coi đó là sự thay đổi toàn bộ nội dung, gây ra xung đột và không thể hỗ trợ Git Diff từng dòng.
-   Sai lầm về tính cộng tác & xem trước: File Word không hiển thị được trực tiếp trên giao diện trình duyệt của GitHub, làm mất tính trực quan và bắt buộc người khác phải tải về mới đọc được.
### 2. Tại sao Markdown an toàn và nhẹ hơn?
-   An toàn :
    -   Word (.docx) : Mất 1 byte dữ liệu ở cấu trúc nén ZIP sẽ làm hỏng toàn bộ file , phần mềm không thể mở được.   
    -   Markdown (.md) : Là văn bản thô (Plain Text), nếu mất hoặc lỗi 1 byte thì chỉ hỏng đúng 1 ký tự tại vị trí đó, toàn bộ phần còn lại vẫn đọc được bình thường.   
-   Dung lượng siêu nhẹ : Tệp .md chỉ lưu các ký tự chữ và ký hiệu định dạng thô , không mang theo mã định dạng cồng kềnh như Word , giúp tăng tốc độ đồng bộ và tiết kiệm băng thông khi push lên Git.
    
## Phần 2. Hoàn thiện : Sử dụng StackEdit để chuyển đổi đoạn giới thiệu từ Word sang Markdown (.md).
### Quy trình chuyển đổi trên StackEdit:
1.  Copy nội dung từ file Word (`Ctrl + A`,  `Ctrl + C`).
2.  Dán vào [StackEdit](https://stackedit.io/) và gắn các ký hiệu Markdown (`#`,  `*`,  `**`).  
3.  Chọn **Export to disk** để tải về file `README.md` và tải lên GitHub.

