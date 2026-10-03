# Halcyon Pain Management — Meta Ads calls report

Client-facing report for **Halcyon Pain Management**, covering **both** ad accounts:

| Account | ID | What it runs |
|---|---|---|
| Pallavi Halcyon | `1999324147481098` | Call ads + website-lead campaigns |
| Pallavi Kiran | `694358492762548` | Call ads only |

Live: https://lenkasacademy-pixel.github.io/halcyon-reports/

A single self-contained `index.html` with a **month tab bar** (August /
September / October). Figures are baked into the `DAILY_AUG` / `DAILY_SEP` /
`DAILY_OCT` arrays and the `MONTHS` object near the bottom of the file — nothing calls the network.

**Scope: three tabs.** August 2026 (1-31, complete), September 2026 (1-30,
complete) and October 2026 (1-2, in progress). Each month stops at the last
complete day - Meta keeps revising the most recent ~48h, and the live part-day
moves between calls minutes apart. Showing it would read as a collapse in spend
that is not real. The range under each tab name is read off that month's own
`DAILY_*` rows at load, so it cannot drift from them.

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

Frozen **3 Oct 2026, 8:10 am IST**. **September is complete (1-30)** and a
third tab opens for **October (1-2)**.

> **All the movement since the last cut is on Pallavi Halcyon.** Pallavi Kiran
> has spent nothing since 27 September and closes September at
> ₹1,97,583.42 for 2,568 calls, **identical to the last cut to the paisa** -
> every campaign on it is paused or archived. Pallavi Halcyon has carried the
> account alone since the 28th.
>
> **The four per-number call campaigns are the whole story now.** Opened on
> 28 Sep, they ran 28-30 September for ₹21,528.69 and 347 calls, and the
> whole of October so far: ₹13,914.33 and 236 calls. Alongside them the new
> Enquiry LP website-lead campaign ramped from ₹3,976.85 on the 28th to
> ₹9,589.18 for September and ₹5,784.32 in two days of October.
>
> **Meta revised 28 September up by ₹21.14** after it was published
> (call spend +₹18.45, web +₹2.69, impressions +293, reach +119, clicks +4).
> Call counts and web leads did not move. Days 1-27 came back byte-identical.
>
> **2 October is complete but still settling.** It moved **₹0.29 between two
> calls minutes apart** while this refresh was built (7788091092 +₹0.22,
> 7272897897 +₹0.05, 8585072072 +₹0.02). The later figures are the ones baked
> in. 3 October is the live part-day and is excluded; it stood at ₹303.59 for
> 4 calls.
>
> **One pre-existing error on the August tab was corrected.** Its headline note
> read "23.4L impressions, 6,921 link clicks" against `MONTHS.aug.impressions`
> of 2,338,227 and `clicks` of 6,921 - less than half the truth. `DAILY_AUG`'s
> own rows sum to **5,047,184 impressions and 27,226 link clicks**, and that is
> exactly what Meta returns for the two accounts over 1-31 Aug (Pallavi Halcyon
> 3,054,990 / 22,207; Pallavi Kiran 1,992,194 / 5,019). The two constants were
> wrong, not the daily rows; they are now the daily sums. No August spend, call
> or campaign figure was touched.

| | August (1-31) | September (1-30) | October (1-2) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹19,698.65 |
| Calls placed | 5,144 | 4,539 | 236 |
| Cost per call | **₹59.99** | **₹69.07** | **₹58.96** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 52 (22.0%) · ₹267.58 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 22 (9.3%) · ₹632.47 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹13,914.33 / 236 / ₹58.96 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹0 / 0 / — |
| De-dup reach (freq) | 11,39,310 (2.68) · 6,12,279 (3.25) | 8,00,412 (2.44) · 8,37,451 (3.09) | 1,68,101 (1.51) · — |

(September and October account rows are **call spend only**; the website-lead
spend - ₹13,712.53 in September, ₹5,784.32 in October - sits outside them.
August's Pallavi Halcyon row is total spend, its cost per call call-only - that
inconsistency is in the August figures as published.)

Previous cut (1-28 Sep, published 29 Sep): ₹3,04,514.33 · 4,256 calls · ₹69.65.

All figures are **ex-GST** (Meta bills 18% GST on top in India). Unlike
`o2-reports`, this page does not show a GST-inclusive billed total - if the
client asks for one, add it, don't silently change the per-call numbers.

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across all of
   September and October.

**September (1-30), complete.** ₹69.07 a call, 15% above the August average,
tracking August's second half (₹72.36). The month got cheaper as it ended:
₹70.24 over 1-22, ₹67.63 over 23-27, then **₹52.86 over 28-30** -
₹24,528.69 for 464 calls. That last figure is the restructure, not a trend in
the old setup: on the 28th the old call campaigns were paused and four new
per-number campaigns opened on Pallavi Halcyon, and they are the only thing
that has spent since.

The gap over the month is still one account: Pallavi Halcyon ₹58.81 a call,
Pallavi Kiran ₹76.94 on ₹1,97,583 against ₹1,15,915. `ad set level 3 camp`
remains the standout at **₹45.77** across 1,102 calls; the archived
`4 Numbers` campaign did 469 calls at ₹67.68, cheaper than
`Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two dearest lines,
`New Leads Campaign` (₹95.69) and its copy (₹94.47), both stopped by the 23rd.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → ₹564.60 → **₹572.08** across eight cuts, against August's
₹507.57. It is the one figure on the page with a steady direction.

**October (1-2), in progress.** ₹58.96 a call on one account - cheaper than
September as a whole (₹69.07) and dearer than the 28-30 September stretch
(₹52.86). Two days on 236 calls is not a trend; the comparison card says so.

**The per-number spread is the finding worth acting on.** Four campaigns on one
creative set, one landing experience, differing fourfold on cost per call:

| Number | 28-30 Sep | 1-2 Oct |
|---|---|---|
| 8585072072 | ₹5,455.00 / 117 / **₹46.62** | ₹3,568.26 / 87 / **₹41.01** |
| 7272897897 | ₹5,386.31 / 82 / ₹65.69 | ₹3,513.99 / 67 / ₹52.45 |
| 9490631010 | ₹5,347.17 / 97 / ₹55.13 | ₹3,222.57 / 59 / ₹54.62 |
| 7788091092 | ₹5,340.21 / 51 / ₹104.71 | ₹3,609.49 / 23 / **₹156.93** |

**7788091092 is getting worse, not better** - ₹104.71 a call in September,
₹156.93 in October, on spend level with the other three, and ₹1,335 then ₹902
per minute-long call. It carried the same warning in the last cut as
`7788- call ads-new` (132 calls, 8 past 60 seconds, ₹1,825 each). The number
itself is the variable; 8585072072 is buying calls at a third of its price.

**Website leads have grown into a real share.** ₹5,784.32 over two days of
October for 52 Contact-good leads, ₹111.24 each - 29% of October's budget. It
optimises a **custom conversion** (`offsite_conversion.custom.1564834054962652`),
a fourth distinct lead event, and is kept out of every cost per call.

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
- Age figures come from a separate call with `breakdowns: ["age"]` (no
  `time_increment`). Assert each campaign's age rows sum to its month total.
  ₹1.93 and 1 call land in an `Unknown` band and are omitted from the age table.
- `reachSum` is the sum of each day's reach and double-counts people across days.
  Meta's de-duplicated August reach was 11,39,310 (Pallavi Halcyon, frequency
  2.68) and 6,12,279 (Pallavi Kiran, frequency 3.25); September 1–30 is 8,00,412
  (2.44) and 8,37,451 (3.09); October 1–2 is 1,68,101 (1.51) and nil — those come from a call *without* `time_increment`
  and are quoted in the footer only.
- The `reachSum` column is **each account's own daily reach, added together** —
  two numbers, not a sum over campaigns. September days 1–10 were originally
  built from campaign-level reach, which double-counts within an account and ran
  5–9k a day high; they were rebuilt from the account pull on 18 Sep so the
  column means one thing down its whole length.
- Recent days keep settling for ~48h; re-pull the whole month rather than
  appending. A full re-pull of 1-27 Sep on 3 Oct returned byte-identical
  figures, so in practice only the last three or four days move; the cheap
  check is to compare each campaign's period total against the sum of its
  days and only re-pull days in detail when they disagree.
- **A campaign's period total can differ from the sum of its days by a paisa
  or two while the window is still settling.** On 1-2 Oct the four per-number
  campaigns' period totals summed to ₹13,914.31 against ₹13,914.33 from the
  day rows. `campCalls` carries Meta's own period totals (that is what makes
  the 20s/60s divisions land on whole numbers); `callSpend` carries the
  day-row total, which is what reconciles against the account. Both render at
  zero decimal places, so the difference is invisible on the page - but keep
  them from the sources named here rather than forcing one to match the other.
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
