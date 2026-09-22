# UAT Runbook — Product-3 (Order Management & Fulfillment Cascade)

## Feature
Order placement and event mesh cascade propagation

## Preconditions
- Service is configured with valid environment (`.env.local` or `.env.example`).
- Database migrations have been applied via `make migrate`.
- Required port is free and accessible.

## Steps
1. Start Product-3 on port 8083 alongside running fleet services
2. Submit order via POST /api/v1/orders with customer ID, SKU, and quantity
3. Verify order status transitions to 'submitted' / 'confirmed'
4. Verify event mesh dispatch logs confirm delivery to downstream services

## Expected Results
- Order is created with unique Order ID and status 'confirmed'
- Event mesh dispatches order.created event to Billing, Notifications, Audit, Telemetry, and Jobs

---
*Author: QA & Primary Owner (MasterSpec Section 31.1, Section 33.1)*
*Verification Contract: `verification/contract.yaml`*
