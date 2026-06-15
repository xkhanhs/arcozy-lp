# arcozy-lp — Purisia Landing Pages

Static affiliate landing pages cho **purisia.com**, deploy lên Cloudflare Pages.  
Không có build step — tất cả là raw HTML/CSS/JS inline.

---

## Cấu trúc

```
dist/                          # thư mục deploy (Cloudflare serve thư mục này)
  index.html                   # homepage purisia.com
  tapeher/
    index.html                 # money page — "Best mouth tape" comparison
    assets/
      hero-packshot.jpg
      review-model.jpg
      features.jpg
      howto-steps.jpg
```

**Docs:**
- `ADS-PLAN-tapeher.md` — toàn bộ chiến lược Google Ads (keyword, bid, RSA copy, stop-rules, weekly đối soát)
- `README-deploy.md` — hướng dẫn deploy Cloudflare Pages

---

## Deploy

```bash
npx wrangler pages deploy dist --project-name purisia --commit-message "deploy" --commit-dirty=true
```

> Luôn pass `--commit-message "deploy"` (ASCII). Cloudflare API reject commit message tiếng Việt.  
> Dùng `pages deploy` (không phải `wrangler deploy` — cái đó là Workers).

**Live URLs:**
- `https://purisia.com/` — homepage
- `https://purisia.com/lp/tapeher/` — money page TapeHer

---

## Tracking — placeholders cần điền

File `dist/tapeher/index.html` có 3 placeholder **phải thay trước khi chạy Ads:**

| Placeholder | Thay bằng | Tìm ở đâu |
|---|---|---|
| `GA_MEASUREMENT_ID` | `G-XXXXXXXXXX` | GA4 → Admin → Data Streams → Web |
| `AW_CONVERSION_ID` | `AW-XXXXXXXXXX` | Google Ads → Tools → Conversions |
| `AW_CONVERSION_LABEL` | chuỗi ngắn sau dấu `/` | cùng chỗ với AW_CONVERSION_ID |

Sau khi điền → re-deploy. Kiểm tra bằng Google Tag Assistant.

**Sự kiện đã tích hợp sẵn:**
- `affiliate_click` — bắn khi click bất kỳ link `tapeher.com`, kèm `cta_position` (hero/comparison/review/final/sticky)
- `conversion` — gửi thẳng sang Google Ads cùng lúc (gtag direct)

---

## Thêm landing mới

1. Tạo thư mục `dist/<product-name>/`
2. Copy `dist/tapeher/index.html` làm template
3. Thêm ảnh vào `dist/<product-name>/assets/`
4. Tạo `ADS-PLAN-<product-name>.md` theo cùng cấu trúc
5. Deploy

---

## Quy tắc khi sửa

- **Không** dùng framework, CDN font, hay external JS ngoài Google Tag (gtag)
- CSS inline trong `<style>` — giữ nguyên cấu trúc CSS variable (`--accent`, `--bg`, v.v.)
- Affiliate link **phải** có `rel="sponsored noopener"` và `target="_blank"`
- UTM params trên link affiliate: `utm_content=hero|comparison|review|final|sticky`  
  (dùng để đối soát weekly — xem `ADS-PLAN-tapeher.md` mục 9)
- **Không** thêm UTM vào Final URL Google Ads (double-UTM) — UTM nằm trên link trong landing
