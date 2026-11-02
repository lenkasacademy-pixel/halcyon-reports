# Halcyon Pain Management — Meta Ads calls report

Client-facing report for **Halcyon Pain Management**, covering **both** ad accounts:

| Account | ID | What it runs |
|---|---|---|
| Pallavi Halcyon | `1999324147481098` | Call ads + website-lead campaigns |
| Pallavi Kiran | `694358492762548` | Call ads only |

Live: https://lenkasacademy-pixel.github.io/halcyon-reports/

A single self-contained `index.html` with a **month tab bar** (August / September /
October / November). Figures are baked into the `DAILY_AUG` / `DAILY_SEP` / `DAILY_OCT` / `DAILY_NOV` arrays and the
`MONTHS` object near the bottom of the file — nothing calls the network.

**Scope: four tabs.** August 2026 (1–31), September 2026 (1–30) and October 2026
(1–31) are all complete and settled; November 2026 holds **1 Nov only**. Each month
stops at the last complete day — Meta keeps revising the most recent ~48h, and the
live part-day moves between calls minutes apart. Showing it would read as a collapse
in spend that is not real: **2 November is excluded** (it stood at ₹174.29 when this
was taken). The range under each tab name is read off that month's own `DAILY_*` rows
at load, so it cannot drift from them, and a single-day month prints just the day.
**The page opens on October**, the latest complete month (`let M=MONTHS.oct`).

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

Frozen **2 Nov 2026, 8:20 am IST**. **September has closed and two new months are on
the page.**

| | August (1–31) | September (1–30) | **October (1–31)** | Nov (1 only) |
|---|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | **₹1,68,508.95** | ₹2,675.65 |
| Calls placed | 5,144 | 4,539 | **1,834** | 23 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.45** | ₹67.26 |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | **442 (24.1%) · ₹288.15** | 7 · ₹220.99 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | **172 (9.4%) · ₹740.49** | 1 |
| Call spend | ₹3,08,602.82 | ₹3,13,497.97 | ₹1,27,364.09 | ₹1,546.92 |
| Website-lead spend | ₹53,443.78 / 332 | ₹13,712.53 / 63 | **₹41,144.86 / 226** | ₹1,128.73 / 0 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,15,623.01 / 1,740 / ₹66.45 | ₹1,546.92 / 23 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 | ₹0 |

September/October/November account rows are **call spend only**; website-lead spend sits
outside them. August's Pallavi Halcyon row is total spend with a call-only cost per call —
that inconsistency is in the August figures as published and is left alone.

Previous cut (1–28 Sep, published 29 Sep): ₹3,04,514.33 · 4,256 calls · ₹69.65.

### September closed cheaper than it was published

Adding the 29th and 30th pulled the month from **₹69.65 to ₹69.07**. Both days were
**Pallavi Halcyon alone** — every campaign on Pallavi Kiran stopped after the 27th — and
Halcyon runs cheaper, so the average fell. The 29th was ₹9,214.92 of call spend for 167
calls (**₹55.18**, the cheapest day of the month's tail); the 30th ₹7,847.78 for 116 at
₹67.65. Meta also revised the 28th up by ₹21.14 after publication.

The four per-number call campaigns went from one day of data to three, and they separate:
**8585072072 at ₹46.62** across 117 calls against **7788091092 at ₹104.71** across 51.
`ad set level 3 camp` is still the month's standout at **₹45.77** across 1,102 calls.

### October: the rate held, the account shrank, and the calls got shorter

Cost per call barely moved (₹69.45 against ₹69.07) but the account spent **a third of
September's call budget** — ₹1,27,364.09 against ₹3,13,497.97 — and Pallavi Kiran ran for
**five days only** (5–9 Oct, ₹11,741.08 for 94 calls at ₹124.91, the dearest line anywhere
in this report). Pallavi Halcyon was dark on **17–20 and 25–28 October**.

**The best line this report has recorded since early August is in this month.**
`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each` took ₹19,482.72 and returned
**525 calls at ₹37.11** — cheaper than `ad set level 3 camp` (₹45.77) and beaten only by
`Halcyon | Calls — Age 35+ | FB only | CBO` (₹19.60, early August). It ran 9–24 October and
is **now paused**. Along with Age 35+, that is the thing to restart.

**The quality side is the month's bad news.** Only 24.1% of calls held twenty seconds and
9.4% held a minute — both the worst shares in this report. **The minute-long call has now
risen at every single cut**: ₹497 → ₹503 → ₹512 → ₹526 → ₹543 → ₹546 → ₹564.60 → ₹572.08 →
**₹740.49**, and this jump is by far the largest. The account paid September's price for a
materially shorter call.

**Website leads were a quarter of October** — ₹41,144.86 against ₹13,712.53 in September,
226 conversions on the `offsite_conversion.custom.1564834054962652` custom conversion. Kept
out of every per-call figure, as always.

### November: one day, and it is a new setup

1 Nov is the three **Daily 500** per-number call campaigns plus the Enquiry LP **Daily
1000** website-lead campaign, all created 29 October. ₹1,546.92 for 23 calls (₹67.26) and
₹1,128.73 on website leads with no conversions on the day. One day of 23 calls says nothing
about a rate; the tab exists so the month is on the record.

## A campaign was renamed — check this before reading October against September

**On 6 Oct 2026 at 10:14 am (activity log, Power Editor, actor Abhijeet Lenka), campaign
`120255796887700348` was renamed:**

    Campaign name updated
      old_value "Halcyon | Call 8585072072 | TS only | All days"
      new_value "Halcyon | Call 094906 31010 | TS only | All days"

It is **the same campaign object** carrying the same history. The September tab names it
`8585072072` because that is what it was called for all of September; the October tab names
it `094906 31010`. Without this note the 8585072072 line looks like it vanished and a new
line appeared.

**Two things for a human to check.** The account now has **two** campaigns whose names point
at 9490631010 — the renamed one (`094906 31010 | TS only`, ₹25,578.75 / 371 calls in October)
and `9490631010 | TS+AP | All days` (₹14,502.32 / 243) — and **none** naming 8585072072. Either
the rename is a typo, or the campaign was deliberately repointed at a different number. Also note
the 28 Sep batch rename of four campaigns from `Mon–Sat 9–5` to `All days`, which is already
reflected in the published September names.

**Always pull `ads_account_get_activity_logs` with `event_category: "campaign"` on a refresh
that spans a month boundary** and look for `Campaign name updated`. Campaign-level renames are
the same trap the ad-level README section describes, and the reconciliation will *not* catch
them: every total still balances, because the money is real — it is just attached to a
different name.

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
  Meta's de-duplicated reach, from a call *without* `time_increment`, is quoted in the
  footer only: August 11,39,310 (Pallavi Halcyon, frequency 2.68) and 6,12,279 (Pallavi
  Kiran, 3.25); **September 1–30 is 8,00,412 (2.44) and 8,37,451 (3.09)**; **October
  8,55,599 (2.34) and 90,931 (1.46)**; 1 Nov 24,497 (1.26) and 0.
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
- Update the snapshot date in the masthead and in the baked-figures comment above
  `DAILY_AUG` (two places in `index.html`) and in this README.
- **The `reachSum` column is the two accounts' own daily reach added together, not a sum
  over campaigns.** This was re-verified on this refresh: for every settled September day
  the published `reachSum` equals `a1 account reach + a2 account reach` exactly, while the
  campaign-level sum runs 6-8k a day higher. `impressions` and `linkClicks` *are* campaign
  sums (and equal the account totals).
