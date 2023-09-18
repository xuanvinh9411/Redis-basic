======================================
                List
======================================

Ứng dụng vào hàng đợi và ngăn sếp messega queue

Đáp ứng được 3 yêu cầu
    -bảo toàn được thứ tự tin nhắn
    -xử lí tin nhắn trùng lập
    -độ tin cậy tin nhắn
----------------------------------

Ứng dụng History

LPUSH list:01 a b c
=> [ c, b, a]

RPUSH list:02 x y z

các lệnh thông dụng : LPUSH , RPUSH , LPOP , RPOP ,LLEN, LRANGE

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

    LREM(L remove) : xóa một phần tử khớp với index và value
        => LREM index value
    
    LTRIM : xóa các phần tử không trong index1 đến index2
        => LTRIM index1 index2

    LLEN: trả về số phần tử trong list
    => LLEN :  nếu key chưa tồn tại hoặc value list rỗng thì 0
               nếu value ko phải là list thì trả về error

    LRANGE: cú pháp LRANGE key index1 index2 . Get element trong khoảng  theo index 
            index bắt đầu từ 0 
            => nếu tính số âm thì kết thúc là -1
            vd: value list là [1,2,3,4,5] thì index âm là -5, -4, -3, -2, -1
            lấy all thì index là : 0 -1
    
    BLPOP : bock key khi delete element
    => làm message queue 

    LSET : update value array
        LSET key index newvalue

    LINSERT : chèn value vào array trước hoặc sau value được chỉ định 
        LINSERT key (BEFORE|AFTER) value newvalue