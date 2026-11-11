# BÀI 2: CSS, SELECTOR, BOX MODEL & TEXT

---

## 1. 3 CÁCH NHÚNG CSS & ĐỘ ƯU TIÊN

### 1.1 Bảng So Sánh 3 Cách Nhúng

| Cách Nhúng               | Cú Pháp Mẫu                                | Đánh Giá                                |
| :----------------------- | :----------------------------------------- | :-------------------------------------- |
| **Inline** (Trực tiếp)   | `<h1 style="color: red;">`                 | Trùng lặp code, khó quản lý             |
| **Internal** (Nội bộ)    | `<style> h1 { color: red; } </style>`      | Chỉ dùng cho 1 trang                    |
| **External** (Ngoại bọc) | `<link rel="stylesheet" href="style.css">` | ✅ **Chuẩn doanh nghiệp** (Tái sử dụng) |

### 1.2 Công Thức Độ Ưu Tiên (Thấp $\rightarrow$ Cao)

> `*` (Thấp nhất) $\rightarrow$ **Element** (`p`) $\rightarrow$ **Class** (`.btn`) $\rightarrow$ **ID** (`#id`) $\rightarrow$ **Inline Style** $\rightarrow$ **`!important`** (Cao nhất)

---

## 2. BỘ CHỌN CSS (SELECTORS)

### 2.1 Bộ Chọn Cơ Bản

| Bộ Chọn       | Ký Hiệu      | Ví Dụ                           | Ý Nghĩa                             |
| :------------ | :----------- | :------------------------------ | :---------------------------------- |
| \*\*Universal | `*`          | `* { box-sizing: border-box; }` | Chọn tất cả phần tử                 |
| **Element**   | `tên_thẻ`    | `p { color: #333; }`            | Chọn theo tên thẻ HTML              |
| **Class**     | `.tên_class` | `.btn { background: green; }`   | Chọn theo class (Dùng nhiều lần)    |
| **ID**        | `#tên_id`    | `#logo { width: 100px; }`       | Chọn theo ID (**Duy nhất** 1 trang) |

### 2.2 Bộ Chọn Kết Hợp & Giả Lập

- **`div p`** (Descendant): Chọn tất cả `<p>` nằm trong `<div>`.
- **`div > p`** (Child): Chỉ chọn `<p>` là **con trực tiếp** cấp 1 của `<div>`.
- **`a:hover`**: Kích hoạt khi **rê chuột** qua thẻ `<a>`.
- **`li:nth-child(2)`**: Chọn phần tử `<li>` thứ 2 trong danh sách.
- **`p::before` / `p::after`**: Chèn nội dung giả vào trước/sau `<p>`.

---

## 3. BOX MODEL & BÍ KÍP `border-box`

### 3.1 Sơ Đồ Box Model Mini

```text
+-----------------------------------+
| MARGIN (Lề ngoài)                |
|   +---------------------------+   |
|   | BORDER (Viền)             |   |
|   |   +-------------------+   |   |
|   |   | PADDING (Đệm trong)|   |   |
|   |   |   +-----------+   |   |   |
|   |   |   | CONTENT   |   |   |   |
|   |   |   +-----------+   |   |   |
+---+---+---+-----------+---+---+---+
```

### 3.2 Bí Kíp Đi Thi: `content-box` vs `border-box`

- **`content-box`** (Mặc định): `Width thực = width + padding + border` $\rightarrow$ **Dễ vỡ layout**.
- **`border-box`**: `Width thực = width cố định` (Padding & border tự co vào trong) $\rightarrow$ ✅ **Luôn reset ở dòng 1 file CSS**:

```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

---

## 4. TEXT, FONT & BACKGROUND (CHEATSHEET 1 DÒNG)

- **`font-family`**: Họ font (`Arial, sans-serif`).
- **`font-size`**: Kích thước chữ (`16px`, `1.2rem`).
- **`text-align`**: Căn lề (`left`, `center`, `right`, `justify`).
- **`text-decoration: none;`**: Bỏ gạch chân mặc định của thẻ liên kết `<a>`.
- **Nhúng font ngoại**: `@font-face { font-family: 'MyFont'; src: url('font.woff2'); }`
- **`background-size`**: `cover` (phủ kín khung), `contain` (vừa vặn toàn bộ ảnh).

---

## 5. CODE MẪU THỰC HÀNH: CARD SẢN PHẨM HOVER ZOOM

```html
<!DOCTYPE html>
<html lang="vi">
  <head>
    <meta charset="UTF-8" />
    <title>Card Sản Phẩm</title>
    <style>
      * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
      }
      body {
        font-family: sans-serif;
        background: #f4f4f4;
        padding: 40px;
        display: flex;
        justify-content: center;
      }

      .card {
        width: 280px;
        background: #fff;
        border-radius: 8px;
        padding: 15px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        text-align: center;
        transition: transform 0.3s;
      }
      .card:hover {
        transform: translateY(-5px);
      } /* Hiệu ứng nảy khi hover */
      .card img {
        width: 100%;
        height: 160px;
        object-fit: cover;
        border-radius: 4px;
      }
      .title {
        font-size: 1.1rem;
        margin: 10px 0;
      }
      .price {
        color: e53935;
        font-weight: bold;
        margin-bottom: 10px;
      }
      .btn {
        display: inline-block;
        padding: 8px 16px;
        background: #008080;
        color: #fff;
        text-decoration: none;
        border-radius: 4px;
      }
    </style>
  </head>
  <body>
    <div class="card">
      <img src="product.jpg" alt="Sản phẩm" />
      <h3 class="title">Trà Thạch Vải Poly</h3>
      <p class="price">25.000 VNĐ</p>
      <a href="#" class="btn">Mua Ngay</a>
    </div>
  </body>
</html>
```

---

## 6. 10 CÂU TRẮC NGHIỆM ÔN THI (ĐÁP ÁN NHANH)

**Câu 1**: Cách nhúng CSS nào tốt nhất cho dự án thực tế?

- A. Inline | B. External | C. Internal | D. Import

**Câu 2**: Selector nào có độ ưu tiên cao nhất?

- A. `.class` | B. `#id` | C. `element` | D. `*`

**Câu 3**: Thuộc tính bỏ gạch chân thẻ `<a>`?

- A. `text-align: none;` | B. `font-style: none;` | C. `text-decoration: none;` | D. `text-transform: none;`

**Câu 4**: Thuộc tính `box-sizing: border-box;` giúp gì?

- A. Tăng gấp đôi width | B. Padding & border không làm tăng width tổng | C. Đẩy margin ra ngoài | D. Tự động đổi màu

**Câu 5**: Ký hiệu kích hoạt khi rê chuột vào phần tử?

- A. `:focus` | B. `:active` | C. `:hover` | D. `:visited`

**Câu 6**: Bộ chọn `div > p` dùng để chọn gì?

- A. Mọi thẻ `<p>` trong `<div>` | B. Chỉ thẻ `<p>` là con trực tiếp cấp 1 của `<div>` | C. Thẻ `<div>` sau `<p>` | D. Tất cả ngoại trừ `<div>`

**Câu 7**: Quy tắc nhúng font chữ tùy chỉnh vào CSS?

- A. `@import-font` | B. `@font-face` | C. `@keyframes` | D. `@include`

**Câu 8**: `background-size: cover;` có tác dụng gì?

- A. Phủ kín toàn bộ khung chứa | B. Thu nhỏ thấy hết ảnh | C. Lặp ảnh | D. Xóa ảnh

**Câu 9**: Lề nằm NGOÀI đường viền (Border) trong Box Model gọi là gì?

- A. Padding | B. Content | C. Margin | D. Spacing

**Câu 10**: Từ khóa có độ ưu tiên tuyệt đối cao nhất trong CSS?

- A. `!force` | B. `!important` | C. `!override` | D. `!primary`
