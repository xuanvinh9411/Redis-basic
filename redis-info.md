============ Cập nhật redis ============
1. BitMap (2.2)
2. HyperLogLog (2.8)
3. GEO (3.2)
4. Stream (5.0)

redis xử lí duy nhất các lệnh là 1 luồng

Sử dụng redis để đồng bộ hóa các thông tin phiên session 
Hình thong-tin-phien-01 việc đăng nhập lập đi lập lại nhiều lần do không tìm tháy thông tin phiên ở các server
Hình thong-tin-phien-02 sẽ đồng bộ các session ở các thông tin phiên . 
    Khi login ở server1 sẽ đồng bộ ở redis khi login server2 sẽ lấy thông tin redis