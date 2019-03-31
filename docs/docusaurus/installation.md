---
id: installation
title: Cài đặt
---

Docusaurus giúp bạn cài và chạy website tài liệu một cách nhanh chóng.

## Cài đặt Docusaurus
Facebook đã tạo một script để việc cài đặt cực kỳ dễ dàng:

1. Đảm bảo rằng bạn đã cài đặt phiên bản [Node](https://nodejs.org). Họ cũng khuyến khích bạn cài [Yarn](https://yarnpkg.com/en/docs/install):
> Bạn phải có Node >= 8.x và Yarn >= 15.

2. Tạo project nếu chưa tồn tại và truy cập vào thư mục gốc của project `cd your-project-root`.

Tại đây bạn sẽ tạo thư mục **docs** nơi chứa các tài liệu. Thư mục gốc cũng có thể chứa các file khác tuỳ bạn. Script cài đặt Docusaurus sẽ tạo ra 2 thư mục `docs-examples-from-docusaurus` và `website`.

> Thông thường một dự án hiện hữu hoặc tạo mới một Github project sẽ là nơi cho trang Docusaurus của bạn nhưng không bắt buộc bạn dùng Docusaurus.

3. Chạy lệnh cài đặt Docusaurus `npx docusaurus-init`.

> Nếu bạn không có Node phiên bản từ 8.2 hoặc nếu bạn muốn cài đặt Docusaurus toàn cục (global) thì chạy `yarn global add docusaurus-init` hoặc `npm install --global docusaurus-init`. Sau đó chạy `docusaurus-init`

## Kiểm tra việc cài đặt

Cùng với các file và thư mục trước đó trong thư mục gốc thì giờ cấu trúc thư mục của bạn có thể tương tự như sau:

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

## Chạy thử

Sau khi chạy script cài đặt `docusaurus-init` bạn đã có thể chạy thử website của mình với một số tài liệu mẫu. Để chạy:

1. Trong thư mục gốc, đổi tên `docs-examples-from-docusaurus` thành `docs`.
2. `cd website`
3. Đổi tên `blog-examples-from-docusaurus` thành `blog`.
4. Bên trong thư mục `website` chạy lệnh `yarn start` hoặc `npm start`.
4. Truy cập website của bạn tại địa chỉ [http://localhost:3000](http://localhost:3000) nếu máy bạn không tự động mở.
5. Bạn sẽ nhìn thấy website mẫu trên trình duyệt. Ở đây thì LiveReload server cũng chạy và bất kỳ thay đổi nào với các tài liệu của bạn hoặc các tập tin bên trong thư mục website sẽ làm server refresh bạn sẽ nhìn thấy thay đổi.

![Cài đặt Docusaurus](https://docusaurus.io/img/getting-started-preparation-verify.png)

### Chạy server đằng sau proxy

Nếu như máy bạn nằm sau proxy công ty, bạn cần phải vô hiệu hoá nó bằng cách sử dụng biến môi trường `NO_PROXY`

    SET NO_PROXY=localhost
    yarn start (or npm run start)

## Cập nhật phiên bản Docusaurus của bạn

Sau khi cài đặt Docusaurus, bất kỳ khi nào bạn cũng có thể kiểm tra phiên bản hiện hành của Docusaurus bằng cách vào thư mục `website` và chạy `yarn outdated docusaurus` hoặc `npm outdated docusaurus`:

    $ yarn outdated
    Using globally installed version of Yarn
    yarn outdated v1.5.1
    warning package.json: No license field
    warning No license field
    info Color legend :
     "<red>"    : Major Update backward-incompatible updates
     "<yellow>" : Minor Update backward-compatible features
     "<green>"  : Patch Update backward-compatible bug fixes
    Package    Current Wanted Latest Package Type    URL
    docusaurus 1.0.9   1.2.0  1.2.0  devDependencies https://github.com/facebook/Docusaurus#readme
    ✨  Done in 0.41s.

> Nếu bạn không thấy thông báo nào từ lệnh `outdated`, bạn đang có phiên bản cao nhất.

Bạn có thể cập nhật phiên bản mới nhất bằng cách

    yarn upgrade docusaurus --latest

hoặc

    npm update docusaurus

Nếu bạn thấy rằng mình gặp lỗi sau khi nâng cấp, hãy thử xoá bộ nhớ cách của Babel thường trong [temporary directory](https://babeljs.io/docs/en/babel-register/#environment-variables) hoặc chạy Docusaurus server (`yarn start`) với `BABEL_DISABLE_CACHE=1`.

    
