# SRS - Website Bán Mỹ Phẩm Online

## 1. Giới thiệu
Tài liệu mô tả các chức năng chính của hệ thống bán mỹ phẩm online.

---

## 2. Chức năng: Thêm vào giỏ hàng

### GWT-ADD-CART-01: Thêm sản phẩm thành công
```
GIVEN    người dùng đang xem sản phẩm còn hàng
WHEN     nhấn "Thêm vào giỏ hàng"
THEN     sản phẩm được thêm vào giỏ
AND      hiển thị thông báo thành công
```

### GWT-ADD-CART-02: Sản phẩm đã có trong giỏ
```
GIVEN    sản phẩm đã tồn tại trong giỏ
WHEN     người dùng thêm lại sản phẩm
THEN     hệ thống tăng số lượng sản phẩm
AND      không tạo sản phẩm trùng
```

### GWT-ADD-CART-03: Sản phẩm hết hàng
```
GIVEN    sản phẩm đã hết hàng
WHEN     người dùng nhấn "Thêm vào giỏ hàng"
THEN     không thêm vào giỏ
AND      hiển thị thông báo "Hết hàng"
```

### GWT-ADD-CART-04: Số lượng không hợp lệ
```
GIVEN    người dùng nhập số lượng <= 0
WHEN     nhấn thêm giỏ
THEN     hệ thống từ chối
AND      hiển thị lỗi "Số lượng không hợp lệ"
```

---

## 3. Chức năng: Xem giỏ hàng

### GWT-VIEW-CART-01: Xem giỏ có sản phẩm
```
GIVEN    giỏ hàng có sản phẩm
WHEN     người dùng mở giỏ hàng
THEN     hiển thị danh sách sản phẩm
AND      hiển thị tổng tiền
```

### GWT-VIEW-CART-02: Giỏ hàng trống
```
GIVEN    giỏ hàng không có sản phẩm
WHEN     người dùng mở giỏ hàng
THEN     hiển thị "Giỏ hàng trống"
AND      gợi ý quay lại mua hàng
```

### GWT-VIEW-CART-03: Lỗi tải dữ liệu
```
GIVEN    hệ thống lỗi server
WHEN     người dùng mở giỏ hàng
THEN     không hiển thị dữ liệu
AND      hiển thị "Không thể tải giỏ hàng"
```
