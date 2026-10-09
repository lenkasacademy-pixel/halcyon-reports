# Halcyon Pain Management — Meta Ads calls report

Client-facing report for **Halcyon Pain Management**, covering **both** ad accounts:

| Account | ID | What it runs |
|---|---|---|
| Pallavi Halcyon | `1999324147481098` | Call ads + website-lead campaigns |
| Pallavi Kiran | `694358492762548` | Call ads only |

Live: https://lenkasacademy-pixel.github.io/halcyon-reports/

A single self-contained `index.html` with a **month tab bar** (August /
September / October). Figures are baked into the `DAILY_AUG` / `DAILY_SEP` / `DAILY_OCT` arrays and the
`MONTHS` object near the bottom of the file — nothing calls the network.

**Scope: three tabs.** August 2026 (1–31, complete), September 2026 (1–30,
complete) and October 2026 (1–8). Each month stops at the last complete day —
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

Frozen **9 Oct 2026, 8:45 am IST**. September is now **complete** (1-30) and a
third tab carries **October 1-8**.

> ### A renamed campaign - handled, but check it
>
> **`Halcyon | Call 8585072072 | TS only | All days` was renamed at Meta to
> `Halcyon | Call 094906 31010 | TS only | All days`** on 6 Oct 2026 at 10:14 am
> (activity log, `event_category: "campaign"`, actor Abhijeet Lenka, Power Editor).
> Campaign id `120255796887700348` throughout - it is the **same campaign**, so its
> history is carried forward **in place** under the current name in both the
> September and the October tables. Nothing was appended and nothing re-labelled
> itself; its 28 Sep figure is still Rs 1,172.70 / 27 calls.
>
> **But the rename looks like a mistake, and a human should decide.** The ads inside
> that campaign are all still the 8585 creatives (`8585 | Celeb ...`,
> `8585 | Proven ...`, `8585 | Review ...`, `8585 | Aara ...`, `8585 | Kiran ...`),
> and no creative or destination change is logged. So the account now shows **two
> campaigns named for 9490631010** (one "TS only", one "TS+AP") and **none for
> 8585072072**. Either the name is wrong or the number was repointed without a
> creative change. The page uses Meta's current name so it matches Ads Manager, and
> says so on the October tab.
>
> This is the same trap `elixir-reports` documents, caught the same way: a name
> disappeared from the listing, a new one appeared carrying the whole history, and
> the activity log settled it. The tell that it was a *pure* rename and not a
> creative swap is that no `Ad updated` old/new creative-id event exists and the
> campaign's own day rows are continuous across the rename date.

### September 2026, complete (1-30)

Rs 3,27,210.50 spent, **4,539 calls at Rs 69.07** - down from the Rs 69.65 the
1-28 cut published, because the last two days ran cheap on the restructured account.

| | August (1-31) | September (1-30) | October (1-8) |
|---|---|---|---|
| Spent | Rs 3,62,046.60 | Rs 3,27,210.50 | Rs 78,144.84 |
| Calls placed | 5,144 | 4,539 | 889 |
| Cost per call | **Rs 59.99** | **Rs 69.07** | **Rs 70.68** |
| Lasted 20s+ | 1,448 (28.1%) - Rs 213.12 | 1,328 (29.3%) - Rs 236.07 | 237 (26.7%) - Rs 265.13 |
| Lasted 60s+ | 608 (11.8%) - Rs 507.57 | 548 (12.1%) - Rs 572.08 | 95 (10.7%) - Rs 661.43 |
| Pallavi Halcyon (call only) | Rs 2,18,901.90 / 3,063 / Rs 54.02 | Rs 1,15,914.55 / 1,971 / Rs 58.81 | Rs 53,764.41 / 816 / Rs 65.89 |
| Pallavi Kiran | Rs 1,43,144.70 / 2,081 / Rs 68.79 | Rs 1,97,583.42 / 2,568 / Rs 76.94 | Rs 9,071.78 / 73 / Rs 124.27 |
| Website-lead spend (outside every per-call figure) | Rs 53,443.78 / 332 | Rs 13,712.53 / 67 | Rs 15,308.65 / 84 |

(August's Pallavi Halcyon row is total spend, its cost per call call-only - that
inconsistency is in the August figures as published.)

**What the two added days did.** 29 and 30 September were carried entirely by
Pallavi Halcyon's four new per-number call campaigns: Rs 9,214.92 for **167 calls
at Rs 55.18** on the 29th - the cheapest day of the month - and Rs 7,847.78 for
116 at Rs 67.65 on the 30th. Over the two days together they bought 283 calls at
**Rs 60.29**. Pallavi Kiran spent nothing from the 28th to the 30th. Meta also
settled **28 September up by Rs 21.14** after publication; its 68 calls did not move.

`Halcyon | Call 094906 31010 | TS only` is the standout of the new set at
**Rs 46.62** across 117 September calls, within a rupee of `ad set level 3 camp`
(Rs 45.77 over 1,102 calls). `Halcyon | Call 7788091092 | TS only` opened at
Rs 104.71 - the 7788 number has now been the dearest line on this account under
three successive campaign structures.

### October 2026 so far (1-8)

Rs 78,144.84 spent, **889 calls at Rs 70.68**, within Rs 1.61 of the finished
September. Volume is down a third (111 calls a day against 151). The whole call
operation is now Pallavi Halcyon's four per-number campaigns, which take roughly
equal budgets and return wildly unequal numbers of calls:

| Campaign | Spend | Calls | Each | 20s+ | per 20s |
|---|---|---|---|---|---|
| `Call 094906 31010` (TS only) | Rs 13,064.26 | 275 | **Rs 47.51** | 68 | Rs 192.12 |
| `Call 9490631010` (TS+AP) | Rs 13,414.04 | 233 | Rs 57.57 | 48 | Rs 279.46 |
| `Call 7272897897` (TS+AP) | Rs 13,518.77 | 184 | Rs 73.47 | 59 | Rs 229.13 |
| `Call 7788091092` (TS only) | Rs 13,767.34 | 124 | **Rs 111.03** | 30 | Rs 458.91 |

The cheapest line buys more than twice as many calls per rupee as the dearest on an
equal budget. **Moving the 7788 budget onto the two cheap numbers is the obvious test.**

**Pallavi Kiran came back on the 5th** after eight days dark - one day of the old
`3 Numbers` campaign (Rs 1,254.60 / 11 calls), then a new
`Calls | ABO | Hyderabad | Ara + Top Performers` from the 6th (Rs 7,817.18 / 62 calls
at Rs 126.08). It is the dear side again: Rs 124.27 a call against Rs 65.89.

**Website leads scaled.** The Enquiry LP custom-conversion campaign took Rs 15,309
for 84 Contact-good leads, **Rs 182.25 each**, against Rs 184.41 over its three
September days. Still a different event from a call and still outside every per-call
figure.

> **Read 7 and 8 October with care.** 9 October is a live part-day and is excluded
> entirely. Meta was still revising the 7th and 8th while this was pulled: the
> Pallavi Halcyon account total for 1-8 Oct read Rs 69,073.06 from the day rows and
> Rs 69,079.69 from a period pull minutes later, and re-pulling
> `Call 7788091092` alone moved 7 Oct up by Rs 6.51. The **call counts** on those
> days look under-attributed rather than weak: 8 October returned 71 calls on
> Rs 9,378 of call spend against 143 on Rs 9,649 on the 6th. October's Rs 70.68 is
> best read as a **ceiling**; 1-6 October alone reads Rs 61.72. The page says this
> on its own tab.

Previous cut (1-28 Sep, published 29 Sep): Rs 3,04,514.33 - 4,256 calls - Rs 70.21
on 1-22, Rs 69.65 on 1-28.

All figures are **ex-GST** (Meta bills 18% GST on top in India). Unlike
`o2-reports`, this page does not show a GST-inclusive billed total - if the
client asks for one, add it, don't silently change the per-call numbers.

## Reconciliation on this refresh

- **Campaign day rows equal each account's own `level: "ad_account"` daily totals on
  spend, impressions *and* link clicks, on every day of both windows** - all 30
  September days and all 8 October days, both accounts, zero mismatches.
- Each campaign's period total equals the sum of its own day rows, except the
  Rs 6.63 of still-settling 7-8 October noted above.
- **Every 20s and 60s derivation lands on a whole number** - all 13 September
  campaign-periods and all 6 October ones.
- The archived `4 Numbers` campaign's calls are still derived from
  `cost_per_action_type:click_to_call_native_call_placed`; every day and the period
  divide to whole numbers (469 calls in five days).
- September age rows sum to the month's call spend and call count **exactly**
  (Rs 3.55 and 1 call in an `Unknown` band omitted). October age rows sum Rs 6.52
  above the day rows - the same 7-8 October settling - and match on calls exactly.
- The page renders with no JS errors and all three tabs switch cleanly.

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across the whole of
   September and the first eight days of October.

**September (1–30, complete).** ₹69.07 a call, 15% above the August average,
still tracking August's second half (₹72.36). The daily series stays noisy —
₹56.76 (23rd), ₹78.02 (26th), ₹68.74 (27th), ₹65.68 (28th), ₹55.18 (29th),
₹67.65 (30th) — so read the last two days as what they are: the restructured
account's first real run, not a trend.

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

`DAILY_AUG` / `DAILY_SEP` / `DAILY_OCT` rows are
`[day, a1CallSpend, a1Calls, a1WebSpend, a1WebLeads, a2CallSpend, a2Calls, impressions, reachSum, linkClicks]`
where `a1` = Pallavi Halcyon, `a2` = Pallavi Kiran. `day` is the day of month.

Everything else a tab shows — headline totals, narrative copy, campaign tables,
age rows — lives in the `MONTHS` object keyed `aug` / `sep` / `oct`. October was
added exactly that way on 9 Oct 2026: one `DAILY_OCT` array, one `MONTHS.oct`
entry and one `<button class="tab" data-month="oct">`, and nothing else changed. **To add a month,
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
  each call stays under 200 campaign-days, and check every id came back. On the
  9 Oct pull, 11 Pallavi Halcyon ids × 13 days came back at 156 rows — safe —
  but the same ids across the full 38-day window would have been 418.
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
- **Check for renamed campaigns every refresh.** If a name vanishes from the
  listing and a new one appears carrying the same history, pull
  `ads_account_get_activity_logs` with `event_category: "campaign"` and look for
  `Campaign name updated`. A pure rename is carried forward **in place** on the
  same campaign id — never appended as a new row, which would double-count the
  history. `Halcyon | Call 8585072072 | TS only` → `Halcyon | Call 094906 31010 |
  TS only` on 6 Oct 2026 is the worked example; see the Snapshot section.
- Update the snapshot date in the masthead and in this README.
