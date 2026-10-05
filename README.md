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
complete) and October 2026 (1–4). Each month stops at its last complete day —
Meta keeps revising the most recent ~48h, and the live part-day moves between
calls minutes apart. Showing it would read as a collapse in spend that is not
real. **5 October is the excluded part-day.** The range under each tab name is
read off that month's own `DAILY_*` rows at load, so it cannot drift from them.

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
- The spend and reach tiles **derive whether both accounts ran**: a month where one
  account is dark reads "on Pallavi Halcyon alone" and shows one reach figure, rather
  than inheriting "across both accounts" and a `+ 0.0L`.
- Calls and cost per call by age band, both accounts combined.
- The full day-by-day table for the selected month.

## Snapshot

Frozen **5 Oct 2026, 8:50 am IST**. August and September are complete months;
October runs **1–4 Oct**, with 5 October excluded as the live part-day.

| | August (1–31) | September (1–30) | **October (1–4)** |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹36,004.67 |
| Calls placed | 5,144 | 4,539 | 460 |
| Cost per call | **₹59.99** | **₹69.07** | **₹59.79** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 113 (24.6%) · ₹243.38 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 43 (9.3%) · ₹639.59 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹27,502.22 / 460 / ₹59.79 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | — (dark) |

(September and October account rows are **call spend only**; the website-lead
spend — ₹13,712.53 in September, ₹8,502.45 in October — sits outside them.
August's Pallavi Halcyon row is total spend, its cost per call call-only; that
inconsistency is in the August figures as published.)

Previous cut (1–28 Sep, published 29 Sep): ₹3,04,514.33 · 4,256 calls · ₹69.65.

All figures are **ex-GST** (Meta bills 18% GST on top in India). Unlike
`o2-reports`, this page does not show a GST-inclusive billed total — if the
client asks for one, add it, don't silently change the per-call numbers.

### September closed at ₹69.07, better than the ₹69.65 published at the 28th

The last two days of the month were its cheapest stretch. **Pallavi Kiran went
dark on 27 September** and has spent nothing since — not for the rest of September
and not in October — so from the 28th the account is Pallavi Halcyon alone, running
four per-number call campaigns plus the Enquiry LP website-lead campaign.

23–30 Sep ran at ₹65.99 against ₹70.24 over 1–22, and the last three days (the
first of the new per-number structure) came in at **₹61.34**. Daily it is still
noisy — ₹78.02 on the 26th, ₹55.18 on the 29th — so read the direction, not a day.

The ₹31,740.53 that once looked like a Meta data gap is still accounted for in
`Halcyon | Calls — 4 Numbers | ABO | 22 Sep` (`120251289083450425`), **ARCHIVED**,
469 derived calls at ₹67.68. An unfiltered campaign listing still omits it.

Meta settled **28 Sep up ₹21.14** after publication (call spend +₹18.45, web
+₹2.69); no call counts moved.

### October: cost per call is back to the August average

**₹59.79 a call over 1–4 October — 13% below September and level with August's
₹59.99**, the first time that has been true since 9 August. The daily rate is
steady rather than lucky: ₹55.20, ₹63.34, ₹59.98, ₹61.28. Two things changed at
once, so neither can be credited alone: the call budget now runs through four
per-number campaigns, and the expensive Kiran account stopped.

| October line | spend | calls | each | 20s+ | 60s+ |
|---|---|---|---|---|---|
| `Call 8585072072 \| TS only` | ₹6,903.33 | **173** | **₹39.90** | 44 · ₹156.89 | 16 · ₹431.46 |
| `Call 9490631010 \| TS+AP` | ₹6,783.35 | 128 | ₹52.99 | 29 · ₹233.91 | 12 · ₹565.28 |
| `Call 7272897897 \| TS+AP` | ₹6,854.13 | 112 | ₹61.20 | 29 · ₹236.35 | 9 · ₹761.57 |
| `Call 7788091092 \| TS only` | ₹6,961.41 | 47 | **₹148.12** | 11 · ₹632.86 | 6 · ₹1,160.24 |

**7788091092 is the one to act on.** The README flagged it last refresh at
₹104.71; four days into October it is **₹148.12** — the same budget as the best
line for 47 calls against 173. Moving its budget to 8585072072 is the obvious test.

**The cheaper calls are shorter calls.** 24.6% past 20 seconds against
September's 29.3%, 9.3% past a minute against 12.1% — so a minute-long call went
*up*, ₹572.08 → **₹639.59**. The per-number structure is buying more dials rather
than more conversations so far. Put that trade-off to the clinic rather than
reading ₹59.79 as a clean win.

> **4 October is a real but throttled day.** The account ran out of prepaid
> balance: it took ₹5,270.02 against about ₹10,000 on each of 1–3 Oct, and the
> 5th had managed only ₹188.46 when this snapshot was taken. **₹45,000 was added
> to the balance at 7:50 am on 5 October** (activity log, "Money added to
> balance"); no budget or status change is logged. The rate held through it
> (₹61.28 a call on the 4th), so the dip in the bars is funding, not performance —
> but expect the 5th to settle much higher once delivery picks back up.

**`Halcyon | Calls — Age 35+ | FB only | CBO` is still ₹0.00** — nothing in
September, nothing in October. It returned 410 calls at **₹19.60** in 1–8 August,
the best rate ever recorded on either account. Restarting it remains the single
clearest thing to try.

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across 1–28 Sep.

**September (1–30, complete).** ₹69.07 a call, 15% above the August average,
tracking August's second half (₹72.36). The month's own arc, and October's
return to the August rate, are in *Snapshot* above.

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
  In September ₹3.55 and 1 call land in an `Unknown` band and are omitted from the
  age table; October has none. **The archived 4 Numbers campaign needs its age
  calls derived too** — its age rows carry `actions:lead` / "Not available" just
  like its total, so each band's calls are `band spend /
  cost_per_action_type:click_to_call_native_call_placed` for that band. All six
  bands divide to whole numbers and sum to exactly 469.
- **`reachSum` is per account, never per campaign — the easiest thing here to get
  wrong.** Build it from the `level: "ad_account"` daily pull: account 1's own daily
  reach plus account 2's. Summing the campaign-level reach rows instead double-counts
  people within an account: on this refresh that ran 5–6k a day high (121,549 against
  119,168 on 20 Sep; 104,433 against 98,160 on the 30th). The assertion
  `reachSum == a1_account_reach + a2_account_reach` is what catches it, and it did
  catch it here. Impressions and link clicks *are* additive across campaigns — only
  reach is not.
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
  appending. In practice days more than about a week old have not moved: on this
  refresh 20–27 Sep reproduced the published rows to the paisa and only the 28th had
  drifted (+₹21.14), so the account-level reconciliation is enough to prove the older
  days and the campaign-level re-pull can start a week back.
- **To add a month** (October was added this way): one `DAILY_*` array, one `MONTHS`
  entry, one `<button class="tab" data-month="...">`. Nothing else is month-specific —
  the tab's date range, the KPI tiles, the chart, the funnel and the account-spread
  wording all derive from the array and the entry.
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
