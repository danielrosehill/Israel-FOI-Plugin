---
name: jerusalem-foi-status
description: Check the status of a Jerusalem Municipality FOI request (or any of the user's online requests to the city, e.g. 106 hotline, arnona) in the "סטטוס דיגיטל" portal - status trail, sub-status, department notes, stored form. Use on "status of my FOI request Jerusalem", "check request 4…", "did the municipality answer", "מה הסטטוס של הבקשה".
---

# Jerusalem request status (סטטוס דיגיטל)

One portal shows **every online form the person filed with the municipality**: FOI,
106 hotline reports, arnona and so on. Each entry has its status trail. Verified
2026-11-23 on an FOI request filed the same day.

## Log in

URL: `https://jerdigistatusapi.jerusalem.muni.il/Client/#/login` (it redirects to
`#/statusDigital/login`).

- Identifier: **ID number and/or request number**. Use the **request number** so the
  agent never types the ID.
- Contact: **mobile and/or email**. Must match the details given on the form.
- `שלחו >` opens a two-step verification prompt: text message, voice call or email.
  **The user picks the method and enters the code.** If the contact details are out of date,
  the portal says to call 02-6296666.
- Logging in may land in a **new tab** (`#/statusDigital/main`). Re-read the tab list
  instead of assuming the original tab moved on.

## What the list shows

Sort by `עדכון סטטוס אחרון` (latest update, the default), `תאריך שליחת טופס` or `אגף ושם טופס`.
Each card has: `אגף` (unit), `שם פניה` (form name), `מספר בקשה`, `תאריך הגשה`,
`סטטוס נוכחי`, optionally `תת סטטוס`, and a dated trail.

Statuses seen:

| Status | Meaning |
|---|---|
| `נשמר כטיוטה` | saved / submitted (the first trail entry) |
| `ממתין לבדיקת האגף` | waiting for the unit to review it. FOI requests sit here at first, unit `מזכיר העיר` |
| `ממתין להשלמת נתונים` | the unit wants more information from you. Act on this, it can expire |
| `הסתיים טיפול` | handling finished. Read the sub-status |
| sub-status `התקבלה תשובה` | "an answer was received". The answer text may **not** be in the portal |
| sub-status `אושר` | approved |
| sub-status `פג תוקף הוחזר לתיקונים` | expired after being returned for corrections (a missed `ממתין להשלמת נתונים`) |

`לצפייה בטופס` opens the stored form, read-only, in a new tab
(`jeronlineforms.jerusalem.muni.il/<form>?sess=…`). It shows `הערות האגף` (department notes:
"לא קיימות הערות אגף" means none) and the submitted fields. Its `הדפס טופס` opens the browser
print dialog. **Avoid that from automation** (a modal can hang the session). Take
screenshots and extract the text instead.

## Report and record

- Report only the requests the user asked about. The list also shows unrelated personal
  entries (tax, residency). Leave them out of reports and files unless asked.
- Record per request: status, sub-status, trail dates, department notes, and the check date.
- For FOI: the clock runs 30 days from receipt (see `references/israel-foi-basics.md`).
  If it is still `ממתין לבדיקת האגף` near day 30, chase by email
  (`Hofesh_meida@jerusalem.muni.il`), quoting the request number.
- `הסתיים טיפול / התקבלה תשובה` with no notes: look for an email or letter. If nothing
  arrived, ask the unit for the answer in writing, quoting the request number.
