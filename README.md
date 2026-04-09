# ❄️ Multi Air Conditioner Card

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/hacs/integration)
![version](https://img.shields.io/badge/version-1.4-blue)
![HA](https://img.shields.io/badge/Home%20Assistant-2023.1+-green)
![license](https://img.shields.io/badge/license-MIT-lightgrey)

> 🇻🇳 **Phiên bản tiếng Việt:** [README_vi.md](README_vi.md)

A custom Home Assistant Lovelace card for multi-room air conditioner control — live temperature dial, fan & swing controls, per-room status tabs, eco mode, timer scheduling, environment sensors, and a full visual editor with up to 8 rooms.

**No extra plugins required. Works standalone, fully configurable through the built-in UI editor.**

---

## 📸 Preview

![Multi AC Card Preview](assets/preview.png)

---

## 🎛️ Visual Config Editor

![Multi AC Card Editor](assets/editor-preview.png)

---

## ✨ Features (v1.4)

### 🎨 Display & Interface
- ❄️ **Temperature dial** — animated arc gauge with dynamic colour glow: blue (cold) → cyan → green → orange → red (hot)
- 🔵 **Set-point inner ring** — a second thin arc inside the dial shows the target temperature, coloured by the active HVAC mode
- 🏠 **Room photo panel** — per-room image (default or custom URL) with live ON/OFF overlay badge and colour-matched temperature + humidity badge
- 📊 **Status block** — running state, air quality indicator, PM2.5 ring, outdoor temperature, humidity and power consumption
- 🕐 **Live clock** — real-time date and time display with greeting by time of day
- 🌿 **Eco mode badge** — toggle eco/preset mode directly from the card header

### 🖥️ Three View Modes
- **Full** — complete two-column layout with all panels visible (default)
- **Lite** — compact two-column layout, room photo hidden, ideal for smaller dashboards or mobile
- **Super Lite** ⚡ — ultra-compact single-column layout featuring a large dial, temperature control, HVAC mode selector and room selector; perfect for widgets, sidebars or very narrow spaces

### ✨ Super Lite Popup Style
When using **Super Lite** mode, the HVAC mode and room selectors support three interaction styles — configurable in the editor:
- **Normal** — native `<select>` dropdown (most compatible, consistent on iOS/Android)
- **Effect** — custom glass-style popup with spring open/close animation
- **Wave** — same glass popup with a wave-ripple entrance animation

### 🎛️ Per-element Visibility Toggles
Every section of the card can be individually shown or hidden directly from the editor:
- Greeting row, HVAC mode buttons (Cool / Heat / Dry / Fan individually), fan speed panel, airflow panel, Eco/Fav/Clean bar, status & sensor block, outdoor temperature, humidity, power, timer button, turn-all-off button
- **Room Temp / Humidity** (Super Lite) — toggle to show the selected room's temperature and humidity in the Super Lite header instead of outdoor sensor data

### ❄️ Multi-Room Control (up to 8 rooms)
- **Room selector tabs** (Full / Lite) — shows icon, name, current temperature and ON/OFF badge; always displays 4 rows, scrollable for more
- **Room selector dropdown** (Super Lite) — compact dropdown / glass popup listing all rooms with live temperature and ON/OFF badge
- **Per-room HVAC control** — Cool / Heat / Dry / Fan Only mode buttons with colour-coded active state
- **Temperature set** — `+` / `−` buttons to adjust set-point
- **Fan speed** — cycle through Auto / Low / Medium / High with animated fan blade SVG and bar chart
- **Swing direction** — cycles only through modes actually supported by the entity (reads `swing_modes` attribute)
- **Custom room image** — each room supports a custom photo URL, falling back to built-in defaults

### 🌡️ Per-Room Environment Sensors
Each room now supports dedicated temperature and humidity sensors independent of the AC entity:
- `entities[n].temp_entity` — override the room's displayed temperature (useful when the AC reports no `current_temperature`)
- `entities[n].humidity_entity` — override the room's displayed humidity
- Displayed in the room photo badge (Full/Lite) and in the Super Lite header when **Room Temp / Humidity** is enabled

### 🌿 Eco & Quick Actions
- **Eco toggle** — activates eco/preset mode on the selected room's AC unit
- **Quick-action chips** — Eco, Fav, Clean shortcut buttons (Full mode only)

### ⏱️ Timer Scheduling
- **Per-room timer** — 8 preset durations: `30m · 1h · 1.5h · 2h · 3h · 4h · 6h · 8h` + free custom-minute input
- **Schedule on or off** — choose whether the timer turns the AC on or off
- **Countdown display** — live countdown shown on the timer button
- **Persistent timers** — state saved to localStorage, restored after page reload

### 🌐 Multi-language Support (11 languages)
- 🇻🇳 Tiếng Việt / 🇬🇧 English / 🇩🇪 Deutsch / 🇫🇷 Français / 🇳🇱 Nederlands
- 🇵🇱 Polski / 🇸🇪 Svenska / 🇭🇺 Magyar / 🇨🇿 Čeština / 🇮🇹 Italiano / 🇵🇹 Português
- **Real country flag images** in language selector (via flagcdn.com)

### 🎨 Visual Customisation
- **16 background gradient presets** — Default, Night, Sunset, Forest, Aurora, Desert, Ocean, Cherry, Volcano, Galaxy, Ice, Olive, Slate, Rose, Teal, Custom
- **3 colour pickers** — Accent, Text, Background custom colours

---

## 📦 Installation

### Option 1 — HACS (recommended)

**Step 1:** Add Custom Repository to HACS:

[![Open HACS Repository](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=doanlong1412&repository=multi-air-conditioner-card&category=plugin)

> If the button doesn't work, add manually:
> **HACS → Frontend → ⋮ → Custom repositories**
> → URL: `https://github.com/doanlong1412/multi-air-conditioner-card` → Type: **Dashboard** → Add

**Step 2:** Search for **Multi Air Conditioner Card** → **Install**

**Step 3:** Hard-reload your browser (`Ctrl+Shift+R`)

---

### Option 2 — Manual

1. Download [`multi-air-conditioner-card.js`](https://github.com/doanlong1412/multi-air-conditioner-card/releases/latest)
2. Copy to `/config/www/multi-air-conditioner-card.js`
3. Go to **Settings → Dashboards → Resources** → **Add resource**:
   ```
   URL:  /local/multi-air-conditioner-card.js
   Type: JavaScript module
   ```
4. Hard-reload your browser (`Ctrl+Shift+R`)

---

## ⚙️ Card Configuration

### Step 1 — Add the card to your dashboard

```yaml
type: custom:multi-air-conditioner-card
```

After adding the card, click **✏️ Edit** to open the Config Editor.

### Step 2 — Config Editor sections

| # | Section | Contents |
|---|---------|----------|
| 1 | 🌐 **Language** | 11 languages with real flag images |
| 2 | 🖥️ **View mode** | Full / Lite / Super Lite layout |
| 3 | ✨ **Popup style** | Normal / Effect / Wave (Super Lite only) |
| 4 | 👁️ **Visibility** | Toggle individual sections on or off |
| 5 | 🔢 **Room count** | Slider to set 1–8 rooms |
| 6 | ❄️ **Air Conditioners** | Entity picker, display name, icon, custom image URL and per-room sensors per room |
| 7 | 📡 **Environment Sensors** | PM2.5, outdoor temperature, humidity, power |
| 8 | 🎨 **Colors** | Accent, text colours |
| 9 | 🎨 **Background** | 16 gradient presets + custom two-colour picker |

---

## 🔌 Entity Reference

### Room entities (per room, up to 8)

| Config key | Entity type | Description |
|---|---|---|
| `entities[n].entity_id` | `climate` | AC unit entity ✅ |
| `entities[n].label` | string | Display name for the room |
| `entities[n].icon` | string | Emoji icon for the room tab |
| `entities[n].area` | string | Room area label (e.g. `25 m²`) |
| `entities[n].image` | string | Custom room photo URL (optional) |
| `entities[n].temp_entity` | `sensor` | Room temperature sensor (if AC has none) |
| `entities[n].humidity_entity` | `sensor` | Room humidity sensor (if AC has none) |

### Environment sensors (optional)

| Config key | Entity type | Description |
|---|---|---|
| `pm25_entity` | `sensor` | PM2.5 fine dust sensor |
| `outdoor_temp_entity` | `sensor` | Outdoor temperature sensor |
| `humidity_entity` | `sensor` | Outdoor humidity sensor |
| `power_entity` | `sensor` | AC power consumption (kW) |

---

## ⚙️ Full Config Reference

| Config key | Type | Default | Description |
|---|---|---|---|
| `language` | string | `vi` | `vi`/`en`/`de`/`fr`/`nl`/`pl`/`sv`/`hu`/`cs`/`it`/`pt` |
| `view_mode` | string | `full` | `full` · `lite` · `super_lite` |
| `popup_style` | string | `normal` | Super Lite selector style: `normal` · `effect` · `wave` |
| `room_count` | number | `4` | Number of rooms to display (1–8) |
| `owner_name` | string | `Smart Home` | Owner name shown in greeting |
| `show_greet` | boolean | `true` | Show greeting row |
| `show_cool` | boolean | `true` | Show Cool mode button |
| `show_heat` | boolean | `true` | Show Heat mode button |
| `show_dry` | boolean | `true` | Show Dry mode button |
| `show_fan_only` | boolean | `true` | Show Fan Only mode button |
| `show_fan` | boolean | `true` | Show fan speed panel |
| `show_swing` | boolean | `true` | Show airflow direction panel |
| `show_preset_bar` | boolean | `true` | Show Eco / Fav / Clean bar |
| `show_status` | boolean | `true` | Show status & sensor block |
| `show_outdoor_temp` | boolean | `true` | Show outdoor temperature metric |
| `show_humidity` | boolean | `true` | Show humidity metric |
| `show_power` | boolean | `true` | Show power consumption metric |
| `show_all_off` | boolean | `true` | Show turn-all-off button |
| `show_timer` | boolean | `true` | Show timer button |
| `show_room_env` | boolean | `false` | Super Lite: show selected room temp & humidity in header (instead of outdoor) |
| `background_preset` | string | `default` | Gradient preset name |
| `bg_color1` | hex | `#001e2b` | Custom gradient colour 1 (top-left) |
| `bg_color2` | hex | `#12c6f3` | Custom gradient colour 2 (bottom-right) |
| `accent_color` | hex | `#00ffcc` | Accent / glow colour |
| `text_color` | hex | `#ffffff` | Primary text colour |
| `entities` | array | — | List of room objects (see above) |
| `pm25_entity` | entity | — | PM2.5 sensor |
| `outdoor_temp_entity` | entity | — | Outdoor temperature sensor |
| `humidity_entity` | entity | — | Outdoor humidity sensor |
| `power_entity` | entity | — | Power consumption sensor |

---

## 📝 Full YAML example

```yaml
type: custom:multi-air-conditioner-card
language: en
view_mode: full
room_count: 4
owner_name: My Home

background_preset: default
accent_color: "#00ffcc"
text_color: "#ffffff"

show_greet: true
show_cool: true
show_heat: true
show_dry: true
show_fan_only: true
show_fan: true
show_swing: true
show_preset_bar: true
show_status: true
show_outdoor_temp: true
show_humidity: true
show_power: true
show_all_off: true
show_timer: true

entities:
  - entity_id: climate.living_room_ac
    label: Living Room
    area: "25 m²"
    icon: 🛋
    image: "https://example.com/photos/living.jpg"   # optional custom photo
    temp_entity: sensor.living_room_temperature       # optional room sensor
    humidity_entity: sensor.living_room_humidity      # optional room sensor
  - entity_id: climate.bedroom_ac
    label: Bedroom
    area: "18 m²"
    icon: 🛌
  - entity_id: climate.kitchen_ac
    label: Kitchen
    area: "20 m²"
    icon: 🍳
  - entity_id: climate.office_ac
    label: Office
    area: "15 m²"
    icon: 💼

pm25_entity: sensor.pm25
outdoor_temp_entity: sensor.outdoor_temperature
humidity_entity: sensor.outdoor_humidity
power_entity: sensor.ac_power_kwh
```

### Super Lite example

```yaml
type: custom:multi-air-conditioner-card
language: en
view_mode: super_lite
popup_style: effect     # normal | effect | wave
show_room_env: true     # show room temp/humidity in header
room_count: 4
entities:
  - entity_id: climate.living_room_ac
    label: Living Room
    icon: 🛋
    temp_entity: sensor.living_room_temperature
    humidity_entity: sensor.living_room_humidity
  - entity_id: climate.bedroom_ac
    label: Bedroom
    icon: 🛌
```

### Lite mode example

```yaml
type: custom:multi-air-conditioner-card
language: en
view_mode: lite
room_count: 4
entities:
  - entity_id: climate.living_room_ac
    label: Living Room
    icon: 🛋
  - entity_id: climate.bedroom_ac
    label: Bedroom
    icon: 🛌
```

---

## 🖥️ Compatibility

| | |
|---|---|
| Home Assistant | 2023.1+ |
| Lovelace | Default & custom dashboards |
| Devices | Mobile & Desktop |
| Dependencies | None — fully standalone |
| Browsers | Chrome, Firefox, Safari, Edge |

---

## 📋 Changelog

### v1.4
- ⚡ New **Super Lite** view mode — ultra-compact single-column layout with large dial, temperature control, HVAC mode selector and room selector
- ✨ **Popup style selector** (Super Lite) — choose between Normal (native), Effect (glass + spring animation) or Wave (glass + wave animation) for mode and room dropdowns
- 🌡️ **Per-room temperature sensor** — set a dedicated `temp_entity` per room to override `current_temperature` when the AC entity doesn't provide it
- 💧 **Per-room humidity sensor** — set a dedicated `humidity_entity` per room for accurate indoor humidity display
- 🏠 **Custom room photo** — set a custom image URL per room via `entities[n].image`
- 🔵 **Set-point inner ring** — thin arc inside the temperature dial shows the target set-point temperature, coloured by active HVAC mode
- 💧 **Room humidity in photo badge** — humidity value now displayed alongside temperature in the room photo corner (Full/Lite modes)
- 👁️ **show_room_env** toggle — Super Lite header can show selected room's own temperature & humidity instead of outdoor sensor data
- 🔧 **Swing mode fix** — swing cycle now reads `swing_modes` attribute from the entity, preventing "invalid swing mode" errors on ACs with limited swing options
- 🐛 Bug fixes and layout improvements

### v1.3
- 🖥️ New **Lite view mode** — compact layout ideal for mobile or sidebar dashboards
- 👁️ **Per-element visibility toggles** — show/hide greeting, each HVAC mode button, fan, swing, Eco bar, status block, metrics, timer and all-off button individually
- 🐛 Bug fixes and stability improvements

### v1.2
- 🇵🇹 New language — Português (11 languages total)
- 🌡️ Dynamic temperature colour on dial — blue (cold) → cyan → green → orange → red (hot)
- ⏱️ Timer overhaul — 8 preset durations (30m · 1h · 1.5h · 2h · 3h · 4h · 6h · 8h) + free custom-minute input
- 🔢 Room tabs enlarged — always shows 4 rooms, scrollable when more than 4

### v1.1
- 🔢 Configurable room count — 1 to 8 rooms via editor slider
- 🌐 10-language support with real flag images
- 🎨 16 background gradient presets
- 🎛️ Full visual editor — entity pickers, accordion sections, 3-layer colour picker
- 🐛 Focus fix — text inputs no longer lose focus while typing

### v1.0
- 🚀 Initial release — 4-room AC control card

---

## 📄 License

MIT License — free to use, modify, and distribute.
If you find this useful, please ⭐ **star the repo**!

---

## 🙏 Credits

Designed and developed by **[@doanlong1412](https://github.com/doanlong1412)** from 🇻🇳 Vietnam.
