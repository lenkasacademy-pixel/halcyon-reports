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
complete) and October 2026 (1–5, running). The live month stops at the last
complete day — Meta keeps revising the most recent ~48h, and the part-day moves
between calls minutes apart. Showing it would read as a collapse in spend that
is not real. The range under each tab name is read off that month's own `DAILY_*`
rows at load, so it cannot drift from them. **August is still the tab that opens
by default** (`let M=MONTHS.aug`); change that line if the newest month should
open first.

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

Frozen **6 Oct 2026, 8:20 am IST**. Two complete months plus five settled days
of October. September is now closed; 6 October is a live part-day and is left
out of every figure.

> **September is complete, and it ended nothing like it ran.** The two days
> missing from the last cut were the two biggest of the month on Pallavi
> Halcyon: **₹11,858.31 on the 29th and ₹10,816.72 on the 30th**, against a
> ₹3,000–4,500 daily rate for the first three weeks. Meta also revised 28 Sep up
> by **₹21.14** (call +₹18.45, web +₹2.69); no call counts moved.
>
> **Pallavi Kiran finished September dark.** It spent ₹0 on the 28th, 29th and
> 30th and closed at ₹1,97,583.42 — unchanged from the last cut, because every
> campaign on it was already paused or archived. The whole of the clinic's call
> budget is now in the four per-number campaigns on Pallavi Halcyon.
>
> **October is a different account.** Four per-number call campaigns and one
> website-lead campaign, nothing else. Pallavi Kiran was dark 1–4 Oct, ran
> `Kiran | Calls — 3 Numbers | ABO` for a single day on the 5th (₹1,239.20, 11
> calls) and has a **new campaign, `Calls | ABO | Hyderabad | Ara + Top
> Performers`, that only began spending on the 6th** — so it appears nowhere in
> the October tab yet. Add it next refresh.
>
> **4 October was a Sunday** and the Enquiry LP campaign is scheduled Mon–Sat
> 9–5, so it correctly spent nothing; that day's bar is call spend only. Do not
> read it as a stop.

| | August (1–31) | September (1–30) | October (1–5) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹45,860.69 |
| Calls placed | 5,144 | 4,539 | 569 |
| Cost per call | ₹59.99 | ₹69.07 | **₹60.19** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 145 (25.5%) · ₹236.19 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 55 (9.7%) · **₹622.69** |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹33,008.88 / 558 / ₹59.16 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹1,239.20 / 11 / ₹112.65 |
| Website-lead spend | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹11,612.61 / 74 |

(September and October account rows are **call spend only**; the website-lead
spend sits outside them, and its counts are not one comparable number — see
*Two result types* below. August's Pallavi Halcyon row is total spend, its cost
per call call-only — that inconsistency is in the August figures as published.)

Previous cut (1–28 Sep, published 29 Sep): ₹3,04,514.33 · 4,256 calls · ₹69.65.

**August's headline impressions and link clicks were wrong and are now fixed.**
`MONTHS.aug` carried `impressions:2338227, clicks:6921`, which is roughly the
Pallavi Halcyon *reach* figure and one account's clicks — not the month. Both
`DAILY_AUG` and a fresh account-level pull agree on **5,047,184 impressions and
27,226 link clicks** (Pallavi Halcyon 30,54,990 / 22,207 + Pallavi Kiran
19,92,194 / 5,019). The August KPI tile had been reading 23.4L impressions
instead of 50.5L since it was published. Spend, calls and every cost figure
were unaffected. **The check that caught it is the one worth keeping: assert
each month's `impressions` and `clicks` equal the sum of its own `DAILY_*`
column.**

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
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across all of September
   and 1–5 October.

**September (1–30), final: ₹69.07 a call** — 15% above the August average and
close to August's second half (₹72.36), not its first nine days (₹44.82). The
cheap early-August setup has not come back: `Halcyon | Calls — Age 35+ | FB only
| CBO`, which produced calls at ₹19.60, spent nothing all month.

**But the last three days of September are the story.** From the 28th the old
call campaigns were paused and four new per-number campaigns took the whole
budget. Those three days bought **351 calls for ₹21,528.69 — ₹61.33 each**,
against **₹69.72** over the 27 days before them. `ad set level 3 camp` was still
the best single line of the month at **₹45.77** across 1,102 calls, and the
archived `4 Numbers` campaign did 469 calls at ₹67.68 — cheaper than
`Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two dearest lines,
`New Leads Campaign` (₹95.69) and its copy (₹94.47), both stopped by the 23rd.

**October (1–5): the restructure is holding at ₹60.19 a call** — 13% cheaper
than September and essentially back to the August average (₹59.99), the first
sub-₹65 reading this report has carried since early August. It is not a mix
effect: Pallavi Halcyon alone is at **₹59.16** across 558 calls, and that
account is now four campaigns and nothing else.

**One number is carrying it and one is spoiling it.** On near-identical budgets
(₹8,106–₹8,355 each over the five days):

| Number | spend | calls | per call | 20s+ | per 20s | 60s+ | per 60s |
|---|---|---|---|---|---|---|---|
| 8585072072 | ₹8,354.93 | 204 | **₹40.96** | 54 | ₹154.72 | 17 | ₹491.47 |
| 9490631010 | ₹8,105.71 | 156 | ₹51.96 | 34 | ₹238.40 | 15 | ₹540.38 |
| 7272897897 | ₹8,274.25 | 131 | ₹63.16 | 36 | ₹229.84 | 10 | ₹827.42 |
| 7788091092 | ₹8,273.99 | 67 | **₹123.49** | 14 | ₹591.00 | 9 | ₹919.33 |

**7788091092 has been the dearest line for eight straight days across two
months** (₹377.06 on its first day, ₹104.71 over September's three, ₹123.49
across October's five). On equal money it is delivering roughly 137 fewer calls
than 8585072072. It is the obvious thing to pause or rebuild. 8585072072 is
unusual in the other direction: cheapest placed call *and* cheapest 20-second
and 60-second call, where cheap calls are normally short ones.

**Pallavi Kiran ran one day in October.** The 5th took ₹1,239.20 for 11 calls at
₹112.65 — far above anything on Pallavi Halcyon — but on eleven calls that is
noise, and the duration mix is extraordinary: **7 of 11 held twenty seconds and
4 reached a minute**, ₹309.80 per minute-long call, the cheapest minute anywhere
in this report. Watch it for a week before reading anything into either number.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → ₹565 → ₹572.08 (September, final) → **₹622.69** (October 1–5),
against August's ₹507.57. This is the one figure on the page with a steady
direction, and October is its worst reading yet: only **9.7%** of calls reach a
minute, against 12.1% in September and 11.8% in August. The 20-second call, by
contrast, has gone nowhere — ₹236.07 in September, ₹236.19 in October. **The
cheaper placed call has bought no cheaper conversation.** Keep both in front of
the client: the headline improved, the quality did not.

**Age reversed between the two months.** September's cheapest calls came from
the youngest and oldest bands (₹55.56 at 18–24, ₹59.84 at 65+) with the money
concentrated in 35–54 at about ₹74. October's cheapest are the *oldest* only —
₹45.89 at 65+ and ₹50.24 at 55–64 — and 25–34 is both the largest and the
dearest at ₹66.13. **October has no 18–24 row at all:** that band only ever came
from Pallavi Kiran's broad campaigns, and they barely ran.


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

The page names the event on every row and keeps this spend **out of cost per
call**. Blending it in reads ₹70.38 and overstates what a call costs — don't.

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
  ~30 campaigns and Pallavi Kiran ~80; Meta returns a row for every campaign ×
  every day, almost all empty, which blows past the row cap and silently drops
  campaigns. Query the month at campaign level first to find which campaigns
  actually spent, then re-fetch only those ids with `time_increment`.
- The daily response for 5 campaigns × 31 days already exceeds the tool's output
  limit and gets spilled to a file — parse it with `jq`/python, don't try to read
  it inline.
- **Always reconcile.** Pull `level: "ad_account"` with `time_increment: "1"` for
  the same range and assert the campaign sums equal the account's own daily spend
  *and* impressions for every day. On the August pull both accounts matched to
  the rupee on all 31 days — that check is what proves no campaign was missed. It
  also earns its keep: on the September pull it flagged a ₹28.35 gap on the part-day
  that turned out to be Meta still settling, not a dropped campaign.
- **Assert each month's `impressions` and `clicks` equal the sum of its own
  `DAILY_*` column.** August shipped with `impressions:2338227, clicks:6921`
  against day rows totalling 5,047,184 and 27,226 — one account's clicks and
  something close to the other's reach. It survived several refreshes because
  nothing else on the page reads those two fields. Fixed 6 Oct 2026.
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
- Update the snapshot date in the masthead (one place) and in this README.
- Adding a month: one `DAILY_*` array, one `MONTHS` entry, one
  `<button class="tab" data-month=...>`. Nothing else is month-specific —
  `MONTHS[id].id` is the only thing the renderer branches on (it prints "month
  average" for `aug` and "period average" otherwise).
