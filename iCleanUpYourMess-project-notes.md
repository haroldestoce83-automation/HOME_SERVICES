# iCleanUpYourMess — Project Notes

## Overview

Business: **iCleanUpYourMess**, a home cleaning service (Philippines, ₱ pricing).

Goals:
1. Build a lead-capture funnel + automated new-lead notification (welcome email to customer, alert email to admin) as a low-stakes practice project before rebuilding the same system in GoHighLevel (GHL).
2. Get hands-on reps with CRMs that show up repeatedly in job postings — GoHighLevel, HubSpot, Salesforce, Zoho — since GHL fluency alone isn't guaranteed to be the tool used at every job.

## Assets & Links

**Solar landing page** (earlier unrelated practice run — "HaroldE Solar Coordinator"):
- Preview: https://id-preview--750c777a-2597-46a7-9ee2-f40e7027b3b8.lovable.app
- Editor: https://lovable.dev/projects/750c777a-2597-46a7-9ee2-f40e7027b3b8

**iCleanUpYourMess — Lovable build** (paused, ran out of free credits mid-build):
- Preview: https://id-preview--47f4edde-ddfc-4045-8b04-9f48c1fba115.lovable.app
- Editor: https://lovable.dev/projects/47f4edde-ddfc-4045-8b04-9f48c1fba115

**iCleanUpYourMess — static HTML landing page** (current, no credits needed):
- File: `icleanupyourmess-landing.html`
- Plain HTML/CSS/JS, single file. Sections: hero, trust stats, services, pricing table, how-it-works, testimonials, lead form, footer.
- Lead form currently points at a placeholder `action` — not yet wired to a real backend. Setup notes for wiring it to Zoho are written as a comment at the bottom of the file.

## Pricing Table (source data)

| Building Type | Typical Services Included | Price |
|---|---|---|
| Studio Condo (20–35 sqm) | Dusting, vacuuming, mopping, bathroom cleaning, kitchenette cleaning, trash removal | ₱1,200 |
| 1-Bedroom Condo (35–60 sqm) | General cleaning, kitchen countertops, bathroom, mirrors, floor cleaning | ₱1,800 |
| 2-Bedroom Condo (60–90 sqm) | Full condo cleaning, bathrooms, kitchen, bedrooms, balcony (if any) | ₱2,800 |
| 3-Bedroom Condominium (90–130 sqm) | Complete cleaning including living areas, kitchen, bathrooms, interior windows | ₱4,000 |
| Small Townhouse (70–100 sqm) | Whole-house cleaning, stairs, bathrooms, kitchen, bedrooms | ₱3,500 |
| Medium Townhouse (100–150 sqm) | Deep dusting, floor care, bathrooms, kitchen appliances exterior, stairs | ₱5,000 |
| Single Detached House (100–180 sqm) | Complete interior cleaning, multiple bathrooms, kitchen, bedrooms | ₱6,500 |
| Large Single Detached House (180–300 sqm) | Detailed house cleaning, ceiling fans, light fixtures, interior windows | ₱9,000 |
| Luxury Home / Villa (300–500 sqm) | Premium cleaning, multiple living areas, large kitchens, several bathrooms | ₱15,000 |
| Move-In / Move-Out Cleaning (any residential property) | Empty property deep cleaning, cabinets, closets, appliances (exterior), interior windows | Starts at ₱5,000 |

## Lead Pipeline (mapped out earlier)

1. **New Lead** — form submitted, record created
2. **Contacted** — admin calls, handshake conversation
3. **Discovery** — needs and scope assessed
4. **Quote Sent** — price and scope shared
5. **Booked** — appointment date confirmed
6. **Completed** — cleaning job done
7. **Follow-Up** — review and feedback requested
8. **Won / Lost** — repeat customer, or not interested / no response

Automated today (planned): welcome email to customer + admin alert email to `guidoifawkes83@gmail.com`, both triggered the moment the form is submitted. Email only for now — no SMS. Everything from "Contacted" onward stays manual (admin picks up the phone).

## Automation Philosophy (notes to self)

- No live automation system yet by design — building reps gradually before going all-in on GHL.
- Strategy/logic reps transfer between tools (offer, page structure, follow-up sequence content/timing, pipeline stages). Tool-specific UI reps (a specific automation builder's buttons) mostly don't transfer — don't over-invest time there.
- A script-based automation approach (webhook → conditional logic → CRM API call → scheduled follow-up check) mirrors GHL's own trigger → condition → action → wait structure, so it's legitimate practice even outside GHL, not wasted effort.

## CRM Practice Plan

Most requested in job postings, roughly in order: **GoHighLevel, HubSpot, Salesforce, Zoho** (all four repeatedly show up; Zoho already chosen as first CRM to get real reps in since it has a genuinely free tier with both pipeline and at least one real workflow automation).

### Zoho Setup Progress

- [x] Signed up for free Zoho CRM account (3 users, 1 workflow rule, 5,000 API calls/day, Web-to-Lead forms included)
- [ ] **Phase 1** — Add custom fields to Leads: `Property Type` (pick list, 10 values matching the pricing table above) and `Preferred Date` (date field)
- [ ] **Phase 2** — Build the Web-to-Lead form (Setup → Developer Space → Web Forms), map fields, grab the generated form `action` URL + hidden inputs, paste into `icleanupyourmess-landing.html`
- [ ] **Phase 3** — Set Deal pipeline stages to mirror the lead pipeline above
- [ ] **Phase 4** — Create the one free Workflow Rule (Trigger: Lead Created) with two actions: welcome email to the lead + admin alert email to `guidoifawkes83@gmail.com`

### GHL → Zoho concept map

| GHL concept | Zoho equivalent | Note |
|---|---|---|
| Contact (flat record) | Lead → converts to Contact + Deal | Biggest conceptual gotcha — see below |
| Pipeline / Opportunities | Deals module, Pipeline stages | Same kanban drag-drop idea |
| Workflows (trigger→action) | Workflow Rules | Free tier = 1 rule, but a rule can have multiple actions |
| Tags | Tags | Transfers directly |
| Custom Fields | Custom Fields (Setup → Modules → Fields) | Same idea, different menu |
| Forms/surveys | Web-to-Lead Forms (or Zoho Forms) | No API key exposed — safe for a public page |
| Calendars/booking | Zoho Bookings (separate free product) | Not built into CRM itself |
| Snapshots (templates) | No free equivalent | Closest is Blueprint, paid-only |

**Key gotcha:** GHL keeps one continuous contact record as it moves through the pipeline. Zoho (like Salesforce and HubSpot) splits this into a Lead → Convert → Contact/Account/Deal flow. Getting comfortable with that conversion step in Zoho effectively teaches the same concept in Salesforce and HubSpot too.

## Next Steps

1. Finish Zoho Phase 1 (custom fields on Leads)
2. Phase 2: build the Web-to-Lead form, paste the real action URL + hidden fields into `icleanupyourmess-landing.html` (replacing the placeholder)
3. Phase 3 & 4: pipeline stages + the one workflow rule (welcome + admin alert)
4. Decide whether to keep iterating on the static HTML page or revisit the Lovable build once credits refresh
5. Once Zoho reps feel solid, repeat similar hands-on setup in HubSpot's free tier for pipeline/deal-stage practice
