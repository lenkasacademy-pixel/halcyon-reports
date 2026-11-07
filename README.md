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

**Scope: three tabs, all complete months.** August 2026 (1–31), September 2026
(1–30) and October 2026 (1–31). No tab carries a part-day: Meta keeps revising
the most recent ~48h and the live part-day moves between calls minutes apart, so
a month is only tabbed once it is closed. The range under each tab name is read
off that month's own `DAILY_*` rows at load, so it cannot drift from them, and
**the tab that opens is the last key in `MONTHS`**, derived rather than named —
the page opened on August for six weeks because `MONTHS.aug` was hard-coded.

**November is deliberately not a tab.** See *Three result types* below: it is a
live part-month and it introduced WhatsApp conversations, which the `DAILY_*` row
shape has no field for. Its figures are in the snapshot section and in the page
footer, in prose.

## What it shows

- Amount spent, phone calls placed, blended cost per call, reach.
- A three-panel day-wise chart on one shared calendar: daily spend stacked by
  account (with the website-lead spend split out), calls placed stacked by
  account, and cost per call against that period's average. One hover reads all three.
- A two-up comparison card carrying each tab's headline finding (August's
  1–9 vs 10–31 split; September against the August month; October's bundled-ABO
  campaign against the four single-number ones).
- A **call-quality funnel**: placed → 20s+ → 60s+, with each step's share of
  placed calls and its true cost.
- Per-campaign totals for the call campaigns and, separately, the website-lead
  campaigns.
- Calls and cost per call by age band, both accounts combined.
- The full day-by-day table for the selected month.

## Snapshot

Frozen **7 Nov 2026, 8:10 am IST**, data window **1 August – 31 October**.
September is now closed and **October is a new tab**. The report had been stuck
at 28 September for close to six weeks while ₹1,68,509 of October spend went
unreported.

> **September's last two days were the heaviest call days of the month.** The
> 29th and 30th were held out of the last cut as a live part-day. Settled, the
> 29th is ₹11,858.31 for 167 calls and the 30th ₹10,816.72 for 116 — the two
> biggest call days Pallavi Halcyon ran in September — and they pull the month's
> cost per call from ₹69.65 down to **₹69.07**. The 28th settled up ₹21.14
> (impressions +293) with its call count unchanged.
>
> **A zero-spend campaign still books calls — pull zero-spend days.** My first
> September pull came back 4 calls short of the published 28 Sep figure of 68.
> Nothing was wrong with the published number: `new 3 ads 8585` (1 call) and
> `ad set level 3 camp` (3 calls) had **stopped spending** by the 28th and still
> received late-attributed taps on it. October has one more, on the 17th, and the
> 25th carries one on zero spend too. Filtering the daily pull to days with spend
> loses them and the month comes out short. Same class of bug as the archived
> campaign, different mechanism.
>
> **A campaign was renamed.** `Halcyon | Call 8585072072 | TS only | All days`
> now reads `Halcyon | Call 094906 31010 | TS only | All days`
> (`120255796887700348`). The id is unchanged and the activity log shows a name
> change with no creative swap and no Pending Review, so history carries forward
> safely — unlike the `elixir-reports` case where a rename hid a creative
> replacement. The published September figure for it (₹1,168.72 / 27 calls on the
> 28th) is now ₹5,455.00 / 117 across 28–30 Sep.
>
> **The August tab was contradicting itself, and that is now fixed.** Its Reach
> tile read *23.4L impressions, 6,921 link clicks* while its own day table footed
> at **50,47,184 and 27,226** — both visible to a client on the same tab. The day
> rows are the correct side: August's reach x frequency
> (11,39,310 x 2.68 + 6,12,279 x 3.25) independently implies 50,43,257, within
> 0.08% of them, and the carried pair looks like one account's share. Impressions
> and link clicks are **plain sums of the day rows**, so the second copy has been
> deleted from all three `MONTHS` entries and the tile now derives them
> (`dSum(7)` / `dSum(9)`). This changes a published August figure; it corrects it.
>
> **`reachSum` must come from the account pull, not the campaign rows.** Summing
> campaign-level reach for 28 Sep gave 80,542 against the account's own 78,435 —
> reach de-duplicates *within* an account, so campaign reach double-counts. The
> three new September days and all of October are built from the account-level
> daily pull.

| | August (1–31) | September (1–30) | October (1–31) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,68,508.95 |
| Impressions | 50,47,184 | 45,42,427 | 21,36,472 |
| Link clicks | 27,226 | 14,574 | 10,716 |
| Calls placed | 5,144 | 4,539 | 1,834 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.45** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 442 (24.1%) · ₹288.15 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 172 (9.4%) · ₹740.49 |
| Website-lead spend | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹41,144.86 / 226 |
| Pallavi Halcyon, call ads | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,15,623.01 / 1,740 / ₹66.45 |
| Pallavi Kiran, call ads | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 |
| Days with any spend | 31 of 31 | 30 of 30 | **23 of 31** |

(September and October account rows are **call spend only**; website-lead spend
sits outside them. August's Pallavi Halcyon row is total spend with a call-only
cost per call — that inconsistency is in the August figures as published and has
been left alone.)

Previous cuts: 1–22 Sep (published 28 Sep) ₹2,34,692.62 · 3,284 calls · ₹70.21;
1–28 Sep (published 29 Sep) ₹3,04,514.33 · 4,256 calls · ₹69.65.

**November 1–7 is not on the page.** Pallavi Halcyon only; Pallavi Kiran has
spent nothing since 9 October. Call ads ₹5,245.18 / 60 calls (₹87.42); website
leads ₹1,188.62 / 13; and **WhatsApp ₹4,160.90 / 56 conversations (₹74.30)** from
`Halcyon | ABO | WhatsApp | 6 numbers | 700 each | Telangana regions`, the only
ACTIVE campaign on either account. Total ₹10,594.70. The 7th is still accruing.

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
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across 1–28 Sep.

**September (1–30), closed.** ₹69.07 a call, **15% above the August month**,
tracking August's second half (₹72.36). The gap is one account: Pallavi Halcyon
₹58.81, Pallavi Kiran ₹76.94 on ₹1,97,583 — nearly two thirds of the month's call
budget bought the dearer calls. `ad set level 3 camp` remains the standout at
**₹45.77** across 1,102 calls; the archived `4 Numbers` campaign did 469 calls at
₹67.68. Kiran's two dearest lines, `New Leads Campaign` (₹95.69) and its copy
(₹94.47), both stopped by the 23rd, and from the 28th the account is dark.

**The four per-number campaigns (28–30 Sep) are not close to each other.** On
roughly equal money — ₹5,340 to ₹5,455 each — they ran a **2.2× spread**:

| Campaign | Spend | Calls | Each | 20s+ | 60s+ |
|---|---|---|---|---|---|
| `Call 094906 31010 \| TS only` (was 8585072072) | ₹5,455.00 | 117 | **₹46.62** | 37 (32%) | 10 |
| `Call 9490631010 \| TS+AP` | ₹5,347.17 | 97 | ₹55.13 | 17 (18%) | 5 |
| `Call 7272897897 \| TS+AP` | ₹5,386.31 | 82 | ₹65.69 | 19 (23%) | 6 |
| `Call 7788091092 \| TS only` | ₹5,340.21 | 51 | **₹104.71** | 12 (24%) | 4 |

The ranking holds on all three measures — 094906 31010 is cheapest on placed,
20-second and minute-long calls; 7788091092 dearest on all three. Those four
produced 347 of the 351 calls booked on 28–30 Sep; the other four are the
late-attributed taps described above.

**October (1–31): the one finding to put in front of the client.**
`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each` (`120255979446760348`)
ran 9–24 Oct — **inside the same window as the four single-number campaigns, on
the same numbers** — and bought calls at **₹37.11** while they averaged **₹79.64**
(₹92,380.71 / 1,160 calls over 1–25 Oct). On a fifth of their spend it produced
45% as many calls. It is the cheapest call line on either account since August's
`Calls — Age 35+ | FB only | CBO` (₹19.60), and the lesson is the same: letting
Meta move money between numbers beats pinning a budget to each number.

It holds on connected calls, which is the test a cheap-call campaign usually
fails: **₹172.41 per 20-second call** against ₹287.40 (094906 31010), ₹290.05
(9490631010), ₹333.86 (7272897897) and ₹437.64 (7788091092). On minute-long calls
it is mid-pack at ₹695.81, because only 5.3% of its calls reach a minute against
11.2% on 7788091092 — it buys many more short conversations, not more long ones.

**It was paused on the 24th**, and what started on the 29th is three more
single-number campaigns on ₹500/day — the structure that cost twice as much. They
have ₹3,759.58 and 55 calls between them (₹68.36), too few days to judge but
already nowhere near ₹37.

**October only ran on 23 of 31 days.** Nothing was spent on 17–20 or 25–28 Oct,
and the 21st ran website ads only. At October's own daily rate those eight dark
days are roughly ₹58,000 of delivery not bought. The day rows carry explicit
zeros for them, so the gap shows as data rather than as missing days.

**Pallavi Kiran ran five days all month** (5–9 Oct, ₹11,741.08) and has spent
nothing since. `Calls | ABO | Hyderabad | Ara + Top Performers` is the best line
either account has recorded **on duration** — 38.6% past 20 seconds, 19.3% past a
minute — but it cost ₹126.34 a call, the dearest of the month. Cheap calls and
long calls still have not come from the same campaign.

**Website leads tripled and became a quarter of the budget:** ₹41,144.86 (24% of
October) for 226 leads at ₹182.06, against ₹13,712.53 and 67 in September. Both
October rows optimise for the *same* custom conversion, so for the first time the
two website-lead counts are comparable with each other — still not with the
`HContacted` rows on the August and September tabs.

**The minute-long call has risen at every single cut:** ₹497 → ₹503 → ₹512 →
₹526 → ₹543 → ₹546 → ₹565 → ₹572 (Sept) and now **₹740.49** for October — 46%
above August's ₹507.57. It is the one figure on this page with a steady
direction, and October's is the sharpest jump yet.

**Age inverted between the two months.** September's cheapest band was 18–24 at
₹55.56; October's is **65+ at ₹58.07**, with 18–24 the *dearest* at ₹100.43 on
only 22 calls (almost all from Pallavi Kiran's four days — read it as a small
sample, not a shift). October's three middle bands sit within ₹5 of each other
and carry 78% of the money.

## 20s and 60s calls are derived, not reported

There is **no count field** for call duration. Meta returns only an average cost
per connect, so each figure is:

    calls20s = spend / cost_per_action_type:click_to_call_native_20s_call_connect
    calls60s = spend / cost_per_action_type:click_to_call_native_60s_call_connect

**Every division must land on a whole number** — that is the check that the
derivation is sound. Assert it; if one does not, something is wrong. (Confirmed
for all **23 campaign-periods** in the September and October data, 46 divisions.)
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
one to watch: 132 calls, only 8 past 60 seconds, at ₹1,825 each. October's
bundled ABO campaign is the same shape in miniature: cheapest on placed and on
20s calls, only mid-pack per minute. **Quote both rates or the cheap campaign
looks better than it is.**

## Three result types — do not merge them

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

From 28 Sep both `Enquiry LP` campaigns optimise for the **custom conversion**
`offsite_conversion.custom.1564834054962652` ("Contact-good lead"), a fourth
distinct lead event — comparable with each other but with nothing above them.

**WhatsApp conversations are the third type, and they are the reason November has
no tab.** `Halcyon | ABO | WhatsApp | 6 numbers | 700 each | Telangana regions`
(`120256437300820348`, ACTIVE) reports
`actions:onsite_conversion.messaging_conversation_started_7d` — ₹4,160.90 for 56
conversations over 1–7 Nov. The `DAILY_*` row shape has fields for call spend and
website-lead spend only. Putting WhatsApp spend in the website-lead column would
merge two result types, which this report does not do; leaving it out of the row
would break the account reconciliation by ₹4,160.90. **So November is reported in
prose until someone decides on a messaging column.** This is the same choice
`o2-reports` already makes for its own WhatsApp campaign. A human should decide
between (a) adding `a1MsgSpend` / `a1Conversations` to the row shape and a fourth
band to the spend chart, or (b) keeping messaging in prose permanently.

The page names the event on every row and keeps all of this spend **out of cost
per call**. Blending the website-lead spend in reads ₹70.38 for September's calls
and overstates what a call costs — don't.

## Refreshing

`DAILY_AUG` / `DAILY_SEP` / `DAILY_OCT` rows are
`[day, a1CallSpend, a1Calls, a1WebSpend, a1WebLeads, a2CallSpend, a2Calls, impressions, reachSum, linkClicks]`
where `a1` = Pallavi Halcyon, `a2` = Pallavi Kiran. `day` is the day of month.

Everything else a tab shows — headline totals, narrative copy, campaign tables,
age rows — lives in the `MONTHS` object keyed `aug` / `sep` / `oct`. **To add a
month, add a `DAILY_*` array and a `MONTHS` entry, then add one
`<button class="tab">` with a matching `data-month`.** Nothing else is
month-specific: the open tab is the last `MONTHS` key, the range under each tab
name comes from its own day rows, and whether the chart's reference line says
"month average" or "period average" is derived by `monthComplete()` from whether
the last day row is that calendar month's last day. Append new months at the end
of `MONTHS` — the open tab follows key order, not label order.

Pull with Meta MCP `ads_get_ad_entities`, `level: "campaign"`,
`time_increment: "1"`, one call per account.

- **Pull zero-spend days, and never filter the daily response to days with
  spend.** Meta attributes a call tap to the day it happened, so a campaign that
  has already stopped keeps booking calls on days it spends ₹0: 4 of September's
  calls (28 Sep) and 1 of October's (17 Oct) arrive that way, and the 25th of
  October carries one too. Dropping ₹0 rows makes the month come out short
  against the campaign totals and looks like a reconciliation failure.
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
  An `Unknown` band is omitted from the age table: **₹3.55 and 1 call in
  September, ₹0.74 and 0 calls in October.** The archived `4 Numbers` campaign
  has no per-age `results` either, so its age-band calls are derived from its
  per-band cost per call the same way its monthly total is — all six bands divide
  to whole numbers (138 / 136 / 82 / 61 / 33 / 19 = 469).
- **A renamed campaign needs the activity log checked before history is carried
  forward.** `8585072072` → `094906 31010` was a pure rename (same id, no
  creative swap, no Pending Review), so carrying it forward is safe. Confirm that
  with `ads_account_get_activity_logs` rather than assuming it — `elixir-reports`
  was burnt by a rename that hid a creative replacement on the same ad id. Also
  **set `limit` high** on that call: a `limit: 120` request returned exactly 120
  entries and silently truncated; `limit: 1000` returned 230.
- **`impressions` and `clicks` are no longer fields.** They are summed from the
  day rows at render time, because a month total that is a plain sum of the rows
  has no business being stored twice — the August entry carried a wrong pair for
  weeks. Only `reach` and `freq` are carried, because de-duplicated reach genuinely
  cannot be derived from the rows. Do not re-add them.
- `reachSum` is the sum of each day's reach and double-counts people across days.
  Meta's de-duplicated reach, from a call *without* `time_increment`, quoted on
  the Reach tile only: August 11,39,310 (Pallavi Halcyon, frequency 2.68) and
  6,12,279 (Pallavi Kiran, 3.25); September 8,00,412 (2.44) and 8,37,451 (3.09);
  October 8,55,599 (2.34) and 90,931 (1.46).
- **`reachSum` comes from the account-level daily pull, never from campaign
  rows.** Reach de-duplicates within an account, so adding campaigns up
  over-counts: for 28 Sep the campaign sum was 80,542 against the account's
  78,435. Spend and impressions can be summed from campaigns; reach cannot.
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
