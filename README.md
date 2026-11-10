# ✈️ DjangoAir — Airline Management ERP System

**DjangoAir** is a comprehensive Enterprise Resource Planning (ERP) platform designed for managing airline operations. It integrates passenger services, ticket booking, online check-in, and role-based management interfaces for airline staff into a unified architecture.

---

## 📌 Project Overview & Architecture Blueprint

### 1. System Decomposition
The ERP system split into two primary web interfaces built on top of a single core backend:
* **Customer Interface:** Simple, multi-step booking process, account management, and self-check-in.
* **Staff Interface:** Role-based dashboard for operational workflows at the airport (check-in, gate management, and supervisory oversight).

---

## 📱 User Interfaces & Features

### 👤 Customer Interface
Designed for simplicity and speed:
1. **Welcome Screen:** 
   * Destination selection
   * Date picker
   * Passenger count selector
2. **Options & Seat Selection:** 
   * Real-time seat availability and pricing display
   * Add-on selection (extra luggage, in-flight meals, seat upgrades)
3. **Booking Finalization & Confirmation:** 
   * Instant delivery of electronic tickets and invoices via email upon booking completion.
   * Automated credential generation for the Customer Personal Cabinet.
4. **Personal Cabinet:** 
   * View upcoming and historical flight history
   * Account balance management
   * Online check-in service

#### 🌟 Optional Customer Features
* **Payment Gateway Emulation:** Integrated third-party open-source library/service for simulating ticket payments during checkout.
* **Social Authentication:** OAuth2 single sign-on (Google / Facebook integration).

---

### 💼 Staff Interface (Role-Based Access Control)

Access control strictly adheres to the following organizational hierarchy (sorted ascending):

1. 🎟️ **Gate Manager**
   * Register and confirm passenger boarding at the gate using ticket scan/code verification.
2. 🧳 **Check-in Manager**
   * Perform manual passenger check-in.
   * Manage baggage fees and attach additional flight options.
3. 👑 **Supervisor**
   * Includes all capabilities of Gate and Check-in Managers.
   * User Management: Hire/fire or modify accounts for Gate and Check-in Managers.
   * Operations: Create, edit, or cancel flights; configure system options and pricing.

---

## 🗄️ Core Domain Entities

* **Flight:** Route details, departure/arrival schedules, status, and assigned aircraft.
* **Passenger:** Personal details, passport info, and travel history.
* **Airplane:** Fleet details, total capacity, layout, and maintenance status.
* **Seat Type:** Pricing tiers, class categories (Economy, Business, First).
* **Option:** Extra services (luggage weight limits, meals, priority boarding).
* **Ticket:** Booking reference, seat assignment, pricing breakdown, and payment status.
* **Discount:** Promotional codes, loyalty program reductions, and special tariffs.

---

## 🛠️ Tech Stack & Infrastructure

| Layer | Technology |
| :--- | :--- |
| **Backend Frameworks** | Django (Core ERP & Web App), Flask (Mock Services) |
| **Database** | PostgreSQL |
| **Containerization** | Docker / Docker Compose |
| **Task Queue & Broker** | Celery + Redis |
| **Frontend** | Vue.js, Webpack, Bootstrap |
| **Web Server / Reverse Proxy** | Nginx |

#### 🌐 Optional Extensions & Integrations
* **Mobile API & WebSockets:** Mock service built with Flask for real-time mobile app updates and WebSockets connection.
* **Third-Party Webhooks:** Flask mock server simulating external service notifications (e.g., flight status updates, external payment processors).

---

## 🗺️ System Development Plan
### 🎯 Priority Steps (Phase 1 — Core Infrastructure)
1. **Database Modeling & Core Entities:** Define ORM models for `Airplane`, `Seat Type`, `Flight`, `Passenger`, and `Ticket`.
2. **UML Class Diagram:** Document domain relationships, inheritance, and business logic methods.
3. **Authentication & RBAC:** Implement Django custom user models, permissions, and group-based roles for staff hierarchy.

### Phase 2 — Customer Booking Engine & Notifications
* Implement search, selection, options attachment, and checkout workflow.
* Integrate Celery tasks with Redis for background email generation (tickets & credentials delivery).
* Build Customer Personal Cabinet.

### Phase 3 — Staff Portal & Workflows
* Build UI dashboards for Check-in Managers and Gate Managers.
* Implement Supervisor management panels (Flight management & Staff access rights).

### Phase 4 — Optional Enhancements & Services
* Implement Payment Gateway Emulation and Social Senders (Google OAuth).
* Deploy Flask mock services for WebSockets and Webhook handling.
* Containerize the full stack using Docker & Nginx setup.
