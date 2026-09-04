# MMG CRM

A **mock** lead-intake CRM for MMG (Messina Madrid Global) — a demonstration of the intake
workflow, not a system of record. Never enter real client, prospect or company details. One
HTML file, no build step. Data lives in a Firebase Realtime Database with anonymous
sign-in, so everyone who opens the page sees the same leads, live. It is all fake, and
anyone with the URL can read and write it.

Live: https://bih-mmg.github.io/mmg-crm/

## What it does

- **Leads** — searchable, sortable table; filter by stage, destination, owner. Overdue
  follow-ups in red.
- **Lead** — intake form laid out the way the 15-minute free call runs: contact, current
  status, who's moving, work, money, intent. Stage, owner, follow-up date, activity log.
- **Screening hints** — rule-of-thumb fit per programme (Spain DNV / NLV, Thailand LTR /
  Privilege, Malta MPRP / GRP, Canada Express Entry / PNP / sponsorship) computed from the
  saved values against the Ready Reckoner thresholds. Never a processing time, never a
  settlement-funds figure. The consultant confirms.
- **Pipeline** — kanban by stage; drag a card or use ‹ ›. Moving a lead to *Free call held*
  while the intake owner (Admin) still holds it asks which rep took the call and makes them
  the owner.
- **Dashboard** — counts by stage, destination, owner, source; free-call-to-paid-consult
  conversion; overdue list.
- **Data** — load the 58 sample leads, clear all, export JSON / CSV, restore from file or
  pasted text.
- **Admin** — mock admin panel behind a PIN (default `0000`, changeable there). Owners
  table: add, rename, remove (leads are reassigned), role (Rep / Partner / Admin), active
  toggle, default owner for new leads. The PIN is a demo gate, not security.

## Stages

New lead → Free call booked → Free call held → Agreed to paid consult → Handed to partner →
Scheduling email sent → Paid → Paid consult held → Service engagement → Closed (won / lost /
not yet).

## Notes

- Sample leads are the 58 fictional practice callers from the Call Training sets — name only,
  with generated example.com emails and 555 phone numbers, all at Free call booked.
- Currency conversion in the hints uses rough fixed rates; it exists only to compare against
  thresholds.
- Storage: Firebase project `mmg-crm-3b949`, Realtime Database in asia-southeast1.
  `/leads/{id}` holds one lead each; `/settingsJson` holds the settings as a JSON string.
  Rules are `auth != null` for read and write, satisfied by anonymous sign-in (enabled in
  Firebase Authentication). The Firebase config in `index.html` is not a secret.
- `localStorage` (`crm_leads`, `crm_settings`) is a cache. Opened as a plain
  file without the SDK, the app runs local-only, which is how the test harness drives it.
- *Clear all leads* clears the shared database for everyone. Download a backup first.
