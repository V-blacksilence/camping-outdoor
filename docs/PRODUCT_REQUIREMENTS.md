# Product Requirements Document (PRD) — Vietnam Camping & Outdoor (CampVN)

## 1. Vision & Core Pillars

CampVN connects Vietnamese outdoor enthusiasts, Gen Z weekend campers, and international travelers to verified camping experiences in Northern Vietnam, prioritizing safety, reliable geospatial information, and early commercial viability.

### Pillar A: Explore & Plan
1. **Interactive Geospatial Map**: Clustered campsite pins with real-time filter by terrain (lake, mountain, pine forest, glamping, wild).
2. **Detailed Location Profiles**: High-resolution galleries, amenities breakdown (toilets, clean water, cell signal, vehicle access), pricing, legal notes, and ranger/host contact.
3. **Trip Planning & Budget Estimator**: Automated estimate of fuel, campsite fees, equipment rental, and food costs.
4. **Smart Packing Checklist**: Dynamically suggested checklist based on terrain, altitude, season, and duration.
5. **Weather & Elevation Widget**: Hyper-local weather, temperature drop at night, and precipitation warning.

### Pillar B: Community & Connect
1. **Social Activity Feed**: Photo and story sharing with attached campsite tags and equipment tags.
2. **Community Verification & Reviews**: Structured reviews rating road accessibility, cleanliness, and safety.
3. **Find Travel Companions ("Tìm Bạn Đi Cắm Trại")**: Group matching for weekend carpooling or shared gear costs.
4. **Location Contribution Pipeline**: User-submitted campsites with moderation queue.

---

## 2. Target User Personas

| Persona | Demographics | Pain Points | Primary Features Used |
| :--- | :--- | :--- | :--- |
| **Gen Z Weekend Camper** | 18–26 years old, Hanoi resident, student or early career | Doesn't own gear; fears getting lost or arriving at a closed/illegal site; budget conscious. | Glamping discovery, rental gear bundles, Instagrammable location filters, budget calculator. |
| **Hardcore Outdoor Enthusiast** | 25–40 years old, experienced trekker/biker | Dislikes crowded glamping; needs topographical maps, offline GPS, water source info, and wild camping legality. | Topographical maps, offline mode, difficulty ratings, altitude & cell signal meters. |
| **International Traveler** | 20–45 years old, traveling through Northern Vietnam | Language barrier, unsure of local permits in border provinces (Ha Giang, Cao Bang). | English interface, verified guides/tours, booking assistance, emergency contacts. |

---

## 3. Localization & Internationalization (i18n)

- Languages: **Vietnamese (vi-VN)** as primary default; **English (en-US)** as secondary.
- Currency: **VND (₫)** with clean formatting (e.g., `150.000 ₫`); USD alternative for English locale.
- Distance & Elevation: Metric system (km, meters above sea level).
- Formats: Local date formats (`DD/MM/YYYY`) and 24-hour time notation.
