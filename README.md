# MMG CRM

A dummy lead-intake CRM for MMG (Messina Madrid Global). One HTML file, no backend, no
dependencies. Everything typed into it stays in the browser's `localStorage`.

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
- **Pipeline** — kanban by stage; drag a card or use ‹ ›.
- **Dashboard** — counts by stage, destination, owner, source; free-call-to-paid-consult
  conversion; overdue list.
- **Data** — load 12 sample leads, clear all, edit the owner list, export JSON / CSV,
  restore from file or pasted text.

## Stages

New lead → Free call booked → Free call held → Agreed to paid consult → Handed to partner →
Scheduling email sent → Paid → Paid consult held → Service engagement → Closed (won / lost /
not yet).

## Notes

- Sample leads are fictional.
- Currency conversion in the hints uses rough fixed rates; it exists only to compare against
  thresholds.
- Storage keys are `crm_leads` and `crm_settings`.
- Data never leaves the browser. Use *Download backup* before clearing a browser or
  switching machines.
