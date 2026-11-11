# API Specification (REST / GraphQL Endpoint Contracts)

All endpoints conform to JSON:API / standard REST formatting with UTF-8 encoding.

## Base URL
- Staging: `https://api-staging.campvn.app/v1`
- Production: `https://api.campvn.app/v1`

---

## 1. Campsite Discovery & Geospatial APIs

### `GET /campsites`
Returns campsites within viewport or proximity radius.
- **Query Parameters**:
  - `lat` (float, optional): User latitude.
  - `lng` (float, optional): User longitude.
  - `radius_km` (int, default: `50`): Search radius.
  - `province` (string, optional): e.g. `Hanoi`, `Hoa Binh`, `Lao Cai`.
  - `category` (string, optional): `glamping`, `managed_campsite`, `wild_camping`.
  - `has_toilet` (boolean, optional).
  - `min_verification` (int, default: `2`).
- **Response `200 OK`**:
  ```json
  {
    "data": [
      {
        "id": "c1f7a0b2-84b3-4f9e-9d2e-68f44d82b012",
        "slug": "dong-do-lake-soc-son",
        "name": {
          "vi": "Hồ Đồng Đò - Sóc Sơn",
          "en": "Dong Do Lake - Soc Son"
        },
        "category": "managed_campsite",
        "coordinates": {
          "latitude": 21.3256,
          "longitude": 105.8124
        },
        "province": "Hanoi",
        "district": "Soc Son",
        "distance_km": 38.5,
        "difficulty_level": 1,
        "verification_level": 3,
        "estimated_cost_min": 50000,
        "estimated_cost_max": 250000,
        "cover_image_url": "https://cdn.campvn.app/media/dong-do-cover.jpg",
        "rating_average": 4.6,
        "review_count": 84
      }
    ],
    "meta": {
      "total_count": 1,
      "page": 1,
      "limit": 20
    }
  }
  ```

---

## 2. Commercial Partner Redirection & Affiliate Tracking

### `POST /partners/click-through`
Tracks user booking intents and redirects to partner contact channels (Zalo / Direct Booking Page).
- **Request Body**:
  ```json
  {
    "campsite_id": "c1f7a0b2-84b3-4f9e-9d2e-68f44d82b012",
    "partner_id": "p8e4b1-partner-dongdo",
    "intent_type": "campground_booking" // or "gear_rental", "guide_hiring"
  }
  ```
- **Response `200 OK`**:
  ```json
  {
    "status": "success",
    "redirect_url": "https://zalo.me/0987654321",
    "tracking_token": "trk_98f7a6b5c4"
  }
  ```

---

## 3. Trip Planner & Checklist Generator

### `POST /trips/generate-checklist`
Generates equipment checklist and budget estimate based on destination attributes.
- **Request Body**:
  ```json
  {
    "campsite_id": "c1f7a0b2-84b3-4f9e-9d2e-68f44d82b012",
    "start_date": "2026-11-20",
    "duration_days": 2,
    "group_size": 4,
    "has_own_gear": false
  }
  ```
- **Response `200 OK`**:
  ```json
  {
    "checklist": [
      { "item": "Double-layer Tent (Waterproof 3000mm)", "category": "shelter", "required": true, "rental_available": true },
      { "item": "Warm Sleeping Bag (15°C rating)", "category": "sleep", "required": true, "rental_available": true },
      { "item": "Headlamp / Torch", "category": "lighting", "required": true, "rental_available": false }
    ],
    "estimated_budget": {
      "total_vnd": 1800000,
      "per_person_vnd": 450000,
      "breakdown": {
        "campsite_fee": 400000,
        "gear_rental": 600000,
        "food_supplies": 600000,
        "fuel_transport": 200000
      }
    }
  }
  ```
