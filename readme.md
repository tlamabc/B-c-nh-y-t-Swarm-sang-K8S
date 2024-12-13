# Giới Thiệu Kubernetes (K8s) Cho Người Chuyên Docker Swarm

## Tại sao nên quan tâm đến Kubernetes?

Nếu bạn đã quen thuộc với Docker Swarm, chắc hẳn bạn hiểu rõ giá trị của việc sử dụng container orchestration để quản lý các ứng dụng container hóa. Tuy nhiên, Kubernetes (K8s) đã trở thành tiêu chuẩn công nghiệp, với khả năng mở rộng mạnh mẽ hơn, cộng đồng phát triển lớn hơn, và hỗ trợ tốt hơn từ các nhà cung cấp dịch vụ đám mây.

Dưới đây là cái nhìn tổng quan về Kubernetes, cùng với sự so sánh với Docker Swarm để giúp bạn dễ dàng tiếp cận và khai thác tiềm năng của K8s.

---

## Kubernetes là gì?

Kubernetes là một nền tảng **orchestration container** mã nguồn mở, được phát triển bởi Google và hiện nay được quản lý bởi CNCF (Cloud Native Computing Foundation). K8s cung cấp một bộ công cụ mạnh mẽ để triển khai, quản lý, và mở rộng ứng dụng container hóa trên nhiều môi trường khác nhau, từ on-premises đến cloud.

---

## So sánh Docker Swarm và Kubernetes

| **Tiêu chí**           | **Docker Swarm**                            | **Kubernetes**                                   |
|-------------------------|---------------------------------------------|-------------------------------------------------|
| **Dễ sử dụng**         | Cấu hình đơn giản, dễ học                   | Cấu hình phức tạp hơn nhưng mạnh mẽ hơn         |
| **Mở rộng (Scalability)** | Hạn chế khi cần quản lý cụm lớn            | Rất mạnh mẽ, phù hợp với ứng dụng phức tạp      |
| **Networking**         | Dễ thiết lập nhưng hạn chế trong tùy chỉnh  | Linh hoạt, hỗ trợ nhiều plugin networking       |
| **Hệ sinh thái**       | Ít tích hợp, tập trung vào Docker           | Tích hợp sâu rộng với hệ sinh thái cloud-native |
| **Cộng đồng**          | Nhỏ hơn                                    | Rất lớn, hỗ trợ từ nhiều nhà cung cấp cloud     |

---

## Kiến trúc cơ bản của Kubernetes

1. **Master Node**: Chịu trách nhiệm quản lý toàn bộ cụm, bao gồm:
   - **API Server**: Giao tiếp với người dùng và hệ thống.
   - **Scheduler**: Xác định nơi triển khai container.
   - **Controller Manager**: Quản lý trạng thái của các thành phần.

2. **Worker Node**: Chạy các container thông qua **Pod**.
   - **Kubelet**: Quản lý các container trên node.
   - **Kube-proxy**: Quản lý mạng giữa các node.

3. **Pod**: Đơn vị triển khai nhỏ nhất, chứa một hoặc nhiều container.

4. **ConfigMap/Secret**: Cung cấp cách quản lý cấu hình và thông tin nhạy cảm.

---

## Chuyển từ Docker Swarm sang Kubernetes

### Bước 1: Hiểu khái niệm tương đương

- **Service (Swarm)** tương đương với **Deployment** và **Service** trong K8s.
- **Stack (Swarm)** tương đương với **Namespace** trong K8s.
- **Overlay Network** trong Swarm được thay bằng **CNI Plugins** trong K8s.

### Bước 2: Sử dụng công cụ chuyển đổi

Nếu bạn đã có file `docker-compose.yml`, bạn có thể sử dụng **Kompose** để chuyển đổi sang file Kubernetes YAML.

```bash
kompose convert
