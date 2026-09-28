# Halcyon Pain Management — Meta Ads calls report

Client-facing report for **Halcyon Pain Management**, covering **both** ad accounts:

| Account | ID | What it runs |
|---|---|---|
| Pallavi Halcyon | `1999324147481098` | Call ads + website-lead campaigns |
| Pallavi Kiran | `694358492762548` | Call ads only |

Live: https://lenkasacademy-pixel.github.io/halcyon-reports/

A single self-contained `index.html` with a **month tab bar** (August /
September). Figures are baked into the `DAILY_AUG` / `DAILY_SEP` arrays and the
`MONTHS` object near the bottom of the file — nothing calls the network.

**Scope: two tabs.** August 2026 (1–31, complete) and September 2026
(1–27 settled, plus **28 September shown as a part-day**).

The part-day gets a row on the chart and in the day table, tagged *so far*, and
is **added into no total** — every headline, footer and funnel figure on the
September tab is 1–27. Meta keeps revising the most recent ~48h and the live
part-day moves between calls minutes apart; counting it would read as a collapse
in spend that is not real. The `snap` field on a month is what marks that day —
see **Refreshing**.

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

Frozen **28 Sep 2026, 1:30 pm IST**. September now runs **1–27 settled**, with
28 September carried as a labelled part-day.

> **The five-day hole is closed.** September was stuck at the 22nd because
> Pallavi Kiran's campaign breakdown has been incomplete since the 23rd. It
> still is:
>
> | window | account total | sum of campaign rows | covered |
> |---|---|---|---|
> | 1–22 Sep | ₹1,49,609.85 | ₹1,49,609.85 | **100%** |
> | 23–28 Sep | ₹47,951.48 | ₹16,221.42 | **33.8%** |
>
> Per day from the 23rd: 47.1%, **0%**, **0%**, 51.9%, 45.3%. On the 24th and
> 25th every campaign on the account reports zero against ₹14,522.69 of real
> spend. Not pagination and not sorting — the three spending campaigns were
> queried directly by `object_ids` and genuinely return zero. Ad-set level shows
> the identical gap, so it is not campaign-specific either. **Worth raising with
> Meta support; it has not fixed itself in six days.**
>
> **What unblocked it: calls can be counted at account level after all.**
> `results` is "Not available" at `level: "ad_account"` — an account can span
> result types, so Meta refuses the count. But
> `cost_per_action_type:click_to_call_native_call_placed` *is* available there,
> and `spend / cost` gives the count. Same derivation this report already used
> for the 20s and 60s figures, just applied one level up. See
> **Deriving call counts at account level** below for the validation.
>
> The five recovered days came in **better than the month, not worse** — ₹67.86
> a call against the month's ₹69.73:
>
> | | spend | calls | per call | 20s+ | 60s+ | per 60s |
> |---|---|---|---|---|---|---|
> | 23 Sep | ₹11,749.80 | 207 | ₹56.76 | 62 (30.0%) | 27 | ₹435.18 |
> | 24 Sep | ₹7,629.68 | 121 | ₹63.06 | 36 (29.8%) | 19 | ₹401.56 |
> | 25 Sep | ₹6,940.86 | 102 | ₹68.05 | 33 (32.4%) | 19 | ₹365.31 |
> | 26 Sep | ₹20,674.67 | 265 | ₹78.02 | 76 (28.7%) | 32 | ₹646.08 |
> | 27 Sep | ₹14,280.86 | 208 | ₹68.66 | 45 (21.6%) | **4** | **₹3,570.22** |
> | 28 Sep (part-day, to 1:30 pm) | ₹3,773.49 | 10 | — | 2 | 1 | — |
>
> Holding the month at the 22nd would have **understated** the client's
> performance for six days.
>
> **Two things to watch, both on duration, not price.** 27 September placed 208
> calls and kept only **4** past a minute, ₹3,570 each — by far the worst day of
> the month. Duration settles more slowly than spend, so the 27th may still fill
> in; if it has not moved at the next cut, it is real. More broadly the recovered
> week buys calls more cheaply and keeps fewer of them on the line: 27.9% past
> 20s over 23–27 against 30.2% over 1–22, and ₹606.69 a minute-long call against
> ₹546.63.
>
> **Pallavi Halcyon's two-day stop is resolved.** It stopped on the 24th–25th
> (₹47.85, then ₹0.00) and recovered on its own. The activity log is silent on
> both the stop and the recovery, so **"check the payment method" remains
> unresolved rather than answered** — nobody paused anything and nobody restarted
> it. It has run ₹6,394 and ₹2,747 since. The account also disappeared from
> `ads_get_ad_accounts` for four days while still spending; that was an access
> failure, not a delivery one, and it answers again.
>
> **Still scoped to the 22nd:** the per-campaign table and the age table, which
> can only be built from the breakdown Meta has not filled in. Both say so on the
> page — the campaign table's footer sums *the rows it shows* and is tagged
> `1–22 Sep only`, and a scope note sits above it. Nothing on the page claims
> campaign coverage it does not have.

| | August (1–31) | September (1–27) |
|---|---|---|
| Spent | ₹3,62,046.60 | ₹2,96,076.15 |
| Calls placed | 5,144 | 4,187 |
| Cost per call | **₹59.99** | **₹69.73** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,243 (29.7%) · ₹234.88 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 523 (12.5%) · ₹558.23 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹94,379.02 / 1,619 / ₹58.29 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,573.78 / 2,568 / ₹76.94 |

(Both September account rows are **call spend only**; the ₹4,123.35 of
website-lead spend sits outside them. August's Pallavi Halcyon row is total
spend, its cost per call call-only — that inconsistency is in the August figures
as published.)

September is tracking August's *second half* (₹72.36), not its first nine days
(₹44.82). Calls still connect past 20 seconds more often than in August, but the
minute-long call has run dearer every cut this month: ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → ₹558, against August's ₹507.57. Seven moves one way.

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
   margin, on ~₹1,000/day. Worth restarting — **still off**: ₹0.00 across the
   whole of 1–28 Sep on Pallavi Halcyon, whose campaign breakdown is complete, so
   that is a confirmed zero and not a gap in the data.

**September (1–27).** ₹69.73 a call, 16% above the August average.
The gap is one account, not the client's advertising: Pallavi Halcyon runs
₹58.29 a call against Pallavi Kiran's ₹76.94. Pallavi Halcyon has now read
₹59.03, ₹59.74, ₹59.05, ₹58.60, ₹58.72, ₹58.29 across six cuts — flat, still
above its own August call-only rate of ₹54.02.
Website-lead spend has almost stopped (₹4,123 in the first three days, nothing
since), so the budget is back on the phone.
`ad set level 3 camp` is the standout at **₹45.56** across 946 calls on only
~₹1,959/day (1–22) — the one line beating August's average.

**Duration is where the month is drifting, not price.** Now that call counts can
be derived per day at account level, the whole month reads day by day for the
first time. The best day is **15 September** — 139 calls at ₹65.29, 39.6% of them
past 20 seconds and a minute-long call at ₹362.99. The worst is **27 September**:
208 calls, **4** past a minute, ₹3,570.22 each. Across 23–27 the recovered week
buys calls more cheaply than 1–22 (₹67.86 vs ₹70.24) and keeps fewer on the line
(27.9% vs 30.2% past 20s; ₹606.69 vs ₹546.63 a minute-long call).

An earlier cut of this README called 22 September "the best day of the month on
duration" at 33.5% past 20s. With the full daily series now available that is
wrong — 15 Sep (39.6%), 9 Sep (36.4%) and 12 Sep (34.3%) all beat it. The claim
was written from a five-day comparison, not the month. Don't call a day best
without the series behind it.

**The five-day read on the two copies is noisy, not directional:**

| Campaign | Account | Spend | Calls | Cost | 18–19 → 18–21 → 18–22 |
|---|---|---|---|---|---|
| `New Leads Campaign – Copy` | Pallavi Kiran | ₹12,818.98 | 139 | **₹92.22** | ₹93.96 → ₹98.03 → ₹92.22 |
| `7788- call ads-new – Copy` | Pallavi Halcyon | ₹3,837.26 | 50 | ₹76.75 | ₹78.10 → ₹73.34 → ₹76.75 |

Yesterday's note called the Kiran copy "the dearest line on either account, above
the ₹95.69 it replaced". It is now **below** that at ₹92.22. Neither series has
enough days behind it to read as a direction — do not act on either yet. The
Kiran copy is still the weakest live line on duration, at ₹754.06 a minute-long
call.

Both rows above are as at 1–22, which is where the page's campaign table stands.
Pallavi Halcyon's breakdown has since moved, though, and it changes one of them:
**`7788- call ads-new – Copy` ran 18–26 Sep, ₹6,952.13 across 96 calls —
₹72.42**, and has now stopped. The Kiran copy cannot be updated, because that
account's breakdown has not moved since the 22nd.

**Five new campaigns opened on 28 September** — all on Pallavi Halcyon, all
inside the part-day, so none of them counts anywhere in the September totals:

| Campaign | Spend (part-day) | Calls |
|---|---|---|
| `Halcyon \| Call 8585072072 \| TS only \| All days` | ₹319.94 | 3 |
| `Halcyon \| Call 7788091092 \| TS only \| All days` | ₹292.59 | 1 |
| `Halcyon \| Call 7272897897 \| TS+AP \| All days` | ₹274.28 | 1 |
| `Halcyon \| Call 9490631010 \| TS+AP \| All days` | ₹259.88 | 2 |
| `Halcyon \| Enquiry LP \| Contact-good lead \| Mon–Sat 9–5` | ₹2,626.80 | 0 (lead campaign) |

One call campaign per clinic number, which is a structural change — the old
campaigns dialled several numbers each, so from the 28th the table can finally
read *which line rang*. They will have a full day behind them at the next
refresh; do not read anything into a few hundred rupees.

A fourth Pallavi Kiran campaign, `Halcyon | Calls — 4 Numbers | ABO | 22 Sep`,
was created on the 22nd and has still spent nothing.

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

**Derive per day and sum; never derive over a period.** Meta rounds
`cost_per_action_type` to six decimals, and dividing a *month's* spend by a
*month's* average cost compounds that rounding — on the September pull it gave
`ad set level 3 camp` 1,098 calls against the 1,099 you get by deriving each day
and adding. Per day it lands on a whole number every time; per period it does
not. The whole-number assert is what catches this, so keep it.

The 20s/60s figures appear in the funnel and the campaign table but not in the
day table, because the day table's columns are spend and calls. The daily series
*is* available — one `cost_per_action_type` pull per account per month with
`time_increment` — and the September narrative is written from it. Large
responses; expect them to spill to a file.

## Deriving call counts at account level

`results` is **"Not available"** at `level: "ad_account"` — an account can span
result types, so Meta refuses to give one count. That was the blocker that held
September at the 22nd, because calls were only ever read off campaign rows.

**`cost_per_action_type:click_to_call_native_call_placed` is available at account
level**, and `spend / cost` gives the count — the same derivation used above for
duration, one level up:

    callsPlaced = spend / cost_per_action_type:click_to_call_native_call_placed

Validation before it was used for anything: on all **44 account-days** where both
the account-level derivation and the campaign-level `results` exist (2 accounts ×
22 days), the two agree **exactly**, and every division lands on a whole number.
Assert both when re-running.

This is how days 23–27 are priced while Pallavi Kiran's campaign breakdown is
still broken, and it is the reason the day table, chart, funnel and every
headline figure can run to the 27th while the campaign and age tables cannot.

One day carries a real exception: **25 Sep on Pallavi Halcyon reports the
`click_to_call_native_call_placed` key with ₹0.00 spend**, so the division is
undefined. It is recorded as 0 calls, which is what the account's own totals say.
Handle a zero-spend key as zero, not as an error and not as a skip.

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

The range printed under each tab name (*1–31*, *1–27*) is **derived from that
month's own `DAILY_*` array at load**, not written into the markup. It used to be
hardcoded and it drifted: the September tab read *1–16* for days while the data,
the note, the totals and the day table had all moved on to 1–22. Nothing about a
month's window is hand-written any more.

### `snap` — the part-day

A month may carry `snap: <day>`. That day **gets a row** in the day table and a
bar on the chart, tagged *so far*, and is **added into no total**: not the KPI
tiles, not the day-table footer, not the funnel, not the tab range. One rule, one
place — `renderDays()` skips it when accumulating and `t-sub` filters it out.

Omit `snap` for a finished month (August has none). Set it to the current day
when the window runs up to today. Never let the part-day set a headline number —
Meta revises the most recent ~48h, and the live day moves between calls minutes
apart.

### `campWindow` / `campScope` — when the campaign table lags the month

The campaign table's footer sums **the rows it shows**, not the month, because
`campCalls` can cover a shorter window than the day data (September's does:
Pallavi Kiran's breakdown has been broken since the 23rd). Set `campWindow` to
that shorter range and it is printed in the footer as a tag; put the explanation
in `campScope` and it renders above the table. Leave both off and the table is
assumed to cover the whole month.

Neither field changes a number — they only stop the page claiming coverage it
does not have. If you extend `campCalls`, update `campWindow` in the same edit.

Everything else a tab shows — headline totals, narrative copy, campaign tables,
age rows — lives in the `MONTHS` object keyed `aug` / `sep`. **To add a month,
add a `DAILY_*` array and a `MONTHS` entry, then add one `<button class="tab">`
with a matching `data-month`.** Nothing else is month-specific.

Pull with Meta MCP `ads_get_ad_entities`, `level: "campaign"`,
`time_increment: "1"`, one call per account.

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
- **Where the 28 Sep refresh landed.** Pallavi Halcyon reconciles on spend *and*
  impressions on 27 of 28 days; the 27th is off by ₹0.04 and 2 impressions, which
  is Meta still settling inside the ~48h window. Pallavi Kiran reconciles exactly
  on 1–22 and is only 33.8% covered from the 23rd — the known breakdown failure,
  which is why account-level derivation is used for those days.
- **A period pull and a sum of daily pulls do not agree exactly**, and neither is
  wrong. Pulling 1–27 in one call gives ₹2,96,077.12 and 41,52,570 impressions
  against ₹2,96,076.15 and 41,52,556 from the daily rows — ₹0.97 and 14
  impressions apart, Meta's own rounding. Reach and frequency have no daily
  equivalent at all and must come from the period call. Take totals from one
  source and say which; this page takes them from the daily rows, and reach and
  frequency from the period call.
- Age figures come from a separate call with `breakdowns: ["age"]` (no
  `time_increment`). Assert each campaign's age rows sum to its month total.
  ₹1.93 and 1 call land in an `Unknown` band and are omitted from the age table.
- `reachSum` is the sum of each day's reach and double-counts people across days.
  Meta's de-duplicated August reach was 11,39,310 (Pallavi Halcyon, frequency
  2.68) and 6,12,279 (Pallavi Kiran, frequency 3.25); September 1–27 is 6,49,262
  (2.41) and 8,37,451 (3.09) — those come from a call *without* `time_increment`
  and are quoted in the footer only. **Re-pull them whenever the window moves**;
  they cannot be summed out of the daily rows.
- The `reachSum` column is **each account's own daily reach, added together** —
  two numbers, not a sum over campaigns. September days 1–10 were originally
  built from campaign-level reach, which double-counts within an account and ran
  5–9k a day high; they were rebuilt from the account pull on 18 Sep so the
  column means one thing down its whole length.
- Recent days keep settling for ~48h; re-pull the whole month rather than
  appending.
- `campCalls` rows are
  `[name, account(1|2), daysLive, spend, callsPlaced, calls20s, calls60s]`. The
  account flag drives the colour dot — keep it correct when adding rows.
- A month's `calls20` / `calls60` are the **month's** funnel totals and equal the
  sum of the `campCalls` rows *only when the table covers the whole month*.
  August's do (1,448 / 608). September's do not — 1,243 / 523 over 1–27 against
  991 / 422 in the rows, which cover 1–22 — and that is what `campWindow` exists
  to say. Assert the equality when `campWindow` is unset; do not assert it when
  it is set.
- **Pallavi Halcyon's own breakdown is complete and reconciles exactly**
  (₹94,379.02 of campaign rows against ₹94,379.02 of account-level call spend,
  1–27). Only Pallavi Kiran's is broken. The campaign table is held at 1–22 for
  *both* accounts so its footer means one window rather than two; if you decide
  to advance Halcyon's rows alone, every row already prints its own `daysLive`
  range, but say so in `campScope` and expect the footer to read as a mixture.

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
