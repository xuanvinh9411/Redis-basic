======================================
                STRING
======================================

String : SDS

Kịch bản làm việc : đối tượng bộ đếm, sống lượng thông thường , khóa phân tán , thông tin được chia sẻ theo phiên
Max : 512mb

embstring (<= 44 bytes) Lưu trữ chuỗi
vd: 0123456789012345678901234567890123456789abcd
raw (> 44 bytes) Lưu trữ chuỗi
vd: abcd0123456789012345678901234567890123456789abcd
==> tham khảo hình type_string

int (integer) lưu trữ dữ liệu sô nguyên

--lệnh set get string
Mset key1 value1 key2 value2 key3 value3
Mget key1 key2 key3
=> cách đặt key cho redis là product:product_id , user:user_id
vd : Mset user:user_id:name "name" user:user_id:age 20 // set giá trị
     Mget user:user_id:name user:user_id:age // kết quả là "name" "20"
    
//Kịch bản like 
    set 001:like 0

    -Tăng giá trị string
    INCR 001:like  // tăng giá trị 0001:like lên 1
    INCRBY 001:like 8 // tăng giá trị 0001:like lên thêm 8

    -Giảm giá trị string
    DECR 001:like  // giảm giá trị 0001:like xuống 1
    DECRBY 001:like 8 // giảm giá trị 0001:like xuống thêm 8

    -Search key trong string 
    KEYS '001:*' //lấy các key có ký tự đầu bằng 001

    - Set : set val cho một key 
        Set keyName 'val'

    - SetNX : set val cho một key nếu key tồn tại trả về 0
            Setnx keyName 'val'

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

++ Kịch bản khóa phân tán 
    SET lock_key unique_value NX PX 1000
    