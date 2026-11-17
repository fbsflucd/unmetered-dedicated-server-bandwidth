# Unmetered Dedicated Server: What the Label Really Means, What a 10Gbps Port Costs at RackNerd, and When Metered Bandwidth Is the Cheaper Buy

An unmetered dedicated server is priced by port speed rather than by gigabytes. You rent a fixed port (1Gbps, 10Gbps, 40Gbps) and anything that fits through it is yours to send for the month, with no per-TB line on the invoice. The ceiling is the port, not a traffic counter.

At RackNerd, the unmetered line starts at **$599/month for a dedicated 10Gbps port**. The same company rents a metered Xeon E3-1240 V2 with 32GB RAM and 30TB of monthly transfer for **$70/month**, or **$55/month** if you pay quarterly. That gap is the real decision, and most people searching this term don't need to cross it.

What follows is what unmetered does and doesn't cover, the RackNerd options I could price against a live source, the arithmetic that tells you which side of the gap you're on, and what to confirm before you pay.

> **Quick pick.** If you're moving under 30TB a month, RackNerd's metered Xeon plan at $70/month handles it, and quarterly billing drops that to $55/month. The 10Gbps unmetered tier at $599/month earns its price only when you've measured throughput a 1Gbps port can't carry, or you serve video, game, or CDN traffic with spikes you can't forecast.
> 👉 [Check RackNerd's current dedicated server pricing](https://bit.ly/RacKnerd)

## RackNerd dedicated server options and prices

| Option | Hardware | Port and transfer | Price | Order |
| --- | --- | --- | --- | --- |
| Unmetered, 10Gbps tier | Configured on the order page | Dedicated 10Gbps, unmetered | **$599/mo** | [Check the 10Gbps tier](https://my.racknerd.com/aff.php?aff=11397&pid=746) |
| Unmetered, 20Gbps tier | Configured on the order page | Dedicated 20Gbps, unmetered | Priced above the 10Gbps tier; shown at checkout | [See current port tiers](https://bit.ly/RacKnerd) |
| Unmetered, 40Gbps tier | Configured on the order page | Dedicated 40Gbps, unmetered | Priced above the 20Gbps tier; shown at checkout | [See current port tiers](https://bit.ly/RacKnerd) |
| Metered Xeon (Palworld-era spec) | Xeon E3-1240 V2, 4c/8t 3.40GHz, 32GB RAM, 240GB SSD | 30TB on 1Gbps, /29 IPv4 (5 usable), IPMI | **$70/mo** monthly, **$55/mo** billed quarterly | [Check the Xeon E3-1240 V2 plan](https://my.racknerd.com/aff.php?aff=11397&pid=837) |

RackNerd rotates the CPU, RAM, and drive attached to each port tier, and the exact spec for a given tier lives on the order page. I'd rather point you there than print a spec sheet that goes stale in a quarter. The metered plan above ships from New York, Los Angeles, Dallas, or Chicago, with month-to-month terms and no setup fee.

## What an unmetered dedicated server actually bills you for

Three terms get mixed together in provider marketing, and the difference costs money.

**Metered** means a fixed monthly transfer allowance. Go past it and you pay overage, get throttled, or both. The 30TB Xeon plan above is metered.

**Unmetered** means transfer volume isn't measured for billing purposes. You're charged for the port, and the port sets your maximum throughput. That's the definition worth memorizing: the transfer isn't counted, the speed is capped.

**Unlimited** means nothing precise. Providers use it loosely, and it usually hides a fair-use clause or a soft cap somewhere in the terms. When a host advertises "unlimited bandwidth," read the acceptable use policy before you read the price.

The practical consequence: an unmetered plan protects you from a surprise bandwidth bill, not from a traffic jam. If 5,000 concurrent viewers can't fit through your port, the fact that the transfer was free doesn't help you.

## Port speed is the real limit, and the math is simple

A 1Gbps port running flat out moves roughly 125MB per second, about 10.8TB per day, or **324TB in a 30-day month**. A 10Gbps port multiplies that by ten, to about **3.2PB per month**.

Almost nobody saturates a port for 730 hours straight. That's the point. A single 1Gbps unmetered port has more theoretical headroom than the vast majority of production sites will ever touch, which is why the jump to 10Gbps is about burst capacity and peak concurrency, not about raw monthly volume.

Here's where the marketing gets slippery. Many unmetered plans include unlimited inbound traffic but cap outbound at around 10TB, then bill per additional terabyte. Outbound is the direction that matters for a site serving images, video, downloads, or API responses to users. If a provider quotes "unmetered" without separating inbound from outbound, ask for the outbound figure in writing. A plan with unlimited inbound and a 10TB outbound ceiling is a metered plan wearing a different hat.

## What RackNerd's unmetered tier includes

The unmetered line is sold by port tier: 10Gbps at $599/month, then 20Gbps and 40Gbps above it. Ordering runs through locations in Los Angeles, New Jersey, London, and Montreal, and each location lists a test IP on the order page so you can ping or traceroute it from where your users actually sit before committing. That last detail matters more than most buyers expect. New Jersey and Los Angeles behave very differently for Asia-facing traffic, and no spec sheet tells you which is right for your audience.

Included with the server:

- Full IPMI/KVM access, so you can reinstall an OS, mount an ISO, and cycle power without opening a ticket
- Linux, Windows Server, FreeBSD, or a custom ISO noted in the order comments
- Bare-metal provisioning quoted at up to 72 hours, frequently same-day
- Root access on single-tenant hardware, not a wrapped VPS

The control layer is the part budget buyers underestimate. IPMI means a bad kernel or a broken network config is a twenty-minute fix from your desk instead of a support queue.

## Running the numbers: $599 unmetered vs $70 metered

RackNerd's metered Xeon plan works out to **$2.33 per terabyte** at 30TB for $70. At that rate, $599 buys about **257TB** of transfer. So on pure cost per terabyte, the unmetered tier doesn't pay for itself until you're consistently moving a couple hundred terabytes a month, or until a single traffic spike would trigger overages expensive enough to erase the difference. Ask RackNerd what the overage rate is on the 30TB plan; that number, not the base price, decides whether a viral day hurts.

Billing cycle is the other lever. Monthly billing on that Xeon plan runs $840 a year. Quarterly billing at $55/month runs **$660 a year**, a $180 saving for the same hardware and the same 30TB allowance.

The 10Gbps unmetered tier runs **$7,188 a year** at list. RackNerd has publicly listed a lifetime dedicated-server code, `15OFFDEDI`, which applied to that tier lands near **$509/month, about $6,110 a year**. Enter it at checkout and confirm the discounted total appears before you pay; promo codes get retired, and the order page is the only place that settles it.

👉 [Start a RackNerd order and test the discount at checkout](https://bit.ly/RacKnerd)

## Who should stay on metered bandwidth

Unmetered hardware costs more than equivalent metered hardware almost everywhere, and RackNerd's own lineup shows it. If your monthly transfer sits comfortably inside a 30TB allowance and your peaks are predictable, the $599 tier is $529 a month for capacity you won't touch. That's $6,348 a year spent on insurance against a spike you could have handled with a CDN in front of the box.

Cases where the metered plan stops working:

- Sustained outbound above roughly 30TB, with overage pricing that turns ugly fast
- Live video, IPTV, or game distribution where a single event triples your normal traffic
- Backup, mirroring, or replication jobs that move hundreds of terabytes on a schedule
- VPN, proxy, or file-delivery services where per-GB economics never made sense

Cases where it doesn't: a business site, a WooCommerce store, a SaaS app with a few thousand users, a media site that offloads video to a CDN. Those fit on metered, and the money is better spent on RAM.

## How RackNerd's port tiers compare with other providers

Port policy varies wildly between hosts, and it changes the real price of "unmetered" by a lot.

| Provider | Port policy on unmetered plans | Published starting point |
| --- | --- | --- |
| RackNerd | Sold by port tier: 10Gbps entry, 20Gbps and 40Gbps above it | $599/mo for 10Gbps |
| ServerRoom | 1Gbps port included on most lines; 10/20/100Gbps sold as paid upgrades | $62.58/mo for a Xeon E3-1585L v5, 32GB, 240GB NVMe on 1Gbps |
| Rackdog | 10Gbps standard on most configurations, options up to 400Gbps | Pricing not published in the material reviewed |
| OVHcloud | Unmetered bare metal with fixed port speeds, hourly billing available | Pricing not published in the material reviewed |

The ServerRoom row is the one to study. A $62.58 monthly price with a 1Gbps included port is a completely different product from a $599 10Gbps port, and comparing the two headline numbers tells you nothing. Check what port is actually in the box before you compare anything.

## Before you order, confirm these

1. **Port speed in the base price.** Not the maximum the provider offers, the one attached to the price you're paying.
2. **Inbound vs outbound treatment.** Unlimited inbound with a capped outbound allowance is common.
3. **Overage rate** if you're choosing a metered plan, since that's the number that decides whether a spike is survivable.
4. **Fair-use language** in the acceptable use policy, especially around sustained saturation.
5. **Extra IPv4 pricing** and whether a /29 is already included. RackNerd includes a /29 with 5 usable IPs on the Xeon plan above.
6. **Windows licensing.** Windows Server installs are available; confirm whether the licence is bundled or billed separately.
7. **Deployment window and SLA terms.** Up to 72 hours is the quoted ceiling at RackNerd, frequently same-day. Get the SLA specifics for your location in writing rather than assuming a number from a marketing page.

## FAQ

**Is an unmetered dedicated server truly unlimited?**
No. Transfer isn't counted for billing, but the port caps throughput and fair-use policies can constrain sustained saturation. Treat "unmetered" as "no per-GB charges" and "unlimited" as a marketing word.

**Is the 10Gbps port included in the $599 price?**
Yes on RackNerd's 10Gbps tier; the port is the product. Other hosts bundle 1Gbps and sell 10Gbps as an upgrade, which is why the entry prices across providers aren't comparable.

**Can I upgrade the port later without moving hosts?**
RackNerd sells 10Gbps, 20Gbps, and 40Gbps tiers, so moving up means moving tiers. Confirm lead time and pricing with sales before you build around the assumption.

**How fast does a RackNerd bare-metal server come online?**
Up to 72 hours quoted, often same-day. You get IPMI credentials, root login, and IP assignments by email once it's live.

**Can I install my own OS?**
Linux distributions, Windows Server, FreeBSD, and custom ISOs noted in the order comments are supported.

**Does unmetered cover DDoS traffic?**
Filtered attack traffic isn't the same as legitimate transfer, but the treatment varies. Ask directly if you're a frequent target.

## Which one to buy

Under 30TB a month, predictable peaks, a normal website or app: **the metered Xeon E3-1240 V2 at $70/month**, billed quarterly at $55/month if cash flow allows. You get 32GB of RAM, a /29, and IPMI for $660 a year.

Sustained hundreds of terabytes, live video, game backends, or replication jobs where a 1Gbps port is the actual bottleneck: **the 10Gbps unmetered tier at $599/month**, with `15OFFDEDI` entered at checkout. That's a $7,188 list price buying a port, not a transfer quota, and it's the right purchase only after you've measured the throughput you need.

Before you pay either way, open a ticket and ask two questions: what's the outbound allowance on the plan I'm buying, and what does an extra terabyte cost if I go over. The answers decide more than the headline price does.

👉 [Compare RackNerd's current dedicated server plans and port tiers](https://bit.ly/RacKnerd)
