======================================
                Sets
======================================

++Kịch bản làm việc : Dùng làm chức năng like, tìm bạn chung

    SADD: thêm 1 phần tử vào value 
          nếu key chưa tồn tại thì tạo key rồi push phần tử vào set
          nếu key tồn tại và value ko phải set thì result error
            + thêm thành công trả về 1 ,thêm thất bại trả về 0  (value đã tồn tại)

    SREM: xóa một phần tử type set
          nếu key không phải set thì trả về lỗi
          + xóa thành công trả về 1 ,xóa thất bại trả về 0 (value đã tồn tại)
    
    SISMEMBER: kiểm tra một value có thuộc key set
          + nếu thuộc trả về 1 ,nếu không thuộc trả về 0

    SMEMBERS : get tất cả value trong key set
              nếu key không phải set thì trả về lỗi
    
    SUNION : get value của nhiều key
             nếu có key không thuộc set trả về lỗi 
             nếu có value giống giống chỉ lấy ra 1 giá trị
    
    SRANDMEMER : get random 1 item trong key
            + SRANDMEMER key quantity
    
    SPOP : xóa ngẫu nhiên
            +SPOP  key quantity

    SMOVE : duy chuyển 1 element 
            + SMOVE key1 key2 element
    
++ Kịch bản like trong Sets
        SADD feed:1 uid:1
        SADD feed:1 uid:2
        SADD feed:1 uid:3
        3 user 3 lượt like

        //check bao nhiêu like
        SCARD  feed:1 
        => 3 

        //nếu like tiếp thì kq là 0
        SADD feed:1 uid:1
        => trả về 0

        SCARD  feed:1 
        => 3 

        //hủy like
        SREM feed:1 uid:1

        SCARD  feed:1 
        => 2

        kiểm tra kết quả   
        SMEMBER 

++ Kịch bản bạn chung
        SADD friend1 1 2 3 4 5 6 7

        SADD friend2 5 6 7 8 9 10

        //get bạn chung
        SINTER friend1 friend2
        SINTER friend1 friend2
        => 5 6 7 

++ sản phẩm ko có trong giỏ hàng đối phương
        SDIFF friend1 friend2
        => 1 2 3 4

         SDIFF friend2 friend=1
        => 7 8 9 10
++ get random 1  element
        SRANDMEMBER