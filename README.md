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
complete) and October 2026 (1–14). October stops at the last complete day — Meta
keeps revising the most recent ~48h, and the live part-day moves between calls
minutes apart. Showing it would read as a collapse in spend that is not real. The
range under each tab name is read off that month's own `DAILY_*` rows at load, so it
cannot drift from them.

**The page still opens on the August tab** (`let M=MONTHS.aug`, and `tab-aug` carries
`aria-selected="true"`). That was tolerable with two tabs and is getting less so with
three — worth deciding whether the newest month should be the default.

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

Frozen **15 Oct 2026, 8:05 am IST**. **September is now complete (1–30) and October is
open as a third tab (1–14).** 15 October is a live part-day and is excluded.

| | August (1–31) | September (1–30) | October (1–14) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,17,155.42 |
| Calls placed | 5,144 | 4,539 | 1,376 |
| Cost per call | **₹59.99** | **₹69.07** | **₹62.74** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 335 (24.3%) · ₹257.72 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 125 (9.1%) · ₹690.69 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹74,595.23 / 1,282 / ₹58.19 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 |
| Website-lead spend | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹30,819.11 / 139 |

(September and October account rows are **call spend only**; the website-lead spend is
the last row and sits outside every per-call figure. August's Pallavi Halcyon row is
total spend with a call-only cost per call — that inconsistency is in the August
figures as published.)

Previous cut (1–28 Sep, published 29 Sep): ₹3,04,514.33 · 4,256 calls · ₹69.65.

All figures are **ex-GST** (Meta bills 18% GST on top in India). Unlike
`o2-reports`, this page does not show a GST-inclusive billed total — if the
client asks for one, add it, don't silently change the per-call numbers.

### What moved

**September closed cheaper than it was running.** The last three days (28–30) were
Pallavi Halcyon alone — Pallavi Kiran spent nothing from the 28th and stayed dark —
and the four new per-number call campaigns bought **347 calls at ₹62.04** against the
month's ₹69.07. **29 September was the cheapest day of the month**, ₹55.18 a call on
167 calls. The month average fell ₹69.65 → ₹69.07. Meta revised 28 Sep up by ₹21.14
after publication (+91 impressions); no call counts moved.

**October has a step change on the 9th.** Until then the four per-number campaigns ran
and the daily rate drifted the wrong way — ₹55.20 on the 1st to **₹132.45 on the 8th**,
the dearest day in the whole report. At 3:56 pm on the 9th all four were paused and
replaced by one consolidated campaign, **`Halcyon | ABO | Calls | 7788 + 7272 + 9490 |
600 each`**, and the rate fell to ₹35.21, ₹39.82, ₹47.40, ₹47.78 and **₹29.43 on the
14th** — the cheapest day on this page since early August. Split: ₹71.85 over 1–9,
**₹38.69 over 10–14**.

**The consolidated campaign is the best cost per call since 8 August.** 418 calls at
**₹37.72** in six days, and the cheapest 20-second call on either account (₹183.33).
**But only 5.3% of its calls reach a minute**, so a minute-long call from it costs
₹716.64. That is the trade to watch before more budget moves into it.

**Calls got cheaper and shorter at the same time.** 20s share 29.3% → 24.3%, 60s share
12.1% → 9.1%. So the minute-long call keeps getting dearer: **₹507.57 (Aug) → ₹572.08
(Sep) → ₹690.69 (Oct)**, now 36% above where it started. It has risen at every cut of
this report.

**`7788091092` is the worst line two months running.** ₹104.71 a call in September and
**₹105.03 in October** on near-identical budget to its siblings — 144 calls against
094906 31010's 286. Of the four it replaced, only `094906 31010` (₹49.55 in October,
₹46.62 in September) was close to the consolidated campaign.

**Pallavi Kiran is the expensive half again and barely ran.** ₹11,741.08 across five
days (5–9 Oct) for 94 calls — **₹124.91 each, twice Pallavi Halcyon's ₹58.19** — on a
new campaign `Calls | ABO | Hyderabad | Ara + Top Performers` (₹126.34) plus one day of
its old 3 Numbers line (₹114.05). Nothing since the 9th. On this evidence it is not
worth restarting at that price without a change to the setup.

**`Enquiry LP` is now the single largest line on either account** — ₹30,819.11 in the
fortnight, **26% of October's budget**, for 139 custom-conversion leads at ₹221.72. It
is a different event bought at a different price and stays out of every cost-per-call
figure. It ran on twelve of fourteen days; the 4th and 11th are Sundays (outside its
Mon–Sat schedule) and **the 8th is a third blank the schedule does not explain** —
worth a look.

### A campaign was renamed — and this time it really was just a rename

`Halcyon | Call 8585072072 | TS only | All days` disappeared from the campaign listing
and `Halcyon | Call 094906 31010 | TS only | All days` appeared carrying its whole
history. Same campaign id, `120255796887700348`. The activity log
(`event_category: "campaign"`) records **one** event —

    Campaign name updated   6 Oct 2026, 10:14 AM, Power Editor, Abhijeet Lenka
    old "Halcyon | Call 8585072072 | TS only | All days"
    new "Halcyon | Call 094906 31010 | TS only | All days"

— and nothing else until it was paused on the 9th. So the rows carry straight through
under the new name. **Check the log every time a campaign name moves**, the way
`elixir-reports` does for ads: a name change that comes with a creative or targeting
change is a different campaign wearing the old numbers.

Note the new name collides with `Halcyon | Call 9490631010 | TS+AP | All days` — there
are now two campaigns named for 9490631010 and none for 8585072072. The page prints
Meta's current names, so if that is a slip at Meta it should be fixed there, not here.

### Pre-existing: August's impressions and clicks tiles disagree with its own day table

`MONTHS.aug.impressions` is 2,338,227 and `clicks` 6,921, but `DAILY_AUG` sums to
**5,047,184 impressions and 27,226 clicks**. September and October both use the
DAILY-sum convention and reconcile exactly. This was already true before this refresh
and is left alone — fixing it needs a fresh August pull to decide which number the
tile is supposed to carry.

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Still ₹0.00 in September and October. The consolidated
   October campaign is the first thing since to get near it (₹37.72).

**September (1–30).** ₹69.07 a call, 15% above the August average, tracking
August's second half (₹72.36). The daily series is noisy — ₹82.77 (6th) at one end,
₹55.18 (29th) at the other — but the shape of the month is clear enough: 1–27 ran at
₹69.72 on the old setup, and the four per-number campaigns that replaced it on the 28th
bought **347 calls at ₹62.04** over the last three days. (The 28–30 day window reads
₹61.34 across 351 calls — four of those calls were attributed late to two paused
campaigns that spent nothing, which is why the campaign-level and day-level rates differ
slightly.)

The gap is one account: Pallavi Halcyon ₹58.81 a call, Pallavi Kiran ₹76.94 on 70%
more spend. `ad set level 3 camp` remains the standout of the old setup at **₹45.77**
across 1,102 calls; the archived `4 Numbers` campaign did 469 calls at ₹67.68, cheaper
than `Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two dearest lines,
`New Leads Campaign` (₹95.69) and its copy (₹94.47), both stopped by the 23rd, and the
account went dark from the 28th.

**October (1–14).** ₹62.74 a call — better than September, still above August. The
fortnight is really two regimes either side of 9 October, when the four per-number
campaigns were paused and one consolidated campaign took the whole call budget:
**₹71.85 over 1–9, ₹38.69 over 10–14**. `Halcyon | ABO | Calls | 7788 + 7272 + 9490 |
600 each` has 418 calls at **₹37.72** and is the only call campaign still active.
Pallavi Kiran ran five days at ₹124.91 a call and stopped.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → ₹565 → **₹572.08** across the September cuts, and October opens at
**₹690.69**, against August's ₹507.57. In September the Kiran lines held callers best
(4 Numbers ₹460, New Leads ₹480, 3 Numbers ₹484 per 60s call) while Pallavi Halcyon's
cheap calls were short (`ad set level 3 camp` ₹664, `7788- call ads-new` ₹1,825).
October makes that trade explicit: the cheapest placed call on the account is also one
of the dearest minute-long calls (₹716.64).

**The per-number campaigns got three September days and nine October ones**, and the
ranking held the whole way: `094906 31010` (renamed from 8585072072 on 6 Oct) cheapest
at ₹46.62 then ₹49.55, `7788091092` dearest at ₹104.71 then ₹105.03. The warning on
7788091092 after its single 28 Sep day was right.

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
  (2.44) and 8,37,451 (3.09); October 1–14 is 6,18,804 (2.20) and 90,931 (1.46) — those
  come from a call *without* `time_increment` and are quoted in the footer only.
- The `reachSum` column is **each account's own daily reach, added together** —
  two numbers, not a sum over campaigns. September days 1–10 were originally
  built from campaign-level reach, which double-counts within an account and ran
  5–9k a day high; they were rebuilt from the account pull on 18 Sep so the
  column means one thing down its whole length.
- Recent days keep settling for ~48h; re-pull the whole month rather than
  appending.
- **Meta's period and daily aggregates can disagree by a few paise.** On the October
  pull, `level: "ad_account"` without `time_increment` read ₹1,05,414.55 for Pallavi
  Halcyon while the daily rows summed to ₹1,05,414.34, and the `age` breakdown agreed
  with the period figure. Campaign-day rows matched account-day rows **exactly** on
  every day, which is the check that matters; take the headline from the day rows (the
  page's own totals come from them) and let the ₹0.21 sit in the age table, where the
  October `ageIntro` says so out loud. Do not chase it as a missing campaign.
- **A day can carry calls with no spend behind it.** 28 Sep has 4 calls attributed to
  two campaigns that spent ₹0 that day, and 10 Oct has 1. They belong in the day row
  (they are real calls) but they make a day-window cost per call differ slightly from
  the same window summed per campaign. Say which one a quoted rate is.
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
- Update the snapshot date in the masthead prose and in this README (two places:
  the masthead `<p class="prose">` line and the `/* ---- Baked figures ... */` comment
  at the top of the script block).
