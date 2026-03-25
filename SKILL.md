---
name: transnatur-landing
description: Build the Transnatur INC recruitment landing page. Use this skill whenever working on the Transnatur website, landing page, driver recruitment site, lead form, or any page for TRANSNATUR INC. Contains all branding, company data, page structure, and Google Sheets integration instructions.
---

# Transnatur INC — Recruitment Landing Page

## Company Information

```
Company:    TRANSNATUR INC
Address:    16305 S WHEATGRASS ST, LOCKPORT IL 60441
MC#:        1592651
USDOT#:     4149516
President:  Vasilii Iurcu
Phone:      (312) 909-4861
Email:      Transnaturinc@gmail.com
```

---

## Branding Colors

| Role         | Name       | Hex       |
|--------------|------------|-----------|
| Primary      | Navy Blue  | `#0B1F3A` |
| Secondary    | Dark Gray  | `#4A444A` |
| Background   | White      | `#FFFFFF` |
| CTA / Accent | Red        | `#C62828` |

**Usage rules:**
- Navy Blue → headers, navbar, hero background, footer
- Red → ALL call-to-action buttons, highlights, urgency elements
- Dark Gray → body text, secondary text
- White → section backgrounds, text on dark backgrounds

---

## Logo Files

Located at: `/mnt/user-data/uploads/`

| File                          | Use                        |
|-------------------------------|----------------------------|
| `Ttransnatur_logo_white.png`  | Dark backgrounds (navbar, footer, hero) |
| `Ttransnatur_logo_black.png`  | Light backgrounds          |

---

## Image Assets

| File           | Use                    |
|----------------|------------------------|
| `cover_img.png`| Hero section background — sunset truck shot |
| `4.png`        | Fleet/truck section — highway truck photo   |

---

## Site Structure

The project has **2 pages**:

### Page 1: Main Landing Page (`index.html`)

Sections in order:
1. **Hero Section** — Full-width truck image (`cover_img.png`), headline, subheadline, CTA button → links to Lid Form page
2. **Pay & Benefits** — Icons + numbers (CPM rate, home time, bonuses)
3. **Modern Fleet** — Truck photo (`4.png`), fleet description
4. **Why Drive With Us** — 3–4 cards with icons, short text
5. **Driver Requirements** — Checklist (CDL-A, experience, etc.)
6. **Final CTA** — Big red button → links to Lid Form page
7. **Footer** — Logo (white), address, MC#, USDOT#, phone, email

### Page 2: Lid Form Page (`form.html`)

Sections in order:
1. **Header** — Logo + company name (minimal, clean)
2. **Call to Action** — Short motivating text above the form
3. **Lid Form** — Fields listed below
4. **Footer** — Same as main page footer

---

## Lead Form Fields

```
- First Name *
- Last Name *
- Phone Number *
- Email *
- CDL Class (dropdown: CDL-A / CDL-B / No CDL)
- Years of Experience (dropdown: Less than 1 / 1–2 / 3–5 / 5+)
- State (dropdown, all US states)
- Submit Button → "APPLY NOW" (red, full-width)
```

On submit:
- Send data to Google Sheets via Apps Script (see Google Sheets section below)
- Redirect to Thank You page (`thankyou.html`)

---

## Page 3: Thank You Page (`thankyou.html`)

- Simple page: logo, "Thank You!" headline, "We will contact you within 24 hours."
- CTA: "Back to Home" button

---

## Design Rules

### Core Layout
- **Mobile-first** — Most drivers browse on phones. All sections must be fully responsive.
- **Hero:** Full viewport height (`100vh`), dark overlay on truck image, white text
- **Sections:** Alternate between white and light gray (`#F5F5F5`) backgrounds
- **Navbar:** Sticky, navy blue, white logo, "APPLY NOW" red button on right
- **Footer:** Navy blue background, white text
- **Buttons:** Always red (`#C62828`), white text, rounded corners (8px), bold

### Aesthetic Direction — "Industrial American Power"
This is a recruitment page for hardworking CDL drivers. The tone must feel:
**Bold, trustworthy, no-nonsense, American blue-collar**. Not corporate. Not generic.

Before building, commit to this direction: heavy typography, strong contrast, a sense of movement and road. The site must feel like it was designed FOR truck drivers — confident, direct, built to last.

**CRITICAL:** Avoid generic AI aesthetics — no soft gradients, no rounded pastel cards, no generic icon libraries. Every design choice must feel intentional and specific to trucking/logistics culture.

### Typography
- **DO NOT use:** Inter, Roboto, Arial, or system fonts
- **Headings (h1, h2, h3):** `Poppins` ExtraBold — weight **800**
- **Descriptors / subtext:** `Bebas Neue` Regular — weight **400**

Google Fonts import (add to every page `<head>`):
```html
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@800&family=Bebas+Neue&display=swap" rel="stylesheet">
```

CSS usage:
```css
h1, h2, h3 {
  font-family: 'Poppins', sans-serif;
  font-weight: 800;
}

.subtext, .descriptor, .subtitle, .card-label {
  font-family: 'Bebas Neue', sans-serif;
  font-weight: 400;
  letter-spacing: 0.05em;
}
```

### Color & CSS Variables
Define all colors as CSS variables at the top of every stylesheet:
```css
:root {
  --navy:    #0B1F3A;
  --red:     #C62828;
  --gray:    #4A444A;
  --white:   #FFFFFF;
  --light:   #F5F5F5;
  --red-hover: #A31515;
}
```

### Motion & Micro-interactions
- Hero CTA button: subtle pulse animation to draw attention
- Benefit cards: fade-in + slide-up on scroll (use `IntersectionObserver`)
- Navbar: changes background opacity on scroll
- Form inputs: smooth border-color transition on focus (`transition: border-color 0.2s`)
- Staggered reveal on benefit icons (use `animation-delay` increments)

### Backgrounds & Depth
- **Hero:** Full-bleed truck image with dark gradient overlay (`linear-gradient(rgba(11,31,58,0.7), rgba(11,31,58,0.85))`)
- **Benefits section:** Navy background with subtle diagonal stripe texture or light noise overlay
- **Why Drive section:** Deep navy with a faint road/tire tread geometric pattern as background texture
- Avoid flat solid color backgrounds — add depth with subtle gradients or textures

### What Makes This Site UNFORGETTABLE
One thing a driver must remember: **"These guys are serious and pay well."**
- Use large, bold CPM numbers as visual anchors (e.g., `$0.65` in massive text)
- The red CTA button must appear at least 3 times on the page
- The hero headline must be the largest text on the page — no competition

---

## SEO Meta Tags (add to every page)

```html
<meta name="description" content="Drive with Transnatur INC. CDL-A drivers wanted. Competitive pay, modern fleet, home time. Apply now!">
<meta name="keywords" content="CDL-A driver jobs, truck driver hiring, Transnatur INC, flatbed driver, Illinois trucking">
<meta property="og:title" content="Drive With Transnatur INC — Apply Now">
<meta property="og:description" content="Join our team. Competitive pay, modern Peterbilt fleet, great home time.">
```

---

## Analytics (add to every page `<head>`)

```html
<!-- Google Analytics placeholder — replace UA-XXXXXXXX with real ID -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

---

## Google Sheets Integration

### Step 1 — Create Google Sheet

1. Go to [sheets.google.com](https://sheets.google.com)
2. Create new sheet, name it: **Transnatur Leads**
3. Add headers in Row 1:
   ```
   A: Timestamp | B: First Name | C: Last Name | D: Phone | E: Email | F: CDL Class | G: Experience | H: State
   ```

### Step 2 — Create Apps Script

1. In the Sheet: click **Extensions → Apps Script**
2. Delete all existing code
3. Paste this code:

```javascript
function doPost(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var data = JSON.parse(e.postData.contents);
  
  sheet.appendRow([
    new Date(),
    data.firstName,
    data.lastName,
    data.phone,
    data.email,
    data.cdlClass,
    data.experience,
    data.state
  ]);
  
  return ContentService
    .createTextOutput(JSON.stringify({ result: "success" }))
    .setMimeType(ContentService.MimeType.JSON);
}
```

4. Click **Deploy → New Deployment**
5. Type: **Web app**
6. Execute as: **Me**
7. Who has access: **Anyone**
8. Click **Deploy** → Copy the **Web App URL**

### Step 3 — Add URL to Form

In `form.html`, replace `YOUR_APPS_SCRIPT_URL` with the copied URL:

```javascript
const GOOGLE_SHEET_URL = "https://script.google.com/macros/s/YOUR_APPS_SCRIPT_URL/exec";

async function submitForm(formData) {
  try {
    await fetch(GOOGLE_SHEET_URL, {
      method: "POST",
      mode: "no-cors",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(formData)
    });
    window.location.href = "thankyou.html";
  } catch (error) {
    console.error("Submit error:", error);
    alert("Error submitting form. Please call us: (312) 909-4861");
  }
}
```

---

## Content Copy — Key Sections

### Hero Section
```
Headline:    JOIN THE TRANSNATUR TEAM
Subheadline: CDL-A Drivers Wanted — Competitive Pay · Modern Fleet · Home Time
CTA Button:  APPLY NOW →
```

### Pay & Benefits
```
💰 Up to $0.65 CPM
🏠 Home Weekly
🚛 2022–2024 Peterbilt Fleet
🏥 Health Insurance Available
💵 Direct Deposit Weekly
📦 Flatbed & Dry Van Loads
✈️ Relocation Support (flight covered)
```

### Why Drive With Us
```
✅ Family-Owned Company — You're not a number
✅ Consistent Freight — No forced dispatch
✅ 24/7 Dispatch Support
✅ Clean DOT Record Required
```

### Driver Requirements
```
✔ Valid CDL-A License
✔ Minimum 1 Year OTR Experience
✔ Clean MVR (no DUI/DWI)
✔ Must pass DOT Physical
✔ Flatbed experience preferred (not required)
✔ US Work Authorization
```

### Final CTA
```
Headline:  Ready to Drive With the Best?
Subtext:   Join Transnatur INC today. We respond within 24 hours.
Button:    APPLY NOW — IT'S FREE
```

---

## File Structure to Create

```
transnatur-landing/
├── video-hero.html     ← Entry point — video background + path selector
├── index.html          ← Main landing page (drivers)
├── form.html           ← Lead form page
├── thankyou.html       ← Thank you page
├── assets/
│   ├── logo-white.png  ← Copy from uploads
│   ├── logo-black.png  ← Copy from uploads
│   ├── hero-bg.png     ← cover_img.png
│   ├── truck.png       ← 4.png
│   └── vide_truck.mp4  ← Video for hero background
└── README.md           ← Setup instructions
```

> **Video Hero Page** — see `VIDEO-HERO-PAGE.md` for full instructions.

---

## How to Start in Claude Code

Paste this prompt to Claude Code:

> "Read /path/to/SKILL.md and build the full Transnatur INC recruitment landing page exactly as described. Start with index.html, then form.html, then thankyou.html. Use all branding colors, images from assets/, and include Google Sheets form submission."
