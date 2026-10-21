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
complete) and October 2026 (1–20). October stops at the 20th because **both
accounts have stopped spending** — Pallavi Halcyon last billed on 16 October,
Pallavi Kiran on 9 October — so the 21st is an empty live day with nothing in it.
The general rule still holds: never let the live part-day set a headline, because
Meta keeps revising the most recent ~48h and the part-day moves between calls
minutes apart. The range under each tab name is read off that month's own
`DAILY_*` rows at load, so it cannot drift from them.

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

Frozen **21 Oct 2026, 8:20 am IST**. August and September are both complete;
October covers **1–20** and the account group is currently dark.

| | August (1–31) | September (1–30) | October (1–20) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,24,016.93 |
| Calls placed | 5,144 | 4,539 | 1,477 |
| Cost per call | ₹59.99 | ₹69.07 | **₹60.73** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 360 (24.4%) · ₹249.17 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 131 (8.9%) · ₹684.75 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹77,961.48 / 1,383 / ₹56.37 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 |
| Website-lead spend | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹34,314.37 / 189 |
| De-dup reach (A1 / A2) | 11,39,310 / 6,12,279 | 8,00,412 / 8,37,451 | 6,42,176 / 90,931 |
| Frequency (A1 / A2) | 2.68 / 3.25 | 2.44 / 3.09 | 2.25 / 1.46 |

Account rows are **call spend only**; website-lead spend sits outside them and
outside every per-call figure. (August's Pallavi Halcyon row is total spend with a
call-only cost per call — that inconsistency is in the August figures as published
and has been left alone.) All figures are **ex-GST** (Meta bills 18% on top in
India); this page does not show a GST-inclusive total.

### ⚠️ A campaign was renamed, and Meta moved its whole history

**`Halcyon | Call 8585072072 | TS only | All days` no longer exists.** On
**6 Oct 2026 at 10:14 am** (activity log, `event_category: "campaign"`, Power
Editor, actor Abhijeet Lenka) campaign `120255796887700348` was renamed to
**`Halcyon | Call 094906 31010 | TS only | All days`**, and Meta now reports its
entire September history — including the ₹1,168.72 and 27 calls published as
8585072072 — under the new name.

It is a **pure rename**, not a restructure: the campaign never re-entered
Pending Review afterwards, and its id, budget and spend series are continuous.
So the row is renamed **in place** on the September tab rather than split or
re-labelled, and September's totals are unchanged by it.

Two things to watch:
- There are now **two campaigns pointing at 9490631010** — the original
  `Call 9490631010 | TS+AP` and this renamed one — which looks like a slip rather
  than a plan. Worth asking the clinic which number `094906 31010` is really meant
  to ring.
- **Always diff the campaign-name list against the previous cut.** A campaign that
  silently disappears while a new name appears carrying its spend is a rename, and
  carrying the history forward under the new name without checking the log is how
  a creative swap got misattributed in `elixir-reports`. The tell is the same:
  pull `ads_account_get_activity_logs` with `event_category: "campaign"` and look
  for `Campaign name updated`.

### The archived-campaign trap bit again, exactly as documented

On this refresh an unfiltered September listing of Pallavi Kiran returned three
campaigns totalling ₹1,65,842.89 against an account total of ₹1,97,583.42 —
**₹31,740.53 short**, the same gap and the same campaign
(`Halcyon | Calls — 4 Numbers | ABO | 22 Sep`, ARCHIVED) as last month. Re-pulling
with `filtering: effective_status IN ["ARCHIVED","DELETED"]` recovered it exactly,
and its 469 calls still derive to whole numbers on every day and every age band.
**This check is not optional and never will be.**

### Structural history

- **28 Sep** — Pallavi Kiran went to zero and has not spent since. Pallavi Halcyon
  paused its old call campaigns and opened four per-number call campaigns plus the
  Enquiry LP website-lead campaign (a **custom conversion**,
  `offsite_conversion.custom.1564834054962652`, a fourth distinct lead event).
- **6 Oct** — the 8585072072 campaign renamed (above).
- **9 Oct, 3:33–3:56 pm** — `Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each`
  created and set Active; the four per-number campaigns all set Inactive in the
  same minute. **This is the best change made to the account in three months**:
  519 calls at **₹36.86** over the following eight days, against ₹68.09 for the
  four separate campaigns it replaced.
- **16 Oct** — Pallavi Halcyon's last billed day (₹849.07). Dark since.

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across all of September
   and all of October.

**September (1–30, final).** ₹69.07 a call, 15% above the August average,
tracking August's second half (₹72.36). The gap is one account: Pallavi Halcyon
₹58.81, Pallavi Kiran ₹76.94 on the larger budget. `ad set level 3 camp` remains
the standout at **₹45.77** across 1,102 calls; the archived `4 Numbers` campaign
did 469 calls at ₹67.68, cheaper than `Kiran | Calls — 3 Numbers | ABO` (₹72.90).
Kiran's two dearest lines, `New Leads Campaign` (₹95.69) and its copy (₹94.47),
both stopped by the 23rd. The last three days are the new shape: Kiran dark, and
Pallavi Halcyon's four per-number campaigns delivering **347 calls at ₹62.04** —
better than either account's month average, with a wide spread inside it (₹46.62
on 094906 31010 against ₹104.71 on 7788091092).

**October (1–20).** **₹60.73 a call, the cheapest month on record** and below
August's ₹59.99 on the Halcyon account alone (₹56.37). The cause is the 9 Oct
consolidation, above. Pallavi Kiran is the opposite: ₹11,741 across five days at
**₹124.91** a call, its worst rate, almost all in the new
`Calls | ABO | Hyderabad | Ara + Top Performers` campaign (₹126.34).

**But October's cheap calls are shorter calls.** 24.4% passed 20 seconds against
September's 29.3%, and 8.9% passed a minute against 12.1% — the weakest duration
mix of the three months. Cost per 20-second call *rose* to ₹249.17 and per
minute-long call to ₹684.75 even as cost per call placed fell. Both are true;
the funnel is the honest view. The consolidated ABO campaign drives both halves
(519 calls at ₹36.86, but only 111 past 20s and 28 past 60s), while Kiran's
Hyderabad campaign is the inverse — dear per call but 39% past 20 seconds, the
best share on the page.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → ₹565 → **₹572.08** across eight cuts of September, against
August's ₹507.57 — and October is dearer again at ₹684.75. The Kiran
lines hold callers best (4 Numbers ₹460, New Leads ₹480, 3 Numbers ₹484 per
60s call); Pallavi Halcyon's cheap calls are short (`ad set level 3 camp` ₹664,
`7788- call ads-new` ₹1,825). The earlier claim that 22 Sep was "the best day of
the month on duration" was removed — it rested on a five-day comparison.

**The per-number campaigns ran 28 Sep – 9 Oct and are now switched off**, replaced
by the single consolidated ABO campaign. Over September's three days they did 347
calls at ₹62.04; over 1–9 October, 864 calls at ₹68.09. The consolidated campaign
then did 519 calls at ₹36.86. On that evidence, **one campaign across the three
numbers beats one campaign per number**, and it is worth saying so plainly to the
clinic before anyone splits them again.


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
  2.68) and 6,12,279 (Pallavi Kiran, frequency 3.25); September 1–30 is 8,00,412
  (2.44) and 8,37,451 (3.09); October 1–20 is 6,42,176 (2.25) and 90,931 (1.46).
  Those come from a call *without* `time_increment` (or with
  `time_increment: "monthly"`, which gives both months in one call per account)
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
- `MONTHS[x].range` is **not read by the page** (the tab sub-label is computed
  from the day rows). Keep it accurate anyway — it is the only in-file record of
  what a tab is supposed to cover.
- `MONTHS[x].days` **is** read, for the "per day" averages under the KPI tiles.
  Set it to the number of days the tab covers (30 for September, 20 for October),
  not to the length of the month.
- The first tab stays selected on load, so adding a month does **not** make it the
  default view. That was true when September was added and is still true for
  October; change it deliberately if at all.
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
