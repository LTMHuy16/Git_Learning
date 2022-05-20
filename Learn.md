  # có 3 khu cực chính của git

  | Thư mục đang làm việc      | Staging Area | Committed |
  

  # git add

    => Chuyển thư mục được chọn từ thư mục đang làm việc đến Staging Area

    + .  thêm tất cả các file vào
    + tên file: thêm một file được chỉ định vào

  # git restore --staged tên file

    => chuyển file từ khu vực staging area về lại thư mục đang làm việc

  # git commit

    => chuyển file từ Staging Area đến committed
  
  # git status

    => Xem trạng thái các file chưa được commit

  # git log

    => Xem thông tin các lần commit, để thoát khoải chế độ git log thì bấm Q

    + git log --oneline

  # git checkout -b new-branch

    => Tạo ra các nhánh, khi làm việc nhóm mỗi người có thể thực hiện một chức năng thì cần thì cần phải tạo ra một branch để thực thực hiện chức năng của mình mà không ảnh hưởng tới người khác, khi xong thì ta mới gộp các thay đổi này lên branch chính

  # git checkout branch-name

    => Chuyển về một branch đã có

  # git merge branch-name

    => merge branch đang đứng với branch-name