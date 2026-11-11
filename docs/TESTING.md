# Quality Assurance & Testing Strategy

## 1. Test Pyramid & Automation Standards

```
       /\
      /E2E\     --> Detox / Maestro (Critical user journeys: Map -> Details -> Booking)
     /------\
    / Integr \  --> Jest + Supabase Local Emulator (PostGIS spatial queries, Auth)
   /----------\
  /    Unit    \ --> Jest + React Native Testing Library (Components, Utils, Formatters)
 /--------------\
```

### Coverage Minimums
- **Unit & Utility Logic**: 85% coverage (budget calculation, i18n string resolution, coordinate math).
- **Core State Stores**: 90% coverage (caching layer, favorites, filter state).
- **Critical Paths**: 100% automated test coverage on authentication and partner booking link redirection.

---

## 2. Device Compatibility Matrix (Vietnam Market Focus)
Because Vietnam has a high density of mid-range and budget Android devices:
- **Primary Android Baseline**: Android 10+ (API Level 29+), 3GB RAM (e.g., Samsung Galaxy A-series, Xiaomi Redmi Note).
- **Primary iOS Baseline**: iOS 15+ (iPhone 8 / SE2 and later).
- **Offline Network Testing**: All major views must be tested under simulated 2G/3G throttled networks and zero-connectivity airplane mode.
