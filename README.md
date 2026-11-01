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

**Scope: three tabs.** August 2026 (1–31), September 2026 (1–30) and October 2026
(1–31) — all three complete months. Each month stops at the last complete day:
Meta keeps revising the most recent ~48h, and the live part-day moves between
calls minutes apart. Showing it would read as a collapse in spend that is not
real. The range under each tab name is read off that month's own `DAILY_*` rows
at load, so it cannot drift from them.

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

Frozen **1 Nov 2026, 11:00 am IST**. **August, September and October are all
complete closed months.** September, which had been held at the 28th, gained its
last two days; October is new.

| | August (1–31) | September (1–30) | October (1–31) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,68,503.10 |
| Calls placed | 5,144 | 4,539 | 1,834 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.44** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 442 (24.1%) · ₹288.14 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 172 (9.4%) · ₹740.46 |
| Website-lead spend | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹41,144.35 / 226 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,15,617.67 / 1,740 / ₹66.45 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 |

(September and October account rows are **call spend only**; website-lead spend
sits outside them. August's Pallavi Halcyon row is total spend, its cost per call
call-only — that inconsistency is in the August figures as published.)

### What September gained

The 29th and 30th settled and added **₹22,675.03 and 283 calls**. Meta also
**revised the 28th up by ₹21.14** after publication (call spend +₹18.45,
website-lead spend +₹2.69, impressions +293, reach +119, clicks +4). **Every
other day of September came back byte-identical** — days 1–27 are exactly as they
were published, which is the strongest evidence yet that this account stops moving
once it is ~48h past.

September's cost per call therefore improved slightly on the final cut, from
₹69.65 (1–28) to **₹69.07** (1–30), because the two closing days were cheaper
than the month's average.

### October

**Cost per call held; a quarter of the budget stopped buying calls.** ₹69.44
against September's ₹69.07 — three months now in a narrow band well above
August's ₹59.99. What changed is the mix: **website-lead campaigns took ₹41,144,
24% of the month**, against ₹13,713 in September. Total spend roughly halved and
calls per day fell from 151 to 59.

**The cheapest call line since early August.** `Halcyon | ABO | Calls | 7788 +
7272 + 9490 | 600 each` ran 9–17 October and bought **525 calls at ₹37.11** — 41%
of the month's calls on 15% of its spend, the best rate since
`Halcyon | Calls — Age 35+ | FB only | CBO` managed ₹19.60 in early August. Then
it stopped, and nothing in the data says why. The per-number campaigns that
replaced it cost ₹68.95–₹96.81 a call. **This is the one thing on the page worth
acting on** — and it is the same shape as the August finding, which is still
unactioned.

**Pallavi Kiran has all but stopped.** ₹11,741 across five days (5–9 October) and
nothing in the twenty-two days since, after being the *larger* account in
September. Its 94 calls cost **₹124.91** each — the worst rate in any month this
report covers. 83 of them came from a campaign new this month,
`Calls | ABO | Hyderabad | Ara + Top Performers`, at ₹126.34. Somebody should
confirm whether that account is deliberately off.

**Two real dark stretches:** nothing served on **18–20 October** or **26–28
October**. The page shows them as flat, which is correct — they are stops, not
gaps in the data.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 → ₹543 →
₹546 → ₹565 → ₹572 → **₹740.46**. It has risen at every single cut this report
has taken, and October is the largest jump of the series. The duration mix is the
weakest of the three months (24.1% past 20s, 9.4% past 60s).

### A campaign was renamed — check it was deliberate

The campaign published in September as **`Halcyon | Call 8585072072 | TS only |
All days`** (id `120255796887700348`) now reads **`Halcyon | Call 094906 31010 |
TS only | All days`** at Meta. Same campaign id, same history, and its figures
reconcile to the paisa on both months — so this is a rename, not a creative swap
of the kind the Elixir report hit. But **the clinic number in the name changed**,
and **no campaign on the account now carries 8585072072** at all. The page lists
it under its current name in both months rather than re-labelling September's
history as a different line.

If the ad actually now dials 094906 31010, that is a real routing change and the
September comparison is between two different destinations. Worth confirming.

### Reconciliation

Clean, with one documented drift.

- **September:** campaign rows equal each account's own daily spend *and*
  impressions on every one of the 30 days, both accounts, to the paisa.
- **October:** the same holds on every delivering day **except the 31st**, where
  campaign rows run **₹0.51 ahead** of Meta's account-level daily figure. The 31st
  was yesterday and is still inside Meta's revision window; both accounts'
  *period* totals reconcile exactly (₹1,56,762.02 and ₹11,741.08), so the gap is
  Meta's own daily-versus-period rounding, not a dropped campaign. It is written
  into October's `partNote` so the page reports it itself.
- Every 20s/60s derivation in both months lands on a whole number.
- Both months' `age` rows sum to that month's call spend and call count exactly
  (September leaves ₹3.55 and 1 call in an `Unknown` band, October ₹0.74 and 0).
- The archived `4 Numbers` campaign's **age-band calls are derived too** —
  `spend / cost_per_action_type:click_to_call_native_call_placed` per band — and
  the six bands sum to exactly its 469 calls.

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
  `time_increment`). Assert each campaign's age rows sum to its month total — on
  the 1 Nov pull all 14 September campaigns and all 10 October ones matched to the
  paisa. A small `Unknown` band is left over and omitted from the age table
  (September ₹3.55 and 1 call, October ₹0.74 and none).
- **Rebuild a month's `age` array from a full-month pull, do not patch it with a
  delta.** Adding only the new days' age rows leaves any revision to an already
  published day stranded outside the bands, and it shows up as `Unknown` drift
  that is really an error. The 1 Nov refresh re-pulled all of September.
- **An `amount_spent > 0` filter drops archived campaigns from an age pull**, the
  same way an unfiltered listing drops them. The archived `4 Numbers` campaign had
  to be fetched by `object_ids` on its own. Fetch archived campaigns explicitly.
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
