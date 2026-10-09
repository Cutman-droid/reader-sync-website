# Reader Sync — Website cho Google OAuth Branding

Website tĩnh gồm 3 trang, viết bằng tiếng Việt, không cần npm, framework hay backend:

- `index.html` — Trang chủ giới thiệu Reader Sync
- `privacy.html` — Chính sách quyền riêng tư
- `terms.html` — Điều khoản sử dụng
- `styles.css` và `favicon.svg` — Giao diện

## BẮT BUỘC KIỂM TRA TRƯỚC KHI ĐĂNG

1. Tìm và thay **tất cả** `YOUR_EMAIL@example.com` bằng email hỗ trợ thật. Email này nên khớp với `User support email` đã đăng ký trong OAuth Branding.
2. Đọc và kiểm tra lại toàn bộ nội dung chính sách quyền riêng tư có phản ánh **đúng hành vi ứng dụng thật** hay không, đặc biệt:
   - Reader Sync đang yêu cầu scope `drive.appdata`, `drive.file` hay quyền rộng `drive`?
   - Có thực sự đồng bộ tiến độ, dấu trang, tùy chọn đọc và dữ liệu cấu hình không?
   - Token OAuth được lưu cục bộ hay gửi qua server? Có dịch vụ nào khác nhận dữ liệu?
   - Có log, analytics, quảng cáo, hoặc chuyển dữ liệu cho bên thứ ba không?
   - Có chức năng xóa dữ liệu đồng bộ trong ứng dụng không?
3. Nếu chưa biết câu trả lời, kiểm tra code Reader Sync **trước khi** dùng chính sách này để nộp Google. Đây là bản dự thảo, không phải cam kết đã được kiểm toán.
4. Không đặt client secret, refresh token, mã API hoặc khóa riêng vào website hay repository công khai.

## Đăng GitHub Pages

1. Đăng nhập https://github.com/ và tạo repository mới, ví dụ `reader-sync-site` (Public).
2. Giải nén và tải trực tiếp **các tệp trong thư mục** này vào thư mục gốc repository; chọn Commit changes.
3. Vào repository → **Settings → Pages** → Build and deployment: **Deploy from a branch** → Branch `main`, folder `/ (root)` → Save.
4. Khi site được phát hành, URL sẽ theo mẫu:
   - Homepage: `https://TEN_GITHUB.github.io/reader-sync-site/`
   - Privacy: `https://TEN_GITHUB.github.io/reader-sync-site/privacy.html`
   - Terms: `https://TEN_GITHUB.github.io/reader-sync-site/terms.html`
5. Nếu dùng tên miền riêng, cấu hình **Settings → Pages → Custom domain** và DNS theo hướng dẫn chính thức GitHub.

## Khai báo vào Google OAuth Branding

Trong https://console.cloud.google.com/auth/branding :

- **Application home page**: URL trang chủ (ví dụ `https://reader.example.com/`)
- **Application privacy policy link**: cùng domain + `/privacy.html`
- **Application terms of service link**: cùng domain + `/terms.html`
- **Authorized domains**: tên miền mà bạn kiểm soát, ví dụ `example.com`

**Quan trọng:** Google yêu cầu bạn chứng minh quyền sở hữu tên miền, thường bằng Google Search Console. Để xác minh OAuth thuận lợi, **khuyến nghị gắn tên miền riêng** do bạn sở hữu, chẳng hạn `reader.example.com`, với GitHub Pages, sau đó xác minh domain qua Google Search Console. Địa chỉ mặc định `github.io` có thể không đáp ứng được quy trình chứng minh quyền sở hữu cho mọi trường hợp Google OAuth; đừng coi đó là lựa chọn chắc chắn sẽ được duyệt.

Website cần công khai, sử dụng HTTPS và không bắt người xem đăng nhập. Cần kiểm tra cả nội dung, quyền OAuth và các yêu cầu xác minh ứng dụng của Google.

**Các thông tin này không phải giới hạn 7 ngày:** hạn 7 ngày của refresh token ở OAuth Testing là vấn đề riêng. Production không còn giới hạn Testing đó, nhưng refresh token vẫn có thể mất hiệu lực trong những trường hợp khác. Việc Publish và việc Google duyệt xác minh là hai bước khác nhau.

## Dùng lâu dài

GitHub Pages không có cơ chế được công bố rằng tự xóa website chỉ vì không có lượt truy cập. Nhưng repository có thể bị xóa/tạm dừng nếu chủ sở hữu xóa, tài khoản bị khóa, vi phạm điều khoản hoặc dịch vụ thay đổi. Tên miền riêng cần được gia hạn. Nên giữ bản sao bộ mã nguồn website này.

## Nguồn hướng dẫn chính thức

- https://developers.google.com/identity/protocols/oauth2/policies
- https://support.google.com/cloud/answer/15549049
- https://developers.google.com/identity/protocols/oauth2/production-readiness/policy-compliance
- https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site
