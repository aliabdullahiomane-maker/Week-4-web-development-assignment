# SpendWise – Budget Dashboard Shell (Week 4)

This project is the **SpendWise Dashboard Shell**, the foundation for the capstone budget tracker.  
Week 4 focuses on **layout and theming** using modern CSS:

- CSS Grid for the overall page layout.
- Flexbox inside the header, sidebar, and cards.
- CSS custom properties (variables) for theming.
- Responsive design (single column below 768px).
- Subtle card micro‑interactions (hover & focus).

No new functionality is added; all content is static and realistic.

## Files in This Repository

- `index.html` – Dashboard structure with:
  - Sidebar
  - Header
  - Six category cards (Food, Transport, Rent, Entertainment, Savings, Utilities)
- `style.css` – All styles, including:
  - CSS variables in `:root`
  - Grid + Flexbox layout
  - Responsive media query
  - Dark theme (stretch goal)
- `README.md` – This file.

## How the Layout Is Built

### 1. CSS Grid for Overall Layout

The `.dashboard` container uses Grid:

```css
.dashboard {
  display: grid;
  grid-template-columns: var(--sidebar-width) 1fr;
  grid-template-rows: auto 1fr;
  min-height: 100vh;
}
```

- First column: sidebar.
- Second column: main content (header + dashboard).

### 2. Flexbox Inside Components

Flexbox is used for:

- `.sidebar` – vertical navigation.
- `.sidebar-header` – icon + brand name.
- `.sidebar-nav` – list of nav items.
- `.top-header` – title + user actions.
- `.category-card` – header + body content.
- `.card-header`, `.card-body` – internal layout of each card.

Example:

```css
.sidebar {
  display: flex;
  flex-direction: column;
}

.top-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.category-card {
  display: flex;
  flex-direction: column;
}
```

### 3. Theme Using CSS Custom Properties

All key colors are defined in `:root`:

```css
:root {
  --brand-color: #2563eb;
  --accent-color: #16a34a;
  --surface-color: #ffffff;
  --bg-color: #f3f4f6;
  --text-primary: #111827;
  --text-secondary: #6b7280;
  --border-color: #e5e7eb;
  --card-shadow: 0 6px 18px rgba(0, 0, 0, 0.08);
  --card-shadow-hover: 0 10px 24px rgba(0, 0, 0, 0.12);
  --sidebar-width: 260px;
  --header-height: 64px;
  --radius: 12px;
}
```

These variables are used consistently for:

- Backgrounds
- Text colors
- Borders
- Shadows
- Layout sizes

### 4. Responsive Design (Below 768px)

A media query collapses the layout into a single column on small screens:

```css
@media (max-width: 768px) {
  .dashboard {
    grid-template-columns: 1fr;
  }

  .cards-grid {
    grid-template-columns: 1fr;
  }

  /* Sidebar becomes a top bar */
  .sidebar {
    flex-direction: row;
    justify-content: space-between;
  }

  .sidebar-nav {
    flex-direction: row;
  }
}
```

This can be verified using DevTools Device Toolbar.

### 5. Card Micro‑interactions

Each `.category-card` has hover and focus animations:

```css
.category-card {
  transition: transform 200ms ease, box-shadow 200ms ease;
}

.category-card:hover,
.category-card:focus {
  transform: translateY(-3px);
  box-shadow: var(--card-shadow-hover);
}
```

- Duration: 200ms (≤250ms as required).
- Uses `transform` and `box-shadow`.
- Applies to both `:hover` and `:focus`.

### 6. Dark Theme (Stretch Goal)

A dark theme is implemented by overriding CSS variables:

```css
@media (prefers-color-scheme: dark) {
  :root {
    --surface-color: #0b0f19;
    --bg-color: #05080f;
    --text-primary: #e5e7eb;
    --text-secondary: #9ca3af;
    --border-color: #1f2937;
    --card-shadow: 0 6px 18px rgba(0, 0, 0, 0.5);
    --card-shadow-hover: 0 10px 24px rgba(0, 0, 0, 0.6);
  }
}
```

Only the variables change; the rest of the CSS remains the same.

## How to Run This Project Locally

1. Clone or download this repository.
2. Open the folder in Visual Studio Code.
3. Ensure these files are present:
   - `index.html`
   - `style.css`
   - `README.md`
   - `money.png` (icon used in sidebar and header)
4. Open `index.html` in your browser.
5. Use DevTools Device Toolbar to test responsiveness at different widths.

## What Each Part Does

- **Sidebar**  
  Contains the SpendWise brand and navigation links (Dashboard, Transactions, Budgets, Reports, Settings). Styled with Flexbox and uses CSS variables for colors.

- **Header**  
  Shows the page title and user actions (name + logout button). Uses Flexbox for alignment.

- **Category Cards**  
  Six cards showing realistic financial categories:
  - Food
  - Transport
  - Rent
  - Entertainment
  - Savings
  - Utilities  

  Each card uses Flexbox internally and has hover/focus micro‑interactions.

- **Responsive Behavior**  
  Below 768px:
  - Sidebar becomes a top navigation bar.
  - Cards stack in a single column.
  - Layout remains usable on mobile.

- **Dark Theme**  
  Automatically applied if the user’s system prefers dark mode, by overriding CSS variables.

## Assessment Alignment

This implementation meets the Week 4 requirements:

- **Dashboard layout** with sidebar, header, and six category cards.
- **CSS Grid** for overall layout; **Flexbox** inside components.
- **CSS custom properties** for a consistent theme.
- **Responsive design** with a single‑column layout below 768px.
- **Card micro‑interactions** using `transform` and `box-shadow` on hover/focus (≤250ms).
- **Dark theme** implemented as a stretch goal.

## Future Work

In later weeks, this shell will be extended with:

- Real transaction data.
- Dynamic charts and summaries.
- JavaScript interactivity (filtering, adding transactions, etc.).

For now, this week is purely about **layout, theming, and responsiveness with CSS**.
