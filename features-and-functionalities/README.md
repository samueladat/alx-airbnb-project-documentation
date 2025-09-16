# Airbnb Clone — Use Case Diagram

This folder contains the **Use Case Diagram** that visualizes how the main actors interact with the Airbnb Clone backend. It is derived from the features listed in Task 0.

---

## Actors
- **Guest** — browses listings, books stays, pays, reviews, messages hosts.  
- **Host** — creates/edits listings, manages availability and bookings, communicates with guests, receives payouts.  
- **Admin** — moderates users/listings/reviews, resolves disputes, manages refunds/exceptions.  
- **Payment Provider** — external service that processes charges/refunds and triggers webhooks.  
- **Email/SMS Provider** *(optional)* — external service that sends verifications and notifications.  

---

## Key Use Cases
- **Register / Log in / Verify Account**  
- **Manage Profile**  
- **Search & View Listings**  
- **Create / Edit / Pause Listing** *(Host)*  
- **Set Availability & Pricing** *(Host)*  
- **Request-to-Book / Instant Book**  
- **Pay for Booking / Refund**  
- **Message Host / Guest**  
- **Leave Review**  
- **Moderate Content / Users** *(Admin)*  
- **Handle Webhooks** *(Payment Provider → System)*  

---

## Files
- `airbnb-use-case.drawio` — Draw.io source file (editable).  
- `airbnb-use-case.png` — PNG export for quick viewing.  
- `README.md` — this file.  

> 💡 Tip: Open the `.drawio` file at [diagrams.net](https://app.diagrams.net/) to make edits and re-export the PNG.
