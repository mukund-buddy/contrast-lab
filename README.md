# 🎨 Contrast Lab

![vanilla JS](https://img.shields.io/badge/vanilla-JS-f7df1e?logo=javascript&logoColor=black)
![WCAG 2.x](https://img.shields.io/badge/WCAG-2.x-e63329)
![license](https://img.shields.io/badge/license-MIT-4dd0e1)

**Paste your CSS → every colour gets extracted → every text/background pair gets a real WCAG contrast ratio → the failures get ranked worst-first with a one-click fix.**

> Part of [The Antigle](https://github.com/mukund-buddy) 🔥 — AI-assisted build, hand-tested.
> The luminance math is checked against known values (`#000`/`#fff` = 21:1, `#767676`/`#fff` = 4.54:1).

**Live demo:** _coming soon_ · [Repository](https://github.com/mukund-buddy/contrast-lab)

---

## 🎯 Why This Exists

Two-colour contrast checkers are everywhere. They're also useless the moment your
palette has more than two colours — because the pair you got wrong is never the pair
you thought to check.

Contrast Lab audits **the whole matrix**: every colour it can find crossed with every
other one, sorted so the worst offenders sit at the top. If the paste is real CSS, it
also lifts out the pairs your `color:` / `background:` rules *actually declare* and
shows those first.

## ✨ Features

- **Full N×N audit** — up to 15 colours, every ordered pair, worst first
- **Declared-pairs section** — parsed from real `color` / `background` rules, with selectors
- **AA + AAA badges** — normal and large-text thresholds, pass/fail
- **Worst-offender hero** — the failure rendered at real body-text size, so you *see* it
- **Darken / Lighten → AA** — hue and saturation preserved, lightness adjusted until the ratio clears 4.50:1
- **Quick pair mode** — two colour pickers, live ratio, for when you don't have CSS to paste
- **Copy report** — plain-text failure list for issues/PRs
- **Handles hex, `rgb()`, `hsl()` and 18 named colours**

## 🚀 Quick Start

```bash
git clone https://github.com/mukund-buddy/contrast-lab
start index.html
```

Paste CSS → **Run audit** → fix from the top of the table down.

## 🧱 How It Works

```
index.html   →  input band + summary + hero + matrix tables
style.css    →  Swiss-poster theme (newsprint, signal red, zero radius)
app.js       →  parseColor → luminance → ratio → rank → fix
```

The WCAG 2.x relative-luminance formula is implemented literally (sRGB channel
linearisation, `.2126/.7152/.0722` weights). Everything — including the fix
suggestion — is a few hundred lines of plain JS you can read in one sitting.

## ✅ Verified

| Pair | Expected | This tool |
|------|----------|-----------|
| `#000` on `#fff` | 21.00 | 21.00 |
| `#767676` on `#fff` | 4.54 | 4.54 |
| `#ff0000` on `#fff` | 4.00 | 4.00 |
| `#808080` on `#fff` | 3.95 | 3.95 |
| `#fff` on `#0000ff` | 8.59 | 8.59 |

## 🗺️ Roadmap

- [x] Full-matrix audit + fixes (v1)
- [ ] CSS variable resolution (`var(--x)` → its declared value)
- [ ] Export fixed palette as CSS custom properties
- [ ] APCA (WCAG 3) scoring alongside legacy ratios

## 🧑‍💻 Honest Note

AI-assisted, human-tested. Ratios were cross-checked by hand before shipping; the
auto-fix is a *starting point* — re-check the result in your real component, because
large text, bold weights and images behind text change the rules.

## 🏷️ Suggested GitHub Topics

`a11y` `accessibility` `contrast` `wcag` `color` `design-tools` `frontend` `vanilla-js` `client-side` `the-antigle`

Add them under **Settings → General → Topics**.

---

Part of **[The Antigle](https://github.com/mukund-buddy)** — browser tools and web products, built with AI and finished by hand.

## 📄 License

MIT
