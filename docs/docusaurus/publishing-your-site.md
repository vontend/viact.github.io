---
id: publishing-your-site
title: Xuất bản website
---

Bây giờ bạn đã có một website đã chạy trên localhost. Một khi bạn tuỳ chỉnh nó theo ý thích của mình, đến lúc phải xuất bản nó chứ đúng ko nào. Docusaurus tạo ra một website html tĩnh để up lên server hoặc hosting.

## Tạo trang HTML tĩnh

Để tạo trang tĩnh cho website của bạn, chạy script sau bên trong thư mục `website`:

    yarn run build # hoặc `npm run build`

Lệnh này sẽ tạo ra một thư mục `build` bên trong thư mục `website` chứa các tệp `.html` từ tất cả các tài liệu và các trang bên trong thư mục `pages`.

## Host web của bạn

Bây giờ bạn có thể lấy tất cả file bên trong thư mục `website/build` và up lên server và host của mình.

> Ví dụ, cả Apache và Nginx đều mặc định truy cấp vào folder `/var/www/html`. Điều này nghĩa là việc sử dụng web server nào là cũng được, nằm ngoài phạm vi của Docusaurus.

> Khi bạn up website lên web server của bạn, đảm bảo rằng web server sẽ trả về các file asset với HTTP header thích hợp. Các tệp CSS phải có header `content-type` là `text/css`. Với nginx, nghĩa là bạn phải cấu hình `include /etc/nginx/mime.types;` trong `nginx.conf`. Xem [issue](https://github.com/facebook/Docusaurus/issues/602) này để có thêm thông tin.

## Host web trên các dịch vụ

* Github Pages
* Netlify

### Sử dụng Github Pages

Docusaurus được thiết kế để có thể host trên hầu hết bất kỳ máy chủ web nào, điển hình là [Github Pages](https://pages.github.com/).

#### Xuất bản lên Github Pages

1. Docusaurus hỗ trợ xuất bản mà repository của bạn không nhất thiết phải là public.

> Nếu repository là private, tất cả những gì ở branch `gh-pages` sẽ là public.

**Chú ý**: Khi bạn triển khai dưới dạng trang người dùng/tổ chức, script xuất bản sẽ được triển khai đến thư mục gốc  nhánh **`master`** của repo `username.github.io`. Trong trường hợp này, bạn nên đặt toàn bộ source code ở một nhánh khác, hoặc thậm chí là một repo khác.

2. Bạn cần phải điều chỉnh tệp `website/siteConfig.js` và thêm vào một số tham số bắt buộc.

| Tên | Chú thích    |
| :------------- | :------------- |
| `organizationname`| Tên người dùng hoặc tổ chức sở hữu repo, nếu bạn là người sở hữu repo thì đó là tên người dùng Github của bạn như trường hợp của Docusaurus thì đó là tên tổ chức "*facebook*" |
| `projectName` | Tên của repo cho dự án của bạn. Ví dụ source code của Docusaurus được host tại  https://github.com/facebook/docusaurus, vì vậy tên project sẽ là "docusaurus" |
| `url` | URL của website bạn trên Github như "*https://username.github.io*" |
| `baseUrl` | URL cơ sở cho project. Đối với các dự án host trên Github, nó dùng định dạng "*/projectName/*", với https://github.com/facebook/docusaurus, `baseUrl` là `/docusaurus/` |

    const siteConfig = {
      ...
      url: 'https://__userName__.github.io', // Your website URL
      baseUrl: '/testProject/',
      projectName: 'testProject',
      organizationName: 'userName'
      ...
    }

Trong trường hợp bạn triển khai với trang người dùng hoặc tổ chức thì `projectName` là `<username>.github.io` hoặc `<orgname>.github.io`. Ví dụ: Nếu Github username là `user42` thì là `user42.github.io`, hoặc trong trường hợp một tổ chức tên `org123` thì là `org123.github.io`.

**Chú ý**: Thiết lập sai `url` và `baseUrl` sẽ gây ra lỗi với các file tĩnh đã được khởi tạo.

> Mặc dù chúng tôi khuyên bạn nên tự đặt tên dự án trong `projectName` và `organizationName` trong `siteConfig.js`, bạn vẫn có thể dùng các biến môi trường `ORGANIZATION_NAME` và `PROJECT_NAME`.

3. Bây giờ bạn phải chỉ định người dùng git làm biến môi trường và chạy `publish-gh-pages`.

| Te6n | Chú thích |
| :------------- | :------------- |
| GIT_USER | Tên người dùng Github có quyền truy cập vào repo . Với repo của cá nhân bạn, đây thường là tên người dùng Github của bạn. GIT_USER được chỉ định phải có quyền truy cập **push** lên repo chỉ định trong sự kết hợp của `organizationName` và `projectName` |

Để chạy script trực tiếp từ command-line, bạn có thể sử dụng như sau, thay các giá trị phù hợp với bạn:

    GIT_USER=<GIT_USER> \
      CURRENT_BRANCH=master \
      USE_SSH=true \
      yarn run publish-gh-pages # or `npm run publish-gh-pages`

Ngoài ra còn hai biến môi trường khác được sử dụng:

| Tên | Chú thích |
| :------------- | :------------- |
| USE_SSH | Nếu bằng `true` thì SSH sẽ được sử dụng thay vì HTTPS cho việc kết nối tới Github repo. Mặc định HTTPS được sử dụng nếu biến này không set. |
| CURRENT_BRANCH | Branch chứa tài liệu sẽ được triển khai. Thường thì nhánh `master`, nhưng nó cũng có thể là bất kỳ nhánh nào khác trừ nhánh `gh-pages`. Nếu không set biến này thì nhánh hiện tại sẽ được dùng. |

Nếu bạn chạy mà gặp lỗi liên quan tới SSH key, truy cập [Github's authentication](https://help.github.com/articles/connecting-to-github-with-ssh/).

Giờ bạn đã có thể truy cập Github Page URL của mình, dạng như là https://username.github.io/projectName hoặc một tên miền tuỳ chỉnh mà bạn đã setup. Ví dụ Docusaurus có URL là https://facebook.github.io/Docusaurus vì nó được host trên nhánh `gh-pages` của Github repo https://github.com/facebook/docusaurus tuy nhiên bạn cũng có thể truy cập thông qua `https://docusaurus.io`, tên miền tuỳ chỉnh này đã được Facebook thiết lập.

Chúng tôi khuyến khích bạn nên đọc qua [Tài liệu Github Pages](https://pages.github.com/) để hiểu hơn về cách hoạt động này.

Bạn có thể chạy lệnh trên bất kỳ khi nào để cập nhật tài liệu hoặc muốn tạo ra thay đổi với website của mình. Chạy lệnh này theo cách thủ công có thể tốt cho các trang web mà tài liệu ít có thay đổi và không quá bất tiện để ghi nhớ nhằm triển khai các thay đổi theo cách thủ công.

Tuy nhiên bạn cũng có thể xuất bạn bằng quá trình tích hợp liên tục (Continuous Integration - CI).
