# 301 Redirect Setup for Cloudflare Pages

Hướng dẫn triển khai 301 redirect từ perangangka.com sang olxtoto.hot trên Cloudflare Pages.

## Cấu trúc Project

```
/
├── public/
│   └── _redirects
└── README.md
```

## Cách hoạt động

File `public/_redirects` chứa rule:
```
/* https://olxtoto.hot/:splat 301
```

- `/*` khớp tất cả đường dẫn
- `:splat` giữ nguyên path và query string
- `301` redirect vĩnh viễn (SEO-friendly)

## Triển khai

1. **Deploy lên Cloudflare Pages:**
   - Connect repository này với Cloudflare Pages
   - Build command: (để trống)
   - Build output directory: `public`

2. **Cấu hình Custom Domain:**
   - Thêm `perangangka.com` vào Custom domains
   - Tạo DNS record CNAME: `perangangka.com` → `<your-project>.pages.dev`

3. **SEO & Google Search Console:**
   - Verify cả 2 domain trong GSC
   - Sử dụng "Change of Address" tool
   - Giữ redirect ít nhất 6 tháng
   - Cập nhật sitemap cho domain mới

## Kiểm tra

Sau khi deploy:
```bash
curl -I https://perangangka.com/
# Phải trả về HTTP 301 với location: https://olxtoto.hot/

curl -I https://perangangka.com/blog/post-1
# Phải trả về HTTP 301 với location: https://olxtoto.hot/blog/post-1
```

## Lưu ý quan trọng

- **Không xóa redirect trong 6 tháng** để Google cập nhật đầy đủ
- Monitor Search Console để theo dõi quá trình chuyển đổi
- Đảm bảo sitemap mới được submit cho domain đích
