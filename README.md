# 📊 Slot Booking → Dashboard → Reporting (Interview Exercise)

This repository contains a small **Laravel + Next.js** exercise we will complete **together during the technical interview**.

The exercise simulates a simplified real-world booking system where we:

* Accept booking requests
* Apply business rules
* Store bookings
* Provide dashboard statistics
* Generate simple reports

You will have roughly **30–45 minutes** to implement the core behaviour.

---

# 🧠 Business Context

Imagine this is a small booking system for a shared workspace.

Slots represent time windows (Morning, Afternoon, Evening), and users can book seats.

However, there are business rules to ensure fair usage and realistic constraints.

---

## 1. Getting started

```bash
git clone <REPO_URL>
cd booking-dashboard-exercise
```

---

## Backend (Laravel)

```bash
cd backend
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate
php artisan serve
```

Server:

```
http://localhost:8000
```

Health check:

```bash
curl http://localhost:8000/api/health
```

---

## Frontend (Next.js)

```bash
cd frontend
npm install
npm run dev
```

```
http://localhost:3000
```

---

# 2. Data model (Booking)

```json
{
  "slot": "Morning",
  "user_name": "John",
  "seats": 2
}
```

---

# 🧩 3. Business Rules (Important)

Candidates should implement these rules.

### Rule 1 — Maximum seats per booking

A user cannot book more than **5 seats in a single booking**.

---

### Rule 2 — Total seats per slot

Each slot has a maximum capacity of **20 seats**.

Bookings must not exceed available seats.

---

### Rule 3 — Duplicate user booking

A user cannot book the **same slot more than once**.

---

### Rule 4 — Booking cutoff rule

Bookings are not allowed if system time is after **6 PM** (simulate cutoff).

---

### Rule 5 — Minimum booking size

Booking must be at least **1 seat**.

---

### Rule 6 — Slot name validation

Only allowed slots:

* Morning
* Afternoon
* Evening

---

# 4. Your tasks

| Task               | Endpoint | Status |
| ------------------ | -------- | ------ |
| POST /api/bookings | Required |        |
| GET /api/dashboard | Required |        |
| GET /api/report    | Optional |        |

---

# Task 1 — POST /api/bookings

Accept booking request and apply all business rules.

---

## Success response

```json
{
  "status": "ok",
  "bookingId": 1
}
```

---

## Example error

```json
{
  "error": "Slot capacity exceeded"
}
```

---

# Task 2 — GET /api/dashboard

Return aggregated stats.

```json
{
  "totalBookings": 12,
  "totalSeatsBooked": 30,
  "slots": [
    {
      "slot": "Morning",
      "bookingCount": 5,
      "seatsBooked": 12,
      "remainingSeats": 8
    }
  ]
}
```

---

# Task 3 — GET /api/report (optional)

Filter by slot.

```http
GET /api/report?slot=Morning
```

---

## Response

```json
{
  "slot": "Morning",
  "totalBookings": 5,
  "totalSeats": 12,
  "bookings": []
}
```

---

# 5. Frontend Task

Update dashboard page to:

✅ Show totals
✅ Show slot stats
✅ Show remaining seats

---

## Optional

Add booking form.

---


# 6. Notes

There is no single perfect solution – we are interested in:

- Logical thinking
- Ability to translate business rules into code
- Validation strategy
- Edge case handling
- Clean architecture
- Naming clarity
- Communication

---


**Feel free to:**

- Extract helper functions
- Create additional modules/files
- Add comments where you think they help

---

> 💡 **We will work through this while you share your screen.**
> It is completely fine if you don't finish everything — we care more about your approach and reasoning than total completeness.