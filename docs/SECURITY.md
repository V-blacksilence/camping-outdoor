# Security & Safety Protocols

## 1. Safety Policies for Outdoor Campers in Vietnam

### 1.1 Border and Military Zone Regulations
- Provinces like Ha Giang, Cao Bang, and Lao Cai have strict border belt regulations (*khu vực biên giới*).
- Foreign nationals require a special border entry permit issued by the provincial immigration police.
- **System Rule**: Any campsite within 10 km of the national border must automatically display a bilingual legal advisory and the direct address of the local district police station for permit issuance.

### 1.2 Flash Flood, Hydrological & Weather Advisories
- Campsites situated in dry riverbeds or downstream of hydroelectric dams (Hoa Binh, Na Hang, Son La) face sudden water surges during rainy season (June – October).
- Locations flagged with hydrological risk must display automated seasonal warning banners.

---

## 2. Technical Security Baseline

1. **Authentication**: Supabase Auth with bcrypt hashing; JWT tokens with short expiration (1 hour) and secure refresh tokens stored in iOS Keychain / Android Keystore via `expo-secure-store`.
2. **Row-Level Security (RLS)**: Enforced on all PostgreSQL tables. Direct client queries cannot bypass RLS.
3. **Data Protection**: Personal contact information (phone number, Zalo ID) is never exposed to unauthenticated users or public scrapers.
4. **Zero Hardcoded Secrets**: All API keys (Mapbox token, Supabase Anon key, SENTRY DSN) must be loaded from environment variables (`.env`) and validated with Zod at runtime.
