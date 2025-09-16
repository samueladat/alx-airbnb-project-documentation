# Airbnb Clone — Project Documentation (Features & Functionalities)

## Overview
The **Airbnb Clone** is a backend application designed to mimic the core functionality of Airbnb. It will expose a **RESTful API** (or **GraphQL**) that handles user accounts, property listings, booking reservations, and payment processing.  
This phase produces a **blueprint** for the system—capturing high-level features, diagrams, and low-level API specifications **before any code is written**.

---

## Learning Objectives
By completing this documentation project, you will learn how to:

- Translate project requirements into a structured list of **features and functionalities**.
- Model system interactions visually using **Use Case Diagrams** to identify actors and their goals.
- Articulate user needs by writing clear **User Stories** that guide development from a user-centric perspective.
- Map data movement through the system using **Data Flow Diagrams (DFDs)** to understand how information is processed.
- Detail specific processes with **Flowcharts** to define logical sequences and decision points.
- Write precise **technical specifications** that define API endpoints, data validation, and system behavior for developers.
- Utilize diagramming tools like **Draw.io (Diagrams.net)** to create professional and clear technical diagrams.

---

## Key Concepts
- **Backend Architecture:** Routers, controllers, services, models, repositories; environment & configuration; error handling; logging.
- **RESTful API Design:** Resource-oriented endpoints, proper HTTP methods (GET, POST, PUT/PATCH, DELETE), status codes, pagination, filtering, sorting.
- **Data Modeling:** SQL (e.g., PostgreSQL) or NoSQL (e.g., MongoDB) schemas for **Users**, **Listings**, **Bookings**, **Payments**, etc.
- **Authentication & Authorization:** JWT access/refresh tokens, session strategy, role-based access control (RBAC), CSRF (if relevant), rate limiting.
- **Payment Gateway Integration:** Provider-based tokenization and PCI compliance (e.g., **Stripe**), webhooks for asynchronous events.
- **Documentation:** Clear, maintainable, comprehensive specs and diagrams enabling implementation and review.

---

## Tools & Libraries (Suggested)
- **Draw.io / Diagrams.net:** Use Case, DFDs, Flowcharts, architecture diagrams.
- **Git & GitHub:** Version control and hosting the documentation repo.
- **Markdown:** README and supporting docs.
- **Runtime & Framework (Potential):** Node.js + Express.js / NestJS (or Django/FastAPI/Rails).
- **Database (Potential):** PostgreSQL (relational) or MongoDB (non-relational).
- **Auth (Potential):** `bcrypt` for hashing, `jsonwebtoken` for JWTs.
- **Payments (Potential):** Stripe SDK.

---

## Deliverable in This Folder
This `features-and-functionalities/` folder contains the **feature blueprint** and diagrams for Task 0.

- `README.md` (this file): Complete feature list, scope, and instructions.
- `airbnb-backend-features.drawio`: Diagram source (Draw.io).
- `airbnb-backend-features.png`: Exported PNG from the Draw.io file.

> If you update the diagram, re-export the PNG and commit both files.

---

## Core Features & Functionalities (Checklist)

### 1) User Accounts & Authentication
- [ ] Email/password registration & login, logout
- [ ] Password hashing (bcrypt/argon2), password reset flows
- [ ] Email/phone verification (codes/links)
- [ ] Token-based auth (JWT access/refresh), optional sessions
- [ ] RBAC (guest, host, admin)
- [ ] Account status: active, suspended, deleted

### 2) User Profiles
- [ ] Profile CRUD: name, bio, avatar, phone
- [ ] Identity & trust: verification badges, government ID (KYC-ready)
- [ ] Notification preferences, language, timezone

### 3) Listings (Property Management)
- [ ] Listing CRUD (host only)
- [ ] Metadata: title, description, property/room type, capacity, amenities, house rules
- [ ] Location: address, coordinates (geocoding hook)
- [ ] Photos/media upload & ordering
- [ ] Pricing: nightly/base, seasonal/weekly/monthly, extra fees (cleaning, service), taxes
- [ ] Availability calendar (blocks, blackout dates)
- [ ] Status: draft, active, paused, delisted
- [ ] Compliance: license/registration number (where required)

### 4) Search & Discovery
- [ ] Text search (title/description/location)
- [ ] Filters: price range, dates, capacity, amenities, property type
- [ ] Sorting: price, rating, distance, relevance
- [ ] Map/bounds/radius search (optional)
- [ ] Pagination & caching strategy

### 5) Bookings
- [ ] Availability/quote check (conflict detection)
- [ ] Request-to-Book vs Instant Book flow
- [ ] Booking lifecycle: pending → accepted/declined → canceled → completed
- [ ] Policies: host cancellation, guest cancellation, refunds
- [ ] Overbooking prevention (locks/transactions)
- [ ] iCal import/export (optional)

### 6) Payments & Payouts
- [ ] Provider integration (e.g., Stripe): charges, holds, refunds
- [ ] Split payments & payout scheduling to hosts (post check-in)
- [ ] Security deposits (auth/capture/refund)
- [ ] Multi-currency display & conversion (provider rates)
- [ ] Webhook handling (payment succeeded/failed, dispute/chargeback)
- [ ] Receipts & invoices

### 7) Reviews & Ratings
- [ ] Two-sided reviews (guest ↔ host) after completed stays
- [ ] Rating aggregation per listing and per user
- [ ] Moderation & reporting (spam/abuse flags)

### 8) Messaging & Notifications
- [ ] Guest–host messaging threads per inquiry/booking
- [ ] Email/SMS/push notifications for key events (requests, approvals, reminders)
- [ ] Attachments (images only, optional)
- [ ] Read receipts (optional)

### 9) Wishlists
- [ ] Save/unsave listings to collections
- [ ] Shareable lists (optional)

### 10) Admin Console
- [ ] Users: moderation, suspensions
- [ ] Listings: review/flag/delist
- [ ] Bookings & disputes: refunds/exceptions
- [ ] Finance reports: revenue, payouts, fees, taxes
- [ ] Policy/content management

### 11) Non-Functional Requirements
- [ ] Security: validation/sanitization, rate limiting, secrets management
- [ ] Privacy: GDPR/CCPA-friendly export/delete
- [ ] Observability: logs, metrics, tracing, health checks
- [ ] Reliability: backups, disaster recovery, idempotency for webhooks
- [ ] Performance: pagination, caching, N+1 avoidance
- [ ] Testing: unit, integration, e2e; CI pipeline

---

## High-Level Data Model (Indicative)
- **Users** (roles, verification, profile)
- **Listings** (amenities, photos, pricing, availability)
- **Bookings** (guest, host/listing, dates, state, policy)
- **Payments / Transactions** (charges, refunds, deposits)
- **Payouts** (to hosts)
- **Reviews** (target: listing/user)
- **Messages** (threads, participants, attachments)
- **Wishlists** (collections, items)
- **Notifications**
- **AuditLogs**

---

## API Surface (Illustrative REST Endpoints)
- `/auth/*` — register, login, refresh, logout, password reset, verify
- `/users` — get/update profile, preference & verification endpoints
- `/listings` — CRUD, photos, pricing, availability
- `/search` — listings query with filters/sort/pagination
- `/bookings` — quote, create, update state, cancel
- `/payments` — charge/refund, webhook receiver
- `/payouts` — host payout info/history
- `/reviews` — create/read reviews
- `/messages` — threads & messages
- `/wishlists` — collections & items
- `/admin/*` — moderation, reports

> If you choose GraphQL, model equivalent queries/mutations and input/output types.

---

## Diagrams to Include (Draw.io)
1. **Use Case Diagram** — Actors: Guest, Host, Admin, Payment Provider.  
   Key use cases: search, view listing, request/instant book, pay, review, message, moderate.
2. **Level-1 DFD** — Context + main flows (Auth, Listings, Search, Booking, Payment, Reviews).
3. **Flowcharts** — e.g., *Request-to-Book* vs *Instant Book*; *Refund* decision tree; *Review* publishing & moderation.
4. **Component/Service Diagram** — API gateway/router, services, DB, cache, payment provider, email/SMS provider.

> Save the source as `airbnb-backend-features.drawio` and **export PNG** as `airbnb-backend-features.png`.

---

## Repository Structure (Required)
