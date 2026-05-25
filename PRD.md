# Remipay — Product Requirements Document (PRD)

> **Version:** 1.0 MVP  
> **Last Updated:** May 2026  
> **Status:** Active Development

---

## Product Name

**Remipay**

---

## Overview

Remipay is a modern invoice and receipt generation platform designed for freelancers, creators, startups, and small businesses who need a fast, elegant, and reliable way to manage financial documents.

The platform simplifies invoice creation, payment tracking, and receipt generation through a clean and intuitive interface that prioritizes speed, usability, and professional presentation.

Unlike traditional accounting software that often feels overwhelming and enterprise-heavy, Remipay focuses on delivering a lightweight financial workspace with a premium user experience — inspired by the design sensibilities of Stripe, Linear, and Notion.

---

## Problem Statement

Many existing invoicing platforms are either:

- Overly complex and bloated with accounting features
- Visually outdated and unappealing
- Difficult for non-technical users to navigate
- Cluttered with unnecessary enterprise-level workflows

Freelancers and small business owners consistently need a simpler solution that allows them to:

- Generate invoices quickly (under 60 seconds)
- Maintain professional branding and presentation
- Track payments without friction
- Convert invoices into receipts in one click
- Manage client information effortlessly

Current solutions prioritize accounting systems over user experience, leaving a significant gap for a modern, design-first invoicing platform.

---

## Product Vision

> *To create the simplest and most elegant financial workspace for modern freelancers and small businesses.*

Remipay makes professional invoicing feel effortless, visually polished, and accessible to users without financial or technical expertise.

---

## Target Audience

### Primary Users

**Freelancers**
- UI/UX designers
- Developers
- Photographers
- Writers and copywriters
- Consultants
- Video editors and motion designers

**Small Businesses**
- Creative agencies
- Local vendors and service providers
- Early-stage startups
- Independent contractors

**Creators**
- Content creators and influencers
- Online educators and coaches
- Digital product sellers

---

## Goals

### Business Goals

- Deliver a polished, shippable MVP
- Demonstrate strong product and design thinking
- Showcase a scalable SaaS architecture
- Create a visually memorable and differentiated product

### User Goals

- Create professional invoices in under 60 seconds
- Maintain consistent, branded client communication
- Track invoice payment statuses at a glance
- Export beautiful, print-ready invoices and receipts as PDFs
- Organize and search financial records without complexity

---

## Success Metrics

The MVP will be considered successful when users can:

- Create an account and complete onboarding without confusion
- Generate their first invoice without needing documentation
- Export invoices and receipts as PDFs
- Convert a paid invoice into a receipt in one action
- Manage clients and invoice records across sessions
- Navigate the platform intuitively on both desktop and mobile

**Additional quality indicators:**
- Fast initial load time (< 2s)
- Responsive and consistent experience across devices
- Clear information hierarchy throughout all screens
- Minimal onboarding friction — zero required tutorials

---

## Core Features

---

### 1. Authentication

Users must be able to:

- Create a new account (email + password)
- Log in securely with persistent sessions
- Reset forgotten passwords
- Maintain private, persistent financial records tied to their account

**Authentication Provider:** Supabase Auth

---

### 2. Dashboard

The dashboard provides users with an at-a-glance overview of their financial activity and quick access to core actions.

**Dashboard Components:**

| Component | Description |
|---|---|
| Total Revenue | Sum of all paid invoices |
| Pending Invoices | Count and value of sent, unpaid invoices |
| Paid Invoices | Count and value of fully settled invoices |
| Overdue Invoices | Invoices past due date and unpaid |
| Recent Invoices | List of the 5–10 most recent invoices |
| Quick Actions | Create invoice, add client, view reports |

The dashboard should include data visualization cards that make financial health easy to interpret at a glance.

---

### 3. Invoice Generation

Users should be able to create professional invoices quickly through a split-screen builder with a live preview panel.

**User Inputs:**

- Business name and logo
- Business address and contact details
- Client name, email, and address
- Invoice items/services (name, quantity, unit price)
- Subtotal, tax/VAT rate, and total
- Invoice number (auto-generated, editable)
- Issue date and due date
- Accepted payment methods
- Notes and payment terms

**Invoice States:**
- `Draft` — saved but not yet sent
- `Sent` — shared with client
- `Paid` — payment confirmed
- `Overdue` — past due date, unpaid

Each status should be visually distinguishable using color-coded badges.

---

### 4. Real-Time Invoice Preview

The invoice builder uses a split-screen layout:

- **Left panel:** Form inputs and configuration
- **Right panel:** Live rendered invoice preview, updating in real time

**Objectives:**
- Improve user confidence during invoice creation
- Reduce editing errors before export
- Deliver a premium, professional-grade builder experience

---

### 5. Invoice Status Tracking

Each invoice supports the following status lifecycle:

```
Draft → Sent → Paid
              ↓
           Overdue (if due date passes without payment)
```

Users can manually update invoice statuses. Status changes should be reflected immediately in the dashboard analytics.

---

### 6. Receipt Generation

Users can convert any paid invoice into a downloadable receipt in a single action.

**Receipt Features:**
- Auto-generated, sequential receipt number
- Reference to the originating invoice number
- Downloadable as a formatted PDF
- Consistent branded formatting matching the invoice style

---

### 7. Client Management

Users should be able to:

- Add and save client profiles
- Edit existing client details
- Reuse saved clients when creating new invoices
- Search and filter the client list

**Client Data:**
- Full name or company name
- Email address
- Phone number
- Billing address

---

### 8. PDF Export

Invoices and receipts should be exportable as high-quality PDFs.

**Export Requirements:**
- Consistent layout and branding across exports
- Support for business logo and color theme
- Print-optimized formatting
- Works reliably across browsers and devices

**PDF Library:** `jsPDF` or `react-pdf`

---

### 9. Search and Filtering

Users should be able to:

- Search invoices by client name, invoice number, or keyword
- Filter invoices by status (Draft, Sent, Paid, Overdue)
- Sort by date created, due date, or total amount
- Quickly locate specific client records

---

### 10. Dark / Light Mode

The platform should support both light and dark themes, respecting the user's system preference by default with a manual toggle available in the UI.

---

### 11. Mobile Responsiveness

The full platform must function seamlessly across:

- Desktop (1280px+)
- Tablet (768px – 1279px)
- Mobile (320px – 767px)

The invoice builder layout adapts gracefully on smaller screens — the live preview collapses into a toggle or tab on mobile.

---

## Optional Stretch Features

### AI Invoice Suggestions *(Phase 2)*

AI-assisted generation of:
- Item and service descriptions
- Suggested pricing based on industry/type
- Professional invoice notes and terms

### Recurring Invoices *(Phase 2)*

Users can configure automatic repeat invoices for recurring clients on a custom schedule.

### Email Sharing *(Phase 2)*

Users can send invoices and receipts directly to clients via email from within the platform.

### Multi-Currency Support *(Phase 2)*

Supported currencies:
- NGN (Nigerian Naira) — default
- USD (US Dollar)
- GBP (British Pound)
- EUR (Euro)

---

## User Flows

### Authentication Flow

```
Landing Page → Sign Up / Log In → Dashboard
```

### Invoice Creation Flow

```
Dashboard → New Invoice → Add Client → Add Line Items → Preview → Export PDF / Mark Sent
```

### Receipt Conversion Flow

```
Invoice (Paid) → Convert to Receipt → Preview Receipt → Download PDF
```

### Client Management Flow

```
Clients Page → Add Client → Fill Details → Save → Reuse in Invoice Builder
```

---

## Technical Stack

| Layer | Technology |
|---|---|
| Frontend | Next.js 14 (App Router) |
| Styling | TailwindCSS |
| UI Components | shadcn/ui |
| Backend & Auth | Supabase (Auth + PostgreSQL) |
| PDF Generation | jsPDF / react-pdf |
| Deployment | Vercel |
| Font | Geist (via next/font) |

---

## Database Schema

### `users`
| Field | Type | Notes |
|---|---|---|
| id | uuid | Primary key |
| name | text | Full name |
| email | text | Unique |
| business_name | text | |
| business_address | text | |
| business_logo_url | text | |
| created_at | timestamp | |

---

### `clients`
| Field | Type | Notes |
|---|---|---|
| id | uuid | Primary key |
| user_id | uuid | Foreign key → users |
| client_name | text | |
| email | text | |
| phone | text | |
| address | text | |
| created_at | timestamp | |

---

### `invoices`
| Field | Type | Notes |
|---|---|---|
| id | uuid | Primary key |
| user_id | uuid | Foreign key → users |
| client_id | uuid | Foreign key → clients |
| invoice_number | text | Auto-generated |
| status | enum | draft, sent, paid, overdue |
| subtotal | numeric | |
| tax_rate | numeric | Percentage |
| tax_amount | numeric | Calculated |
| total | numeric | |
| due_date | date | |
| payment_method | text | |
| notes | text | |
| created_at | timestamp | |

---

### `invoice_items`
| Field | Type | Notes |
|---|---|---|
| id | uuid | Primary key |
| invoice_id | uuid | Foreign key → invoices |
| item_name | text | |
| description | text | |
| quantity | numeric | |
| unit_price | numeric | |
| total | numeric | Calculated |

---

### `receipts`
| Field | Type | Notes |
|---|---|---|
| id | uuid | Primary key |
| invoice_id | uuid | Foreign key → invoices |
| receipt_number | text | Auto-generated |
| created_at | timestamp | |

---

## Design Principles

Remipay should feel:

- **Premium** — Elevated, refined, never cheap-looking
- **Minimal** — Every element earns its space
- **Fast** — Snappy interactions, zero lag perception
- **Modern** — Contemporary SaaS aesthetic, not legacy accounting
- **Trustworthy** — Financial data handled with care and clarity

**Avoid:**
- Cluttered enterprise accounting software aesthetics
- Dense tables without breathing room
- Overwhelming multi-step workflows
- Gradient abuse or visual noise

---

## Accessibility Considerations

- Maintain WCAG AA contrast ratios across light and dark modes
- Support full keyboard navigation
- Use accessible, semantic form labels
- Provide clear inline error messaging
- Maintain responsive, scalable typography
- Ensure status badges are never color-only (include text or icons)

---

## Risks & Constraints

| Risk | Mitigation |
|---|---|
| PDF rendering inconsistencies across browsers | Test across Chrome, Safari, Firefox; use server-side PDF generation if needed |
| Mobile layout complexity for invoice builder | Collapse preview to tab/toggle on mobile |
| Invoice status accuracy | Use optimistic UI with server confirmation |
| Feature creep during MVP | Strict scope gate — defer all Phase 2 features |

---

## MVP Scope

### ✅ Included

- Authentication (sign up, log in, password reset)
- Dashboard with analytics cards
- Invoice generation with live preview
- Invoice status tracking (Draft, Sent, Paid, Overdue)
- Receipt conversion from paid invoices
- PDF export for invoices and receipts
- Client management (add, edit, reuse)
- Search and filter invoices
- Dark / light mode
- Mobile responsive design

### ❌ Excluded from MVP

- Advanced accounting or bookkeeping
- Payroll management
- Banking or payment gateway integrations
- Team collaboration or multi-user accounts
- AI-assisted suggestions
- Recurring invoice automation
- Email delivery of invoices

---

## Future Roadmap

### Phase 2
- Recurring invoices
- AI invoice assistance (item descriptions, pricing)
- Email delivery from platform
- Multi-currency support
- Enhanced dashboard analytics

### Phase 3
- Payment gateway integrations (Paystack, Stripe)
- Client self-service portals
- Financial reporting and exports
- Multi-user team collaboration
- White-label invoice branding

---

## AI-Assisted Workflow

AI tools leveraged during development:

| Tool | Use Case |
|---|---|
| Lovable | UI scaffolding and rapid component generation |
| Bolt.new | Workflow prototyping |
| Cursor | Code refinement and architecture decisions |
| ChatGPT / Claude | Copywriting, PRD drafting, logic planning |

All AI-generated output was manually reviewed, refined, and curated to ensure product quality, design consistency, and alignment with the Remipay design system.

---

## Competitive Advantage

Remipay differentiates itself through:

- **Premium UI/UX** — Feels like a design tool, not an accounting system
- **Simplified workflows** — Invoice creation in under 60 seconds
- **Creator-focused experience** — Built for freelancers, not enterprise finance teams
- **Real-time invoice preview** — Confidence-building split-screen builder
- **Elegant document design** — Beautiful, print-ready output by default
- **Mobile-first usability** — Works flawlessly on all devices

---

## Conclusion

Remipay is designed to give freelancers and small businesses a lightweight yet powerful invoicing experience that prioritizes speed, elegance, and usability above all else.

The MVP delivers the essential financial workflows — invoice creation, status tracking, receipt generation, client management, and PDF export — through a polished, modern interface that feels intuitive, trustworthy, and built to scale.

---

*Built with care for the modern independent professional.*
