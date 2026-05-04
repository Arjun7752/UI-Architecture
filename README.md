# UI-Architecture
feature_specific folder structure


├── public
│   ├── index.html          # Main HTML file for the application
│   └── manifest.json       # Metadata about the application
├── src
│   ├── modules            # Feature-wise folders
│   │   ├── auth           # Authentication feature
│   │   │   ├── components # Auth-specific components
│   │   │   ├── hooks      # Custom hooks for auth
│   │   │   ├── contexts   # Auth-specific contexts
│   │   │   ├── services   # API/service logic for auth
│   │   │   ├── store      # State management for auth
│   │   │   ├── AuthPage.tsx
│   │   │   └── Auth.test.tsx
│   │   ├── dashboard      # Dashboard feature
│   │   │   ├── components # Dashboard-specific components
│   │   │   ├── hooks      # Custom hooks for dashboard
│   │   │   ├── contexts   # Dashboard-specific contexts
│   │   │   ├── services   # API/service logic for dashboard
│   │   │   ├── store      # State management for dashboard
│   │   │   ├── DashboardPage.tsx
│   │   │   └── Dashboard.test.tsx
│   │   └── user           # User feature
│   │       ├── components # User-specific components
│   │       ├── hooks      # Custom hooks for user
│   │       ├── contexts   # User-specific contexts
│   │       ├── services   # API/service logic for user
│   │       ├── store      # State management for user
│   │       ├── UserPage.tsx
│   │       └── User.test.tsx
│   ├── api                # External API integrations/services
│   ├── routes             # Applications Routes
│   ├── shared             # Shared/reusable components, hooks, utils
│   │   ├── components     # Shared UI components
│   │   ├── hooks          # Shared hooks
│   │   ├── contexts       # Shared contexts
│   │   └── utils          # Utility functions
│   ├── app                # Global setup and entry points
│   │   ├── store.ts       # Global store
│   │   ├── App.tsx        # Main application component
│   │   └── index.tsx      # Entry point for the React application
│   ├── assets             # Images, global styles
│   │   ├── images
│   │   └── styles
│   └── react-app-env.d.ts # TypeScript definitions for the React app environment
├── package.json           # npm configuration file
├── tsconfig.json          # TypeScript configuration file
└── README.md              # Project documentation



# Example
dashboard/                           # Feature root – Dashboard (analytics, overview, insights)
│
├── components/                      # Presentation Layer – Feature-specific UI components (UI rendering, minimal state, presentation logic)
│   ├── analytics/                   # Presentation Layer – Analytics widgets/components
│   │   ├── charts/                  # Chart-level components
│   │   │   ├── RevenueChart.tsx     # Displays revenue trends
│   │   │   ├── UserGrowthChart.tsx  # Displays user growth over time
│   │   │   └── SalesChart.tsx       # Displays sales metrics
│   │   │
│   │   └── insights/                # Insight-level components
│   │       ├── KPIWidget.tsx        # Key performance indicator widget
│   │       ├── SummaryCard.tsx      # Summary card for quick stats
│   │       └── TrendIndicator.tsx   # Shows trends (up/down indicators)
│   │
│   └── activity/                   # Presentation Layer – Activity/feeds
│       ├── RecentActivities.tsx     # Displays recent user/system activities
│       └── Notifications.tsx        # Displays alerts/notifications
│
├── constants/                       # Configuration Layer – Dashboard constants
│   └── dashboard.constants.ts       # Labels, chart configs, enums
│
├── hooks/                           # Business Layer – Feature-specific hooks
│   └── useDashboard.ts              # Hook for dashboard data fetching and orchestration
│
├── utils/                           # Helper Layer – Helper functions
│   ├── formatChartData.ts           # Formats API data for charts
│   └── calculateMetrics.ts          # Utility to compute KPIs/aggregates
│
├── pages/                           # Container Layer – Route-level pages (data fetching, orchestration)
│   └── DashboardPage.tsx            # Main dashboard page (e.g., /dashboard)
│
├── services/                        # Business Layer – API calls and async logic
│   └── dashboard.service.ts         # Service to fetch dashboard analytics data
│
├── store/                           # State Management Layer – Redux/Zustand state
│   └── dashboardSlice.ts            # Stores dashboard data, loading, filters
│
├── types/                           # Type Layer – TypeScript types/interfaces
│   └── dashboard.types.ts           # Types for metrics, charts, widgets
│
└── data/                            # Data Layer – Mock / static feature data
    └── dashboard.mock.ts            # Mock dashboard data for development


    | Item Type        | Naming Style           | Example                | Purpose                                 |
| ---------------- | ---------------------- | ---------------------- | --------------------------------------- |
| Folder           | camelCase              | analytics, activity    | Domain-specific, feature-scoped folders |
| Component file   | PascalCase.tsx         | RevenueChart.tsx       | UI rendering, responsibility-specific   |
| Hook file        | useCamelCase.ts        | useDashboard.ts        | Encapsulates feature logic              |
| Service file     | camelCase.service.ts   | dashboard.service.ts   | API calls / async logic                 |
| Constants file   | camelCase.constants.ts | dashboard.constants.ts | Static values, labels, enums            |
| Types file       | camelCase.types.ts     | dashboard.types.ts     | TypeScript interfaces and types         |
| Page file        | PascalCase.tsx         | DashboardPage.tsx      | Route-level orchestration               |
| Utils file       | camelCase.ts           | formatChartData.ts     | Reusable helper functions               |
| Redux Slice      | camelCaseSlice.ts      | dashboardSlice.ts      | Feature-specific state management       |
| Data / Mock file | camelCase.mock.ts      | dashboard.mock.ts      | Feature-scoped mock/static data         |


SASS: 7-1 architecture
styles/
│
├── abstracts/        # No CSS output (only helpers)
│   ├── _variables.scss
│   ├── _mixins.scss
│   ├── _functions.scss
│
├── base/             # Reset + base styles
│   ├── _reset.scss
│   ├── _typography.scss
│   └── _base.scss
│
├── components/       # Small reusable UI components
│   ├── _button.scss
│   ├── _card.scss
│
├── layout/           # Layout-related styles
│   ├── _header.scss
│   ├── _footer.scss
│   ├── _grid.scss
│
├── pages/            # Page-specific styles
│   ├── _home.scss
│   ├── _dashboard.scss
│
├── themes/           # Theme variations
│   ├── _light.scss
│   └── _dark.scss
│
├── vendors/          # Third-party CSS
│   └── _bootstrap.scss
│
└── main.scss         # 👈 Imports everything



# 🎨 Frontend CSS Architecture Guidelines

## 1. 📌 Objective

This document defines the CSS architecture, conventions, and best practices for the project to ensure:

* Scalability across teams
* Maintainability over time
* Consistent design implementation
* Minimal styling conflicts

---

## 2. 🧱 Architecture Overview

We follow a **feature-based, component-scoped CSS architecture** using:

* **CSS Modules** → Scoped styling
* **Design Tokens (CSS Variables)** → Consistency & theming
* **Minimal Global Styles** → Base + reset only

---

## 3. 📂 Folder Structure

```bash
src/
│
├── styles/                    # Global styles (minimal)
│   ├── base/                 # Reset, typography
│   ├── tokens/               # Design tokens (colors, spacing, etc.)
│   ├── themes/               # Light/Dark themes
│   └── globals.css           # Entry point
│
├── shared/
│   └── components/
│       └── Button/
│           ├── Button.tsx
│           └── Button.module.css
│
├── features/
│   └── dashboard/
│       └── components/
│           └── KPIWidget/
│               ├── KPIWidget.tsx
│               └── KPIWidget.module.css
```

---

## 4. 🎯 Styling Strategy

### 4.1 Component-Level Styling (Primary)

* All components MUST use **CSS Modules**
* Styles must be colocated with components

```tsx
import styles from "./Component.module.css";
```

✅ Benefits:

* No global conflicts
* Easier refactoring
* Predictable styling

---

### 4.2 Design Tokens (Mandatory)

All reusable values must use CSS variables:

```css
:root {
  --color-primary: #4f46e5;
  --spacing-md: 16px;
}
```

🚫 Avoid:

```css
margin: 17px;
color: #123456;
```

---

### 4.3 Global Styles (Restricted)

Allowed:

* CSS Reset
* Typography
* Theme variables

Not allowed:

* Feature-specific styles
* Component styles

---

## 5. 🧩 Naming Conventions

### 5.1 Files

| Type       | Naming Format         | Example             |
| ---------- | --------------------- | ------------------- |
| Component  | PascalCase.tsx        | UserCard.tsx        |
| CSS Module | PascalCase.module.css | UserCard.module.css |
| Hook       | useCamelCase.ts       | useAuth.ts          |

---

### 5.2 CSS Classes

Use **clear, readable names (BEM-inspired but simplified)**:

```css
.container {}
.header {}
.title {}
.active {}
```

🚫 Avoid:

```css
.box {}
.redText {}
.style1 {}
```

---

## 6. 🧠 Best Practices

### ✅ Do

* Keep styles **small and component-focused**
* Use **design tokens** for consistency
* Prefer **composition over overrides**
* Keep CSS **flat (avoid deep nesting)**

---

### ❌ Don’t

* Don’t write global component styles
* Don’t use `!important`
* Don’t deeply nest selectors
* Don’t hardcode values

---

## 7. 🎨 Theming

Themes must be implemented using CSS variables:

```css
[data-theme="dark"] {
  --color-primary: #818cf8;
}
```

Switch themes via root attribute.

---

## 8. ⚙️ Utilities (Limited Usage)

Utility classes are allowed only in `styles/utilities/`:

```css
.mt-sm { margin-top: var(--spacing-sm); }
.flex { display: flex; }
```

⚠️ Avoid overusing utilities (no Tailwind-style clutter unless explicitly adopted)

---

## 9. 🧪 Maintainability Rules

* Each component should have **its own CSS module**
* No cross-feature style imports
* Shared styles must go into `shared/` or `styles/`

---

## 10. 🚀 Performance Considerations

* Avoid unused CSS
* Prefer scoped styles over global
* Minimize runtime styling (avoid heavy CSS-in-JS unless needed)

---

## 11. 📏 Code Review Checklist

Before merging:

* [ ] Is styling scoped (CSS Module)?
* [ ] Are design tokens used?
* [ ] Any hardcoded values?
* [ ] Any unnecessary nesting?
* [ ] Any global leakage?

---

## 12. 🏁 Summary

We prioritize:

* **Scalability** → Feature-based structure
* **Isolation** → CSS Modules
* **Consistency** → Design Tokens
* **Simplicity** → Minimal global CSS

This ensures a clean, maintainable, and enterprise-ready styling system.
#clean SMACSS-based folder structure adapted for a real project
src/
│
├── styles/                         # 🌍 All global styles (SMACSS-driven)
│
│   ├── base/                       # Base Layer – Default element styles
│   │   ├── _reset.css              # Reset / normalize
│   │   ├── _typography.css         # Headings, paragraphs, fonts
│   │   └── _base.css               # Body defaults, global HTML rules
│   │
│   ├── layout/                     # Layout Layer – Page structure
│   │   ├── _header.css             # Header layout
│   │   ├── _footer.css             # Footer layout
│   │   ├── _grid.css               # Grid system
│   │   └── _sidebar.css            # Sidebar layout
│   │
│   ├── modules/                    # Module Layer – Reusable components
│   │   ├── _button.css             # Button styles
│   │   ├── _card.css               # Card component
│   │   ├── _modal.css              # Modal component
│   │   └── _table.css              # Table component
│   │
│   ├── state/                      # State Layer – UI states
│   │   ├── _isActive.css           # .is-active
│   │   ├── _isHidden.css           # .is-hidden
│   │   └── _hasError.css           # .has-error
│   │
│   ├── theme/                      # Theme Layer – Visual themes
│   │   ├── _light.css              # Light theme
│   │   └── _dark.css               # Dark theme
│   │
│   └── main.css                    # 👈 Entry point (imports everything)
│
├── index.tsx                       # App entry point
