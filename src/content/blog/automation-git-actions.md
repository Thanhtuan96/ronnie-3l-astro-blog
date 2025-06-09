---
title: 'First post'
description: 'Lorem ipsum dolor sit amet'
pubDate: 'Jul 08 2025'
heroImage: 'https://plus.unsplash.com/premium_photo-1677094310899-02303289cadf?q=80&w=1032&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
---

Tất nhiên! Dưới đây là một đoạn **blog demo** nói về **automation với một ví dụ thực tế**, có **code block minh hoạ**, phù hợp với blog cá nhân hoặc kỹ thuật. Chủ đề được chọn là: _"Tự động hoá việc build và deploy website tĩnh với GitHub Actions"_, một chủ đề phổ biến, dễ tiếp cận và hữu ích với nhiều developer.

## 🚀 Tự động hoá Build & Deploy Website Tĩnh với GitHub Actions

Bạn đã bao giờ cảm thấy phiền phức khi phải build và deploy thủ công mỗi lần update website? 🤯

**Automation (tự động hoá)** là chìa khoá giúp bạn tiết kiệm thời gian, giảm lỗi và duy trì workflow chuyên nghiệp. Trong bài viết này, mình sẽ hướng dẫn cách sử dụng **GitHub Actions** để tự động build và deploy một website tĩnh (ví dụ với Astro hoặc Next.js) lên **GitHub Pages** hoặc **Vercel/Netlify**.

### 🧠 Tại sao nên tự động hoá?

Việc tự động hoá quá trình build & deploy mang lại rất nhiều lợi ích:

-   ✅ Không còn quên chạy lệnh `build` trước khi push
-   ✅ Luôn đảm bảo code mới nhất được deploy
-   ✅ Giảm rủi ro bug do sai sót thủ công
-   ✅ Dễ dàng scale và áp dụng cho nhiều dự án

### 🛠️ Bắt đầu với GitHub Actions

Giả sử bạn đang dùng Astro và muốn deploy lên GitHub Pages. Đây là file workflow tối giản để làm điều đó:

```yaml
# .github/workflows/deploy.yml
name: Deploy to GitHub Pages

on:
    push:
        branches: [main]

jobs:
    build-deploy:
        runs-on: ubuntu-latest

        steps:
            - name: Checkout code
              uses: actions/checkout@v3

            - name: Setup Node.js
              uses: actions/setup-node@v3
              with:
                  node-version: 18

            - name: Install dependencies
              run: npm install

            - name: Build project
              run: npm run build

            - name: Deploy to GitHub Pages
              uses: peaceiris/actions-gh-pages@v3
              with:
                  github_token: ${{ secrets.GITHUB_TOKEN }}
                  publish_dir: ./dist
```

### 📦 Giải thích từng bước:

-   **on.push.branches**: Kích hoạt khi bạn push lên nhánh `main`.
-   **setup-node**: Thiết lập môi trường Node.js.
-   **npm install & build**: Cài package và build website.
-   **peaceiris/actions-gh-pages**: Deploy thư mục `dist` lên GitHub Pages.

### 🎉 Kết quả?

Mỗi lần bạn `git push`, GitHub sẽ tự động:

1. Build lại project
2. Deploy bản mới nhất lên production

**Không cần chạy gì thủ công nữa!**

### 📝 Tổng kết

Automation không cần phải phức tạp. Chỉ với một file YAML và vài phút cấu hình, bạn đã có thể tiết kiệm hàng giờ làm việc lặp đi lặp lại mỗi tuần. 🚀

Hãy bắt đầu với dự án nhỏ, và từng bước xây dựng một hệ thống CI/CD linh hoạt – bạn sẽ cảm nhận rõ sự khác biệt trong cách làm việc!

Bạn muốn mình viết thêm về:

-   Auto testing với GitHub Actions?
-   Deploy sang Vercel/Netlify?
-   Trigger workflows theo pull request?

Hãy comment hoặc gửi yêu cầu nhé! 🛠️✨

Bạn có muốn mình chuyển bài này thành Markdown file, Gamma presentation, hay viết tiếp phần 2 không?
