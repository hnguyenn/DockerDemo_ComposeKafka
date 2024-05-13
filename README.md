# Cấu Hình Docker Compose Cho Apache Kafka

Kho lưu trữ này chứa một tệp Docker Compose để triển khai Apache Kafka sử dụng hình ảnh Kafka của Bitnami. 
## Yêu Cầu
- Docker 19.03.0+
- Docker Compose 1.27.0+

## Tổng Quan Về Cấu Hình

### Kafka trong Chế Độ KRaft
Cài đặt này triển khai Kafka với chế độ KRaft. Điều này được chỉ định bởi biến môi trường `KAFKA_ENABLE_KRAFT=yes`.

### Dịch Vụ Được Cấu Hình
- **Kafka**: Dịch vụ được cấu hình để đóng vai trò cả nhà môi giới và điều khiển, được chỉ ra bởi `KAFKA_CFG_PROCESS_ROLES=broker,controller`.

### Networking
- Dịch vụ Kafka được cấu hình với hai loại listener:
  - **PLAINTEXT**: Dành cho giao tiếp nội bộ trên cổng 9092.
  - **CONTROLLER**: Dành cho giao tiếp điều khiển trên cổng 2181.
- Các giao thức bảo mật cho mỗi người nghe được thiết lập qua `KAFKA_CFG_LISTENER_SECURITY_PROTOCOL_MAP`.

