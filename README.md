# Halcyon Pain Management — Meta Ads calls report

Client-facing report for **Halcyon Pain Management**, covering **both** ad accounts:

| Account | ID | What it runs |
|---|---|---|
| Pallavi Halcyon | `1999324147481098` | Call ads + website-lead campaigns |
| Pallavi Kiran | `694358492762548` | Call ads only |

Live: https://lenkasacademy-pixel.github.io/halcyon-reports/

A single self-contained `index.html` with a **month tab bar** (August /
September / October / November). Figures are baked into the `DAILY_AUG` /
`DAILY_SEP` / `DAILY_OCT` / `DAILY_NOV` arrays and the `MONTHS` object near the
bottom of the file — nothing calls the network.

**Scope: four tabs.** August 2026 (1–31), September 2026 (1–30) and October 2026
(1–31) are all complete months; November 2026 runs 1–11, the days that are fully
settled. Each month stops at the last complete day — Meta keeps revising the most
recent ~48h, and the live part-day moves between calls minutes apart. Showing it
would read as a collapse in spend that is not real. The range under each tab name
is read off that month's own `DAILY_*` rows at load, so it cannot drift from them.

**The default tab is still August.** Four months in, that is probably wrong for a
client opening the link; change the initial `M` assignment if you want the newest
month to open first. **November's `days` is 11 but only five days delivered**, so
the "per day" sub-lines on that tab divide by 11 — its `partNote` says so.

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

Frozen **12 Nov 2026, 8:20 am IST**. September and October are now complete
months; November covers 1–11.

> ### BOTH ACCOUNTS HAVE BEEN DARK SINCE 5 NOVEMBER
>
> Call ads ran 1–4 Nov, a new WhatsApp campaign the 4th–5th, and **nothing at all
> since**. Pallavi Kiran has spent nothing in November, and nothing since 9 Oct
> apart from that. Nothing in the activity log explains either stop. **Raise this
> before sending the report.**
>
> October was not continuous either: the account ran 1–16 Oct, **stopped 17–21
> Oct**, ran hard on the 22nd–24th, stopped again 25–28 Oct, and restarted on the
> 29th on a smaller budget. 23 of October's 31 days had any delivery.

| | August (1–31) | September (1–30) | October (1–31) | November (1–11) |
|---|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,68,508.95 | ₹10,594.70 |
| Calls placed | 5,144 | 4,539 | 1,834 | 60 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.45** | **₹87.42** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 442 (24.1%) · ₹288.15 | 17 (28.3%) · ₹308.54 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 172 (9.4%) · **₹740.49** | 6 (10.0%) · ₹874.20 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,15,623.01 / 1,740 / ₹66.45 | ₹5,245.18 / 60 / ₹87.42 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 | ₹0.00 / 0 / — |
| Non-call spend | ₹53,443.78 / 332 | ₹13,712.53 / 63 | ₹41,144.86 / 226 | ₹5,349.52 / 69 |

Per-account rows are **call spend only** from September onward; the non-call row
sits outside them. August's Pallavi Halcyon row is total spend with a call-only
cost per call — that inconsistency is in the August figures as published and has
been left alone.

All figures are **ex-GST** (Meta bills 18% GST on top in India).

### September: the month closed cheaper than the 1–28 cut

**29 and 30 September were the two cheapest days of the month** — ₹17,062.70 of
call spend for 283 calls, **₹60.29 each** against the month's ₹69.07 — which is
what pulls the headline down from the ₹69.65 the 1–28 cut reported. Meta also
revised 1–28 Sep up by ₹18.45 with no change to call counts (that window still
reads ₹69.65). Pallavi Kiran stopped on the 27th.

### October: flat headline, worse calls

Cost per call barely moved (₹69.45 against ₹69.07) but on **half the call
volume**, and the daily spread is the widest in this report: **₹17.97 on the 16th
to ₹148.16 on the 24th**. The real change is quality — only 24.1% of calls lasted
20 seconds and 9.4% reached a minute, both the weakest here, and **the
minute-long call hit ₹740.49**, continuing the only series on this page with a
steady direction (₹497 → ₹503 → ₹512 → ₹526 → ₹543 → ₹546 → ₹565 → ₹572 →
**₹740**).

**`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each` is the best line since
August.** Opened 9 Oct, it bought **525 calls at ₹37.11** — a third of the
month's calls for 15% of its call spend, the cheapest rate since `Age 35+ | FB
only | CBO` managed ₹19.60 in early August. The three single-number "All days"
campaigns it replaced ran at ₹68.95–₹96.81. **Worth more budget** — but judge it
on ₹172.41 per 20-second call, not ₹37.11, because only 21.5% of its calls held
twenty seconds.

`Halcyon | Calls — Age 35+ | FB only | CBO` is **still ₹0.00** across September,
October and November.

### November: five days, and a third result type

₹87.42 a call is the dearest rate here, but it rests on **60 calls across four
days** — a flag to check, not a trend. The cheap ABO line did not run at all.

**`Halcyon | ABO | WhatsApp | 6 numbers | 700 each | Telangana regions` is new**
(4–5 Nov): ₹4,160.90 for **56 conversations at ₹74.30 each**. See the
three-result-types section below — it is kept out of every cost per call.

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

## Three result types — do not merge them

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

**WhatsApp campaigns** (new, from 4 Nov 2026) report `results` with indicator
`actions:onsite_conversion.messaging_conversation_started_7d`. A WhatsApp
conversation is neither a phone call nor a website lead.

The page names the event on every row and keeps all non-call spend **out of cost
per call**. Blending it in reads ₹70.38 for August and overstates what a call
costs — don't.

**Where the third type lives in the data.** `DAILY_*` has only two non-call
columns, so the WhatsApp campaign goes into the **same columns as the
website-lead campaigns** (`a1WebSpend` / `a1WebLeads`). That keeps the one
invariant that matters — total spend = call + non-call = the account's own daily
total — and keeps WhatsApp out of cost per call. Those two columns are therefore a
**deliberately mixed bucket**, which is why the shared labels now read **"Non-call
spend"** and **"Non-call results"** rather than "Website leads", and why the
`campWeb` table names the event on every row. It is the same treatment August
already needed for its four different pixel events. If the mix ever has to be
split apart on the chart, that needs a new `DAILY_*` column and is **not** a
month-only change.

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
  2.68) and 6,12,279 (Pallavi Kiran, frequency 3.25); September 1–28 is 7,00,847
  (2.37) and 8,37,451 (3.09) — those come from a call *without* `time_increment`
  and are quoted in the footer only.
- The `reachSum` column is **each account's own daily reach, added together** —
  two numbers, not a sum over campaigns. September days 1–10 were originally
  built from campaign-level reach, which double-counts within an account and ran
  5–9k a day high; they were rebuilt from the account pull on 18 Sep so the
  column means one thing down its whole length.
- **August was never converted, and was rebuilt on 12 Nov 2026.** All 31 of its
  days were still campaign-level reach, running **978–13,051 a day high** and
  **2,20,596 (5.7%) high over the month**. Spend, impressions and link clicks were
  already correct and are untouched; only `DAILY_AUG[i][8]` changed. The column now
  means the same thing across all four months.
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
- Update the snapshot date in the masthead (one place, around line 332), the
  `Baked figures` comment, and in this README.
