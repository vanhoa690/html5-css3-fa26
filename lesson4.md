# BÀI 4: CHUYỂN ĐỘNG & HIỆU ỨNG NÂNG CAO VỚI CSS3 TRANSITION, TRANSFORM & ANIMATION

---

## 1. CHUYỂN ĐỘNG MƯỢT MÀ VỚI CSS3 TRANSITION

### 1.1 Khái Niệm Transition

- **CSS Transition**: Cho phép thay đổi giá trị thuộc tính CSS một cách mượt mà từ trạng thái ban đầu sang trạng thái mới trong khoảng thời gian xác định (thường kích hoạt qua `:hover`, `:focus`, `:active`).

### 1.2 Bảng Tra Cứu 4 Thuộc Tính Transition

| Thuộc Tính                       | Ý Nghĩa Nhớ Nhanh                   | Ví Dụ Cụ Thể                                           |
| :------------------------------- | :---------------------------------- | :----------------------------------------------------- |
| **`transition-property`**        | Tên thuộc tính CSS cần tạo hiệu ứng | `background-color`, `transform`, `all` (tất cả)        |
| **`transition-duration`**        | Thời gian thực hiện chuyển động     | `0.3s`, `500ms` (Bắt buộc phải có)                     |
| **`transition-timing-function`** | Gia tốc / Nhịp điệu chuyển động     | `ease`, `linear`, `ease-in`, `ease-out`, `ease-in-out` |
| **`transition-delay`**           | Độ trễ trước khi hiệu ứng bắt đầu   | `0.1s`, `0s` (Mặc định: 0)                             |

> **Cú pháp viết tắt (Shorthand)**:
> `transition: <property> <duration> <timing-function> <delay>;`  
> _Ví dụ_: `transition: all 0.3s ease 0.1s;` hoặc đơn giản: `transition: 0.3s;`

---

## 2. BIẾN ĐỔI HÌNH HỌC VỚI CSS3 TRANSFORM (2D & 3D)

### 2.1 Bảng Tra Cứu Các Hàm Transform 2D Thường Gặp

| Hàm Transform          | Công Dụng                                                    | Ví Dụ Cú Pháp                            |
| :--------------------- | :----------------------------------------------------------- | :--------------------------------------- |
| **`translate(x, y)`**  | Dịch chuyển vị trí theo trục X (ngang) và Y (dọc)            | `transform: translate(10px, -20px);`     |
| **`scale(x, y)`**      | Co giãn kích thước (Tỷ lệ 1 là gốc, >1 phóng to, <1 thu nhỏ) | `transform: scale(1.2);` (Phóng to 120%) |
| **`rotate(deg)`**      | Xoay phần tử theo góc (đơn vị `deg` - độ)                    | `transform: rotate(45deg);` (Xoay 45 độ) |
| **`skew(x, y)`**       | Nghiêng / Bóp méo phần tử theo góc                           | `transform: skew(10deg, 0deg);`          |
| **`transform-origin`** | Thay đổi **tâm điểm biến đổi** (Mặc định: `center center`)   | `transform-origin: top left;`            |

### 2.2 Transform 3D Cơ Bản

- **`rotateX(deg)`** / **`rotateY(deg)`**: Xoay phần tử quanh trục X/Y trong không gian 3D.
- **`perspective`**: Đặt chiều sâu không gian 3D trên phần tử cha (ví dụ: `perspective: 1000px;` để tạo hiệu ứng lật card 3D).

---

## 3. HOẠT HỌA NÂNG CAO VỚI CSS3 ANIMATION & @KEYFRAMES

### 3.1 Cấu Trúc Khai Báo `@keyframes`

Animation cho phép chuyển động tự động lặp lại mà không cần sự tương tác chuột của người dùng.

```css
/* Định nghĩa kịch bản chuyển động */
@keyframes pulse {
  0% {
    transform: scale(1);
    opacity: 1;
  }
  50% {
    transform: scale(1.1);
    opacity: 0.8;
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}
```

### 3.2 Bảng Tra Cứu Thuộc Tính CSS Animation

| Thuộc Tính                      | Các Giá Trị Phổ Biến                    | Ý Nghĩa Nhớ Nhanh                                       |
| :------------------------------ | :-------------------------------------- | :------------------------------------------------------ |
| **`animation-name`**            | Tên kịch bản                            | Khớp với tên sau `@keyframes`                           |
| **`animation-duration`**        | `1s`, `2s`                              | Thời gian hoàn thành 1 chu kỳ animation                 |
| **`animation-iteration-count`** | Số lần (`3`), `infinite`                | Số lần lặp lại (dùng `infinite` để lặp vô hạn)          |
| **`animation-direction`**       | `normal`, `reverse`, `alternate`        | Direction: `alternate` chạy đi rồi chạy ngược lại       |
| **`animation-fill-mode`**       | `none`, `forwards`, `backwards`, `both` | `forwards`: Giữ nguyên trạng thái cuối sau khi kết thúc |

> **Cú pháp viết tắt (Shorthand)**:
> `animation: <name> <duration> <timing-function> <delay> <iteration-count> <direction> <fill-mode>;`  
> _Ví dụ_: `animation: pulse 1.5s ease-in-out infinite;`

---

## 4. BÀI TẬP: DỰNG CARD SẢN PHẨM HOVER 3D & LOADING SPINNER ANIMATION

### Yêu cầu: Tiếp nối các bài trước, áp dụng CSS3 Transition, Transform 2D/3D và Animation `@keyframes` để dựng Card có hiệu ứng nâng khối mượt và hiệu ứng xoay Loading Spinner.

```html
<!DOCTYPE html>
<html lang="vi">
  <head>
    <meta charset="UTF-8" />
    <title>Bài 4 - CSS3 Transition & Animation</title>
    <style>
      * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
      }
      body {
        font-family: "Segoe UI", sans-serif;
        background: #f4f6f9;
        padding: 50px;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 40px;
      }

      /* 1. Card sản phẩm hiệu ứng Transition & Transform */
      .card {
        width: 280px;
        background: white;
        border-radius: 12px;
        padding: 20px;
        text-align: center;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        /* Chuyển động mượt 0.3 giây cho tất cả biến đổi */
        transition:
          transform 0.3s ease,
          box-shadow 0.3s ease;
      }

      /* Hover: Phóng to nhẹ + Nâng khối + Đổ bóng sâu */
      .card:hover {
        transform: translateY(-8px) scale(1.02);
        box-shadow: 0 12px 24px rgba(0, 0, 0, 0.15);
      }

      .card img {
        width: 100%;
        height: 160px;
        object-fit: cover;
        border-radius: 8px;
        transition: transform 0.4s ease;
      }

      /* Hover Card: Ảnh bên trong xoay nhẹ */
      .card:hover img {
        transform: scale(1.05) rotate(1deg);
      }

      .btn-action {
        margin-top: 15px;
        padding: 10px 20px;
        border: none;
        background: #008080;
        color: white;
        font-weight: bold;
        border-radius: 6px;
        cursor: pointer;
        transition:
          background 0.2s ease,
          transform 0.1s ease;
      }

      .btn-action:hover {
        background: #005656;
      }
      .btn-action:active {
        transform: scale(0.95);
      } /* Nút ấn lún xuống khi click */

      /* 2. Loading Spinner sử dụng @keyframes Animation */
      .spinner-container {
        text-align: center;
      }

      .spinner {
        width: 40px;
        height: 40px;
        border: 4px solid #e0e0e0;
        border-top: 4px solid #008080;
        border-radius: 50%;
        /* Gọi animation xoay tròn lặp vô hạn */
        animation: spin 1s linear infinite;
      }

      @keyframes spin {
        0% {
          transform: rotate(0deg);
        }
        100% {
          transform: rotate(360deg);
        }
      }
    </style>
  </head>
  <body>
    <!-- Khối Card với Transition & Transform -->
    <div class="card">
      <img src="https://via.placeholder.com/280x160" alt="Demo Product" />
      <h3 style="margin: 12px 0 6px;">Trà Sữa Poly 3D</h3>
      <p style="color: #e53935; font-weight: bold;">35.000 VNĐ</p>
      <button class="btn-action">Thêm Vào Giỏ</button>
    </div>

    <!-- Khối Spinner với Animation -->
    <div class="spinner-container">
      <div class="spinner"></div>
      <p style="margin-top: 10px; font-size: 14px; color: #666;">
        Đang tải dữ liệu...
      </p>
    </div>
  </body>
</html>
```

---

## 5. 10 CÂU HỎI TRẮC NGHIỆM

**Câu 1**: Thuộc tính nào trong CSS3 Transition dùng để khai báo thời gian thực hiện chuyển động?

- A. `transition-delay`
- B. `transition-duration`
- C. `transition-timing-function`
- D. `transition-property`

**Câu 2**: Để phần tử xoay 90 độ theo chiều kim đồng hồ khi di chuột qua, ta dùng khai báo CSS nào?

- A. `transform: rotate(90deg);`
- B. `transition: rotate(90);`
- C. `transform: turn(90);`
- D. `animation: rotate(90deg);`

  **Câu 3**: Thuộc tính `transform: scale(1.5);` có tác dụng gì đối với phần tử HTML?

- A. Dịch chuyển phần tử sang phải 1.5px.
- B. Xoay phần tử 1.5 vòng.
- C. Phóng to kích thước phần tử lên 150% (gấp 1.5 lần).
- D. Làm mờ phần tử 50%.

**Câu 4**: Quy tắc CSS nào dùng để định nghĩa các mốc chuyển động (kịch bản) cho CSS Animation?

- A. `@keyframes`
- B. `@font-face`
- C. `@media`
- D. `@import`

**Câu 5**: Để một CSS Animation lặp đi lặp lại liên tục không bao giờ dừng, ta thiết lập thuộc tính `animation-iteration-count` giá trị nào?

- A. `loop`
- B. `repeat`
- C. `infinite`
- D. `always`

**Câu 6**: Sự khác biệt cốt lõi giữa CSS Transition và CSS Animation là gì?

- A. Transition không thể đổi màu sắc, Animation thì có.
- B. Transition cần sự kiện kích hoạt (như `:hover`), trong khi Animation có thể tự động chạy và lặp lại nhiều mốc phức tạp.
- C. Transition chỉ chạy được trên điện thoại, Animation chỉ chạy trên máy tính.
- D. Hai thuộc tính này hoàn toàn giống hệt nhau.

**Câu 7**: Thuộc tính `animation-fill-mode: forwards;` có ý nghĩa gì sau khi animation kết thúc?

- A. Đưa phần tử quay trở lại trạng thái ban đầu trước khi chạy animation.
- B. Giữ nguyên trạng thái kiểu dáng của mốc cuối cùng (100% / to).
- C. Xóa bỏ phần tử khỏi giao diện.
- D. Tự động phát lại từ đầu.

**Câu 8**: Hàm `translate(-50%, -50%)` kết hợp với `position: absolute; top: 50%; left: 50%;` thường được dùng để làm gì?

- A. Căn giữa tuyệt đối một phần tử cả chiều ngang lẫn chiều dọc.
- B. Phóng to phần tử gấp 2 lần.
- C. Ẩn phần tử khỏi màn hình.
- D. Đẩy phần tử về góc trên cùng bên trái.

**Câu 9**: Giá trị `transition-timing-function: linear;` khiến chuyển động diễn ra như thế nào?

- A. Bắt đầu chậm, giữa nhanh, cuối chậm.
- B. Tốc độ chuyển động đều đặn từ đầu đến cuối không đổi.
- C. Bắt đầu rất nhanh rồi dừng đột ngột.
- D. Chuyển động giật cục theo từng bước.

**Câu 10**: Thuộc tính `transform-origin: top left;` có tác dụng gì?

- A. Thay đổi điểm mốc xoay/co giãn của phần tử về góc trên bên trái.
- B. Di chuyển phần tử về góc trên bên trái màn hình.
- C. Đặt màu nền cho góc trên bên trái.
- D. Căn chỉnh chữ về bên trái.
