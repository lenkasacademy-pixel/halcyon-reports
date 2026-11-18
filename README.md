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
(1–31) are all complete and settled. November 2026 covers 1–17; the live part-day
is excluded, because Meta keeps revising the most recent ~48h and the part-day
moves between calls minutes apart. Showing it would read as a collapse in spend
that is not real. The range under each tab name is read off that month's own
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

Frozen **18 Nov 2026, 11:00 am IST**, data window **1 Aug – 17 Nov 2026** across
four month tabs.

> ### Both accounts have been dark since 6 November
>
> Pallavi Halcyon spent Rs 10,594.70 across 1–5 November and then **nothing at
> all — zero spend and zero impressions every day from the 6th to the 17th**.
> Pallavi Kiran has spent nothing in November, and nothing since 9 October.
>
> This is a stop, not a performance result, and the page says so rather than
> showing it as a collapse. **Someone should confirm the 6 November stop was
> intended** — a budget, billing or spend-limit change looks exactly like this.

| | August (1–31) | September (1–30) | October (1–31) | November (1–17) |
|---|---|---|---|---|
| Spent (total) | Rs 3,62,046.60 | Rs 3,27,210.50 | Rs 1,68,508.95 | Rs 10,594.70 |
| Call spend | Rs 3,08,602.82 | Rs 3,13,497.97 | Rs 1,27,364.09 | Rs 5,245.18 |
| Calls placed | 5,144 | 4,539 | 1,834 | 60 |
| Cost per call | **Rs 59.99** | **Rs 69.07** | **Rs 69.45** | **Rs 87.42** |
| Lasted 20s+ | 1,448 (28.1%) · Rs 213.12 | 1,328 (29.3%) · Rs 236.07 | 442 (24.1%) · Rs 288.15 | 17 (28.3%) · Rs 308.54 |
| Lasted 60s+ | 608 (11.8%) · Rs 507.57 | 548 (12.1%) · Rs 572.08 | 172 (9.4%) · Rs 740.49 | 6 (10.0%) · Rs 874.20 |
| Pallavi Halcyon | Rs 2,18,901.90 / 3,063 / Rs 54.02 | Rs 1,15,914.55 / 1,971 / Rs 58.81 | Rs 1,15,623.01 / 1,740 / Rs 66.45 | Rs 5,245.18 / 60 / Rs 87.42 |
| Pallavi Kiran | Rs 1,43,144.70 / 2,081 / Rs 68.79 | Rs 1,97,583.42 / 2,568 / Rs 76.94 | Rs 11,741.08 / 94 / Rs 124.91 | Rs 0.00 / 0 / — |
| Non-call spend | Rs 53,443.78 | Rs 13,712.53 | Rs 41,144.86 | Rs 5,349.52 |

Account rows from September onward are **call spend only**; non-call spend sits
outside them. August's Pallavi Halcyon row is total spend with a call-only cost
per call — that inconsistency is in the August figures as published.

All figures are **ex-GST** (Meta bills 18% GST on top in India).

## The findings

**September closed at Rs 69.07 a call.** The 1–28 cut read Rs 69.65; adding the
29th (Rs 11,858.31) and 30th (Rs 10,816.72), both on Pallavi Halcyon alone, pulled
it down slightly. **The two accounts swapped roles on 28 September**: Pallavi Kiran
spent nothing after the 27th and closed at Rs 76.94 a call, while Pallavi Halcyon
picked the month up with four new per-number call campaigns and closed at Rs 58.81
— the cheaper account on roughly half the budget. `ad set level 3 camp` remains the
standout at **Rs 45.77** across 1,102 calls.

**October's headline barely moved — Rs 69.45 against Rs 69.07 — but the
composition changed completely.**

1. **`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each` is the find of the
   quarter.** It ran 9–24 October on about Rs 1,200/day and delivered **525 calls
   at Rs 37.11 each** — more calls than any other campaign on either account that
   month, at less than half the cost of the three per-number campaigns running
   alongside it (Rs 94.80, Rs 96.81, Rs 68.95). It is the cheapest call campaign
   since `Halcyon | Calls — Age 35+ | FB only | CBO` did Rs 19.60 in early August.
   **Worth restarting before anything else on this account.** Caveat: only 21% of
   its calls held twenty seconds, so on connected calls it reads Rs 172.41 — still
   the best on the month, but a smaller lead than the headline suggests.
2. **Pallavi Kiran is effectively finished.** Rs 11,741.08 across five days
   (5–9 Oct) for 94 calls at Rs 124.91, against Rs 1,97,583.42 in September. Its
   one new line, `Calls | ABO | Hyderabad | Ara + Top Performers`, did 83 calls at
   Rs 126.34 and stopped.
3. **Non-call spend grew to Rs 41,144.86 — 24% of October** — almost all of it the
   Enquiry LP custom-conversion campaign, which bought 226 site enquiries. Same
   pattern that pushed the blended figure up in August: not wasted, but a different
   thing at a different price.

**The minute-long call keeps getting dearer:** Rs 507.57 (Aug) → Rs 572.08 (Sep) →
Rs 740.49 (Oct) → Rs 874.20 (Nov, 6 calls). The 20-second call followed the same
path: Rs 213.12 → Rs 236.07 → Rs 288.15 → Rs 308.54.

**`Halcyon | Calls — Age 35+ | FB only | CBO` is still at Rs 0.00** across all of
September, October and November. It returned 410 calls at Rs 19.60 in early August
and has never been restarted.

### November: a third result type appeared

A **new WhatsApp campaign** (`Halcyon | ABO | WhatsApp | 6 numbers | 700 each |
Telangana regions`, OUTCOME_ENGAGEMENT) took Rs 4,160.90 on 4–5 November for
**56 WhatsApp conversations at Rs 74.30 each**. That is a *third* kind of result on
this client, alongside phone calls and website enquiries.

**How it is handled, and the judgment call in it.** `DAILY_*` has only two spend
columns per account (call and non-call), so the WhatsApp spend sits in the
**non-call** bucket — which keeps it rigorously out of every per-call figure and
keeps the day rows reconciling to the account totals to the paisa. Its event is
named on its own row in the campaign table, exactly as the four pixel events
already are. **The consequence to be aware of:** November's aggregate `webLeads`
of 69 is 56 WhatsApp conversations + 13 custom-conversion leads, which is not one
comparable number. November's `webTitle` and `webIntro` say so in as many words.
If this becomes a standing part of the account rather than a two-day test, the
right fix is a third pair of `DAILY_*` columns, not a bigger non-call bucket.

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
  **Request `cost_per_action_type` on the age call too**: the archived
  `4 Numbers` campaign returns no call count per band either, so its per-band
  calls have to be derived band by band, exactly as its total is. Without that,
  September's age table comes out 469 calls short and the shortfall is easy to
  mistake for an age-reporting gap.
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
- **Ad accounts go dark without any campaign status changing.** On the 18 Nov pull
  both accounts read ACTIVE campaigns while spending Rs 0.00 for twelve straight
  days. Always pull `level: "ad_account"` with `time_increment: "1"` across the
  whole window first: a run of zero-spend, zero-impression days is the signal, and
  no campaign-level listing shows it as clearly.
- **A new result type can appear with no warning.** November brought an
  OUTCOME_ENGAGEMENT WhatsApp campaign onto Pallavi Halcyon. Check every spending
  campaign's `results.indicator` on each refresh and classify it before summing
  anything: call / website-event / messaging are three different products. The
  indicators seen so far are `actions:click_to_call_native_call_placed`,
  `conversions:offsite_conversion.fb_pixel_custom.HContacted`,
  `actions:offsite_conversion.custom.1564834054962652`, `actions:lead` (the
  mislabelled archived call campaign) and
  `actions:onsite_conversion.messaging_conversation_started_7d`.
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
