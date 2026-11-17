# Vessa — Marlow & Fern Inventory Management Dashboard

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-blue?style=for-the-badge&logo=github)](https://mrchandrayee.github.io/vessa-inventory-dashboard/)
[![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org) [![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org) [![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](./LICENSE)

Standalone frontend reconstruction from the uploaded 7.13-second screen recording (720 × 1280, 30 fps).

## Run
1. Extract `vessa-inventory-dashboard.zip`.
2. Open `index.html` in a modern browser.
3. No npm install or build step is required.

Optional local server:
```bash
python3 -m http.server 8000
```
Open `http://localhost:8000`.

## Product and screens observed in the video

Brand: **Vessa**  
Workspace: **Marlow & Fern**  
Signed-in user shown: **Imani Okafor**  
Date shown: **Monday, Oct 19 · 10:40 AM**

### Overview
Greeting: “Welcome back, Imani!” Supporting text says there are 2 orders to ship and 2 batches waiting on QA.

Summary cards shown:
- Units on hand — 3,163 (video later animates to 4,345); 12 SKUs · 3 sites.
- Total stock value — $23,323 (video later animates to $32,041); at cost.
- Low stock items — 5 (later 7); 3 products · 4 materials; 1 out.

Inventory statistics chart shows Stock in, Stock out and Stock value, with Monthly selector and Jan–Oct labels. A tooltip for Oct reads Stock in $6,232, Stock out $4,732, Stock value $32,041.

Sales overview gauge animates from 47.0% to 69.8%. Number of sales animates from 29 to 48; total sales from $10,282 to $17,113.

### Catalog
Header text: “Finished goods across Riverside DC, the lab and the Studio Shop”.
Summary:
- SKUs 12; 5 categories.
- Units on hand 4,318; 3 locations.
- Retail value $110,598.
- Low or out 3; 1 out at the DC.

Category filters: All, Cleanse, Treat, Moisturise, Protect, Body. Controls include Low only, search by Name/SKU/barcode, Sort: Name, Grid and List.

Visible products:
- Barrier Fluid SPF 30 — 50 ml · MF-BPS-50; Out at DC.
- Calendula Rescue Balm — 15 ml · MF-CRB-15.
- Calendula Rescue Balm — 50 ml · MF-CRB-50; Running low.
- Camellia Cleansing Oil — 30 ml · MF-CLO-30.

### Reports
The recording shows a Reports screen with 30 days / 90 days / This year, Export CSV, six metric cards (Revenue, Orders, Units sold, Avg order value, Stock value, Gross margin), and a Revenue line chart with Day / Week / Month, channel filters (All channels, Wholesale, Online store, Studio shop) and Compare toggle.

Readable values in one frame:
- Revenue $25,537
- Orders 73
- Units sold 1,843
- Avg order value $349.81
- Stock value $32,035
- Gross margin 67.2%

### Sales
The Sales screen shows Revenue, Orders, Average order and Units sold cards; Revenue by channel line chart; Sales by state list. Visible state ranking:
- Texas — $5,574
- Vermont — $5,088
- Oregon — $2,988
- North Carolina — $2,812
- Georgia — $2,649

## Readable source code shown in the video

The bottom code panel is titled `ui.ts`, with breadcrumb `src > ui.ts > wipe`. This is the legible TypeScript transcription from the recording. The clip ends during the function; no hidden continuation is inferred.

```ts
// dark mode opens as a circle from the button you pressed
export function setTheme(p: ThemePref, origin?: Element | null) {
  wipe(origin, () => { mem.theme = p; applyTheme(); });
}

export function wipe(origin: Element, change: () => void) {
  const r = origin.getBoundingClientRect();
  const x = r.left + r.width / 2, y = r.top + r.height / 2;
  const end = Math.hypot(Math.max(x, innerWidth - x),
                         Math.max(y, innerHeight - y));
  document.startViewTransition(change).ready.then(() => {
    document.documentElement.animate({ clipPath: [
      `circle(0px at ${x}px ${y}px)`,
      `circle(${end}px at ${x}px ${y}px)`,
    ] }, { duration: 620, easing: 'cubic-bezier(.65,0,.35,1)',
      pseudoElement: '::view-transition-new(root)' });
  });
}
```

The screen shows `ThemePref`, `mem`, `applyTheme` and the native View Transition API; their declarations are outside the visible snippet.

## Included interactions in this reconstruction
- Sidebar navigation: Overview, Products, Orders, Stock, Reports, Customers, Settings.
- Overview / Activity / Alerts top tabs.
- Animated inventory bar chart and sales goal gauge.
- Catalog search, category filters, low-stock-only filter, sorting, Grid/List layout.
- Product CSV export.
- Stock search, adjustment dialog, and CSV export.
- Order search and local order-status changes.
- Add customer, create order and make-batch dialogs.
- Report date range, chart interval, channel filters and Compare toggle.
- Sales-by-state panel.
- Alerts review and activity log.
- Light/dark theme with circular reveal animation from the clicked theme button.
- Keyboard shortcut Cmd/Ctrl + K for search.

## Files
- `index.html` — dashboard structure and pages.
- `styles.css` — responsive visual system, cards, charts, catalogue and circular theme reveal.
- `app.js` — sample data, navigation, chart rendering, filters, stock/order/customer interactions.
- `README.md` — screen observations, readable source snippet and run instructions.

## Accuracy / limitations
The recording shows a short UI walkthrough plus a partial code preview, not the original full repository. Only the visible `ui.ts` code fragment is transcribed as original source. The rest is a frontend reconstruction of the visible screens. Figures and records are sample/demo data; local changes are held in browser memory only. No live inventory database, ERP, fulfilment, supplier integration, authentication, or persistent backend is connected.

## 👨‍💻 Author

**mrchandrayee** · [GitHub](https://github.com/mrchandrayee)

## 📄 License

[MIT License](./LICENSE)
