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

