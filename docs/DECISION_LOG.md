# Architectural Decision Log (ADR)

## ADR-001: Mobile Application Architecture Selection
- **Status**: Proposed (Awaiting Human Approval)
- **Date**: 2026-11-11
- **Context**: The startup requires a cross-platform mobile app targeting Android and iOS with native map integration, offline caching, and fast time-to-market.
- **Decision**: Propose **React Native with Expo SDK (TypeScript)** over Flutter.
- **Consequences**:
  - Accelerated development cycles and seamless pairing with Antigravity AI code synthesis.
  - Broad availability of React Native developers in the Vietnamese tech market.
  - Reliable map rendering via `@rnmapbox/maps` and `react-native-maps`.

---

## ADR-002: Backend and Database Technology
- **Status**: Proposed (Awaiting Human Approval)
- **Date**: 2026-11-11
- **Context**: Need a scalable backend supporting spatial radius queries, instant authentication, file storage, and offline synchronization for campsite reviews.
- **Decision**: Propose **Supabase (PostgreSQL with PostGIS extension)**.
- **Consequences**:
  - Native spatial queries with `ST_DWithin` and spatial GiST indexes.
  - Zero-maintenance authentication with built-in social and OTP providers.
  - Granular data isolation through PostgreSQL Row-Level Security (RLS).

---

## ADR-003: Northern Vietnam Geographic Priority
- **Status**: Approved (As per Master Prompt Mandate)
- **Date**: 2026-11-11
- **Context**: Focus market entry on high-density outdoor hubs to ensure verified data quality.
- **Decision**: Concentrate Phase 1 & 2 exclusively on 9 Northern provinces: Hanoi, Ninh Binh, Quang Ninh, Lao Cai, Ha Giang, Cao Bang, Tuyen Quang, Hoa Binh, and Son La.
