Tạo một mạng dùng chung:

```bash
docker network create calmvestor-network
```

- `n8n_service` (tên container)
- `n8n_postgres_db`
- `api`

Bạn muốn **gắn `n8n_service` và `api` vào cùng mạng `calmvestor-network`**. Dưới đây là lệnh để thực hiện điều đó **mà không cần restart container**:

---

### ✅ Bước 1: Gắn `n8n_service` vào `calmvestor-network`

```bash
docker network connect calmvestor-network n8n_service
```

---

### ✅ Bước 2: Gắn `api` vào `calmvestor-network`

```bash
docker network connect calmvestor-network api
```

---

### ✅ (Tuỳ chọn) Kiểm tra lại

```bash
docker network inspect calmvestor-network
```

Bạn sẽ thấy cả hai container nằm trong danh sách `Containers`.

---