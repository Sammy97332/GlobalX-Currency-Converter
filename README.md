# 💱 GlobalX Currency Converter

A clean, lightweight, and fully responsive currency converter built with **vanilla HTML, CSS, and JavaScript** — zero dependencies, no build tools, no frameworks.

---

## 🖥️ Live Demo

> Open `index.html` directly in your browser — no server required.

---

## ✨ Features

- **Currency conversion** across 6 major currencies (USD, EUR, GBP, GHS, JPY, CNY)
- **Swap button** to instantly reverse the conversion direction
- **Conversion history** table with smooth fade-in animation
- **Dark / Light theme** toggle, persisted via `localStorage`
- **Keyboard support** — press `Enter` in the amount field to convert
- **Responsive design** — works on desktop, tablet, and mobile
- **Accessible markup** with ARIA labels and live regions
- **Zero dependencies** — runs offline with no internet connection needed

---

## 📁 Project Structure

```
GlobalX-Currency-Converter/
│
├── index.html              # Main HTML page
│
├── assets/
│   ├── css/
│   │   └── style.css       # All styles (design tokens, layout, components)
│   └── js/
│       └── script.js       # Conversion logic, history, theme toggle
│
└── README.md               # Project documentation
```

---

## 🚀 Getting Started

1. **Clone the repository:**
   ```bash
   git clone https://github.com/SamuelNkrumah/GlobalX-Currency-Converter.git
   ```

2. **Open in your browser:**
   ```bash
   cd GlobalX-Currency-Converter
   open index.html   # macOS
   # or double-click index.html on Windows/Linux
   ```

No npm install. No build step. Just open and go.

---

## 💱 Supported Currencies

| Code | Currency           |
|------|--------------------|
| USD  | US Dollar          |
| EUR  | Euro               |
| GBP  | British Pound      |
| GHS  | Ghanaian Cedi      |
| JPY  | Japanese Yen       |
| CNY  | Chinese Yuan       |

> **Note:** Exchange rates are static reference values from **November 2025** and are intended for demonstration purposes only. For production use, integrate a live API such as [Frankfurter](https://www.frankfurter.app/) or [ExchangeRate-API](https://www.exchangerate-api.com/).

---

## 🛠️ Built With

- **HTML5** — semantic markup
- **CSS3** — custom properties (design tokens), CSS Grid, Flexbox, animations
- **Vanilla JavaScript (ES6+)** — `'use strict'`, clean module-style organization

---

## 🔮 Future Improvements

- [ ] Integrate a live exchange rate API for real-time rates
- [ ] Add more currencies (NGN, ZAR, CAD, AUD, etc.)
- [ ] Export conversion history as CSV
- [ ] Add a rates table / multi-currency dashboard
- [ ] PWA support (offline caching via Service Worker)

---

## 👤 Author

**Nkrumah Samuel Kojo**
- Student ID: PUIS/23210007
- Course: PBSE304 · Pentecost University, Ghana
- GitHub: [@SamuelNkrumah](https://github.com/SamuelNkrumah)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

> _Built as a coursework project at Pentecost University — November 2025._
