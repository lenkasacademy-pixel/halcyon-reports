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
calls the network. **The page opens on the newest tab** (`let M=MONTHS.oct`), so a
client landing on it sees current data rather than August.

**Scope: three tabs.** August 2026 (1–31, complete), September 2026 (1–30,
complete) and October 2026 (1–27). October stops at the last complete day — Meta
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

Frozen **28 Oct 2026, 8:15 am IST**. **September is now closed (1–30)** and a new
**October tab covers 1–27**; 28 October is a part-day that had taken nothing at
snapshot time and is excluded.

> ### ⚠ A per-number campaign was renamed to a different phone number
>
> **This is the one thing on this refresh that needs a human.** Campaign
> `120255796887700348` was created on 28 Sep as
> `Halcyon | Call 8585072072 | TS only | All days`. On **6 Oct at 10:14 am**
> (activity log, Power Editor, actor Abhijeet Lenka) it was renamed to
> `Halcyon | Call 094906 31010 | TS only | All days` — a *different clinic
> number*. The rename alone triggered no review cycle, so by the `elixir-reports`
> test it is a genuine rename and not a creative swap.
>
> **But the campaign did not actually switch number.** Its ads tell a different
> story: six of its seven ads are named `8585 | ...` and kept spending right
> through 24 Oct, and a single `9490 | Proven | "1" video` ad was *added* on
> 9 Oct (₹4,623.97, 23 calls). So from 9 October this campaign runs **mostly
> 8585 creative under a name that says 9490631010**, while a separate campaign,
> `Halcyon | Call 9490631010 | TS+AP | All days`, also targets 9490631010.
>
> What this report does about it:
> - **September keeps the September name.** The `sep` tab still lists the line as
>   `Halcyon | Call 8585072072 | TS only | All days`, because that is what it was
>   and what it ran. Every September figure for it is unchanged in substance.
> - **October carries Meta's current name**, because that is what the client will
>   see in Ads Manager — but the October per-number table is **not a clean
>   per-number split** for this line.
>
> **Do not read October's `094906 31010` row as the performance of 9490631010.**
> Decide with the client whether the campaign should be renamed back, split, or
> have its 8585 ads moved out, then fix the row. Everything still reconciles to
> the paisa; the numbers are real, the label is wrong.

| | August (1–31) | September (1–30) | October (1–27) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,62,154.48 |
| Calls placed | 5,144 | 4,539 | 1,779 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.48** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 429 (24.1%) · ₹288.12 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 167 (9.4%) · ₹740.15 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,11,863.43 / 1,685 / ₹66.39 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 |
| Website-lead spend | ₹53,443.78 / 332 | ₹13,712.53 / 63 | ₹38,549.97 / 211 |

(September and October account rows are **call spend only**; the website-lead
spend sits outside them, as it does in every per-call figure. August's Pallavi
Halcyon row is total spend with a call-only cost per call — that inconsistency is
in the August figures as published.)

**September closed at ₹69.07**, down from ₹69.65 at the 28th: the four new
per-number campaigns ran cheaply on the 29th and 30th (283 calls on ₹17,063,
₹60.29 each). Pallavi Kiran spent nothing after the 27th. Meta revised 28 Sep up
by ₹21.14 after publication (per-number campaigns +₹18.45, Enquiry LP +₹2.69),
with no call count moved.

### October's finding: consolidation halved the cost of a call

On 9 October one campaign, **`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600
each`**, started running three numbers together. It bought **525 calls at
₹37.11** — the cheapest line on either account in any month this report covers,
better even than August's ₹44.82 phase. Over the same month the four separate
per-number campaigns bought 1,160 calls at **₹79.64**.

It was switched off on the 16th. When the per-number campaigns came back on the
22nd without it, cost per call went **₹60.77 (1–16 Oct) → ₹112.63 (21–24 Oct)**,
the dearest stretch in the report.

| October call campaign | spend | calls | each |
|---|---|---|---|
| ABO — 7788 + 7272 + 9490 (9–16, 24) | ₹19,482.72 | 525 | **₹37.11** |
| Call 9490631010 TS+AP (1–9) | ₹14,502.32 | 243 | ₹59.68 |
| Call 094906 31010 TS only (1–9, 22–24) | ₹25,578.75 | 371 | ₹68.95 |
| Call 7788091092 TS only (1–9, 22–24) | ₹26,258.49 | 277 | ₹94.80 |
| Call 7272897897 TS+AP (1–9, 22–24) | ₹26,041.15 | 269 | ₹96.81 |
| Kiran · Ara + Top Performers (6–9) | ₹10,486.48 | 83 | ₹126.34 |
| Kiran · 3 Numbers ABO (5) | ₹1,254.60 | 11 | ₹114.05 |

**Putting the numbers back into one ABO campaign is the clearest action this data
supports** — but read it next to the duration numbers below before moving the
whole budget.

**The calls got shorter.** 24.1% past 20 seconds against 29.3% in September, 9.4%
past a minute against 12.1%. Cost per call barely moved, so the whole change lands
in the duration prices: the 20-second call ₹236.07 → **₹288.12**, the minute-long
call ₹572.08 → **₹740.15**. Both are the worst in the report, and the minute-long
call has now risen at every single cut: ₹497 → 503 → 512 → 526 → 543 → 546 →
565 → 572 → **740**. The consolidated ABO campaign is part of this: ₹172.41 for a
20-second call is the best on the page, but only 28 of its 525 calls (5.3%) ran
past a minute.

**October did not run continuously.** Pallavi Halcyon delivered 1–16, dark
17–20, back 21–24, dark since the 25th. Pallavi Kiran spent on five days only
(5–9 Oct). The flat stretches in the chart are the account serving nothing, not
missing data.

**Pallavi Kiran has all but stopped** — ₹11,741 over five days against
₹1,97,583 in September, at ₹124.91 a call. Its only real line is
`Calls | ABO | Hyderabad | Ara + Top Performers`, a **traffic-objective**
campaign that nonetheless reports `actions:click_to_call_native_call_placed`, so
it is counted as a call campaign: ₹10,486 for 83 calls, ₹126.34 each.

**Website leads are now 26% of Pallavi Halcyon's spend.** `Halcyon | Enquiry LP |
Contact-good lead` is the only website-lead campaign still running: ₹38,549.97
for 211 custom-conversion leads, ₹182.70 each. That is a *fourth* distinct lead
event (`offsite_conversion.custom.1564834054962652`) and is not comparable with
the HContacted / HEnquiry / fb_pixel_lead counts in earlier months. None of it is
in any cost-per-call figure — blending it in would read ₹91.15 a call for October
instead of the true ₹69.48.

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

**September (1–30, closed).** ₹69.07 a call, 15% above the August average,
tracking August's second half (₹72.36). The last two days were the month's most
expensive in absolute terms (₹11,858 and ₹10,817) but among its cheaper ones per
call, which is what pulled the month from ₹69.65 at the 28th to ₹69.07.

The gap is one account: Pallavi Halcyon ₹58.55 a call, Pallavi Kiran ₹76.94 on
twice the spend. `ad set level 3 camp` remains the standout at **₹45.77** across
1,102 calls; the archived `4 Numbers` campaign did 469 calls at ₹67.68, cheaper
than `Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two dearest lines,
`New Leads Campaign` (₹95.69) and its copy (₹94.47), both stopped by the 23rd.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → **₹564.60** across seven cuts, against August's ₹507.57. The Kiran
lines hold callers best (4 Numbers ₹460, New Leads ₹480, 3 Numbers ₹484 per
60s call); Pallavi Halcyon's cheap calls are short (`ad set level 3 camp` ₹664,
`7788- call ads-new` ₹1,825). The earlier claim that 22 Sep was "the best day of
the month on duration" was removed — it rested on a five-day comparison.

**The four per-number campaigns across their three September days** (28–30)
read ₹62.04 a call on ₹21,528.69 and 347 calls — from ₹46.62 (8585072072,
117 calls) to ₹104.71 (7788091092, 51 calls). In October, with a full month
behind them, that ordering holds: 7788091092 is still the dearest per-number line
at ₹94.80. **See the rename warning above before reading the 8585072072 line
forward into October.**


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
- **Diff the campaign names against the previous cut, every refresh.** A campaign
  renamed at Meta carries its whole history forward under the new name and every
  total still reconciles, so reconciliation will not catch it. On the 28 Oct pull
  `Halcyon | Call 8585072072 | TS only | All days` had become
  `Halcyon | Call 094906 31010 | TS only | All days` on the same id. Pull
  `ads_account_get_activity_logs` with `event_category: "campaign"` to date the
  rename, then **check the ad names inside the campaign** — that is what showed
  the campaign was still running 8585 creative under a 9490 name. Keep a closed
  month's row under the name it had in that month.
- A campaign with a **traffic objective can still be a call campaign**:
  `Calls | ABO | Hyderabad | Ara + Top Performers` is `OUTCOME_TRAFFIC` but
  reports `actions:click_to_call_native_call_placed`. Decide by the `results`
  indicator, never by `objective`.
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
  `DAILY_AUG`, and in this README — three places.
- When you add a month, also move `let M=MONTHS.<newest>` and the
  `aria-selected`/`tabindex` defaults on the tab buttons and `aria-labelledby` on
  `#report`, so the page still opens on the newest tab.
