# 🎨 DESIGN GUIDE - Visual Style & Components

## 📐 Design System

### **Color Palette**

```
PRIMARY COLORS
┌─────────────────────────────────────────┐
│ Majestic Blue      #1B3A8B              │
│ ██████████████████████ (Primary Brand)  │
│ Usage: Main CTA, Headers, Accent        │
└─────────────────────────────────────────┘

┌─────────────────────────────────────────┐
│ Light Blue         #E8F0FE              │
│ ██████████████████████ (Background)     │
│ Usage: Page background, Card hover      │
└─────────────────────────────────────────┘

┌─────────────────────────────────────────┐
│ Gold               #D4AF37              │
│ ██████████████████████ (Premium Accent) │
│ Usage: Badges, Icons, Special Elements  │
└─────────────────────────────────────────┘

NEUTRAL COLORS
┌─────────────────────────────────────────┐
│ White              #FFFFFF              │
│ ██████████████████████ (Clean Base)     │
│ Usage: Main background, Cards           │
└─────────────────────────────────────────┘

┌─────────────────────────────────────────┐
│ Dark Gray          #2C3E50              │
│ ██████████████████████ (Text Primary)   │
│ Usage: Headings, Body text              │
└─────────────────────────────────────────┘

┌─────────────────────────────────────────┐
│ Light Gray         #F5F5F5              │
│ ██████████████████████ (Dividers)       │
│ Usage: Borders, Separators              │
└─────────────────────────────────────────┘

SEMANTIC COLORS
┌─────────────────────────────────────────┐
│ Success Green      #27AE60              │
│ ██████████████████████ (Positive)       │
│ Usage: Success messages, Check icons    │
└─────────────────────────────────────────┘

┌─────────────────────────────────────────┐
│ Error Red          #E74C3C              │
│ ██████████████████████ (Negative)       │
│ Usage: Errors, Warnings, Alerts         │
└─────────────────────────────────────────┘

┌─────────────────────────────────────────┐
│ Warning Orange     #F39C12              │
│ ██████████████████████ (Caution)        │
│ Usage: Warnings, Pending status         │
└─────────────────────────────────────────┘

┌─────────────────────────────────────────┐
│ Info Blue          #3498DB              │
│ ██████████████████████ (Information)    │
│ Usage: Info messages, Links             │
└─────────────────────────────────────────┘
```

### **Typography Hierarchy**

```
HEADINGS
┌────────────────────────────────────────────┐
│ H1: 48px | Poppins Bold | Leading 1.1      │
│ SELAMAT DATANG DI SMA NEGERI 1            │
│ Usage: Page titles, Hero section           │
└────────────────────────────────────────────┘

┌────────────────────────────────────────────┐
│ H2: 36px | Poppins Bold | Leading 1.2      │
│ Sambutan Kepala Sekolah                   │
│ Usage: Section titles                      │
└────────────────────────────────────────────┘

┌────────────────────────────────────────────┐
│ H3: 28px | Poppins SemiBold | Leading 1.3  │
│ Program Unggulan                           │
│ Usage: Subsection titles                   │
└────────────────────────────────────────────┘

┌────────────────────────────────────────────┐
│ H4: 20px | Poppins Medium | Leading 1.4    │
│ Ekstrakurikuler Kami                       │
│ Usage: Component titles                    │
└────────────────────────────────────────────┘

BODY TEXT
┌────────────────────────────────────────────┐
│ Body Large: 18px | Inter Regular | 1.6     │
│ Ini adalah teks utama untuk paragraf       │
│ Usage: Introductory text                   │
└────────────────────────────────────────────┘

┌────────────────────────────────────────────┐
│ Body: 16px | Inter Regular | 1.6           │
│ Ini adalah teks normal untuk konten        │
│ Usage: Main content paragraphs             │
└────────────────────────────────────────────┘

┌────────────────────────────────────────────┐
│ Body Small: 14px | Inter Regular | 1.5     │
│ Ini adalah teks kecil untuk detail         │
│ Usage: Secondary text, captions            │
└────────────────────────────────────────────┘

┌────────────────────────────────────────────┐
│ Caption: 12px | Inter Regular | 1.4        │
│ Teks sangat kecil untuk metadata           │
│ Usage: Labels, timestamps, small notes     │
└────────────────────────────────────────────┘

CODE/MONOSPACE
┌────────────────────────────────────────────┐
│ Code: 14px | Fira Code Regular | 1.4       │
│ const website = "smanegeri1.sch.id"        │
│ Usage: Code blocks, technical terms        │
└────────────────────────────────────────────┘
```

---

## 🖼️ Component Library

### **Buttons**

```
PRIMARY BUTTON (CTA)
┌─────────────────────────────────┐
│      📌 DAFTAR SEKARANG          │  Background: #1B3A8B
│                                 │  Text: White
│  Padding: 12px 24px             │  Hover: Darken 10%
│  Border-radius: 8px             │  Transition: 200ms
│  Font: Poppins 16px SemiBold     │
└─────────────────────────────────┘

SECONDARY BUTTON
┌─────────────────────────────────┐
│      📌 PELAJARI LEBIH LANJUT    │  Background: Transparent
│                                 │  Border: 2px #1B3A8B
│  Padding: 10px 20px             │  Text: #1B3A8B
│  Border-radius: 8px             │  Hover: BG Light Blue
│  Font: Poppins 16px Medium       │
└─────────────────────────────────┘

TERTIARY BUTTON
┌─────────────────────────────────┐
│      📌 BACA BERITA              │  Background: #F5F5F5
│                                 │  Text: #2C3E50
│  Padding: 10px 16px             │  Hover: BG Light Gray
│  Border-radius: 6px             │  No border
│  Font: Inter 14px Regular        │
└─────────────────────────────────┘

ICON BUTTON (Minimal)
┌──────┐
│ 🔍   │  Background: Transparent
│      │  Hover: Light Blue BG
│ 24px │  Padding: 8px
│      │  Border-radius: 50%
└──────┘

SOCIAL BUTTON
┌──────┐
│ f    │  Background: Brand color
│      │  Size: 40x40px
│ 16px │  Border-radius: 8px
│      │  Icon: White
└──────┘
```

### **Cards**

```
NEWS CARD
┌──────────────────────────────────────┐
│ ┌──────────────────────────────────┐ │
│ │     [Featured Image]              │ │  Height: 200px
│ │    (aspect 16:9, cover)           │ │  Object-fit: Cover
│ └──────────────────────────────────┘ │
│                                      │
│ 📌 Akademik                          │  Tag: Small, Gold accent
│                                      │
│ Judul Berita Maksimal 60 Karakter    │  H4, 20px
│                                      │
│ Deskripsi singkat berita sampai      │  Body Small, #666
│ maksimal 2 baris saja...             │
│                                      │
│ 🕐 2 jam lalu  👤 Admin             │  Caption text
│                                      │
│ ┌─ Baca Selengkapnya ─────────────┐ │  Link button
│ └────────────────────────────────┘ │
└──────────────────────────────────────┘

STATS CARD (Counters)
┌─────────────────┐
│    2,450        │  Number: Poppins Bold 36px
│                 │  Blue color
│  Siswa Aktif    │  Label: Inter Regular 14px
│                 │  Dark gray
└─────────────────┘

EVENT CARD
┌───────────────────────────────┐
│ 📅 15 Agustus 2024            │  Metadata: Caption
│                               │
│ Upacara Hari Kemerdekaan      │  Title: H4
│                               │
│ Lapangan Utama, 07:00 WIB     │  Location & Time
│                               │
│ 👥 Semua siswa & guru         │  Attendees
│                               │
│ [Selengkapnya]                │  Link
└───────────────────────────────┘

PROFILE/TEACHER CARD
┌─────────────────────────────────┐
│     ┌─────────────┐             │
│     │   PHOTO     │             │  Photo: 120x120px
│     │ (Avatar)    │             │  Border-radius: 50%
│     └─────────────┘             │
│                                 │
│  Nama Guru Lengkap              │  H4, Poppins
│  Guru Matematika                │  Jabatan, Gray
│                                 │
│  📧 email@example.com           │  Contact small
│  📞 +62-xxx-xxxxxx              │
│                                 │
│  [Lihat Profile]                │  Link button
└─────────────────────────────────┘
```

### **Forms & Inputs**

```
TEXT INPUT
┌─ Label Text ────────────────────────┐
│                                     │
│ ┌───────────────────────────────┐   │  Height: 44px
│ │ Placeholder text...           │   │  Padding: 12px 16px
│ └───────────────────────────────┘   │  Border: 1px #DDD
│  Helper text atau error message    │  Border-radius: 6px
└─────────────────────────────────────┘

SELECT/DROPDOWN
┌─ Kategori Berita ───────────────────┐
│                                     │
│ ┌───────────────────────────────┐   │
│ │ Pilih Kategori         [▼]    │   │
│ └───────────────────────────────┘   │
└─────────────────────────────────────┘

CHECKBOX
┌─────────────────────────────────────┐
│ ☑ Saya setuju dengan syarat & KB    │  Checkmark: Gold
│ ☐ Notifikasi email bulanan          │  Label: Body text
└─────────────────────────────────────┘

RADIO BUTTONS
┌─────────────────────────────────────┐
│ ◉ Jalur Reguler                     │  Selected: Gold
│ ○ Jalur Prestasi                    │  Unselected: Gray
│ ○ Jalur Pindahan                    │
└─────────────────────────────────────┘

TOGGLE SWITCH
┌──────────────────────────────────────┐
│ Aktifkan Dark Mode        [●────]    │  ON: Blue
│                                      │  OFF: Gray
│                           [────●]    │  Smooth animation
└──────────────────────────────────────┘
```

### **Navigation**

```
NAVBAR (Desktop)
┌────────────────────────────────────────────────────────────┐
│ 🏫 SMA Negeri 1  │ Home │ Profil │ Akademik │ ... │ 🔍 🌙 │
└────────────────────────────────────────────────────────────┘

NAVBAR (Mobile - Hamburger)
┌─────────────────────────────┐
│ 🏫 SMA Negeri 1      [☰] [🔍]│
└─────────────────────────────┘

DROPDOWN MENU
┌────────────────┐
│ ▼ Akademik     │
├────────────────┤
│ • Kurikulum    │
│ • Kalender     │
│ • Guru & Staf  │
│ • Jadwal       │
└────────────────┘

BREADCRUMB
Home › Akademik › Kurikulum
```

### **Modals & Alerts**

```
MODAL DIALOG
┌─────────────────────────────────────┐
│  ✕ Judul Modal                      │  Header: H3
├─────────────────────────────────────┤
│                                     │
│  Konten modal dengan pesan penting. │
│  Dapat berisi form atau informasi.  │
│                                     │
├─────────────────────────────────────┤
│       [Batal]        [Konfirmasi]   │  Buttons: Primary/Secondary
└─────────────────────────────────────┘

SUCCESS ALERT
┌─────────────────────────────────────┐
│ ✓ Pesan berhasil dikirim!           │  Green: #27AE60
│                                     │  Icon: Checkmark
│ Terima kasih sudah menghubungi kami │
└─────────────────────────────────────┘

ERROR ALERT
┌─────────────────────────────────────┐
│ ✕ Terjadi kesalahan!                │  Red: #E74C3C
│                                     │  Icon: X mark
│ Username atau password salah        │
└─────────────────────────────────────┘

WARNING ALERT
┌─────────────────────────────────────┐
│ ⚠ Perhatian!                        │  Orange: #F39C12
│                                     │  Icon: Triangle
│ Jadwal PPDB akan ditutup dalam 5 jam│
└─────────────────────────────────────┘
```

---

## 📏 Spacing & Layout

### **Spacing Scale**
```
4px   - Base unit
8px   - xs (padding small elements)
12px  - sm (padding elements)
16px  - md (standard padding)
24px  - lg (section margins)
32px  - xl (large spacing)
48px  - 2xl (major sections)
64px  - 3xl (page sections)
```

### **Border Radius**
```
2px  - Sharp (borders, thin lines)
4px  - Subtle (small components)
6px  - Standard (inputs, buttons)
8px  - Cards (medium components)
12px - Large (major components)
50%  - Circular (avatars, badges)
```

### **Box Shadows**
```
Shadow-sm:  0 1px 2px 0 rgba(0,0,0,0.05)
Shadow-md:  0 4px 6px -1px rgba(0,0,0,0.1)
Shadow-lg:  0 10px 15px -3px rgba(0,0,0,0.1)
Shadow-xl:  0 20px 25px -5px rgba(0,0,0,0.1)
```

---

## 📱 Responsive Breakpoints

```
Mobile:      320px - 480px   (xs)
Mobile+:     481px - 640px   (sm)
Tablet:      641px - 1024px  (md/lg)
Desktop:     1025px - 1440px (xl)
Desktop+:    1441px+         (2xl)

GRID COLUMNS:
Mobile:  1 column
Tablet:  2-3 columns
Desktop: 4 columns
```

---

## 🎬 Animations & Transitions

### **Timing Functions**
```
ease-in:     0.25s cubic-bezier(0.4, 0, 1, 1)
ease-out:    0.25s cubic-bezier(0, 0, 0.2, 1)
ease-in-out: 0.25s cubic-bezier(0.4, 0, 0.2, 1)
linear:      0.25s linear
```

### **Transitions**
```
Fast:   150-200ms  (hover states)
Medium: 300-350ms  (modal transitions)
Slow:   500-600ms  (page transitions)
```

### **Effects**
- **Fade In/Out:** Opacity 0 → 1
- **Slide In:** Transform translateY/X
- **Scale:** Transform scale
- **Rotate:** Transform rotate
- **Blur:** Backdrop filter blur

---

## ✨ Micro-interactions

```
BUTTON HOVER
- Background color fade (200ms)
- Slight scale up (1.02)
- Shadow elevation

INPUT FOCUS
- Border color to blue
- Shadow blue glow
- Cursor active

LINK HOVER
- Color transition to blue
- Underline fade in
- Slight color darken

CARD HOVER
- Shadow elevation
- Transform translateY (-2px)
- Smooth 250ms transition
```

---

## 🌙 Dark Mode Support

```
Light Mode (Default)
- Background: #FFFFFF
- Text: #2C3E50
- Borders: #E8E8E8

Dark Mode
- Background: #1A1A1A
- Text: #E0E0E0
- Borders: #333333
- Accent brightness: +10%
```

---

## ♿ Accessibility Guidelines

- ✅ Color contrast ratio 4.5:1 minimum
- ✅ Focus states clearly visible
- ✅ Semantic HTML (h1, h2, button, etc)
- ✅ ARIA labels for screen readers
- ✅ Keyboard navigation support
- ✅ Alt text for all images
- ✅ Form labels associated with inputs
- ✅ Skip-to-content link

---

## 🎨 Component Usage Examples

See `/components/` folder for implementation examples in React/TypeScript with Tailwind CSS.

Common patterns:
- Button variants (primary, secondary, tertiary, icon)
- Card layouts (news, stats, profile)
- Form components (input, select, checkbox)
- Navigation (navbar, footer, breadcrumb)
- Modals (alert, confirm, custom)
- Lists & Tables
- Carousels & Sliders
- Accordion & Tabs

---

**Status:** ✅ Design Guide Complete

*Untuk implementasi, lihat Storybook atau components folder.*
