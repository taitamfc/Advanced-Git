### Ôn tập git:
#### Các lệnh git cơ bản
1. git clone <repository>
- Clone Remote reposity <reposity>
2. git remote –v 
- Xem thông tin Remote reposity hiện t
3. git remote show <name>
- Xem thông tin <name> hiện tại
4. git remote add <name> <repository>
- Add một Local Repository lên Remote Repository tại <repository> và đặt tên nó là <name>
5. git remote rename <name1> <name2>
- Đổi tên <name1> thành <name2>
6. git remote remove <name>
- Xóa remote <name>
7. git pull <name> <branch> 
- Kiểm tra sự thay đổi trên Remote Repository và merge vào phiên làm việc hiện tại
8. git push <name> <branch>
- Đẩy dữ liệu lên remote repository

#### Làm việc với nhánh
1. Xem danh sách nhánh
- git branch
- nhánh nào có dấu * là nhánh chúng ta đang làm việc
2. Tạo nhánh task-login
- git branch task-login
- git branch
3. Chuyển nhánh làm việc
- git checkout task-login
- Trước khi chuyển nhánh phải đảm bảo nhánh làm việc phải “nothing to commit, working tree clean”
4. Demo làm việc trên nhánh
- git branch
- git checkout task-login
- tạo file login.html và commit trên nhánh task-login
- Chuyển nhánh master và xem file login.html có tồn tại hay không?
- git branch -v xem commit mới nhất ở mỗi nhánh
5. Mẹo
- git checkout -b <branchname> tạo branchname và chuyển đến branchname
6. Merge nhánh
- git merge <branchname>
7. Đổi tên nhánh
- git branch -m <oldname> <newname>
8. xóa nhánh <branchname> và nhánh này đã được merge
- git branch -d <branchname> 
9. xóa nhánh <branchname> và nhánh này chưa được merge
- git branch -D <branchname>


### Git flow
1. Main ( Nhánh chính )
- Master branchs có sẵn trong git và là branchs chứa mã nguồn khởi tạo của ứng dụng và các version đã sẵn sàng để realease cho người dùng có thể sử dụng (đặt Tag trên mỗi version). Thường cấu hình cho manage tương tác.

2. Develop ( Nhánh phát triển )
- Branch develop là branch trung tâm cho việc phát triển. Do với mỗi thay đổi ta lại ngắt branch feature tương ứng cho nên có thể nói đây là branch được dùng nhiều nhất trong quá trình phát triển. Cần đặt tên branch sao cho người khác có thể biết được ngay nội dung thay đổi là gì. Mỗi branch được ngắt ra để làm này sau khi làm xong ta lại merge vào develop, merge xong sẽ xóa nó đi.

3. Feature ( Nhánh chức năng )
- Feature branches (hay còn gọi là topic branches) được sử dụng để phát triển các feature mới phục vụ cho release sau này. Khi bắt đầu phát triển một chức năng, có thể chưa rõ được thời điểm chức năng đó được tích hợp vào hệ thống và release. Feature branch sẽ tồn tại trong quá trình chức năng được phát triển, cuối cùng sẽ được merge lại vào develop (khi quyết định lần release tới bao gồm chức năng đó) hoặc bị bỏ đi (khi thấy chức năng không còn cần thiết).
    + Tách từ: develop
    + Merge vào: develop
    + Quy ước đặt tên: tự do, ngoại trừ master, develop, release-*, hotfix-*
    
4. Release
- Trước khi Release một phần mềm dev team cần được tạo ra để kiểm tra lại lần cuối trước đi release sản phần để người dùng có thể sử dụng (Thuông thường mã nguồn tại thời điểm này sẽ tạo ra bản build để test và kiểm tra lại bussiness).
    + Tách từ: develop
    + Merge vào: develop và master
    + Quy ước đặt tên: release-*
    
5. Hotfix
- Được base trên nhánh master để sửa nhanh những lỗi trên UIT hoặc sửa những cấu hình đặc biệt chỉ có trên môi trường productions.
    + Tách từ: master
    + Merge vào: develop và master
    + Quy ước đặt tên: hotfix-*
    
### Triển khai
1. Git manager tạo git và mời các thành viên vào
- Git manager tạo thêm nhánh develop
    + git branch develop
    + git checkout develop
    + git commit -m "create branch develope"
    + git push origin develop
- https://github.com/taitamfc/Advanced-Git/settings/access
- Nhấn Add people để mời thành viên vào ( chỉ có thành viên được mời mới có quyền làm việc với Repo )

2. Các thành viên kiểm tra email -> chấp nhận -> clone dự án về 
- git clone https://github.com/taitamfc/Advanced-Git.git


3. Nhóm/Thành A viên xây dựng chức năng login
- Tạo nhánh feature-login
    + git branch feature-login
    + git checkout feature-login
    + git commit -m "create branch feature-login"
    + git push origin feature-login
- Thực hiện chức năng login ( tạo file login.php ), sau khi hoàn thành chức năng -> đẩy lên git
    + git checkout feature-login
    + git add *
    + git commit -m "complete feature-login"
    + git push origin feature-login

3. Nhóm/Thành B viên xây dựng chức năng register
- Tạo nhánh feature-register
    + git branch feature-register
    + git checkout feature-register
    + git commit -m "create branch feature-register"
    + git push origin feature-register
- Thực hiện chức năng register ( tạo file register.php ), sau khi hoàn thành chức năng -> đẩy lên git
    + git checkout feature-register
    + git add *
    + git commit -m "complete feature-register"
    + git push origin feature-register
    
4. Git manager thực hiện PULL REUQEST các nhánh chức năng vào nhánh develop
    
- Thực hiện trên github    
    + https://github.com/taitamfc/Advanced-Git/pulls
    + New pull request
    + chọn feature-login
    + Góc trái phần base ch develop
    + Create pull request
    + Nhập tiêu đều rồi nhấn: Create pull request
    + Nhấn Merge pull request

- Thực hiện trên git
    + git checkout develop
    + git pull origin develop
    + git merge feature-register
    + git commit -m "merge feature-register"
    + git push origin develop
    
5. Git manager thực hiện PULL REUQEST nhánh develop vào nhánh master
    
### Releases
 - Tạo nhánh release-1.0.0
    + git branch release-1.0.0
    + git checkout release-1.0.0
    + git pull orgin master
    + git commit -m "create branch release-1.0.0"
    + git push origin release-1.0.0
 - https://github.com/taitamfc/Advanced-Git/releases
 - Draft a new release
 - Choose a tag: v1.0.0
 - Target release-1.0.0
 - Release title: Gì cũng được: vd: Phát hành phiên bản 1.0.0
 - Publish release

### Các lỗi thường gặp
 - File to failed to push some refs to remote
    + code ở local repo và remote repo chưa đồng bộ
    + xử lý: git pull <tên remote> <tên nhánh>
    + thực hành:
        + tạo pull request trên github
        + git checkout develop ( chuyển sang nhánh develop )
        + tạo 1 file bất kì
        + git add *
        + git commit -m "test"
        + git push origin develop
 - Automatic merge failed; fix conflicts and then commit the result.
    + các thành viên đều sửa chung trên 1 file dẫn đến conflict
    + thực hành:
        + cả 2 thư mục cùng chuyển sang nhánh develop
        + git checkout develop ( chuyển sang nhánh develop )
        + team A sửa file login.php sang noi dung "login 1"
        + team B sửa file login.php sang noi dung "login 2"
        + team A add commit push to develop
        + team B add commit push to develop
        
    
