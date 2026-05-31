# CONTEXT: Wedding Site — index.html
# Read WEDDING-SKILL.md first. All design decisions must follow that skill.

---

## TASK
Build a complete single-page wedding website as `index.html` using HTML, CSS, and vanilla JavaScript only.
No frameworks. No build tools. No external JS libraries.
All CSS and JS embedded in the single file.

---

## COUPLE
- Names: **Daniel & Kukua** (full: Daniel Dadzie & Belfrieda Kukua Asamoah)
- Church: First Love City Church — Accra platform, East Legon
- Daniel is currently at the Thika, Kenya campus
- After the wedding they are moving to Nairobi

## DESIGN OVERRIDES (from WEDDING-SKILL.md)
- Accent color: `#B5A882` (champagne gold — suits "All things bright & beautiful")
- Image situation: **light on images** — use image-light strategies from the skill
- Hero background: solid `var(--color-bg)`, no gradient
- Oversized background initials `D & K` at ~15vw opacity 0.05 behind hero text

---

## REPO STRUCTURE NOTE
This file lives at the repo root. A second file `upload.html` (built separately) handles guest photo uploads and lives at the same level. The QR code on this site points to `/upload`.

---

## SECTIONS — build in this order

### 1. NAV
- Brand: `D & K`
- Links: `our story` · `schedule` · `tidbits` · `gifts` · `faq`
- Right side: `Share your photos` as a small outlined link → href="/upload"
- Sticky, hide on scroll down, show on scroll up
- Mobile: hamburger menu, full-screen overlay nav

### 2. HERO
- Eyebrow label: `"you are invited to celebrate"`
- Names: `Daniel & Kukua`
- Date: `june 4, 2026`
- Scripture below date (italic Cormorant, muted, ~1.1rem):
  > "He hath made every thing beautiful in his time." — Ecclesiastes 3:11
- Scroll cue: `"scroll to explore"` + animated thin line

### 3. OUR STORY (id="story")
- Eyebrow: `"thank god for meetings after church"`
- Single narrative — no chapters. Render the full story text below as one flowing section.
- Story text (use verbatim):

  "We're both in First Love City Church. Well… Daniel is in Thika campus (Kenya) now,
  but he still keeps tabs on the Accra platform, so make of that what you will.

  We started noticing each other because Bel was pretty loud and had plenty to say in
  meetings (Pastor C must be tired of her by now), and I was never really quiet either.
  Somehow that became the beginning of us actually talking.

  After a few months, I called her. Wanted to take her out, but she was sick, so instead
  we had a phone conversation.

  That call was the first proper step. From there, things grew naturally. Just two people
  who already knew each other a little, getting to know each other properly.

  And now, by the grace of God, here we are. I got the nice girl. She inherited my
  mother's project. Pray for us!"

- After the story text, render this as a large italic pull-quote in Cormorant ~2rem:
  > "Just two people who already knew each other a little, getting to know each other properly."

### 4. SCHEDULE (id="schedule")
- Eyebrow: `"so please join us..."`
- Countdown timer to June 4, 2026 (days / hours / minutes / seconds)
- Two event cards side by side on desktop, stacked on mobile:

  **Card 1 — Private Event**
  - Label badge: `PRIVATE EVENT`
  - Date: `wednesday, 3rd june 2026`
  - No venue details (private)

  **Card 2 — Wedding Ceremony**
  - Label badge: `WEDDING & COCKTAIL`
  - Date: `thursday, 4th june 2026`
  - Venue: First Love Center, Trinity Avenue, East Legon
  - Map link: https://maps.app.goo.gl/Z9YXWaPsEMBmmszb8?g_st=ic
  - Note: "Photography & Cocktail immediately after Ceremony at the same venue"
  - Dress code badge: `All things bright & beautiful`

### 5. TIDBITS (id="tidbits")
- Eyebrow: `"a few things you should know about us"`
- 2-column card grid (1 on mobile)
- Each card: question label small/muted, answer in Cormorant italic
- Cards:

  | Question | Answer |
  |----------|--------|
  | Who made the first move? | Daniel called. She was sick, so they talked on the phone instead. |
  | Who takes out the bin? | Daniel. |
  | Most memorable date? | Holiday Inn, the night before he left for Nairobi. |
  | Favourite activity together? | Talking. |
  | Honeymoon destination? | Ask Daniel 😅 |
  | Most memorable trip? | Road trip to Takoradi. |
  | We agree on? | Our faith and belief in Jesus Christ as our Lord and personal Saviour. |
  | Who's funnier? | Daniel says Daniel. The correct answer is Kukua. |
  | Were these answered under duress? | Absolutely 🤣 |

### 6. GIFTS (id="gifts")
- Eyebrow: `"your presence is the greatest gift"`
- Paragraph: "As Daniel is whisking Kukua away to Nairobi, we kindly request no physical gifts.
  If you'd like, contributions to our honeymoon or future plans would be warmly appreciated."
- Three payment detail blocks, each with a copy-to-clipboard button on the number:

  **MTN Mobile Money**
  Belfrieda Kukua Asamoah
  `0549526397`

  **Daniel Dadzie — Stanbic Bank**
  Account: `9040013102222`
  Sort Code: 190114

  **Belfrieda Kukua Asamoah — Stanbic Bank**
  Account: `9040000099079`
  Sort Code: 190110

### 7. FAQ (id="faq")
- Eyebrow: `"questions and answers"`
- Accordion pattern (one open at a time)
- Items:

  | Question | Answer |
  |----------|--------|
  | Can I bring a date? | Please reach out to us directly to arrange this. |
  | Are kids welcome? | Yes! |
  | What should I wear? | All things bright & beautiful — see the Schedule section for details. |
  | Is the wedding indoors or outdoors? | The ceremony is indoors. The cocktail will be outdoors. |
  | Can I take photos? | Yes! Just be mindful of the official photographers. Share your photos with us via the QR code we'll provide on the day — or visit the link in the nav. |
  | Who should I call with questions? | Elizura Asamoah-Koomson: 0202953372 · Telinam Eli: 0540678253 · Rosebud Arthur: 0243312960 |

### 8. FAITH (id="faith")
- Section background: `var(--color-bg-alt)`
- Opening line in italic Cormorant centered (~1.3rem):
  "As we celebrate this beautiful season of love, we want to share the foundation of our joy —
  a personal relationship with God through Jesus Christ."
- Short paragraph (Cormorant 300, body size) with the gospel message — keep it warm, not preachy
- Prayer accordion: label `"Pray with us"`, full prayer text inside:
  > "Heavenly Father, I come to You today acknowledging that I am a sinner and that I need
  > Your forgiveness. I believe that Jesus Christ is Your Son, that He died for my sins, and
  > that You raised Him from the dead. Today, I turn away from my sins and invite Jesus into
  > my heart and my life as my Lord and Savior. Please forgive me, make me new, and help me
  > to follow You all the days of my life. Thank You for loving me, saving me, and giving me
  > eternal life. In Jesus' name, Amen."
- WhatsApp link below: `"If you prayed this prayer, we'd love to hear from you."` → https://wa.me/233244978433

### 9. FOOTER
- Large italic Cormorant closing quote:
  > "He hath made every thing beautiful in his time."
- Below: `Daniel & Kukua · june 4, 2026` in small Jost muted
- Very bottom: `Made with love ♡` in tiny Jost

---

## PHOTO UPLOAD CTA
- Floating button bottom-right on mobile: `📷 Share photos` → href="/upload"
- On desktop this can be omitted (it's in the nav already)

---

## TECHNICAL REQUIREMENTS
- Single HTML file, all CSS + JS embedded
- Google Fonts loaded in `<head>`
- All section IDs: `#story` `#schedule` `#tidbits` `#gifts` `#faq` `#faith`
- Scroll-reveal: `.reveal` class + IntersectionObserver on all major section children
- Countdown timer: `setInterval` every 1000ms, stops at zero
- Accordion: `max-height` CSS transition, no libraries
- Copy-to-clipboard: `navigator.clipboard.writeText()`, show brief "Copied!" feedback
- Nav scroll behavior: track `lastScrollY`, toggle `.hidden` class
- Mobile hamburger: toggles `.nav-open` class on `<body>`, full-screen overlay
- No `font-weight: 700` anywhere
- Warm CSS background on any placeholder image areas (not grey)
