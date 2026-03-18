# Close.com Solutions Partner Certification

An interactive 10-module training and certification tool for Close.com Solutions Partners — with progress tracking, quiz assessments, and a live admin dashboard.

---

## What's Included

| File | Purpose |
|------|---------|
| `index.html` | Partner-facing training portal |
| `admin.html` | Admin dashboard (your view) |
| `README.md` | Setup instructions |

---

## Setup (15 minutes)

### Step 1 — Create a Firebase Project

1. Go to [https://console.firebase.google.com](https://console.firebase.google.com)
2. Click **Add project** → name it `close-partner-cert` → Continue
3. Disable Google Analytics (optional) → **Create project**

### Step 2 — Enable Firestore

1. In the Firebase Console, go to **Build → Firestore Database**
2. Click **Create database**
3. Choose **Start in test mode** → select your region → **Enable**

### Step 3 — Get Your Web Config

1. Go to **Project Settings** (gear icon) → **General** tab
2. Scroll to **Your apps** → click **</>** (Web app)
3. Register the app (name: `partner-cert`) → copy the `firebaseConfig` object

### Step 4 — Add Config to Both HTML Files

Replace the placeholder in **both** `index.html` and `admin.html`:

```javascript
const FIREBASE_CONFIG = {
  apiKey: "YOUR_API_KEY",              // ← replace
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

### Step 5 — Set Firestore Security Rules

In Firebase Console → **Firestore Database → Rules**, replace with:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /partners/{partnerId} {
      allow read, write: if true;
    }
  }
}
```

Click **Publish**.

### Step 6 — Publish to GitHub Pages

```bash
cd training
git init
git add .
git commit -m "Initial commit: Close Partner Certification"
```

Then on GitHub:
1. Create a new **public** repository (e.g. `close-partner-cert`)
2. Push your code:

```bash
git remote add origin https://github.com/YOUR_USERNAME/close-partner-cert.git
git branch -M main
git push -u origin main
```

3. Go to **Settings → Pages → Source: Deploy from branch (main)**
4. Your site will be live at: `https://YOUR_USERNAME.github.io/close-partner-cert/training/`

---

## Sharing with Partners

Send partners the training URL:
```
https://YOUR_USERNAME.github.io/close-partner-cert/training/index.html
```

---

## Admin Dashboard

Access your dashboard at:
```
https://YOUR_USERNAME.github.io/close-partner-cert/training/admin.html
```

**Default admin password:** `close2026admin`

To change it, update this line in `admin.html`:
```javascript
const ADMIN_PASSWORD = "close2026admin";
```

### Dashboard Features
- **Live partner scores** — all 10 module scores per partner
- **Sort** by name, email, score, completion, status, last active
- **Filter** by Certified / In Progress / Not Started
- **Search** by name or email
- **Partner detail modal** — full score breakdown
- **Export CSV** — full data export

---

## Curriculum: 10 Modules

| # | Module | Theme |
|---|--------|-------|
| 01 | Brand Overview | Who Close is and why partners win |
| 02 | Product Knowledge L1 | What Close does. How it works. |
| 03 | GTM Preparedness | Messaging that converts |
| 04 | Product Knowledge L2 | Customization, API & integrations |
| 05 | ICP & Sales Readiness | Who to sell to. How to qualify. |
| 06 | Product Demonstrations | Demos that open with pain |
| 07 | Product Knowledge L3 | Chloe AI & advanced builds |
| 08 | Client Success Delivery | Implementation & first 90 days |
| 09 | Client Retention & Expansion | Renewals, upsell, expansion |
| 10 | Scalable Business Building | Build a repeatable practice |

### Assessment Rules
- **5 questions** per module (50 total)
- **80% required** (4/5) to pass and unlock next module
- Modules are **sequential** — must complete in order
- Partners can **retake** any failed module quiz
- **Best score** is recorded

---

## Changing the Admin Password

In `admin.html`, find:
```javascript
const ADMIN_PASSWORD = "close2026admin";
```
Change `close2026admin` to your preferred password and redeploy.

---

*Prepared by Barrett King, Head of Partnerships | 2026*
