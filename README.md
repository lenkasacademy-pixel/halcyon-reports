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
complete) and October 2026 (1–22). **October opens by default** — the newest tab
is the active one. October stops at the last complete day: Meta keeps revising
the most recent ~48h, and the live part-day moves between calls minutes apart.
Showing it would read as a collapse in spend that is not real. The range under
each tab name is read off that month's own `DAILY_*` rows at load, so it cannot
drift from them.

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

Frozen **23 Oct 2026, 11:15 am IST**. September is now a **complete month**
(1–30) and **October has been added as a third tab** (1–22).

> ### Read this first: a campaign was renamed and its name no longer matches its ads
>
> On **6 Oct 2026 at 10:14 am** (Power Editor, actor Abhijeet Lenka) the campaign
> `120255796887700348` was renamed:
>
>     Campaign name updated
>     old_value "Halcyon | Call 8585072072 | TS only | All days"
>     new_value "Halcyon | Call 094906 31010 | TS only | All days"
>
> **It is not a clean switch of number.** Over 6–22 Oct that campaign ran seven
> ads: six still carry the **8585** creative (₹8,681.92, 107 calls) and only one
> carries **9490** (₹1,638.31, 8 calls, first delivered 9 Oct). So 84% of its
> post-rename spend is still the 8585 number while the campaign is labelled 9490.
>
> Handling in this report: **September's row keeps the name the campaign carried
> then** (`Halcyon | Call 8585072072 | TS only | All days`), so the 28–30 Sep
> history stays attached to the number that actually ran. **October's row is
> labelled `Halcyon | Call 094906 31010 (renamed 6 Oct, mixed 8585/9490 ads)`**
> and a footer note says so. Treat the per-number split of that line as
> unverified until the client confirms which number the ads should be dialling.
>
> This is the same trap `elixir-reports` documents at ad level. Pull
> `ads_account_get_activity_logs` with `event_category: "campaign"` on **every**
> refresh and check `Campaign name updated` against the ad names underneath.

> ### Corrected: August's impressions and clicks KPIs were wrong
>
> `MONTHS.aug` declared `impressions: 2338227` and `clicks: 6921`. The August day
> rows sum to **5,047,184** impressions and **27,226** clicks, and Meta's own
> account totals for 1–31 Aug confirm the day rows exactly (Pallavi Halcyon
> 3,054,990 + 1,992,194; 22,207 + 5,019). The published August tab was
> understating impressions by 54% and clicks by 75%. Both constants are now
> corrected. No other August figure moved — spend, calls, cost per call, reach
> and the campaign tables all reconciled.

| | August (1–31) | September (1–30) | October (1–22) |
|---|---|---|---|
| Spent (total) | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,40,244.94 |
| Call spend | ₹3,08,602.82 | ₹3,13,497.97 | ₹1,03,053.36 |
| Calls placed | 5,144 | 4,539 | 1,613 |
| Cost per call | **₹59.99** | **₹69.07** | **₹63.89** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 395 (24.5%) · ₹260.89 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 147 (9.1%) · ₹701.04 |
| Website-lead spend | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹37,191.58 / 190 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹91,312.28 / 1,519 / ₹60.11 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 |

(September and October account rows are **call spend only**; website-lead spend
sits outside them. August's Pallavi Halcyon row is total spend, its cost per call
call-only — that inconsistency is in the August figures as published.)

Previous cut (1–28 Sep, published 29 Sep): ₹3,04,514.33 · 4,256 calls · ₹69.65.

### September, finished

The two days the last cut could not see were the biggest Pallavi Halcyon days of
the month: **29 Sep ₹11,858.31 for 167 calls (₹55.18)** and **30 Sep ₹10,816.72
for 116 calls (₹67.65)**, both from the four per-number campaigns opened on the
28th. Because both ran below the month average, the headline *fell* from ₹69.65
to **₹69.07** even as spend rose. Meta also revised **28 Sep up by ₹21.14** after
publication (all five live campaigns, calls unchanged). Pallavi Kiran spent
nothing from the 28th onward, so the last three days are Pallavi Halcyon alone.

### October: consolidating the call campaigns halved the cost per call

October is three regimes, not one month:

| Window | What ran | Spend | Calls | Each |
|---|---|---|---|---|
| 1–9 Oct | four per-number call campaigns | ₹71,709.89 | 998 | **₹71.85** |
| 10–16 Oct | one consolidated ABO campaign | ₹17,992.67 | 478 | **₹37.64** |
| 17–21 Oct | dark (no call spend at all) | ₹0 | 1 | — |
| 22 Oct | per-number campaigns switched back on | ₹13,350.80 | 136 | **₹98.17** |

`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each` (created 9 Oct, now
PAUSED) returned **519 calls at ₹36.86** — the cheapest line on either account
in any month, beating `ad set level 3 camp`'s ₹45.76. On 21 Oct it was paused and
on 22 Oct the three per-number campaigns were reactivated; that day cost ₹98.17 a
call, the dearest of the month.

**That is the decision to put in front of the client:** the consolidated
structure bought calls at roughly half the price of the per-number split, and the
account has just gone back to the expensive one.

Watch the quality trade, though — it is the same one `Calls — Age 35+` showed in
August. The ABO campaign's calls skew short: only **5.4%** reached a minute
against **11.1%** on the 9490 per-number line. October overall is worse on
duration than September at every step: 24.5% past 20s (September 29.3%) and 9.1%
past a minute (12.3% in the 1–28 cut, 12.1% over the full month), at ₹260.89 and
₹701.04 each.

**Pallavi Kiran is nearly finished.** It woke for five days (5–9 Oct, ₹11,741.08)
at **₹124.91 a call** — far worse than anything it did in September — and has
spent nothing since the 9th. A new campaign, `Calls | ABO | Hyderabad | Ara + Top
Performers`, took ₹10,486.48 of that for 83 calls (₹126.34).

**Website leads are now the larger half of the Pallavi Halcyon budget.**
`Enquiry LP` took ₹37,191.58 for 190 Contact-good leads (₹195.75 each) — 29% of
everything the two accounts spent in October, against ₹91,312.28 on calls. Its
daily lead count is very uneven (42 on the 15th, 2 on the 14th, 3 on the 6th and
the 9th), which is worth checking against the clinic's own record of what
arrived. It still optimises a **custom conversion**
(`offsite_conversion.custom.1564834054962652`) — a fourth distinct lead event,
kept out of every cost-per-call figure.

### Reconciliation

Campaign rows equal each account's own `level: "ad_account"` daily spend on
**every one of the 52 days** across both months, both accounts. Every 20s/60s
division lands on a whole number, and the archived `4 Numbers` campaign's derived
daily calls still divide exactly (76, 111, 102, 93, 87 = 469).

Two sub-rupee drifts, both Meta's own rounding, neither material:

- **October age rows sum to ₹1.03 more** than the campaign totals, across three
  campaigns (7788091092 +₹0.78, 094906 31010 +₹0.22, 7272897897 +₹0.03). Call
  counts match exactly. September's age rows reconcile to ₹0.00.
- **Pallavi Halcyon's October period total is ₹1.03 above the sum of its own
  daily rows** (₹1,28,504.89 vs ₹1,28,503.86) for the same reason. The page is
  built from the daily rows.

One call in September and one in August fall in the `Unknown` age band and are
omitted from the age table only, as documented below.

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across all of
   September and October.

**September (1–30, complete).** ₹69.07 a call, 15% above the August average,
tracking August's second half (₹72.36). The last two days ran below the month
(₹55.18 and ₹67.65), which is why finishing the month *lowered* the headline
from the ₹69.65 published at the 28th.

The gap is one account: Pallavi Halcyon ₹58.81 a call, Pallavi Kiran ₹76.94 on
nearly twice the spend. `ad set level 3 camp` remains the standout at **₹45.76**
across 1,102 calls; the archived `4 Numbers` campaign did 469 calls at ₹67.68,
cheaper than `Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two dearest
lines, `New Leads Campaign` (₹95.69) and its copy (₹94.47), both stopped by the
23rd, and the account went dark from the 28th.

**October (1–22).** ₹63.89 a call — better than September, still above August.
The whole of that improvement is one week: see the three-regime table above.
`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each` is the new best line on
either account at **₹36.86** across 519 calls, and it is now paused.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → ₹564.60 → **₹572.08** for September across eight cuts, against
August's ₹507.57 — and October is worse again at **₹701.04**. The Kiran
lines hold callers best (4 Numbers ₹460, New Leads ₹480, 3 Numbers ₹484 per
60s call); Pallavi Halcyon's cheap calls are short (`ad set level 3 camp` ₹664,
`7788- call ads-new` ₹1,825). The earlier claim that 22 Sep was "the best day of
the month on duration" was removed — it rested on a five-day comparison.

**The per-number campaigns now have real data.** Over 28–30 Sep they read
₹58.44 across 347 calls, from ₹46.62 (9490631010) to ₹104.71 (7788091092); over
1–9 and 22 Oct, ₹71.85. 7788091092 is still the worst of them on both price and
duration (₹96.83 a call in October, ₹1,335 a minute-long call in September).
Against the consolidated ABO campaign's ₹36.86 the whole per-number structure
looks expensive.


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
age rows — lives in the `MONTHS` object keyed `aug` / `sep` / `oct`. **To add a
month, add a `DAILY_*` array and a `MONTHS` entry, then add one
`<button class="tab">` with a matching `data-month`.** Nothing else is
month-specific. Also move `aria-selected="true"` (and drop the `tabindex="-1"`)
onto the new tab, point `#report`'s `aria-labelledby` at it, and set
`let M=MONTHS.<new>` so the newest month opens first — those four are the only
places the default month is named.

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
  Expect sub-rupee drift: October's age rows run ₹1.03 above the campaign totals
  on three campaigns (call counts still match exactly), September's reconcile to
  ₹0.00. A few paise and 1 call land in an `Unknown` band and are omitted from
  the age table.
- **Check `ads_account_get_activity_logs` with `event_category: "campaign"` for
  `Campaign name updated` on every refresh**, and compare the new name against
  the ad names under that campaign. A campaign renamed to a different clinic
  number while still serving the old number's creatives will otherwise re-label
  its own history — see the warning at the top of this file.
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
