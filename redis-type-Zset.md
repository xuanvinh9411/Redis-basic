======================================
                Zset
======================================
Zset là tập hợp các phần tử có thứ tự không trùng lập với dạng KeyValue

++ Cấu trúc dữ liệu như [Set]

++ Kịch bản làm việc : Tổng hợp sản phẩm bán chạy, lượt xem và theo dõi , bảng sếp hạng
* Thêm phần tử
  - ZADD pre:2023 89 manCity 84 arsenal 75 manu 71 new 67 liverpool

* sấp xếp từ nhỏ tới 
  - ZRANGE pre:2023 0 -1
   => liverpool
     new
     manu
     arsenal
     manCity
* sấp xếp từ nhỏ tới 
  - ZRANGE pre:2023 0 -1
   => liverpool
     new
     manu
     arsenal
     manCity
* xóa element
   - ZREM pre:2023 manCity

* Lấy số lượng element 
   - ZCARD pre:2023
 
* Tăng số điểm 
   - ZINCRBY pre:2023 arsenal 10
  => get arsenal thành 94 

* Lấy danh sách trong khoảng 
   - ZRANGEBYSCORE pre:2023 70 80 
  =>  new
      manu
      arsenal

++ kịch bản lấy danh sách số lượng bán
   ZADD shopDev 1234 pro:1
   ZADD shopDev 123 pro:2
   ZADD shopDev 234 pro:3
   ZADD shopDev 2367 pro:4
   ZADD shopDev 432 pro:5