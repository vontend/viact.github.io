---
id: site-preparation
title:  Chuẩn bị website
---

Sau khi cài đặt, bây giờ bạn đã khung sườn của một website. Bài viết này sẽ thảo luận về cấu trúc của Docusaurus để bạn chuẩn bị xây dựng website của mình.

## Cấu trúc thư mục

Như Facebook đã show cho bạn cấu trúc thư mục sau khi cài đặt sẽ tương tự như sau:

    root-directory
    ├── docs-examples-from-docusaurus
    │   ├── doc1.md
    │   ├── doc2.md
    │   ├── doc3.md
    │   ├── exampledoc4.md
    │   └── exampledoc5.md
    └── website
        ├── blog-examples-from-docusaurus
        │   ├── 2016-03-11-blog-post.md
        │   ├── 2017-04-10-blog-post-two.md
        │   ├── 2017-09-25-testing-rss.md
        │   ├── 2017-09-26-adding-rss.md
        │   └── 2017-10-24-new-version-1.0.0.md
        ├── core
        │   └── Footer.js
        ├── package.json
        ├── pages
        ├── sidebars.json
        ├── siteConfig.js
        └── static

> Có thể bạn đã đổi tên `docs-examples-from-docusaurus` thành `docs` và `blog-examples-from-docusaurus` thành `blog` tại bước Kiểm tra cài đặt.

### Giải thích các thư mục

* **Nguồn file tài liệu**: Thư mục `docs-examples-from-docusaurus` chứa các tài liệu mẫu được viết bằng Markdown.
* **Blog**: Thư mục `website/blog-examples-from-docusaurus` chứa các file blog mẫu viết bằng Markdown.
* **Trang**: Thư mục `website/pages` chứa các trang mẫu ở cấp cao nhất của trang web.
* **Các file tĩnh và hình ảnh**: Thư mục `website/static` chứa các file asset mẫu được sử dụng bởi các nội dung mẫu mà Docusaurus tạo ra.

### Các file chính

* **Footer**: Tập tin `website/core/Footer.js` là một React Component hoạt động như footer của website tạo ra bởi Docusaurus và bạn nên tuỳ chỉnh nó.
* **Các file cấu hình**: Tập tin `website/siteConfig.js` là file cấu hình chính được sử dụng bởi Docusaurus.
* **Sidebar**: Tập tin `sidebars.json` chứa cấu trúc sắp xếp của các tài liệu.

## Ghi chú

Bạn cần phải giữ lại các tập tin `website/siteConfig.js` và `website/core/Footer.js` nhưng bạn có thể sửa chúng theo ý mình. Giá trị `customDocsPath` trong `website/siteConfig.js` có thể sửa nếu bạn muốn các tài liệu của mình nằm ở một thư mục khác. Thư mục `website` có thể đổi thành bất kỳ tên gì bạn muốn.

Tuy nhiên bạn phải giữ lại hai thư mục `website/pages` và `website/static` và có thể thay đổi nội dung bên trong nó nếu bạn muốn. Ít nhất thì bạn cần có một file `en/index.js` hoặc `en/index.html` bên trong `website/pages` và một hình ảnh sử dụng như icon cho phần đầu trang trong `website/static`.
