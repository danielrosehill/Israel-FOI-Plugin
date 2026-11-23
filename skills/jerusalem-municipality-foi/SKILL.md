---
name: jerusalem-municipality-foi
description: File a Freedom of Information request (בקשת חופש מידע) with the Jerusalem Municipality - building/permit files, planning committee, noise and nuisance enforcement, complaints, inspections. Drafts the Hebrew request, drives the city's online form, records the request number and deadline. Use on "FOI to Jerusalem municipality", "hofesh hameida iriyat yerushalayim", "request the permit file / acoustic opinion / complaints from the city".
---

# Jerusalem Municipality FOI request

Walked through live and filed on 2026-11-23 (request no. REDACTED). Read
`references/israel-foi-basics.md` (plugin root) first: it covers which authority
holds what, the s.20 direct-inspection caveat, fees and the deadline.

## Authority and contacts (checked 2026-11-23)

| | |
|---|---|
| Unit | חופש המידע, עיריית ירושלים |
| Officer | חזי מלכא, מנהל ליישום חוק חופש המידע |
| Email | `Hofesh_meida@jerusalem.muni.il` |
| Phone | 02-6296685 (in-person hours: Sun 10-12, Mon 12-14, Thu 10-12) |
| Address | כיכר ספרא, בניין 1, קומה 5 |
| Info page | https://www.jerusalem.muni.il/he/city/freedomofinformation/ |
| Online form | https://jeronlineforms.jerusalem.muni.il/FreedomInfo |
| Form tech support | 02-6296666, Sun-Thu 08:30-16:00 |

This one unit also covers the local planning and building committee
(הוועדה המקומית לתכנון ובנייה ירושלים) and the licensing authority. They sit
inside the municipality, and no separate FOI officer was found for them. Name
them in the request as holders of the building file. The city's environment page
(`/he/residents/clean-city/environment/freedom-information/`) is a library of
published reports, including noise measurements for 2022-2025, **not** a separate
filing route. Check it first: the document may already be published.

## Before filing

0. Check what is already public: `israel-osint:jerusalem-building-file-lookup` lists permit sub-files, renewals, violation files and applicants for a gush/helka (metadata only). Ask for the specific sub-files it shows, e.g. a `חידוש היתר` renewal.
1. Pin down identifiers: building file no. (תיק בניין), permit no. + issue date,
   gush/helka, address. A city building file can usually be found on the municipality's planning
   site by address or gush/helka.
2. Draft the full request (see the basics reference for structure). Produce:
   - a **PDF of the full request** (letterhead, addressed to the officer, numbered items);
   - a **summary ≤ 400 characters** for the form;
   - a **subject ≤ 50 characters**, Hebrew only (see limits below).
3. Also plan a **direct inspection** of the building file (s.20 risk).

## The form (3 steps, Angular/PrimeNG)

**Step 1, פרטי הפונה**: first/last name, ID type (ת.ז. / דרכון) and number, mobile
(required, prefix dropdown + 7 digits), landline (optional, prefix + 7 digits),
email (required), city / street (searchable dropdowns: open, type, click), house
number, postcode. Then `המשך`.

- **Two-factor check before step 2**: code by SMS, email or voice. The **user**
  picks the method and enters the code.
- The ID number is a government identifier: **the user types it**, not the agent.

**Step 2, סוג המידע**:
- `סוג המידע המבוקש`: `מידע המבוקש על ידי גורם פרטי` (or ארגון / עמותה / סטודנט).
- `המידע מבוקש`: `אודותי` / `אחר` (information about someone else, or general).
- `מקבל קצבה`: כן / לא (benefit recipients may be fee-exempt).
- `סוג הבקשה`: `כללי` (the other option is traffic-camera footage).
- `נושא הבקשה`: **max 50 chars, Hebrew letters and only `" / () ' . , _ -`,
  so no digits** (e.g. `רעש מעבודות חפירה ושבירת סלע - <שם האתר>`).
- `פרטי הבקשה`: **max 400 chars. Latin text (e.g. an email address) and the em
  dash `—` are rejected** ("שפת קלט לא תקינה"). Digits, `/`, `(`, `)`, `"`, `.` and `-` are fine.
  Put the summary here, ending "הפירוט המלא במסמך המצורף."
- Text set from JavaScript (native value setter + input/change/blur events)
  validates fine. Use real keystrokes if a field doesn't take it.

**Step 3, צרופות and consents**:
- `צילום תעודה מזהה`: ID copy (bmp/gif/png/jpg/pdf). Not marked as required.
  **The user attaches it** (government ID document).
- `צילום תעודת זהות של האדם אותו הנך מייצג/ת…`: only if filing for someone else.
- `מסמכים נוספים`: attach the full-request PDF. Claude in Chrome's `file_upload`
  **works on this form** (unlike Israel Post's uploader). Uploaded files get
  renamed `<requestNo>_otherAttach_<timestamp>.pdf`, and that prefix is the
  request number before you submit.
- Checkbox: fee commitment "עד לסכום שלא יעלה על 178 ₪ (כולל אגרת בקשה)", required.
- Checkbox: privacy policy, required.
- Checkbox: marketing/messages consent, optional. Leave unticked unless asked.
- The required checkboxes and `שלח` are the user's: they commit money and accept terms.
- A confirm dialog warns the form is locked once sent ("הטופס ינעל לשינויים").
  Before the user confirms, read back every field, both attachments and the ticked boxes.

## After filing

- Confirmation: "הבקשה נשלחה בהצלחה / מספר בקשה: <n>" plus a link to view requests.
- The fee is billed **afterwards**: the unit sends a payment notice by email or SMS, or a
  bank voucher, or you pay by phone through the city payment centre. The user pays.
- Record: request number, date, the full-request PDF and its sha256, the form
  summary, and the due date (receipt + 30 days). Chase after day 30 by email,
  quoting the request number.
