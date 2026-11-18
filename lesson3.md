# BÀI 3: BỐ CỤC TRANG WEB VỚI CSS FLOAT, POSITION & FLEXBOX

---

## 1. BỐ CỤC THEO PHƯƠNG PHÁP TRUYỀN THỐNG: CSS FLOAT & CLEARFIX

### 1.1 Thuộc Tính `float`

- **Tác dụng**: Đẩy phần tử sang bên trái (`float: left;`) hoặc bên phải (`float: right;`) để văn bản/phần tử khác bao quanh.
- **Hiện tượng trôi (Float collapse)**: Khi các phần tử con dùng `float`, phần tử cha sẽ bị mất chiều cao (height = 0).

## 2. QUẢN LÝ VỊ TRÍ PHẦN TỬ VỚI CSS POSITION

### 2.1 Bảng Tra Cứu 5 Giá Trị Position (CÔNG THỨC ĂN ĐIỂM THI)

| Position       | Vị Trí Làm Mốc                                        | Có Làm Mất Trôi (Flow)? | Ứng Dụng Thực Tế                   |
| :------------- | :---------------------------------------------------- | :---------------------- | :--------------------------------- |
| **`static`**   | Tự nhiên theo luồng web                               | Không                   | Mặc định của tất cả thẻ.           |
| **`relative`** | **Chính vị trí ban đầu** của nó                       | Không (vẫn giữ chỗ)     | Dùng làm mốc cho con `absolute`.   |
| **`absolute`** | **Cha gần nhất** có `position` khác `static`          | Có (bay khỏi luồng)     | Popup, Icon badge, Banner overlay. |
| **`fixed`**    | **Khung nhìn trình duyệt (Viewport)**                 | Có (cố định khi cuộn)   | Header cố định, Nút Back-to-top.   |
| **`sticky`**   | Cuộn bình thường $\rightarrow$ Dính chặt khi chạm mép | Không                   | Sticky Header, Sidebar danh mục.   |

> **Bí kíp**: Muốn con bay tự do theo cha $\rightarrow$ **Cha đặt `position: relative;`**, **Con đặt `position: absolute;`**.

### 2.2 Thuộc Tính `z-index`

- Quản lý **thứ tự chồng lấp** (trên/dưới) của phần tử.
- **Lưu ý**: `z-index` **chỉ có tác dụng** khi phần tử có `position` khác `static` (`relative`, `absolute`, `fixed`, `sticky`).

---

## 3. BỐ CỤC HIỆN ĐẠI: FLEXBOX LAYOUT (TRỌNG TÂM MÔN HỌC)

### Sơ Đồ Trục Flexbox

```text
                  Cross Axis (Trục Dọc)
                           ▲
                           │
Main Start ───►   [Item 1] [Item 2] [Item 3]   ───► Main End (Main Axis - Trục Chính)
                           │
                           ▼
                       Cross End
```

### 3.1 Thuộc Tính Dành Cho CHỦ HỘP (Flex Container)

| Thuộc Tính            | Các Giá Trị Phổ Biến                                                                          | Ý Nghĩa Nhớ Nhanh                                                |
| :-------------------- | :-------------------------------------------------------------------------------------------- | :--------------------------------------------------------------- |
| **`display: flex;`**  | `flex` \| `inline-flex`                                                                       | Kích hoạt mô hình Flexbox cho khối cha.                          |
| **`flex-direction`**  | `row` (ngang) \| `column` (dọc)                                                               | Xác định hướng chạy của **Trục Chính (Main Axis)**.              |
| **`justify-content`** | `flex-start` \| `center` \| `flex-end` \| `space-between` \| `space-around` \| `space-evenly` | Căn chỉnh các item theo **Trục Chính (Chiều ngang mặc định)**.   |
| **`align-items`**     | `stretch` (kéo giãn) \| `center` \| `flex-start` \| `flex-end` \| `baseline`                  | Căn chỉnh các item theo **Trục Vuông Góc (Chiều dọc mặc định)**. |
| **`flex-wrap`**       | `nowrap` (trên 1 dòng) \| `wrap` (cho phép xuống dòng)                                        | Xử lý khi tổng kích thước item vượt quá khung chứa.              |
| **`gap`**             | `10px`, `20px`                                                                                | Tạo khoảng cách giữa các flex item (không cần margin).           |

### 3.2 Thuộc Tính Dành Cho PHẦN TỬ CON (Flex Item)

| Thuộc Tính            | Ý Nghĩa Nhớ Nhanh                                      | Ví Dụ Cú Pháp                     |
| :-------------------- | :----------------------------------------------------- | :-------------------------------- |
| **`flex-grow`**       | Tỷ lệ **phóng to** chiếm khoảng trống còn thừa         | `flex-grow: 1;` (dãn đầy ô)       |
| **`flex-shrink`**     | Tỷ lệ **co lại** khi thiếu không gian                  | `flex-shrink: 0;` (không bị móp)  |
| **`flex-basis`**      | Kích thước ban đầu của item trước khi co dãn           | `flex-basis: 200px;`              |
| **`flex` (Viết tắt)** | Combined: `flex: <grow> <shrink> <basis>;`             | `flex: 1;` (Tương đương `1 1 0%`) |
| **`align-self`**      | Đè lại căn chỉnh `align-items` cho **duy nhất 1 item** | `align-self: flex-end;`           |

---

## 4. BÀI TẬP DỰNG LAYOUT WEBSITE ĐA CỘT HOÀN CHỈNH

### Yêu cầu: Dựng giao diện trang web gồm Header cố định (`fixed`), Menu + Layout 2 cột (Main & Sidebar) bằng `flexbox`, Footer ở dưới cùng.

```html
<!DOCTYPE html>
<html lang="vi">
  <head>
    <meta charset="UTF-8" />
    <title>Bài 3 - Layout Flexbox & Position</title>
    <style>
      * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
      }
      body {
        font-family: sans-serif;
        background: #f0f2f5;
        padding-top: 60px;
      }

      /* 1. Header cố định góc trên */
      header {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 60px;
        background: #008080;
        color: white;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 0 20px;
        z-index: 1000;
      }

      /* 2. Flex Layout chính 2 cột */
      .container {
        display: flex;
        gap: 20px;
        max-width: 1000px;
        margin: 20px auto;
        padding: 0 10px;
      }

      /* Cột chính chiếm phần lớn không gian */
      main {
        flex: 3;
        background: white;
        padding: 20px;
        border-radius: 8px;
      }

      /* Sidebar cố định tỷ lệ */
      aside {
        flex: 1;
        background: #ffffff;
        padding: 20px;
        border-radius: 8px;
        position: relative; /* Làm mốc cho badge con */
      }

      .badge {
        position: absolute;
        top: -10px;
        right: -10px;
        background: red;
        color: white;
        padding: 4px 8px;
        border-radius: 12px;
        font-size: 12px;
        font-weight: bold;
      }

      footer {
        text-align: center;
        padding: 20px;
        background: #333;
        color: white;
        margin-top: 20px;
      }
    </style>
  </head>
  <body>
    <header>
      <h2>Poly Web Layout</h2>
      <nav>
        <span>Home</span> | <span>Services</span> | <span>Contact</span>
      </nav>
    </header>

    <div class="container">
      <main>
        <h2>Nội Dung Chính (Flex: 3)</h2>
        <p>
          Dàn trang sử dụng Flexbox giúp bố cục tự co dãn linh hoạt trên mọi
          kích thước màn hình.
        </p>
      </main>
      <aside>
        <span class="badge">HOT</span>
        <h3>Sidebar (Flex: 1)</h3>
        <p>Khối phụ đặt góc phải với badge định vị Position Absolute.</p>
      </aside>
    </div>

    <footer>
      <p>&copy; 2026 FPT Polytechnic - Thiết kế Web HTML5 & CSS3</p>
    </footer>
  </body>
</html>
```

---

## 5. 10 CÂU HỎI TRẮC NGHIỆM

**Câu 1**: Trong CSS Position, giá trị nào khiến phần tử bị rút khỏi luồng thông thường và đặt vị trí dựa theo khung nhìn (Viewport) trình duyệt?

- A. `position: relative;`
- B. `position: absolute;`
- C. `position: fixed;`
- D. `position: static;`

**Câu 2**: Để định vị một phần tử con `position: absolute;` nằm chính xác theo góc của phần tử cha, phần tử cha cần thiết lập thuộc tính position nào?

- A. `position: static;`
- B. `position: relative;` (hoặc absolute/fixed)
- C. `position: inherit;`
- D. Không cần thiết lập gì.

**Câu 3**: Thuộc tính `z-index` chỉ có hiệu lực khi phần tử có khai báo nào sau đây?

- A. `display: block;`
- B. `float: left;`
- C. `position` có giá trị khác `static` (`relative`, `absolute`, `fixed`, `sticky`).
- D. `overflow: hidden;`

**Câu 4**: Thuộc tính Flexbox nào dùng để căn chỉnh các item theo trục chính (Main Axis - thường là chiều ngang)?

- A. `align-items`
- B. `justify-content`
- C. `align-content`
- D. `flex-direction`

**Câu 5**: Thuộc tính `align-items: center;` trong Flexbox có tác dụng gì khi `flex-direction: row;`?

- A. Dồn các item về góc phải.
- B. Căn giữa các item theo chiều ngang.
- C. Căn giữa các item theo chiều dọc (Trục vuông góc Cross Axis).
- D. Kéo giãn item phủ kín chiều cao.

**Câu 6**: Trong Flexbox, thuộc tính `flex: 1;` ở phần tử con là viết tắt của chuỗi thuộc tính nào?

- A. `flex-grow: 1; flex-shrink: 1; flex-basis: 0%;`
- B. `flex-direction: row; flex-wrap: wrap;`
- C. `justify-content: center; align-items: center;`
- D. `float: left; width: 100%;`

**Câu 7**: Để tạo khoảng cách giữa các phần tử con trong Flexbox Container mà không dùng margin, ta dùng thuộc tính nào?

- A. `spacing`
- B. `gap`
- C. `padding-between`
- D. `flex-margin`

**Câu 8**: Hiện tượng phần tử cha bị mất chiều cao (height = 0) khi các phần tử con sử dụng `float` gọi là gì và xử lý chuẩn nhất bằng cách nào?

- A. Overflow error $\rightarrow$ Dùng `position: fixed;`
- B. Float collapse $\rightarrow$ Dùng kỹ thuật `Clearfix` (`::after`)
- C. Flex wrap $\rightarrow$ Dùng `display: flex;`
- D. Box model bug $\rightarrow$ Dùng `border-box;`

**Câu 9**: Thuộc tính Flex item nào cho phép đè lại (override) quy tắc căn chỉnh `align-items` của container cha cho riêng một item?

- A. `align-content`
- B. `justify-self`
- C. `align-self`
- D. `flex-override`

**Câu 10**: Giá trị `flex-wrap: wrap;` có vai trò gì trong Flex Container?

- A. Ép tất cả các item nằm trên cùng 1 hàng duy nhất.
- B. Cho phép các item tự động xuống hàng mới khi không đủ chiều rộng container.
- C. Đảo ngược thứ tự các item từ phải sang trái.
- D. Tự động ẩn bớt các item bị tràn.
