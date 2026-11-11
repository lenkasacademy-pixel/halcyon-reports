# Halcyon Pain Management — Meta Ads calls report

Client-facing report for **Halcyon Pain Management**, covering **both** ad accounts:

| Account | ID | What it runs |
|---|---|---|
| Pallavi Halcyon | `1999324147481098` | Call ads + website-lead campaigns |
| Pallavi Kiran | `694358492762548` | Call ads only |

Live: https://lenkasacademy-pixel.github.io/halcyon-reports/

A single self-contained `index.html` with a **month tab bar** (August /
September / October / November). Figures are baked into the `DAILY_AUG` /
`DAILY_SEP` / `DAILY_OCT` / `DAILY_NOV` arrays and the `MONTHS` object near the
bottom of the file — nothing calls the network.

**Scope: four tabs.** August 2026 (1–31), September 2026 (1–30) and October 2026
(1–31) are complete and settled; November 2026 runs 1–10. November stops at the
last complete day — Meta keeps revising the most recent ~48h, and the live
part-day moves between calls minutes apart. Showing it would read as a collapse
in spend that is not real. The range under each tab name is read off that month's
own `DAILY_*` rows at load, so it cannot drift from them.

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
  campaigns and (from November) the click-to-WhatsApp campaigns. Three tables,
  three result types, never added together.
- Calls and cost per call by age band, both accounts combined.
- The full day-by-day table for the selected month.

## Snapshot

Frozen **11 Nov 2026, 8:10 am IST**. August, September and October are complete
and settled; November covers **1-10 November** (the 11th is a live part-day and
is excluded).

> **A campaign changed what it advertises mid-October, and it got 2.5x dearer.**
> `Halcyon | Call 8585072072 | TS only | All days` (`120255796887700348`) was
> renamed to `Halcyon | Call 094906 31010 | TS only | All days` at **10:14 am on
> 6 Oct 2026** (activity log, Power Editor, actor Abhijeet Lenka) — and in the
> same minute **every ad in it was given a new creative** ("Ad updated",
> old/new creative ids) and its ad set was renamed `8585 | Hyderabad 30km` →
> `9490 | Kukatpally-Chandanagar-Moosapet` and retargeted from Hyderabad +30km
> to three tight radii. Same campaign id, different campaign. It is **split into
> two rows** in the October table: 1-5 Oct as 8585072072 (204 calls at
> **₹40.99**) and 6-24 Oct as 094906 31010 (167 calls at **₹103.09**).
> September's rows keep the 8585072072 name, because that is what ran then.
>
> This is the same trap `elixir-reports` documents at ad level. The tell is the
> activity log, not the reconciliation — every total still balanced.
>
> **Note there are now two campaigns pointed at 9490631010**: this renamed one
> and the separate `Halcyon | Call 9490631010 | TS+AP | All days`. Do not merge
> them.
>
> **November adds a fourth result type.** From 4 Nov the Pallavi Halcyon account
> put most of its budget behind `Halcyon | ABO | WhatsApp | 6 numbers | 700 each
> | Telangana regions`, which reports `onsite_conversion.messaging_conversation_started_7d`.
> That is neither a phone call nor a website lead, so the `DAILY_*` row gained
> two optional trailing fields (see **Refreshing**) and the page gained a
> WhatsApp band, column and table. Its spend is out of every cost-per-call
> figure.

| | August (1-31) | September (1-30) | October (1-31) | November (1-10) |
|---|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.43 | ₹1,68,508.98 | ₹10,594.70 |
| Calls placed | 5,144 | 4,539 | 1,834 | 60 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.45** | **₹87.42** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 442 (24.1%) · ₹288.15 | 17 (28.3%) · ₹308.54 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 172 (9.4%) · ₹740.49 | 6 (10.0%) · ₹874.20 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,15,623.04 / 1,740 / ₹66.45 | ₹5,245.18 / 60 / ₹87.42 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.35 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 | ₹0 / 0 / — |
| Website leads | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹41,144.86 / 226 | ₹1,188.62 / 13 |
| WhatsApp chats | — | — | — | ₹4,160.90 / 56 |

(September, October and November account rows are **call spend only**; the
website-lead and WhatsApp spend sits outside them. August's Pallavi Halcyon row
is total spend, its cost per call call-only — that inconsistency is in the August
figures as published.)

Previous cut (1-28 Sep, published 29 Sep): ₹3,04,514.33 · 4,256 calls · ₹69.65.

All figures are **ex-GST** (Meta bills 18% GST on top in India). Unlike
`o2-reports`, this page does not show a GST-inclusive billed total — if the
client asks for one, add it, don't silently change the per-call numbers.

### What moved this refresh

- **September closed at ₹69.07**, down from the ₹69.65 published at 1-28. The
  29th settled at ₹11,858.31 for 167 calls (₹55.18, the cheapest day since the
  23rd) and the 30th at ₹10,816.72 for 116 (₹67.65). Meta also revised **28 Sep
  up by ₹21.14** after publication (₹8,421.70 → ₹8,442.84, +293 impressions),
  which is what the last cut's unexplained gap on that day was.
- **October is the consolidation month.** `Halcyon | ABO | Calls | 7788 + 7272 +
  9490 | 600 each` started on the 9th, put all three numbers in one campaign,
  and bought **525 calls at ₹37.11** — the cheapest line on either account since
  August's `Age 35+ | FB only | CBO` (₹19.60). Its best days were ₹29.60 (14th)
  and ₹17.97 (16th). **This is the thing to keep.**
- The headline still barely moved (₹69.45) because the cheap fortnight was
  bracketed by dear days: 22-24 Oct ran ₹98.79, ₹113.85 and ₹148.16 a call.
- **Website-lead spend nearly tripled** to ₹41,144.86 — 24% of October's budget,
  against 4% in September. 226 Contact-good lead conversions at ₹182.06.
- **Pallavi Kiran has effectively closed.** ₹11,741.08 across five days
  (5-9 Oct) and nothing since the 9th. Its new `Calls | ABO | Hyderabad |
  Ara + Top Performers` campaign is October's dearest line at ₹126.34 a call.
- **Delivery gaps:** nothing served on 17-20 Oct, 25-28 Oct, or from 6 Nov
  onward. The Pallavi Halcyon WhatsApp campaign still reads ACTIVE while serving
  nothing, so **check the payment method and the account spending limit** — that
  is not a paused campaign.
- **`Halcyon | Calls — Age 35+ | FB only | CBO` is still at ₹0.00** across
  September, October and November. It remains the best cost per call either
  account has ever recorded (₹19.60). Still worth restarting.

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across 1–28 Sep.

**September (1–30).** ₹69.07 a call, 15% above the August average, tracking
August's second half (₹72.36). 23–30 Sep ran cheaper (₹65.99) than 1–22
(₹70.24), helped by the two closing days (₹55.18 and ₹67.65) on the restructured
per-number campaigns.

The gap is one account: Pallavi Halcyon ₹58.81 a call, Pallavi Kiran ₹76.94 on
nearly twice the spend. `ad set level 3 camp` remains the standout at **₹45.77**
across 1,102 calls; the archived `4 Numbers` campaign did 469 calls at ₹67.68,
cheaper than `Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two dearest
lines, `New Leads Campaign` (₹95.69) and its copy (₹94.47), both stopped by the
23rd, and from the 28th the account stopped altogether.

**October (1–31).** ₹69.45 — flat against September, still 16% above August.
Two findings carry the month: the ABO consolidation at ₹37.11, and the
8585072072 → 094906 31010 repurpose that took one line from ₹40.99 to ₹103.09.
Pallavi Halcyon ₹66.45; Pallavi Kiran ₹124.91 on five days.

**November (1–10).** ₹87.42 — the dearest cost per call in any month on this
page, on only 60 calls from the three "Daily 500" per-number campaigns, all of
which stopped on the 4th. The budget went to WhatsApp instead: ₹4,160.90 for 56
conversations at ₹74.30. On price a conversation looks cheaper than a call, but
Meta counts one when the first message is sent and there is **no duration check**
equivalent to the 20s/60s test that keeps the call numbers honest — treat ₹74.30
as a starting cost, not as proof WhatsApp works better, until the clinic says how
many of those chats reached a person.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → ₹564.60 → **₹572.08** (September, final) → **₹740.49** (October)
→ ₹874.20 (November, on six calls only), against August's ₹507.57. Part of
October's jump is the consolidation campaign's own mix: it has the cheapest
placed call on the account but only 5.3% of its calls reach a minute, so it
flatters the headline and drags the duration figures — judge it on 20-second
calls, where it still wins at ₹172. The Kiran
lines hold callers best (4 Numbers ₹460, New Leads ₹480, 3 Numbers ₹484 per
60s call); Pallavi Halcyon's cheap calls are short (`ad set level 3 camp` ₹664,
`7788- call ads-new` ₹1,825). The earlier claim that 22 Sep was "the best day of
the month on duration" was removed — it rested on a five-day comparison.

**The per-number campaigns, three days in (28–30 Sep):** 8585072072 cheapest at
₹46.62 across 117 calls, then 9490631010 ₹55.13, 7272897897 ₹65.69, and
7788091092 dearest at ₹104.71 across 51. The 28 Sep snapshot that read ₹65.41
blended across one day only; with three days each the ranking is stable and
7788091092 is confirmed as the weak line. All four were replaced in October by
the single ABO consolidation campaign.


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

## Four result types — do not merge them

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

**From 28 August (Pallavi Halcyon only)** a fifth landing-page campaign,
`Halcyon | Enquiry LP | Contact-good lead | Mon–Sat 9–5` and its `Daily 1000`
sibling, optimise a **custom conversion** (`offsite_conversion.custom.1564834054962652`).
That is a fourth distinct lead event; in October these two are the only
website-lead campaigns spending, so their counts are comparable with each other
but still not with a call.

**WhatsApp campaigns** (from 4 November, Pallavi Halcyon only) report `results`
with indicator `actions:onsite_conversion.messaging_conversation_started_7d` —
Meta counts one when a person sends the first message. It is **not a phone
call**: there is no duration equivalent of the 20s/60s check, so a cheap
conversation is not evidence of a cheap conversation *with a person*. It gets its
own `DAILY_*` fields, chart band, day-table columns and `campMsg` table.

The page names the event on every row and keeps all non-call spend **out of cost
per call**. Blending the website-lead budget in reads ₹70.38 for August and
overstates what a call costs — don't. Blending November's WhatsApp spend in would
read ₹156.77 instead of ₹87.42 for that month, and folding in the
website-lead spend as well would read ₹176.58.

## Refreshing

`DAILY_AUG` / `DAILY_SEP` / `DAILY_OCT` / `DAILY_NOV` rows are
`[day, a1CallSpend, a1Calls, a1WebSpend, a1WebLeads, a2CallSpend, a2Calls, impressions, reachSum, linkClicks, a1MsgSpend, a1MsgConversations]`
where `a1` = Pallavi Halcyon, `a2` = Pallavi Kiran. `day` is the day of month.

**The last two fields are optional** and are omitted on any row with no WhatsApp
spend and no conversations, which is every row before 4 November. Every reader
uses `(r[10]||0)` / `(r[11]||0)`, so the older arrays stay valid untouched — do
not go back and pad them with zeros.

**Month totals in `MONTHS` are the sums of that month's own day rows**, not
Meta's period totals, so the headline and the day-table footer agree. They can
differ from Meta's period figure by a few paise (September by ₹0.07, October by
₹0.03) because Meta rounds each day independently; that is Meta's rounding, not
a dropped campaign, and the per-day reconciliation below is what proves it.

Everything else a tab shows — headline totals, narrative copy, campaign tables,
age rows — lives in the `MONTHS` object keyed `aug` / `sep` / `oct` / `nov`.
**To add a month, add a `DAILY_*` array and a `MONTHS` entry, then add one
`<button class="tab">` with a matching `data-month`.** Nothing else is
month-specific — unless the month brings a *new result type*, which is what
November did. Adding WhatsApp needed two optional `DAILY_*` fields, a fourth
chart band (`--s4`), two day-table columns, a legend item and the optional
`campMsg` table. If a fifth result type turns up, follow that pattern rather
than folding it into the website-lead column.

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
  `time_increment`), restricted to the **call campaigns** via `object_ids` —
  an account-level age pull would fold in website-lead and WhatsApp spend.
  Assert each campaign's age rows sum to its month total. An `Unknown` band is
  omitted from the table: ₹1.93 + 1 call in August, ₹3.55 + 1 call in September,
  ₹0.74 in October, nothing in November.
- The archived `4 Numbers` campaign has no per-band result either, so its age
  calls are derived the same way as its daily calls — band spend divided by
  `cost_per_action_type:click_to_call_native_call_placed`. All six bands divide
  to whole numbers and sum to its 469 calls.
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
- `campWeb` rows are `[name, daysLive, spend, eventName, count]`; `campMsg` has
  the same shape and is optional. A month with no `campMsg` hides the WhatsApp
  section entirely (`#msg-section` is `hidden`), so August, September and October
  look exactly as they did.
- **A renamed campaign can hide a creative swap.** Before carrying a campaign's
  history forward under a new name, pull `ads_account_get_activity_logs` with
  `event_category: "campaign"` and look for `Campaign name updated` next to
  `Ad updated` (old/new creative ids) or `Ad set targeting updated` in the same
  minute. If the creative or the targeting changed too, **split the campaign into
  two rows at the swap date** and keep each month's rows under the name that
  actually ran in it. This happened on 6 Oct 2026 and is documented under
  **Snapshot**.
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
