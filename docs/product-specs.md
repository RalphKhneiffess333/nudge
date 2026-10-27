---
title: "Product Specs - Nudge"
author: "Ralph Khneiffess"
---

# Nudge - Product Specs
This document defines product behavior, requirements and acceptance criterias of Nudge.

## Overview
### Context 
The rapid digitization of local retail has shifted consumer expectations toward unified, high speed convenience. In dense urban markets, consumers rely heavily on on-demand delivery for everyday needs, ranging from restaurant meals and daily groceries to pharmacy items and point-to-point courier services.

### Problem
Currently, local commerce operates in a fragmented ecosystem: merchants rely on separate sales channels, traditional courier networks lack real-time visibility, and consumers often bounce between multiple single-purpose apps to fulfill different daily errands.
As a result of this fragmentation, consumers experience severe app fatigue, high cumulative delivery costs, and zero real-time visibility. Merchants face high operational overhead trying to manage delivery independently, restricting their customer reach.

### Goal
Capture high-frequency consumer demand, modern multi-vertical delivery, restaurant ordering, grocery fulfillment and retail commerce into a single unified app experience.

### Solution
Nudge is an all-in-one on-demand platform designed to unify local commerce and hyper-local logistics under a single user experience. 

By aggregating disparate verticals into one interface, Nudge connects consumers, local merchants, and freelance couriers through an automated, real-time fulfillment engine.

## Project Context
### Known Facts
The following facts are currently verified:
- Clients and customers desire orders and items on delivery
- Merchants and restaurants want to provide delivery services to customers
- Delivery couriers can provide transportation of items
- A way is needed to coordinate all these
- The app is meant to be used globally so time, currency and language should be handled.

### Assumptions

The following assumptions are made for Nudge:
- The app will be heavily utilized so a scalable architecture needs to be developed
- Clients and consumers prefer using a unified app instead of individual company specific delivery apps.
- Merchants are willing to share a percentage of sales or pay a platform fee in exchange for expanded customer reach and outsourced delivery.
- Merchants can fulfill orders fast enough to support hyper-local, sub-hour delivery promises without causing driver bottlenecks
- Local merchants (restaurants, pharmacies, bakeries, retail shops) have digitizable product catalogs and are willing to adopt Nudge’s merchant tools and portal to handle orders.
- There is a sufficient, steady supply of freelance couriers with their own transportation (mopeds, bikes, cars) willing to perform both standard deliveries

### Constraints
- This application is developed as part of a course project and won't support full feature implementations due to time constraints.
- Payments cannot be developed as part of this project
- Only a web app will be developed excluding mobile platforms

### Non-Goals
- Integrating live credit card processors (e.g., Stripe, Checkout.com) will not be built. The MVP will mock payments or rely strictly on simple Cash on Delivery (COD) / simulated wallet flows.
- Automated banking payouts and tax withholdings will be excluded.
- Users cannot mix items from two different restaurants or grocery stores in a single checkout order. Orders remain strictly 1 Store = 1 Order.
- Live two-way integration with external legacy POS software (e.g., Micros, NCR) is excluded. Merchants will manage inventory directly via a simple, simplified Nudge web dashboard.
- Edge-case dispute resolutions and automated partial refund workflows will be handled manually/mocked rather than automated.
- Grouping multiple separate user orders onto a single driver route based on complex machine learning will not be built. Dispatch will use a simplified radius/closest-available-driver logic.
- Freight, van, or specialized cold-chain logistics selection will not be supported; dispatch assumes standard two-wheeler/car delivery capabilities.

### Actors
#### Customer
The primary consumer requesting food, groceries and retail items.
Main actions include:
- Browse merchant catalogs, filter categories, search items, and add products to a single-store cart.
- Place orders, select payment methods (Cash on Delivery / Simulated Wallet), and receive real-time updates.
- Track active deliveries with live GPS courier positioning on an interactive map.
- Rate and review completed orders and couriers.

#### Merchant
Third-party retail business owners (restaurants, supermarkets, pharmacies, specialty stores) selling items through the platform.
Main actions include:
- Create, update, and manage product listings, pricing, and category catalogs.
- Toggle inventory availability (e.g., mark items as "Out of Stock" or temporarily pause store ordering).
- Receive incoming customer orders, accept/reject requests, and set estimated preparation times.
- Update order preparation status (e.g., "Accepted", "Preparing", "Ready for Pickup").

#### Courier (Delivery Driver)
Freelance logistics partners responsible for picking up orders/parcels and delivering them to end consumers.
Main actions include:
- Toggle online/offline availability to receive incoming delivery requests.
- Accept or decline assigned delivery offers within a designated timeout window.
- Access turn-by-turn navigation instructions for merchant pickup
- Update order status throughout the lifecycle (e.g., "Arrived at Store", "Picked Up", "Arrived at Customer", "Delivered").
- Collect payments (for Cash on Delivery orders)

#### System Administrator
Internal team members managing platform parameters, oversight, and operational health.
Main actions include:
- Manage and onboard user accounts, merchant profiles, and courier credentials.
- Oversee platform-wide live orders, active courier locations, and system dispatch health.
- Manage global system configurations (e.g., base delivery fees, service radiuses, active city regions).
- View system analytics and transaction logs.
