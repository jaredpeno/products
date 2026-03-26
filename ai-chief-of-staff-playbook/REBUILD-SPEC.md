# AI Chief of Staff Playbook — Landing Page Rebuild Spec

## Overview
Complete rebuild of the landing page and thank-you page at:
- `/ai-chief-of-staff-playbook/index.html` (sales page)
- `/ai-chief-of-staff-playbook/thank-you/index.html` (post-purchase)
- `/refund/index.html` (refund policy — add digital download exception)

## CRITICAL CHANGES (Non-negotiable)

### 1. Timeline: "30 days" → "a weekend"
- Replace ALL "30 days" / "30-day" references with "a weekend" or "by Monday"
- Hero: "Built in 30 Days" → "Built in a Weekend"
- The framing: "I spent 30 days building this. You'll spend a weekend."
- FAQ: update all timeline references
- Thank-you page: update roadmap from 4-week to weekend plan
- Proof stats: "30 Days to build" → change to something like "12 Failures documented"

### 2. Thank-you page: Purchase gate
- Add the SAME JavaScript purchase verification gate as vendor-scorecard/thank-you/index.html
- Checks for `session_id` query param starting with `cs_`
- Calls `/api/verify-purchase?session_id=...`
- Redirects to sales page if invalid
- `body` starts with `style="display:none;"` until verified

### 3. Download button: Wire to actual PDF
- The download button currently has `href="#"` — replace with the actual Stripe-hosted file or a direct download link
- For now, use a Google Drive link to the PDF: create a shareable link
- The PDF is at: `/Users/jared/.openclaw/workspace/brand/products/openclaw-setup-guide/THE-AI-CHIEF-OF-STAFF-PLAYBOOK.pdf`

### 4. Newsletter: Replace email.simplifyit.co links
- email.simplifyit.co is DEAD — remove all references
- In the FAQ "What if I get stuck?" answer: remove the newsletter link, just mention the newsletter by name
- In footer: remove the newsletter link or link to jaredpeno.com instead
- On thank-you page: use embedded Beehiiv signup form (see #5)

### 5. Thank-you page: Embedded newsletter signup
- Match the format from vendor-scorecard/thank-you/index.html
- Use the embedded form with `subscribeBeehiiv()` function
- POST to `/api/subscribe` with utm_source: 'ai-playbook-buyer'
- Include email input + subscribe button in the standard `.form-wrap` layout

### 6. Thank-you page: Download format
- Match other thank-you pages: direct document access links
- Step 1 should have a direct download button (not "check your email")
- Remove "Your download link has been sent to your purchase email" language
- Replace with direct access button(s) like vendor-scorecard has

### 7. Refund policy: Digital download exception
- Add a new section to `/refund/index.html` BEFORE the general digital products section
- Title: "Digital Downloads (AI Chief of Staff Playbook)"
- Content: "Due to the nature of instantly-delivered digital downloads that can be copied, all sales of the AI Chief of Staff Playbook are final. No refunds will be issued for this product. Please review the product details carefully before purchasing."
- Update the general digital products section to note "except where marked as all-sales-final"
- On the landing page: replace the 30-day guarantee box with an "All Sales Final" notice

### 8. Sales copy overhaul (War Room synthesis)

#### Hero Section
- Eyebrow: Remove "v1.1, March 2026"
- Headline: "What If Your Business Had a Chief of Staff Who Never Slept, Never Forgot, and Cost $4/Day?"
- Sub: "I spent 30 days building this system. You'll spend a weekend. This is the exact playbook — every architecture decision, every failure, every fix."
- CTA: "Get Instant Access — $197"
- Secondary: "See What's Inside ↓"
- Trust line: "🔒 Stripe checkout · Instant PDF download · All sales final"
- Keep the terminal card mockup on the right but make it cleaner

#### Problem Section
- New opener: "You're not behind on AI because you're lazy. You're behind because no one's shown you the architecture."
- Rewrite the supporting paragraph to be more specific to ICP
- Keep 4 pain points but make them sharper

#### Vision Section  
- Add before/after framing
- Keep the 4 feature cards but tighten copy

#### Ally Proof Section
- Reframe: "This guide wasn't written by a consultant. It was written by Ally — the autonomous AI Chief of Staff this playbook teaches you to build. That's not a gimmick. That's a product demo."
- Update stats: remove "30 days" stat

#### Pricing Section
- Remove "v1.1 — March 2026" badge
- Add price anchoring: show what alternatives cost (ops coordinator, AI consultant, etc.)
- Update guarantee to "All Sales Final" with clear digital product notice
- Add friction reducer under CTA: "Instant PDF download. No subscription. No upsells."

#### FAQ Updates
- Update timeline answers to "weekend" framing
- Add: "Why are all sales final?" 
- Remove email.simplifyit.co newsletter link
- Update "How long does it take" to emphasize weekend

### 9. Product images
- Hero: Use `images/playbook-hero.png` (the floating book mockup)
- Telegram: Use `images/telegram-briefing-v2.png` (when ready, fallback to telegram-briefing.png)
- Place hero image on RIGHT side of hero section, replacing the CSS terminal stack
- Place Telegram mockup in the Vision section or Ally Proof section
- Keep the terminal card aesthetic as a secondary visual element if space allows
- All images should use proper alt text and lazy loading

### 10. Drop version references
- Remove "v1.1" and "March 2026" from ALL copy
- Remove from: eyebrow, pricing badge, price-includes list, download note
- Product name is just "The AI Chief of Staff Playbook" — no version

### 11. Landing page best practices
- Don't add images where not necessary — only where they demonstrate value
- Keep the page scannable
- Ensure consistent CTA copy throughout
- Mobile responsive (test all breakpoints)
- Images should have proper width/height attributes
- Lazy load below-fold images

## Files to modify
1. `ai-chief-of-staff-playbook/index.html` — full rebuild
2. `ai-chief-of-staff-playbook/thank-you/index.html` — full rebuild  
3. `refund/index.html` — add digital download section

## Reference files (for format/style matching)
- `vendor-scorecard/thank-you/index.html` — purchase gate + newsletter embed format
- Existing CSS design system should be maintained (Inter font, navy theme, blue accents)

## Image assets available
- `images/playbook-hero.png` — 1536x1024, floating book mockup
- `images/telegram-briefing.png` — 1024x1536, Telegram chat mockup (v1)
- `images/telegram-briefing-v2.png` — 1024x1536, improved version (may be generating)
- `images/agent-dashboard.png` — 1536x1024, terminal dashboard
