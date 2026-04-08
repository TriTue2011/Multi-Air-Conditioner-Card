# ❄️ Multi Air Conditioner Card

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/hacs/integration)
![version](https://img.shields.io/badge/version-1.1-blue)
![HA](https://img.shields.io/badge/Home%20Assistant-2023.1+-green)
![license](https://img.shields.io/badge/license-MIT-lightgrey)

> 🇬🇧 **English version:** [README.md](README.md)

Card tùy chỉnh cho Home Assistant Lovelace — điều khiển điều hòa nhiều phòng với đồng hồ nhiệt độ động, điều chỉnh quạt & hướng gió, tab chọn phòng, chế độ Eco, hẹn giờ tắt/bật, cảm biến môi trường và trình chỉnh sửa giao diện trực quan hỗ trợ tới 8 phòng.

**Không cần plugin bổ sung. Hoạt động độc lập, cấu hình hoàn toàn qua giao diện chỉnh sửa tích hợp.**

---

## 📸 Xem trước

![Multi AC Card Preview](assets/preview.png)

---

## 🎛️ Visual Config Editor

![Multi AC Card Editor](assets/editor-preview.png)

---

## ✨ Tính năng (v1.1)

### 🎨 Hiển thị & Giao diện
- ❄️ **Đồng hồ nhiệt độ** — vòng cung động hiển thị nhiệt độ phòng hiện tại với ánh sáng đổi màu theo chế độ
- 🏠 **Ảnh phòng** — ảnh riêng từng phòng kèm badge ON/OFF và nhiệt độ trực tiếp
- 📊 **Khối trạng thái** — tình trạng hoạt động, chỉ số PM2.5, nhiệt độ ngoài trời, độ ẩm và điện năng tiêu thụ
- 🕐 **Đồng hồ thực** — hiển thị ngày giờ theo thời gian thực với lời chào theo buổi trong ngày
- 🌿 **Badge Eco** — bật/tắt chế độ Eco trực tiếp từ đầu card

### ❄️ Điều khiển nhiều phòng (tối đa 8 phòng)
- **Tab chọn phòng** — hiển thị icon, tên, nhiệt độ hiện tại và badge ON/OFF; luôn hiện 4 phòng, cuộn để xem thêm
- **Điều khiển HVAC từng phòng** — các nút chế độ Làm lạnh / Sưởi / Hút ẩm / Quạt với màu trạng thái
- **Điều chỉnh nhiệt độ** — nút `+` / `−` để đặt nhiệt độ mong muốn; nhiệt độ hiện tại hiển thị trên đồng hồ
- **Tốc độ quạt** — chuyển đổi Tự động / Thấp / Vừa / Cao với SVG cánh quạt động và biểu đồ cột
- **Hướng gió** — chuyển đổi Cố định / Lên xuống / Trái phải / Tất cả với SVG sóng động

### 🌿 Eco & Tác vụ nhanh
- **Bật/tắt Eco** — kích hoạt chế độ Eco/preset cho điều hòa phòng đang chọn
- **Chip tác vụ nhanh** — nút tắt Eco, Fav, Clean ngay trên bảng điều khiển

### ⏱️ Hẹn giờ
- **Hẹn giờ từng phòng** — đặt timer 1 / 2 / 4 / 8 giờ để tự động bật hoặc tắt điều hòa
- **Đếm ngược trực tiếp** — thời gian còn lại hiển thị ngay trên nút hẹn giờ
- **Timer bền vững** — trạng thái được lưu vào localStorage, khôi phục sau khi tải lại trang

### 🌐 10 ngôn ngữ
- 🇻🇳 Tiếng Việt / 🇬🇧 English / 🇩🇪 Deutsch / 🇫🇷 Français / 🇳🇱 Nederlands
- 🇵🇱 Polski / 🇸🇪 Svenska / 🇭🇺 Magyar / 🇨🇿 Čeština / 🇮🇹 Italiano
- **Ảnh cờ quốc gia thật** qua flagcdn.com

### 🎨 Tùy chỉnh giao diện
- **16 preset gradient nền** — Default, Night, Sunset, Forest, Aurora, Desert, Ocean, Cherry, Volcano, Galaxy, Ice, Olive, Slate, Rose, Teal, Custom
- **3 bộ chọn màu** — Nhấn, Chữ, Màu nền tùy chỉnh

---

## 📦 Cài đặt

### Cách 1 — HACS (khuyến nghị)

**Bước 1:** Thêm Custom Repository vào HACS:

[![Open HACS Repository](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=doanlong1412&repository=multi-air-conditioner-card&category=plugin)

> Nếu nút không hoạt động:
> **HACS → Frontend → ⋮ → Custom repositories**
> → URL: `https://github.com/doanlong1412/multi-air-conditioner-card` → Type: **Dashboard** → Add

**Bước 2:** Tìm **Multi Air Conditioner Card** → **Install**

**Bước 3:** Hard-reload trình duyệt (`Ctrl+Shift+R`)

---

### Cách 2 — Thủ công

1. Tải [`multi-air-conditioner-card.js`](https://github.com/doanlong1412/multi-air-conditioner-card/releases/latest)
2. Sao chép vào `/config/www/multi-air-conditioner-card.js`
3. Vào **Settings → Dashboards → Resources** → **Add resource**:
   ```
   URL:  /local/multi-air-conditioner-card.js
   Type: JavaScript module
   ```
4. Hard-reload trình duyệt (`Ctrl+Shift+R`)

---

## ⚙️ Cấu hình Card

### Bước 1 — Thêm card vào dashboard

```yaml
type: custom:multi-air-conditioner-card
```

Sau khi thêm, nhấn **✏️ Edit** để mở Config Editor.

### Bước 2 — Các phần trong Config Editor

| # | Phần | Nội dung |
|---|------|----------|
| 1 | 🌐 **Ngôn ngữ** | 10 ngôn ngữ với ảnh cờ thật |
| 2 | 🔢 **Số phòng** | Thanh trượt chọn 1–8 phòng |
| 3 | ❄️ **Điều hòa** | Chọn entity, tên hiển thị và icon từng phòng |
| 4 | 📡 **Cảm biến môi trường** | PM2.5, nhiệt độ ngoài trời, độ ẩm, điện năng |
| 5 | 🎨 **Màu sắc** | Màu nhấn, màu chữ |
| 6 | 🎨 **Màu nền** | 16 preset + bộ chọn hai màu tùy chỉnh |

---

## 🔌 Tham chiếu thực thể

### Thực thể từng phòng (tối đa 8 phòng)

| Config key | Loại | Mô tả |
|---|---|---|
| `entities[n].entity_id` | `climate` | Entity điều hòa ✅ |
| `entities[n].label` | string | Tên hiển thị của phòng |
| `entities[n].icon` | string | Emoji icon cho tab phòng |
| `entities[n].area` | string | Diện tích phòng (ví dụ: `25 m²`) |

### Cảm biến môi trường (tuỳ chọn)

| Config key | Loại | Mô tả |
|---|---|---|
| `pm25_entity` | `sensor` | Cảm biến bụi mịn PM2.5 |
| `outdoor_temp_entity` | `sensor` | Cảm biến nhiệt độ ngoài trời |
| `humidity_entity` | `sensor` | Cảm biến độ ẩm ngoài trời |
| `power_entity` | `sensor` | Cảm biến điện năng tiêu thụ (kW) |

---

## ⚙️ Tham chiếu cấu hình đầy đủ

| Config key | Kiểu | Mặc định | Mô tả |
|---|---|---|---|
| `language` | string | `vi` | `vi`/`en`/`de`/`fr`/`nl`/`pl`/`sv`/`hu`/`cs`/`it` |
| `room_count` | number | `4` | Số phòng hiển thị (1–8) |
| `owner_name` | string | `Smart Home` | Tên chủ nhà hiển thị trong lời chào |
| `background_preset` | string | `default` | Tên preset gradient |
| `bg_color1` | hex | `#001e2b` | Màu gradient tùy chỉnh 1 (trên trái) |
| `bg_color2` | hex | `#12c6f3` | Màu gradient tùy chỉnh 2 (dưới phải) |
| `accent_color` | hex | `#00ffcc` | Màu nhấn / glow |
| `text_color` | hex | `#ffffff` | Màu chữ chính |
| `entities` | array | — | Danh sách đối tượng phòng (xem bên trên) |
| `pm25_entity` | entity | — | Cảm biến PM2.5 |
| `outdoor_temp_entity` | entity | — | Cảm biến nhiệt độ ngoài trời |
| `humidity_entity` | entity | — | Cảm biến độ ẩm |
| `power_entity` | entity | — | Cảm biến điện năng tiêu thụ |

---

## 📝 Ví dụ YAML đầy đủ

```yaml
type: custom:multi-air-conditioner-card
language: vi
room_count: 4
owner_name: Nhà Của Tôi

background_preset: default
accent_color: "#00ffcc"
text_color: "#ffffff"

entities:
  - entity_id: climate.dieu_hoa_living
    label: Phòng khách
    area: "25 m²"
    icon: 🛋
  - entity_id: climate.bed_air_conditioning
    label: Phòng ngủ
    area: "18 m²"
    icon: 🛌
  - entity_id: climate.kitchen_air_conditioning
    label: Phòng ăn
    area: "20 m²"
    icon: 🍳
  - entity_id: climate.dieu_hoa_office
    label: Văn phòng
    area: "15 m²"
    icon: 💼

pm25_entity: sensor.pm25
outdoor_temp_entity: sensor.outdoor_temperature
humidity_entity: sensor.outdoor_humidity
power_entity: sensor.ac_power_kwh
```

### Ví dụ tối giản (2 phòng, không có cảm biến)

```yaml
type: custom:multi-air-conditioner-card
language: vi
room_count: 2
entities:
  - entity_id: climate.dieu_hoa_living
    label: Phòng khách
    icon: 🛋
  - entity_id: climate.bed_air_conditioning
    label: Phòng ngủ
    icon: 🛌
```

---

## 🖥️ Tương thích

| | |
|---|---|
| Home Assistant | 2023.1+ |
| Lovelace | Dashboard mặc định & tùy chỉnh |
| Thiết bị | Mobile & Desktop |
| Phụ thuộc | Không — hoàn toàn độc lập |
| Trình duyệt | Chrome, Firefox, Safari, Edge |

---

## 📋 Lịch sử thay đổi

### v1.1
- 🔢 Số phòng có thể cấu hình — 1 đến 8 phòng qua thanh trượt trong editor
- 🌐 Hỗ trợ 10 ngôn ngữ với ảnh cờ thật
- 🎨 16 preset gradient nền
- 🎛️ Trình chỉnh sửa trực quan đầy đủ — entity picker, accordion, bộ chọn màu 3 lớp
- 🐛 Sửa lỗi mất focus khi nhập text trong editor

### v1.0
- 🚀 Phát hành lần đầu — card điều khiển 4 điều hòa

---

## 📄 Giấy phép

MIT License — miễn phí sử dụng, chỉnh sửa và phân phối.
Nếu bạn thấy hữu ích, hãy ⭐ **star repo** nhé!

---

## 🙏 Credits

Thiết kế và phát triển bởi **[@doanlong1412](https://github.com/doanlong1412)** từ 🇻🇳 Việt Nam.
