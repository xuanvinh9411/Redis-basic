Redis gồm các kiểu dữ liệu : LIST, SET, SORTED SET, HASH
1: List
    Kiểu list bao gồm các lệnh commnad : LPUSH , RPUSH , LPOP , RPOP ,LLEN, LRANGE

    LPUSH: thêm một phần tử vào đầu list
    RPUSH: thêm một phần tử vào cuối list
    => LPUSH & RPUSH : nếu key chưa tồn tại thì tạo key rồi push phần tử vào List
                       nếu key tồn tại và value ko phải List thì result error
                       Result trả về số lượng phần tử đang có sau khi push
    vd:

    LPOP: xóa một phần tử đầu tiên list
    RPOP: xóa một phần tử cuối cùng list
    => LPOP & RPOP :   nếu key chưa tồn tại hoặc value list rỗng thì trả về nil
                       nếu key tồn tại và value ko phải List thì result error
                       Result trả về phần tử đã xóa trong list
    vd:

    LLEN: trả về số phần tử trong list
    => LLEN :  nếu key chưa tồn tại hoặc value list rỗng thì 0
               nếu value ko phải là list thì trả về error

    LRANGE: cú pháp LRANGE key index1 index2 . Get element trong khoảng  theo index 
            index bắt đầu từ 0 
            => nếu tính số âm thì kết thúc là -1
            vd: value list là [1,2,3,4,5] thì index âm là -5, -4, -3, -2, -1
            lấy all thì index là : 0 -1
    vd:

2: Set
    Kiểu set bao gồm các lệnh commnad : SADD, SREM, SISMEMBER, SMEMBERS, SUNION

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
    
3: Sorted Set  
    Kiểu set bao gồm các lệnh commnad : ZADD, SCARD, ZRANGE, ZSCORE  , ZRANK ,ZCOUNT 

    Redis sorted set sẽ sấp sếp theo độ ưu tiên
    ZADD test scores value

4: Hash
    hash là kiểu dữ liệu với value là string