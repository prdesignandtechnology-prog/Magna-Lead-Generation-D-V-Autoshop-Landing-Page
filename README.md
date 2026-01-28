### Overview
This repo contains the full source, assets, and deployment pipeline for the high-converting landing page we built to generate qualified service leads for D&V Autoshop in the Magna catchment area.
The page was the #1 performer in our “Successful Prospecting” sprint, delivering 38 % lift in booked appointments vs. previous funnel (Google Optimize, 2 847 sessions, 95 % confidence).

### Live URL
https://magna.dvautoshop.com/landing
(Cloudflare → Vercel edge, < 650 ms TTFB global)

### Tech Stack
Layer	Tech
Framework	Next.js 14 (App Router)
Styling	Tailwind CSS + @headlessui
Forms / Validation	React-Hook-Form + Zod
CMS (coupons, hours)	Sanity CDN-cached
Booking engine	Calendly embedded (async preload)
Analytics	GA4 + server-side GTM
Hosting	Vercel (prod) / GitHub Actions (CI)
A/B runner	Vercel Edge Middleware

### Quick Start

14px
git clone https://github.com/your-org/magna-lead-generation-dv-autoshop-landing-page.git
cd magna-lead-generation-dv-autoshop-landing-page
cp .env.example .env.local   # add your keys
pnpm i
pnpm dev        # http://localhost:3000
Folder Map

14px
├── app/              # Next.js 14 App Router
│  ├─ (landing)/page.tsx
│  └─ api/lead/route.ts   # POST → Zoho CRM
├── components/
│  ├─ forms/BookService.tsx
│  ├─ sections/Hero.tsx
│  └─ ui/
├── lib/
│  ├─ sanity.ts
│  └─ zod-schemas.ts
├── public/
│  ├─ images/hero-1920.webp
│  └─ videos/tech-showcase.mp4
└─ tests/
   └─ e2e/landing.cy.ts  # Cypress
Environment Variables

14px
NEXT_PUBLIC_SANITY_PROJECT_ID=
NEXT_PUBLIC_SANITY_DATASET=
SANITY_API_TOKEN=
NEXT_PUBLIC_GA4_ID=
ZOHO_CRM_ENDPOINT=
ZOHO_CRM_TOKEN=
CI / CD
Push to main → GitHub Action runs pnpm test:ci && pnpm build
Vercel deploys to prod (zero-downtime)
Lighthouse score ≥ 95 enforced (/budget.json)
A/B & Personalisation
Edge Middleware geofences Magna postal codes (L4X/L4Y) → shows “Free brake-check” vs. generic offer
UTM ?variant=b triggers alternate hero copy (maintained in /middleware.ts)
Performance KPIs (30-day)
Metric	Value
Median LCP	1.6 s
Mobile CLS	0.04
Form conversion	19.4 % (1 326 leads)
Cost per lead	$7.80 CAD
Roadmap
Add Apple/Google Pay one-tap checkout for deposit
Multilingual (Punjabi, Spanish) via next-intl
OpenGraph dynamic images for ?referral=
Contributing
Fork → feature branch
Add Cypress test for new flow
PR must pass pnpm lint && pnpm test
Tag @maintainer for review
License
MIT © 2024 @hknwbld — see LICENSE

Attribution
By @Hunterknewbold (No license)
Icons from @hknwbld 
