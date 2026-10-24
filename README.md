# scraperapi pricing: What Every Plan Actually Costs, How Credits Really Burn, and Which Tier Makes Sense for Your Project

ScraperAPI's paid plans run from **$49/month (Hobby)** to **$1,975/month (Advanced)**, with a free plan and a 7-day trial in between — but the sticker price is only half the story. Every plan is metered in API credits, and a single request can cost anywhere from 1 credit to 75 depending on the site you're hitting and the options you enable. That gap is where most people get surprised, so this guide walks through the full plan lineup, the credit mechanics behind the prices, and the discounts that are actually verified.

> **Quick take:** paid plans start at $49/month (Hobby, 100,000 credits) and top out at $1,975/month (Advanced) before Enterprise goes custom. Annual billing saves 10% on every tier automatically, and the code **START10** knocks another 10% off your first month at checkout. 👉 [See all current ScraperAPI plan prices](https://scraperapi.io/pricing?fp_ref=coupons)

## The full ScraperAPI pricing table

Here's the complete lineup as shown on the official pricing page — all eight tiers, including the two highest ones most reviews skip. Prices are in USD.

| Plan | Monthly price | Annual (per month) | Credits / month | Concurrent threads | Get it |
| --- | --- | --- | --- | --- | --- |
| Free | $0 | — | 1,000 | 5 | [Start free](https://dashboard.scraperapi.com/signup?fp_ref=coupons) |
| Hobby | $49 | $44.10 | 100,000 | 20 | [View Hobby](https://scraperapi.io/pricing?fp_ref=coupons) |
| Startup | $149 | $134.10 | 1,000,000 | 50 | [View Startup](https://scraperapi.io/pricing?fp_ref=coupons) |
| Business | $299 | $269.10 | 3,000,000 | 100 | [View Business](https://scraperapi.io/pricing?fp_ref=coupons) |
| Scaling | $475 | $427.50 | 5,000,000 | 200 | [View Scaling](https://scraperapi.io/pricing?fp_ref=coupons) |
| Professional | $975 | $877.50 | 10,500,000 | 300 | [View Professional](https://scraperapi.io/pricing?fp_ref=coupons) |
| Advanced | $1,975 | $1,777.50 | 21,500,000 | 500 | [View Advanced](https://scraperapi.io/pricing?fp_ref=coupons) |
| Enterprise | Custom | Custom | 22,000,000+ | 500+ | [Contact sales](https://scraperapi.io/contact-sales/?fp_ref=coupons) |

A second layer of differences sits behind those numbers, and it matters more than the credit counts when you're picking between adjacent tiers:

- **Geotargeting:** Hobby and Startup are locked to US & EU. Business and up get country-level targeting globally (50+ countries).
- **Analytics history:** 30 days on Free through Startup; unlimited from Business up.
- **Pay-as-you-go overage:** only available on Scaling and above. On Hobby, Startup, and Business, hitting 100% of your credits means upgrading or waiting for renewal.
- **Included everywhere:** JS rendering, premium residential and mobile IPs, CAPTCHA and anti-bot handling, JSON auto-parsing, custom sessions, automatic retries, unlimited bandwidth, and a 99.9% uptime guarantee.

That last point is worth pausing on. Every tier gets the same core scraping features — the higher plans sell you more credits, more concurrency, wider geotargeting, and overage flexibility, not better scraping quality.

## Why your real cost won't match the sticker price

ScraperAPI charges in credits, and one credit equals one standard page request — but "standard" is doing a lot of work in that sentence. The official rule: a standard page costs 1 credit, Amazon costs 5, Google and Bing (including subdomains) cost 25, and LinkedIn costs 30. Sites behind Cloudflare, Datadome, or PerimeterX protection add another 10 credits per request when ScraperAPI successfully bypasses them.

On top of the domain-based costs, request parameters stack their own charges:

| Parameter | Extra credits |
| --- | --- |
| `render=true` (JavaScript rendering) | +10 |
| `screenshot=true` | +10 |
| `premium=true` (premium proxy) | +10 |
| `ultra_premium=true` | +30 |
| Anti-bot bypass (auto-detected) | +10 each |

The part that catches people off guard is that these don't add linearly. Combining `premium=true` with `render=true` costs **+25 credits**, not the +20 you'd get from adding them separately. Combining `ultra_premium=true` with `render=true` costs **+75** — nearly double what the individual surcharges would suggest. That stacking is the main reason users report credits draining faster than the headline numbers implied.

Put it all together and the spread is enormous: two customers on the same 100,000-credit Hobby plan can get anywhere from roughly 1,333 scrapes (hard targets, full rendering, ultra-premium proxies) to the full 100,000 (plain static pages). Before committing to a tier, run your actual target URLs through the Domain Cost Estimator in the dashboard — it tells you the exact credit cost for any URL, and you can set a `max_cost` per scrape to cap how much any single request consumes.

One bit of context that explains the whole system: before mid-2022, ScraperAPI sold raw "API calls" where every request counted as one. The switch to credits re-priced requests by difficulty, which is how the company has held the same $49/$149/$299 headline prices for years while anti-bot defenses got harder — the multiplier, not the price tag, absorbs the cost increases. Worth knowing when you compare old reviews that quote 250,000 API calls for Hobby.

## The free ways in: 1,000 monthly credits plus a 7-day trial

You don't have to pay anything to find out what your targets actually cost. Two options exist, and they stack in usefulness even though neither shows up as a card on the pricing grid:

1. **Free plan:** 1,000 free API credits per month, capped at 5 concurrent connections, ongoing for as long as you want it. Good enough to validate that ScraperAPI can handle your target site at all.
2. **7-day trial:** 5,000 API credits, no credit card required. This is the better option for testing at anything resembling real volume, since 1,000 credits burns out fast on rendered pages.

If your test needs more than 5,000 credits, support can grant additional testing credits — you have to ask, though. 👉 [Start the 7-day free trial with 5,000 credits](https://dashboard.scraperapi.com/signup?fp_ref=coupons)

## What actually happens when you run out of credits

The overage rules split the plan lineup in half, and it's one of the least-advertised differences between tiers.

On Free, Hobby, Startup, and Business, scraping pauses when your credits hit zero until the next renewal. You can opt into **auto-upgrade** (available on Hobby through Professional), which bumps your account to the next plan automatically when credits run out — convenient, but also an easy way to spend more than you planned.

On Scaling, Professional, Advanced, and Enterprise, you get **pay-as-you-go** instead: keep scraping past your included credits at a fixed per-credit rate, up to a monthly spending cap you set yourself. If your workload has spiky months, this is a genuine reason to pick Scaling over Business even though Business looks like decent value at $299.

A few billing details that live in the fine print:

- **Credits don't roll over.** Unused credits vanish at your renewal date. No banking them for a slow month.
- **You're billed for 200s and 404s.** Any request that returns a 200 or a 404 counts, as does one you cancel before ScraperAPI's 70-second attempt window finishes. A "failed" scrape on your end doesn't always mean a free one.
- **Concurrency overages are free.** If you exceed your thread limit, you get a 429 response asking you to back off and retry — the request is turned away, not queued, and there's no extra charge.

## Annual billing and the promo code that actually works

Annual billing takes a flat 10% off every paid plan, applied automatically — no code needed. In practice: Hobby goes from $49 to $44.10 per month, Scaling from $475 to $427.50, and Business saves $360 over twelve months. If you're staying past two or three months, the math works itself out.

There's also one promo code worth using at checkout: **START10**, which takes 10% off your first month on any paid plan. It's been confirmed across multiple independent sources as recently as August 2026. Treat it as a first-month discount, not a lifetime one — and be skeptical of the "28% off" and "50% off" codes floating around coupon aggregators; most of those are auto-generated and don't apply. One caveat: some coupon sites describe START10 as tied to annual subscriptions, so check the checkout terms when you enter it.

Two more things to look for before you pay: the 10% annual discount and START10's first-month discount are separate mechanisms, and the pricing page currently shows a limited-offer badge of +250K bonus credits on Professional (with +500K reported for Advanced), so if you're eyeing those tiers, check what's live before you buy. 👉 [Open the pricing page and apply START10 at checkout](https://scraperapi.io/pricing?fp_ref=coupons)

## How to estimate your real monthly cost before you buy

The reliable way to size a plan takes about ten minutes and uses tools ScraperAPI gives you for free:

1. List your target URLs and how many requests per month you need for each.
2. Run each URL through the Domain Cost Estimator in the dashboard to get its exact per-request credit cost.
3. Multiply: expected requests × average credit cost per request = monthly credits needed.
4. Divide by the plan's included credits to sanity-check the fit — and add 20–30% headroom, because credits don't roll over and hard targets are more common than people expect.

Running this before purchase is the difference between "100,000 credits sounds like plenty" and knowing that Hobby covers Amazon price checks (5 credits each on plain requests) about 20,000 times a month, but only manages around 1,300–1,400 full renders of a Cloudflare-protected site.

## Which plan fits which situation

Based on the verified numbers, the decision tree looks like this:

- **Just validating a target site:** Free plan (1,000 credits) or the 7-day trial (5,000 credits). Spend nothing yet.
- **Solo dev, mostly static pages, side project:** Hobby at $49/month is the realistic entry point. Just confirm your credit burn rate first — 20 threads is plenty for one person.
- **Small team, recurring scraping workflow:** Startup at $149/month, 1M credits and 50 threads, is the first tier built for sustained use rather than occasional bursts.
- **Production e-commerce or market research pipeline:** Business at $299 adds global country-level targeting and unlimited analytics. If your volume swings month to month, Scaling at $475 buys pay-as-you-go overage so you don't hit a hard wall.
- **Continuous, multi-source data pipelines:** Professional ($975) and Advanced ($1,975) bring tens of millions of credits, 300–500 threads, and priority routing. Enterprise covers anything above 22M credits with custom terms.

It's also worth knowing that every tier includes the structured extras, not just raw requests: Structured Data Endpoints return parsed JSON for Amazon, Google, Walmart, eBay, and Redfin (price, rating, BSR, images, seller info — no parser to maintain), plus Async Scraper Service for firing off massive request batches and DataPipeline for building automated workflows without code. If you're currently paying for a separate Amazon or SERP data API, that bundled capability can shift which tier makes sense — or make a mid-tier plan cover more than the credit count suggests.

## FAQ

**Does ScraperAPI have a free plan?**
Yes — 1,000 free API credits per month with up to 5 concurrent connections, plus a one-time 7-day trial with 5,000 credits that doesn't require a credit card. Neither appears as a card on the pricing grid; you access the free plan through the signup page.

**How much does 1 request actually cost?**
Between 1 and 75 credits. A standard unprotected page costs 1, Amazon costs 5, Google/Bing searches cost 25, LinkedIn costs 30, and each enabled option (JS rendering, premium proxy, anti-bot bypass) adds its own surcharge — with non-linear stacking when you combine them.

**Do unused ScraperAPI credits roll over?**
No. Anything left in your credit pool at the renewal date is gone. Annual plans can renew early for a fresh batch if you run dry ahead of schedule.

**Does ScraperAPI offer refunds?**
The pricing page and FAQ don't publish a refund policy, so don't assume one exists. If a refund matters to your decision, confirm the terms with support before you pay — the 7-day trial without a credit card is the safer way to evaluate first.

**What's the cheapest way to get a discount?**
Annual billing gives 10% off automatically on every paid plan, and the START10 code takes another 10% off your first month. Beyond that, the free plan and trial let you defer spending entirely until you've confirmed your credit burn rate.

## Before you check out

The plan choice really comes down to two questions: how hard are your target sites, and does your volume spike? Static pages on a solo project → Hobby. Recurring team workflows → Startup or Business. Spiky production workloads where hitting a wall mid-month would hurt → Scaling or above, for the pay-as-you-go safety valve.

Whatever you land on, do the Domain Cost Estimator check first, and remember credits expire at renewal — starting one tier lower with auto-upgrade enabled beats overbuying a pool that evaporates. Check that START10 applies correctly at checkout, and if you're eyeing Professional or Advanced, verify whether the bonus-credit offer is still live. 👉 [Compare all ScraperAPI plans and current pricing](https://scraperapi.io/pricing?fp_ref=coupons)
