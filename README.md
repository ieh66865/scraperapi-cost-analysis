# Web Scraping API Pay Per Request: Is ScraperAPI's Credit System Worth It? — How Credits Really Work, Which Plan Fits Your Scale, and Where the Hidden Costs Are (Full Plan Breakdown + Real Cost Math)

If you've ever Googled "web scraping api pay per request" and ended up more confused than when you started, you're not alone.

Most people searching that phrase are in one of two boats: they're sick of building and babysitting their own proxy infrastructure, or they just ran into their third IP ban this week and need a faster solution. Either way, the promise of a scraping API — *just throw a URL at it, get data back* — sounds like exactly what they need.

But the moment you look at actual pricing pages, the dream starts getting complicated. Credits, multipliers, tiers, concurrent threads, annual discounts... suddenly you're doing spreadsheet math at midnight.

This article cuts through all of that. We're going to talk honestly about how **ScraperAPI** — one of the most popular web scraping APIs on the market — actually prices its service, what "pay per request" really means in practice, and how to figure out if it's the right tool for what you're trying to build.

---

**What Does "Pay Per Request" Actually Mean for a Scraping API?**

Let's start with a definition, because the phrase is used loosely.

In the traditional sense, a true pay-per-request model means you pay a flat fee for each request you make — no monthly commitment, no subscription. Think of it like a vending machine: put money in, get one item out.

Most scraping APIs, including ScraperAPI, don't work exactly like that. They use a **credit-based subscription model**: you buy a plan that includes a bucket of credits per month, and each request draws from that bucket. The number of credits consumed per request varies based on what you're scraping and what features you turn on.

So why does this matter? Because the difference between "100,000 credits" and "100,000 actual useful requests" can be anywhere from equal to a **75x gap**, depending entirely on what you're scraping.

---

**How ScraperAPI's Credit System Works (And Why It Surprises People)**

ScraperAPI was founded in 2018, is headquartered in Las Vegas, and now processes over 36 billion API requests per month for over 10,000 brands — including Deloitte, Sony, and Alibaba. The core value proposition is simple: you send a URL, they handle proxy rotation across 40 million+ IPs in 50+ countries, CAPTCHA solving, JavaScript rendering, and automatic retries. You get back the HTML.

The credit system is where things get nuanced.

**Base domain costs:**

| Target Domain Type | Credits per Request |
|---|---|
| Normal websites (blogs, news, simple HTML) | 1 |
| E-commerce (Amazon, eBay, Walmart) | 5 |
| SERP (Google, Bing — all subdomains) | 25 |
| Social Media (LinkedIn) | 30 |

These multipliers are automatic — you don't opt in. The moment ScraperAPI detects you're hitting an Amazon URL, it costs 5 credits per request, no matter what.

On top of the base domain cost, optional features add more:

| Parameter / Feature | Extra Credits |
|---|---|
| JavaScript rendering (`render=true`) | +10 |
| Screenshot (`screenshot=true`) | +10 |
| Premium proxy (`premium=true`) | +10 |
| Ultra-premium proxy (`ultra_premium=true`) | +30 |
| `premium=true` + `render=true` combined | +25 (not +20) |
| `ultra_premium=true` + `render=true` combined | +75 (not +40) |
| Cloudflare / DataDome / PerimeterX bypass | +10 each (auto-detected) |

Notice that last row in the combo section. Combining `ultra_premium` with `render=true` costs **75 extra credits per request** — not the 40 you'd expect if you just added the two together. This non-linear stacking is one of the biggest sources of budget surprises for new users.

Some parameters, thankfully, cost nothing extra: `wait_for_selector`, `country_code`, `session_number`, `device_type`, `output_format`, `keep_headers=true`, `autoparse=true`.

**One more thing:** ScraperAPI only charges for successful requests — those returning HTTP 200 or 404 status codes. Genuine network failures don't cost you. However, if you cancel a request before ScraperAPI finishes processing (the window is 70 seconds), you will still be charged.

---

**Every ScraperAPI Plan, Laid Out Clearly**

Here's a complete breakdown of every plan currently available, including the new Growth plans launched in May 2026:

| Plan | Monthly Price | Annual Price (per mo) | API Credits | Concurrent Threads | Geotargeting | Pay-As-You-Go |
|---|---|---|---|---|---|---|
| **Free** | $0 | — | 1,000/mo | 5 | No | No |
| **Hobby** | $49 | ~$44.10 | 100,000/mo | 20 | US & EU only | No |
| **Startup** | $149 | ~$134.10 | 1,000,000/mo | 50 | US & EU only | No |
| **Business** | $299 | ~$269.10 | 3,000,000/mo | 100 | 50+ countries | No |
| **Scaling** | $475 | ~$427.50 | 5,000,000/mo | 200 | 50+ countries | ✅ Yes |
| **Professional** | $975 | ~$877.50 | 10,500,000/mo + 250K bonus | 300 | 50+ countries | ✅ Yes |
| **Advanced** | $1,975 | — | 21,500,000/mo + 500K bonus | 500 | 50+ countries | ✅ Yes |
| **Enterprise** | Custom | Custom | 5M+/mo custom | 200+ | 50+ countries | ✅ Yes |

> **Free trial:** When you first sign up, you get **5,000 API credits for 7 days** — no credit card required. After that, you drop to the Free tier (1,000 credits/month with 5 concurrent connections). There's also a **7-day no-questions-asked refund policy** on paid plans.

👉 [Start Your Free Trial — 5,000 Credits, No Card Required](https://www.scraperapi.com/?fp_ref=coupons)

---

**The Real Math: What Each Plan Actually Gets You**

The advertised credit numbers look great on paper. Here's what they translate to in practice, across three common scraping scenarios:

| Plan | Monthly Cost | Standard (1 cr/req) | JS Rendered (10 cr/req) | Amazon (5 cr/req) | Ultra-Premium + JS (75 cr/req) |
|---|---|---|---|---|---|
| Hobby | $49 | 100,000 pages | 10,000 pages | 20,000 pages | ~1,333 pages |
| Startup | $149 | 1,000,000 pages | 100,000 pages | 200,000 pages | ~13,333 pages |
| Business | $299 | 3,000,000 pages | 300,000 pages | 600,000 pages | ~40,000 pages |
| Scaling | $475 | 5,000,000 pages | 500,000 pages | 1,000,000 pages | ~66,667 pages |

If most of your target sites need JavaScript rendering and are protected by Cloudflare — which is increasingly common — a $49/month Hobby plan can realistically get you around 1,300 actual usable pages. That's a far cry from the "100,000 credits" headline.

The key question to ask before signing up: **what does my specific scraping scenario actually cost per request?**

ScraperAPI has a Domain Multiplier tool inside the dashboard, and an API endpoint (`https://api.scraperapi.com/account/urlcost`) that lets you calculate the exact credit cost for any URL before you commit to large runs. Use it. Seriously.

---

**Pay-As-You-Go: What It Is and Who Gets It**

One of the most misunderstood aspects of ScraperAPI's pricing is the Pay-As-You-Go (PAYG) option.

PAYG allows you to continue using the API even after your monthly credit allocation runs out — you just pay for the extra credits at a fixed per-credit rate, with a spending cap you set yourself so you're never surprised. This protects you from getting cut off mid-project at a critical moment.

Here's the catch: **PAYG is only available on the Scaling plan and above.** If you're on Hobby, Startup, or Business and you exhaust your credits before your billing cycle renews, you have two options: auto-upgrade to the next plan tier, or get a custom plan from their support team. There's no "keep going at overage rates" button for lower plans.

This is a meaningful constraint for teams building anything that has unpredictable or spiky usage patterns.

For Scaling, Professional, Advanced, and Enterprise plans, PAYG is fully available with a configurable monthly spending cap — your pipeline won't silently rack up bills beyond what you've approved.

👉 [Explore ScraperAPI Plans — Find the Right Tier for Your Volume](https://www.scraperapi.com/?fp_ref=coupons)

---

**Where ScraperAPI Shines — and Where It Doesn't**

No scraping API performs equally well on every website. Independent benchmarks from Scrapeway (April 2026) give a clear picture of where ScraperAPI earns its reputation:

| Target Site | Success Rate | Notes |
|---|---|---|
| Zillow | 100% | Exceptional |
| Etsy | 99% | Very strong |
| Amazon | 98% | Reliable, good structured data endpoints |
| LinkedIn | 95% | Works but expensive at 30 cr/req |
| Walmart | 93% | Solid |
| Indeed | 90% | Adequate |
| StockX | 84% | Mixed |
| Realtor.com | 12% | Struggles significantly |
| Instagram | 0% | Complete failure |
| Booking.com | 0% | Complete failure |
| Twitter/X | 0% | Complete failure |

The overall average success rate hovers around 62–64%, slightly above the industry average of 58–59%. Average response time is in the 5–7 second range, which is faster than the industry average.

**ScraperAPI's Structured Data Endpoints (SDE)** are one of its strongest differentiators. Rather than returning raw HTML that you have to parse yourself, the SDEs deliver pre-parsed JSON for 18 endpoints across 5 platforms:

- **Amazon**: Product details (ASIN), search results, competitor offers — 18+ fields, 21 regional marketplaces
- **Google**: SERP, Shopping, Maps, News, Jobs
- **Walmart**: Product, Search, Category, Reviews
- **eBay**: Product, Search
- **Redfin**: Search, Agent Details, Rental Properties, For Sale

These endpoints are available on all plans, including the Free tier. If Amazon product data or Google SERP data is your primary use case, the SDEs alone can save significant development time — you skip writing and maintaining your own parsing logic.

---

**One Thing Most Reviews Gloss Over: The DataPipeline Credit Cost**

ScraperAPI offers a no-code DataPipeline feature for scheduling scraping jobs and delivering data via webhooks — great in theory for non-engineers who want automated data collection.

The catch: DataPipeline uses a **different, higher credit schedule**. A basic normal request that costs 1 credit via the standard API costs **6 credits** inside DataPipeline.

| Request Type | Standard API | DataPipeline | Multiplier |
|---|---|---|---|
| Basic normal request | 1 credit | 6 credits | 6x |
| E-commerce basic | 5 credits | 10 credits | 2x |
| SERP basic | 25 credits | 30 credits | 1.2x |
| Ultra-premium + JS | 75 credits | 80 credits | ~1.07x |

If you set up no-code pipelines expecting standard credit consumption, you'll burn through your allocation much faster than anticipated. This is documented, but you have to dig through the docs to find it.

---

**What Real Users Say**

ScraperAPI has a 4.5/5 rating on Trustpilot (43 reviews), 4.4/5 on G2 (16 reviews), and 4.6/5 on Capterra (62 reviews) — with Ease of Use scoring 4.9/5 on Capterra, which tells you something about the developer experience.

Common praise across platforms:

> *"We love their pricing model where you pay only for successful requests."*

> *"ScraperAPI was extremely easy to use out of the box. We are able to get around website blocks easily."*

> *"Very reliable and fast and worth every cent."*

The complaints cluster around two themes: credit multiplier surprises (people burning through credits faster than expected), and performance on heavily protected or niche targets. One notable Trustpilot review described a situation where a user was quoted $3,600 for 60M credits at 1 credit per Amazon request, but a 5x domain multiplier was applied post-payment — reducing the effective delivery to 12M requests.

The lesson isn't that ScraperAPI is deceptive — the multiplier system is documented — it's that you need to understand the credit math **before** you commit, especially for domain-specific work like Amazon.

---

**Who Should Actually Use ScraperAPI?**

ScraperAPI is built for **developers**. If you can write Python or Node.js, and you're building a pipeline that needs to handle scale, it's one of the most battle-tested tools in the space. The setup experience is genuinely clean:

python
import requests

payload = {
    "api_key": "YOUR_KEY",
    "url": "https://example.com/products",
    "render": "true",
    "country_code": "us"
}

response = requests.get("http://api.scraperapi.com", params=payload)
html = response.text


That's it. Proxy rotation, CAPTCHA handling, and retry logic all happen automatically.

**ScraperAPI is a strong fit if:**
- You're scraping Amazon, Google SERPs, Walmart, or Zillow at meaningful volume
- Your team includes developers who can build around raw HTML or use the structured data endpoints
- You need global geotargeting (Business plan or above)
- You're processing hundreds of thousands to millions of pages per month and want reliable infrastructure

**It's probably not the right tool if:**
- You're trying to scrape Instagram, Twitter/X, or Booking.com (0% success rate)
- You need to scrape sites that require authentication — ScraperAPI explicitly forbids scraping behind login walls
- You're a non-technical user who wants to export data to a spreadsheet without writing code
- Your volume is very low and irregular — the subscription model may not justify the fixed monthly cost

---

**The DataPipeline and Async Scraper for Non-Engineers**

Worth briefly noting: ScraperAPI does offer two paths that reduce coding requirements.

**DataPipeline** is a no-code scheduling interface where you set up recurring scraping jobs, configure delivery webhooks, and manage data collection without writing scraping code yourself. The trade-off is the 6x credit multiplier mentioned above.

**Async Scraper Service** handles high-throughput batch jobs — you send millions of URLs asynchronously and retrieve results when they're ready. This is particularly useful for large-scale one-time collection projects or when you're not able to process results in real time.

Both are available on paid plans, with the Async Scraper being most useful at the Business tier and above.

👉 [See All ScraperAPI Features and Sign Up Free](https://www.scraperapi.com/?fp_ref=coupons)

---

**Practical Tips Before You Spend a Dollar**

**1. Test on your actual targets first.** Use the free 7-day trial (5,000 credits, no card) to run 200–500 requests against your real URLs. Track which sites need JavaScript rendering and which trigger anti-bot multipliers. This gives you the real numbers for budget calculation.

**2. Use the Domain Multiplier tool.** ScraperAPI's dashboard has a Domain Multiplier lookup where you can enter any URL and see its credit cost before running at scale. The API endpoint (`https://api.scraperapi.com/account/urlcost`) does the same thing programmatically.

**3. Don't combine `ultra_premium` and `render=true` unless necessary.** The combined cost is 75 credits — nearly the cost of 75 standard requests. Test whether `premium=true` + `render=true` (25 credits) achieves the same success rate before jumping to the ultra-premium tier.

**4. Watch for forced caching.** On heavily protected targets, ScraperAPI applies a 10-minute result cache. If you're tracking time-sensitive data like live pricing or stock levels, you may receive results that are up to 10 minutes old. Plan your refresh intervals accordingly.

**5. Set a Pay-As-You-Go spending cap.** If you're on Scaling, Professional, Advanced, or Enterprise, the PAYG feature lets you set a hard monthly cap. Use it — it prevents any scenario where your pipeline runs away and generates unexpected overage bills.

**6. Check your response headers.** Every ScraperAPI response includes a `sa-credit-cost` header showing exactly how many credits that request consumed. Log these in your pipeline so you can spot unexpected multipliers before they drain your budget.

---

**ScraperAPI Plan Quick-Select Guide**

Not sure which plan to pick? Here's a simple way to think about it:

- **Just testing / tiny project (under 1K pages/month):** Start with the Free tier or the 7-day trial. No credit card needed.
- **Small project / side project (~100K pages/month, simple HTML):** Hobby at $49/month.
- **Growing team scraping moderate volumes from standard sites:** Startup at $149/month or Business at $299/month (get the Business plan if you need geotargeting outside US & EU).
- **Production pipeline with variable usage and need for PAYG:** Scaling at $475/month — this is the entry point for Pay-As-You-Go and 200 concurrent threads.
- **High-volume operations (10M+ credits/month):** Professional at $975/month or Advanced at $1,975/month, both with PAYG included and the recently added bonus credit pools.
- **Custom deal / large enterprise:** Contact ScraperAPI's sales team directly for a tailored Enterprise arrangement.

👉 [Start Free — 5,000 Credits, 7-Day Trial, No Card Required](https://www.scraperapi.com/?fp_ref=coupons)

---

**The Bottom Line on Web Scraping API Pay Per Request**

The phrase "pay per request" is appealing because it implies you only pay for what you use — no waste, no idle fees. In practice, ScraperAPI's model is a step away from that: it's a subscription that includes a monthly credit pool, with optional PAYG overflow for higher tiers.

For most developer teams building real scraping pipelines, that's actually fine. Subscriptions are predictable, the credit system scales sensibly, and the infrastructure — 40M+ IPs, automatic CAPTCHA solving, JS rendering — genuinely removes weeks of engineering work.

The gotchas are real but avoidable: understand the credit multipliers before you build, test on your actual target sites, and choose a plan that includes PAYG if your usage is anything other than perfectly predictable.

ScraperAPI has been around since 2018, serves tens of thousands of brands, and has earned its reputation as one of the most reliable scraping APIs in the market. For Amazon, Google, Walmart, and Zillow specifically, it's hard to argue against it. Just do the math first.

👉 [Get Started with ScraperAPI — First 5,000 Credits Free](https://www.scraperapi.com/?fp_ref=coupons)
