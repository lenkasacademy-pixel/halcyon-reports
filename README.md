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
complete) and October 2026 (1–24). October stops at the 24th because **both
accounts have spent nothing since** — not because the month is being truncated
for settling. Each month stops at its last day with delivery; never show a live
part-day, because Meta keeps revising the most recent ~48h and the part-day moves
between calls minutes apart. The range under each tab name is read off that
month's own `DAILY_*` rows at load, so it cannot drift from them.

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

Frozen **26 Oct 2026, 8:20 am IST**. All three months reconcile to the paisa
against each account's own daily totals, on every day.

| | August (1–31) | September (1–30) | October (1–24) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,62,154.48 |
| Calls placed | 5,144 | 4,539 | 1,779 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.48** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 429 (24.1%) · ₹288.12 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 167 (9.4%) · **₹740.15** |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,11,863.43 / 1,685 / ₹66.39 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / **₹124.91** |
| Website-lead spend | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹38,549.97 / 211 |

(September and October account rows are **call spend only**; the website-lead
spend sits outside them. August's Pallavi Halcyon row is total spend with a
call-only cost per call — that inconsistency is in the August figures as
published.)

Previous cut (1–28 Sep, published 29 Sep): ₹3,04,514.33 · 4,256 calls · ₹69.65.

All figures are **ex-GST** (Meta bills 18% GST on top in India). This page does
not show a GST-inclusive billed total — if the client asks for one, add it, don't
silently change the per-call numbers.

### October 2026

**Cost per call held flat; call duration did not.** ₹69.48 against September's
₹69.07, still 16% above the August average. But only **9.4%** of calls passed a
minute (September 12.1%, August 11.8%), and the minute-long call now costs
**₹740.15** against September's ₹572.08 — a 29% jump, and the sharpest move in
the eight refreshes this figure has been tracked across (₹497 → 503 → 512 → 526
→ 543 → 546 → 565 → 572 → **740**).

**`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each` is the find of the
month, and it is paused.** Opened 9 Oct via the MCP server, it bought **525 calls
at ₹37.11** on ₹19,482.72 — the most calls of any line in October and the first
campaign under ₹40 since `Calls — Age 35+ | FB only | CBO` managed ₹19.60 in
early August. It also holds a minute-long call at ₹696, better than every
single-number campaign bar 9490631010. The four single-number campaigns it
replaced run ₹59.68 (9490631010) to ₹96.81 (7272897897). **Worth restarting.**

**Pallavi Kiran is effectively switched off** — ₹11,741.08 over five days (5–9
Oct) for 94 calls at **₹124.91**, the dearest line anywhere in this report. Its
new campaign `Calls | ABO | Hyderabad | Ara + Top Performers` ran the 6th to the
9th at ₹126.34 a call and has not run since.

**Website-lead spend is now the biggest single line on the account.** Enquiry LP
took ₹38,549.97 — 24% of everything both accounts spent in October, against
₹13,712.53 in September — for 211 "Contact-good lead" custom conversions at
₹182.70 each. Blending it into cost per call would read **₹91.15** instead of
₹69.48, a 31% overstatement. Keep it out.

**The account was dark 17–20 October** and has spent nothing since the 24th.

### September 2026 (now complete)

The two closing days brought the month down from the published ₹69.65 to
**₹69.07**, because the four new per-number campaigns delivered cheaply once they
had more than one day behind them. **The one-day read on them was noise, exactly
as the previous cut warned:** `7788091092` looked catastrophic at ₹377.06 across
three calls on 28 Sep; over its three settled days it lands at **₹104.71** on 51
calls — still the dearest of the four, but not an outlier. The others read ₹46.62
(8585072072), ₹55.13 (9490631010) and ₹65.69 (7272897897).

`ad set level 3 camp` remains the month's standout at **₹45.76** across 1,102
calls. The archived `4 Numbers` campaign bought 469 calls at ₹67.68 in five days,
cheaper than Kiran's main line at ₹72.90.

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across 1–28 Sep.

**September (1–28).** ₹69.65 a call, 16% above the August average, tracking
August's second half (₹72.36). 23–28 Sep ran slightly cheaper (₹67.63) than
1–22 (₹70.24), but the daily series is noisy — ₹56.76 (23rd), ₹63.06, ₹67.39,
₹78.02 (26th), ₹68.74, ₹65.41 (28th) — not a trend.

The gap is one account: Pallavi Halcyon ₹58.55 a call, Pallavi Kiran ₹76.94 on
twice the spend. `ad set level 3 camp` remains the standout at **₹45.77** across
1,102 calls; the archived `4 Numbers` campaign did 469 calls at ₹67.68, cheaper
than `Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two dearest lines,
`New Leads Campaign` (₹95.69) and its copy (₹94.47), both stopped by the 23rd.

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

## A campaign rename re-labels history — check the activity log

**This bit the 26 Oct refresh.** `Halcyon | Call 8585072072 | TS only | All days`
disappeared from the Pallavi Halcyon listing and `Halcyon | Call 094906 31010 |
TS only | All days` appeared in its place, carrying the whole history. It was a
**rename on the same campaign id** (`120255796887700348`), recorded in
`ads_account_get_activity_logs` with `event_category: "campaign"`:

    Campaign name updated   6 Oct 2026, 10:14 AM, Power Editor
      old_value "Halcyon | Call 8585072072 | TS only | All days"
      new_value "Halcyon | Call 094906 31010 | TS only | All days"

**September's `campCalls` row keeps the name the campaign ran under**
(`8585072072`); October's carries the new one. Writing the new name into
September would tell the client that September's 117 calls came from a number
that campaign was not dialling at the time — the same class of error as the ad
rename in `elixir-reports`. **Pull the campaign activity log whenever a name
appears or disappears between refreshes.**

Also worth a human eye: after the rename the account has **two** campaigns naming
9490631010 — one `TS only` (the renamed one) and one `TS+AP`. That may be
deliberate or may be a mistake in the rename.

## Day-level call attribution can trail the period figure

In October, `Halcyon | Call 7788091092 | TS only | All days` reports **277** calls
for 1–24 Oct, but its day rows sum to **276**, and so do its age bands. One call
is attributed to the period and to no day and no age band.

**The headline `calls`, `calls20`, `calls60` and `callSpend` in `MONTHS` come
from the per-campaign period reads**, which are Meta's own totals and what the
campaign table sums to. The day rows are a distribution view of the same month
and may trail by a call. Assert the two agree within 1 and report the difference;
do not reconcile them by adding a call to a day.

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
- **An `amount_spent > 0` filter does NOT carry the status filter with it.** On
  the 26 Oct refresh, listing Pallavi Kiran's September campaigns with *only*
  `amount_spent GREATER_THAN 0` returned **3 of the 4** campaigns that spent —
  the ARCHIVED `4 Numbers` campaign was omitted again, leaving the campaign sums
  ₹31,740.53 short of the account total, the identical symptom to 28 Sep. If you
  filter on spend, pass the `effective_status` clause **in the same call**, and
  reconcile against the account either way. The reconciliation is what caught it,
  both times.
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
  `time_increment`). Assert each campaign's age rows sum to its month total.
  ₹1.93 and 1 call land in an `Unknown` band and are omitted from the age table.
- `reachSum` is the sum of each day's reach and double-counts people across days.
  Meta's de-duplicated August reach was 11,39,310 (Pallavi Halcyon, frequency
  2.68) and 6,12,279 (Pallavi Kiran, frequency 3.25); September 1–30 is 8,00,412
  (2.44) and 8,37,451 (3.09); October 1–24 is 8,27,837 (2.33) and 90,931 (1.46) —
  those come from a call *without* `time_increment` and are quoted in the footer
  only.
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
- Update the snapshot date in the masthead, in the baked-figures comment and in
  this README.
- **The `campWeb` assert must include zero-spend rows.** `LP 8585 | Website
  Leads` spent nothing in September yet carries 4 HContacted conversions Meta
  attributed back to it, and those 4 sit inside the 1–3 Sep day rows (which read
  9 + 1 + 5 = 15 against LP 7788's own campaign total of 11). Comparing the day
  rows against only the campaigns that spent therefore reads 4 leads short and
  looks like a reattribution; it isn't. Sum **all** `campWeb` rows. September's
  web leads rose 26 → 67 purely because Enquiry LP ran three days instead of one.
- Meta also revised **28 Sep up by ₹21.14** (call +₹18.45, web +₹2.69) with no
  call count moving. Days 1–27 were byte-identical to the previous publication.
