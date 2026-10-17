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
complete) and October 2026 (1–16). Each month stops at the last complete day —
Meta keeps revising the most recent ~48h, and the live part-day moves between
calls minutes apart. Showing it would read as a collapse in spend that is not
real. The range under each tab name is read off that month's own `DAILY_*` rows
at load, so it cannot drift from them.

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

Frozen **17 Oct 2026, 8:15 am IST**. September is now **complete (1–30)** and
October runs **1–16**, the last complete day.

> **September's last three days were a restructure, not a wind-down.** Pallavi
> Kiran went dark on the 28th and stayed dark. Pallavi Halcyon paused its old call
> campaigns the same day and opened **four per-number call campaigns** plus the
> Enquiry LP website-lead campaign. Those four took ₹21,528.69 over 28–30 Sep and
> booked 347 calls at **₹62.04** — below the month's ₹69.07 average.
>
> **October consolidated them, and it halved the price of a call.** The four
> per-number campaigns ran 1–9 Oct (864 calls at **₹68.09**) and were all paused
> on the 9th at 3:56 pm, replaced the same afternoon by one campaign,
> `Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each` (`120255979446760348`),
> which has produced **518 calls at ₹36.93** — the cheapest call line on either
> account since August's `Age 35+ | FB only | CBO` (₹19.60). **But it buys short
> calls**: only 21.4% of its calls hold twenty seconds, so a minute-long call off
> it costs ₹683. Read both numbers before shifting more budget.
>
> **Pallavi Kiran came back for five days.** After eleven dark days it restarted
> on 5 Oct and ran a new campaign, `Calls | ABO | Hyderabad | Ara + Top
> Performers` (`120251497637820425`), from the 6th to the 9th, then stopped again:
> ₹11,741.08 for 94 calls, **₹124.91 each** — the dearest line of the month.

| | August (1–31) | September (1–30) | October (1–16) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,24,016.93 |
| Calls placed | 5,144 | 4,539 | 1,476 |
| Cost per call | **₹59.99** | **₹69.07** | **₹60.77** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 360 (24.4%) · ₹249.17 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 131 (8.9%) · ₹684.75 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹77,961.48 / 1,382 / ₹56.41 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 |

(September and October account rows are **call spend only**. September's
₹13,712.53 of website-lead spend — ₹4,123.35 on 1–3 Sep, ₹9,589.18 on 28–30 Sep —
and October's ₹34,314.37 sit outside them. August's Pallavi Halcyon row is total
spend, its cost per call call-only — that inconsistency is in the August figures
as published.)

Previous cut (1–28 Sep, published 29 Sep): ₹3,04,514.33 · 4,256 calls · ₹69.65.

**The website-lead campaign is now a third of the budget.** `Enquiry LP` took
₹34,314.37 in October — 28% of everything the two accounts spent — for 189
custom-conversion leads at ₹181.56 each. It optimises a **custom conversion**
(`offsite_conversion.custom.1564834054962652`, "Contact-good lead"), a fourth
distinct lead event, so its count is not comparable with the HContacted /
HEnquiry / `fb_pixel_lead` campaigns and its spend stays out of every cost per
call.

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

**September (1–30, complete).** ₹69.07 a call, 15% above the August average,
tracking August's second half (₹72.36). The month got cheaper as it closed: 1–22
ran ₹70.24, 23–30 came in at ₹66.20 and the three restructured days at ₹62.04.

The gap is one account: Pallavi Halcyon ₹58.81 a call, Pallavi Kiran ₹76.94 on
close to twice the spend. `ad set level 3 camp` remains the standout at **₹45.77**
across 1,102 calls; the archived `4 Numbers` campaign did 469 calls at ₹67.68,
cheaper than `Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two dearest
lines, `New Leads Campaign` (₹95.69) and its copy (₹94.47), both stopped by the
23rd. Among the four new per-number campaigns the spread is wide: `8585072072`
did 117 calls at ₹46.62 while `7788091092` managed 51 at ₹104.71 on almost the
same money.

**October (1–16).** ₹60.77 a call — the cheapest month since August, and the
consolidation is why. See the Snapshot section above.

**The minute-long call stopped climbing, then jumped.** ₹497 → ₹503 → ₹512 →
₹526 → ₹543 → ₹546 → ₹565 → **₹572.08** (September, complete) → **₹684.75**
(October). The October jump is not a price rise so much as a mix change: the
consolidated campaign buys rings cheaply and conversations expensively.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → **₹564.60** across seven cuts, against August's ₹507.57. The Kiran
lines hold callers best (4 Numbers ₹460, New Leads ₹480, 3 Numbers ₹484 per
60s call); Pallavi Halcyon's cheap calls are short (`ad set level 3 camp` ₹664,
`7788- call ads-new` ₹1,825). The earlier claim that 22 Sep was "the best day of
the month on duration" was removed — it rested on a five-day comparison.

**The new per-number campaigns have one day of data** (28 Sep): ₹4,447.54,
68 calls, ₹65.41 — from ₹43.29 (8585072072, 27 calls) to ₹377.06 (7788091092,
3 calls). Too early to judge; watch 7788091092.


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

## A campaign rename can move a phone number under you

**This bit the report on 17 Oct 2026.** `Halcyon | Call 8585072072 | TS only |
All days` disappeared from the Pallavi Halcyon campaign list and
`Halcyon | Call 094906 31010 | TS only | All days` appeared in its place with a
whole month of history behind it. It is the **same campaign object**
(`120255796887700348`) renamed — confirmed in the activity log
(`event_category: "campaign"`):

    Campaign name updated   6 Oct 2026, 10:14 AM   actor Abhijeet Lenka, Power Editor
      old_value "Halcyon | Call 8585072072 | TS only | All days"
      new_value "Halcyon | Call 094906 31010 | TS only | All days"

Unlike the Elixir ad renames there is no sign the creative changed, so the
history is carried forward on the one row — but **the number in the name changed**,
and that is a real question for the clinic: if the campaign now dials a different
number, September's 117 calls were to the old one. The tables therefore label each
month with the name the campaign ran under **in that month**: September's row says
`8585072072`, October's says `094906 31010`. **If a per-number campaign's name
changes, pull the activity log before carrying history forward**, and say which
number the calls actually went to.

## Daily `results` can trail the period total

Meta's per-day `results` do not always add up to its own figure for the month: a
call counted in the period is not always pinned to a single day. On the September
pull the day rows came to **4,535 calls against a period total of 4,539** — 4
short, all on Pallavi Halcyon, split `new 3 ads 8585` −1 and `ad set level 3 camp`
−3. October was exact.

**Headline `calls` follows the period total**, because that is what the
per-campaign table sums to and what Ads Manager shows for the month; the day rows
stay faithful to what Meta reports per day and are there for shape. Do not pad a
day to close the gap — the previous cut had 4 extra calls sitting on 28 September
for exactly that reason, which made its own day table disagree with its own
campaign table. **Spend and impressions must still reconcile exactly**, and they
do, on every day of both months and both accounts.

## Refreshing

`DAILY_AUG` / `DAILY_SEP` rows are
`[day, a1CallSpend, a1Calls, a1WebSpend, a1WebLeads, a2CallSpend, a2Calls, impressions, reachSum, linkClicks]`
where `a1` = Pallavi Halcyon, `a2` = Pallavi Kiran. `day` is the day of month.

Everything else a tab shows — headline totals, narrative copy, campaign tables,
age rows — lives in the `MONTHS` object keyed `aug` / `sep`. **To add a month,
add a `DAILY_*` array and a `MONTHS` entry, then add one `<button class="tab">`
with a matching `data-month`.** Nothing else is month-specific — October was added
with exactly those three edits.

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
- Age figures come from a separate call with `breakdowns: ["age"]` (no
  `time_increment`). Assert each campaign's age rows sum to its month total — all
  13 September and all 7 October campaigns did, to the paisa. An `Unknown` band
  (September ₹3.55 and 1 call, October ₹0.24 and none) is omitted from the table.
  For the archived `4 Numbers` campaign the per-band calls are **derived** the same
  way as the campaign total, and they sum back to 469 exactly.
- **Filtering `amount_spent > 0` on the campaign listing hides lagging
  conversions.** It is otherwise the cheapest way to find which campaigns spent,
  but `Halcyon | LP 8585 | Website Leads` has ₹0 spend and still carries 4
  HContacted conversions attributed back from its August run. Re-check the
  zero-spend website-lead campaigns by name before settling `webLeads`.
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
- Update the snapshot date in the masthead (one line of prose) and in the
  `Baked figures` comment above the arrays, and in this README.
