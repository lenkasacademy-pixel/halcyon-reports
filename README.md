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
calls the network. **The page opens on the newest month**, worked out as the last
key of `MONTHS` rather than a named one, so adding a month needs no change there.

**Scope: three tabs.** August 2026 (1–31), September 2026 (1–30, now complete)
and October 2026 (1–30). October stops at the 30th — Meta keeps revising the most
recent ~48h, and 31 October had taken only ₹165.41 when this was pulled. The range
under each tab name is read off that month's own `DAILY_*` rows at load, so it
cannot drift from them.

## What it shows

- Amount spent, phone calls placed, blended cost per call, reach.
- A three-panel day-wise chart on one shared calendar: daily spend stacked by
  account (with the website-lead spend split out), calls placed stacked by
  account, and cost per call against that period's average. One hover reads all three.
- A two-up comparison card carrying each tab's headline finding.
- A **call-quality funnel**: placed → 20s+ → 60s+, with each step's share of
  placed calls and its true cost.
- Per-campaign totals for the call campaigns and, separately, the website-lead
  campaigns.
- Calls and cost per call by age band, both accounts combined.
- The full day-by-day table for the selected month.

## Snapshot

Frozen **31 Oct 2026, 11:45 am IST**. September is closed; October runs to the 30th.

| | August (1–31) | September (1–30) | October (1–30) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,65,852.12 |
| Calls placed | 5,144 | 4,539 | 1,814 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.27** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 435 (24.0%) · ₹288.85 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 170 (9.4%) · **₹739.11** |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,13,907.14 / 1,720 / ₹66.23 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / **₹124.91** |
| Website-lead spend | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹40,203.90 / 211 |

(September and October account rows are **call spend only**; website-lead spend
sits outside them. August's Pallavi Halcyon row is total spend with a call-only
cost per call — that inconsistency is in the August figures as published.)

All figures are **ex-GST** (Meta bills 18% GST on top in India). Unlike
`o2-reports`, this page does not show a GST-inclusive billed total — if the
client asks for one, add it, don't silently change the per-call numbers.

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the best of any month by a
   wide margin, on ~₹1,000/day. Still ₹0.00 across September and October.

**September closed at ₹69.07**, 15% above the August average and tracking
August's second half. It improved as it went: ₹70.24 over 1–22, ₹65.99 over
23–30, and ₹61.34 over the last three days. `ad set level 3 camp` remains the
standout at **₹45.77** across 1,102 calls.

**October's result is the structural one, and it is the clearest this report has
carried.** Splitting the three clinic numbers across **four per-number call
campaigns** bought 864 calls at **₹68.09** over 1–10 Oct. Putting the same
numbers into **one consolidated ABO campaign** (`Halcyon | ABO | Calls | 7788 +
7272 + 9490 | 600 each`, `120255979446760348`) from the 9th bought 525 calls at
**₹37.11**. When three per-number campaigns were switched back on from the 22nd
they ran at **₹113.35** — 296 calls on ₹33,551, their worst stretch yet. The
consolidated campaign beat the split setup in both of its windows, by 45%
against the better one. **It is the recommendation to put to the client.**

The caveat: the consolidated campaign's calls are cheap and *short*. ₹172.41 per
20-second call is less than half the next best line, but 21.5% of its calls hold
twenty seconds against the account's own 24.0%, and its minute-long call costs
₹695.81 — middling. Watch duration before the whole budget moves across.

**Pallavi Kiran has effectively stopped.** Five days in October (5–9), ₹11,741,
94 calls at **₹124.91** — its dearest ever, against ₹76.94 in September and
₹68.79 in August. Nearly all of it is one new campaign, `Calls | ABO | Hyderabad
| Ara + Top Performers`, at ₹126.34 a call. On this evidence the money belongs on
Pallavi Halcyon.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 → ₹543
→ ₹546 → ₹565 → ₹572 → **₹739** across the refreshes recorded here. October is
the largest single jump in the run, and 20-second and 60-second shares both fell
(24.0% and 9.4%, from 29.3% and 12.1%).

**Two long delivery stops in October**: nothing served 17–20 Oct or 25–28 Oct.
Neither is explained here; the activity log was not pulled for them.

**Website leads are back to a quarter of the budget** — ₹40,204 in October
against ₹13,713 in September. One campaign did all of it: `Enquiry LP | Mon–Sat
9–5`, ₹38,550 for 211 custom-conversion leads at **₹182.70**. Its replacement,
`Enquiry LP | Daily 1000`, has taken ₹1,653.93 over the 29th and 30th with
**no conversions reported at all** — its cost-per-conversion key is absent, which
is how a true zero reads here. Two days is not a verdict, but check the event is
firing for it.

## A campaign was renamed at Meta

`Halcyon | Call 8585072072 | TS only | All days` (`120255796887700348`) now reads
**`Halcyon | Call 094906 31010 | TS only | All days`** — same campaign id, same
spend, impressions and call counts carried forward. So it is a rename, not a
number or creative swap, and the September rows were relabelled in place. Two
things to watch: the account now has **two** campaigns naming 094906 31010 (one
`All days`, one `Daily 500`) and **none** naming 8585072072, and `094906 31010`
and `9490631010` are the same phone number written two ways. Check the id, not
the name.

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
`impressions` and `linkClicks` are **both accounts added**, and `linkClicks` is
Meta's `link_click`, **not** `clicks` — September's `clicks` is 60,664 against
14,574 link clicks, so pulling the wrong field inflates the column fourfold.

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
  appending. **And re-pull the paused campaigns too, not just the ones that spent.**
  On this refresh the 28 September day row was 4 calls short of the campaign
  totals until `new 3 ads 8585` and `ad set level 3 camp` were pulled for that
  day: both spent nothing on it and each carried late-attributed calls. Meta also
  settled 28 September up by ₹21.14 a month after it was published.
- **Filtering `amount_spent GREATER_THAN 0` alongside the `effective_status`
  filter works** when there is no `time_increment`, and cuts a ~30-campaign
  listing to the handful that actually spent. It is silently ignored once
  `time_increment` is set.
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
