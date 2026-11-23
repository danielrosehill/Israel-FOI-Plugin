# Israel FOI

Agent skills for Israeli Freedom of Information requests (חוק חופש המידע, התשנ"ח-1998):
choosing the authority that actually holds the information, drafting the request in
Hebrew, filing it through that authority's own channel, and tracking the statutory deadline.

## Skills

| Skill | Status | What it does |
|---|---|---|
| `jerusalem-municipality-foi` | working (filed live 2026-11-23) | Jerusalem Municipality: officer and contacts, the 3-step online form with its field limits and validation quirks, two-factor step, attachments, fee commitment, after-filing record. Covers building/permit files (local planning committee), noise and nuisance enforcement, complaints and inspections. |
| `jerusalem-foi-status` | working (2026-11-23) | Check status in the city's סטטוס דיגיטל portal: login by request number plus mobile or email with a two-step code, statuses and sub-statuses explained, read-only form view with department notes, what to do on each status. Also covers 106 hotline and other city forms. |

Shared reference: `references/israel-foi-basics.md`: which authority holds what,
the s.20 "use the other access route" caveat (inspect the building file directly too),
deadlines, fees, how to write the request.

More authorities (other municipalities, ministries) can be added as one skill each.

## Boundaries

The agent drafts and fills forms. The user enters their ID number and attaches any ID
copy, enters two-factor codes, ticks the fee commitment and terms, submits, and pays.

## Installation

```bash
claude plugins install israel-foi@danielrosehill
```
