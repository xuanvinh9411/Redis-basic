======================================
                HASH
======================================

kiểu dữ liệu hash là băm
Dùng để lưu trữ các đối tượng
Kịch bản là làm giỏ hàng
lưu trữ giá trị bồ đệm

Khác nhau với string xem hình redis-type-hash và redis-type-string

// set giá trị cho key user:01
HSET user:06 name vinh

HSET user:06 age 26
=> mổi lần chỉ set dc một key

//lấy giá trị user:01
HGET user:01 name
 "vinh"
=> mổi lần chỉ get dc một key

//set giá trị nhiều key nhiều value
HMSET user:04 email email4 phone 4 name vinh4 
HMGET user:04 email phone name 

// xóa giá trị trong trường(name , email, age)
HDEL user:03 email

// kiểm tra có bao nhiêu trường(name , email, age)
HLEN user:03 
kết quả là 02

// kiểm tra tất cả các key 
HGETALL USER:01
"name"
"vinh"
"age"
"39"

// kiểm tra key có tồn tại ko
HEXISTS user:01 . error
HEXISTS user:01 name
> nếu tồn tại trả về 1
> ko tồn tại trả về 0

// công giá trị với key là init
HINCRBY user:06 name 1 . error
HINCRBY user:06 age 1 
>nếu chưa có key sẽ tạo key 
>nếu có rồi thì trả về kết quả sau khi cộng

//get key hash
HKEYS user:01
"name"
"age"

//get value của key hash
HVALS user:01
"vinh"
"38"

