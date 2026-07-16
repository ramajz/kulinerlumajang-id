# KulinerLumajang.id — Design System

> **Status:** DOKUMENTASI — Untuk implementasi SaaS dan referensi desain
> **Last Updated:** Juli 2026

---

## Color Palette

### Primary Colors

| Nama | Hex | Penggunaan |
|------|-----|------------|
| **Red** | `#E63946` | CTA utama, tombol primary, badge Featured |
| **Red Dark** | `#C1121F` | Hover state CTA |
| **Yellow** | `#FFB703` | Badge, highlight, accent |
| **Yellow Light** | `#FFC940` | Hover state yellow |
| **Orange** | `#FB8500` | Badge Premium, secondary accent |

### Neutral Colors

| Nama | Hex | Penggunaan |
|------|-----|------------|
| **Dark** | `#1D3557` | Teks utama, section gelap |
| **Dark Light** | `#2B3A55` | Teks sekunder |
| **Cream** | `#F8F9FA` | Background utama |
| **Cream Dark** | `#E9ECEF` | Border, divider |
| **White** | `#FFFFFF` | Card, surface |

### Special Colors

| Nama | Hex | Penggunaan |
|------|-----|------------|
| **WhatsApp Green** | `#25D366` | Tombol Chat WhatsApp |

---

## Typography

### Font Families

| Role | Font | Fallback |
|------|------|----------|
| **Display/Headings** | Playfair Display | serif |
| **Body** | DM Sans | -apple-system, BlinkMacSystemFont, sans-serif |
| **Utility/Numbers** | JetBrains Mono | monospace |

### Font Weights

| Font | Weights |
|------|---------|
| Playfair Display | 500, 700, 800 |
| DM Sans | 400, 500, 600, 700 |
| JetBrains Mono | 500, 700 |

### Type Scale

| Element | Size | Weight | Font |
|---------|------|--------|------|
| h1 (Hero) | clamp(36px, 5vw, 56px) | 800 | Playfair Display |
| h2 (Section) | clamp(28px, 4vw, 40px) | 700 | Playfair Display |
| h3 (Card) | 20px | 700 | DM Sans |
| Body | 16-18px | 400-500 | DM Sans |
| Small/Label | 12-14px | 500-700 | DM Sans |
| Numbers/Prices | 28-32px | 700 | JetBrains Mono |

---

## Spacing & Radius

### Border Radius

| Token | Value | Penggunaan |
|-------|-------|------------|
| `--radius-sm` | 10px | Tombol, badge kecil |
| `--radius` | 16px | Card, search bar |
| `--radius-lg` | 24px | Hero card, listing card |

### Shadows

| Token | Value |
|-------|-------|
| `--shadow-sm` | 0 2px 8px rgba(29, 53, 87, 0.08) |
| `--shadow-md` | 0 8px 24px rgba(29, 53, 87, 0.12) |
| `--shadow-lg` | 0 16px 48px rgba(29, 53, 87, 0.16) |

---

## Responsive Breakpoints

| Breakpoint | Layout |
|------------|--------|
| > 1024px | 2-column grid (hero), 3-column (features/listings) |
| 768px - 1024px | 1-column hero, 2-column grid |
| < 768px | Single column, hide nav links |
| < 480px | Full-width buttons, stacked elements |

---

## Component Examples

### Button Primary
```css
background: var(--red);
color: white;
padding: 16px 28px;
border-radius: var(--radius-sm);
font-weight: 700;
```

### Button Secondary
```css
background: white;
border: 1px solid var(--cream-dark);
color: var(--dark);
padding: 16px 28px;
border-radius: var(--radius-sm);
```

### Card
```css
background: white;
border: 1px solid var(--cream-dark);
border-radius: var(--radius-lg);
box-shadow: var(--shadow-sm);
```

---

## Reference

- **Source:** WordPress Fast Food Delivery Theme
- **File:** ~/kulinerlumajang-landing.html
- **Holographic Fact ID:** 42

---

## Implementation Notes

1. Selalu gunakan CSS variables untuk konsistensi
2. Font Playfair Display hanya untuk headings/display
3. JetBrains Mono untuk angka, harga, dan rating
4. WhatsApp Green (#25D366) khusus untuk tombol chat
5. Hover state harus ada untuk semua interactive elements
6. Animasi: fadeInUp dengan reduced-motion support
