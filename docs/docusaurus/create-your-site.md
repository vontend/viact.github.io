---
id: create-your-site
title: Tạo site của bạn
---

Docusaurus được tạo ra với hi vọng làm một site siêu đơn giản cho việc phát triển tài liệu dự án của bạn.

Sau khi cài đặt và chuẩn bị site, gần như các công việc cơ bản để tạo nên website tại liệu của bạn đã hoàn tất.

## Cấu trúc website

    root-directory
    ├── docs
    └── website
        ├── blog
        ├── core
        │   └── Footer.js
        ├── package.json
        ├── pages
        ├── sidebars.json
        ├── siteConfig.js
        └── static

> Ở đây giả định rằng bạn đã xoá tất cả các file tài liệu mẫu `.md` được cài đặt khi chạy script khởi tạo dự án.

Tất cả tài liệu của bạn nên được chứa trong thư mục `docs` dưới dạng tập tin Markdown `.md`. Tất cả các blog nên được viết bên trong thư mục `blog`.

> Các bài blog phải được đặt tên theo đúng định dạng `YYYY-MM-DD-your-file-name.md`.

## Tạo site cơ bản

Để tạo một trang đầy đủ chức năng, bạn chỉ cần thực hiện các bước sau đây:

1. Tạo tài liệu của bạn bên trong thư mục `docs` với định dạng `.md`. Đảm bảo rằng bạn có tiêu đề phù hợp trong mỗi tệp. Tiêu đề đơn giản nhất như trong ví dụ sau đây, `id` là tên link (Ví dụ: `docs/intro.html`) và `title` là tiêu đề của website:

    ---
    id: intro
    title: Getting Started
    ---

    My new content here..

2. Thêm hoặc không thêm tài liệu vào `sidebars.json` để tài liệu được hiển thị trên sidebar.

> Nếu bạn không thêm tài liệu vào `sidebars.json`, tài liệu vẫn được render nhưng chúng chỉ có thể được link từ tài liệu khác hoặc được truy cập bằng cách dùng một URL cho trước.

3. Chỉnh sửa tệp `website/siteConfig.js` để cấu hình website, làm theo hướng dẫn của những dòng comment bên trong tệp này.

4. Tạo một trang tuỳ chỉnh và/hoặc tuỳ chỉnh `website/core/Footer.js` hiển thị footer của web bạn.

5. Tạo ra các asset ví dụ như hình ảnh bên trong thư mục `website/static`.

6. Chạy website mà bạn vừa sửa.

    cd website
    yarn run start // or `npm run start`

## Tuỳ chỉnh đặc biệt

### Landing page

Nếu bạn muốn Landing page của mình đi thẳng vào một tài liệu nào đó thì có thể dùng redirect.

1. Xoá tệp `index.js` bên trong `website/pages` nếu nó tồn tại.

2. Tạo một trang `index.html` tĩnh bên trong thư mục `website/static` với nội dung:

    ```<!DOCTYPE HTML>
    <html lang="en-US">
      <head>
        <meta charset="UTF-8">
        <meta http-equiv="refresh" content="0; url=docs/id-of-doc-to-land-on.html">
        <script type="text/javascript">
          window.location.href = 'docs/id-of-doc-to-land-on.html';
        </script>
        <title>Your Site Title Here</title>
      </head>
      <body>
        If you are not redirected automatically, follow this <a href="docs/id-of-doc-to-land-on.html">link</a>.
      </body>
    </html>
    ```
> Chèn `id` của tài liệu mà bạn muốn truy cập vào code bên trong thẻ script phía trên.

### Thuần blog

Bạn có thể sử dụng Docusaurus để tạo một trang Thuần blog.
