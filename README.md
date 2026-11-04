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
(1–31), all complete, plus November 2026 (1–3). November stops at the last
complete day — Meta keeps revising the most recent ~48h, and the live part-day
moves between calls minutes apart. **Verified again on this refresh:** 4 November
read ₹33.47 at the start of the pull and ₹36.31 a few minutes later, and the 3rd's
campaign rows were ₹0.99 short of the account total on the first read and exact on
the second. Showing a part-day would read as a collapse in spend that is not real.
The range under each tab name is read off that month's own `DAILY_*` rows at load,
so it cannot drift from them.

**The page still opens on August.** With two tabs that was harmless; with four it
means the live page lands three months back. Changing it is one line
(`let M=MONTHS.aug;` near the top of the script, plus the `aria-labelledby` on
`#report`) and is deliberately **not** done here — it changes what the client sees
first, which is their call.

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

Frozen **4 Nov 2026, 8:11 am IST**. Four tabs: **August 1–31**, **September 1–30**,
**October 1–31** and **November 1–3**.

| | Aug (1–31) | Sep (1–30) | Oct (1–31) | Nov (1–3) |
|---|---|---|---|---|
| Spent (total) | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,68,508.95 | ₹5,886.51 |
| …of which call ads | ₹3,08,602.82 | ₹3,13,497.97 | ₹1,27,364.09 | ₹4,697.89 |
| …of which website leads | ₹53,443.78 | ₹13,712.53 | ₹41,144.86 | ₹1,188.62 |
| Calls placed | 5,144 | 4,539 | 1,834 | 55 |
| **Cost per call** | **₹59.99** | **₹69.07** | **₹69.45** | **₹85.42** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 442 (24.1%) · ₹288.15 | 15 (27.3%) · ₹313.19 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 172 (9.4%) · ₹740.49 | 5 (9.1%) · ₹939.58 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,15,623.01 / 1,740 / ₹66.45 | ₹4,697.89 / 55 / ₹85.42 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 | ₹0 / 0 / — |
| De-dup reach (H / K) | 11,39,310 / 6,12,279 | 8,00,412 / 8,37,451 | 8,55,599 / 90,931 | 47,879 / 0 |
| Frequency (H / K) | 2.68 / 3.25 | 2.44 / 3.09 | 2.34 / 1.46 | 1.42 / — |

Every account row from September onward is **call spend only**; website-lead spend
sits outside them. August's Pallavi Halcyon row is total spend with a call-only cost
per call — that inconsistency is in the August figures as published and is left alone.

All figures are **ex-GST** (Meta bills 18% GST on top in India). Unlike
`o2-reports`, this page does not show a GST-inclusive billed total — if the
client asks for one, add it, don't silently change the per-call numbers.

### September closed at ₹69.07, not the ₹69.65 we published

The 29 September cut stopped at the 28th because the 29th was then a live part-day.
Settled, the 29th and 30th add **₹22,675 of spend and 283 calls**, and they came in
*below* the month's average, so cost per call fell ₹69.65 → **₹69.07**. Meta also
revised 28 September up by ₹21.14 (impressions +293, reach +119, clicks +4); no call
counts moved.

The four per-number campaigns that opened on the 28th now have **three days** instead
of one, which changes the read on them completely:

| campaign (28–30 Sep) | spend | calls | each | 1 day in |
|---|---|---|---|---|
| Call 094906 31010 \| TS only | ₹5,455.00 | 117 | **₹46.62** | ₹43.29 |
| Call 9490631010 \| TS+AP | ₹5,347.17 | 97 | ₹55.13 | ₹53.60 |
| Call 7272897897 \| TS+AP | ₹5,386.31 | 82 | ₹65.69 | ₹76.84 |
| Call 7788091092 \| TS only | ₹5,340.21 | 51 | ₹104.71 | ₹377.06 |

7788091092 is still the laggard but nothing like the ₹377 it read on one day — that
is why the one-day warning was worth printing.

> ### ⚠ A campaign was renamed at Meta — the same trap as `elixir-reports`
>
> The campaign published on 29 September as **`Halcyon | Call 8585072072 | TS only |
> All days`** now reports as **`Halcyon | Call 094906 31010 | TS only | All days`**.
>
> It is the **same campaign object**, not a new one: same id
> (`120255796887700348`), and its 28 September figures are continuous —
> ₹1,168.72 / 27 calls as published, ₹1,172.70 / 27 calls now, a ₹3.98 settling
> revision with the call count unchanged. So its history is carried forward under
> the new name.
>
> **I could not confirm the rename in the activity log.** An `event_category:
> "campaign"` pull over 28 Sep – 4 Nov returns no `Campaign name updated` event, but
> the 40-entry page only reaches back to 8 October, so a rename in late September or
> early October would not appear. Worth a human glance: if the *ads inside it* were
> also swapped (the `elixir-reports` failure mode), the campaign row is now labelled
> with a phone number it did not dial for. The spend and call continuity says the
> campaign is the same; it does not prove the creative is.
>
> Note there are now **two 9490631010 campaigns** with different targeting
> (`094906 31010 | TS only` and `9490631010 | TS+AP`) and **no 8585072072 campaign
> at all**. That looks like a naming correction rather than a new line, but the
> client should confirm which number each is actually dialling.

### October: a complete month, two four-day blackouts, and the cheapest line in months

₹1,68,508.95 across 31 days, **₹69.45 a call** — all but identical to September's
₹69.07, on a much smaller account: 59 calls a day against 151.

**Eight days of October spent nothing at all**, on either account: 17–20 Oct and
25–28 Oct. Both are deliberate, from the activity log (actor Abhijeet Lenka):

| when | what |
|---|---|
| 9 Oct 3:33 pm | `ABO \| Calls \| 7788 + 7272 + 9490 \| 600 each` created |
| 9 Oct 3:56 pm | the four per-number "All days" campaigns paused, ABO activated |
| 21 Oct 2:42 pm | ABO paused → the 17–20 gap is the four per-number lines being off |
| 22 Oct 5:43 am | three per-number lines + Enquiry LP reactivated |
| 23 Oct 5:46 pm | all paused again → the 25–28 gap |
| 24 Oct 5:55 am | reactivated; ABO paused again at 8:08 am |
| 29 Oct 9:40–9:44 am | four new campaigns created (3 × Call ₹500/day + Enquiry LP ₹1,000/day), old set paused |
| 2 Nov 7:51 am | Enquiry LP Daily 1000 paused |
| 3 Nov 12:58 pm | `TEST \| WhatsApp number check \| delete me` created (₹0, never delivered) |

**The find of the month is the consolidated ABO campaign.** `Halcyon | ABO | Calls |
7788 + 7272 + 9490 | 600 each` took ₹19,482.72 over nine days and returned **525 calls
at ₹37.11** — the cheapest placed call on this account since August's Age 35+ campaign
(₹19.60), and unlike that one it did it at scale (58 calls a day). It also held
callers reasonably: 113 twenty-second calls at ₹172.41, 28 minute-long at ₹695.81.
**It was paused on 24 October and has not run since.** That is the one decision in
this report worth revisiting with the client.

**Pallavi Kiran came back for five days only** (5–9 Oct, ₹11,741.08) and was the
dearest delivery of the month at ₹124.91 a call. It has been dark since.

**Website-lead spend is now 24% of the budget** (₹41,144.86 of ₹1,68,508.95, against
4% in September) and both October campaigns optimise the *same* custom conversion, so
for the first time those two rows are comparable with each other — though still not
with the HContacted rows from August and early September.

### November: three days, three campaigns, and the dearest calls on record

₹5,886.51 and 55 calls at **₹85.42** — the highest in this report, 23% above October
and 42% above the August average. **Three days and 55 calls is not a trend**, and
the daily spread says so (23 calls, then 17, then 15, on near-identical spend).

Only the three per-number campaigns created on 29 October are running, each on
₹500/day. The ordering has reversed again: `094906 31010` ₹70.56, `7788091092`
₹77.09 (it was the dearest line in both September and October), `7272897897`
**₹123.36**. Same budget on each, so the spread is response, not spend.

**Half the account's structure from a month ago is switched off**: Pallavi Kiran dark
for nearly four weeks, and the ₹37.11 ABO campaign off since 24 October.

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Worth restarting — still **₹0.00 across September,
   October and November**. October's consolidated ABO campaign (₹37.11 a call over
   525 calls) is the nearest thing to it the account has produced since, and that is
   paused too.

**September (1–30, complete).** ₹69.07 a call, 15% above the August average,
tracking August's second half (₹72.36) rather than its cheap first nine days.

The gap is one account: Pallavi Halcyon ₹58.81 a call, Pallavi Kiran ₹76.94 on
nearly twice the spend. `ad set level 3 camp` remains the standout at **₹45.77**
across 1,102 calls; the archived `4 Numbers` campaign did 469 calls at ₹67.68,
cheaper than `Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two dearest lines,
`New Leads Campaign` (₹95.69) and its copy (₹94.47), both stopped by the 23rd.

**The cost-per-call series now reads ₹59.99 → ₹69.07 → ₹69.45 → ₹85.42** across
August, September, October and the first three days of November. The middle two are
flat; the last is three days of data on three campaigns.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → ₹565 → **₹572.08** for the full September, then **₹740.49** in October
and **₹939.58** over the first three November days, against August's ₹507.57. It has
risen at every single cut this report has recorded, and October is the biggest step. The Kiran
lines hold callers best (4 Numbers ₹460, New Leads ₹480, 3 Numbers ₹484 per
60s call); Pallavi Halcyon's cheap calls are short (`ad set level 3 camp` ₹664,
`7788- call ads-new` ₹1,825). The earlier claim that 22 Sep was "the best day of
the month on duration" was removed — it rested on a five-day comparison.

**The new per-number campaigns now have three days** (28–30 Sep): ₹21,528.69,
347 calls, ₹62.04 — from ₹46.62 (094906 31010, formerly 8585072072) to ₹104.71
(7788091092). On one day 7788091092 read ₹377.06; three days later it is ₹104.71.
That is the whole case for not publishing one-day campaign rates as findings.


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
  In September ₹3.55 and 1 call land in an `Unknown` band and are omitted from the
  age table; October and November have no `Unknown` spend at all.
- **`Halcyon | Calls — 4 Numbers | ABO | 22 Sep` needs its age calls derived too.**
  It reports `results` as "Not available" per band as well as per day, so each band's
  calls are `spend / cost_per_action_type:click_to_call_native_call_placed` — 138,
  136, 82, 61, 33, 19 for 18–24 through 65+, summing to the campaign's 469.
- **Some Pallavi Halcyon campaigns book no 18–24 delivery at all.** September and
  October both have an 18–24 row that is entirely Pallavi Kiran, and November has no
  18–24 row because all three live campaigns target 25 and over. An empty band is a
  targeting fact, not a missing pull.
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
