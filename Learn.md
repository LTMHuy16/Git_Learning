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

  # khái niệm stash

    => Lưu ý: khi thưc hiện chuyển đổi đến 1 branch khác, những file được thêm mới hay nội dung vẫn còn lưu lại trong staging area mà thực hiện checkout đến branch khác thì nội dung thay đổi sẽ chuyển từ branch ban đầu đến branch chuyển đến.

    => Tuy nhiên, khi chuyển qua một branch mà có các file giống như vậy (mà các file này còn được thay đổi nội dung) thì checkout sẽ thất bại

    => Để giải quyết vấn đề này ta cần
      + commit lại nội dung đã thay đổi rồi mới checkout
      + sử dụng slash để tạm lưu lại lưu lại nội dung thay đổi, sau đó phải thực hiện commit

    => Khái niệm stash: là một khu vực ghi lại tạm thời nội dung thay đổi của file trong 2 khu vực working và staging area

  # Gộp branch

    + Có 2 cách gộp branch là merge và rebase
    ==> Hai cách này có sự khác biệt khá lớn
  
  ## Merge

    1. merge fast-forward (chuyển tiếp nhanh): với hình bên dưới thì chỉ cần branch lấy nội dung của new-branch

      A ==== B 
            || ==== C` ==== D` ====|| // new-branch = master

    2. non fast-forward: new-branch tách ra từ B và cả 2 đến D, khi thưc hiện merge thì sẽ chuyển đến nút M
      A ==== B ==== C  ==== D  ==== M
            || ==== C` ==== D` ====|| // new-branch
  
  ## Rebase

    A ==== B ==== C  ==== D // master
          || ==== C` ==== D` // new-branch
    
    Khi thực hiện rebase thì lịch sử new-branch sẽ được đính kèm vào branch master

      A ==== B ==== C  ==== D ==== C` ==== D`// master == new-branch

  # git merge branch-name

    => merge branch đang đứng với branch-name

    => Ở phần non-fast-forward

    A ==== B ==== C  ==== D  ==== M  ===== Change
           || ==== C` ==== D` ====|| ===== Change -> conflict  
            // new-branch

    => Phần trên sẽ gây ra conflict, để giải quyết ta cần chọn giữa 2 phần Current changes vs Incoming change -> sau đó ta thực hiện add/ commit lại để resolve

  # git reset

    => --soft [mã commit]: chuyển về commit đã được chọn, mọi thay đổi từ điểm gốc đến điểm commit (hình dưới) sẽ được đưa vào staging area, khi git log ra thì sẽ mất các commit1, HEAD

    HEAD ---- commit 1 ---- commit2
      |-------------------------|

    ==> git reset khá ok khi làm việc tại local, tuy nhiên cần cân nhắc khi làm việc remote với nhiều thành viên sử dụng, để làm share cho remote repos thì cần phải thực hiện git push -f, nó sẽ hủy tất cả các history trên branch thực hiện sau điểm push

  # git revert

    => Chuyển về một commit được chọn
    ==> ví dụ có 6 commit và bạn đang ở commit thứ 6 => sau khi revert về 4 chẳng hạn => thì git sẽ coppy phiên bản đó cho hiện tại => không ảnh hưởng gì đến các commit (các commit từ 1 đến 6 vẫn tồn tại)