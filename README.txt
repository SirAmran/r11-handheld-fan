YOYOS DEVICES — R11 Handheld Fan
==============================================================
Single-file pages: index.html and learn-more.html (CSS + JS
inlined, no separate style.css/script.js). Images in /images.

WHAT'S IN THIS BUILD (all 3 phases)
-------------------------------------
PHASE 1 — Hero, benefits, "Why You Need This"
  - All water/mist/fragrance copy removed (this fan has no water
    tank or mist function — that was the wrong product)
  - New copy built only from what's actually confirmed: double-click
    power control, rechargeable, portable, adjustable speed shown
    on the digital display
  - Real photos in place: hero shot, control-guide diagram, and two
    cluttered source photos that were background-removed and
    recomposited onto a clean on-brand backdrop (images/r11-colors.jpg,
    images/r11-stock.jpg)

PHASE 2 — Pricing, demo section, use-case cards
  - Pricing locked in: 1 unit ₦15,000 (was ₦17,000), 2 units ₦25,000
    (was ₦26,500), 3 units ₦30,000 (was ₦32,000) — 2-unit tier tagged
    "Most Popular", 3-unit tier tagged "Best Value"
  - Demo section resized for a 9:16 VERTICAL video (you said the demo
    video is 9:16) instead of the old 16:9 layout
  - A "coming soon" placeholder sits where the video goes until you
    add it — an HTML comment right above it on both index.html and
    learn-more.html has copy-paste-ready snippets for either a
    self-hosted <video> file or a YouTube embed
  - Use-case cards (Home/Office/Travel/Outdoors) each show a
    different photo now — no card repeats an image already shown
    right next to it

PHASE 3 — Learn More page
  - Rewritten for the R11: description, "Available Colors" section
    (purple/black and rose-gold/cream, shown side by side), and a
    full spec grid
  - Spec grid only states what's actually confirmable: model, ~0.2kg
    weight, double-click power control, digital display, 2 colors,
    handheld/rechargeable design
  - Everything NOT independently confirmable — battery capacity,
    charging port, motor RPM, runtime — is flagged honestly in a note
    under the spec grid instead of guessed at
  - "What's in the Box" only lists the fan itself; charging cable
    inclusion is flagged as unconfirmed rather than assumed
  - Care tips: charge before first use, don't submerge, keep from
    young children, store cool and dry

PERFORMANCE PASS (page weight / speed)
-----------------------------------------
  - Also found and fixed a real bug: the logo/favicon files
    (logo.png, favicon-32.png, apple-touch-icon.png) were missing
    from the last delivery even though the HTML referenced them —
    they're back in /images now.
  - All 4 product photos converted from JPEG to WebP and resized to
    their actual display size instead of full camera resolution:
    total product-photo weight dropped from ~205KB to ~54KB.
  - Logo shrunk from an oversized 256×256 PNG down to 128×128
    (still 2x sharp for its 34px display size).
  - Total /images folder: ~345KB → ~112KB.
  - Hero image loads eagerly with fetchpriority="high" (it's the
    first thing visitors see); every other image on both pages now
    uses loading="lazy" so nothing downloads until the visitor
    actually scrolls to it.
  - All images have explicit width/height so the page doesn't jump
    around while images load in on a slow connection.

STILL OPEN / NEEDS YOUR INPUT
--------------------------------
1. DEMO VIDEO — drop your 9:16 video in and swap the placeholder for
   one of the two ready-made snippets (see the HTML comments above
   the placeholder on both pages).

2. SPEC CONFIRMATION — if your supplier can confirm battery mAh,
   charging port type, motor RPM, or runtime, send them over and
   I'll drop them into the Learn More spec grid.

3. CHARGING CABLE — confirm whether one ships in the box so
   "What's in the Box" can state it definitively.

4. META PIXEL ID — index.html <head>, the second Meta Pixel script
   block still has PIXEL_ID_HERE as a placeholder (the first block
   already has your real ID — this second one looks like a leftover
   duplicate from an earlier edit; worth deleting entirely, or at
   minimum leaving it as-is since fbq() guards against double-firing).

5. WHATSAPP / CONTACT — footer of both pages still has
   WHATSAPP_NUMBER_HERE as a placeholder.

6. ORDER NOTIFICATION EMAILS — your existing Netlify "Email"
   notifications for the mistfan-order form won't fire anymore since
   the form is now named "r11-order". Go to Netlify → Project
   configuration → Notifications → Emails and webhooks → Form
   submission notifications → Add notification, and set up email
   notifications (or your Google Sheets Apps Script webhook) for the
   new "r11-order" form name.

7. DOMAIN NAME — the live site is still hosted at
   mistfans.yoyosdevices.com.ng, which no longer matches the product.
   Not something I can change from here — worth deciding if you want
   to rename the subdomain or just keep it as an internal detail
   visitors won't notice.

DEPLOY
------
Push index.html, learn-more.html, and /images to your GitHub repo —
same as before, it'll pick up on Netlify automatically. No build
step, plain HTML with inline CSS/JS.
