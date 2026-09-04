# Sadia Saad Yusuf — Portfolio Build Guide (VS Code + Claude Code)

---

## Your final design decision

- **Layout:** Prototype A — Monolith (bold, brutalist, list-style)
- **Palette:** Slate & Ice (grey background, steel-blue accent)
- **Feel:** Corporate, understated
- **Client names:** None — use neutral sector descriptions
- **Projects:** Image-led cards (16:9 screenshot at top)
- **Hero headline:** Chartered Accountant (not a role target)

---

## Token spec — paste this at the top of every Claude Code prompt

```
Design tokens — use these exactly:

COLOURS
--bg:    #23272d   page background (slate grey)
--p1:    #2b3037   card / panel background
--p2:    #333942   alternate panel / hover
--ink:   #eef1f5   primary text
--mut:   #9aa4b2   secondary text, labels, dates
--acc:   #5b8bb0   primary accent (steel blue)
--acc2:  #8fb4d1   secondary accent (ice blue)
--gh:    #2c3139   ghost text (for big faded heading word)
--line:  #39404a   borders and dividers
--rad:   20px      card border radius

TYPOGRAPHY
Display / headings:  Archivo, sans-serif — weights 800, 900
                     text-transform: uppercase, letter-spacing: -.02em
Body / UI:           Inter, sans-serif — weights 300, 400, 500, 600
Load from Google Fonts with display=swap

LAYOUT
Padding: 0 6vw each side, max-width 1180px centred
Mobile breakpoint: 820px
Section padding: 96px top and bottom

MOTION
Single scroll-reveal: .r class → opacity 0 + translateY 22px
On .vis class: opacity 1, translateY 0, transition 0.6s ease
IntersectionObserver threshold 0.12
No other animation

SECTION HEADING PATTERN
<div class="eyebrow">Label</div>          ← ✳ prefix, --acc2 colour, 0.7rem uppercase
<h2 class="sechead">Word<span class="gh">Ghost</span></h2>
where .gh = color: var(--gh) — the second word appears large and faded

HERO HEADLINE — must use exactly:
Line 1: CHARTERED ACCOUNTANT   (white, Archivo 800)
Line 2: & FINANCIAL             (white, same)
Line 3: DATA ANALYST           (--gh faded, same — this is the ghost word)
```

---

## Phase 0 — Project setup

Create this folder structure in VS Code:

```
portfolio/
  index.html
  assets/
    projects/
      project-1.png    ← Data Warehouse
      project-2.png    ← Retail EDA
      project-3.png    ← DMart DCF
      project-4.png    ← NHS Analysis
      project-5.png    ← Product Attribution
      project-6.png    ← Banking Anomaly
      project-7.png    ← ConnectTel Churn
      project-8.png    ← Customer Loyalty
```

Save your 8 project screenshots with the exact filenames above (16:9 landscape crops work best — a dashboard, chart output, or notebook plot).

---

## Phase 1 — Skeleton prompt

Open Claude Code and paste this exactly:

```
Build a single-file portfolio site: index.html. All CSS in a <style> block, no external CSS files.

DESIGN TOKENS:
[paste the full token spec from above]

SECTIONS in this exact order:
1. Nav — fixed, dark, brand name left, 6 nav links right
2. Hero — full viewport height
3. About — two column: paragraph + chip row left, info card right
4. Expertise — 6 tiles in a 3-column grid (first two tiles use --acc and --acc2 as background)
5. Experience — stacked cards, 4 roles
6. Projects — image-led card grid, 8 cards, 16:9 image slot at top of each
7. Certifications — auto-fill grid, 16 items, alternating left border --acc / --acc2
8. Virtual Internships — 3 cards in a row
9. Contact — centred block with rounded card
10. Footer

All content is placeholder text for now.
Responsive at 820px breakpoint.
Add the .r / .vis scroll reveal system with IntersectionObserver.
Do not use any framework, no React, no Tailwind.
```

---

## Phase 2 — Hero content prompt

```
Replace only the hero section content with this. Do not touch any CSS or other sections.

HERO:
- Top bar: small monogram block "SS" in --acc colour | "Available for Finance & Data roles" pill with --acc2 dot
- H1 line 1: CHARTERED ACCOUNTANT   (color: var(--ink))
- H1 line 2: & FINANCIAL            (color: var(--ink))
- H1 line 3: DATA ANALYST           (color: var(--gh) — the large faded ghost word)
- Subtext: "Chartered Accountant with 7+ years auditing India's largest public-sector banks, metro rail and power & infrastructure organisations — now turning that domain depth into risk analytics with Python, SQL, Power BI and Tableau."
- Two buttons: "View GitHub ↗" (--acc background) | "LinkedIn" (border only)
- Four stat blocks below a top border:
  7+  / Years in audit & assurance
  15+ / Major clients audited
  16  / Certifications earned
  8   / Analytics projects
  Alternate stat numbers between --acc and --acc2 colours.
```

---

## Phase 3 — About content prompt

```
Replace the about section with this real content. No CSS changes.

LEFT COLUMN — two paragraphs:
Para 1: "I'm a Chartered Accountant from ICAI who spent seven years auditing India's most complex organisations. That work gave me an instinct for where financial data lies, misleads, or reveals truth under pressure."
Para 2: "Now I pair that domain depth with real analytical capability — building the models, pipelines and dashboards that finance leaders actually use."
Chip row below: Python | SQL | Power BI | Tableau | Excel / VBA | Ind AS / IFRS | Risk Analytics | Financial Modelling

RIGHT COLUMN — info card with 4 rows:
Qualification  |  CA · M.Com · B.Com (Hons)
Location       |  New Delhi, India
Focus          |  Risk · BI · Transformation
Email          |  sadiayusuf23@gmail.com
```

---

## Phase 4 — Experience content prompt

```
Replace the experience section. Four cards, stacked. No client names — use sector descriptions only.

Card 1:
Company:  KPMR & Associates
Role:     Auditor — Engagement Lead
Dates:    Nov 2019 – Present  |  6+ yrs
Sector:   BFSI · Infrastructure · 15+ clients
Bullets:
- Led statutory & internal audits for 15+ clients across banking, infrastructure and manufacturing.
- Automated reconciliation and anomaly detection in Python & SQL, moving testing to full-population coverage.
- Built KPI dashboards used by finance leadership and audit committees.
- Identified process gaps improving operational efficiency by 25% and reducing compliance risk.

Card 2:
Company:  Independent Practice
Role:     Chartered Accountant
Dates:    Jun 2018 – Nov 2019  |  1.5 yrs
Sector:   ICAI Certificate of Practice
Bullets:
- Ran an independent CA practice across audit, tax and finance-process engagements for owner-managed businesses.
- Led post-GST reconciliations (GSTR-1 / 3B) and built repeatable monthly routines clients used independently.

Card 3:
Company:  Thakur Vaidyanath Aiyar & Co.
Role:     Senior Articled Assistant
Dates:    Feb 2013 – Jul 2015  |  2.5 yrs
Sector:   Power · Infrastructure · Financial services
Bullets:
- Executed statutory, internal, tax and stock audits across power, infrastructure and finance clients.
- Prepared audit reports and financial-statement analyses for organisations with multi-crore asset bases.

Card 4:
Company:  A.K. Khattar & Associates
Role:     Articled Assistant
Dates:    Feb 2012 – Feb 2013  |  1 yr
Sector:   Foundational articleship
Bullets:
- Built foundations in audit methodology, reconciliations and workpapers.
```

---

## Phase 5 — Projects content prompt

```
Replace the projects section. 8 image-led cards in a responsive grid (auto-fill, minmax 340px).

Each card structure:
  <a class="pc" href="GITHUB_URL">
    <div class="pimg">
      <span class="ph">01</span>   ← placeholder number, shown when image missing
      <img src="assets/projects/project-1.png" alt="..." loading="lazy" onerror="this.remove()">
    </div>
    <div class="pbody">
      [tags] [title] [description] [View on GitHub ↗]
    </div>
  </a>

The onerror="this.remove()" ensures missing images fail gracefully (gradient tile shows instead).

8 projects:

1. Modern Data Warehouse Build | SQL · PL/pgSQL · ETL
   "Star-schema warehouse built from scratch with ETL pipelines and stored procedures for financial reporting."
   https://github.com/sadia-yusuf/SOL--DataWarehouse-project

2. Multi-Country Retail EDA | SQL · Tableau · RFM
   "RFM segmentation, channel evaluation and high-value product analysis with interactive Tableau dashboards."
   https://github.com/sadia-yusuf/Exploratory-Data-analysis-using-SQL-and-Tableau

3. DMart — DCF Valuation | Excel · DCF · Modelling
   "Full DCF and comparable-company valuation of Avenue Supermarts with forecasting and sensitivity scenarios."
   https://github.com/sadia-yusuf/Financial-Modelling_DCF-Valuation

4. NHS Diagnostic Analysis | Python · Pandas · Healthcare
   "Diagnostic analysis of NHS appointment data: capacity, waiting-time and operational-efficiency trends."
   https://github.com/sadia-yusuf/NHS-Diagnostic-Analysis-Healthcare-Capacity-Appointment-Analysis

5. Product Attribution System | Python · Classification
   "Confidence-scored engine mapping raw product data to client-defined taxonomies."
   https://github.com/sadia-yusuf/Product_Attribution

6. Banking Transaction Anomaly Detection | Python · Anomaly · Risk
   "Dual-method (Z-score + IQR) anomaly and risk-signal detection over banking transaction data."
   https://github.com/sadia-yusuf/-Banking-Transaction-Analysis

7. ConnectTel Churn Prediction | Python · scikit-learn · ML
   "Soft-voting ensemble with a cost-optimised threshold; ROC-AUC 0.841 and ~£23k projected saving per cycle."
   https://github.com/sadia-yusuf/connecttel-churn-model

8. Customer Loyalty Analytics | Python · R · NLP
   "K-Means segmentation, regression and NLP sentiment; tree models to R² 0.94 for CRM deployment."
   https://github.com/sadia-yusuf/Customer-loyalty-analytics-segmentation-drivers-and-predictive-modelling
```

---

## Phase 6 — Certifications + Internships content prompt

```
Replace the credentials sections. No CSS changes.

CERTIFICATIONS (16 items, alternating left border accent colour):
1.  Chartered Accountant (CA)                          — ICAI · 2017
2.  Tableau & Power BI Specialist                      — Grant Thornton
3.  Advanced Excel & VBA                               — Grant Thornton
4.  Financial Modelling & Valuation                    — Grant Thornton
5.  Google Data Analytics                              — Coursera / Google
6.  Investment Banking & Financial Analytics           — Boston Institute of Analytics
7.  Power Query & Power Pivot Mastery                  — Udemy
8.  Statistical Analysis & Data Visualization          — Udemy
9.  Excel Skills for Data Analytics                    — Macquarie University
10. Gen AI for Managers                                — TimesPro
11. Business Analytics for Executives                  — LSE Online
12. Applying Python for Data Analysis                  — IBM
13. GenAI for Data Science Teams                       — IBM
14. Data Visualization & Dashboards (Cognos)           — IBM
15. Introduction to Data Analytics                     — IBM
16. Python for Data Science, AI & Development          — IBM

VIRTUAL INTERNSHIPS (3 cards):
1. Data Visualisation: Empowering Business with Effective Insights — Tata · Forage
2. Controllers Job Simulation                                       — Goldman Sachs · Forage
3. Data Analytics Job Simulation                                    — Deloitte Australia · Forage
```

---

## Phase 7 — Contact + final links prompt

```
Replace the contact section and footer with this real data. No CSS changes.

Contact heading: "Let's build something that counts."
"counts." should be in --acc2 colour.

Three buttons:
  Email me ↗  →  href="mailto:sadiayusuf23@gmail.com"  (--acc background)
  LinkedIn    →  href="https://www.linkedin.com/in/sadia-yusuf1208/"  (border only)
  GitHub      →  href="https://github.com/sadia-yusuf"  (border only)

Footer left:  © 2026 Sadia Saad Yusuf — CA · Financial Data Analyst
Footer right: New Delhi, India
```

---

## Phase 8 — Final audit prompt

```
Do a final review of index.html. Check and fix all of the following:

□ Hero headline reads: CHARTERED ACCOUNTANT / & FINANCIAL / DATA ANALYST
□ No client names anywhere: SBI, BSES, Delhi Metro, DMICDC, IFCI must not appear
□ All 8 project image slots point to assets/projects/project-N.png
□ onerror="this.remove()" on every project <img> tag
□ All external links have target="_blank" rel="noopener noreferrer"
□ LinkedIn URL is https://www.linkedin.com/in/sadia-yusuf1208/
□ No inline colours overriding the CSS variables
□ One h1 on the page, h2 for each section heading
□ Mobile layout works at 820px with no horizontal scroll
□ Google Fonts link uses display=swap
□ Footer year is 2026

Report what you fixed and flag anything you could not verify.
```

---

## Phase 9 — Deploy to GitHub Pages

```
Push this site to GitHub Pages at sadia-yusuf.github.io.

I have a folder called portfolio/ containing index.html and an assets/ subfolder.
I am on Windows using VS Code's integrated terminal.

Walk me through the exact commands to:
1. Navigate into the portfolio folder
2. Initialise git if needed
3. Add and commit index.html and the assets/ folder
4. Push to the main branch of the existing repo sadia-yusuf/sadia-yusuf.github.io
   (replace the current index.html — do not create a subfolder)
```

---

## Quick reference — prompt formula

Use this structure for every prompt you write:

```
CONTEXT:    [which section or file]
TASK:       [exactly what to change]
CONSTRAINT: [what must NOT change]
REFERENCE:  [paste screenshot if visual]
FORMAT:     [full file / CSS only / diff]
```

---

## Troubleshooting cheat-sheet

| Problem | Prompt to use |
|---|---|
| Wrong headline in hero | "Change the h1 in the hero to: CHARTERED ACCOUNTANT / & FINANCIAL / DATA ANALYST. Do not touch any other section." |
| Client name crept in | "Search the entire file for: SBI, BSES, Delhi Metro, DMICDC, IFCI. Remove every occurrence and replace with neutral sector language." |
| Project image not showing | "Check the img src path in project card N. It should be assets/projects/project-N.png with onerror=this.remove()" |
| Mobile layout broken | "Show me only the @media block and fix the horizontal overflow at 820px. Do not touch desktop styles." |
| Colours look off | "The card background reads too dark. Change only --p1 to [hex]. Do not touch other variables." |
| Git push error | "I got this error on Windows: [paste error]. Walk me through fixing it." |
