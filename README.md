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
complete) and October 2026 (1–28). The current month stops at the last complete
day — Meta keeps revising the most recent ~48h, and the live part-day moves
between calls minutes apart. Showing it would read as a collapse in spend that is
not real. The range under each tab name is read off that month's own `DAILY_*`
rows at load, so it cannot drift from them.

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

Frozen **29 Oct 2026, 8:25 am IST**. September is now a **complete month** and
**October has its own tab**, covering 1–28 Oct.

| | August (1–31) | September (1–30) | October (1–28) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,62,154.48 |
| Calls placed | 5,144 | 4,539 | 1,779 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.48** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 429 (24.1%) · **₹288.12** |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 167 (9.4%) · **₹740.15** |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,11,863.43 / 1,685 / ₹66.39 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / **₹124.90** |

(Both September and October account rows are **call spend only**. Website-lead
spend — ₹13,712.53 in September, ₹38,549.97 in October — sits outside them.
August's Pallavi Halcyon row is total spend, its cost per call call-only; that
inconsistency is in the August figures as published.)

### September closed at ₹69.07

The two days the previous cut could not show were the month's structural turn.
**29 and 30 September were Pallavi Halcyon alone** — ₹11,858.31 and ₹10,816.72
— running the four new per-number call campaigns and the new Enquiry LP
website-lead campaign. **Pallavi Kiran spent nothing from the 28th onward**, so
the account that carried 63% of September's call budget ended the month silent.
Adding the two days moved cost per call ₹69.65 → **₹69.07** and lifted the
20-second count to 1,328 and the 60-second count to 548. Meta also revised
1–28 September up by **₹18.45** after publication; no call counts moved.

### October: the blended rate stood still and that hides the real move

**Both accounts got more expensive.** Pallavi Halcyon went ₹58.81 → **₹66.39**
a call, Pallavi Kiran ₹76.94 → **₹124.90**. The blend barely moved (₹69.07 →
₹69.48) only because the money moved: Pallavi Halcyon carried **37% of
September's call budget and 91% of October's**, so the cheaper account now sets
the average. **Always read the two account rows, never the headline alone** —
this month is the clearest example yet of the blend hiding both components
moving the same way.

**Call quality fell, and that is October's real finding.** Only 24.1% of calls
held 20 seconds (29.3% in September, 28.1% in August) and 9.4% reached a minute
(12.1%, 11.8%). The per-call rate stood still while the cost of a real
conversation rose hard: **₹288.12** per 20-second call and **₹740.15** per
minute-long one.

**One campaign is worth the whole account's attention.**
`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each` consolidates three clinic
numbers into one ABO campaign and bought **525 calls at ₹37.11** — the cheapest
call on either account since August's ₹19.60 line, and roughly a third of what
the single-number campaigns pay (₹59.68 to ₹96.81). It wins on duration too:
₹172.41 per 20-second call against ₹437.64 for `7788091092`, which is the line
to question (277 calls, only 31 past a minute). Same numbers, same creative,
three times cheaper — **that comparison is the decision in front of this
account**.

**October is not a full month of delivery.** Nothing served on 17–20 October and
the account **has been dark since the 25th** — four full days at this snapshot.
Pallavi Kiran ran only 5–9 October. Nothing in the activity log explains the
stops. The 22nd and 23rd alone took ₹14,691 and ₹13,994, more than the whole of
10–21 October put together, so read the daily series as bursts rather than a
month.

**Website-lead spend is now a quarter of the budget** — ₹38,549.97, up from
₹13,712.53, buying 211 Contact-good leads at ₹182.70. It optimises a **custom
conversion** (`offsite_conversion.custom.1564834054962652`), a different event
from August's HContacted and HEnquiry campaigns, so the counts are **not
comparable across months** and none of that spend is in any cost per call.

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across September and
   October.

**September (1–30, complete).** ₹69.07 a call, 15% above the August average,
tracking August's second half (₹72.36). The gap is one account: Pallavi Halcyon
₹58.81 a call against Pallavi Kiran's ₹76.94 on 1.7x the spend. `ad set level 3
camp` is the standout at **₹45.77** across 1,102 calls; the archived `4 Numbers`
campaign did 469 calls at ₹67.68, cheaper than `Kiran | Calls — 3 Numbers | ABO`
(₹72.90). Kiran's two dearest lines, `New Leads Campaign` (₹95.69) and its copy
(₹94.47), both stopped by the 23rd.

**October (1–28).** ₹69.48 a call — flat against September, and that flatness is
misleading: **both accounts got dearer** (₹66.39 and ₹124.90) while 91% of the
call budget moved to the cheaper one. The winner is
`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each` at **₹37.11** across 525
calls — three numbers consolidated into one ABO campaign, against ₹59.68–₹96.81
for the same numbers run separately. **Consolidation is beating per-number
splitting on this account, on both cost and duration.**

**The minute-long call has got dearer at every single cut this report has
published:** ₹497 → ₹503 → ₹512 → ₹526 → ₹543 → ₹546 → ₹565 →
₹572.08 (Sep, complete) → **₹740.15** (Oct), against August's ₹507.57. It is the
one figure here with an unbroken direction, and October is the biggest jump of
the series. In September the Kiran lines held callers best (4 Numbers ₹460, New
Leads ₹480, 3 Numbers ₹484 per 60s call) while Pallavi Halcyon's cheap calls were
short ones (`ad set level 3 camp` ₹664, `7788- call ads-new` ₹1,825). In October
the consolidated ABO campaign leads on duration as well (₹695.81 a minute-long
call) and `7788091092` is the laggard (₹847.05, only 31 of 277 calls past a
minute). The earlier claim that 22 Sep was "the best day of the month on
duration" was removed — it rested on a five-day comparison.

**The per-number campaigns now have a month behind them.** The three that ran all
of October read ₹68.95 (094906 31010), ₹94.80 (7788091092) and ₹96.81
(7272897897); `9490631010` stopped on the 9th at ₹59.68. The 28 Sep snap
judgement — "₹43.29 on 8585072072, ₹377.06 on 7788091092, too early to judge" —
held up directionally on 7788091092, which remains the dearest line.


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

`DAILY_AUG` / `DAILY_SEP` / `DAILY_OCT` rows are
`[day, a1CallSpend, a1Calls, a1WebSpend, a1WebLeads, a2CallSpend, a2Calls, impressions, reachSum, linkClicks]`
where `a1` = Pallavi Halcyon, `a2` = Pallavi Kiran. `day` is the day of month.

Everything else a tab shows — headline totals, narrative copy, campaign tables,
age rows — lives in the `MONTHS` object keyed `aug` / `sep` / `oct`. **To add a
month, add a `DAILY_*` array and a `MONTHS` entry, then add one
`<button class="tab">` with a matching `data-month`.** Nothing else is
month-specific; October was added on 29 Oct 2026 with exactly those three edits
and no change to any rendering code.

Pull with Meta MCP `ads_get_ad_entities`, `level: "campaign"`,
`time_increment: "1"`, one call per account.

- **Derive calls whenever `results` says "Not available".** The archived
  `4 Numbers` campaign is the known case, but write the refresh so *any* campaign
  with blank results falls back to
  `spend / cost_per_action_type:click_to_call_native_call_placed`, and **assert
  every division lands on a whole number.** On the 29 Oct refresh the first pass
  returned 2,099 Pallavi Kiran calls for September instead of 2,568 because that
  one campaign silently contributed zero; the campaign-total check caught it. The
  same fallback is needed in the **age** breakdown, where that campaign's bands
  are also blank (138 + 136 + 82 + 61 + 33 + 19 = 469, matching its month total).
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
- **Carry `impressions`, `reachSum` and `linkClicks` from a fresh account-level
  daily pull for the whole month, not from the previously published rows.** On
  the 29 Oct refresh, reusing the published 1–28 September values left the month
  293 impressions and 4 clicks short of the account's own total, because Meta had
  revised those days along with the ₹18.45 of spend.
