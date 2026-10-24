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
complete) and October 2026 (1–23). October stops at the last complete day — Meta
keeps revising the most recent ~48h, and the live part-day moves between calls
minutes apart. Showing it would read as a collapse in spend that is not real. The
range under each tab name is read off that month's own `DAILY_*` rows at load, so
it cannot drift from them. The page still opens on the August tab (`let M=MONTHS.aug`);
move that to `MONTHS.oct` if the client should land on the current month.

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

Frozen **24 Oct 2026, 8:10 am IST**. **September is now complete** (1–30) and
**October is a new tab** (1–23, the last complete day).

> **A campaign was renamed underneath the report.** On **6 Oct 2026, 10:14 am**
> (Power Editor, actor Abhijeet Lenka) campaign `120255796887700348` went from
> `Halcyon | Call 8585072072 | TS only | All days` to
> `Halcyon | Call 094906 31010 | TS only | All days`. Same campaign id, and
> `ads_account_get_activity_logs` shows **no** creative replacement or Pending
> Review alongside it — so it is a true rename, not the creative swap the
> `elixir-reports` README warns about. But the phone number in the name changed,
> which means the campaign advertises a different number from the 6th.
> **September's row keeps the old name** (that is the number it carried all
> month); October's row uses the new one. If it is renamed again, do the same:
> label each month's row with the name the campaign ran under that month.

> **Four dark days in October.** 17–20 Oct both accounts spent **₹0.00**, after
> the 16th tailed off at ₹849.07, and delivery resumed on the 22nd at ₹14,691.44.
> Nothing in the campaign activity log explains the 17th–20th; the 24 Oct log
> shows campaigns being switched off on the 23rd at 5:46 pm and back on at
> 5:55–5:56 am on the 24th, which is a separate, later event. Worth asking the
> client before reading the October rate as an improvement.

| | August (1–31) | September (1–30) | October (1–23) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,54,272.93 |
| Calls placed | 5,144 | 4,539 | 1,729 |
| Cost per call | **₹59.99** | **₹69.07** | **₹67.26** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 418 (24.2%) · ₹278.21 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 162 (9.4%) · ₹717.86 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,04,551.69 / 1,635 / ₹63.95 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 |
| Website leads (outside the above) | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹37,980.16 / 211 |

(September and October account rows are **call spend only**. August's Pallavi
Halcyon row is total spend, its cost per call call-only — that inconsistency is
in the August figures as published.)

Previous cut (1–28 Sep, published 29 Sep): ₹3,04,514.33 · 4,256 calls · ₹69.65.

All figures are **ex-GST** (Meta bills 18% GST on top in India). Unlike
`o2-reports`, this page does not show a GST-inclusive billed total — if the
client asks for one, add it, don't silently change the per-call numbers.

### What moved in September

The last two days closed the month, and both were cheap: **29 Sep ₹9,214.92 for
167 calls (₹55.18)** and **30 Sep ₹7,847.78 for 116 calls (₹67.65)**, both
Pallavi Halcyon alone — which pulled the month from ₹69.65 at the 28th to
**₹69.07**. 28 Sep itself settled up ₹21.14 (call spend ₹4,447.54 → ₹4,465.99,
website-lead spend ₹3,974.16 → ₹3,976.85, calls 68 → 64). Pallavi Kiran spent
nothing from the 28th and did not come back in September, so its September
figures are **byte-identical** to the previous cut.

The four per-number campaigns got three days: **₹21,528.69 for 347 calls,
₹62.04 each** — from ₹46.62 on 8585072072 (117 calls) to ₹104.71 on 7788091092
(51 calls). Early, but the spread across four identical campaigns pointing at
four different numbers is itself the finding.

### What October says so far

**The improvement is one campaign.** `Halcyon | ABO | Calls | 7788 + 7272 + 9490 |
600 each` (created 9 Oct, already PAUSED) took ₹19,132.26 over eight days and
returned **519 calls at ₹36.86** — the cheapest call on this report since
`Halcyon | Calls — Age 35+ | FB only | CBO` at ₹19.60 in early August.
**Strip it out and October reads ₹80.30 a call, dearer than September.** It
carries the same caveat as the Age 35+ campaign: only 21% of its calls held
twenty seconds and 5.4% held a minute (month: 24.2% and 9.4%), so its calls skew
short. Its 20-second call is still the cheapest here at ₹172.36, so it is not
*only* short calls. Worth restarting and watching.

**Pallavi Kiran came back for five days and left again.** A new campaign,
`Calls | ABO | Hyderabad | Ara + Top Performers`, ran 6–9 Oct beside one last day
of `Kiran | Calls — 3 Numbers | ABO` on the 5th: ₹11,741.08 for 94 calls,
**₹124.91 each** — the dearest line anywhere in this report. Nothing since the 9th.

**Website leads are now a quarter of the budget.** `Enquiry LP` spent ₹37,980.16
for 211 "Contact-good lead" custom conversions, **₹180.00 each**, against
₹184.41 over its three September days. Still out of every cost-per-call figure.

### Reconciliation this refresh

- **September: clean.** Campaign rows equal each account's own daily spend *and*
  impressions on all thirty days, both accounts, to the paisa. Month totals match
  the accounts' own period totals exactly (₹1,29,627.08 and ₹1,97,583.42).
- **October: two sub-rupee gaps, both on days Meta is still settling.**
  1. **23 Oct:** campaign day rows add to ₹13,942.07 against ₹13,941.93 on the
     account's own day row — **14 paise apart** (7788091092 +₹0.06,
     094906 31010 +₹0.08). Same class of event as the ₹28.35 part-day gap
     recorded below; it should settle.
  2. **Month aggregate:** the Pallavi Halcyon account's own *period* total reads
     ₹1,42,532.45 and 18,27,201 impressions, against ₹1,42,531.85 and 18,27,189
     from the sum of its *daily* rows — **60 paise and 12 impressions**. The page
     uses the campaign period totals, which equal the daily sum exactly.
- **September calls: a 4-call attribution gap, and the page says so.** Meta's
  campaign totals for the month report **4,539** calls while its own day rows add
  to **4,535** (`ad set level 3 camp` 1,102 against 1,099, `new 3 ads 8585` 271
  against 270) — calls attributed after the day closed. The headline, campaign
  table and funnel use the month totals; the day table shows the day rows; the
  September `partNote` states the difference. October has no such gap (1,729 both
  ways).
- Every 20s/60s division landed on a whole number, in both months, for all
  twenty campaign-periods.
- Age rows sum to each campaign's month total on spend and calls. ₹3.55 and one
  call land in an `Unknown` band in September, 74 paise and no calls in October;
  both are omitted from the age table, and each month's `ageIntro` says so.

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across the whole of
   September and 1–23 October. The nearest thing to it since is October's
   `ABO | Calls | 7788 + 7272 + 9490` at ₹36.86 — less than half the ₹76.54 the
   four per-number campaigns paid in October — and it shares the same weakness:
   cheap calls that do not last.

**September (1–30, complete).** ₹69.07 a call, 15% above the August average,
tracking August's second half (₹72.36). The month ended cheaply — ₹55.18 on the
29th and ₹67.65 on the 30th — which is what pulled it in from ₹69.65 at the
28th, but the daily series stays noisy (₹56.76 on the 23rd, ₹78.02 on the 26th),
so read the fall as two good days, not a trend.

The gap is one account: Pallavi Halcyon ₹58.81 a call, Pallavi Kiran ₹76.94 on
close to twice the spend. `ad set level 3 camp` remains the standout at
**₹45.77** across 1,102 calls; the archived `4 Numbers` campaign did 469 calls at
₹67.68, cheaper than `Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two
dearest lines, `New Leads Campaign` (₹95.69) and its copy (₹94.47), both stopped
by the 23rd, and the account went dark from the 28th.

**October (1–23).** ₹67.26 a call — the first month-to-date under September, and
entirely one campaign: see **What October says so far** above. ₹79.42 without it.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → ₹564.60 → **₹572.08** across eight cuts of September, against
August's ₹507.57 — and October so far is **₹717.86**, the worst yet. The Kiran
lines hold callers best (4 Numbers ₹460, New Leads ₹480, 3 Numbers ₹484 per
60s call); Pallavi Halcyon's cheap calls are short (`ad set level 3 camp` ₹664,
`7788- call ads-new` ₹1,825). The earlier claim that 22 Sep was "the best day of
the month on duration" was removed — it rested on a five-day comparison.

**The four per-number campaigns, three days in September and then all of
October.** September 28–30: ₹21,528.69, 347 calls, ₹62.04 — from ₹46.62
(8585072072, 117 calls) to ₹104.71 (7788091092, 51 calls). October 1–23:
₹85,419.43, 1,116 calls, ₹76.54 — from ₹59.68 (9490631010, which ran only to the
9th) and ₹65.96 (094906 31010, the renamed 8585072072) up to ₹92.55
(7788091092). **7788091092 is still the weak one**, dearest per call in both
months and dearest per minute-long call (₹846) in October. The two cheapest
lines are also the two that hold callers longest — ₹631 and ₹693 a 60-second
call — which is the pair of facts that usually means the number itself is being
answered better.


## 20s and 60s calls are derived, not reported

There is **no count field** for call duration. Meta returns only an average cost
per connect, so each figure is:

    calls20s = spend / cost_per_action_type:click_to_call_native_20s_call_connect
    calls60s = spend / cost_per_action_type:click_to_call_native_60s_call_connect

**Every division must land on a whole number** — that is the check that the
derivation is sound. Assert it; if one does not, something is wrong. (Confirmed
for all 20 campaign-periods in the current data: 13 in September, 7 in October.)
Same method as `o2-reports`.

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
age rows — lives in the `MONTHS` object keyed `aug` / `sep` / `oct`. **To add a
month, add a `DAILY_*` array and a `MONTHS` entry, then add one
`<button class="tab">` with a matching `data-month`.** Nothing else is
month-specific. (October was added exactly that way on 24 Oct 2026 — three edits,
no changes to any rendering code.)

- **Label each month's campaign rows with the name the campaign ran under that
  month.** Campaign renames happen: `120255796887700348` was
  `Halcyon | Call 8585072072 | TS only | All days` through September and
  `Halcyon | Call 094906 31010 | TS only | All days` from 6 Oct. Pull
  `ads_account_get_activity_logs` with `event_category: "campaign"` every refresh
  and look for `Campaign name updated`; a rename that changes the phone number in
  the name changes what the row *means*, even though the id and its history are
  continuous. Unlike the `elixir-reports` ad-level trap, a campaign rename here
  came with no creative-replacement or Pending Review event — check for those too
  before carrying history forward.
- **Meta's campaign period totals and its own day rows can disagree on calls.**
  In September the month totals report 4,539 calls against 4,535 from the day
  rows. Keep the headline, campaign table and funnel on the period totals (they
  are what Ads Manager shows, and they make the campaign table, age table and
  funnel agree), leave the day table on the day rows, and say so in that month's
  `partNote`. Do not reconcile them by editing either set.

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
- Update the snapshot date in the masthead and in this README.
