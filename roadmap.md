# HungryBird Product Roadmap

**Document owner:** Product + Engineering  
**Last updated:** February 18, 2026  
**Audience:** Founders, operators

This roadmap is the execution record for building HungryBird from prototype to launch. It is intentionally outcome-driven: each sprint maps to shipped capability, operational impact, and launch readiness.

## Program Snapshot

- **Total program:** 12 sprints across 4 phases
- **Completed:** **11/12 sprints**
- **Current stage:** Launch readiness
- **Next milestone:** Sprint 12 (Go Live)

## Sprint Status Ledger

| Sprint | Focus | Status | Outcome |
| --- | --- | --- | --- |
| 1 | Platform Infrastructure & Subdomain Routing | **Complete** | Single codebase serving customer, merchant, rider, and admin surfaces |
| 2 | Supabase Schema, Auth, and Role Access | **Complete** | Unified data/auth backbone with role-aware routing and policy model |
| 3 | Merchant Onboarding + Menu Operations | **Complete** | Merchants can onboard, manage store profile, and run menu CRUD |
| 4 | Customer Feed on Live Data | **Complete** | Customer experience migrated from static data to database-backed APIs |
| 5 | Checkout, Payments, and Fee Logic | **Complete** | Stripe Connect flow live with marketplace split logic and order linkage |
| 6 | Merchant KDS Operations | **Complete** | Real-time order handling from new to ready-for-pickup |
| 7 | Rider Portal (PWA) | **Complete** | Mobile-first rider app with onboarding, availability control, and earnings/settings views |
| 8 | Dispatch Engine + Atomic Batch Claim | **Complete** | Batch creation and race-safe driver claim flow implemented |
| 9 | Delivery Completion + Notifications | **Complete** | End-to-end delivery progression, completion handling, and customer comms loop |
| 10 | Admin Control Plane | **Complete** | Admin dashboard with platform visibility and control actions |
| 11 | Hardening, Testing, and Performance | **Complete** | Auth isolation tests, API integration tests, load scripts, caching, and DB index hardening |
| 12 | Production Launch | **Planned** | Domain cutover, production keys, partner rollout, and launch operations |

## Phase-by-Phase Progress

## Phase 1: Foundation (Sprints 1-3) - **Complete**

### Sprint 1 - Infrastructure & Routing - **Complete**
Delivered:
- Transition from static export constraints to server-capable architecture.
- Host-based routing for subdomain-specific app surfaces.
- Baseline multi-portal structure for customer, merchant, rider, and admin.

Business impact:
- Established the core platform topology required for role-specific products without splitting the codebase.

### Sprint 2 - Data & Auth Backbone - **Complete**
Delivered:
- Supabase-first data model for profiles, restaurants, menu, orders, drivers, and delivery batches.
- Role-aware authentication flows and protected route behavior.
- PostGIS-enabled location model for proximity search and dispatch logic.

Business impact:
- Replaced prototype-level assumptions with a durable, policy-driven production data backbone.

### Sprint 3 - Merchant Supply Platform - **Complete**
Delivered:
- Merchant onboarding flow with operational setup fields.
- Menu CRUD and availability control.
- Merchant dashboard and settings foundation.

Business impact:
- Supply-side operations are now self-serve, reducing manual onboarding overhead.

## Phase 2: Transaction Loop (Sprints 4-6) - **Complete**

### Sprint 4 - Live Customer Data Layer - **Complete**
Delivered:
- API routes for restaurants, menu, and search.
- Customer feed migration from static fixtures to live records.
- Location-aware discovery flow connected to persisted coordinates.

Business impact:
- Students now see current inventory and real merchant availability.

### Sprint 5 - Ordering & Payments - **Complete**
Delivered:
- Checkout pipeline and order creation lifecycle.
- Stripe Connect marketplace mechanics with transfer-group linkage.
- Shared pricing logic for delivery fee modes.

Business impact:
- Core monetization path is operational and traceable across order/payment records.

### Sprint 6 - Merchant Kitchen Operations - **Complete**
Delivered:
- Merchant order management interface for prep-state transitions.
- Real-time state updates and workflow visibility.

Business impact:
- Restaurants can execute from order intake to pickup-ready with low operational friction.

## Phase 3: Logistics Network (Sprints 7-9) - **Complete**

### Sprint 7 - Rider Portal (PWA) - **Complete**
Delivered:
- Mobile-first rider interface suitable for home-screen usage.
- Rider onboarding with profile, vehicle, and payout-link setup.
- Dashboard controls for online/offline state plus settings and earnings views.

Business impact:
- Driver-side capacity can be activated and managed in real time.

### Sprint 8 - Dispatch and Atomic Claims - **Complete**
Delivered:
- Dispatch engine that groups ready orders into driver batches.
- Driver-facing batch discovery/decision endpoints.
- Atomic acceptance logic to prevent double-assignment race conditions.

Business impact:
- Assignment reliability improved under concurrency, protecting delivery integrity.

### Sprint 9 - Delivery Completion & Notifications - **Complete**
Delivered:
- Active delivery flow from pickup to drop-zone completion.
- Completion-state progression for order lifecycle closure.
- Customer communication events for key order milestones.

Business impact:
- Full operational loop is closed from order placement to delivery confirmation.

## Phase 4: Governance and Scale Readiness

### Sprint 10 - Admin Control Plane - **Complete**
Delivered:
- Admin-only surface with role-gated access.
- Platform management pages for operational entities.
- Server-side admin action routes for intervention workflows.

Business impact:
- Leadership has direct visibility and control across supply, demand, and logistics.

### Sprint 11 - Hardening & Stress Testing - **Complete**
Delivered:
- Cross-subdomain auth isolation and authorization behavior validation.
- Integration test suite for auth, orders, restaurants, and dispatch.
- Load/stress scripts for order bursts, browsing churn, and dispatch churn.
- Performance improvements via indexing and caching strategy.
- Failure-path handling for payment and dispatch edge cases.

Business impact:
- Platform moved from feature-complete to reliability-focused, reducing launch risk.

### Sprint 12 - Go Live - **Planned**
Scope:
- Production environment finalization (domains, secrets, webhooks, monitoring).
- Initial campus rollout operations (restaurant onboarding, rider ramp, support runbook).
- Launch readiness review with rollback and incident playbooks.

Exit criteria:
- Zero-blocker launch checklist signed by Product, Engineering, and Operations.
- First production cohort transacts successfully end-to-end.

## Launch Readiness Checklist (Pre-Sprint 12 Signoff)

- Production secrets rotated and verified across all environments.
- Stripe live mode and webhook signatures validated.
- Database backups, restoration drill, and alerting baselines confirmed.
- Critical-path test pass for order -> dispatch -> delivery -> payout.
- On-call escalation matrix and incident command workflow published.

## Why This Plan Is Investor-Grade

- It shows **sequenced execution**, not feature sprawl.
- It demonstrates **risk retirement** in the right order: architecture -> revenue -> logistics -> governance -> reliability.
- It provides a clear handoff from build phase to launch phase with objective signoff gates.

## Appendix: Strategic Design Principles

- **Single codebase, multi-surface architecture:** faster iteration and lower maintenance overhead.
- **Marketplace-native money movement:** Stripe Connect for clean settlement and payout accounting.
- **Race-safe dispatch core:** atomic claim model to preserve assignment correctness under load.
- **Location economics discipline:** geocode-once and query-local strategy to control infra cost.
- **Operational observability:** admin tooling plus test/load coverage before production scaling.
