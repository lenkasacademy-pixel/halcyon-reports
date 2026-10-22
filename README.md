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
complete) and October 2026 (1–21). October stops at the last complete day — Meta
keeps revising the most recent ~48h, and the live part-day moves between calls
minutes apart. Showing it would read as a collapse in spend that is not real. The
range under each tab name is read off that month's own `DAILY_*` rows at load, so
it cannot drift from them.

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

Frozen **22 Oct 2026, 8:15 am IST**. September is now complete (1–30) and
**October has been added as a third tab** (1–21).

| | August (1–31) | September (1–30) | October (1–21) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,25,632.94 |
| Calls placed | 5,144 | 4,539 | 1,477 |
| Cost per call | **₹59.99** | **₹69.07** | **₹60.73** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 360 (24.4%) · ₹249.17 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 131 (8.9%) · ₹684.75 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹77,961.48 / 1,383 / ₹56.37 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 |
| Website leads | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹35,930.38 / 189 |

Both accounts' rows are **call spend only**; website-lead spend sits outside them.
August's Pallavi Halcyon row is total spend, its cost per call call-only — that
inconsistency is in the August figures as published.

All figures are **ex-GST** (Meta bills 18% GST on top in India).

### ⚠️ A campaign was renamed, and its name no longer matches its ads

> `Campaign name updated`, **6 Oct 2026, 10:14 am**, Power Editor, actor Abhijeet Lenka:
>
>     120255796887700348
>     "Halcyon | Call 8585072072 | TS only | All days"
>  -> "Halcyon | Call 094906 31010 | TS only | All days"
>
> This is the same campaign that the 29 Sep snapshot published as
> **Halcyon | Call 8585072072**. The September tab therefore still calls it
> `8585072072` — that is the number it dialled and the name it carried all through
> September. The October tab uses its current name.
>
> **But the name is now misleading, and somebody should look at it.** Of the seven
> ads in that campaign, six are prefixed `8585 |` (₹19,370 of spend) and only one is
> prefixed `9490 |` — `9490 | Proven | "1" video`, added on 9 Oct for ₹314.82. So a
> campaign named after 9490631010 is still spending almost entirely on 8585072072
> creatives, **and a separate `Halcyon | Call 9490631010 | TS+AP | All days`
> campaign also exists**. Two campaigns now appear to claim the same number while
> one of them runs the other's ads. Nothing in the figures is wrong; the labelling
> is. Pull `ads_account_get_activity_logs` with `event_category: "campaign"` before
> carrying any per-number name forward.

Three other campaigns were renamed on 28 Sep (`Mon–Sat 9–5` → `All days`), which
is cosmetic — same numbers, same ads.

### ⚠️ Calls stopped on 16 October

Every call campaign on both accounts has spent **nothing since 16 October**. Only
the Enquiry LP website campaign has spent since — ₹1,616.01 on the 21st, for zero
conversions. **No status change is logged against any call campaign**, so the
activity log does not explain it. The page states the stop from the data rather
than asserting a cause. Worth checking the account directly.

## What October says

**One new campaign halved the cost of a call.** October splits in two:

| | spend | calls | each |
|---|---|---|---|
| 1–9 Oct (four per-number campaigns) | ₹71,709.89 | 998 | **₹71.85** |
| 10–16 Oct (one consolidated campaign) | ₹17,992.67 | 478 | **₹37.64** |

`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each` was created on 9 Oct and
by the 10th was carrying the account alone. It booked **519 calls at ₹36.86** —
the cheapest call line since `Halcyon | Calls — Age 35+ | FB only | CBO` did
₹19.60 in early August, and against ₹49.55–₹105.03 for the four per-number
campaigns it replaced. This is the clearest result in the report.

**The catch is duration, and it is the same trade the Age 35+ campaign made.**
Only 8.9% of October's calls lasted a minute (September 12.1%), and a minute-long
call now costs ₹684.75 against ₹572.08. The cheap campaign holds 21.4% of callers
past 20s and 5.4% past a minute. Cheaper calls, shorter calls — do not let the
headline settle the question on its own.

**October's per-campaign cost per call:**

| Campaign | Acct | Spend | Calls | Each | 20s | 60s |
|---|---|---|---|---|---|---|
| ABO Calls 7788+7272+9490 | 1 | ₹19,132.26 | 519 | **₹36.86** | 111 | 28 |
| Call 094906 31010 (was 8585072072) | 1 | ₹14,170.55 | 286 | ₹49.55 | 68 | 22 |
| Call 9490631010 | 1 | ₹14,502.32 | 243 | ₹59.68 | 50 | 23 |
| Call 7272897897 | 1 | ₹15,031.32 | 191 | ₹78.70 | 60 | 19 |
| Call 7788091092 | 1 | ₹15,125.03 | 144 | ₹105.03 | 32 | 19 |
| Kiran — 3 Numbers | 2 | ₹1,254.60 | 11 | ₹114.05 | 7 | 4 |
| Calls ABO Hyderabad Ara + Top | 2 | ₹10,486.48 | 83 | ₹126.34 | 32 | 16 |

**Website leads are now 29% of the budget** — ₹35,930 in 21 days against ₹13,713
in all of September, for 189 conversions at ₹190.11. Still the `Contact-good lead`
custom conversion, so still not comparable with HContacted or with phone calls,
and still excluded from every per-call figure.

**Pallavi Kiran came back for five days** (5–9 Oct) and was expensive: ₹11,741 for
94 calls, ₹124.91 each. It has spent nothing since the 9th.

## What September's last three days added

September gained 29 and 30 Sep, and 28 Sep was revised up ₹21.14 (call counts
unchanged). All three days were Pallavi Halcyon alone — Pallavi Kiran spent
nothing from the 28th.

| | call spend | calls | each |
|---|---|---|---|
| 28 Sep | ₹4,465.99 | 68 | ₹65.68 |
| 29 Sep | ₹9,214.92 | 167 | ₹55.18 |
| 30 Sep | ₹7,847.78 | 116 | ₹67.65 |

Those three days ran at ₹61.34 a call against ₹70.24 over 1–22, which pulls the
month from the previously published ₹69.65 (1–28) down to **₹69.07** (1–30). The
four per-number campaigns finished September at ₹46.62 (8585072072, 117 calls),
₹55.13 (9490631010, 97), ₹65.69 (7272897897, 82) and ₹104.71 (7788091092, 51).

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across September and
   October. (October's `ABO | Calls` campaign at ₹36.86 is the closest anything
   has come to it since.)

**September (1–30).** ₹69.07 a call, 15% above the August average, tracking
August's second half (₹72.36). The month got cheaper as it went: ₹70.24 over
1–22, ₹67.80 over 23–27, ₹61.34 over 28–30 — but the daily series is noisy, so
read the last window as the new per-number campaigns being cheaper than what
they replaced, not as a trend within the month.

The gap is one account: Pallavi Halcyon ₹58.81 a call, Pallavi Kiran ₹76.94 on
not quite twice the spend. `ad set level 3 camp` remains the standout at
**₹45.77** across 1,102 calls; the archived `4 Numbers` campaign did 469 calls at
₹67.68, cheaper than `Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two
dearest lines, `New Leads Campaign` (₹95.69) and its copy (₹94.47), both stopped
by the 23rd, and the account went dark from the 28th.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → ₹564.60 → **₹572.08** for September across eight cuts, against
August's ₹507.57 — **and ₹684.75 in October**. The Kiran lines hold callers best
(4 Numbers ₹460, New Leads ₹480, 3 Numbers ₹484 per 60s call); Pallavi Halcyon's
cheap calls are short (`ad set level 3 camp` ₹664, `7788- call ads-new` ₹1,825).
This is the one figure on the page with a steady direction, and October extended
it sharply.

**The four per-number campaigns closed September with three days each**:
₹46.62 (8585072072, 117 calls), ₹55.13 (9490631010, 97), ₹65.69 (7272897897, 82)
and ₹104.71 (7788091092, 51). The earlier one-day read — ₹43.29 to ₹377.06 — was
too small to mean anything; the three-day figures are the ones to use, and
7788091092 stayed the worst line into October (₹105.03).


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

- **Check `event_category: "campaign"` in the activity log for renames, every
  refresh.** On 6 Oct 2026 `Halcyon | Call 8585072072 | TS only | All days` was
  renamed to `Halcyon | Call 094906 31010 | TS only | All days` on the same
  campaign id. A month tab must keep the name the campaign carried *during that
  month*, or September's history silently re-labels itself to a different phone
  number. Same class of bug as the `elixir-reports` creative swap: the totals all
  still balance, so reconciliation will not catch it. Where the name encodes a
  phone number, also check the ad names inside the campaign — after that rename,
  six of its seven ads were still `8585 |` creatives.
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
- Adding a month: one `DAILY_*` array, one `MONTHS` entry, one `<button class="tab"
  data-month=...>`. October was added exactly that way on 22 Oct 2026 and nothing
  else in the file was month-specific, as documented.
