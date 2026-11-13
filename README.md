# Halcyon Pain Management — Meta Ads calls report

Client-facing report for **Halcyon Pain Management**, covering **both** ad accounts:

| Account | ID | What it runs |
|---|---|---|
| Pallavi Halcyon | `1999324147481098` | Call ads + website-lead campaigns |
| Pallavi Kiran | `694358492762548` | Call ads only |

Live: https://lenkasacademy-pixel.github.io/halcyon-reports/

A single self-contained `index.html` with a **month tab bar** (August /
September / October / November). Figures are baked into the `DAILY_AUG`,
`DAILY_SEP`, `DAILY_OCT` and `DAILY_NOV` arrays and the `MONTHS` object near the
bottom of the file — nothing calls the network.

**Scope: four tabs.** August 2026 (1–31), September 2026 (1–30) and October 2026
(1–31) are complete months; November 2026 runs 1–12. November stops at the last
complete day — Meta keeps revising the most recent ~48h, and the live part-day
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

Frozen **13 Nov 2026, 8:25 am IST**. Four tabs: **1–31 August**, **1–30 September**,
**1–31 October** and **1–12 November**.

| | August (1–31) | September (1–30) | October (1–31) | November (1–12) |
|---|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,68,508.95 | ₹10,594.70 |
| Calls placed | 5,144 | 4,539 | 1,834 | 60 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.45** | **₹87.42** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 442 (24.1%) · ₹288.15 | 17 (28.3%) · ₹308.54 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 172 (9.4%) · ₹740.49 | 6 (10.0%) · ₹874.20 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,15,623.01 / 1,740 / ₹66.45 | ₹5,245.18 / 60 / ₹87.42 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 | ₹0.00 / 0 / — |
| Non-call spend | ₹53,443.78 / 332 | ₹13,712.53 / 63 | ₹41,144.86 / 226 | ₹5,349.52 / 69 |

(September, October and November account rows are **call spend only**; the non-call
row sits outside them. August's Pallavi Halcyon row is total spend with a call-only
cost per call — that inconsistency is in the August figures as published.)

All figures are **ex-GST**. Unlike `o2-reports` this page shows no GST-inclusive total.

### September closed cheaper than the 1–28 cut

The 29th and 30th were Pallavi Halcyon alone — Pallavi Kiran spent nothing from the
28th and has not spent since. Those two days ran ₹55.18 and ₹67.65 a call, which pulled
the month from the published **₹69.65 (1–28)** down to **₹69.07 (1–30)**. The four
per-number campaigns that opened on the 28th finished the month three days old and
already far apart: **8585072072 ₹46.62** (117 calls), 9490631010 ₹55.13 (97),
7272897897 ₹65.69 (82), **7788091092 ₹104.71** (51). 7788091092 was flagged as the one
to watch; it is the dearest of the four and stays so through October.

### October: the rate held, the volume did not

Cost per call moved ₹69.07 → **₹69.45**, but calls fell **60%** (4,539 → 1,834).
That is delivery, not price: Pallavi Halcyon served on 23 of 31 days (dark 17–20 and
25–28 October) and Pallavi Kiran ran for five days only (5–9 Oct) at **₹124.91** a
call, the dearest line of the month.

**`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each` is the find of the month.**
Four days (21–24 Oct), ₹19,482.72, **525 calls at ₹37.11** — cheaper than September's
best line (`ad set level 3 camp`, ₹45.77) and under a third of Pallavi Kiran's rate. It
is still ACTIVE. Caveat: only **5.3%** of its calls reached a minute (28 of 525), the
weakest rate of the month, so the ₹37.11 headline flatters it — the same trade the
August `Age 35+` campaign had.

Non-call spend rose to **₹41,144.86**, about a quarter of October, for 226
Contact-good leads at ₹182.06 each.

### November: dearest calls on record, then nothing

Four days of call delivery, 60 calls, **₹87.42** — 26% above October and the highest in
this report. **Delivery stopped on 6 November**: both accounts have spent ₹0.00 every
settled day since, and ₹0.00 on the 13th so far. Nothing in the account activity log
explains it — **check the payment method and the campaign budgets before reading
November as a performance result.**

## A third result type: WhatsApp

**New on 4 November.** `Halcyon | ABO | WhatsApp | 6 numbers | 700 each | Telangana
regions` took ₹4,160.90 for **56 messaging conversations** (`actions:onsite_conversion.
messaging_conversation_started_7d`), ₹74.30 each. It is the only campaign still ACTIVE
on either account.

A messaging conversation is neither a phone call nor a pixel lead, so it is **a third
kind of result** on this page. It is carried in the November `campWeb` table with its
event named, and its spend is in `webSpend` — i.e. **outside every per-call figure**,
which is the same rule the website-lead campaigns follow. `campWeb`'s count column is
therefore "non-call results, mixed events", exactly as it already was for the
HContacted / HEnquiry / fb_pixel_lead rows; the event is named on every row and the
column is never totalled as one number.

## A campaign rename moved a phone number

**6 October 2026, 10:14 am** (activity log, `event_category: "campaign"`, Power Editor,
actor Abhijeet Lenka):

    Campaign name updated
      old_value  "Halcyon | Call 8585072072 | TS only | All days"
      new_value  "Halcyon | Call 094906 31010 | TS only | All days"

Same campaign id (`120255796887700348`). The spend and calls carry straight through, so
nothing in the totals moves — but **the number in the campaign name is the number the
ad dials**, and the account already has a separate `Call 9490631010 | TS+AP` campaign.
So either two campaigns now point at one number and 8585072072 has no campaign at all,
or the label was changed without the creative. **The API cannot show the dialled number,
so a human has to confirm which.**

The report handles it the way `elixir-reports` handles a renamed ad: the row is labelled
with the name the campaign carried **during that month**, so September reads
`Call 8585072072` and October reads `Call 094906 31010`. `campCalls` is keyed by name
for display only, so no history re-labels itself.

## A daily pull can silently zero the last days of its window

**This bit the report on 13 Nov 2026, and it is the worst failure mode seen yet.**
One `ads_get_ad_entities` call (`level: "campaign"`, `time_increment: "1"`, 11 campaign
ids, 1–30 September) returned the full 11 × 30 = **330 rows, with every campaign's
28th, 29th and 30th reading `amount_spent: 0`**. The October pull (10 ids × 31 days =
310 rows) did the same to the 29th, 30th and 31st. Nothing was missing: no error, no
dropped id, no short page, the right number of rows, correct dates.

Re-requesting the same days in a **short window** (28 Sep – 4 Oct, 28–31 Oct) returned
them in full — ₹31,117.87 on Pallavi Halcyon for 28–30 September alone.

**The account reconciliation is the only thing that catches this.** Campaign rows fell
short of the account's own daily spend on exactly those days, by exactly the missing
amount. Rules now:

- Keep every `time_increment` pull **well under ~200 rows** (campaigns × days).
- **Reconcile every day**, not the period total — a period total pulled without
  `time_increment` is correct even when the daily rows are not, so comparing totals
  hides this completely.
- If the tail of a window reads zero, re-pull those days in a window of their own
  before believing them.

Same family as the `o2-reports` trap of 13 Nov, where a seven-campaign daily pull zeroed
all thirty days of one campaign.

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

## Two result types — do not merge them

*(Three, from 4 November: see **A third result type: WhatsApp** above.)*

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
- Update the snapshot date in **two places** in `index.html` — the masthead paragraph
  and the comment above the baked figures — and in this README.
- Campaign listings are filtered `amount_spent > 0`, so a campaign that spent nothing
  in the month is not listed even if Meta attributes lagging pixel events to it. That
  is why September's non-call count is 63 (Enquiry LP 52 + LP 7788 11) and no longer
  carries the four lagging conversions the zero-spend `LP 8585` row held.
