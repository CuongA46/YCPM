# Đề tài - Website Bán Mỹ Phẩm Online

## Quy tắc nghiệp vụ (Business Rules)

BR-01:Tồn kho thực tế,Khách hàng không thể thêm số lượng sản phẩm lớn hơn số lượng hiện có trong kho.

BR-02:Cập nhật giá,Giá sản phẩm trong giỏ hàng phải được cập nhật theo giá niêm yết mới nhất của hệ thống tại thời điểm xem giỏ.

BR-03:Sản phẩm trùng,"Nếu thêm sản phẩm đã có trong giỏ, hệ thống chỉ tăng số lượng (quantity) thay vì tạo dòng mới."

BR-04:Trạng thái hết hàng,"Nếu sản phẩm trong giỏ bị hết hàng trong kho, hệ thống phải ngăn chặn hành vi thanh toán (Checkout)."

## 1. Chức năng: Thêm vào giỏ hàng (Add to Cart)

### Acceptance Criteria (AC) - Tiêu chí chấp nhận
```
Chức năng: Thêm vào giỏ hàng
AC 1: Khi nhấn "Thêm vào giỏ", hệ thống phải phản hồi ngay lập tức (hiển thị thông báo hoặc thay đổi số icon giỏ hàng).

AC 2: Nếu sản phẩm có nhiều biến thể (màu son, dung tích), khách hàng phải chọn biến thể trước khi thêm vào giỏ.

AC 3: Hệ thống phải thông báo lỗi cụ thể nếu người dùng cố tình thêm sản phẩm vượt quá số lượng tồn kho cho phép.
```

### User Story
```
"Là một Khách hàng, tôi muốn thêm các sản phẩm yêu thích vào giỏ hàng để tôi có thể gom nhiều món đồ và tiến hành thanh toán một lần."
```
### Đặc tả 
```
Cho phép người dùng chọn sản phẩm và số lượng để đưa vào danh sách chờ thanh toán.
Dữ liệu đầu vào (Inputs): Mã sản phẩm (ID), số lượng cần thêm.
Luồng xử lý (Processing): Hệ thống kiểm tra trạng thái tồn kho của sản phẩm trong cơ sở dữ liệu.
Kết quả đầu ra (Outputs): Thông báo thành công và cập nhật số hiệu (Badge) trên biểu tượng giỏ hàng.
```

#### Scenario 1: Thêm sản phẩm thành công (Happy path)
```
GIVEN    người dùng đang xem sản phẩm còn hàng
WHEN     nhấn "Thêm vào giỏ hàng"
THEN     sản phẩm được thêm vào giỏ
AND      hiển thị thông báo thành công
AND      cập nhật số lượng giỏ hàng
```

#### Scenario 2: Sản phẩm đã có trong giỏ (Happy path)
```
GIVEN    sản phẩm đã tồn tại trong giỏ
WHEN     người dùng thêm lại sản phẩm
THEN     hệ thống tăng số lượng sản phẩm
AND      không tạo sản phẩm trùng
```

#### Scenario 3: Sản phẩm hết hàng (Happy path)
```
GIVEN    sản phẩm đã hết hàng
WHEN     người dùng nhấn "Thêm vào giỏ hàng"
THEN     không thêm vào giỏ
AND      hiển thị thông báo "Hết hàng"
```

#### Scenario 4: Số lượng vượt quá tồn kho (Unhappy path)
```
GIVEN    sản phẩm còn 5 trong kho
WHEN     người dùng thêm 10 sản phẩm
THEN     không thêm vào giỏ
AND      hiển thị "Vượt quá tồn kho"
```



## 2. Chức năng: Xem giỏ hàng (View Cart)

### Acceptance Criteria (AC) - Tiêu chí chấp nhận
```
Chức năng: Xem giỏ hàng
AC 1: Giỏ hàng phải hiển thị đầy đủ: Ảnh sản phẩm, Tên, Đơn giá, Số lượng, và Thành tiền của từng món.

AC 2: Tổng tiền thanh toán (Total) phải bằng tổng các thành tiền của từng sản phẩm cộng lại.

AC 3: Nếu giỏ hàng trống, hệ thống phải hiển thị nút "Quay lại cửa hàng" để khuyến khích tiếp tục mua sắm.
```

### User Story
```
"Là một Khách hàng, tôi muốn xem lại danh sách các sản phẩm đã chọn để kiểm tra số lượng, đơn giá và tổng số tiền mình cần phải trả."
```
### Đặc tả 
```
Hiển thị chi tiết các mặt hàng khách hàng đã chọn và tính toán giá trị đơn hàng.
Dữ liệu đầu vào (Inputs): Dữ liệu phiên làm việc (Session) hoặc ID giỏ hàng của người dùng.
Luồng xử lý (Processing): Truy xuất danh sách sản phẩm trong giỏ kèm hình ảnh, tên, đơn giá.
Kết quả đầu ra (Outputs): Giao diện danh sách sản phẩm chi tiết.
```

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

## 3. Chức năng: Áp dụng Voucher (Apply Voucher)

### Acceptance Criteria (AC) - Tiêu chí chấp nhận
```
Chức năng: Áp dụng Voucher
AC 1: Người dùng có thể nhập mã voucher vào ô "Mã giảm giá".
AC 2: Nếu voucher hợp lệ, hệ thống phải áp dụng giảm giá đúng theo giá trị (%, hoặc số tiền cố định).
AC 3: Tổng tiền thanh toán phải được cập nhật sau khi áp dụng voucher.
AC 4: Nếu voucher không hợp lệ hoặc hết hạn, hệ thống phải hiển thị thông báo lỗi.
AC 5: Một đơn hàng chỉ được áp dụng 1 voucher tại một thời điểm.
```

### User Story
```
"Là một Khách hàng, tôi muốn nhập mã giảm giá để được giảm giá trên tổng đơn hàng trước khi thanh toán."
```

### Đặc tả
```
Cho phép người dùng nhập và áp dụng mã voucher để giảm giá đơn hàng.

Dữ liệu đầu vào (Inputs): 
- Mã voucher người dùng nhập
- Tổng tiền đơn hàng hiện tại
Luồng xử lý (Processing):
- Kiểm tra voucher có tồn tại không
- Kiểm tra còn hạn sử dụng
- Kiểm tra điều kiện áp dụng (ví dụ: đơn hàng tối thiểu)
- Tính toán giá trị giảm
Kết quả đầu ra (Outputs):
- Tổng tiền mới sau khi áp dụng voucher
- Thông báo thành công hoặc lỗi
```

### Scenario 8: Áp dụng voucher thành công (Happy path)
```
GIVEN    tổng tiền giỏ hàng là 500000 VND
AND      voucher "SALE10" giảm 10%
WHEN     người dùng nhập mã "SALE10" và áp dụng
THEN     hệ thống áp dụng giảm giá 10%
AND      tổng tiền mới = 450000 VND
```

---

### Scenario 9: Voucher không tồn tại (Unhappy path)
```
GIVEN    người dùng nhập mã "ABC123"
WHEN     hệ thống kiểm tra
THEN     không tìm thấy voucher
AND      hiển thị "Voucher không hợp lệ"
```

### Scenario 10: Voucher hết hạn (Unhappy path)
```
GIVEN    voucher "SALE20" đã hết hạn
WHEN     người dùng áp dụng voucher
THEN     hệ thống từ chối
AND      hiển thị "Voucher đã hết hạn"
```

### Scenario 11: Không đủ điều kiện áp dụng (Unhappy path)
```
GIVEN    voucher yêu cầu đơn hàng tối thiểu 300000 VND
AND      tổng tiền hiện tại là 200000 VND
WHEN     người dùng áp dụng voucher
THEN     không áp dụng
AND      hiển thị "Không đủ điều kiện áp dụng"
```

### Scenario 12: Áp dụng nhiều voucher (Unhappy path)
```
GIVEN    giỏ hàng đã áp dụng 1 voucher
WHEN     người dùng nhập thêm voucher khác
THEN     hệ thống từ chối
AND      hiển thị "Chỉ được sử dụng 1 voucher"
```
