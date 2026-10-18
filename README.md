# LIFETIME

**Your money has a price. Your time.**

LIFETIME is a proposed personal purchase decision-support web application for **COP 5818 — Full Stack Development for FinTech**. It helps users reconsider discretionary purchases by showing their cost in working hours and their estimated impact on available funds.

> **Project status:** Planning / P1 proposal. Application code has not yet been implemented.

## The Problem

Students and young professionals sometimes make purchases based on their bank balance without accounting for upcoming expenses or the time spent earning that money. LIFETIME provides a clearer perspective before a purchase, encouraging more intentional spending.

## Planned Essential Features

1. **Financial Profile:** Enter bank balance, monthly take-home salary, monthly working hours, and reserved expenses.
2. **Wishlist:** Add, view, edit, and delete items under consideration.
3. **Working-Hours Calculator:** Convert an item's price into hours of work using take-home salary and monthly hours.
4. **Affordability Analysis:** Show available funds after reserved expenses and estimated funds remaining after purchase.
5. **Think Twice Decision:** Save a decision to purchase, postpone, or decline an item.

**Optional, time permitting:** Purchase history and wishlist priorities.

**Out of scope:** Bank integrations, real payments, automatic transaction tracking, financial advice, native mobile development, and user authentication. The demonstration will use manually entered fictional data.

## Example (Fictional Data)

| Input | Value |
| --- | ---: |
| Bank balance | $3,000 |
| Monthly take-home salary | $4,000 |
| Monthly working hours | 160 |
| Reserved expenses | $2,000 |
| Wishlist item | Headphones — $300 |

Expected results:
- Effective hourly earnings: $4,000 / 160 = **$25/hour**
- Work represented by purchase: $300 / $25 = **12 hours**
- Share of monthly income: **7.5%**
- Available funds before purchase: $3,000 − $2,000 = **$1,000**
- Estimated available funds afterward: $1,000 − $300 = **$700**

LIFETIME asks: **“Is it worth 12 hours of your life?”** These estimates are based on user-entered information, not verified bank balances.

## Planned Tech Stack

- **Frontend:** HTML, CSS, vanilla JavaScript (single-page application; Fetch API)
- **Backend:** Node.js with Express (REST API and server-side calculations)
- **Database:** File-backed SQLite (persistent records, monetary values stored in integer cents)

### Planned SPA Sections

- Financial Profile
- Wishlist
- Purchase Analysis

### Planned API

| Method | Route | Purpose |
| --- | --- | --- |
| GET | `/api/profile` | Read financial profile |
| PUT | `/api/profile` | Create/update financial profile |
| GET | `/api/items` | List wishlist items |
| POST | `/api/items` | Add wishlist item |
| PUT | `/api/items/:id` | Edit item or decision |
| DELETE | `/api/items/:id` | Delete item |
| GET | `/api/items/:id/analysis` | Calculate financial impact |

### Planned Database Tables

- `financial_profile`: `id` (PK), `balance_cents`, `monthly_salary_cents`, `monthly_work_hours`, `reserved_expenses_cents`
- `wishlist_items`: `id` (PK), `profile_id` (FK), `title`, `price_cents`, `status`, `created_at`

One financial profile can have many wishlist items. The backend will validate inputs and handle missing records and errors. SQLite will preserve saved data after server restarts.

## Development Plan

This is an **individual project**. Target work includes requirements and database design (Week 1), SQLite/Express API (Week 2), SPA integration (Week 3), calculations and wishlist (Week 4), testing and fixes (Week 5), and documentation/demo preparation (Week 6). Timing is relative to the proposal submission and will be adjusted to the course deadline.

## Responsibilities & GitHub Workflow

**Developer:** Mauricio Figueiredo Mattos Costa — Team 17

As the sole developer, I am responsible for planning, design, implementation, integration, testing, and documentation. I will track tasks with GitHub Issues, create feature branches, make descriptive commits, and self-review pull requests before merging into `main`.

## Testing Plan

Planned manual tests will use fictional data to verify:
- Working-hours and income-percentage calculations
- Available funds after a purchase
- Rejection of invalid prices or working hours
- A full browser → Express API → SQLite workflow
- Data persistence after restarting the server

Issues will be documented, fixed, and retested.

## Learning Resource

I plan to study dynamic SPA updates and API requests using [MDN's Fetch API guide](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch).

## Running the Application

Setup and run instructions will be added once implementation begins. **No runnable application is included at the P1 proposal stage.**
