# Google Ads — TapeHer (qua landing purisia.com/lp/tapeher) · Tài liệu vận hành

> **Mục đích:** Cấu hình campaign Google Ads để đẩy traffic vào landing comparison
> `https://purisia.com/lp/tapeher/`, khách bấm ra affiliate `https://tapeher.com/?ref=serena1`.
> Tài liệu này copy thẳng vào Google Ads. Ad copy/keyword giữ **tiếng Anh**; hướng dẫn tiếng Việt.
>
> **Nguyên tắc sống còn:** thị trường mouth tape paid rất đắt. Dự án này chỉ có biên khi
> **CPC thực ≤ ~CA$0.30**. Bất cứ keyword/nhóm nào kéo CPC vượt trần → giảm bid hoặc tắt ngay.

---

## Mục lục
1. [Tổng quan & cảnh báo kinh tế](#1-tổng-quan--cảnh-báo-kinh-tế)
2. [Cài đặt campaign](#2-cài-đặt-campaign)
3. [Cấu trúc ad group + keyword](#3-cấu-trúc-ad-group--keyword)
4. [Negative keywords (copy-paste)](#4-negative-keywords-copy-paste)
5. [Ad copy RSA](#5-ad-copy-rsa)
6. [Assets (sitelinks / callouts / snippets)](#6-assets)
7. [Conversion action](#7-conversion-action)
8. [Stop-rules](#8-stop-rules)
9. [Bảng đối soát WEEKLY](#9-bảng-đối-soát-weekly)
10. [Checklist khởi động](#10-checklist-khởi-động-trước-khi-bật-ads)

---

## 1. Tổng quan & cảnh báo kinh tế

**Funnel 2 bước:** `ad click` → `landing purisia` → `click affiliate (outbound)` → đơn trên tapeher.

Số liệu thật từ dashboard (CAD):

| Chỉ số | Giá trị | Ghi chú |
|---|---|---|
| EPC (mỗi click affiliate) | **CA$0.84** | dùng CA$0.74 khi tính thận trọng / lúc pending cao |
| CVR click affiliate → đơn | 6.82% | |
| HH trung bình / đơn | CA$12.38 | |

**Doanh thu / ad-click = L × EPC**, với **L = % khách trên landing bấm ra affiliate.**
⇒ **Trần CPC hoà vốn** (dùng EPC thận trọng CA$0.74):

| L (landing→affiliate) | Doanh thu / ad-click | **CPC hoà vốn** | CPC mục tiêu để có lãi |
|---|---|---|---|
| 30% | CA$0.222 | CA$0.22 | ≤ CA$0.18 |
| **40%** | CA$0.296 | **~CA$0.34*** | **≤ CA$0.25** |
| **55%** | CA$0.407 | **~CA$0.46*** | **≤ CA$0.35** |
| 70% | CA$0.518 | CA$0.52 | ≤ CA$0.40 |

> *Mốc CA$0.34 (L=40%) và CA$0.46 (L=55%) tính theo EPC đầy đủ CA$0.84 (0.84×0.40=0.336;
> 0.84×0.55=0.462) — đây là **trần tuyệt đối, không phải mục tiêu**. Vận hành phải đặt CPC
> mục tiêu **thấp hơn trần** để có biên an toàn. Cột "CPC hoà vốn" theo EPC thận trọng CA$0.74
> chặt hơn — ưu tiên cột này khi quyết định tắt.

**Quy tắc vàng:** chỉ giữ keyword giữ được **CPC thực ≤ ~CA$0.30**. Mọi keyword category rộng
(`mouth tape` CA$1.02, `best mouth tape` CA$2.34…) đều **CẤM** — không bao giờ thêm.

**Cảnh báo đo lường:** Google Ads **không** thấy đơn thật trên tapeher.com (cross-domain affiliate).
Conversion đo được = **outbound click ra affiliate** (proxy). ⇒ **bắt buộc đối soát thủ công weekly**
với dashboard tapeher (mục 9). Đừng để Google tối ưu mù theo proxy.

---

## 2. Cài đặt campaign

| Mục | Giá trị | Lý do |
|---|---|---|
| **Campaign type** | Search | Chỉ search, không Performance Max / Display. |
| **Networks** | ✅ Google Search · ❌ **Search Partners** · ❌ **Display Network** | Partners + Display traffic rác/đắt, kéo CPC & L tụt. **Tắt cả hai.** |
| **Mục tiêu** | "Create campaign without a goal's guidance" | Tránh Google ép smart bidding. |
| **Locations** | **Canada** (chính) | Dashboard tính CAD → giữ đồng tiền nhất quán. |
| | (tuỳ chọn) United States — **tách campaign riêng** | Đừng gộp CA+US 1 campaign: CPC/đồng tiền khác nhau, khó đối soát. Nếu chạy US, clone campaign, ngân sách + bid riêng. |
| | Location options → **"Presence: People in your targeted locations"** | KHÔNG dùng "presence or interest" (kéo traffic ngoài vùng). |
| **Languages** | English | |
| **Bidding** | **Manual CPC** (bật *Enhanced CPC = OFF*) | **Bắt buộc** để giữ trần CPC theo từng keyword. Smart bidding sẽ phá trần vì nó tối ưu theo proxy outbound, không thấy đơn thật. |
| | (thay thế tạm) **Maximize clicks + bid cap CA$0.30** | Chỉ dùng nếu muốn dò nhanh; **phải** đặt *Maximum CPC bid limit = CA$0.30*. Khi đủ data → chuyển về Manual CPC. |
| **Budget** | **CA$10–15 / ngày** (test) | Đủ ~30–50 click/ngày để học, không cháy ngân sách khi sai. |
| **Ad rotation** | "Optimize: prefer best performing ads" | |
| **Ad schedule** | Bật cả tuần; sau 1–2 tuần xem report giờ/ngày → cắt khung giờ CPA xấu | Mouth tape là quyết định buổi tối/đêm (sleep) — theo dõi khung 19:00–24:00. |
| **Devices** | Ưu tiên **Mobile** | Landing mobile-first. Sau khi có data: Desktop/Tablet nếu CPA xấu → bid adjustment −30%…−50%. |
| **Start** | Manual CPC, không "auto-apply recommendations" | Tắt mọi auto-apply để Google không tự bật broad/Partners/smart bidding. |

---

## 3. Cấu trúc ad group + keyword

1 campaign · 2 ad group. **Match type: ưu tiên exact `[ ]`; vài phrase `" "` để dò; KHÔNG broad.**

### AG "Brand" — bid cap **CA$0.15–0.35**
| Keyword | Match | Bid khởi điểm |
|---|---|---|
| `[tapeher]` | exact | CA$0.20 |
| `[tapeher mouth tape]` | exact | CA$0.25 |
| `[tapeher bestseller]` | exact | CA$0.20 |
| `"tapeher mouth tape"` | phrase | CA$0.30 |

> ⚠️ **Rủi ro brand:** (1) keyword brand có thể "ăn" traffic organic mà lẽ ra free → theo dõi
> xem có thực sự incremental không. (2) `tapeher` là brand của đối tác — nếu họ/affiliate khác
> cũng bid hoặc cấm bid trên trademark, có thể bị khiếu nại. Giữ bid thấp, không dùng "TapeHer"
> trong Display URL gây hiểu nhầm là trang chính chủ. (3) Brand thường CPC rất rẻ & CVR cao →
> đây là nhóm "an toàn" để mở màn.

### AG "Long-tail" — bid cap **CA$0.20–0.45** · *chỉ giữ keyword giữ được CPC ≤ CA$0.30*
| Keyword | Match | Bid khởi điểm |
|---|---|---|
| `[mouth taping benefits]` | exact | CA$0.30 |
| `[how to use mouth tape]` | exact | CA$0.30 |
| `[does mouth tape help jawline]` | exact | CA$0.35 |
| `[pfas free tape]` | exact | CA$0.25 |
| `[mouth tape for women]` | exact | CA$0.35 |

> Sau 50–100 click/keyword: keyword nào CPC thực > CA$0.30 mà không kéo được L cao → **tắt**.
> Phrase chỉ dùng để **khám phá search term mới** rồi chuyển từ tốt sang exact, từ rác sang negative.

---

## 4. Negative keywords (copy-paste)

Tạo 1 **Negative keyword list** dùng chung (Tools → Shared library → Negative keyword lists),
gắn cho campaign. Dán nguyên khối:

```
breathe right
somnifix
hostage tape
myotape
dryft
vio2
frownies
reddit
free
diy
sleep mask
eye mask
tennis
alcaraz
amazon
coupon
wholesale
bulk
job
affiliate
```

> Đây là negative dạng **broad** (không ngoặc) để chặn rộng mọi biến thể chứa từ đó.
> Bổ sung thêm theo Search Terms report mỗi tuần (xem stop-rules).

---

## 5. Ad copy RSA

Mỗi ad group 1 RSA. **Headline ≤ 30 ký tự · Description ≤ 90 ký tự.**
**Final URL =** `https://purisia.com/lp/tapeher/` (cho cả 2 AG).
**Tracking template / UTM:** UTM (`utm_source=google&utm_medium=cpc&utm_campaign=tapeher_lp&utm_content=…`)
**đã được gắn sẵn trên link affiliate trong landing**. ⇒ **KHÔNG** thêm UTM vào Final URL hay
Tracking template của Google Ads → tránh double-UTM. Để Final URL "sạch" như trên.
Tông: beauty / sleep / self-care. **KHÔNG** claim y tế tuyệt đối ("cures", "stops snoring guaranteed"…).

### RSA — AG "Brand"
**Headlines (≤30):**
```
TapeHer Mouth Tape
TapeHer — Made for Women
Gentle Mouth Tape for Her
PFAS-Free Mouth Tape
Skin-Safe & Easy Peel-Off
See Why It's Rated #1
TapeHer vs The Rest
Mouth Tape, Done Right
Sensitive-Skin Friendly
Nightly Mouth Tape Review
```
**Descriptions (≤90):**
```
TapeHer rated #1 in our mouth tape comparison. PFAS-free, skin-safe, made for women.
Gentle, easy peel-off mouth tape designed for sensitive skin. See the full review.
We compared the top mouth tapes. TapeHer came out on top. Read why before you buy.
Soft, breathable mouth tape for a calmer night. Made for women. Honest comparison.
```

### RSA — AG "Long-tail"
**Headlines (≤30):**
```
Best Mouth Tape, Compared
Mouth Taping Benefits
How To Use Mouth Tape
PFAS-Free Mouth Tape
Mouth Tape for Women
Top 5 Mouth Tapes Ranked
Gentle, Skin-Safe Tape
Is Mouth Tape Safe?
Made for Sensitive Skin
Our #1 Pick Inside
```
**Descriptions (≤90):**
```
We compared the top mouth tapes side by side. See benefits, safety and our #1 pick.
New to mouth taping? Learn how it works and which tape is gentlest on your skin.
PFAS-free, easy peel-off, made for women. See the full mouth tape comparison.
Honest mouth tape guide: benefits, how to use, and the top-rated option for women.
```

> Pin tuỳ chọn: pin 1 headline brand/USP vào vị trí 1 nếu muốn kiểm soát; mặc định để Google xoay
> để tối ưu Ad Strength "Good/Excellent".

---

## 6. Assets

Thêm ở cấp campaign/ad group (Ads & assets → Assets).

**Sitelinks** (trỏ tới anchor section của landing — landing có sẵn các id):

| Sitelink text | URL |
|---|---|
| How to use | `https://purisia.com/lp/tapeher/#how-h` |
| Is it safe? | `https://purisia.com/lp/tapeher/#faq-h` |
| Best for sensitive skin | `https://purisia.com/lp/tapeher/#rev-h` |
| Compare top 5 | `https://purisia.com/lp/tapeher/#cmp-h` |

> Anchor có thật trong landing: `#how-h` (how to use), `#cmp-h` (comparison), `#rev-h` (review),
> `#faq-h` (FAQ/safety), `#final-h` (final CTA), `#ru-h`. **Trước khi chạy, mở landing kiểm tra
> anchor scroll đúng chỗ.** Final URL của sitelink vẫn là purisia (không UTM riêng).

**Callouts** (≤25 ký tự):
```
PFAS-Free
Skin-Safe
Easy Peel-Off
Made for Women
Gentle on Sensitive Skin
Honest Comparison
```

**Structured snippets:**
- Header **"Features":** `PFAS-free`, `Skin-safe adhesive`, `Easy peel-off`, `For sensitive skin`, `Made for women`
- Header **"Types":** `Mouth tape`, `Sleep aid`, `Nightly use`

---

## 7. Conversion action

Tạo conversion để Google hiểu giá trị (dù chỉ là **proxy**, không phải đơn thật).

| Trường | Giá trị |
|---|---|
| Goal / name | **Affiliate Click Out** |
| Category | **Other** |
| Source | **Website** (Google tag đã gắn trên landing) |
| Count | **One** (1 outbound click / phiên là đủ, tránh đếm bội) |
| Value | **CA$0.74** mỗi conversion (EPC thận trọng) — "Use the same value for each conversion" |
| Click-through window | 30 ngày |
| Attribution | Data-driven (hoặc Last click nếu volume thấp) |
| Include in "Conversions" | ✅ Yes |

**Cách bắt sự kiện:** outbound click vào link `tapeher.com` trên landing. Hai cách:
1. **GA4 → Google Ads:** trong GA4 đã có event outbound click (gtag tự bắt `click` ra domain ngoài),
   đánh dấu event đó là conversion → import sang Google Ads. (Khuyến nghị — không cần sửa landing.)
2. **Gtag event trực tiếp:** gắn `gtag('event','conversion', …)` vào onclick link affiliate.

> ⚠️ Đây là **proxy outbound click**, KHÔNG phải đơn tapeher thật. Giá trị CA$0.74 chỉ để Google
> ước lượng — **lãi/lỗ thật vẫn phải chốt bằng bảng đối soát weekly (mục 9)** đối chiếu đơn thật
> từ dashboard tapeher.

---

## 8. Stop-rules

| Tín hiệu | Ngưỡng | Hành động |
|---|---|---|
| CPC thực quá cao | **> CA$0.34** | Giảm bid keyword về ≤ CA$0.30; nếu vẫn vượt → **tắt keyword**. |
| Click nhiều, 0 outbound | **≥ 50 click / 0 outbound** (1 keyword hoặc toàn campaign) | Soát landing: link affiliate sống? CTA hiện? tracking bắt đúng? trang load mobile? |
| Landing rò rỉ | **L < 35% sau ≥ 100 click** | **Dừng tăng tiền.** Sửa landing (CTA, tốc độ, trust) trước khi scale. L thấp = đốt tiền. |
| Search term xấu | xuất hiện competitor / category rộng / off-topic | Thêm **negative ngay** (vào list mục 4). Rà Search Terms ≥ 2×/tuần. |
| Pending hoa hồng tăng | dashboard báo pending/hold cao | Chuyển sang tính theo **EPC CA$0.74** (thận trọng) khi đánh giá lãi/lỗ, siết bid. |
| Đơn thật < kỳ vọng | EPC thực (mục 9) < CA$0.60 kéo dài | Hạ trần CPC toàn campaign; nghi ngờ chất lượng traffic/long-tail → cắt keyword yếu. |
| Brand ăn organic | Brand AG nhiều click nhưng tổng đơn không tăng | Cân nhắc giảm/tắt brand nếu không incremental. |

---

## 9. Bảng đối soát WEEKLY

Đối soát **theo `utm_content`** (vị trí CTA trên landing) — đây là chìa khoá nối Google Ads ↔ GA4 ↔ dashboard tapeher.

**Lấy số từ đâu:**
- **ad clicks, ad cost, CPC** → Google Ads (campaign/ad group/keyword).
- **outbound clicks** (chia theo `utm_content`) → GA4 (event outbound click, breakdown by link URL / utm_content).
- **orders, commission** → **dashboard tapeher** (lọc theo `ref=serena1`, đối chiếu utm_content nếu dashboard giữ).
- **L%** = outbound clicks ÷ ad clicks. **EPC thực** = commission ÷ outbound clicks. **CPA outbound** = ad cost ÷ outbound clicks.

> Lưu ý ghép số: Google Ads cho ad clicks theo **keyword/ad group**, còn utm_content phân biệt theo
> **vị trí CTA trên landing** — 1 ad click có thể không ra outbound, hoặc ra qua bất kỳ CTA nào.
> ⇒ Cột "ad clicks/cost" ghép ở **dòng tổng (campaign)**; các dòng utm_content tập trung vào
> **outbound → orders → commission**. Giữ cả 2 lát cắt: (A) theo utm_content (chất lượng landing/CTA),
> (B) theo ad group/keyword (chất lượng traffic). Mẫu A dưới đây + 1 dòng tổng nối sang B.

### (A) Theo utm_content — tuần: `____ → ____`

| utm_content | Outbound clicks (GA4) | Orders (dashboard) | Commission CA$ | EPC thực = HH/outbound | CVR outbound→order | Ghi chú CTA |
|---|---|---|---|---|---|---|
| hero | | | | | | |
| comparison | | | | | | |
| review | | | | | | |
| final | | | | | | |
| sticky | | | | | | |
| **TỔNG** | | | | | | |

### (B) Tổng campaign — kinh tế thật

| Chỉ số | Công thức | Giá trị tuần này | Quyết định |
|---|---|---|---|
| Ad clicks | Google Ads | | |
| Ad cost CA$ | Google Ads | | |
| CPC thực | cost ÷ ad clicks | | so trần ≤ CA$0.30 |
| Outbound clicks | GA4 (tổng) | | |
| **L%** | outbound ÷ ad clicks | | < 35% → sửa landing |
| Orders | dashboard | | |
| Commission CA$ | dashboard | | |
| **EPC thực** | commission ÷ outbound | | < CA$0.60 → siết bid |
| **CPA outbound** | cost ÷ outbound | | so EPC: < EPC = lãi |
| **Lãi/lỗ CA$** | commission − ad cost | | ▲ scale / ▼ cắt / = giữ |

> **Đọc nhanh:** lãi khi `commission > ad cost`, tức `CPC thực < L × EPC thực`. Nếu lỗ: ưu tiên (1)
> tăng L bằng sửa landing, (2) hạ CPC bằng cắt keyword đắt, trước khi nghĩ tới tăng ngân sách.

---

## 10. Checklist khởi động (trước khi bật ads)

- [ ] **Gtag ID thật đã gắn?** — landing hiện đang để placeholder `G-XXXXXXXXXX`. **Phải thay
      bằng Measurement ID GA4 thật** rồi re-deploy purisia, nếu không **không đo được outbound** → mù hoàn toàn.
- [ ] **Domain purisia.com đã trỏ & live HTTPS?** Mở `https://purisia.com/lp/tapeher/` trên mobile thật.
- [ ] **Landing live & link affiliate sống?** Bấm thử mọi CTA (hero/comparison/review/final/sticky) →
      ra `tapeher.com/?ref=serena1&...&utm_content=…` đúng, mở tab mới, `rel="sponsored noopener"`.
- [ ] **Anchor sitelink scroll đúng?** Thử `#how-h #cmp-h #rev-h #faq-h`.
- [ ] **Conversion action "Affiliate Click Out" verified?** GA4 event outbound bắt được + đã import
      sang Google Ads, trạng thái "Recording conversions" (test 1 click thật).
- [ ] **Negative keyword list đã nạp & gắn campaign?** (20 từ ở mục 4)
- [ ] **Bid cap đặt đúng?** Brand CA$0.15–0.35 · Long-tail CA$0.20–0.45 · không keyword nào > CA$0.45.
- [ ] **Search Partners OFF · Display OFF · Manual CPC (ECPC off)?**
- [ ] **Location = Canada, "Presence" only?** (US tách campaign riêng nếu chạy)
- [ ] **Budget CA$10–15/ngày · auto-apply recommendations OFF?**
- [ ] **Final URL sạch (không UTM)** để tránh double-UTM với link trong landing.
- [ ] Lịch **đối soát weekly** đã đặt (mục 9) — chốt lãi/lỗ bằng đơn thật, không tin proxy.
