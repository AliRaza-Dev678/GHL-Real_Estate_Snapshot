# Reusable GoHighLevel Real Estate CRM & Automation Snapshot

A client-agnostic GoHighLevel snapshot that deploys a full lead-to-close system for real estate clients. Every asset rebrands from a single table of 30 Custom Values, which cuts per-client onboarding from a day of manual edits to under an hour.

**Full build documentation:** [docs/GHL-Real-Estate-Snapshot-Build-Report.pdf](docs/GHL-Real-Estate-Snapshot-Build-Report.pdf)

> This repository holds the documentation for the build. The snapshot itself lives inside GoHighLevel and is not stored here.

## What it covers

Lead capture through landing pages and forms, automatic qualification and routing, sub-60-second speed-to-lead, appointment booking with reminders and no-show recovery, 45-day buyer and seller nurture sequences, review requests after closing, and a Conversation AI agent that qualifies leads and books appointments.

## What was built

| Component | Count | Purpose |
|---|---|---|
| Custom Values | 30 | Client configuration table: the deployment mechanism |
| Custom Fields | 53 | CRM data structure for lead qualification |
| Tags | 41 | Lead state tracking and workflow triggers |
| Pipelines | 3 | Buyer, Seller, and Investor deal tracking |
| Calendars | 4 | Consultation, showing, listing appointment, quick call |
| Forms | 3 | Buyer intake, seller valuation, general contact |
| Surveys | 1 | Multi-step buyer qualification with conditional branching |
| Funnels | 4 (6 pages) | Lead generation and booking pages |
| SMS Templates | 10 | Speed-to-lead, reminders, recovery, reactivation |
| Email Templates | 22 | Transactional plus buyer and seller nurture sequences |
| Workflows | 14 | The automation engine connecting every component |
| Conversation AI | 1 agent | Lead qualification and appointment booking |
| Dashboard | 1 | Performance reporting for the client |

## The core design decision

Every client-specific value (agent name, phone number, brokerage, city, booking links, review link) is stored as a Custom Value instead of being typed into any asset. Deploying to a new client means filling in one table of thirty fields; every SMS, email, landing page, form, and AI prompt rebrands itself.

## Workflows

| Workflow | Behaviour |
|---|---|
| Speed to Lead: Buyer | SMS within 60 seconds of form submission, creates a pipeline opportunity, notifies the agent, escalates if unanswered |
| Speed to Lead: Seller | Same pattern, routed to the Seller pipeline; creates a task to prepare comparables |
| Missed Call Text Back | Automatic SMS after any missed call, creating a contact if none exists |
| Lead Scoring | Score built from timeline, pre-approval status, engagement, and appointment activity |
| Appointment Booked | Confirmations, pipeline stage advance, removal from nurture sequences |
| Appointment Reminders | 24-hour and 1-hour reminders |
| No-Show Recovery | Three-stage rebooking sequence |
| Post-Appointment Follow-Up | Recap email plus an internal task |
| Buyer Nurture | 45-day sequence with exit conditions on reply or booking |
| Seller Nurture | 45-day sequence with the same exit conditions |
| Database Reactivation | Quarterly re-engagement of cold contacts |
| Review Request | Triggered on closed deals; SMS then email |
| Stale Opportunity Alert | Daily check for deals stuck in one stage beyond seven days |
| Unsubscribe / DND Handler | Detects opt-out keywords and removes the contact from every active sequence |

## Compliance built in

- A2P 10DLC-ready SMS consent language on every form
- Do-not-contact checks before every send in every messaging workflow
- Exit conditions on all automated sequences

## Deploying to a client

1. Business profile and branding
2. Phone number and A2P 10DLC registration (start first)
3. Email sending domain (SPF, DKIM, DMARC)
4. Complete the 30 Custom Values
5. Add client users
6. Assign and connect calendars
7. Connect integrations
8. Publish forms and funnels
9. Connect the client domain
10. Supply client content for the marked placeholder sections
11. Activate workflows
12. End-to-end test

Details for every step are in the build report.

## Stack

GoHighLevel, Conversation AI, HTML email, A2P 10DLC

## Author

Ali Raza, Full-Stack AI Engineer
[Portfolio case study](https://ali-raza-engineer.vercel.app/projects/ghl-real-estate-crm-snapshot) | [GitHub](https://github.com/AliRaza-Dev678)
