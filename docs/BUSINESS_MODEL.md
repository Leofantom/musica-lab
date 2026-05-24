# MusicA — Business Model & Glossary

Đọc file này TRƯỚC khi viết bất kỳ copy / label / hợp đồng nào. Hiểu sai domain → copy sai.

---

## 1. Định vị một câu

> **MusicA là sàn môi giới (marketplace) ghép người mua với nghệ sĩ / nhà phát hành để mua tác quyền sử dụng tác phẩm âm nhạc trên môi trường số.**

Không phải:
- ❌ "Nền tảng cấp phép âm nhạc" (cấp phép = licensing → ám chỉ MusicA là chủ thể cấp phép, sai)
- ❌ "Nền tảng nghe nhạc" (Spotify-like, KHÔNG phải mục đích)
- ❌ "Sàn nhạc số" (mơ hồ, có thể hiểu là sàn streaming)

Đúng:
- ✅ "Sàn môi giới tác quyền âm nhạc"
- ✅ "Marketplace mua tác quyền tác phẩm âm nhạc"
- ✅ "Kết nối nghệ sĩ với người mua tác quyền"

---

## 2. Hai bên user

### Bên Bán — Nghệ sĩ / Nhà phát hành (Publisher)
- Đăng tác phẩm lên sàn kèm hồ sơ pháp lý (giấy SHTT, ISRC)
- Định giá cơ bản, các biến thể giá
- Bàn giao bộ tài sản tác quyền cho người mua sau khi giao dịch xong
- Nhận tiền (MusicA giữ phí xử lý + VAT)

### Bên Mua
Người mua tác quyền để khai thác:
- **Creator / Influencer**: dùng nhạc cho YouTube, TikTok, Reels
- **SME**: TVC, video sản phẩm, podcast, livestream bán hàng
- **Đơn vị tổ chức sự kiện**: concert, gala, fanmeeting, festival
- **Brand / Agency**: chiến dịch marketing đa nền tảng

---

## 3. Sản phẩm bán trên sàn

**Mỗi "product" = 1 tác phẩm âm nhạc** có sẵn để mua tác quyền, với các **biến thể (variants)** quyết định giá:

### Variant cấp 1 — Mục đích sử dụng (purpose)
- `youtube` — Phát hành YouTube (MV, vlog, short-form)
- `performance` — Biểu diễn trực tiếp (concert, sự kiện)
- *(tương lai)* `tvc`, `livestream`, `tiktok`,…

### Variant cấp 2 — Tham số phụ thuộc purpose

**Nếu purpose = youtube**:
- `monetize`: có / không bật kiếm tiền (× 1.5 / × 1.0)
- `duration`: 6 tháng / 12 tháng / 2 năm / 3 năm (× 0.55 / 1.0 / 1.7 / 2.3)
- `scope`: toàn cầu / Việt Nam (× 1.0 / 0.7)

**Nếu purpose = performance**:
- `scale`: Dưới 200 / 200-1000 / 1000-5000 / Trên 5000 khách (× 1.0 / 1.8 / 3.2 / 5.5)
- `shows`: số buổi (× `1 + (n-1) * 0.6`)

### Công thức giá

```
youtube_price     = base × duration_mult × monetize_mult × scope_mult
performance_price = base × scale_mult × (1 + (shows - 1) * 0.6)
```

Sau đó: `total = subtotal + 4% phí xử lý` (chưa gồm VAT).

---

## 4. Bộ tài sản tác quyền (Deliverables)

Khi mua tác quyền, nghệ sĩ phải bàn giao TỐI THIỂU:

1. File audio MP3 320kbps (master)
2. File audio WAV gốc (24-bit / 48kHz)
3. File karaoke / instrumental
4. Khuông nhạc (PDF + MusicXML)
5. Lời bài hát (LRC + plain text)
6. Stems tách bè (vocal / drums / bass / synth)
7. Giấy đăng ký SHTT bản số
8. Cover art độ phân giải cao

Danh sách định nghĩa ở `src/data/catalog.js` → `defaultDeliverables`. Khi prototype mở rộng cho phép custom per-product, mỗi product có thể có array `deliverables` riêng override default.

---

## 5. Quy trình giao dịch (User flow)

```
Khám phá ──> Chi tiết tác phẩm ──> Cấu hình variant ──> Thêm giỏ
                                                            │
                                                            ▼
                                              Xem giỏ ──> Checkout
                                                            │
              ┌─────────────────────────────────────────────┤
              ▼                                             │
   Bước 1: Thông tin bên mua                                │
              │                                             │
              ▼                                             │
   Bước 2: Hợp đồng số + ký chữ ký điện tử                 │
              │                                             │
              ▼                                             │
   Bước 3: Thanh toán (VNPay/Visa/MoMo/Bank)               │
              │                                             │
              ▼                                             │
   Success: nhận bộ tài sản + mã giao dịch ────────────────┘
```

---

## 6. Glossary tiếng Việt (BẮT BUỘC)

| Nên dùng                          | Đừng dùng                              |
|-----------------------------------|----------------------------------------|
| Mua tác quyền                     | Cấp phép, licensing                    |
| Gói tác quyền / Cấu hình gói mua  | License package                        |
| Bộ tài sản tác quyền              | License files                          |
| Sàn môi giới                      | Nền tảng cấp phép                      |
| Người mua                         | Người được cấp phép, Bên B (chỉ trong văn bản pháp lý) |
| Nghệ sĩ / Nhà phát hành           | Chủ sở hữu bản quyền (chỉ dùng trong văn bản pháp lý) |
| Hợp đồng tác quyền                | Hợp đồng cấp phép                      |
| Giao dịch                         | Cấp phép (verb)                        |
| Tìm tác quyền                     | Tìm license                            |
| Mã giao dịch                      | Mã license                             |

**Lưu ý**: trong nội dung hợp đồng pháp lý có thể vẫn dùng các thuật ngữ chuẩn ("quyền sử dụng", "Bên A", "Bên B") — nhưng UI marketing/copy luôn dùng nhóm bên trái.

---

## 7. Pricing & doanh thu MusicA

- **Phí xử lý**: 4% trên subtotal (hiển thị cho buyer)
- **Phí nghệ sĩ**: 12% trên giá bán cuối (deduct khi payout) — *chưa hiển thị trong prototype*
- **VAT**: 10% — *chưa tính trong prototype, sẽ thêm khi tích hợp hoá đơn*

---

## 8. Roadmap ưu tiên domain

1. ✅ MVP: discover + variant pricing + cart + contract sign + payment (prototype)
2. Auth + onboarding nghệ sĩ (đăng tác phẩm, upload deliverables)
3. Hệ thống approve/verify tác phẩm trước khi listing
4. Auto Content ID protection với YouTube (tích hợp Partner API)
5. Tranh chấp & escrow (giữ tiền cho đến khi buyer xác nhận đã nhận deliverables)
6. Tax + e-invoice (hoá đơn điện tử)
