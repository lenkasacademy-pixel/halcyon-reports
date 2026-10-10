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
complete) and October 2026 (1–9). The current month stops at the last complete
day — Meta keeps revising the most recent ~48h, and the live part-day moves
between calls minutes apart. Showing it would read as a collapse in spend that
is not real. The range under each tab name is read off that month's own
`DAILY_*` rows at load, so it cannot drift from them.

**The page still opens on the August tab** (`let M=MONTHS.aug`). That was fine
with two tabs and is now questionable with three — change it to `MONTHS.oct` if
the client should land on the current month.

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

Frozen **10 Oct 2026, 8:05 am IST**. August and September are both complete
months; October runs **1–9**, with the 10th held out as a live part-day
(₹276.03 on Pallavi Halcyon at the time of the pull).

| | August (1–31) | September (1–30) | October (1–9) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹90,236.50 |
| Calls placed | 5,144 | 4,539 | 998 |
| Cost per call | **₹59.99** | **₹69.07** | **₹71.82** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 255 (25.6%) · ₹281.10 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 104 (10.4%) · ₹689.23 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹59,948.71 / 904 / ₹66.31 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,730.88 / 94 / ₹124.80 |

(September and October account rows are **call spend only** — ₹13,712.53 of
September website-lead spend and ₹18,556.91 of October's sit outside them.
August's Pallavi Halcyon row is total spend, its cost per call call-only — that
inconsistency is in the August figures as published.)

Previous cut (1–28 Sep, published 29 Sep): ₹3,04,514.33 · 4,256 calls · ₹69.65.

### Three things this refresh turned up

> **1. A campaign was renamed mid-flight, and the new name is a different phone
> number.** On **6 Oct 2026 at 10:14 am** (Power Editor, actor Abhijeet Lenka)
> campaign `120255796887700348` went from
> `Halcyon | Call 8585072072 | TS only | All days` to
> `Halcyon | Call 094906 31010 | TS only | All days`. It is the **same campaign
> object** — same id, and its whole history carries forward, including the 27
> calls on 28 Sep that the previous refresh published under 8585072072. This is
> a pure rename: the activity log shows a `Campaign name updated` event and
> **no** status churn or creative change around it. But `094906 31010` is
> the 9490631010 number with a leading zero and a space, and there is already a
> separate `Halcyon | Call 9490631010 | TS+AP` campaign — so either the
> campaign's call number was changed too, or the rename is a slip. **Worth
> asking the client.** Both tabs label the row
> `Halcyon | Call 094906 31010 | TS only (was 8585072072)` so one campaign does
> not read as two.
>
> **2. Meta settled 28 September after publication, and its call count went
> *down*.** Spend rose ₹21.14 (₹8,421.70 → ₹8,442.84: +₹18.45 across the four
> per-number call campaigns, +₹2.69 on Enquiry LP) while calls fell from 68 to
> **64**. The 68 did not come from Meta's daily data even at the time — see the
> next point. The restructure's first day now reads ₹69.78 a call, not ₹65.41.
>
> **3. September's campaign totals carry 4 calls Meta will not place on a
> day.** `ad set level 3 camp` reports 1,102 calls for the month but its daily
> rows sum to 1,099; `new 3 ads 8585` reports 271 against 270. Every one of the
> 27 days matches the published row exactly on both spend *and* calls, so this
> is not a missed day — it is Meta's own month-level attribution exceeding its
> own day-level breakdown. The headline, funnel and campaign table use the
> campaign totals (**4,539**, which is what Ads Manager shows and what the age
> breakdown sums to); the day table sums to **4,535** and now carries a
> `callsDrift` footnote saying so. **Do not close the gap by adding calls to a
> day** — that is what produced the wrong 68 on 28 Sep.

**September closed with one account running.** Pallavi Kiran spent nothing from
the 28th onward, so the last three days are Pallavi Halcyon alone: four
per-number call campaigns plus Enquiry LP, about ₹9,215 and ₹7,848 of call
spend on the 29th and 30th at ₹55.18 and ₹67.65 a call. 23–30 Sep ran ₹66.20
against ₹70.24 over 1–22 — a modest improvement, not a trend.

**October: cheaper for six days, then three bad ones.** Daily cost per call ran
₹55.20, ₹63.34, ₹59.98, ₹61.28, ₹62.35, ₹67.47 — all better than September —
then **₹89.79 (7th), ₹132.45 (8th), ₹80.83 (9th)**. The 8th is the worst day in
either account in two months: ₹6,283 of Pallavi Halcyon call spend for 48
calls. The 8th and 9th are inside Meta's revision window, so re-read them next
refresh before acting.

**The per-number campaigns separate the same way in both months, and then were
all paused.** October: `094906 31010` (the 8585072072 campaign) ₹49.55 across
286 calls; `9490631010` ₹59.92; `7272897897` ₹78.70; `7788091092` **₹105.01**
— dearest in both months, ₹20,462 lifetime. On **9 Oct at 3:56 pm** all four
were paused and replaced by one consolidated campaign,
`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each`, created the same
afternoon. Its single day reads ₹27.41 a call across 41 calls — the best figure
on either account, but one day on an opening budget, and the consolidation ends
the only clean per-number comparison this account has.

**Pallavi Kiran came back on 5 Oct** after eight days dark: one day on the old
`Kiran | Calls — 3 Numbers | ABO` (₹1,254.60, 11 calls), then a new campaign
`Calls | ABO | Hyderabad | Ara + Top Performers` from the 6th (₹10,476.28, 83
calls, **₹126.22**). The account is now far dearer than Pallavi Halcyon —
₹124.80 against ₹66.31.

**Call quality is slipping.** The 20-second share fell 29.3% → 25.6% and the
60-second share 12.1% → 10.4%, and both true costs are the highest this report
has recorded: ₹281.10 per 20-second call and **₹689.23** per minute-long one.
The minute-long call has now risen at every refresh: ₹497 → ₹503 → ₹512 →
₹526 → ₹543 → ₹546 → ₹565 → ₹572 (Sept) → **₹689** (Oct).

**Website leads: one campaign, and the count is falling.** October is Enquiry LP
alone — ₹18,556.91 for 87 custom "Contact-good lead" conversions (₹213.30
each). Its daily count runs 21, 31, 7, —, 15, 3, 7, —, 3: the last four
delivering days produced 28 against 59 in the first three, on similar spend.
Still **not comparable** with the HContacted counts on the other tabs.

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across 1–28 Sep.

**September (1–30, complete).** ₹69.07 a call, 15% above the August average,
tracking August's second half (₹72.36). 23–30 Sep ran cheaper (₹66.20) than
1–22 (₹70.24), but the daily series is noisy — ₹56.76 (23rd), ₹78.02 (26th),
₹69.78 (28th), ₹55.18 (29th), ₹67.65 (30th) — not a trend.

The gap is one account: Pallavi Halcyon ₹58.81 a call, Pallavi Kiran ₹76.94 on
₹1,97,583 against ₹1,15,915 of call spend. `ad set level 3 camp` remains the
standout at **₹45.77** across 1,102 calls; the archived `4 Numbers` campaign did
469 calls at ₹67.68, cheaper than `Kiran | Calls — 3 Numbers | ABO` (₹72.90).
Kiran's two dearest lines, `New Leads Campaign` (₹95.69) and its copy (₹94.47),
both stopped by the 23rd, and the account is dark from the 28th.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → ₹565 → **₹572.08** across eight cuts, against August's ₹507.57. The Kiran
lines hold callers best (4 Numbers ₹460, New Leads ₹480, 3 Numbers ₹484 per
60s call); Pallavi Halcyon's cheap calls are short (`ad set level 3 camp` ₹664,
`7788- call ads-new` ₹1,825). The earlier claim that 22 Sep was "the best day of
the month on duration" was removed — it rested on a five-day comparison.

**The per-number campaigns now have twelve days** (28 Sep – 9 Oct) and the
ranking held the whole way: the 8585072072 campaign cheapest (₹46.62 in Sept,
₹49.55 in Oct), 7788091092 dearest (₹104.71, then ₹105.01). All four were
paused on 9 Oct in favour of one consolidated campaign. Its first day is
₹27.41 a call — promising, and one day long.


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

- **Check the activity log for campaign renames every refresh**
  (`ads_account_get_activity_logs`, `event_category: "campaign"`, event type
  `Campaign name updated`). A renamed campaign keeps its id and its whole
  history, so it is not a new row — but the name on a client-facing table
  changes under you, and a per-number campaign renamed to a *different* number
  is a question for the client, not a silent relabel. This happened on 6 Oct
  2026 to `120255796887700348`. Where a name has changed, label the row
  `<new name> (was <old>)` in **both** months so one campaign does not read as
  two.
- **The day table's Calls column can sum below the headline, and that is
  expected.** Meta's month-level total for a campaign can exceed the sum of its
  own `time_increment: "1"` rows; in September it does so by 4 calls. Put the
  difference in `callsDrift` on the `MONTHS` entry and the page prints a
  footnote under the day table. **Never** add the difference onto a day — the
  68-calls-on-28-Sep error in the previous cut came from exactly that.
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
  appending. **This bites the last published day in particular:** 28 Sep moved
  +₹21.14 and −4 calls between the 29 Sep and 10 Oct pulls, after it had been
  published as settled. Always re-pull the previous snapshot's final day.
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
