1 . Giới thiệu Redis 
    Redis là một cơ sở dữ liễu NoSQL
    Database redis được lưu trữ trên ram
    Data redis dạng key - value

2 . Hướng và cài đặt redis

3 . Các lệnh cơ bản cảu redis
    - Set : set val cho một key 
        Set keyName 'val'

    - Get : get val của một key 
        get keyName
        * nếu key undefined giá trị trả về : nil 

    - DEL : delete một cập key : val
        delet keyName

    - EXPIRE : set time sencod 
        expire keyName 100(time)

    - TTL : check time tồn tại 
        ttl  keyName
        . nếu -1 là ko set time
        . nếu -2 là đã bị xóa

    - RENAME : reanme key
        rename key newkey
        . nếu key đã tồn tại thì nó sẽ ghi đè lên giá trị của key
        . kết quả trả về OK

    - RENAMENX : rename key (newkey không tồn tại)
        renamenx key newkey
        . newkey tồn tại trả về 0

    - TYPE : check type dữ liệu
        type key

    - EXISTS : check tồn tại key
        exists key

    -** Redis Transaction
        Redis transaction cho phép một nhóm các lệnh thực hiện theo thứ tự cho đến khi lệnh cuối cùng được thực hiện xong.
        Khi này Redis mới cập nhật đồng thời dữ liệu thay đổi bởi nhóm lệnh này.
        MULTI : start transaction
        EXEC  : end transaction