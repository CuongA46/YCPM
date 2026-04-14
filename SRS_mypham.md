# SRS - Website Bán Mỹ Phẩm Online

## 1. Chức năng: Thêm vào giỏ hàng (Add to Cart)

### Scenario 1: Thêm sản phẩm thành công (Happy path)
```
GIVEN    người dùng đang xem sản phẩm còn hàng
WHEN     nhấn "Thêm vào giỏ hàng"
THEN     sản phẩm được thêm vào giỏ
AND      hiển thị thông báo thành công
AND      cập nhật số lượng giỏ hàng
```

### Scenario 2: Sản phẩm đã có trong giỏ (Happy path)
```
GIVEN    sản phẩm đã tồn tại trong giỏ
WHEN     người dùng thêm lại sản phẩm
THEN     hệ thống tăng số lượng sản phẩm
AND      không tạo sản phẩm trùng
```

### Scenario 3: Sản phẩm hết hàng (Happy path)
```
GIVEN    sản phẩm đã hết hàng
WHEN     người dùng nhấn "Thêm vào giỏ hàng"
THEN     không thêm vào giỏ
AND      hiển thị thông báo "Hết hàng"
```

### Scenario 4: Số lượng vượt quá tồn kho (Unhappy path)
```
GIVEN    sản phẩm còn 5 trong kho
WHEN     người dùng thêm 10 sản phẩm
THEN     không thêm vào giỏ
AND      hiển thị "Vượt quá tồn kho"
```

---

## 2. Chức năng: Xem giỏ hàng (View Cart)

### Scenario 5: Xem giỏ có sản phẩm (Happy path)
```
GIVEN    giỏ hàng có sản phẩm
WHEN     người dùng mở giỏ hàng
THEN     hiển thị danh sách sản phẩm
AND      hiển thị giá, số lượng, tổng tiền
```

### Scenario 6: Giỏ hàng trống (Happy path)
```
GIVEN    giỏ hàng không có sản phẩm
WHEN     người dùng mở giỏ hàng
THEN     hiển thị "Giỏ hàng trống"
AND      gợi ý quay lại mua sắm
```

### Scenario 7: Sản phẩm trong giỏ hết hàng (Unhappy path)
```
GIVEN    sản phẩm trong giỏ đã hết hàng
WHEN     người dùng mở giỏ hàng
THEN     hiển thị trạng thái "Hết hàng"
AND      không cho phép thanh toán
```

