# Technology Stack Evaluation & Architectural Decision Record

## 1. Executive Summary & Recommendation

| Evaluated Dimension | React Native + Expo (SDK 52+ / New Architecture) | Flutter (Dart) | Recommendation Impact |
| :--- | :--- | :--- | :--- |
| **Development Speed & Prototyping** | **High** (Fast refresh, extensive JSX component libraries, rapid OTA updates via EAS) | **Medium-High** (Fast compilation, but stricter widget nesting and boilerplate) | Expo wins for MVP speed. |
| **AI Coding Compatibility** | **Superior** (LLMs have massive training corpora on TypeScript, React, Tailwind, and React Native hooks) | **Moderate** (Dart syntax is well-understood, but custom widget layouts and animations frequently hallucinate obsolete APIs) | RN + Expo leads for Antigravity pairing. |
| **Map & GPS Integration** | **Mature** (`@rnmapbox/maps` with vector tiles, `react-native-maps` for Google/Apple Maps, `expo-location`) | **Mature** (`google_maps_flutter`, `flutter_map` with MapLibre) | Tied in capability; RN offers smoother React context integration. |
| **Native Device Capabilities** | **Excellent** (Expo Config Plugins give access to camera, location, notifications without manual Xcode/Gradle diving) | **Excellent** (Direct engine rendering, strong platform channel ecosystem) | Tied. |
| **Maintenance & Talent Pool in Vietnam** | **Dominant** (Massive JS/TS & React developer base in Hanoi and HCMC) | **Strong** (Active Flutter community, but smaller talent pool than JS/TS) | Easier recruitment & handover with TypeScript. |
| **Offline Resilience & Local Storage** | **Robust** (WatermelonDB / OP-SQLite / MMKV for instant local reads and syncing) | **Robust** (Isar, Hive, Drift) | Tied. |
| **Cost of Development** | **Lower** (Code sharing across Web Admin potential, standard tooling) | **Moderate** | Expo reduces mobile + admin duplication. |

### Final Recommendation: **React Native with Expo (TypeScript)**
- **Why**: Fastest path to market for an MVP, maximum synergy with Google Antigravity's code synthesis capabilities, abundant Vietnamese developer talent, and robust Mapbox/OpenStreetMap support for terrain and offline caching.
- **Backend Recommendation**: **Supabase (PostgreSQL + PostGIS)** or **Node.js/NestJS + PostgreSQL (PostGIS)**.
  - Supabase provides instant auth, Row-Level Security (RLS), real-time subscriptions, PostGIS spatial queries (finding campsites within $X$ km radius), and managed file storage for images.

---

## 2. Deep Comparative Breakdown

### 2.1 Map Integration for Northern Vietnam
Northern Vietnam camping requires topographical maps, elevation contour lines, and offline tile caching because cell service is frequently absent in valleys and mountain passes (e.g., Y Ty, Lung Cu, Ta Xua).
- **Mapbox Vector Tiles via `@rnmapbox/maps`**: Supports offline tile pack downloads, custom elevation shading, and fast clustering of thousands of campsite markers.
- **MapLibre React Native / OpenStreetMap**: Zero-cost license option for open-source community mapping.

### 2.2 AI Coding Synergy
Antigravity agents generate higher-precision code with TypeScript/React Native because:
1. Strict typing catches schema discrepancies at compile time.
2. Hook-based state (`tanstack-query`, `zustand`) reduces boilerplate compared to Flutter BLoC or Riverpod state machines.
3. Automated unit and component tests with Jest and React Native Testing Library are readily generated.

---

## 3. Technology Decisions Requiring Human Sign-Off

Before initializing the mobile client scaffolding, the human project owner must review and approve:
1. Selection of **React Native + Expo (TypeScript)** as the mobile app framework.
2. Selection of **Supabase (Managed PostgreSQL + PostGIS)** as the Phase 1 backend to accelerate MVP delivery, or an alternative custom NestJS/Go microservice.
3. Selection of **Mapbox SDK** vs. **OpenStreetMap / MapLibre** for map tile rendering.
