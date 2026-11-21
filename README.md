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

**Scope: four tabs.** August, September and October 2026 complete (1–31, 1–30,
1–31) and November 2026 at 1–20. November stops at the last complete day — Meta
keeps revising the most recent ~48h, and the live part-day moves between calls
minutes apart. Showing it would read as a collapse in spend that is not real.
The range under each tab name is read off that month's own `DAILY_*` rows at
load, so it cannot drift from them.

**Blank days are kept as zero rows, not dropped.** October has eight days with
no spend (17–20, 25–28) and November fifteen (6–20). Leaving them out would make
a stop look like a shorter month; the chart and the day table both want them.

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

Frozen **21 Nov 2026, 8:25 am IST**, data window **1–20 November**. September and
October are now closed months; two new tabs joined the page.

> **A campaign was renamed underneath the report.** The September row published
> last cut as `Halcyon | Call 8585072072 | TS only | All days` now reads
> `Halcyon | Call 094906 31010 | TS only | All days` — **same campaign id**
> (`120255796887700348`). `ads_account_get_activity_logs` on that object shows it
> renamed on 8 Oct 2026 at 12:21 pm, together with its ad set (`8585 | Hyderabad
> 30km | 25–65 | Calls` → `9490 | Kukatpally-Chandanagar-Moosapet | 25–65 |
> Calls`) and retargeted from Hyderabad +30km onto three small radii. The
> campaign was repointed from the 8585 number to 9490. It is **renamed in place**
> in the September tab, so that month's history stays attached to the campaign
> that produced it. See *A campaign can be renamed underneath you* below.
>
> **September grew by three days, and one published figure went backwards.** The
> four per-number call campaigns ran 28–30 Sep, not just the 28th, so September
> closes at 4,539 calls on ₹3,13,497.97 of call spend — ₹69.07, not the ₹69.65
> published for 1–28. The four lagging `HContacted` conversions shown last cut
> against the dormant `LP 8585` campaign have been **revised away to zero**, which
> is why September's website-lead count now reads 63 (52 + 11) rather than 26 plus
> a stray row. Expect zero-spend rows carrying only attributed conversions to move.
>
> **A fourth result type appeared in November.** `Halcyon | ABO | WhatsApp |
> 6 numbers | 700 each | Telangana regions` spent ₹4,160.90 on 4–5 Nov and started
> **56 WhatsApp conversations** (`actions:onsite_conversion.messaging_conversation_started_7d`).
> Its spend sits in the off-phone column; its 56 conversations are **not** in
> `webLeads` and touch no per-call figure.
>
> **Both accounts have been dark since 5 November.** Pallavi Kiran spent nothing
> at all in November and only five days in October.

| | August (1–31) | September (1–30) | October (1–31) | November (1–20) |
|---|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,68,508.95 | ₹10,594.70 |
| Calls placed | 5,144 | 4,539 | 1,834 | 60 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.45** | **₹87.42** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 442 (24.1%) · ₹288.15 | 17 (28.3%) · ₹308.54 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 172 (9.4%) · ₹740.49 | 6 (10.0%) · ₹874.20 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,15,623.01 / 1,740 / ₹66.45 | ₹5,245.18 / 60 / ₹87.42 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 | ₹0 / 0 / — |
| Off-phone spend | ₹53,443.78 / 332 | ₹13,712.53 / 63 | ₹41,144.86 / 226 | ₹5,349.52 / 13 + 56 WA |

(The September, October and November account rows are **call spend only**; the
off-phone spend in the last row sits outside them. August's Pallavi Halcyon row
is total spend, its cost per call call-only — that inconsistency is in the August
figures as published.)

Previous cuts: 1–22 Sep (published 28 Sep) ₹2,34,692.62 · 3,284 calls · ₹70.21;
1–28 Sep (published 29 Sep) ₹3,04,514.33 · 4,256 calls · ₹69.65.

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
   margin, on ~₹1,000/day. Worth restarting — **still ₹0.00 in September,
   October and November.**

**September, closed (1–30).** ₹69.07 a call, 15% above the August average and in
line with August's second half (₹72.36) rather than its first nine days (₹44.82).

The gap is one account: Pallavi Halcyon ₹58.81 a call, Pallavi Kiran ₹76.94 on
₹1,97,583 against ₹1,15,915. `ad set level 3 camp` remains the standout at
**₹45.77** across 1,102 calls; the archived `4 Numbers` campaign did 469 calls at
₹67.68, cheaper than `Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two
dearest lines, `New Leads Campaign` (₹95.69) and its copy (₹94.47), both stopped
by the 23rd.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → ₹565 → **₹572.08** for September across eight cuts, then **₹740.49**
in October and **₹874.20** in November. This is the one figure on the page with a
steady direction in every single refresh. The Kiran lines hold callers best
(4 Numbers ₹460, New Leads ₹480, 3 Numbers ₹484 per 60s call); Pallavi Halcyon's
cheap calls are short (`ad set level 3 camp` ₹664, `7788- call ads-new` ₹1,825).
The earlier claim that 22 Sep was "the best day of the month on duration" was
removed — it rested on a five-day comparison.

**The per-number campaigns beat the thing they replaced — by three days.** Over
1–27 Sep the two accounts paid ₹69.72 a call; over 28–30, with Pallavi Kiran off
and the four per-number campaigns alone on Pallavi Halcyon, ₹61.34 across 351
calls. Inside those three days `Call 094906 31010` did 117 calls at ₹46.62 and
`Call 7788091092` only 51 at ₹104.71 — the same spread the one-day reading
showed, so 7788091092 is still the number to watch.

**October: the price held, the volume did not.** ₹69.45 a call against
September's ₹69.07 — half a percent — but calls fell 60%, 4,539 → 1,834. That is
budget, not performance: **₹41,145 (24% of the month) went to website-lead
campaigns**, and Pallavi Kiran ran only five days (₹11,741 / 94 calls /
₹124.91 — the dearest account-month on the page).

October also holds **the cheapest call campaign since early August**:
`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each` ran 9–24 Oct for **525
calls at ₹37.11** on ₹19,483 — 29% of the month's calls on 15% of its call
budget, and the best 20s cost on the page since August (₹172.41). Only 5.3% of
its calls reached a minute, so the ₹37.11 flatters it, but this is the structure
to restart. It has not run since the 24th. The four per-number *All days*
campaigns ran ₹59.68 (9490631010) to ₹96.81 (7272897897).

**November: four days, then nothing.** ₹87.42 a call on ₹5,245 and 60 calls —
the dearest reading on the page, but a four-day sample, so a reading rather than
a trend. The three Daily 500 campaigns stopped after the 4th; the WhatsApp
campaign ran the 4th–5th; **nothing on either account since 5 November.** The
clinic question is whether that stop was deliberate.


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
| `Halcyon \| Enquiry LP \| Contact-good lead \| Mon–Sat 9–5` | `offsite_conversion.custom.1564834054962652` |
| `Halcyon \| Enquiry LP \| Contact-good lead \| Daily 1000` | `offsite_conversion.custom.1564834054962652` |
| `Halcyon \| ABO \| WhatsApp \| 6 numbers \| 700 each \| Telangana regions` | `onsite_conversion.messaging_conversation_started_7d` |

The page names the event on every row and keeps this spend **out of cost per
call**. Blending it in reads ₹70.38 and overstates what a call costs — don't.

**WhatsApp is a fifth thing, not a website lead.** November's WhatsApp campaign
returns *conversations started*. Its spend goes in the off-phone column so the
per-day reconciliation against the account total stays exact, but its 56
conversations are deliberately **excluded from `webLeads`** and from every
per-lead and per-call division. That is why `nov` sets `webFootEach:"&mdash;"` —
dividing the mixed off-phone column by site leads alone would invent a number.
October's two campaigns share one event, so `oct` sets
`webFootEvent:"Contact-good lead"` instead of the default "mixed".

### The off-phone column is labelled per month

Six places used to hard-code the words *Website leads*: the section eyebrow, the
day-table `Web spend` / `Site leads` column heads, the chart tooltip's two rows,
the campaign-table footer, the chart legend, and the day-table intro sentence.
They now read from the active month, so November can say *site + WhatsApp*
without a code change:

    webEyebrow, webLabel, webSpendLabel, webFoot, legendWeb,
    webSpCol, webCtCol, dayNote        (+ optional webFootEvent, webFootEach)

Every month must carry the first eight. `aug`, `sep` and `oct` carry the
original wording.

## A campaign can be renamed underneath you

On 8 Oct 2026 `120255796887700348` was renamed from `Halcyon | Call 8585072072 |
TS only | All days` to `Halcyon | Call 094906 31010 | TS only | All days`, and its
ad set was retargeted at the same time. Nothing in an insights pull flags this:
the id is stable and the name just comes back different.

- **Match campaigns by id, never by name.** A renamed campaign fetched by name
  looks like a new campaign and the old row looks like it stopped.
- **Rename in place in every past month's `campCalls`.** Adding a second row for
  the new name would split one campaign's history in two and break the
  `campCalls` spend/calls totals against `callSpend`/`calls`.
- **Confirm a suspected rename before editing.** `ads_account_get_activity_logs`
  scoped to the object id gives the date, the actor and the old/new `extra_data`;
  a rename that also changes targeting (as this one did) means the campaign is
  now buying something different, which is worth saying in the tab's note.

## Refreshing

`DAILY_AUG` / `DAILY_SEP` / `DAILY_OCT` / `DAILY_NOV` rows are
`[day, a1CallSpend, a1Calls, a1WebSpend, a1WebLeads, a2CallSpend, a2Calls, impressions, reachSum, linkClicks]`
where `a1` = Pallavi Halcyon, `a2` = Pallavi Kiran. `day` is the day of month.

Everything else a tab shows — headline totals, narrative copy, campaign tables,
age rows — lives in the `MONTHS` object keyed `aug` / `sep` / `oct` / `nov`.
**To add a month,
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
  The de-duplicated per-account figures on the Reach tile come from a separate
  pull — one call per account with `time_increment: "monthly"` over the whole
  span gives every month at once, which is cheaper than one call per month:

  | | Pallavi Halcyon | Pallavi Kiran |
  |---|---|---|
  | August | 11,39,310 (2.68) | 6,12,279 (3.25) |
  | September | 8,00,412 (2.44) | 8,37,451 (3.09) |
  | October | 8,55,599 (2.34) | 90,931 (1.46) |
  | November 1–20 | 82,250 (1.40) | 0 (—) |

  (September's 1–28 cut read 7,00,847 / 2.37 for Pallavi Halcyon.)
- The `reachSum` column is **each account's own daily reach, added together** —
  two numbers, not a sum over campaigns. September days 1–10 were originally
  built from campaign-level reach, which double-counts within an account and ran
  5–9k a day high; they were rebuilt from the account pull on 18 Sep so the
  column means one thing down its whole length.
- Recent days keep settling for ~48h; re-pull the whole month rather than
  appending. **Re-pull closed months too** — September's last three days, its
  per-number campaign names and its website-lead count all changed after it was
  published.
- **Account-level daily pulls do not carry `cost_per_action_type` unless you ask
  for it by name**, and the field is huge. Getting per-day calls from
  `account_spend / cpa` needs that field requested explicitly; the per-campaign
  daily pull you need for reconciliation anyway gives calls directly in
  `results`, so prefer it and keep `cost_per_action_type` for the duration
  derivations and for the archived `4 Numbers` campaign.
- `campCalls` rows are
  `[name, account(1|2), daysLive, spend, callsPlaced, calls20s, calls60s]`. The
  account flag drives the colour dot — keep it correct when adding rows, and keep
  each month's `calls20` / `calls60` totals equal to the sum of its rows.
- `campWeb` rows are `[name, daysLive, spend, event, count]`, and the month's
  `webSpend` must equal the sum of their spend — including a WhatsApp row — while
  `webLeads` must equal the sum of only the site-lead rows.
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
