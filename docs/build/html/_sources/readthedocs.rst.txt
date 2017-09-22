Hướng dẫn sử dụng Git và Github cơ bản
==============================================
**26/08/2016\ `*KHÔNG CÓ PHẢN
HỒI* <https://lucngoc.com/hoc-tap/huong-dan-su-dung-git-va-github/#respond>`__**

Git và Github được sử dụng khá phổ biến trong giới lập trình viên, chắc
hẳn bạn sẽ thấy nhiều đường kho mã nguồn có link từ Github.com. Nó rất
tiện lợi và an toàn, đáp ứng tốt các nhu cầu làm việc nhóm. Để sử dụng
Git và Github bạn cần có những kiến thức cơ bản dòng lệnh trên Linux (vì
cơ bản Git được xây dựng trên Linux).

|it|

GIT LÀ GÌ?

Git là một hệ thống quản lý phiên bản phân tán (Distributed Version
Control System – DVCS). Bạn có thể hình dung như thế này, có hai anh A
và anh B cùng làm việc chung một dự án, mỗi người code một phần, hàng
ngày họ dùng Git để đẩy (commit) phần việc đã hoàn thành của mình lên
một kho mã nguồn chung (repository), từ kho chung này, họ có thể tải về
phần làm việc của đối phương về máy tính cá nhân của mình để làm chung.
Hệ thống này lưu lại mỗi lần thay đổi thành những phiên bản khác nhau để
quản lý và tiện cho việc người dùng muốn khôi phục lại.

GITHUB LÀ GÌ?

Trong phần giới thiệu về Git, mình có nhắc đến các kho mã
nguồn repository, Github là một hệ thống máy chủ dành riêng để chứa các
kho này, các repository trên Github được gọi là remote repository. Như
vậy, bạn có thể thấy rất rõ ràng sự khác nhau Git là một mô hình hệ
thống còn Github là hệ thống máy chủ. Tất nhiên có nhiều dịch vụ giống
như Github, nhưng trong khuôn khổ bài viết này, chúng ta sẽ chỉ làm việc
với Github mà thôi.

Truy cập \ `**https://github.com/join** <https://github.com/join>`__ để
tạo tài khoản nếu bạn chưa có.

BẮT ĐẦU LÀM VIỆC

Trong bài viết này, mình xin hướng demo sử dụng Git và Github trên máy
tính chạy Windows 10. Để chuẩn bị làm việc bạn cầtải Git về máy và cài
đặt, link
tải \ `**https://git-scm.com/downloads** <https://git-scm.com/downloads>`__,
việc cài đặt không có gì lưu ý đặc biệt, bạn cứ để các tùy chọn mặc định
và tiền hành  cài đặt bình thường.

Cấu hình Git cơ bản sau khi cài đặt, mở Git Bash và gõ.

| $ git config –global user.name “your\_name”
| $ git config –global user.email “your\_email@youremail.com”

Nhớ thay tên và email của bạn vào nhé, Git sẽ sử dụng các thông tin này
khi bạn tham gia vào các dự án.

TẠO REPOSITORY REMOTE TRÊN GITHUB

Đăng nhập vào Github trên trình duyệt,  nhấn vào dấu + và
chọn \ **New repository**

|it-02|

Điền các thông tin cần thiết và nhấn \ **Create Repository** để tạo một
repository mới:

|it-03|

Bạn sẽ thu được link của remote repository vừa tạo, link này có
dạng \ **https://github.com/user-name/repository-name**, trong demo của
mình là https://github.com/lucngoc/Git.git.

TẠO LOCAL REPOSITORY

Chúng ta đã tạo ra một repository trên Github, nhưng phần lớn công việc
bạn đều làm trên máy tính của mình, do đó bạn cần phải tạo một local
repository và kết nối chúng lại với nhau.

Dùng Windows Explorer mở thư mục chứa dự án bạn đang code trên máy, nhấn
chuột trái vào vùng trống và chọn \ **Git Bash Here**.

Gõ lệnh \ **$ git init** để khởi tạo một repository trong thư mục đó
(init là viết tắt của initialize). Lúc này một thư mục Git đã được tạo
ra nhưng nó là thư mục ẩn nên bạn không thể nhìn thấy được.

| $ git init
| Initialized empty Git repository in /.git/

KẾT NỐI LOCAL REPOSITORY VÀ REMOTE REPOSITORY TRÊN GITHUB

Repository trên Github được coi là remote repository và để kết nối với
Local Repository bạn dùng lệnh:

$ git remote add origin https://github.com/user-name/repository-name.git

Để kiểm tra lại remote repository bạn đã add, gõ lệnh \ **$ git remote
-v**

| $ git remote -v
| origin https://github.com/lucngoc/Git.git (fetch)
| origin https://github.com/lucngoc/Git.git (push)

Trong dòng kết quả, \ **origin** là tên của remote repository được đặt
mặc định, bạn có thể đổi tên này bằng lệnh \ **$ git remote rename
origin new\_name**, việc này có ích nếu như bạn có nhiều remote
repository trong dự án.

ĐƯA FILE VÀO REPOSITORY

**Quy trình người dùng đưa tập tin vào Repository.**

|it-07|

**Giai đoạn 1:** Các tập tin trong dự án của bạn đã nằm trong thư mục
Local Repository mà bạn đã dùng lệnh \ **$ git init** để tạo ở trên. Tuy
nhiên chúng vẫn chưa được \ **track**, để đưa chúng vào trạng
thái \ **track** bạn dùng lệnh sử dụng lệnh \ **$ git add
file\_name** (sử dụng \ **$ git add \*** để đưa toàn bộ các file trong
thư mục), lúc này các file sẽ được \ **đặt trạng thái đã tracked** và
sẵn sàng \ **commit** (file nằm trong vùng file vào \ **staging
area** và sẵn sàng để commit). Dùng lệnh \ **$** **git status** để kiểm
tra trạng thái của các file.

Ví dụ mình có file cat.txt trong thư mục Local Repository:

| $ git add cat.txt
| $ git status
| On branch master
| Initial commit
| Changes to be committed:
| (use “git rm –cached <file>…” to unstage)
| new file: cat.txt

**Giai đoạn 2:** Commit có mục đích là chụp lại (snapshot) các file
trong staging area và sự thay đổi với phiên bản trước đó nếu có, thông
tin được lưu lại kèm theo tên email của người commit. Để commit ta sử
dụng lệnh \ **$ git commit -m “message”**. Message đi kèm lệnh commit
giúp người dùng có thể dễ dàng nhận biết các lần commit, bạn có thể đặt
sao cho dễ nhớ.

| $ git commit -m “Add cat.txt”
| [master 2a6786a] Add cat.txt
| 1 file changed, 0 insertions(+), 0 deletions(-)
| create mode 100644 cat.txt

Lưu ý:

-  Với file bạn đã dùng lệnh \ **$ git add** nhưng sau đó bạn sửa đổi
       nội dung của file, tập tin vẫn ở trang thái tracked nhưng sẽ được
       đưa về dạng modified và bạn không thể commit. Bạn phải sử dụng
       lệnh \ **$** **git add** một lần nữa. Tuy nhiên nếu không muốn
       dài dòng như vậy, bạn có thể dùng lệnh \ **$ git commit -a -m
       “message”** để commit luôn, bỏ qua trạng thái modified.

-  Để đưa một tập tin ra khỏi staging area bạn dùng lệnh \ **$ git reset
       HEAD tên-file**, để xóa file bạn dùng lệnh \ **$ rm
       file\_name** (chưa xóa hẳn khỏi ổ cứng), để xóa hẳn bạn dùng
       lệnh git \ **$ rm -f file\_name**.

-  Để xem lại chi tiết lịch sử các lần commit, bạn sử dụng
       lệnh \ **$ git log**.

**Đưa tập tin sau khi commit lên Remote Repository trên Github**

Bạn dùng lệnh \ **$ git push -u origin master **\ (để hiểu về master
chúng ta sẽ nghiên cứu khái niệm \ **branch **\ trong phần tiếp theo của
bài viết), toàn bộ các tập tin đã được commit sẽ được đưa lên Github.
Bạn có thể được yêu cầu đăng nhập vào tài khoản Github của mình. Tiền
tố \ **-u** giúp Git ghi nhớ lại các thông tin truyền vào để lần kế tiếp
bạn chỉ cần gõ \ **$ git push** là Git sẽ tự biết phải làm gì.

| $ git push -u origin master
| Counting objects: 3, done.
| Writing objects: 100% (3/3), 207 bytes \| 0 bytes/s, done.
| Total 3 (delta 0), reused 0 (delta 0)
| To https://github.com/lucngoc/Git.git
| \* [new branch] master -> master
| Branch master set up to track remote branch master from origin.

Đợi cho đến khi thông báo hoàn tất. Bạn có thể xem các file mình vừa đưa
lên trên Github.com.

LÀM VIỆC VỚI REMOTE REPOSITORY

Giả sử như team của bạn có nhiều người làm chung một dự án và cùng đẩy
dữ liệu lên Github. Khi có người push dữ liệu của họ lên và bạn muốn
kiểm tra và lấy về máy mình, dùng lệnh \ **$ git pull origin master**

| $ git pull origin master
| From https://github.com/lucngoc/Git
| \* branch master -> FETCH\_HEAD
| Already up-to-date.

Pull giúp lấy toàn bộ dữ liệu trên remote repository và gộp vào brand
hiện tại. Ngoài cách lấy dữ liệu với pull, ta còn có
lệnh \ **clone** và **fetch**.

-  Lệnh\ ** clone ($ git clone
       remote**\ \_\ **repository**)\ ** **\ giúp sao chép toàn bộ dữ
       liệu và các thiết lập trên remote repository và tự động tạo ra
       một master branch trên máy tính của bạn. Lệnh này chỉ nên sử dụng
       khi bạn cần tạo mới một local repository mới trên máy tính với
       toàn bộ dữ liệu và thiết lập của remote repository.

-  Lệnh \ **fetch **\ (**$ git fetch remote\_repository**) lấy toàn bộ
       dữ liệu từ remote repository nhưng sẽ cho phép bạn gộp thủ công
       vào một branch nào đó.

KỸ THUẬT PHÂN NHÁNH BRANCH

Ở phần trên chúng ta đã đã động đến master cùng khái niệm branch, và bay
giờ ta sẽ tìm hiểu về chúng.

|it-08|

Khi bạn tạo một repository, mặc định bạn sẽ có một branch tên
là \ **master**, kỹ thuật phân nhánh branch giúp tạo ra một hoặc nhiều
nhánh (branch) mới, mã nguồn từ \ **branch master**\ được clone sang
các \ **branch phụ** mới tạo ra, các thay đổi mã nguồn trên branch phụ
không làm thay đổi mã nguồn trên nhánh chính. Việc này rất có ích khi
bạn muốn phát triển thêm tính năng cho dự án, nếu tính năng đó gây xung
đột bạn có thể xóa nó đi mà không làm ảnh hưởng tớ cả dự án, nếu tính
năng đó OK, bạn có thể gộp chung vào dự án chính.

Để tạo ta một branch bạn dùng lệnh \ **$ git branch tên\_branch**, để
xem các branch hiện có bạn dùng lệnh \ **$ git branch. **\ Để bắt đầu
làm việc với một branch nào đó, bạn dùng lệnh \ **$ git checkout
tên\_branch**. Lúc này các lệnh add, commit, push… sẽ được thực hiện
trên branch được checkout và không ảnh hưởng tới các branch khác. Kết
thúc làm việc với một branch, để trở về branch chính, bạn lại sử dụng
lệnh checkout \ **$ git checkout master**, lúc này bạn muốn gộp các thay
đổi trên branch phụ vừa làm việc vào branch chính, bạn dùng
lệnh \ **$ git merge tên\_branch**.

Bạn có thể dễ hình dung hơn với vụ dụ dưới đây:

| $ git branch feature
| $ git branch
| feature
| \* master
| $ git checkout feature
| Switched to branch ‘feature’
| $ touch dog.txt
| $ git add dog.txt
| $ git commit -m “Add dog.txt”
| On branch feature
| nothing to commit, working tree clean
| $ git push -u origin feature
| Total 0 (delta 0), reused 0 (delta 0)
| To https://github.com/lucngoc/Git.git
| \* [new branch] feature -> feature
| Branch feature set up to track remote branch feature from origin.
| $ git checkout master
| Switched to branch ‘master’
| Your branch is up-to-date with ‘origin/master’.
| $ git merge feature
| Updating 6aeb630..6dc95bb
| Fast-forward
| dog.txt \| 0
| 1 file changed, 0 insertions(+), 0 deletions(-)
| create mode 100644 dog.txt
| $ git branch -d feature
| Deleted branch feature (was 6dc95bb)
| $ git push
| Total 0 (delta 0), reused 0 (delta 0)
| To https://github.com/lucngoc/Git.git
| 6aeb630..6dc95bb master -> master

Chúng ta đã đi đến phần cuối cùng trong bài viết này, đây là các kiến
thức cơ bản, có thể vẫn còn thiếu sót, để tìm hiểu đầy đủ bạn có thể
truy cập \ `***https://git-scm.com/doc*** <https://git-scm.com/doc>`__.
Chúc các bạn sử dụng thành thạo Git và Github.

.. |it| image:: media/image1.jpeg
   :width: 5.20694in
   :height: 2.27014in
.. |it-02| image:: media/image2.png
   :width: 6.57639in
   :height: 2.48780in
.. |it-03| image:: media/image3.png
   :width: 6.47898in
   :height: 5.20556in
.. |it-07| image:: media/image4.png
   :width: 6.21319in
   :height: 3.58853in
.. |it-08| image:: media/image5.png
   :width: 6.36597in
   :height: 1.59573in
