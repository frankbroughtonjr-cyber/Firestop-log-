# KIM Industries — Firestop Log App Roadmap
## Job #5063 · UPMC Presbyterian · Pittsburgh PA

---

## ✅ BUILT & LIVE
- Firebase-backed daily penetration log
- 10 installer slots with personal log views
- 10 item types with color coding (SNS/LCI)
- Fire animation selector screen
- Daily Summary with job totals
- Excel export — 4 sheets (Daily Summary, Job Totals, Full Detail, Job Progress w/ live history)
- Week strip + date navigation
- History sidebar (all past dates)
- USA theme header (KIM logo, gold/navy/crimson)
- Offline banner + sync status
- Mobile responsive

---

## 🧪 PROTOTYPE BUILT (not yet in main app)
- Crew Calendar — month view, color-coded days off
- Day Off Requests — submit, approve, deny
- Days Missed tracker — two sources:
  - Auto-detected: weekdays with no log data
  - Superintendent-logged: NCNS / Call Off
- Expandable installer rows with incident history

---

## 🗺 FULL VISION — Future Phases

### PHASE 1 — Bare Minimum (START HERE)
- [ ] Firebase Auth — email/password login
- [ ] Role system: Superintendent vs Installer
  - Superintendent: sees everything, can approve/deny, log incidents
  - Installer: sees only their own log + calendar + days missed
- [ ] Basic installer profile (name, phone, role)
- [ ] Lock installer view to logged-in user (no more dropdown picker)

### PHASE 2 — Crew Management
- [ ] Crew Calendar integrated into main app
- [ ] Day Off Request system (live in Firebase)
- [ ] Days Missed tracker (live in Firebase)
- [ ] Superintendent dashboard — pending requests badge

### PHASE 3 — Certifications & Profiles
- [ ] Installer profile page:
  - Full name, phone, hire date
  - Cert type (SNS, LCI, other)
  - Cert number
  - Issued date / expiry date
- [ ] Auto-flag certs expiring within 30 / 60 days
- [ ] Superintendent cert overview — who's current, who's lapsing

### PHASE 4 — Crew Help & Reference
- [ ] Help page with useful links:
  - Spec-Seal / LCI product pages
  - Installation guides
  - Safety data sheets
- [ ] Embedded training videos (YouTube)
- [ ] Interactive cheat sheets (SNS + LCI quick reference)
  - Product, application, coverage rates
  - Common annular space limits

### PHASE 5 — UL System Reference
- [ ] Curated searchable database of UL-listed assemblies used on this job
  - Based on Firestop Search (firestopsearch.com)
  - Filter by: wall type, floor/ceiling type, pipe size, rating
  - Show: UL system number, required products, installation notes
- [ ] Link systems to log entries (optional future feature)
- [ ] Tested & listed systems library — job-specific

---

## 💡 OTHER IDEAS CAPTURED
- Foreman sign-off at end of day (lock entries)
- Superintendent sign-off mode
- Photo reference per log entry
- Deficiency counter / punch list
- EJ (expansion joint) flag per row
- UL system number field per entry
- Assembly type + fire rating per entry
- Pass/Fail status per penetration
- Installer cert tracker on profile
- Push notifications for pending requests (service worker)
- Overtime tracker — flag 40+ hrs

---

## TECH STACK
- Single HTML file hosted on GitHub Pages
- Firebase Realtime Database (open rules — tighten for auth)
- Firebase Auth (to be added in Phase 1)
- SheetJS for Excel export
- Vanilla JS + CSS (no framework)
- Google Fonts: Oswald, Source Sans 3, Source Code Pro

**Live URL:** https://frankbroughtonjr-cyber.github.io/Firestop-log-/
**GitHub Repo:** frankbroughtonjr-cyber/Firestop-log-
**Firebase DB:** https://firestop-log-default-rtdb.firebaseio.com

---

*Last updated: March 2026*
---

## 🏠 HOME SCREEN — Designed & Saved (ready to build)

Full home screen was built and tested. Reverted until auth is ready.
Wire it in during Phase 1 after login is working.

### What was built:
- Loads as the first screen (fire still burns behind it)
- Live clock — ticking seconds, day/date/month/year
- Job badge — Job #5063 · UPMC Presbyterian · Pittsburgh PA
- **3 live stat tiles** (pull from Firebase on load):
  - Total penetrations logged today
  - Active installers today
  - Total log entries today
- **4 navigation tiles:**
  - 🔥 Enter My Log → installer selector
  - 📊 Daily Summary → goes straight to summary
  - 📅 Crew Calendar → locked (Phase 2)
  - 📋 UL System Reference → locked (Phase 5)
- "← Back to Home" button added to selector screen
- Back from Daily Summary → returns to Home (not selector)

### Flow when home screen is active:
  App open → Home
  Home → "Enter My Log" → Selector → Installer log
  Home → "Daily Summary" → Summary
  Installer log → "Change Installer" → Selector
  Selector → "← Back" → Home
  Summary → "← Back" → Home

### CSS classes built (save for Phase 1):
  .home-screen, .home-date-bar, .home-day, .home-dow
  .home-month, .home-clock, .home-stats, .home-stat
  .home-stat-val, .home-stat-label, .home-tiles, .home-tile
  .home-tile-icon, .home-tile-body, .home-tile-title
  .home-tile-sub, .home-tile-arrow, .home-job-badge

### JS functions built (save for Phase 1):
  showHomeScreen() — shows home, starts fire, loads stats, starts clock
  updateHomeDateClock() — updates date/time every second
  loadHomeStats() — Firebase fetch for today's totals
  goToSelector() — home → selector nav
  returnToHome() — selector → home back button
