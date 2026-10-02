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

**Scope: two tabs.** August 2026 (1–31, complete) and September 2026 (1–30,
now also complete). Each month stops at the last complete day — Meta keeps revising the most recent
~48h, and the live part-day moves between calls minutes apart. Showing it would
read as a collapse in spend that is not real. The range under each tab name is
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
- Calls and cost per call by age band, both accounts combined.
- The full day-by-day table for the selected month.

## Snapshot

Frozen **2 Oct 2026, 8:06 am IST**, data window **1–30 September — the whole
month, every day settled**. There is no part-day in either tab: October is out of
scope (see *October needs a tab* below).

> **The Pallavi Kiran "coverage gap" was an archived campaign.** From 23 Sep the
> Kiran campaign rows summed to only 33.8% of the account's spend. The missing
> ₹31,740.53 was in `Halcyon | Calls — 4 Numbers | ABO | 22 Sep`
> (`120251289083450425`), which ran 23–27 Sep and is now **ARCHIVED**. Archived
> (and deleted) campaigns are **not returned by an unfiltered campaign listing** —
> you must filter `effective_status IN [..., "ARCHIVED", "DELETED"]` to see them.
> With it included, campaign rows equal the account's daily spend and impressions
> on every day, both accounts, to the paisa.
>
> **Its calls are derived.** Meta labels it a lead campaign (`results` indicator
> `actions:lead`, "Not available"), though it is a call campaign. Calls =
> `spend / cost_per_action_type:click_to_call_native_call_placed` (request the
> plain `cost_per_action_type` field; the `:subtype` form is rejected). Every day
> divides to a whole number: 76, 111, 102, 93, 87 = **469 calls**. The same check
> reproduces `results` exactly on every other call campaign.
>
> **Structural change on 28 Sep.** Pallavi Kiran spent ₹0 — every campaign on it
> is paused or archived. On Pallavi Halcyon the old call campaigns are paused and
> four new per-number call campaigns started (`Halcyon | Call 8585072072 / 7788091092
> | TS only | All days`, `Halcyon | Call 7272897897 / 9490631010 | TS+AP | All days`),
> plus a new website-lead campaign `Halcyon | Enquiry LP | Contact-good lead |
> Mon–Sat 9–5` optimising a **custom conversion** (`offsite_conversion.custom.1564834054962652`)
> — a fourth distinct lead event, kept out of cost per call.
>
> **The last three days are Pallavi Halcyon alone.** Pallavi Kiran spent ₹0 from
> the 28th onward and closes the month at ₹1,97,583.42 / 2,568 calls / ₹76.94.
> Pallavi Halcyon spent ₹21,527.58 on calls over 28–30 Sep — more than it spent
> across the whole of 23–27 Sep — on the four new per-number campaigns.
>
> Meta revised 21–22 Sep after publication (+₹107.66 in total, calls unchanged),
> and revised **28 Sep up by ₹21.14** on this pull (₹18.45 call, ₹2.69 web), its
> 68 calls unchanged. **29 Sep, excluded last time as in progress, settled at
> ₹11,858.31** — the reason the live part-day never sets a number here.

| | August (1–31) | September (1–30) |
|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,209.39 |
| Calls placed | 5,144 | 4,539 |
| Cost per call | **₹59.99** | **₹69.07** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.07 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,913.44 / 1,971 / ₹58.81 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 |

(Both September account rows are **call spend only**; the ₹13,712.53 of
website-lead spend — ₹4,123.35 on 1–3 Sep and ₹9,589.18 on 28–30 Sep — sits
outside them. August's Pallavi Halcyon row is total spend, its cost per call call-only —
that inconsistency is in the August figures as published.)

Previous cuts: 1–22 Sep (published 28 Sep) ₹2,34,692.62 · 3,284 calls · ₹70.21;
1–28 Sep (published 29 Sep) ₹3,04,514.33 · 4,256 calls · ₹69.65.

### October needs a tab

**October is already running and is not on the page.** Pallavi Halcyon took
**₹9,583.63 on 1 Oct** (125,615 impressions) and ₹470.88 so far on the 2nd;
Pallavi Kiran is still dark. That is a full day of spend the client cannot see.

It was deliberately **not** added in this refresh: an October tab would have one
settled day in it, and every month-specific field here is hand-written prose —
`findingTitle`, `phases`, `findingBody`, `funnelNote`, `ageIntro`. Writing a
month's narrative off one day is the mistake this report has already corrected
once (the "best day of the month on duration" claim that rested on five days).
**Add the tab once October has enough days to describe**, per *Refreshing* below:
one `DAILY_OCT` array, one `MONTHS.oct` entry, one `<button class="tab"
data-month="oct">`.

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
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across all of 1–30 Sep.

**September (1–30, final).** ₹69.07 a call, 15% above the August average, still
tracking August's second half (₹72.36). The month got cheaper at the very end —
**₹61.33 a call over 28–30 Sep against ₹69.72 over 1–27** — but that is
structural, not an improvement: those three days are Pallavi Halcyon alone, and
Pallavi Halcyon has always been the cheaper account. The dear account switching
off is doing the work. Day to day it is still noisy: ₹65.68 (28th), ₹55.18
(29th), ₹67.64 (30th).

The gap held all month: Pallavi Halcyon ₹58.81 a call, Pallavi Kiran ₹76.94 on
roughly 1.7× the spend. `ad set level 3 camp` is still the standout at **₹45.77**
across 1,102 calls; the archived `4 Numbers` campaign did 469 calls at ₹67.68,
cheaper than `Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two dearest
lines, `New Leads Campaign` (₹95.69) and its copy (₹94.47), both stopped by the
23rd, and the account itself stopped after the 27th.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → ₹564.60 → **₹572.07** across eight cuts, against August's ₹507.57.
It has risen at every single refresh this month and is the one figure here with a
steady direction. The Kiran lines hold callers best over the month (4 Numbers
₹460, New Leads ₹480, 3 Numbers ₹484 per 60s call); Pallavi Halcyon's older cheap
calls are short (`ad set level 3 camp` ₹664, `7788- call ads-new` ₹1,825). The
earlier claim that 22 Sep was "the best day of the month on duration" was removed
— it rested on a five-day comparison.

**The four per-number campaigns now have three days each, and they separated.**

| Campaign | Spend | Calls | Each | 20s+ | per 20s | 60s+ | per 60s |
|---|---|---|---|---|---|---|---|
| `Call 8585072072` (TS) | ₹5,454.74 | 117 | **₹46.62** | 37 | **₹147.43** | 10 | ₹545 |
| `Call 9490631010` (TS+AP) | ₹5,347.17 | 97 | ₹55.13 | 17 | ₹314.54 | 5 | ₹1,069 |
| `Call 7272897897` (TS+AP) | ₹5,385.94 | 82 | ₹65.68 | 19 | ₹283.47 | 6 | ₹898 |
| `Call 7788091092` (TS) | ₹5,339.73 | 51 | ₹104.70 | 12 | ₹444.98 | 4 | ₹1,335 |

**`8585072072` is the find of the month.** ₹46.62 a call is within a rupee of
`ad set level 3 camp`, and its **₹147.43 per 20-second call is the cheapest of
any campaign in September by a third** — so for once a cheap placed call is not
just a short one. Its 65+ band is the cheapest cell anywhere in the data: 23
calls at ₹25.56.

**7788091092 was the one to watch and it has improved.** ₹377.06 on its first
day (3 calls) → ₹104.70 over three days, so day one was a cold start rather than
a broken campaign. It is still twice the cost of any other line, and the only
one of the four worth questioning.

**The Enquiry LP website-lead campaign scaled.** ₹9,589.18 over 28–30 Sep for 52
`Contact-good lead` custom conversions, ₹184.41 each — now the second-largest
line of spend on Pallavi Halcyon. It is a **fourth distinct lead event** and
stays out of every cost-per-call figure.


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
  (2.44) and 8,37,451 (3.09) — those come from a call *without* `time_increment`
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
- Update the snapshot date in the masthead (the intro paragraph) and in the
  `Baked figures` comment above `DAILY_AUG`, and in this README.
