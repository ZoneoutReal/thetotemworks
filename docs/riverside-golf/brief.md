# Riverside Golf — current-site read + Totem Works managed-site concept

**Audience:** Totem Works leader (Jon)  
**Date read:** 2026-09-21  
**Method:** Public web only. Started at `https://golftheriverside.com` and corroborated. No outreach, no paid spend, no contact with the course.  
**This folder:** concept + research artifacts only. No production site. No product-app code changes.

Labels used below:

- **FACT** — observed on a public page, HTTP header, HTML source, DNS, or a third-party listing.
- **CONCEPT** — Totem Works mockup idea. Not built. Not proposed to the course.

---

## 1. Confirmed public URL

**FACT.** Canonical public site:

- **https://golftheriverside.com/**
- `https://www.golftheriverside.com/` → 301 to the apex (`X-Redirect-By: WordPress`).
- `http://` → 301 to `https://golftheriverside.com/`.

Verified as **Riverside Golf Club / Riverside Golf, Cambridge Springs, PA**:

| Signal | Value | Source |
|---|---|---|
| Title / brand | “Riverside Golf Club”, “Riverside Golf”, Est. 1915 | Homepage title + hero |
| Address | 24527 US-6, Cambridge Springs, PA 16403 | Site footer, Contact, Course Details |
| Phone | (814) 398-4537 | Site footer |
| Email | jeremy@golftheriverside.com | Site footer / contact |
| Course | 18 holes, restaurant, public | Homepage + Course Details |
| Independent listing | Same name, address, phone, 18 holes / 6332 yd / slope 129 / public | [Golf Digest course page](https://www.golfdigest.com/courses/pa/riverside-golf-club-riverside) |
| Booking listing | Chronogolf club page points back to golftheriverside.com + same phone | [chronogolf.com/club/riverside-golf-course-pennsylvania](https://www.chronogolf.com/club/riverside-golf-course-pennsylvania) |

**FACT (minor discrepancy).** Chronogolf lists street as “24537 Highway 6 & 19”. The course’s own site and Golf Digest use **24527**. Treat 24527 as the site-of-record address.

**FACT.** Restaurant is a **separate** public site: [dinetherambler.com](https://dinetherambler.com) (“The Rambler at The Riverside”), same street address and `jeremy@golftheriverside.com`.

---

## 2. Quick read of the current site

### 2.1 Information architecture (FACT)

Nav and sitemap (Yoast `page-sitemap.xml` + `wp-json/wp/v2/pages`) expose this public tree:

| Area | URLs | Notes |
|---|---|---|
| Home | `/` | Last modified 2025-02-04 |
| Golf | `/rates/`, `/rates/#gamepass`, `/course-details/`, `/live-cam/`, `/game-passes/` | Game Passes also exist as a standalone page |
| Leagues | `/monday-night-ryder-cup-league/`, `/monday-morning-senior-mens-league/`, `/tuesday-night-womens-league/`, `/wednesday-night-spa-men/`, `/thursday-night-womens-league/`, `/thursday-night-mens-league/`, `/friday-night-couples-league/` | One page per weekday product |
| Memberships | `/membership-types/` | 2026 full + weekday + cart |
| Stay | `/stay/` | Off-site Airbnb / hotel blurbs, not on-course lodging |
| Restaurant | outbound to `https://dinetherambler.com/` | Separate brand/site |
| Events | `/host-an-event/`, `/golf-outings/`, `/events/` | Host + outings are near-duplicates; `/events/` is The Events Calendar |
| Commerce | `/store/`, gift cards → SecureTree | Lightspeed eCom script on Store |
| Tournaments | outbound PerfectVenue | Kelly Ballroom |
| Contact | `/contact-us/` | Address / email / phone + CF7 |
| Leftovers | `/sample-page/`, `/home0old/` | Both 200 OK and in the public sitemap |

Homepage modules, top to bottom: Welcome / Riverside Golf (Est. 1915) → Play Golf → cards (Course, Events, Contact) → Become a Member → league weekday list → Come Visit The Rambler → footer (map, phone, email, Facebook, “Website by Lightspeed”).

### 2.2 Content snapshot (FACT)

**Course.** Public 18-hole parkland track, par 71 (women 72 on Chronogolf), five par 3s / four par 5s / nine par 4s. History page: Herbert Lagerblade (Donald Ross assistant) for William Baird / Riverside Hotel, 9 holes 1915, 18 holes 1923; “first public course in Northwest PA” with 18 holes; purchased spring 2021; superintendent named (Michael Bochert); FINN cycle rentals; scorecard image on Course Details.

**2026 walk-up rates** (Rates page, “subject to change”):

| | 9 walk | 9 ride | 18 walk | 18 ride |
|---|---|---|---|---|
| Weekday | $16 | $25 | $21 | $35 |
| Senior week | $15 | $21 | $17 | $28 |
| Weekend / holiday | $21 | $31 | $29 | $44 |
| Finn week | — | $32 | — | $42 |
| Finn weekend | — | $42 | — | $52 |

**2026 memberships** (Membership Types; after 1/31/2026 column on Rates): Full single $825 / couple $1125 / senior $800 / senior couple $1100; weekday single $675 / couple $975 / senior $650 / senior couple $950; cart $500 / couple cart $650.

**Game Passes** (standalone page): 5-round weekday regular **$144** tax-in; 5-round weekday senior **$121.50** tax-in. Page still titles a rates block “**2025** Riverside Golf Rates” — stale vs the 2026 Rates page.

**Leagues (homepage list).** Mon Ryder Cup 2-man; Tue Women’s; Wed Spa Men’s; Thu Men’s and Women’s; Fri Couples. Monday Night Ryder Cup page: 2-man teams, rotating formats, tee-off 4:00–5:30 PM.

**Events / venue.** Kelly Ballroom (up to 220), outdoor pavilion, weddings, corporate, tournaments, proms, showers, holidays. Event inquiry: Jeremy, same phone/email. Tournament path goes to PerfectVenue. Large event photo gallery (typo: “Event Gallary”).

**Stay.** Local Airbnb blurbs + Holiday Inn Erie. Not a lodging booking engine.

**Hours.** Golf hours are **not published** on the homepage or Rates page as of this read. Restaurant hours **are** published on dinetherambler.com (late summer–fall 2026: Wed–Thu 11:30–8, Fri–Sat 11:30–9; copy also says Mon/Tue/Wed closed — internally inconsistent on Wednesday).

**Events calendar.** The Events Calendar is installed (`/events/`, `wp-json/tribe/events/v1/`). API `total` was **0** at read time. Yoast also emits `tec_recurring_events-sitemap.xml` (lastmod 2026-09-21).

**Social.** Facebook only in the chrome: [facebook.com/golftheriverside](https://www.facebook.com/golftheriverside). No Instagram link found in homepage nav.

### 2.3 Visual feel (FACT)

Template golf-club brochure, not a custom brand system:

- **Builder look:** Divi full-width left nav, cover background, 3-column gutters, fade dropdowns, secondary nav on (`et_fullwidth_nav et_header_style_left et_cover_background et_pb_gutters3 et_secondary_nav_enabled` on `<body>`).
- **Type:** Playfair Display + Oswald + Montserrat + Merriweather (Divi `et-builder-googlefonts-cached-inline`).
- **Accent:** Divi `accent_color` `#016335` (forest green). Chronogolf widget theme color `#0860ab`. CookieYes chrome `#1863DC` / `#0056A7` — a third blue family.
- **Imagery:** Course/event WebPs under `/wp-content/uploads/sites/163/2024/09/…`, topographic SVG, Rambler logo PNG. Old homepage `/home0old/` still uses **DuPage Golf Chicago** stock WebPs.
- **Chrome:** CookieYes banner (bottom-left), Font Awesome icons, Facebook in the top bar, sticky “Book A Tee Time” Chronogolf control.
- **Tone:** Heritage + renaissance (“Queen of Northwest PA”, Est. 1915) mixed with casual membership copy (“Age is Just a Number… But Discounts Are Real!”). Typos on-page: “Leaugue Information”, “Event Gallary”, “levate your golf tournament”.

Overall: recognizable Lightspeed/Divi golf template. Competent, photo-forward, a bit crowded and dated. Brand color is not held consistently (green vs widget blue vs cookie blue).

### 2.4 Detectable platform / CMS / hosting (FACT)

This is a **Lightspeed Golf** product site: WordPress multisite + Divi + Lightspeed child theme, hosted on **WP Engine**, edged by **Cloudflare**. Domain DNS is **GoDaddy**. Mail is **Google Workspace**.

| Layer | Detection | Evidence |
|---|---|---|
| CMS | WordPress | `Link: <https://golftheriverside.com/wp-json/>; rel="https://api.w.org/"`, `/xmlrpc.php`, `/wp-content/`, `/wp-admin/admin-ajax.php`, `X-Redirect-By: WordPress` |
| Multisite tenant | Site ID **163** on a shared WP | Upload path `/wp-content/uploads/sites/163/…` |
| Page builder / parent theme | **Divi 4.27.9** (Elegant Themes) | `/wp-content/themes/Divi/style-static.min.css?ver=4.27.9`, `wp-theme-Divi`, `et_pb_*` modules, `et_divi_theme` |
| Child theme | **Lightspeed Golf Child v.1.0.0** | `<meta content="Lightspeed Golf Child v.1.0.0" name="generator"/>`, `/wp-content/themes/lightspeed-golf-child/`, `ds-script.js?ver=7.0.5` |
| Vendor credit | Lightspeed Golf websites | Footer: “Website by [Lightspeed](https://www.lightspeedhq.com/golf/website-app/custom-websites/)” |
| Vendor docs match | Lightspeed publicly says golf sites are WordPress + Divi and documents a Chronogolf widget | [Lightspeed custom websites FAQ](https://www.lightspeedhq.com/golf/website-app/custom-websites/); [Lightspeed Golf support: “Adding the Chronogolf widget”](https://golf-support.lightspeedhq.com/hc/en-us/categories/10959643559963-Website-management) |
| Host | **WP Engine** | Response header `x-powered-by: WP Engine`; apex A records `141.193.213.20` + `141.193.213.21` (WP Engine’s published Cloudflare-fronted anycast pair) |
| CDN / WAF | **Cloudflare** | `server: cloudflare`, `cf-ray`, `cf-cache-status`, `__cf_bm` bot cookie, `/cdn-cgi/l/email-protection` on the email address |
| TLS | Cloudflare-issued Google Trust Services | Cert `CN=golftheriverside.com`, issuer `Google Trust Services / WE1` |
| DNS | GoDaddy | `ns05.domaincontrol.com` / `ns06.domaincontrol.com` |
| Mail | Google Workspace | MX `aspmx.l.google.com` (+ alts) |
| SEO | **Yoast SEO 28.5** | HTML comment “optimized with the Yoast SEO plugin v28.5”; `robots.txt` “START YOAST BLOCK”; sitemap XSL `wordpress-seo/css/main-sitemap.xsl`; `sitemap.xml` 301 → `sitemap_index.xml` (`X-Redirect-By: Yoast SEO`) |
| Events | **The Events Calendar + Events Calendar Pro 7.8.3** | Headers `x-tec-api-root: …/wp-json/tribe/events/v1/`; CSS `events-calendar-pro/…?ver=7.8.3`; `/events/?ical=1` |
| Forms | **Contact Form 7 6.1.7** | `contact-form-7/includes/css/styles.css?ver=6.1.7` |
| Cookies | **CookieYes / cookie-law-info 3.5.6** | `_ckyConfig` `_version":"3.5.6"` |
| Popups | **Popup Maker** (inferred) | CookieYes lists `pum-*`; Divi `waypoints_options.context = [".pum-overlay"]` |
| Analytics | GA4 `G-YXZRH3NNPD` | Comment in source: “Google tag (gtag.js) **LS property**” |
| Other WP | Performance Lab 4.2.0; `dms-cta-logger` | `<meta name="generator" content="performance-lab 4.2.0">`; `/wp-content/plugins/dms-cta-logger/` |
| Store | Lightspeed eCom embed | Store page loads `https://app.shopsettings.com/script.js?110807372` |
| Gift cards | SecureTree | `https://riversidegolf.shop.securetree.com/egift-card` |
| Live cam | ipcamlive embed | `<iframe src="https://www.ipcamlive.com/player/player.php?alias=67169698e819b">` (Hole 18) |
| Tournaments | PerfectVenue | `https://app.perfectvenue.com/venues/the-kelly-ballroom-at-riverside-golf/hello` |

**Not observed:** Squarespace, Wix, Webflow, Shopify storefront (gift cards are SecureTree; shop script is Lightspeed eCom), or a custom headless CMS.

### 2.5 Booking widget (FACT) — do not rebuild

Tee times are **Chronogolf**, already wired on the Lightspeed site:

```html
<!-- Start / Chronogolf Widgets -->
<div class="chrono-bookingbutton"></div>
<script>
  window.chronogolfSettings = { "clubId": 18587, "locale": "en-US" };
  window.chronogolfTheme = { "color": "#0860ab" };
</script>
<script src="https://cdn2.chronogolf.com/widgets/v2"></script>
```

Rates page CTA: `<a class="et_pb_button … chrono-bookingbutton-open" href="">Book A Tee Time</a>` plus a jQuery click-forwarder (`.open-widget` → `.chrono-bookingbutton-open`).

Public booking URL (same club):  
https://www.chronogolf.com/club/riverside-golf-course-pennsylvania

A second Chronogolf slug exists (`/club/riverside-golf-club-pennsylvania`) with thinner data. The populated club record is **riverside-golf-course-pennsylvania**, `clubId` **18587**.

**CONCEPT implication:** keep Chronogolf as system of record. A Totem site only needs a staff-editable booking URL (and optional official widget snippet). Do not rebuild tee sheets, payments, or membership checkout.

### 2.6 Quality notes that matter to a rebuild (FACT)

These are public-page facts, not taste:

1. **Leftover template pages indexed** — `/sample-page/` and `/home0old/` (DuPage Golf Chicago images) return 200 and sit in Yoast’s page sitemap.
2. **Duplicate event marketing** — `/golf-outings/` and `/host-an-event/` share the same wedding/corporate/prom copy, including the same typo (“levate”).
3. **Stale / conflicting year labels** — Game Passes still says “2025 Riverside Golf Rates”; Rates/Memberships are 2026.
4. **Events engine empty** — TEC is installed; zero upcoming events in the public API.
5. **Store page is a shell** plus an eCom script; almost no on-page merchandising.
6. **No on-site golf hours.** Visitors cannot see “are we open today” without calling.
7. **Color / chrome drift** — course green, Chronogolf blue, CookieYes blue.
8. **Restaurant hours copy disagrees with itself** on dinetherambler.com (Wednesday listed both open and closed).
9. **Sitemap lives at** `/sitemap_index.xml`. Apex `/sitemap.xml` 301s there via Yoast (`X-Redirect-By: Yoast SEO`) — fine, just non-default.

None of this requires talking to the course. It is the case for a quieter, staff-editable brochure.

---

## 3. Totem Works mockup concept (CONCEPT)

**What this is:** a static brochure site Totem would design, host, and constrain — Sanity for the few fields staff actually change — with Chronogolf remaining the tee-time system.

**What this is not:** a production build, a Lightspeed migration quote, a booking product, or an offer sent to Riverside.

Totem Works today is an Erie, PA indie game studio. This concept is a **managed local-site** line: one course, one clean public surface, Jon owns the hard parts, staff owns the Tuesday-morning edits.

### 3.1 Product shape

| | |
|---|---|
| Public site | Static brochure (Astro / similar). Fast, boring-in-a-good-way, no WP admin. |
| Editing | Sanity. Staff get a small studio: rates, hours, events, announcements, gallery (capped), booking URL. |
| Design | Clean modern parkland. Heritage without the Divi kit. One green, one cream, one stone. No cookie-banner circus on first paint if we can stay off nonessential trackers. |
| Booking | **Link / official Chronogolf widget only.** Club ID 18587 already exists. |
| Ops | Totem owns layout, design system, DNS/hosting/SSL, new page types, embed wiring, spam hardening. |

### 3.2 Ownership split

**Staff-editable in Sanity (within limits)**

| Field | Limit | Why |
|---|---|---|
| Daily / seasonal **hours** | Structured open/close by day + optional seasonal note | Missing on the current golf site |
| **Rates** table | Rows they already publish (9/18, walk/ride, weekday/weekend/senior/Finn) + “subject to change” note | Changes every season |
| **Membership / game-pass** prices | Same tables; no new product types without Totem | Stale 2025 copy proves they edit this |
| **Announcements** | 1 pinned + short body, start/end dates | Frost delay, shotgun, cart-path only |
| **Events** | Title, date, one-liner, optional link (league night, outing, wedding open house) | TEC is overkill and currently empty |
| **Gallery** | Cap (e.g. 12 images, max px/weight). No dump of 30 event WebPs | Current Host page is a photo pile |
| **Booking URL** | Single URL field, default Chronogolf club link | If they ever change tee vendors |
| **Contact** | Phone, email, address, Facebook URL | Already the footer truth |
| **League blurbs** | Short rich text per weekday | They already maintain 7 pages of this |
| **Rambler / Stay links** | URL + one-line tease | Those products live elsewhere |

**Jon / Totem-owned**

- Layout, type, color, components, responsive behavior
- Design system (buttons, tables, announcement bar, gallery grid)
- DNS, hosting, SSL, redirects (`www` → apex, HTTP → HTTPS)
- New **page types** (do not let staff invent `/sample-page/` or a second events URL)
- Chronogolf **embed wiring** (script, clubId, button class, noindex on thank-you if any)
- **Spam hardening** on the one contact form (honeypot + provider captcha + rate limit; no raw CF7)
- Image pipeline (compress, alt, no leftover stock from another course)
- Analytics only if asked; default is none or a privacy-respecting access log
- Not in staff hands: theme, plugins, PHP, menus-as-pages, SEO plugin sprawl

### 3.3 Proposed public IA (narrower than now)

Keep the jobs-to-be-done; drop the leftovers.

1. **Home** (single scroll — see wireframe)
2. **Play** — course story (short), scorecard image, live-cam embed if they still want it
3. **Rates & passes** — one page: daily rates + game passes + membership table
4. **Leagues** — one page, seven compact cards (not seven full URLs)
5. **Events & outings** — announcements + event list + “host a wedding / tournament” with PerfectVenue + email
6. **Visit** — map, hours, contact form, Stay links, Rambler outbound
7. **Legal** — privacy (CookieYes-level GDPR banner is optional if we do not ship GA by default)

Outbound, not rebuilt: Chronogolf, dinetherambler.com, PerfectVenue, SecureTree gift card, ipcamlive, Facebook.

**Do not ship:** `/sample-page/`, `/home0old/`, duplicate host/outings twins, empty `/store/` unless they actually merchandise.

### 3.4 Home, top to bottom (CONCEPT)

Matches `wireframe.html` in this folder.

1. **Announcement bar** — Sanity, hide-when-empty.
2. **Header** — wordmark, thin nav (Play, Rates, Leagues, Events, Visit), persistent **Book a tee time** (outbound Chronogolf).
3. **Hero** — “Riverside Golf · Cambridge Springs · Est. 1915”. One photograph. One sentence. Two actions: Book (Chronogolf) / View rates.
4. **Course facts** — 18 holes · par 71 · walkable · restaurant on site. No paragraph of Scottish golf history on the first screen.
5. **Play this week** — hours + starting rates pulled from Sanity. “Full rate sheet →”.
6. **Announcements / frost** — or a quiet empty state.
7. **Leagues strip** — Mon–Fri labels, link to Leagues.
8. **Rambler** — one photo, one sentence, outbound to dinetherambler.com.
9. **Events / Kelly Ballroom** — two cards (play an outing / host a wedding), not seven identical blurbs.
10. **Gallery** — 6–8 images, capped.
11. **Visit** — address, map link, phone, email, hours.
12. **Footer** — same contact, Facebook, gift-card outbound, “Site by Totem Works” (if/when this existed). No plugin graveyard.

### 3.5 Chronogolf wiring (CONCEPT)

Do not rebuild booking.

- Default CTA href: `https://www.chronogolf.com/club/riverside-golf-course-pennsylvania` (staff-overridable).
- Optional: same official widget they already use (`cdn2.chronogolf.com/widgets/v2`, `clubId: 18587`) as a modal on the Book button. Totem owns the snippet; staff do not paste JS.
- Membership, game-pass, and gift-card **purchase** stay on Chronogolf / SecureTree / Lightspeed eCom until someone asks to replace those. Brochure site explains; vendors transact.

### 3.6 Why this vs the current Lightspeed/WP stack (CONCEPT)

Current site already does the job of “have a website.” The gap is operational, not missing features:

- Staff should change **rates and hours** without a Divi page-builder and a plugin list.
- Totem should own **layout and uptime** so leftover template pages and Chicago stock images cannot ship.
- Booking is a solved vendor problem (Chronogolf). Rebuilding it would be the wrong product.

A managed brochure + Sanity is smaller than Lightspeed’s WordPress/Divi/TEC/eCom bundle — on purpose.

### 3.7 Out of scope (CONCEPT)

- Contacting the course, pitching, or pricing a real engagement
- Replacing Chronogolf, PerfectVenue, SecureTree, or The Rambler’s site
- Reproducing 30-image event galleries or the full Lightspeed shop
- App, POS, tee-sheet, or membership admin
- Production DNS cutover, brand-new photography, or paid ads

---

## Appendix A — request headers / generator crumbs (FACT)

Captured 2026-09-21 from `GET https://golftheriverside.com/`:

```
HTTP/2 200
server: cloudflare
link: <https://golftheriverside.com/wp-json/>; rel="https://api.w.org/"
link: <https://golftheriverside.com/wp-json/wp/v2/pages/55>; rel="alternate"; type="application/json"
server-timing: wp-before-template;dur=…
x-powered-by: WP Engine
x-tec-api-origin: https://golftheriverside.com
x-tec-api-root: https://golftheriverside.com/wp-json/tribe/events/v1/
x-tec-api-version: v1
```

`robots.txt` (Yoast):

```
Crawl-delay: 10
# START YOAST BLOCK
User-agent: *
Disallow:
# END YOAST BLOCK
Sitemap: https://golftheriverside.com/sitemap_index.xml
```

Homepage published 2024-05-01, modified 2025-02-04 (Yoast schema). Lightspeed-era rebuild is consistent with upload dates in `/2024/03/` and `/2024/09/`.

---

## Appendix B — sources

All public. Retrieved 2026-09-21.

- https://golftheriverside.com/ and inner pages listed in §2.1 (HTML source + headers)
- https://golftheriverside.com/robots.txt
- https://golftheriverside.com/sitemap_index.xml + page-sitemap.xml
- https://golftheriverside.com/wp-json/wp/v2/pages
- https://golftheriverside.com/wp-json/tribe/events/v1/events
- https://www.chronogolf.com/club/riverside-golf-course-pennsylvania
- https://www.chronogolf.com/club/riverside-golf-club-pennsylvania
- https://dinetherambler.com/
- https://www.golfdigest.com/courses/pa/riverside-golf-club-riverside
- https://www.lightspeedhq.com/golf/website-app/custom-websites/
- https://golf-support.lightspeedhq.com/hc/en-us/categories/10959643559963-Website-management
- DNS: `dig` NS / A / MX for golftheriverside.com
- TLS: `openssl s_client` leaf cert for golftheriverside.com

Artifact: [wireframe.html](./wireframe.html) — static CONCEPT homepage, not a production site.
