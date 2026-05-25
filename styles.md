# Remipay — Design System & Style Guide

> **Version:** 1.0  
> **Last Updated:** May 2026  
> **Scope:** UI/UX Design Direction for Remipay MVP

---

## Design Philosophy

Remipay's visual language is inspired by the restraint of **Linear**, the trust-building clarity of **Stripe**, and the structured openness of **Notion**.

The guiding principle is **purposeful minimalism** — every design decision reduces cognitive load and increases confidence. Financial tools must communicate trust, speed, and professionalism without overwhelming the user.

> *"Design that doesn't get in the way of the work."*

---

## Aesthetic Direction

| Attribute | Direction |
|---|---|
| Mood | Premium, calm, professional |
| Density | Spacious — breathing room in every section |
| Personality | Confident, modern, quietly refined |
| Inspiration | Stripe, Linear, Notion, Lemon Squeezy |
| Anti-inspiration | Quickbooks, FreshBooks, legacy accounting UIs |

**What Remipay should feel like:** Opening a beautifully designed notebook that handles money with care — clean, organized, and quietly impressive.

**What Remipay must never feel like:** Enterprise software from 2012, dashboard overload, or an accounting textbook.

---

## Brand Identity

### Logo

- **Wordmark:** "Remipay" in Geist font, semibold weight
- **Brand mark:** Optional — a minimal `R` monogram or abstract mark in brand red
- The wordmark alone is sufficient for MVP
- Logo appears in sidebar header and PDF document headers

### Brand Voice

- **Confident, not arrogant**
- **Helpful, not patronizing**
- **Professional, not formal**

**Microcopy examples:**
- ✅ "Invoice sent." ❌ "Your invoice has been successfully dispatched to the recipient."
- ✅ "Add your first client" ❌ "No client records found in the system."
- ✅ "Mark as paid" ❌ "Update payment confirmation status"

---

## Color System

### Primary Brand Color

```
Brand Red:    #bf0808
```

Used for: primary CTAs, active nav states, status badges (overdue), key highlights, logo accent.

### Extended Palette

```css
/* Brand */
--color-brand:          #bf0808;
--color-brand-hover:    #a30707;
--color-brand-light:    #fef2f2;   /* very light red tint, for backgrounds */
--color-brand-subtle:   #fee2e2;   /* for badges, tags */

/* Neutrals — Light Mode */
--color-bg-primary:     #ffffff;
--color-bg-secondary:   #fafaf9;   /* warm off-white */
--color-bg-tertiary:    #f5f5f4;   /* subtle card background */
--color-bg-hover:       #f0efee;

--color-border:         #e7e5e4;
--color-border-strong:  #d6d3d1;

--color-text-primary:   #1c1917;   /* warm near-black */
--color-text-secondary: #57534e;   /* warm medium gray */
--color-text-muted:     #a8a29e;   /* soft muted */
--color-text-disabled:  #d6d3d1;

/* Neutrals — Dark Mode */
--color-bg-primary-dark:    #0f0f0e;
--color-bg-secondary-dark:  #1a1917;
--color-bg-tertiary-dark:   #242220;
--color-bg-hover-dark:      #2c2a28;

--color-border-dark:        #2e2c2a;
--color-border-strong-dark: #3d3b38;

--color-text-primary-dark:    #fafaf9;
--color-text-secondary-dark:  #a8a29e;
--color-text-muted-dark:      #78716c;

/* Status Colors */
--color-status-draft:    #78716c;   /* gray */
--color-status-sent:     #2563eb;   /* blue */
--color-status-paid:     #16a34a;   /* green */
--color-status-overdue:  #bf0808;   /* brand red */

/* Status Backgrounds (light tints) */
--color-status-draft-bg:   #f5f5f4;
--color-status-sent-bg:    #eff6ff;
--color-status-paid-bg:    #f0fdf4;
--color-status-overdue-bg: #fef2f2;

/* Pastel Accent Colors (for dashboard cards, data viz) */
--color-accent-amber:   #fef3c7;
--color-accent-sky:     #e0f2fe;
--color-accent-green:   #dcfce7;
--color-accent-rose:    #ffe4e6;
--color-accent-purple:  #f3e8ff;
--color-accent-peach:   #ffedd5;
```

### Color Usage Rules

- **Brand red (#bf0808)** — Primary buttons, active navigation, overdue badges, key accents only. Never use as a background fill for large areas.
- **Warm neutrals** — Backgrounds, cards, borders. Always use warm-tinted neutrals (stone scale), never cold grays.
- **No gradients** — Solid colors only. No linear-gradient or radial-gradient usage anywhere in the UI.
- **Status colors** — Always pair colored badges with text labels. Never rely on color alone to communicate state.
- **Pastel accents** — Dashboard analytics cards, chart fills, empty state illustrations. Keep usage light and purposeful.

---

## Typography

### Primary Font

**Geist** — Used exclusively across all UI surfaces.

Import via `next/font/google` or the Vercel Geist package:

```tsx
import { GeistSans } from 'geist/font/sans';
import { GeistMono } from 'geist/font/mono';
```

### Type Scale

```css
/* Display — Landing / Hero moments */
--text-display:    3rem / 48px      /* font-size / line-height */
--text-display-lg: 2.25rem / 36px

/* Headings */
--text-h1:   1.875rem / 2.25rem    /* 30px */
--text-h2:   1.5rem / 2rem         /* 24px */
--text-h3:   1.25rem / 1.75rem     /* 20px */
--text-h4:   1.125rem / 1.75rem    /* 18px */

/* Body */
--text-body-lg:  1rem / 1.75rem    /* 16px — default body */
--text-body:     0.9375rem / 1.625rem  /* 15px */
--text-body-sm:  0.875rem / 1.5rem  /* 14px */

/* UI / Labels */
--text-label:    0.8125rem / 1.25rem  /* 13px — form labels, table headers */
--text-caption:  0.75rem / 1.125rem   /* 12px — meta, timestamps */

/* Mono — Invoice numbers, amounts */
--text-mono:     GeistMono, monospace
```

### Font Weights

| Weight | Usage |
|---|---|
| 400 (Regular) | Body copy, descriptions, table cells |
| 500 (Medium) | Subheadings, navigation items, form labels |
| 600 (Semibold) | Section headings, card titles, amounts |
| 700 (Bold) | Dashboard stats, page titles, CTA labels |

### Typography Rules

- **Invoice amounts and numbers** — Always use GeistMono for numeric values in invoices, receipts, and dashboard stats
- **Large dashboard numbers** — Use bold weight at h2 or h1 scale with a currency prefix in text-secondary color
- **Empty states** — Use h3 for the main message, body-sm in text-muted for supporting text
- **Never center-align body text** — Left-align all paragraphs and descriptions
- **Letter spacing** — Use `tracking-tight` for headings, default for body, `tracking-wide` for uppercase labels only

---

## Spacing System

Remipay uses an 8px base spacing scale via Tailwind.

```
4px   — xs  (tight element spacing, icon gaps)
8px   — sm  (compact padding, small gaps)
12px  — md  (default inline spacing)
16px  — base (default padding unit)
20px  — lg
24px  — xl  (card padding, section gaps)
32px  — 2xl (between sections within a page)
40px  — 3xl
48px  — 4xl (between major page sections)
64px  — 5xl (page-level vertical rhythm)
```

### Layout Rules

- **Page content max-width:** `1280px` with `mx-auto`
- **Sidebar width:** `240px` (collapsed: `64px`)
- **Card padding:** `24px` (`p-6`) minimum
- **Section gaps:** `32px–48px` between major sections
- **Form field spacing:** `16px` between fields, `8px` between label and input

---

## Component Design Tokens

### Borders & Radius

```css
--radius-sm:   0.375rem   /* 6px — inputs, small badges */
--radius-md:   0.5rem     /* 8px — buttons, tags */
--radius-lg:   0.75rem    /* 12px — small cards */
--radius-xl:   1rem       /* 16px — standard cards */
--radius-2xl:  1.5rem     /* 24px — primary dashboard cards */
--radius-full: 9999px     /* pill badges, avatar, toggles */

--border-color: var(--color-border);
--border-width: 1px;
```

**Rule:** Use `rounded-2xl` for all primary dashboard cards and modal containers. Use `rounded-xl` for secondary cards. Use `rounded-lg` for inputs and smaller components.

### Shadows

Remipay uses **minimal or no shadows**. Shadow should suggest elevation, not decoration.

```css
/* Use sparingly — only for modals and dropdowns */
--shadow-sm:  0 1px 2px 0 rgb(0 0 0 / 0.04);
--shadow-md:  0 2px 8px 0 rgb(0 0 0 / 0.06);
--shadow-lg:  0 8px 24px 0 rgb(0 0 0 / 0.08);

/* Never use: large drop shadows, colored shadows, inset shadows for cards */
```

**Rule:** Cards sit flat against the background, differentiated by background color and border — not shadow. Modal dialogs and dropdown menus may use `shadow-lg`.

---

## UI Components

All components built on **shadcn/ui** with Remipay theme overrides.

### Buttons

**Primary Button**
```
Background: #bf0808
Text: white
Hover: #a30707
Radius: rounded-lg (8px)
Padding: px-4 py-2 (desktop) / px-3 py-1.5 (compact)
Font: text-sm font-medium
```

**Secondary Button**
```
Background: transparent
Border: 1px solid var(--color-border)
Text: text-primary
Hover: bg-tertiary
```

**Ghost Button**
```
Background: transparent
Text: text-secondary
Hover: bg-hover, text-primary
No border
```

**Destructive Button**
```
Background: #fee2e2
Text: #bf0808
Hover: #fecaca bg
Border: none
```

### Form Inputs

```
Height: 36px (compact) / 40px (standard)
Border: 1px solid var(--color-border)
Border-radius: rounded-lg
Background: var(--color-bg-primary)
Focus: ring-1 ring-brand (1px brand red ring)
Placeholder: text-muted
Font-size: text-sm
Padding: px-3 py-2
```

### Status Badges

All badges use `rounded-full` with font-size `text-xs font-medium`.

| Status | Background | Text Color |
|---|---|---|
| Draft | `#f5f5f4` | `#78716c` |
| Sent | `#eff6ff` | `#2563eb` |
| Paid | `#f0fdf4` | `#16a34a` |
| Overdue | `#fef2f2` | `#bf0808` |

### Cards

**Dashboard Stat Card**
```
Background: var(--color-bg-secondary)
Border: 1px solid var(--color-border)
Border-radius: rounded-2xl
Padding: p-6
Shadow: none
```

**Content Card**
```
Background: var(--color-bg-primary)
Border: 1px solid var(--color-border)
Border-radius: rounded-xl
Padding: p-6
Shadow: none
```

### Data Tables

```
Header row: bg-secondary, text-label, font-medium, text-muted
Body rows: bg-primary, text-body-sm, border-b border-border
Hover row: bg-hover
Row height: 52px
Cell padding: px-4 py-3
```

### Sidebar Navigation

```
Width: 240px
Background: var(--color-bg-secondary)
Border-right: 1px solid var(--color-border)
Nav item height: 36px
Nav item radius: rounded-lg
Active item: bg-brand-light, text-brand, font-medium
Inactive item: text-secondary, hover bg-hover
Icon size: 16px (w-4 h-4)
Gap between icon and label: 10px
Section labels: text-caption, text-muted, uppercase, tracking-wide
```

---

## Page Layouts

### Dashboard Layout

```
┌─────────────────────────────────────────────────┐
│  Sidebar (240px)  │  Main Content Area           │
│  ─────────────── │  ─────────────────────────── │
│  Logo             │  Page Header (title + CTA)   │
│  ─────────────── │                               │
│  Navigation       │  Stat Cards Row (4 cards)    │
│  - Dashboard      │                               │
│  - Invoices       │  Recent Invoices Table        │
│  - Clients        │                               │
│  - Receipts       │  Quick Actions                │
│  ─────────────── │                               │
│  Settings         │                               │
│  Profile          │                               │
└─────────────────────────────────────────────────┘
```

### Invoice Builder Layout (Desktop)

```
┌─────────────────────────────────────────────────┐
│  Sidebar  │  Builder Form     │  Live Preview   │
│  (240px)  │  (50% remaining)  │  (50% remaining)│
│           │                   │                 │
│           │  [Business Info]  │  ┌───────────┐ │
│           │  [Client Info]    │  │ Invoice   │ │
│           │  [Line Items]     │  │ Preview   │ │
│           │  [Totals]         │  │           │ │
│           │  [Notes/Terms]    │  └───────────┘ │
│           │                   │                 │
│           │  [Export PDF]     │                 │
└─────────────────────────────────────────────────┘
```

### Invoice Builder Layout (Mobile)

```
Tab: [Form] [Preview]
Active tab content fills full width
```

---

## Invoice & Receipt Document Design

The exported PDF and in-app preview should follow this document layout:

### Invoice Document Structure

```
┌─────────────────────────────────────────────────┐
│  [Logo]                          INVOICE         │
│  Business Name                   #INV-0042       │
│  Business Address                                │
│  business@email.com                              │
├─────────────────────────────────────────────────┤
│  BILL TO                         Issue Date:     │
│  Client Name                     Due Date:       │
│  Client Address                  Status: [badge] │
│  client@email.com                               │
├─────────────────────────────────────────────────┤
│  Item              Qty   Unit Price   Total      │
│  ───────────────────────────────────────────    │
│  Design Services   1     ₦150,000    ₦150,000   │
│  ...                                            │
├─────────────────────────────────────────────────┤
│                         Subtotal:  ₦150,000      │
│                         Tax (7.5%): ₦11,250      │
│                         Total:     ₦161,250      │
├─────────────────────────────────────────────────┤
│  Payment Method: Bank Transfer                  │
│  Notes: Thank you for your business.            │
└─────────────────────────────────────────────────┘
```

**Document Design Rules:**
- Background: pure white (`#ffffff`)
- Primary text: `#1c1917`
- Section headers: uppercase, `text-caption`, `text-muted`, `tracking-wide`
- Dividers: `1px solid #e7e5e4`
- Amount column: right-aligned, GeistMono font
- Total row: bold, larger font, brand red accent for the total amount
- Brand color accent: left border stripe or header accent in `#bf0808`

---

## Motion & Interaction

### Principles

- **Purposeful, not decorative** — Animations communicate state, not personality
- **Fast by default** — Transitions at 150ms–200ms feel snappy and premium
- **Ease-out for entrances, ease-in for exits**

### Transition Tokens

```css
--transition-fast:   150ms ease-out;
--transition-base:   200ms ease-out;
--transition-slow:   300ms ease-out;

/* Use on: buttons, nav items, badge color changes, input focus states */
```

### Micro-interactions

| Element | Interaction |
|---|---|
| Primary button | Scale down 0.97 on press (`active:scale-[0.97]`) |
| Nav item | Background fade on hover (150ms) |
| Card hover | Subtle border color shift (no lift/shadow change) |
| Status badge update | Cross-fade color transition (200ms) |
| Invoice row | Row background fade on hover |
| Form input focus | Border color shift + ring appearance (150ms) |
| Modal open | Fade + scale from 0.96 → 1.0 (200ms) |
| Toast notifications | Slide in from bottom-right (200ms) |

### Page Transitions

- Use `opacity` fade for page-level transitions (Next.js layout transitions)
- Avoid complex route animations — keep it fast and clean

---

## Empty States

Every list, table, or data view must have a designed empty state.

### Empty State Anatomy

```
[Minimal Icon Illustration]
        ↓
  No invoices yet
        ↓
  Create your first invoice to get started
        ↓
  [Primary CTA Button]
```

**Rules:**
- Use simple SVG icons or illustrations — no stock photography
- Main message: h3, text-primary
- Supporting text: body-sm, text-muted
- CTA: primary button
- Centered in the available space with generous vertical padding

---

## Dark Mode

All color tokens have dark mode equivalents. Implement via Tailwind `dark:` variant and a `class="dark"` toggle on the `<html>` element.

### Dark Mode Principles

- Backgrounds use warm near-blacks (not pure `#000000`)
- Borders become subtler against dark backgrounds
- Pastel accents desaturate slightly in dark mode
- Brand red remains consistent (`#bf0808`) — it works on dark
- Text hierarchy is maintained via opacity shifts, not just color changes

### Dark Mode Toggle

- Located in the sidebar footer or top-right header
- Uses a `Sun / Moon` icon toggle
- Persist preference to `localStorage`
- Default: match system preference (`prefers-color-scheme`)

---

## Responsive Breakpoints

```css
/* Tailwind breakpoints used in Remipay */
sm:   640px    /* Large mobile — minor layout adjustments */
md:   768px    /* Tablet — sidebar collapses to icon-only or drawer */
lg:   1024px   /* Desktop — full sidebar + content layout */
xl:   1280px   /* Wide desktop — max content width */
```

### Responsive Behavior

| Breakpoint | Sidebar | Invoice Builder | Tables |
|---|---|---|---|
| Mobile (<768px) | Drawer (slide-in) | Single tab | Card list view |
| Tablet (768–1024px) | Icon-only collapsed | Stacked layout | Simplified table |
| Desktop (1024px+) | Full expanded | Split-screen | Full table |

---

## Iconography

Use **Lucide React** icons exclusively for consistency with shadcn/ui.

```
Size standards:
- Navigation icons:    16px (w-4 h-4)
- Button icons:        16px (w-4 h-4)
- Dashboard icons:     20px (w-5 h-5)
- Empty state icons:   40px (w-10 h-10), text-muted color
- Action icons:        14px (w-3.5 h-3.5)
```

**Key icons used:**
- `FileText` — Invoices
- `Receipt` — Receipts
- `Users` — Clients
- `LayoutDashboard` — Dashboard
- `Download` — PDF export
- `Plus` — Create new
- `Search` — Search
- `ChevronRight` — Navigation
- `CheckCircle` — Paid status
- `Clock` — Pending/sent
- `AlertCircle` — Overdue
- `Moon` / `Sun` — Dark mode toggle

---

## Accessibility Standards

| Standard | Requirement |
|---|---|
| Color contrast | WCAG AA minimum (4.5:1 for body, 3:1 for large text) |
| Focus indicators | Visible focus ring on all interactive elements (brand red `ring-2`) |
| Form labels | All inputs have associated `<label>` elements |
| Status indicators | Color + text/icon (never color alone) |
| Keyboard navigation | Full tab-order support across all components |
| Error messages | Inline, below field, in red with icon |
| Screen readers | Proper ARIA labels on icon-only buttons |

---

## shadcn/ui Component Usage

Remipay is built on shadcn/ui. These components are used and customized:

| Component | Usage |
|---|---|
| `Button` | All CTAs and actions |
| `Input` | All form text inputs |
| `Label` | Form labels |
| `Card` | Dashboard stat cards, content cards |
| `Badge` | Invoice status indicators |
| `Select` | Dropdowns (status filter, currency, payment method) |
| `Dialog` | Modals (client form, confirm actions) |
| `Separator` | Section dividers |
| `Table` | Invoice and client lists |
| `Tabs` | Mobile invoice builder, invoice detail tabs |
| `Sheet` | Mobile sidebar drawer |
| `Tooltip` | Action hints on icon buttons |
| `Toaster` / `Toast` | Success/error notifications |
| `Command` | Search/filter invoice and client list |
| `Avatar` | User profile in sidebar |
| `Switch` | Dark mode toggle |
| `Skeleton` | Loading states for cards and tables |
| `DropdownMenu` | Row actions (edit, delete, duplicate) |

All components are themed to match the Remipay color system via `tailwind.config` and `globals.css` CSS variable overrides.

---

## File & Folder Structure Reference

```
/app
  /auth
    /login
    /signup
  /dashboard
  /invoices
    /new
    /[id]
  /clients
  /receipts
/components
  /ui          ← shadcn/ui components
  /layout      ← Sidebar, Header, MobileNav
  /dashboard   ← StatCard, RecentInvoices
  /invoice     ← InvoiceBuilder, InvoicePreview, InvoiceItem
  /client      ← ClientForm, ClientCard
  /receipt     ← ReceiptPreview
  /shared      ← EmptyState, StatusBadge, LoadingSkeleton
/lib
  /supabase    ← client, server, types
  /pdf         ← export utilities
  /utils       ← formatting, calculations
/styles
  globals.css  ← CSS variables, base reset
```

---

## Summary: Design Don'ts

| ❌ Never | ✅ Instead |
|---|---|
| Use gradients | Use flat solid colors |
| Use heavy shadows on cards | Use border + background-color differentiation |
| Use cold gray neutrals | Use warm stone-scale neutrals |
| Use multiple fonts | Use Geist exclusively (sans + mono) |
| Use dense, small text | Use generous spacing and readable type scale |
| Rely on color alone for status | Always pair color with text label |
| Use complex animations | Use subtle, fast transitions only |
| Center-align body paragraphs | Left-align all paragraph text |
| Use pure black (`#000000`) | Use warm near-black (`#1c1917`) |
| Create visually cluttered tables | Use generous row height and clean separators |

---

*Remipay Design System — Built for clarity, speed, and quiet elegance.*
