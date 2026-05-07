# System Overview

## Overview

The Vibrant Fusion platform evolved from a responsive customer-facing website into a broader customer engagement and operational platform integrating loyalty workflows, kiosk systems, realtime admin tooling, promotions infrastructure, and transactional customer tracking.

The system was independently architected and implemented as a modular cloud-based platform emphasizing:

- lightweight operational infrastructure
- realtime synchronization
- serverless backend workflows
- maintainable frontend systems
- incremental platform extensibility

The architecture intentionally prioritized simplicity, scalability, and low operational overhead while supporting real-world business workflows.

---

# Platform Architecture

The platform consists of five primary system layers:

1. Customer-Facing Website
2. Loyalty & Rewards Platform
3. Kiosk Workflow System
4. Admin Operations Dashboard
5. Promotions & Messaging Infrastructure

Each subsystem was designed to operate independently while sharing centralized backend services and database infrastructure.

---

# High-Level Architecture

```text
┌──────────────────────┐
│  Customer Website    │
│  (Public Frontend)   │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│   Kiosk System       │
│  Customer Check-ins  │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────────────┐
│   Netlify Functions / APIs   │
│  Serverless Backend Layer    │
└──────────┬───────────────────┘
      │
      ▼
┌──────────────────────────────┐
│        Supabase Backend      │
│ PostgreSQL + Realtime + Auth │
└───────┬─────────┬────────────┘
   │         │
┌───────────────┘         └────────────────┐
▼                                          ▼
┌───────────────────┐                 ┌────────────────────┐
│   Admin Dashboard │                 │ Promotions Engine  │
│ Requests / Points │                 │ SMS Campaigns      │
└─────────┬─────────┘                 └─────────┬──────────┘
│                                     │
▼                                     ▼
┌────────────────┐                    ┌─────────────────┐
│ Members DB     │                    │ Promotions DB   │
│ Transactions   │                    │ Recipients DB   │
│ Pending Req DB │                    └─────────────────┘
└────────────────┘
```

---

# Core System Components

# 1. Customer Website

The public-facing website serves as the frontend engagement layer of the platform.

Primary responsibilities include:

- customer engagement
- product discovery
- menu browsing
- branding and presentation
- business information delivery
- customer navigation workflows

The frontend was designed mobile-first with responsive rendering optimized across desktop and mobile devices.

See:
- [Website Platform](website-platform.md)

---

# 2. Loyalty Platform

The loyalty subsystem manages:

- member registration
- points accumulation
- redemption workflows
- visit tracking
- customer reward eligibility
- transaction history

The loyalty architecture was intentionally designed around extensible transactional workflows rather than static point counters.

See:
- [Loyalty Platform](loyalty-platform.md)

---

# 3. Kiosk Workflow System

The kiosk platform functions as a customer interaction layer enabling:

- phone number submissions
- visit check-ins
- loyalty requests
- redemption initiation

The kiosk system was intentionally designed as an input-only operational surface.

Business decisions and transactional updates are processed through backend services and admin workflows rather than directly within kiosk clients.

See:
- [Kiosk Admin Sync](kiosk-admin-sync.md)

---

# 4. Admin Operations Dashboard

The admin platform manages operational workflows including:

- request approvals
- redemption processing
- member management
- realtime operational visibility
- transaction monitoring

The admin system integrates realtime subscriptions enabling immediate synchronization between kiosk submissions and operational actions.

---

# 5. Promotions Infrastructure

The promotions subsystem supports customer engagement workflows including:

- SMS campaign processing
- promotions targeting
- recipient tracking
- opt-in workflows
- campaign delivery management

The messaging architecture was designed with future compliance and extensibility considerations for transactional and promotional messaging systems.

See:
- [Promotions Engine](promotions-engine.md)

---

# Backend Architecture

The backend infrastructure leverages a lightweight serverless architecture using:

- Netlify Functions
- Supabase
- PostgreSQL
- realtime database subscriptions

Primary backend responsibilities include:

- transactional processing
- API orchestration
- loyalty state management
- realtime synchronization
- request validation
- admin authorization
- promotions processing

The backend architecture intentionally avoided monolithic service patterns in favor of smaller isolated operational workflows.

---

# Realtime Synchronization Model

Realtime synchronization is a core architectural feature of the platform.

The system uses realtime database subscriptions to synchronize:

- kiosk submissions
- admin actions
- request status updates
- transactional changes
- operational visibility

This model enabled near real-time operational workflows without requiring dedicated websocket infrastructure or custom synchronization services.

---

# Data Architecture

The platform uses relational database modeling for operational consistency and transactional traceability.

Core database entities include:

- members
- transactions
- pending requests
- promotions
- promotion recipients

The schema design emphasized:

- auditability
- transactional consistency
- operational simplicity
- extensibility for future workflows

---

# Security & Operational Controls

Security controls were incorporated across:

- admin authentication
- protected operational actions
- environment variable isolation
- backend validation
- database access policies
- controlled server-side workflows

Operational actions involving loyalty updates and transactional processing were intentionally isolated from direct frontend execution.

---

# Deployment Strategy

The platform uses a cloud-native deployment model emphasizing:

- low maintenance overhead
- rapid deployment iteration
- simplified infrastructure management
- scalable frontend delivery
- serverless backend execution

Deployment components include:

- Netlify hosting
- GitHub-based version control
- Supabase managed backend infrastructure
- environment-based deployment configuration

---

# Engineering Scope

This project involved independent ownership across:

- frontend engineering
- backend development
- database architecture
- realtime workflow design
- serverless infrastructure
- deployment management
- operational tooling
- customer engagement systems

The platform served as both a production business system and a practical engineering initiative focused on scalable web platform architecture and operational workflow design.
