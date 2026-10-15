# 📦 LabelForge — Enterprise SaaS WMS Starter Kit

> LabelForge is a commercial-quality, full-stack B2B Multi-Tenant Warehouse Management System (WMS) SaaS boilerplate and starter kit. Engineered with **Next.js (App Router), Tailwind CSS v4, Drizzle ORM, and PostgreSQL**, it provides everything required to launch or scale modern logistics, 3PL distribution networks, and fulfillment hub software.

[![https://labelforge-ochre.vercel.app/](https://img.shields.io/badge/Demo-Live_Preview-success?style=for-the-badge)](VOTRE_LIEN_DEMO_VERCEL)
[![https://github.com/LabelForgeHQ/labelforge/blob/main/docs/02_ARCHITECTURE.md](https://img.shields.io/badge/Docs-Architecture_Guide-blue?style=for-the-badge)](VOTRE_LIEN_DOCUMENTATION)
[![https://buy.polar.sh/polar_cl_4hLlciLo4KK2DzECHnfhT1cj49QfjNZNW81nw1sf8nq](https://img.shields.io/badge/Polar.sh-Get_Full_Source_Code-orange?style=for-the-badge)](VOTRE_LIEN_POLAR)

---

## 🏛️ Core Architectural Highlights

- **Clean Architecture & Frozen Domain Engine:**
  - Business logic strictly isolated inside pure domain services (`src/services/inventory/*`), fully decoupled from HTTP presentation layers.
  - Formal regression invariants protected by automated PostgreSQL lifecycle tests.
- **Fail-Closed Zero-Trust Multi-Tenancy:**
  - Complete tenant boundary isolation on every query and mutation via workspace scoping.
  - Server-side `TenantContextBridge` verifying active membership before granting context. Tamper-proof handling of workspace headers.
- **Granular RBAC Permissions Matrix:**
  - 16 atomic permissions mapped to 5 hierarchical roles: `OWNER`, `ADMIN`, `WAREHOUSE_MANAGER`, `OPERATOR`, and `VIEWER`.
- **Immutable Double-Entry Styled Inventory Ledger:**
  - Every stock movement generates an immutable, append-only record in `stock_movements` capturing movement types (`RECEIPT`, `PICK`, `TRANSFER`, `ADJUSTMENT`, `RETURN`), signed quantities, running balances, and audit actors.
  - **Invariant:** Total on-hand physical stock strictly equals the cumulative balance of all historical ledger movements.
- **Modern UI & Design System:**
  - Built using Tailwind CSS v4 with semantic OKLCH color tokens, responsive sidebar drawers, and high-density components.

---

## 🗺️ Enterprise Module Map

- **Executive Overview (`/dashboard`):** Real-time KPI metric cards (Available units, Reserved allocations, Active SKUs, Locations) and live stock movement stream.
- **Real-Time Inventory (`/inventory`):** Enterprise compact density table with multi-filter search (SKU, barcode, product), warehouse selectors, and stock status badges.
- **Warehouses & Storage Locations (`/locations`):** Facility map, multi-zone type badges, capacity utilization, and interactive barcode preview with printable shelf labels.
- **Warehouse Floor Scanner Terminal (`/scanner`):**
  - **Optical Viewfinder HUD:** Live targeting reticle with smooth animated scanning laser sweep.
  - **Hardware Wedge Scanner Support:** Auto-focused input responding to physical USB/Bluetooth barcode ring scanners.
  - **Real-Time Asset Resolution:** Instant lookup of SKU, variant description, bin location, and on-hand availability.
- **Access Control & Organization (`/settings/*`):** Multi-tenant workspace configuration, member invitations, and granular role management.

---

## 🧪 Quality & Testing Standards

LabelForge maintains a 100% test pass rate with **90 passing tests across 8 test suites**:

- `permissions.test.ts` (38 tests) — RBAC matrix and permission enforcement.
- `tenant-context.test.ts` (9 tests) — Zero-trust context resolution and header tamper rejection.
- `workspace-service.test.ts` (6 tests) — Workspace domain service and uniqueness constraints.
- `member-service.test.ts` (9 tests) — Member invitations and Last Owner invariant guard.
- `demo-login.test.ts` (7 tests) — 1-Click Demo Persona authentication and redirect contracts.
- `demo-auth-session.test.ts` (8 tests) — Session verification, HMAC cookie signing, and cross-tenant isolation.
- `inventory-api-routes.test.ts` (10 tests) — Protected API routes, 401/403/422 guards, and standard envelopes.
- `inventory-lifecycle.test.ts` (3 tests) — Core inventory domain lifecycle against PostgreSQL.

---

## 🚀 Live Demo & Access

Experience the full enterprise application with 1-click demo access:

- **Interactive Demo:** [Launch Live Preview](https://labelforge-ochre.vercel.app/)
- **Architecture Documentation:** [Explore the Docs](https://github.com/LabelForgeHQ/labelforge/blob/main/docs/02_ARCHITECTURE.md)
- **Purchase Source Code Access:** [Instant GitHub Access on Polar.sh](https://buy.polar.sh/polar_cl_4hLlciLo4KK2DzECHnfhT1cj49QfjNZNW81nw1sf8nq)

---

## 📄 License & Commercial Terms

LabelForge is an enterprise commercial software starter kit. Full source code access is provided under a Commercial Developer License via Polar.sh upon purchase.
