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
calls the network. The page opens on the newest month.

**Scope: three tabs.** August 2026 (1–31, complete), September 2026 (1–30,
complete) and October 2026 (1–12).
Each month stops at its last complete day — Meta keeps revising the most recent
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

Frozen **13 Oct 2026, 8:10 am IST**. Three tabs now: August (1-31, complete),
September (1-30, **complete**) and **October (1-12)**, which opens by default.
Each month stops at its last complete day; 13 October is a live part-day and is
left out entirely.

| | August (1-31) | September (1-30) | **October (1-12)** |
|---|---|---|---|
| Spent (incl. website leads) | &#8377;3,62,046.60 | &#8377;3,27,210.50 | &#8377;1,05,626.35 |
| Call spend | &#8377;3,08,602.82 | &#8377;3,13,497.97 | &#8377;80,758.97 |
| Calls placed | 5,144 | 4,539 | 1,222 |
| Cost per call | **&#8377;59.99** | **&#8377;69.07** | **&#8377;66.09** |
| Lasted 20s+ | 1,448 (28.1%) &middot; &#8377;213.12 | 1,328 (29.3%) &middot; &#8377;236.07 | 298 (24.4%) &middot; &#8377;271.00 |
| Lasted 60s+ | 608 (11.8%) &middot; &#8377;507.57 | 548 (12.1%) &middot; &#8377;572.08 | 117 (9.6%) &#183; &#8377;690.25 |
| Pallavi Halcyon | &#8377;2,18,901.90 / 3,063 / &#8377;54.02 | &#8377;1,15,914.55 / 1,971 / &#8377;58.81 | &#8377;69,017.89 / 1,128 / &#8377;61.19 |
| Pallavi Kiran | &#8377;1,43,144.70 / 2,081 / &#8377;68.79 | &#8377;1,97,583.42 / 2,568 / &#8377;76.94 | &#8377;11,741.08 / 94 / **&#8377;124.91** |
| Website-lead spend | &#8377;53,443.78 / 332 | &#8377;13,712.53 / 63 | &#8377;24,867.38 / 117 |

(September and October account rows are **call spend only**. August's Pallavi
Halcyon row is total spend with a call-only cost per call &mdash; that inconsistency
is in the August figures as published and is left alone.)

Previous cut (1-28 Sep, published 29 Sep): &#8377;2,96,435.27 call spend &middot; 4,256 calls
&middot; &#8377;69.65.

## A campaign was renamed, and the number behind it changed

**Read this before comparing the September and October campaign tables.** Campaign
`120255796887700348` was created on 28 Sep as `Halcyon | Call 8585072072 | TS only |
All days`. On **6 Oct 10:14 am** it was renamed to `Halcyon | Call 094906 31010 | TS
only | All days` (activity log, Power Editor, actor Abhijeet Lenka), and on **9 Oct**
a new ad, `9490 | Proven | "1" video`, started delivering under it &mdash; its earlier
ads are all named `8585 | ...`.

So this is not a cosmetic rename: the campaign was **repointed from 8585072072 to
9490631010**, and the account now has two 9490631010 campaigns and no 8585072072 one.
Unlike the elixir case there is no Pending Review in the log, and the rename and the
creative change are five days apart, so the history is not mislabelled by Meta &mdash;
but it is split.

How the page handles it:

- The **September tab keeps the old name** (`Halcyon | Call 8585072072 | TS only | All
  days`), because that is the number it ran in September. Renaming the September row
  would relabel real history, which is the mistake `elixir-reports` records.
- The **October tab uses the current name**, and its `partNote` says the October
  figures for that row cover two phone numbers.
- Same campaign id in both months. If the client wants the two numbers separated, the
  split has to be done at ad level (1-8 Oct is 8585, 9 Oct onward is 9490).

**Always pull the campaign activity log on a refresh** (`event_category: "campaign"`,
`event_type: "Campaign name updated"`). A renamed campaign silently appears as a new
line and the old line silently vanishes; the campaign reconciliation does **not** catch
it, because every total still balances.

## The findings

Cost per call rose **61%** on 10 August: &#8377;44.82 (2,310 calls on &#8377;1,03,528) for
1-9 Aug, &#8377;72.36 (2,834 calls on &#8377;2,05,075) for 10-31 Aug. Two causes, both real:

1. &#8377;53,444 &mdash; 34% of the Pallavi Halcyon budget from the 10th &mdash; moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls - Age 35+ | FB only | CBO` (`120254451805720348`) stopped after
   8 Aug. It returned **410 calls at &#8377;19.60**, the month's best by a wide margin, on
   ~&#8377;1,000/day. Still &#8377;0.00 across September and October.

**September (1-30): dear all month, then it turned.** &#8377;69.07 a call, 15% above the
August average. But 1-22 Sep ran at &#8377;70.24, 23-28 at &#8377;67.63 and **29-30 at
&#8377;60.29** &mdash; the cheapest stretch since early August, and the first sign that the
28 Sep restructure (old call campaigns paused, four new per-number campaigns opened)
was working. Those two days are Pallavi Halcyon alone; **Pallavi Kiran spent nothing
after the 27th.** The four new campaigns were far from equal even in two days:
8585072072 &#8377;46.62 a call against 7788091092 &#8377;104.71 on near-identical spend.

**October (1-12): the consolidated campaign has roughly halved the cost of a call.**
1-8 Oct cost &#8377;70.72 a call; from the 9th it is **&#8377;53.72**, with 10, 11 and 12
October at &#8377;35.21, &#8377;39.82 and &#8377;47.14. One line explains it:
**`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each`** (`120255979446760348`,
created and activated 9 Oct) has taken &#8377;10,189 for **264 calls at &#8377;38.59** &mdash;
the cheapest call campaign on either account since August's Age 35+ line. It replaced
the four per-number campaigns, which all stopped by the 10th.

**7788091092 remains the dearest number**, as flagged at the end of September:
&#8377;15,125 for 144 calls, **&#8377;105.03 each**, against &#8377;49.55 on 094906 31010 and
&#8377;59.68 on 9490631010, all on the same budget.

**Pallavi Kiran is the problem this month.** It ran only 5-9 October and its 94 calls
cost **&#8377;124.91** each, against &#8377;61.19 on Pallavi Halcyon. The new
`Calls | ABO | Hyderabad | Ara + Top Performers` campaign is the whole of it:
&#8377;10,486 for 83 calls at &#8377;126.34. Nothing on that account has run since the 9th.

**October's calls are shorter, not just cheaper** &mdash; and this is the number to keep
in front of the client. 24.4% past 20 seconds against September's 29.3%; 9.6% past a
minute against 12.1%. So cost per 20-second call went **up**, &#8377;236.07 to
&#8377;271.00, and the minute-long call &#8377;572.08 to &#8377;690.25, while cost per call
placed improved. The consolidated campaign is part of that trade: cheapest calls on the
page at &#8377;38.59, but only 5.3% reach a minute (&#8377;727.81 each).

**8 October was the worst single day in either month**: &#8377;9,404 of call spend for
71 calls, &#8377;132.45 each. The 7th was &#8377;89.79. Both predate the consolidation.

**Website leads are now the biggest single line on the account.** Enquiry LP ran every
day of October for &#8377;24,867 and 117 custom conversions (&#8377;212.54 each) &mdash; 24% of
the month's spend, more than any one call campaign. It optimises a **custom conversion**
(`offsite_conversion.custom.1564834054962652`), a fourth distinct lead event, and is
kept out of every cost per call.

All figures are **ex-GST** (Meta bills 18% GST on top in India). Unlike `o2-reports`,
this page does not show a GST-inclusive billed total &mdash; if the client asks for one,
add it, don't silently change the per-call numbers.

## Reconciliation on this refresh

Campaign sums equal each account's own `level: "ad_account"` daily spend **and**
impressions on **all 30 days of September for both accounts**, and on **1-11 October**,
to the paisa. Two gaps, both inside Meta's ~48-hour settling window:

- **12 Oct**: campaign rows +&#8377;0.12 and +4 impressions over the account total.
  Published as is; it is twelve paise.
- **13 Oct**: +&#8377;8.48 and +123 impressions. **This is why October stops at the 12th.**

Every 20s/60s division lands on a whole number, derived per campaign per period (the
sum-of-days derivation differs by 2 calls on `7788- call ads-new - Copy`, which is why
the period figure is the one used). Age rows sum to each month's call spend:
September &#8377;3.55 and 1 call, October &#8377;0.24 and 0 calls land in an `Unknown` band
and are omitted from the age table only.

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
age rows — lives in the `MONTHS` object keyed `aug` / `sep` / `oct`. **To add a month,
add a `DAILY_*` array and a `MONTHS` entry, then add one `<button class="tab">`
with a matching `data-month`.** Nothing else is month-specific. Also point
`let M=MONTHS.xxx` at the newest month so the page opens on it, and move
`aria-selected="true"` and the panel's `aria-labelledby` to the new tab.

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
- Update the snapshot date in the masthead, in the baked-figures comment above
  `DAILY_AUG`, and in this README.
- **Pull the campaign activity log every refresh** and check for
  `Campaign name updated`. See the rename section above.
