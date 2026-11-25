# Job Posting Scraper Pricing: What 1,000 Postings Really Cost, Why Workday Boards Stop at 2,000, and When a Paid API Isn't Worth It (Plan Table + Credit Math)

A job posting scraper costs between roughly $0.10 and $15 per 1,000 postings once you convert every published rate to the same unit. On ScraperAPI's credit pricing, 1,000 plain career-site pages come to about **$0.49 on Hobby** and **$0.10 on Business**; those same 1,000 pages on LinkedIn are billed at 30 credits each, which lands near **$14.70 on Hobby**.

If you're tracking a handful of employers and a few hundred open roles, you don't need to pay anyone. Workday publishes a JSON endpoint you can call yourself, and a curl loop will pull the list. Past a few thousand postings a month across many employers, the real work becomes the blocking, the rendering, and the pagination caps that quietly cut your dataset in half.

## Quick pick

> **Most people building a job board, a hiring-signal pipeline or a training corpus:** the **Hobby plan at $49/month for 100,000 credits** (or $44.10/month billed annually) covers roughly 95,000 postings including their detail pages, plus the listing requests that found them. Country-level geotargeting and unlimited analytics history start at Business ($299/month), so choose Hobby if US and EU targeting is enough.
> 👉 [See what the Hobby plan includes](https://www.scraperapi.com/pricing/?fp_ref=coupons)

## ScraperAPI's plans, as published

| Plan | Credits / month | Threads | Price | Get it |
| --- | --- | --- | --- | --- |
| Free trial (7 days) | 5,000 | — | $0, no card required | [ Start the trial](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Free | 1,000 | 5 | $0 | [ Free plan](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Hobby | 100,000 | 20 | $49/mo, or $44.10/mo annual ($529.20/yr) | [ Hobby](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Startup | 1,000,000 | 50 | Shown on the pricing page | [ Startup](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Business | 3,000,000 | 100 | $299/mo, or $269.10/mo annual ($3,229.20/yr) | [ Business](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Scaling | 5,000,000 | 200 | $475/mo, or $427.50/mo annual ($5,130/yr) | [ Scaling](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Professional | 10,500,000 | 300 | Shown on the pricing page | [ Professional](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Advanced | 21,500,000 (+500K bonus, limited offer) | 500 | $1,975/mo, or $1,777.50/mo annual ($21,330/yr) | [ Advanced](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Enterprise | 22,000,000+ | 500+ | Custom | [ Talk to sales](https://www.scraperapi.com/pricing/?fp_ref=coupons) |

The published price table carries list prices for Hobby, Business, Scaling and Advanced. Startup and Professional appear in the plan comparison with their credit allowances and thread counts, and their current prices are shown on the page itself, so I've left those two cells blank rather than invent numbers.

Differences beyond the credit count matter more than they look:

- **Geotargeting** is US and EU only on Hobby and Startup. Country-level targeting starts at Business. If your pipeline has to look like it's browsing from Germany or Brazil, Hobby won't do it.
- **Analytics history** is 30 days on Hobby and Startup, unlimited from Business up.
- **Pay-as-you-go** past your credit limit is available on Scaling, Professional, Advanced and Enterprise.
- **Auto-upgrade** to the next plan when credits run out is opt-in on Hobby through Professional.
- **No rollover.** Balances reset at renewal, so don't buy a big plan in advance for a burst you haven't scheduled.
- **Annual billing** takes 10% off every listed plan.

## Credits per request, and what that means per 1,000 postings

ScraperAPI bills per request. A standard page is 1 credit, and the pricing page lists higher rates for harder targets:

| Request type | Credits |
| --- | --- |
| Standard page | 1 |
| Amazon, Walmart, eBay | 5 |
| Google or Bing (including subdomains) | 25 |
| LinkedIn | 30 |
| Bot-protection bypass (Cloudflare, DataDome, PerimeterX, Akamai) | +10 |
| JS rendering (`render=true`) | 10 |
| Premium proxy | 10 |
| Ultra premium | 30 |
| Geotargeting, sessions, device type, output format, auto parsing | 0 |

Turn that into postings and the spread is large:

| What you're fetching | Credits per 1,000 | Hobby ($0.49 / 1,000 credits) | Business ($0.10 / 1,000 credits) |
| --- | --- | --- | --- |
| Plain career-site pages | 1,000 | $0.49 | $0.10 |
| Rendered pages (`render=true`) | 10,000 | $4.90 | $1.00 |
| Rendered + bot-protection bypass (~20 credits) | 20,000 | $9.80 | $2.00 |
| LinkedIn job pages | 30,000 | $14.70 | $2.99 |

The Hobby rate is the most expensive credit on the sheet by a wide margin. Business brings it down to about $0.10 per 1,000 credits, Scaling to $0.095 and Advanced to $0.092. The drop happens at the Hobby-to-Startup step, so if a run needs more than 100,000 credits a month, check Startup's price before assuming Hobby scales with you. Going straight to Business for 150,000 credits is a waste of $250.

Here is how that compares with the per-row scrapers people usually weigh against it. These are different products: the Apify actors return parsed job records, ScraperAPI hands you the page and you write the parser.

| Option | Published rate | Per 1,000 postings | What the number includes |
| --- | --- | --- | --- |
| ScraperAPI Hobby (derived from credit price) | $49 per 100,000 credits | $0.49 plain, $4.90 rendered | Proxy pool, rendering, retries; parsing is yours |
| ScraperAPI Business (derived) | $299 per 3,000,000 credits | $0.10 plain, $1.00 rendered | Same, with country geotargeting |
| Apify Jobs Scraper (solutionssmart) | $0.01 per job | $10.00 | Platform compute and optional proxies billed separately; only saved verified rows charged |
| Apify Career Site Jobs Scraper (automly) | $1.00 per 1,000 on Free, falling to $0.70 on Business+ | $1.00 to $0.70 | Platform usage included; full descriptions cost $1.50 falling to $1.05 on Workday, SmartRecruiters and BambooHR |
| Apify SmartRecruiters jobs search | $2.50 per 1,000; $3.50 with details | $2.50 to $3.50 | Vendor's own listing |
| JobSpy | Free, MIT licensed | $0 plus your proxies and your time | Self-hosted Python library |

Read the middle column as four different billing models, not four quotes for the same job. One charges per saved row, one per request, one per row plus compute, one is free because you run and maintain it.

## Why you won't get every posting

### Workday breaks the obvious loop in three places

Workday boards are the most common target and the easiest to underestimate. The endpoint is public: `POST https://nvidia.wd5.myworkdayjobs.com/wday/cxs/nvidia/NVIDIAExternalCareerSite/jobs` with a body of `{"limit":20,"offset":0,"searchText":"","appliedFacets":{}}` returns clean JSON. Three things then go wrong.

**`limit` is capped at 20.** Ask for 50 and Workday answers with HTTP 400 and an empty error message. You page in twenties whether you like it or not.

**`total` is only real on the first page.** NVIDIA reports 2,000 at offset 0 and 0 at offset 20. A loop written as `while offset < total` reads one page, stops, and reports success. You end up with 20 postings and no error in the log.

**The board URL can't be derived from the company name.** Host label, data centre (`wd1`, `wd5`, and so on) and site name are all the employer's choice. There is no rule that turns "Wells Fargo" into a working endpoint. Any tool that claims to take a company name is carrying a map of boards it has already read real postings from.

Two more things cost you time rather than correctness. List rows carry no description and give the date as a phrase like "Posted 30+ Days Ago"; the full posting is one more GET per job. And Workday reports 2,000 for any board larger than that, so getting the rest means slicing by category, or leaning on Workday's own keyword and location search.

This is the real fork between buying and building. A paid actor that ships the board map and refuses to guess outside it saves you weeks of assembling that map. ScraperAPI gives you the fetching layer and leaves the map to you.

### The 1,000 and 2,000 result caps

Most job board endpoints return around 1,000 results for a given search. Workday's ceiling is 2,000. Anything past those numbers has to be sliced by category, location or keyword, and the quality of your dataset is really the quality of your slicing.

### Rate limits set your wall-clock time

Indeed is currently the least rate-limited of the big three. LinkedIn answers bursts of requests with a 429 that clears in about a minute. Glassdoor rate-limits above roughly 2 requests per second. With ScraperAPI, exceeding your plan's concurrency returns a 429 and the request is refused rather than queued, with no extra charge for the failed attempt.

Your thread count is therefore the throttle. A 20-thread Hobby plan and a 200-thread Scaling plan differ more in how long a full sweep takes than in what it costs, which matters if you want a nightly refresh to finish before your users wake up.

## Detail pages are the cost multiplier

Every scraper on this page charges extra for full descriptions, and the mechanisms are identical: one more request per posting. On ScraperAPI that's a plain 1-credit page, so 1,000 descriptions cost $0.49 on Hobby. On Apify's career-site actor it's a separate price band, $1.50 per 1,000 instead of $1.00. In JobSpy it's `fetch_description=True`, documented as adding one request per job.

Decide this before you pick a plan. Title, company, location and URL are enough for a job board that links out. Salary parsing, seniority tagging, deduplication by content, or training a matching model all need the body text, and that roughly doubles your request count.

👉 [Check the per-credit rates before you size a description-heavy run](https://www.scraperapi.com/pricing/?fp_ref=coupons)

## Coverage: which boards answer with plain JSON

Greenhouse, Lever, Ashby, Workday and SmartRecruiters expose public listing endpoints, so a plain HTTP request works and no browser is involved. That keeps you on 1 credit per page and off the rendering budget.

Employers on Oracle, Eightfold, SAP SuccessFactors, Phenom and Jibe don't. Marriott, Kroger and JPMorgan Chase sit on Oracle; Microsoft, Starbucks and Lockheed Martin on Eightfold; EY and Nestlé on SAP; UPS and Eli Lilly on Phenom; Costco on Jibe. If your target list mixes these in, some pages will need `render=true` at 10 credits, and the per-1,000 cost above stops being the friendly number.

Company-name resolution is a real convenience when it exists: over 3,000 employers can be found on Workday by name. It comes with a caveat. An empty Workday board and a wrong board id look the same from outside, so a tool can only report the error, never "this company isn't hiring".

Indeed and Glassdoor have no public API. Both aggregate from employer career pages, which means the source is both cheaper and fresher. LinkedIn is priced at 30 credits per request, the highest standard rate on the sheet, so 100,000 credits buys you about 3,300 LinkedIn postings and nothing else.

## When you shouldn't pay at all

A single employer's Workday board, a few hundred postings, one refresh a week: write the curl loop. The endpoint is public, there's no key, and the ten lines of Python are less work than reading a pricing page.

A one-off research pull of a few thousand postings: the free trial gives you 5,000 credits over 7 days with no card, which is enough to find out whether your target sites cost 1 credit or 20 before you commit.

LinkedIn and Indeed at small volume: JobSpy is MIT-licensed, scrapes eight boards concurrently into a single dataframe, and costs nothing but your proxy bill and the maintenance when a site changes its HTML.

Paying makes sense when your target list is long, mixed across ATS platforms, and refreshed on a schedule. That's when proxy rotation, rendering and retry logic stop being a weekend project.

## FAQ

**Is scraping job postings legal?**
Reading public career pages is the low-risk end of scraping. Every source here draws the same line: public pages only, no logins, no CAPTCHA solving, no bypassing access controls. Job pages sometimes carry a recruiter's name and contact details, which can bring the data under GDPR if you store it. Keep the fields you actually need.

**Can I scrape LinkedIn and Indeed?**
Indeed and Glassdoor have no public API, and both are downstream of employer career pages. LinkedIn is supported at 30 credits per request on ScraperAPI. Review each site's terms before building a product on its data.

**Why are posting dates missing or wrong?**
"Posted within N days" filters only look at jobs that publish a date; jobs with no date are typically kept, so an apparently fresh result set can contain old postings. Glassdoor filters by whole days and rounds up to the next one. Indeed's date is the day the job was added to Indeed, not necessarily the day the employer posted it. Workday's list rows give a relative phrase, and the exact date needs the detail request.

**How do I dedupe across runs?**
Use the employer's requisition id. Workday's `jobId` stays constant across runs, so a scheduled job can separate new postings from ones already in your table. Where no id is exposed, hash the canonical URL.

**What happens when credits run out?**
Scraping pauses until renewal. Balances don't roll over. Auto-upgrade moves you up a plan automatically if you've opted in, and pay-as-you-go at a fixed per-credit rate is available on Scaling and above.

**Is there a refund?**
Yes, 7 days, no questions asked.

## Which plan, by situation

- **A few hundred postings from one or two employers** → write the script, or use the free plan's 1,000 credits a month.
- **A one-off pull of a few thousand** → the 7-day trial with 5,000 credits.
- **A recurring pipeline from company career sites, up to about 95,000 postings with descriptions** → Hobby at $49/month.
- **Country-level geotargeting, or analytics older than 30 days** → Business at $299/month, which also drops your per-credit cost by about 80%.
- **LinkedIn-heavy or render-heavy work** → do the credit math first. At 30 credits per LinkedIn page, 100,000 credits covers 3,300 postings and no more.

Two things to confirm before you pay. First, what your specific target domains cost: the Domain Cost Estimator in the dashboard quotes a URL's credit cost, every response returns an `sa-credit-cost` header, and `max_cost` caps any single scrape. Second, whether you're buying requests or results, because ScraperAPI sells requests. Budget for the listing pages, the detail pages and the retries instead of assuming one credit per posting.

👉 [Compare the plans and start with 5,000 trial credits](https://www.scraperapi.com/pricing/?fp_ref=coupons)
