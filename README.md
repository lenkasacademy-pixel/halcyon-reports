# Halcyon Pain Management — Meta Ads calls report

Client-facing report for **Halcyon Pain Management**, covering **both** ad accounts:

| Account | ID | What it runs |
|---|---|---|
| Pallavi Halcyon | `1999324147481098` | Call ads + website-lead campaigns |
| Pallavi Kiran | `694358492762548` | Call ads only |

Live: https://lenkasacademy-pixel.github.io/halcyon-reports/

A single self-contained `index.html` with a **month tab bar** (August /
September / October). Figures are baked into the `DAILY_AUG` / `DAILY_SEP` /
`DAILY_OCT` arrays and the `MONTHS` object near the bottom of the file — nothing
calls the network.

**Scope: three tabs.** August 2026 (1–31, complete), September 2026 (1–30,
complete) and October 2026 (1–29). October stops at the last complete day — Meta
keeps revising the most recent ~48h, and the live part-day moves between calls
minutes apart. Showing it would read as a collapse in spend that is not real.
The range under each tab name is read off that month's own `DAILY_*` rows at
load, so it cannot drift from them.

## What it shows

- Amount spent, phone calls placed, blended cost per call, reach.
- A three-panel day-wise chart on one shared calendar: daily spend stacked by
  account (with the website-lead spend split out), calls placed stacked by
  account, and cost per call against that period's average. One hover reads all three.
- A two-up comparison card carrying each tab's headline finding (August's
  1–9 vs 10–31 split; September against the August average).
- A **call-quality funnel**: placed → 20s+ → 60s+, with each step's share of
  placed calls and its true cost.
- Per-campaign totals for the call campaigns and, separately, the website-lead
  campaigns.
- Calls and cost per call by age band, both accounts combined.
- The full day-by-day table for the selected month.

## Snapshot

Frozen **30 Oct 2026, 8:15 am IST**. **September is now closed** (1–30) and
**October is a new tab** (1–29). 30 October is the live part-day and is excluded.

> **The part-day is not a theory.** Pallavi Halcyon's 29 October read ₹667.99 at
> campaign level and ₹668.02 at account level minutes later; 30 October moved
> ₹157.02 → ₹163.52 and 1,528 → 1,586 impressions across the same gap. One
> campaign's figure (`094906 31010 | Daily 500`) moved ₹67.35 → ₹67.49 → ₹96.27
> across three pulls. That is why the last day never sets a headline.
>
> **September's two missing days were its two biggest.** 29 Sep (₹11,858) and
> 30 Sep (₹10,817) on Pallavi Halcyon, 167 + 116 calls at ₹55 and ₹68 — cheap
> enough to pull the month's cost per call down from the ₹69.65 published on the
> 29th to **₹69.07**.
>
> **Only one earlier day was revised.** 28 September settled **₹21.14 higher**
> (₹18.45 call, ₹2.69 web, +293 impressions, +4 link clicks, +119 reach); no call
> count moved. Days 1–27 came back identical to the published figures.
>
> **A campaign was renamed at Meta on 6 October.** `120255796887700348` went from
> `Halcyon | Call 8585072072 | TS only | All days` to
> `Halcyon | Call 094906 31010 | TS only | All days` (activity log,
> `event_category: "campaign"`, 10:14 am, Power Editor). Both months now show it
> under the current name, with the old name called out in the September copy.
> **Flag for a human:** two campaigns now name the 9490631010 line and none names
> 8585072072. If the phone number on the ad actually changed, September's 117 calls
> and October's 371 on that id are measuring two different lines.

| | August (1–31) | September (1–30) | October (1–29) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,62,822.47 |
| Calls placed | 5,144 | 4,539 | 1,786 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.33** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 429 (24.0%) · ₹288.63 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 167 (9.4%) · ₹741.45 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,12,081.63 / 1,692 / ₹66.24 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 |
| Website-lead spend | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹38,999.76 / 211 |
| De-dup reach (PH / PK) | 11,39,310 / 6,12,279 | 8,00,412 / 8,37,451 | 8,30,550 / 90,931 |

(The September and October account rows are **call spend only**; website-lead
spend sits outside them, in its own row. August's Pallavi Halcyon row is total
spend, its cost per call call-only — that inconsistency is in the August figures
as published.)

Previous cut (1–28 Sep, published 29 Sep): ₹3,04,514.33 · 4,256 calls · ₹69.65.

All figures are **ex-GST** (Meta bills 18% GST on top in India). Unlike
`o2-reports`, this page does not show a GST-inclusive billed total — if the
client asks for one, add it, don't silently change the per-call numbers.

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across 1–28 Sep.

**September, closed (1–30).** ₹69.07 a call, 15% above the August average,
tracking August's second half (₹72.36). The month improved as it went: **₹70.24
over 1–22, ₹65.99 over 23–30**, and the two closing days were the cheapest pair
of the month (₹55 on the 29th, ₹68 on the 30th) on the heaviest spend.

The gap is one account: Pallavi Halcyon ₹58.81 a call, Pallavi Kiran ₹76.94 on
₹1,97,583 against ₹1,15,915. `ad set level 3 camp` remains the standout at
**₹45.77** across 1,102 calls; the archived `4 Numbers` campaign did 469 calls at
₹67.68, cheaper than `Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two
dearest lines, `New Leads Campaign` (₹95.69) and its copy (₹94.47), both stopped
by the 23rd.

**The four per-number campaigns now have three days** (28–30 Sep): ₹21,528.69,
**347 calls at ₹62.04** — better than the month average and better than the
₹65.41 the one-day read suggested. `094906 31010` was the best at ₹46.62,
`7788091092` the worst at ₹104.71. The 28 Sep-only figures published last cut
(₹43.29 on 8585072072 etc.) were a single day and are superseded.

**October (1–29) is two different months, and the blended ₹69.33 hides both.**

| | spend on call ads | calls | each |
|---|---|---|---|
| 1–8 Oct | ₹62,868.59 | 889 | ₹70.72 |
| **9–16 Oct** | **₹26,833.97** | **587** | **₹45.71** |
| 17–21 Oct | ₹0 | 1 (late) | — |
| **22–24 Oct** | **₹33,901.95** | **301** | **₹112.63** |
| 25–28 Oct | ₹0 | 0 | — |
| 29 Oct | ₹218.20 | 7 | ₹31.17 |

1–16 October at **₹60.77** is the cheapest stretch on this account since the first
nine days of August. The cause is one campaign:
`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each` (`120255979446760348`),
created 9 Oct, which bought **525 calls at ₹37.11** on roughly ₹1,800 a day — the
cheapest line on either account since August's ₹19.60 `Age 35+ | FB only | CBO`
(still at ₹0.00 in both months; the restart recommendation stands). It was paused
21 Oct, reactivated 24 Oct 5:55 am and paused again 8:08 am the same morning.

**Eight days of October are completely dark** — 17–20 and 25–28, no spend and no
impressions on either account — and the restart on the 22nd cost **two and a half
times** the settled rate. Whatever is stopping and restarting this account now
costs more than any targeting decision on it. **That is the first thing to find
out.** Do not read the ₹18-a-call 16th or the ₹31-a-call 29th as cheap days: they
are near-dead days booking calls earned before them (same guard as the
`elixir-reports` "cheapest day" footnote).

**Call quality fell with the stoppages** — 24.0% past 20 seconds and 9.4% past a
minute, the weakest both ways since this report began. **The minute-long call has
now risen at every single refresh:** ₹497 → ₹503 → ₹512 → ₹526 → ₹543 → ₹546 →
₹565 → ₹572 (Sep) → **₹741.45** (Oct). The cheap campaign is the short-call
campaign: the ABO line books a 20-second call for ₹172.41, the best on the
account, but only 5.3% of its calls reach a minute.

**Website-lead spend is now a quarter of the budget** — ₹38,999.76, 24% of
October, on fourteen delivering days against three in September. Both October
campaigns optimise the same custom conversion, so those two counts are comparable
with each other (₹184.83 blended, against September's ₹184.41) but still not with
the HContacted rows on the August and September tabs.

**Four new daily-budget campaigns went live on 29 October** at 9:40–9:44 am (three
call lines at ₹500/day, one Enquiry LP at ₹1,000) while the "All days" versions
were paused. Between them: **₹668 and seven calls** — nothing to judge yet. A
fifth, `Halcyon | ABO | Calls | 6 numbers | 500 each | Telangana regions`, was
created 26 October and **has never delivered**.

**Pallavi Kiran is now a rounding error** — ₹11,741.08 across 5–9 October for 94
calls at **₹124.91**, nearly double Pallavi Halcyon's ₹66.24, and nothing since.
`Calls | ABO | Hyderabad | Ara + Top Performers` (`120251497637820425`) is new on
that account and is the dearest call placed anywhere on this report (₹126.34).


## 20s and 60s calls are derived, not reported

There is **no count field** for call duration. Meta returns only an average cost
per connect, so each figure is:

    calls20s = spend / cost_per_action_type:click_to_call_native_20s_call_connect
    calls60s = spend / cost_per_action_type:click_to_call_native_60s_call_connect

**Every division must land on a whole number** — that is the check that the
derivation is sound. Assert it; if one does not, something is wrong. (Confirmed
for all 15 campaign-periods in the current data.) Same method as `o2-reports`.

A day with spend but no `click_to_call_native_60s_*` key genuinely had zero
60-second calls — record 0, do not treat the missing key as an error.

These are derived **per campaign per period**, which is why they appear in the
funnel and the campaign table but not in the day table. Daily duration figures
are possible but need one `cost_per_action_type` pull per account per month with
`time_increment` — large responses, so expect them to spill to a file.

Watch the quality/price trade: `Halcyon | Calls — Age 35+ | FB only | CBO` has
by far the cheapest placed calls (₹19.60) **and** the cheapest 20s calls
(₹91.32), but the worst 60s rate of any campaign (3.4%) — its calls skew short,
so the headline number flatters it. In September, `7788- call ads-new` is the
one to watch: 132 calls, only 8 past 60 seconds, at ₹1,825 each.

## Two result types — do not merge them

**Call campaigns** report `results` with indicator
`actions:click_to_call_native_call_placed` ("Phone calls placed"). There is no
queryable `calls` field — `ads_get_field_context` returns `calls`,
`call_confirm` and `click_to_call_*` as unknown. Same trap as `o2-reports`.

**Website-lead campaigns** (Pallavi Halcyon only, from 10 Aug) each optimise for
a *different* pixel event, so their counts are **not one comparable number**:

| Campaign | Event |
|---|---|
| `Halcyon \| LP 8585 \| Website Leads` | `HContacted` |
| `Halcyon \| LP 7788 \| Website Leads` | `HContacted` |
| `Halcyon \| LP 8585 \| Website Leads \| 7788` | `HEnquiry` |
| `Halcyon \| LP 8585 \| Website Leads \| TEST - Copy` | `offsite_conversion.fb_pixel_lead` |
| `Halcyon \| Enquiry LP \| Contact-good lead \| Mon–Sat 9–5` | `offsite_conversion.custom.1564834054962652` |
| `Halcyon \| Enquiry LP \| Contact-good lead \| Daily 1000` | `offsite_conversion.custom.1564834054962652` |

The two Enquiry LP campaigns are the only pair on the account that share an event,
so their counts are comparable with each other and with nothing else.

The page names the event on every row and keeps this spend **out of cost per
call**. Blending it in reads ₹70.38 for August, ₹72.09 for September and
₹91.17 for October, and overstates what a call costs — don't.

## Refreshing

`DAILY_AUG` / `DAILY_SEP` rows are
`[day, a1CallSpend, a1Calls, a1WebSpend, a1WebLeads, a2CallSpend, a2Calls, impressions, reachSum, linkClicks]`
where `a1` = Pallavi Halcyon, `a2` = Pallavi Kiran. `day` is the day of month.

Everything else a tab shows — headline totals, narrative copy, campaign tables,
age rows — lives in the `MONTHS` object keyed `aug` / `sep`. **To add a month,
add a `DAILY_*` array and a `MONTHS` entry, then add one `<button class="tab">`
with a matching `data-month`.** Nothing else is month-specific.

Pull with Meta MCP `ads_get_ad_entities`, `level: "campaign"`,
`time_increment: "1"`, one call per account.

- **Include ARCHIVED and DELETED campaigns in the listing.** An unfiltered
  campaign listing silently omits them. On 28 Sep this made ₹31,740.53 of Pallavi
  Kiran spend look like a Meta data gap for six days; it was an archived campaign.
  Filter `effective_status IN ["ACTIVE","PAUSED","ARCHIVED","DELETED",...]`.
- **Watch the 200-row cap on daily pulls.** 11 campaigns × 28 days returned
  exactly 200 rows and dropped the last campaigns. Split the `object_ids` so
  each call stays under 200 campaign-days, and check every id came back.
- **List all campaigns for the window first, every single refresh.** On the
  20 Sep pull, `New Leads Campaign – Copy` had appeared on Pallavi Kiran and was
  spending ₹1,318–₹2,346 a day; fetching only the known `object_ids` left the
  campaign sums ₹3,664.41 short of the account's own daily total. The account
  reconciliation is what caught it — it is not optional.
- **Fetch by `object_ids`, not by listing all campaigns.** Pallavi Halcyon has
  ~45 campaigns and Pallavi Kiran ~91; Meta returns a row for every campaign ×
  every day, almost all empty, which blows past the row cap and silently drops
  campaigns. Query the month at campaign level first to find which campaigns
  actually spent, then re-fetch only those ids with `time_increment`.
- **An unfiltered daily pull does not merely truncate — it can come back
  zeroed.** On 30 Oct, Pallavi Kiran 1–12 Oct without `object_ids` returned all
  91 campaigns × all 12 days (1,092 rows, nothing dropped) with **every metric
  zero**, while the same window restricted to the two spending ids returned the
  real ₹11,741.08. Nothing in the response says it is wrong. The account
  reconciliation is the only thing that catches it, which is why it is not
  optional.
- **A campaign with zero spend can still carry results.** `Halcyon | LP 8585 |
  Website Leads` (`120255040991190348`) has ₹0.00 and **4 HContacted conversions
  on 1 Sep** — a lagging pixel event from its August run. Filtering the campaign
  listing on `amount_spent > 0` drops it and loses four website leads out of the
  month. List once with no spend filter and keep any campaign whose `results`
  is non-empty, then pull its days separately.
- **Do not sum daily 20s/60s counts to get the period figure.** September's
  Pallavi Halcyon 20-second calls come to 480 added up day by day and **482**
  from the per-campaign period pull; the age breakdown independently gives 482.
  `calls20` / `calls60` are per-campaign-period values, cross-checked against
  the age breakdown — the day rows have no duration columns for this reason.
- The daily response for 5 campaigns × 31 days already exceeds the tool's output
  limit and gets spilled to a file — parse it with `jq`/python, don't try to read
  it inline.
- **Always reconcile.** Pull `level: "ad_account"` with `time_increment: "1"` for
  the same range and assert the campaign sums equal the account's own daily spend
  *and* impressions for every day. On the August pull both accounts matched to
  the rupee on all 31 days — that check is what proves no campaign was missed. It
  also earns its keep: on the September pull it flagged a ₹28.35 gap on the part-day
  that turned out to be Meta still settling, not a dropped campaign.
- Age figures come from a separate call with `breakdowns: ["age"]` (no
  `time_increment`). Assert each campaign's age rows sum to its month total.
  ₹1.93 and 1 call land in an `Unknown` band and are omitted from the age table.
- `reachSum` is the sum of each day's reach and double-counts people across days.
  Meta's de-duplicated August reach was 11,39,310 (Pallavi Halcyon, frequency
  2.68) and 6,12,279 (Pallavi Kiran, frequency 3.25); September 1–28 is 7,00,847
  (2.37) and 8,37,451 (3.09) — those come from a call *without* `time_increment`
  and are quoted in the footer only.
- The `reachSum` column is **each account's own daily reach, added together** —
  two numbers, not a sum over campaigns. September days 1–10 were originally
  built from campaign-level reach, which double-counts within an account and ran
  5–9k a day high; they were rebuilt from the account pull on 18 Sep so the
  column means one thing down its whole length.
- Recent days keep settling for ~48h; re-pull the whole month rather than
  appending.
- `campCalls` rows are
  `[name, account(1|2), daysLive, spend, callsPlaced, calls20s, calls60s]`. The
  account flag drives the colour dot — keep it correct when adding rows, and keep
  each month's `calls20` / `calls60` totals equal to the sum of its rows.
## Mobile

The page is built to work at 320–430px, and there are a few rules to keep:

- **Tables pin their first column.** Under 760px the campaign/day name is
  `position: sticky; left: 0` inside the `.t-scroll` container, so it stays put
  while the numbers swipe under it. A `.swipe` hint sits above each table.
- **Inline percentages hide under 760px** (`.pct`). Without that, a numeric
  column ends up permanently parked under the pinned name column and its leading
  digits get cut — it reads like a data bug.
- **Charts narrow their own gutter.** `PAD_L` drops 54 → 38 and spend ticks
  switch to `₹20k` form when the plot is under 520px, or the y-axis labels eat
  the plot.
- **Day labels step from day 1** (`(day-1) % every === 0`), never "first + last +
  every Nth" — that older rule printed 30 and 31 on top of each other.
- The cost-per-call average moves from a label over the line into the panel
  title (`#cpc-unit`) when narrow.
- KPI tiles are 2-up down to 360px, 1-up below.

- **`<meta name="viewport">` must stay on line 1.** Without it mobile Safari
  renders at a 980px virtual viewport and scales the whole page down, so every
  media query above is dead and the page looks like the desktop layout shrunk.
  The Artifact wrapper injects its own viewport tag, so the artifact copy hides
  this bug — only the GitHub Pages copy shows it. A duplicate tag in the artifact
  is harmless; both carry the same directive.

Verify changes at phone width by loading the page in a 390px-wide `<iframe>` —
resizing the browser window does not reliably change the viewport. **Note the
iframe does not reproduce the mobile virtual viewport**, so it cannot catch a
missing viewport meta; check that tag separately, or open the real URL on a
phone.

- The file is deliberately **pure ASCII**: the rupee sign is `&#8377;` in markup
  and `\u20B9` in script (via the `RS` constant), dashes are entities/escapes. It
  renders correctly even when served without a charset header. Keep it that way.
- Update the snapshot date in the masthead and in this README.
