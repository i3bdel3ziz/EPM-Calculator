# 📊 EPM Performance Bonus Calculator

> 💡 Annual bonus projection based on performance rating

A clean, minimalist web-based calculator for Enterprise Performance Management (EPM) bonus projections. Built as a single-file HTML application — no frameworks, no dependencies, no server required.

🌐 **Live Demo:** `https://i3bdel3ziz.github.io/EPM-Calculator`


---

## 🗂️ Overview

The EPM Performance Bonus Calculator helps employee instantly to calculate performance linked bonus payments based on an employee's monthly basic salary and decimal performance rating. Results are displayed in real time with full breakdown, visual gauge, and export functionality.

All calculations are based on Monthly Basic Salary and follow the defined performance band structure per grade section.

---

## ✨ Features

### 📥 Inputs
- 🏅 **Grade Section selector** — dropdown to select the employee's grade (e.g. MMS), extensible for future grade sections
- 💰 **Monthly Basic Salary** — QAR input with live calculation
- ⏱️ **Decimal Rating (1.0–5.0)** — numeric input with slider sync and real-time band detection
- ✅ **Input validation** — friendly error message if rating is entered outside the 1.0–5.0 range
- 💾 **Input memory** — last used grade, salary and rating are saved automatically via browser localStorage

### 📤 Results
- 💵 **Bonus Payment (QAR)** — large, prominently displayed output
- 🧮 **Contextual breakdown** — equivalent salary months, annual package total, and bonus as % of annual salary
- 📊 **Salary breakdown chart** — horizontal bar showing the split between annual base and bonus
- 🏷️ **Performance Label** — badge showing band name (e.g. Exceeding)
- 🔢 **Rounded Rating, Bonus Multiple, Rating Band** — supporting result fields

### 🎨 Visual Design
- 🎨 **Band color system** — every element (accent strip, gauge, slider, dots, badges) responds to the active performance band:
  - 🔴 Needs Development & Marginally Below Target — light red
  - 🔵 Solid Performer — deep blue
  - 🟢 Exceeding — light warm green
  - 🟢 Outstanding — deep sage green
- 🔠 **Typographic scaling** — bonus amount grows larger as performance band increases
- ✨ **Micro-animations** — bonus pop, badge slide-in, and staggered month dots on band change
- 📏 **Rating gauge** — live fill bar with band segment labels
- 🔵 **Bonus month dots** — 10 dots that illuminate in band color as months are earned

### 📋 Reference Table
- Full performance band table with ranges, labels, months, and live bonus range (QAR) calculated against the current salary
- Active row highlighted in band color

### 📈 Bonus Projection Chart
- 🗺️ **Full rating range view** — canvas-rendered chart plotting every 0.1 rating increment (1.0–5.0) against bonus payment (QAR) for the current salary
- 🎨 **Band-colored line & fill** — each performance band segment is drawn in its own band color with a gradient fill beneath
- 📍 **Selected rating highlight** — a dashed vertical line, glowing dot marker, and bonus label pin mark the exact current rating on the chart
- 🟦 **Band background zones** — subtle color washes behind each band segment for instant visual orientation
- 🖱️ **Hover tooltip** — mousing over any point on the chart shows the rating and projected bonus for that position
- 📱 **Responsive canvas** — redraws automatically on window resize to fit any screen width

### 📦 Export
- 📥 **Export CSV** — downloads a formatted `.csv` summary with all inputs and results, UTF-8 BOM encoded for correct Excel rendering

### 📱 Responsive Design
- Fully responsive across desktop 🖥️, tablet 📲 (≤768px) and mobile 📱 (≤480px)
- Bonus Range column hidden on small screens to preserve table readability

---

## ➕ Adding a New Grade Section

The calculator is designed to support multiple grade sections. To add a new one, open `index.html` and locate the `GRADES` object in the `<script>` section:

```javascript
const GRADES = {
  "MMS": {
    bands: [ ... ],
    lookup: { ... }
  },

  // ➕ Add your new grade section here:
  "Senior": {
    bands: [
      { range:"1.0–1.9", min:1.0, max:1.9, rounded:1, label:"Needs Development",       months:0  },
      { range:"2.0–2.9", min:2.0, max:2.9, rounded:2, label:"Marginally Below Target",  months:0  },
      { range:"3.0–3.7", min:3.0, max:3.7, rounded:3, label:"Solid Performer",          months:5  },
      { range:"3.8–4.4", min:3.8, max:4.4, rounded:4, label:"Exceeding",                months:8  },
      { range:"4.5–5.0", min:4.5, max:5.0, rounded:5, label:"Outstanding",              months:12 },
    ],
    lookup: {
      // map each 0.1 rating increment to a bonus multiple
      10:0, 11:0, ... 50:12
    }
  }
};
```

✅ The new section will appear automatically in the Grade Section dropdown. No other changes required.


---

## 🛠️ Technology

| Layer          | Detail                                       |
|----------------|----------------------------------------------|
| 🧱 Markup      | Semantic HTML5                               |
| 🎨 Styling     | Vanilla CSS with custom properties           |
| ⚙️ Logic       | Vanilla JavaScript (ES6+)                    |
| 🔤 Fonts       | IBM Plex Sans + IBM Plex Mono (Google Fonts) |
| 🖼️ Icons       | Inline SVG (no external icon library)        |
| 💾 Storage     | Browser localStorage (preferences only)     |
| 📦 Export      | Blob CSV download with UTF-8 BOM             |
| 📈 Chart       | Native Canvas 2D API (no chart library)      |

---

## 📋 Changelog

### 🆕 v1.3.0 — 2026-03-06
- 📈 Added **Bonus Projection Chart** — full-width canvas chart showing rating vs bonus payment across all bands
- 🎨 Band-colored line segments and gradient fills per performance band
- 📍 Selected rating highlighted with dashed vertical line, glowing dot marker, and bonus label pin
- 🖱️ Hover tooltip shows projected bonus at any rating point
- 🟦 Subtle band background zones for visual orientation
- 📱 Chart redraws responsively on window resize
- 📝 Updated README with chart documentation and icons

### v1.2.0 — 2026-03-06
- 🖼️ Added inline SVG icons throughout: header logo mark, section labels, field labels, result rows
- 🔲 Pushed all text and icon colors to maximum contrast (`--ink #1a1916`) for clarity
- 📋 Table text color updated to full dark for improved readability

### v1.1.0 — 2026-03-06
- 📥 Added Export CSV with UTF-8 BOM (fixes special character rendering in Excel)
- 📊 Added salary breakdown bar chart in results panel
- 📱 Added responsive design: tablet (≤768px) and mobile (≤480px) breakpoints
- 🙈 Bonus Range (QAR) column hidden on mobile to preserve layout
- ✏️ Updated subtitle to "Annual bonus projection based on performance rating"
- 💾 Input memory via localStorage — grade, salary, and rating persist between sessions
- 🗑️ Clear fields button to reset all inputs and results

### v1.0.0 — 2026-03-06
🎉 **Initial release**
- 🏅 Grade Section dropdown (MMS) with extensible data structure
- 💰 Monthly Basic Salary and Decimal Rating inputs with slider sync
- ⚡ Real-time results: Bonus Payment, Performance Label, Rounded Rating, Bonus Multiple, Rating Band
- 🎨 Band color system across results panel, gauge, slider, month dots, and badges
- 🔠 Typographic scaling on bonus amount by performance band
- ✨ Micro-animations: bonus pop, badge slide-in, staggered dot animation on band change
- 📏 Rating Gauge with live fill and segment labels
- 🔵 10 Bonus Month dots with band-colored fill
- 📋 Reference Table with live Bonus Range (QAR) column
- 🧮 Contextual result lines: salary multiple, annual package, bonus percentage
- ✅ Input validation with friendly error messaging for out-of-range ratings
- 💡 Inline band hint indicator below rating slider
- 📋 Copy Summary to clipboard
- ⚡ Single-file deployment, no dependencies

---

## 📜 License

This project is intended for internal employee use. All rights reserved.

---

*🏢 Built with ❤️ from Qatar*
