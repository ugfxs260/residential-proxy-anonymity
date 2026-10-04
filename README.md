# anonymous proxies: which type actually hides you, what a residential IP really costs, and how to test one before you pay

Two different people type "anonymous proxies" into a search bar. One wants a website to stop knowing their real IP. The other has a scraper that keeps dying at the IP layer. Both end up on the same free-proxy listicles, and both get the same useless answer.

The terminology is half the problem. In the technical sense, an *anonymous proxy* is the middle rung of a three-level ladder — weaker than most buyers assume. In marketing, "anonymous proxy" means "we hide your IP address." Those are not the same claim, and the gap between them decides whether what you buy does what you think it does.

## The three anonymity levels, and which one you're actually buying

Proxy anonymity is decided by the HTTP headers a proxy attaches when it forwards your request. Three levels:

- **Transparent** — passes your real IP in `X-Forwarded-For` and announces itself as a proxy. Zero privacy benefit. It exists for corporate caching and filtering, not for you.
- **Anonymous (level 2, sometimes called "distorting")** — hides your real IP, but the request still carries a `Via` or forwarded header telling the destination a proxy was used.
- **Elite / high-anonymity (level 1)** — strips those headers entirely, so the request looks like a normal direct visit.

Level 2 sounds fine until you consider that plenty of sites treat "a proxy is involved" as a risk signal on its own. The IP might be clean, the request is still flagged.

Here's the part that saves you money: **the level is not usually a product you choose.** Free proxy lists tag each IP as L1/L2/L3 and are frequently wrong about it. Paid residential, ISP and mobile providers ship high-anonymity proxies by default, because that's what their customers need to keep working. So when a provider sells you "anonymous proxies," what actually determines whether you get blocked is the *type* of IP and its reputation — not the anonymity level printed on the marketing page.

### How to verify it instead of believing it

Three steps, and only the third one counts:

1. Ignore the label. Almost every provider advertises anonymity, and the label tells you nothing about header behaviour.
2. Look for wording like "high-anonymity," "elite," or "does not leak your IP" — then treat it as a claim.
3. During the trial, send one request through the proxy to a header-echo page such as `httpbin.org/headers` and read what the destination actually received. If `X-Forwarded-For` or `Via` shows up, you have a level-2 proxy.

That test takes two minutes and settles a question that review sites argue about for paragraphs.

## What anonymous proxies can't hide

Even a clean elite proxy leaves three parties with a view of you.

**Your ISP** sees that you connect to the proxy's IP address — plus timing and volume metadata. It can't read HTTPS traffic inside the tunnel, but the connection record exists and your proxy's anonymity properties don't apply to it.

**The destination site** can still fingerprint your browser. Canvas rendering, WebGL, installed fonts, time zone, language settings and screen resolution identify you across sessions even when your IP changes every request. Proxies move IPs; they do nothing about fingerprints.

**The proxy operator** sits in the middle of everything you send. It knows your real IP from the client connection and the destinations you requested. Elite anonymity hides you from websites. It doesn't hide you from the provider. Which means the provider's logging policy and jurisdiction matter more than its IP pool size, and that's a question worth asking before you pay anyone.

Anti-bot systems also score behaviour, not just headers: request rate, mechanical timing, missing browser headers. A perfect IP with robotic request patterns still gets flagged, which is why rotation settings and realistic headers do as much work as the proxy tier itself.

## Free anonymous proxy lists vs a paid residential pool

Free lists aren't a scam so much as a bad trade. The comparison below reflects the pattern across public proxy lists versus paid residential networks:

| Criteria | Free proxy lists | Paid residential pool |
| --- | --- | --- |
| IP block rate | High — IPs are already blocklisted on major WAFs | Low — ISP-assigned IPs look like real users |
| HTTPS support | Often missing, exposing auth headers | Standard |
| Latency | High, shared and overcrowded | Low, dedicated infrastructure |
| Uptime | Unpredictable | 99%+ from reputable providers |
| Security | Malware injection, traffic logging | Audited infrastructure, clearer policies |
| Real cost | Engineer hours rebuilding after bans | Predictable per-GB or per-IP pricing |

The hidden line item is your time. Working around bans on a free list is an ongoing job, and the IPs on those lists are pre-burned on exactly the targets you care about — search engines, marketplaces, social platforms. Free proxies are fine for learning what a proxy is. They're not infrastructure.

## Where 9Proxy fits in

9Proxy is a residential proxy platform that has been around since 2023, built on a pool of 20M+ residential IPs across 90+ countries, with over 8,000 servers behind it and a claimed 99.95% uptime. It speaks HTTP(S) and SOCKS5, which means SOCKS5-native tools — anti-detect browsers, proxychains, Python scripts — connect without protocol gymnastics.

The features that map onto the anonymity question:

- Targeting down to country, state, city, ZIP code and ISP level, which is what you need when localisation determines what the site shows you.
- Both sticky sessions (hold one IP across many requests — necessary for logged-in or multi-step flows) and per-request rotation.
- Two authentication paths: username/password sub-users, or IP whitelisting if you'd rather not manage credentials.
- Payment via cards, crypto (USDT, BTC, ETH, LTC, DOGE and others), Alipay, Apple Pay and Google Pay.

Two billing models, and picking the wrong one is the most common way people overpay:

**Residential by IP** — you buy a fixed number of IPs and get unlimited bandwidth on each while it's active. Each IP lives anywhere from a few hours to around 24 hours (users frequently report roughly three hours in practice). Unused IPs don't expire, so a balance you don't burn today is still there next month. This model needs the Windows desktop client, which forwards ports locally so any application can use the connection.

**Residential by GB** — you buy traffic and generate as many endpoints as you want, straight from the dashboard, with no app involved. All GB plans carry 180-day validity. This is the model for high-rotation work where each request moves little data: SERP checks, ad verification, price monitoring, API polling.

👉 [Open a 9Proxy account and compare the two models against your own workload](https://bit.ly/9-Proxy)

If you arrive through an invite link or enter the code at signup, the account gets 5% off purchases — that's the referral discount 9Proxy publishes as part of its affiliate program.

## The full plan list, with prices

Everything below is self-serve pricing in USD. One honest caveat first: 9Proxy's tagline advertises a floor of **$0.015 per IP and $0.68 per GB**, and those are volume floors, not entry prices. The smallest self-serve pack costs $0.20 per IP. The vendor has also adjusted these numbers before, so treat the ladder as a guide and confirm at checkout.

### Residential proxy by IP — pay per IP, unlimited bandwidth

| Package | Total price | Rate per IP | Validity | Buy |
| --- | --- | --- | --- | --- |
| 100 IPs | $20 | $0.20 | Unused IPs never expire | [Get the 100-IP pack](https://bit.ly/9-Proxy) |
| 500 IPs | $60 | $0.12 | Unused IPs never expire | [Get the 500-IP pack](https://bit.ly/9-Proxy) |
| 1,000 IPs + 500 bonus | $105 | $0.07 | Unused IPs never expire | [Get the 1,000 + 500 IP pack](https://bit.ly/9-Proxy) |
| 2,500 IPs | $175 | $0.07 | Unused IPs never expire | [Get the 2,500-IP pack](https://bit.ly/9-Proxy) |
| 5,000 IPs | $300 | $0.06 | Unused IPs never expire | [Get the 5,000-IP pack](https://bit.ly/9-Proxy) |
| 15,000 IPs | $600 | $0.04 | Unused IPs never expire | [Get the 15,000-IP pack](https://bit.ly/9-Proxy) |
| 25,000 IPs | $750 | $0.03 | Unused IPs never expire | [Get the 25,000-IP pack](https://bit.ly/9-Proxy) |
| 50,000 IPs | $1,250 | $0.025 | Unused IPs never expire | [Get the 50,000-IP pack](https://bit.ly/9-Proxy) |

The 1,000 + 500 bonus pack is the tier 9Proxy itself flags as most popular, and the maths supports it: it's the first rung where the per-IP price drops below ten cents without a five-figure commitment.

### Residential proxy by GB — pay per GB, unlimited endpoints

| Package | Total price | Rate per GB | Validity | Buy |
| --- | --- | --- | --- | --- |
| 5 GB | $15 | $3.00 | 180 days | [Get the 5 GB pack](https://bit.ly/9-Proxy) |
| 50 GB + 5 GB bonus | $105 | $2.10 | 180 days | [Get the 50 + 5 GB pack](https://bit.ly/9-Proxy) |
| 100 GB | $150 | $1.50 | 180 days | [Get the 100 GB pack](https://bit.ly/9-Proxy) |
| 200 GB | $200 | $1.00 | 180 days | [Get the 200 GB pack](https://bit.ly/9-Proxy) |
| 1,000 GB | $800 | $0.80 | 180 days | [Get the 1,000 GB pack](https://bit.ly/9-Proxy) |
| 2,000 GB | $1,500 | $0.75 | 180 days | [Get the 2,000 GB pack](https://bit.ly/9-Proxy) |

Rates continue downward at higher volumes, reaching the $0.68 per GB floor at the largest tiers. The 180-day window is the detail that matters for project work: you're not racing a 30-day clock to burn traffic you bought for a job that finished early.

### Bundles — IPs and bandwidth in one purchase

| Bundle | What's included | Price | Buy |
| --- | --- | --- | --- |
| Starter | 100 IPs + 5 GB | $30 | [Get the Starter bundle](https://bit.ly/9-Proxy) |
| Popular | 1,500 IPs + 50 GB | $180 | [Get the Popular bundle](https://bit.ly/9-Proxy) |
| Pro | 5,000 IPs + 500 GB | $720 | [Get the Pro bundle](https://bit.ly/9-Proxy) |

Bundles exist for mixed workloads — some tasks want a stable exit for a session, others want a fresh IP per request. Bundle tiers get reshuffled more often than the two main ladders, so check current contents before assuming.

### Enterprise, and what's still coming

The Enterprise program is priced on request and differs in kind rather than degree: unlimited data validity instead of 180 days, team mode with one owner and up to five members, no-expiration bandwidth sharing inside the team, per-member traffic controls, full activity logs and VIP support. A datacenter proxy line is listed as upcoming, with nothing buyable yet — and worth noting that datacenter IPs are the wrong tool for anonymity anyway, since their address ranges are traceable to cloud hosts and get flagged fast.

## Setting it up and proving it works

1. Create the account through the invite link so the 5% discount applies, then pick IP-based or GB-based.
2. For GB-based, go straight to the dashboard: **Residential Proxies → GB → Proxy Generator**. For IP-based, download the Windows client and activate your share code in the dashboard first, or the balance won't appear.
3. Choose authentication — username/password sub-users or IP whitelisting.
4. Set targeting (country, state, city, ZIP, ISP) and session mode — sticky with a fixed duration, or rotating per request.
5. Export as `.txt` or `.csv`, or copy a code sample in your language of choice from the generator.
6. Run the header test from earlier against `httpbin.org/headers` and confirm nothing identifying leaks.
7. Then test your actual target, not a demo page. Success against Cloudflare-protected pages sits around 97.7% in one 2026 review — respectable at this price point, but your target is the only number that matters.

On mobile: there is no official 9Proxy Android app, and any "9Proxy APK" floating around on download sites is repackaged malware — at best a credential stealer. Phone access goes through the IP2Web browser panel instead, no installation required.

## Limits and caveats worth knowing before you pay

- **IP lifetime is short by design.** Residential IPs come and go with the real devices behind them, so an IP-based session can end after a few hours. If a proxy fails within 60 seconds of activation, 9Proxy credits it back automatically — unusually generous, since most providers count a dead connection as consumed.
- **No monthly subscription.** You buy balances, not seats, which suits intermittent work and hurts anyone wanting a flat predictable bill.
- **The trial is limited and availability-dependent.** Support offers trial access to new users on request rather than an unlimited free tier, and forum giveaways of small IP batches have appeared around promotions.
- **Service history is part of the picture.** 9Proxy went down at the end of June 2026 and stayed unreachable for weeks — official channels went mostly quiet — before resurfacing in August 2026. Third-party reviews and reseller reports both describe the recovery, so the service is live, but the episode is a legitimate reason to test before you build a pipeline on top of any single provider.
- **User feedback is mixed, and it splits along use case.** Reviews cite stable connections at a low price, particularly alongside anti-detect tools like Dolphin Anty and AdsPower, while forum users rate it as average for general browsing and poor for streaming — which is unsurprising, since residential proxies are built for data work, not unblocking Hulu.

## Quick answers

**Are 9Proxy's residential IPs anonymous or elite?** Residential IPs come from real ISP-assigned devices, so they don't announce proxy use the way a datacenter range does. Confirm header behaviour with the `httpbin.org/headers` test during your trial rather than trusting any provider's label — including this one.

**Do I still need a VPN or an anti-detect browser?** A VPN and a proxy solve different problems, and neither fixes browser fingerprinting. If your threat model includes fingerprint-based tracking, you need a browser-level tool on top of the proxy.

**Cheapest way to check the fit?** Spend $15 on the 5 GB pack if your work is rotation-heavy, or $20 on 100 IPs if you need one stable exit per session. Both cost less than an afternoon of fighting free proxy lists.

**Which model for scraping?** GB-based when each request moves little data and you want a fresh IP constantly. IP-based when bandwidth is unpredictable and sessions need to survive longer than a single request.

👉 [Start with the free trial request or the $20 entry pack at 9Proxy](https://bit.ly/9-Proxy) — and remember the invite code takes 5% off whatever you end up buying.
