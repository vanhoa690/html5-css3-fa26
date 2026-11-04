## BÀI GIỚI THIỆU MÔN HỌC & BÀI 1: GIỚI THIỆU HTML5

---

### GIỚI THIỆU MÔN HỌC

- **Tên môn học**: Thiết kế Web với HTML5 & CSS3 (Đào tạo theo chuẩn CDIO: _Thực học - Thực nghiệp_).
- **Mục tiêu cốt lõi**: Bỏ thói quen dựng layout bằng `<div>` phi ngữ nghĩa $\rightarrow$ Chuyển sang **Web Ngữ nghĩa (Semantic Web)** & **Responsive Web Design (RWD)**.
- **Lộ trình 8 bài**: HTML5 Basic $\rightarrow$ CSS Selector & Box Model $\rightarrow$ Flexbox Layout $\rightarrow$ Transition $\rightarrow$ Animation $\rightarrow$ RWD $\rightarrow$ Bootstrap $\rightarrow$ Dự án & Thi cuối kỳ.

---

### 1. CẤU TRÚC KHUNG HTML5 CHUẨN

```html
<!DOCTYPE html>
<html lang="vi">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>HTML5 Standard</title>
  </head>
  <body>
    <!-- Nội dung trang web -->
  </body>
</html>
```

⚡ **Mẹo nhớ nhanh**:

- Dòng 1: `<!DOCTYPE html>` (Cú pháp siêu gọn, không phân biệt hoa/thường).
- **Trình duyệt cũ (IE8 trở xuống)** không hiểu thẻ HTML5 $\rightarrow$ Dùng thư viện JavaScript **`HTML5Shiv`** để hỗ trợ.

---

### 2. 5 THẺ KHU VỰC LAYOUT (SEMANTIC TAGS)

#### Sơ Đồ Khung Bố Cục Trang Web

```text
+--------------------------------------------------+
|                  <header> (Logo, Title, Nav)     |
+--------------------------------------------------+
|                  <nav> (Menu liên kết)           |
+-----------------------------------+--------------+
|                                   |              |
|        <main> (Nội dung chính)    |   <aside>    |
|   +---------------------------+   |  (Sidebar,   |
|   |  <section> / <article>    |   |   Quảng cáo) |
|   +---------------------------+   |              |
+-----------------------------------+--------------+
|                  <footer> (Chân trang, Copyright)|
+--------------------------------------------------+
```

#### Bảng Tóm Tắt Chức Năng Cốt Lõi

| Thẻ            | Vai Trò                  | Quy Tắc Nhớ Nhanh                                            |
| :------------- | :----------------------- | :----------------------------------------------------------- |
| **`<header>`** | Đầu trang / Đầu bài viết | Chứa logo, tiêu đề (`<h1>`-`<h6>`), thông tin giới thiệu.    |
| **`<nav>`**    | Thanh điều hướng         | Tập hợp các liên kết menu chuyển trang (Navigation links).   |
| **`<main>`**   | Nội dung trung tâm       | **Chỉ được có DUY NHẤT 1 thẻ `<main>`** trên mỗi trang web.  |
| **`<footer>`** | Chân trang               | Chứa thông tin bản quyền (copyright), liên hệ, chính sách.   |
| **`<aside>`**  | Nội dung phụ (Sidebar)   | Đặt bên cạnh nội dung chính (Quảng cáo, bài viết xem nhiều). |

---

### 3. PHÂN BIỆT `<section>` VS `<article>` (CÔNG THỨC 1 CÂU)

💡 **Công thức ghi nhớ thuộc lòng**:

> - **`<section>`** = **Phân đoạn logic** theo chủ đề (Thường bắt buộc có tiêu đề `<h2>`-`<h6>`).
> - **`<article>`** = **Bài viết độc lập** (Tách ra đăng trang khác người đọc vẫn hiểu đầy đủ).

#### So Sánh Nhanh

| Tiêu Chí     | `<section>`                             | `<article>`                                  |
| :----------- | :-------------------------------------- | :------------------------------------------- |
| **Bản chất** | Gom nhóm nội dung cùng chủ đề           | Khối nội dung tự hoàn chỉnh (Self-contained) |
| **Ví dụ**    | Khối "Giới thiệu", "Dịch vụ", "Liên hệ" | Bài báo, Bài post blog, Bình luận, Sản phẩm  |
| **Độc lập**  | ❌ Tách rời ra sẽ mất ngữ cảnh          | ✅ Tách rời ra vẫn giữ nguyên ý nghĩa        |

---

### 4. FORM 2.0: INPUT & THUỘC TÍNH MỚI

#### 4.1 Thuộc Tính Mới Của Input

- **`placeholder="..."`**: Chữ gợi ý mờ trong ô input (tự mất khi gõ).
- **`required`**: Bắt buộc nhập (chặn submit nếu bỏ trống).
- **`autofocus`**: Tự động đưa con trỏ chuột vào ô khi vừa mở trang.
- **`multiple`**: Chọn nhiều file (cho `type="file"`) hoặc nhiều email.

#### 4.2 Bảng Tra Cứu Kiểu Input (`type="..."`)

| `type="..."` | Chức Năng                           | Code Mẫu Siêu Gọn                                          |
| :----------- | :---------------------------------- | :--------------------------------------------------------- |
| **`email`**  | Kiểm tra tự động cấu trúc email     | `<input type="email" placeholder="a@fpt.edu.vn" required>` |
| **`date`**   | Hộp thoại chọn Ngày/Tháng/Năm       | `<input type="date">`                                      |
| **`time`**   | Hộp thoại chọn Giờ/Phút             | `<input type="time">`                                      |
| **`color`**  | Cửa sổ chọn màu (Mã Hex `#RRGGBB`)  | `<input type="color" value="#008080">`                     |
| **`number`** | Nhập số (dùng `min`, `max`, `step`) | `<input type="number" min="1" max="10" value="1">`         |
| **`range`**  | Thanh trượt chọn giá trị            | `<input type="range" min="1" max="100" value="50">`        |

---

### 5. THẺ MEDIA: `<video>` & `<audio>`

#### Cú Pháp Chuẩn Nhớ Nhanh

```html
<!-- Thẻ Video -->
<video width="320" height="240" controls poster="thumb.jpg">
  <source src="video.mp4" type="video/mp4" />
  Trình duyệt không hỗ trợ video.
</video>

<!-- Thẻ Audio -->
<audio controls autoplay muted>
  <source src="song.mp3" type="audio/mpeg" />
  Trình duyệt không hỗ trợ audio.
</audio>
```

#### Bảng 5 Thuộc Tính Vàng

| Thuộc Tính     | Công Dụng                                                                 |
| :------------- | :------------------------------------------------------------------------ |
| **`controls`** | **Bắt buộc có** để hiện thanh điều khiển Play/Pause/Volume.               |
| **`autoplay`** | Tự động phát ngay khi trang load xong.                                    |
| **`loop`**     | Tự động phát lặp lại liên tục.                                            |
| **`muted`**    | Tắt tiếng mặc định (cần thiết nếu muốn `autoplay` chạy mượt trên Chrome). |
| **`poster`**   | Ảnh đại diện cho `<video>` trước khi người dùng nhấn Play.                |

---

### 6. BÀI TẬP THỰC HÀNH XUYÊN SUỐT (LIỀN MẠCH - SÁT ĐỀ THI)

#### Đề bài: Dựng trang "Hồ Sơ Cá Nhân & Đăng Ký Học Viên" chuẩn HTML5 đầy đủ Semantic + Form 2.0 + Media.

```html
<!DOCTYPE html>
<html lang="vi">
  <head>
    <meta charset="UTF-8" />
    <title>Hồ Sơ & Đăng Ký Học Viên</title>
  </head>
  <body>
    <!-- 1. Header -->
    <header>
      <h1>FPT POLYTECHNIC - LẬP TRÌNH WEB HTML5</h1>
    </header>

    <!-- 2. Navigation -->
    <nav>
      <a href="#about">Giới thiệu</a> | <a href="#media">Media</a> |
      <a href="#register">Đăng ký</a>
    </nav>

    <!-- 3. Main Content -->
    <main>
      <!-- Khối Giới Thiệu -->
      <section id="about">
        <h2>Giới Thiệu</h2>
        <article>
          <h3>Xu hướng Web Ngữ Nghĩa HTML5</h3>
          <p>
            Nắm vững Semantic Tag giúp website đạt chuẩn SEO và thiết kế
            Responsive.
          </p>
        </article>
      </section>

      <!-- Khối Media -->
      <section id="media">
        <h2>Góc Đa Phương Tiện</h2>
        <video width="300" controls poster="thumb.jpg">
          <source src="demo.mp4" type="video/mp4" />
        </video>
        <audio controls>
          <source src="music.mp3" type="audio/mpeg" />
        </audio>
      </section>

      <!-- Khối Form 2.0 -->
      <section id="register">
        <h2>Form Đăng Ký Thành Viên</h2>
        <form action="#" method="POST">
          <p>
            Họ và tên:
            <input type="text" placeholder="Nguyễn Văn A" autofocus required />
          </p>
          <p>
            Email liên hệ:
            <input type="email" placeholder="a@fpt.edu.vn" required />
          </p>
          <p>Ngày sinh: <input type="date" required /></p>
          <p>Giờ học mong muốn: <input type="time" /></p>
          <p>
            Số năm kinh nghiệm (1-5):
            <input type="number" min="1" max="5" value="1" />
          </p>
          <p>
            Mức độ tự tin HTML5 (1-10):
            <input type="range" min="1" max="10" value="8" />
          </p>
          <p>Màu giao diện thích: <input type="color" value="#008080" /></p>
          <p>Ảnh đại diện: <input type="file" multiple /></p>
          <button type="submit">Đăng Ký</button>
          <button type="reset">Làm Lại</button>
        </form>
      </section>
    </main>

    <!-- 4. Aside -->
    <aside>
      <h3>Khóa Học Nổi Bật</h3>
      <p>CSS3, JavaScript ES6, ReactJS Front-End.</p>
    </aside>

    <!-- 5. Footer -->
    <footer>
      <p>&copy; 2026 FPT Polytechnic. All rights reserved.</p>
    </footer>
  </body>
</html>
```

---

#### 7. ÔN LẠI 10 CÂU TRẮC NGHIỆM CỐT LÕI

1. **Thẻ khai báo chuẩn HTML5 là gì?**  
   $\rightarrow$ `<!DOCTYPE html>`
2. **Thẻ bao bọc nội dung trung tâm duy nhất trên trang?**  
   $\rightarrow$ `<main>` (Quy tắc: Chỉ có **duy nhất 1** thẻ `<main>` / trang).
3. **Phân biệt `<article>` và `<section>`?**  
   $\rightarrow$ `<article>` là bài viết độc lập tự chứa; `<section>` là nhóm nội dung theo chủ đề.
4. **Thuộc tính tự động đưa con trỏ chuột vào ô input khi load trang?**  
   $\rightarrow$ `autofocus`
5. **Kiểu input hiển thị thanh trượt chọn giá trị?**  
   $\rightarrow$ `type="range"`
6. **Thuộc tính cho phép chọn nhiều file trong `<input type="file">`?**  
   $\rightarrow$ `multiple`
7. **Thư viện JavaScript hỗ trợ thẻ HTML5 cho IE8 cũ?**  
   $\rightarrow$ `HTML5Shiv`
8. **Thuộc tính cài ảnh đại diện cho `<video>` trước khi phát?**  
   $\rightarrow$ `poster="URL"`
9. **3 định dạng âm thanh được hỗ trợ phổ biến trong `<audio>`?**  
   $\rightarrow$ MP3, WAV, OGG
10. **Thuộc tính bắt buộc nhập dữ liệu trong Form?**  
    $\rightarrow$ `required`

---

#### 5 QUY TẮC "ĂN ĐIỂM" KHI LÀM BÀI THI THỰC HÀNH

1. **Dòng 1 luôn khai báo**: `<!DOCTYPE html>`.
2. **Tuyệt đối không lạm dụng `<div>`**: Dùng chuẩn các thẻ `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`.
3. **Thẻ `<video>` & `<audio>` luôn phải have thuộc tính `controls`** (nếu thiếu sẽ không bấm Play được).
4. **Khai báo thuộc tính Form chuẩn xác**: Thêm `required` cho các ô bắt buộc, `placeholder` để gợi ý.
5. **Trình bày code sạch đẹp**: Thụ đầu dòng lùi lề phân cấp rõ ràng để giám thị dễ chấm điểm.

#### 7.1 Bộ 10 Câu Hỏi Trắc Nghiệm

**Câu 1**: Thẻ khai báo nào sau đây xác định tài liệu chuẩn HTML5?

- A. `<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN">`
- B. `<!DOCTYPE html>`
- C. `<html html5="true">`
- D. `<meta version="5.0">`

**Câu 2**: Thẻ ngữ nghĩa nào đại diện cho phần nội dung chính duy nhất của trang web?

- A. `<section>`
- B. `<article>`
- C. `<main>`
- D. `<body>`

**Câu 3**: Điểm khác biệt cốt lõi giữa thẻ `<article>` và `<section>` là gì?

- A. Thẻ `<article>` chỉ dùng cho ảnh, thẻ `<section>` dùng cho văn bản.
- B. Thẻ `<article>` chứa nội dung độc lập có thể phân phối riêng, thẻ `<section>` chia khối nội dung logic theo chủ đề.
- C. Thẻ `<section>` bắt buộc phải nằm trong thẻ `<article>`.
- D. Hai thẻ này hoàn toàn giống nhau, chỉ khác tên gọi.

**Câu 4**: Thuộc tính nào của thẻ `<input>` tự động đưa con trỏ chuột vào ô nhập liệu khi trang vừa tải xong?

- A. `placeholder`
- B. `required`
- C. `autofocus`
- D. `autocomplete`

**Câu 5**: Kiểu input nào cung cấp giao diện thanh trượt để chọn giá trị số trong khoảng?

- A. `type="number"`
- B. `type="range"`
- C. `type="color"`
- D. `type="progress"`

**Câu 6**: Thuộc tính nào cho phép chọn nhiều tệp cùng lúc trong ô `<input type="file">`?

- A. `multi="true"`
- B. `select-all`
- C. `multiple`
- D. `allow-many`

**Câu 7**: Thư viện JavaScript nào hỗ trợ hiển thị thẻ ngữ nghĩa HTML5 trên các trình duyệt cũ như IE8?

- A. jQuery
- B. Bootstrap
- C. HTML5Shiv
- D. Modernizr

**Câu 8**: Thuộc tính nào trong thẻ `<video>` dùng để cài đặt ảnh đại diện hiển thị trước khi phát video?

- A. `src`
- B. `thumb`
- C. `poster`
- D. `preview`

**Câu 9**: Các định dạng âm thanh nào sau đây được hỗ trợ phổ biến bởi thẻ `<audio>` trong HTML5?

- A. MP3, WAV, OGG
- B. WMA, FLAC, MIDI
- C. AVI, MP4, MOV
- D. ACC, AIFF, M4A

**Câu 10**: Để bắt buộc người dùng không được bỏ trống dữ liệu khi gửi Form, ta dùng thuộc tính nào?

- A. `validate`
- B. `required`
- C. `not-null`
- D. `check`

---
