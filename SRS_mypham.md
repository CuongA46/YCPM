# SRS - Website Bán Mỹ Phẩm Online

## 1. Giới thiệu
Tài liệu mô tả hệ thống website bán mỹ phẩm online, bao gồm các chức năng giỏ hàng, giúp người dùng lựa chọn và mua sản phẩm.

---

## 2. Unhappy Paths

| Tình huống | Thông báo lỗi | Hành vi |
|-----------|--------------|--------|
| Sản phẩm không tồn tại | "Sản phẩm không tồn tại" | Không thêm vào giỏ |
| Sản phẩm hết hàng | "Sản phẩm đã hết hàng" | Chặn thêm |
| Số lượng không hợp lệ | "Số lượng không hợp lệ" | Không xử lý |
| Lỗi hệ thống | "Vui lòng thử lại sau" | Không hiển thị dữ liệu |

---

## 3. Chức năng: Thêm vào giỏ hàng

### Scenario 1: Thêm sản phẩm thành công
```
GIVEN    người dùng đang xem sản phẩm còn hàng
WHEN     nhấn "Thêm vào giỏ hàng"
THEN     sản phẩm được thêm vào giỏ
AND      hiển thị thông báo thành công
AND      cập nhật số lượng giỏ hàng
```

### Scenario 2: Sản phẩm đã có trong giỏ
```
GIVEN    sản phẩm đã tồn tại trong giỏ
WHEN     người dùng thêm lại sản phẩm
THEN     hệ thống tăng số lượng sản phẩm
AND      không tạo sản phẩm trùng
```

### Scenario 3: Sản phẩm hết hàng
```
GIVEN    sản phẩm đã hết hàng
WHEN     người dùng nhấn "Thêm vào giỏ hàng"
THEN     không thêm vào giỏ
AND      hiển thị thông báo "Hết hàng"
```

### Scenario 4: Số lượng vượt quá tồn kho
```
GIVEN    sản phẩm còn 5 trong kho
WHEN     người dùng thêm 10 sản phẩm
THEN     không thêm vào giỏ
AND      hiển thị "Vượt quá tồn kho"
```

---

## 4. Chức năng: Xem giỏ hàng

### Scenario 5: Xem giỏ có sản phẩm
```
GIVEN    giỏ hàng có sản phẩm
WHEN     người dùng mở giỏ hàng
THEN     hiển thị danh sách sản phẩm
AND      hiển thị giá, số lượng, tổng tiền
```

### Scenario 6: Giỏ hàng trống
```
GIVEN    giỏ hàng không có sản phẩm
WHEN     người dùng mở giỏ hàng
THEN     hiển thị "Giỏ hàng trống"
AND      gợi ý quay lại mua sắm
```

### Scenario 7: Sản phẩm trong giỏ hết hàng
```
GIVEN    sản phẩm trong giỏ đã hết hàng
WHEN     người dùng mở giỏ hàng
THEN     hiển thị trạng thái "Hết hàng"
AND      không cho phép thanh toán
```

### Scenario 8: Lỗi tải giỏ hàng
```
GIVEN    hệ thống lỗi server
WHEN     người dùng mở giỏ hàng
THEN     không hiển thị dữ liệu
AND      hiển thị "Không thể tải giỏ hàng"
```

---

## 5. Gợi ý mở rộng hệ thống

- Lưu giỏ hàng bằng Local Storage
- Đồng bộ giỏ hàng khi đăng nhập
- API backend (RESTful)
- Kết nối database (MySQL / MongoDB)
