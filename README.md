# Halcyon Pain Management — Meta Ads calls report

Client-facing report for **Halcyon Pain Management**, covering **both** ad accounts:

| Account | ID | What it runs |
|---|---|---|
| Pallavi Halcyon | `1999324147481098` | Call ads + website-lead campaigns |
| Pallavi Kiran | `694358492762548` | Call ads only |

Live: https://lenkasacademy-pixel.github.io/halcyon-reports/

A single self-contained `index.html` with a **month tab bar** (August /
September / October). Figures are baked into the `DAILY_AUG` / `DAILY_SEP` /
`DAILY_OCT` arrays and the `MONTHS` object near the bottom of the file —
nothing calls the network.

**Scope: three tabs.** August 2026 (1–31, complete), September 2026 (1–30,
complete) and October 2026 (1–15). The current month stops at the last complete
day — Meta keeps revising the most recent ~48h, and the live part-day moves
between calls minutes apart. Showing it would read as a collapse in spend that
is not real. The range under each tab name is read off that month's own
`DAILY_*` rows at load, so it cannot drift from them.

**The default tab is still August.** Adding October did not change that. If the
client would rather land on the newest month, flip `let M=MONTHS.aug` and the
`aria-selected`/`tabindex` attributes on the three buttons — it is a one-line
change, deliberately left alone here.

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

Frozen **16 Oct 2026, 8:05 am IST**. September is now complete (1–30) and
October has its own tab (1–15). 16 October is a live part-day — ₹64.72 at the
time of the pull — and is excluded.

| | August (1–31) | September (1–30) | October (1–15) |
|---|---|---|---|
| Spent (calls + web) | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,23,160.35 |
| Call spend | ₹3,08,602.82 | ₹3,13,497.97 | ₹89,354.56 |
| Calls placed | 5,144 | 4,539 | 1,457 |
| Cost per call | ₹59.99 | **₹69.07** | **₹61.33** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 358 (24.6%) · ₹249.59 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 131 (9.0%) · **₹682.10** |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹77,613.48 / 1,363 / ₹56.94 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 |
| Website-lead spend | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹33,805.79 / 181 |

(Both September and October account rows are **call spend only**; website-lead
spend sits outside them and outside every cost-per-call figure. August's Pallavi
Halcyon row is total spend, its cost per call call-only — that inconsistency is
in the August figures as published.)

Previous cut (1–28 Sep, published 29 Sep): ₹3,04,514.33 · 4,256 calls · ₹69.65.

All figures are **ex-GST** (Meta bills 18% GST on top in India). Unlike
`o2-reports`, this page does not show a GST-inclusive billed total — if the
client asks for one, add it, don't silently change the per-call numbers.

### What moved at this refresh

- **September closed at ₹69.07, not ₹69.65.** Nothing in the 1–28 window moved
  except **₹18.45 of ordinary settling on the 28th** (the four per-number
  campaigns, calls unchanged). The 1–28 call count is still exactly 4,256. The
  month got cheaper only because the 29th and 30th were cheaper than the
  average.
- **The 29th and 30th were big days on Pallavi Halcyon** — ₹11,858.31 and
  ₹10,816.72, roughly triple its rate for the rest of September — split between
  the four new per-number call campaigns (₹21,528 / 347 calls / ₹62.04 over
  28–30) and the new Enquiry LP website campaign (₹9,589 / 52 leads).
- **Pallavi Kiran ended September dark** (zero on the 28th, 29th and 30th) and
  its September total is unchanged from the previous refresh at ₹1,97,583.42 /
  2,568 calls.
- **October is the cheapest half-month since early August: ₹61.33 a call.** The
  consolidation on 9 Oct is why — see the findings below.

### A campaign was renamed underneath this report

The per-number campaign published last refresh as **`Halcyon | Call 8585072072
| TS only | All days`** now reports as **`Halcyon | Call 094906 31010 | TS only
| All days`**. It is the **same campaign object** — id `120255796887700348` —
not a new campaign and not a lost one:

- the campaign id is unchanged;
- 28 September still shows **27 calls** on it, exactly as published;
- its 28 Sep spend moved only ₹1,168.72 → ₹1,172.70, which is the same ordinary
  settling the other three per-number campaigns saw that day;
- campaign sums still equal the account's own daily spend and impressions on
  every day of both months.

So its history is carried forward **in place** under the new name. Note the
account now has two campaigns naming 9490631010 — `Call 9490631010 | TS+AP`
and this renamed `Call 094906 31010 | TS only` — so match on **id**, never on
the phone number in the name.

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Still ₹0.00 across September and October — it has
   now been idle for ten weeks and is still the cheapest line this report has
   ever recorded.

**September (1–30).** ₹69.07 a call, 15% above the August average, still
tracking August's second half (₹72.36). Almost the same money as August bought
605 fewer calls. The gap is one account: Pallavi Halcyon ₹58.81, Pallavi Kiran
₹76.94 on 70% more spend. `ad set level 3 camp` remains the month's standout at
**₹45.77** across 1,102 calls; the archived `4 Numbers` campaign did 469 calls
at ₹67.68, cheaper than `Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two
dearest lines, `New Leads Campaign` (₹95.69) and its copy (₹94.47), both
stopped by the 23rd, and the account went dark after the 27th.

**October (1–15): ₹61.33 a call, 11% below September and within ₹1.35 of the
August average.** Two causes, both on Pallavi Halcyon:

1. **The 9 October consolidation worked.** The four per-number campaigns gave
   way to one campaign, `Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each`
   (`120255979446760348`), and it is the cheapest line since August's Age 35+:
   **₹37.64 a call across 499 calls** in seven days, against ₹64.52 for the
   four per-number campaigns it replaced over 1–9 October.
2. **Pallavi Kiran has barely run.** Nothing 1–4 Oct, five days at
   ₹1,255–₹3,120, dark again since the 10th. Its 94 calls cost ₹124.91 each —
   the dearest line on either account. The account that carried September's
   expensive half is simply not spending.

**Two cautions on October.**

- **The cheap calls are shorter.** 24.6% past twenty seconds against
  September's 29.3%, and 9.0% past a minute against 12.1%. The consolidated ABO
  campaign is the clearest case: cheapest calls on the account at ₹37.64, but
  only 5.6% reach a minute. `Call 7788091092` inverts it — ₹105.03 a call but
  13.2% hold a minute. If the clinic values conversations over rings, the
  per-number structure was doing something the consolidated one is not. Worth
  settling before the old structure is written off.
- **Website-lead spend is now a quarter of the budget.** ₹33,805.79 on
  `Halcyon | Enquiry LP | Contact-good lead | Mon–Sat 9–5` against ₹89,354.56
  on calls, for 181 custom-conversion leads at ₹186.77 each. It is a different
  event bought at a different price and is outside every call figure — but it
  means the call numbers now describe a shrinking share of what the clinic
  spends.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → ₹565 → ₹572 across eight September cuts, and **₹682.10** in
October, against August's ₹507.57. It is the one figure on this page that has
never reversed direction.

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

`DAILY_OCT` has the same row shape. `MONTHS.oct` carries October's copy.

Pull with Meta MCP `ads_get_ad_entities`, `level: "campaign"`,
`time_increment: "1"`, one call per account per month.

- **Filter on `effective_status`, never on `amount_spent`.** Narrowing the
  listing with `{"field":"amount_spent","operator":"GREATER_THAN","value":["0"]}`
  looks like the obvious way to find the campaigns that spent, and it silently
  **re-excludes ARCHIVED campaigns** — it dropped the ₹31,740.53 `4 Numbers`
  campaign again on this refresh, reproducing the exact gap the note above
  describes. Always use the `effective_status IN [...]` filter with `ARCHIVED`
  and `DELETED` in the list, then pick the spenders yourself from the result.
- **Keep zero-spend days that still carry calls.** A campaign-day with
  `amount_spent: 0` and no impressions can still report attributed calls, and
  dropping those rows loses real calls: six such rows exist across September
  and October (3 on 20 Sep, 1 on 25 Sep, 2 on 27 Sep, 4 on 28 Sep for Pallavi
  Halcyon, 1 on 10 Oct). Filtering them out made the September day rows sum to
  1,961 calls against Meta's own period total of 1,971 — a 10-call shortfall
  that looks exactly like an attribution quirk and is really a dropped row.
  Keep any row with spend **or** impressions **or** results.
- **Cross-check day sums against period totals per campaign.** With the
  zero-spend rows kept, every campaign's day-sum equals Meta's own
  no-`time_increment` total on calls exactly. If it does not, suspect a dropped
  row before suspecting Meta.

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
  September: all 13 call campaigns reconcile exactly. October: one campaign,
  `Halcyon | ABO | Calls`, has age rows summing **₹0.24 above** its campaign
  total (calls match exactly) — Meta's own breakdown rounding, carried as-is.
  ₹1.93 and 1 call land in an `Unknown` band and are omitted from the age table.
- `reachSum` is the sum of each day's reach and double-counts people across days.
  Meta's de-duplicated August reach was 11,39,310 (Pallavi Halcyon, frequency
  2.68) and 6,12,279 (Pallavi Kiran, frequency 3.25); September 1–30 is 8,00,412
  (2.44) and 8,37,451 (3.09); October 1–15 is 6,38,370 (2.24) and 90,931 (1.46)
  — those come from a call *without* `time_increment` and are quoted in the
  footer only.
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
