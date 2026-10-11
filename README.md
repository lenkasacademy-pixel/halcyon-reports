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
complete) and October 2026 (1–10, still running). The live month stops at the
last complete day — Meta keeps revising the most recent ~48h, and the part-day
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

Frozen **11 Oct 2026, 8:40 am IST**. **September is now closed** (1–30) and
**October is open** (1–10; the 11th is a live part-day — Pallavi Halcyon had taken
only ₹172.05 of it — and is excluded).

> **A campaign was renamed at Meta, and the rename hides nothing but will confuse
> you.** `Halcyon | Call 8585072072 | TS only | All days` became
> **`Halcyon | Call 094906 31010 | TS only | All days`** at 10:14 am on 6 Oct
> (`ads_account_get_activity_logs`, `event_category: "campaign"`, actor Abhijeet
> Lenka, Power Editor). It is the **same campaign id** `120255796887700348` with its
> whole history — the 28 Sep row the previous cut published under the old name
> (₹1,168.72, 27 calls) is the same row that now reads ₹1,172.70, 27 calls under the
> new one. There are still only **four** per-number campaigns, not five; 9490631010
> simply now appears twice in the naming (once TS+AP, once TS-only). **Check
> `Campaign name updated` in the activity log on every refresh** before concluding a
> campaign is new.

> **Pallavi Kiran went dark, then came back on a new campaign.** It spent nothing
> from 28 Sep to 4 Oct, ran 5–9 Oct, and has spent nothing on the 10th or 11th. Its
> October spend is one revived line (`Kiran | Calls — 3 Numbers | ABO`, the 5th only)
> plus `Calls | ABO | Hyderabad | Ara + Top Performers`, an **`OUTCOME_TRAFFIC`**
> campaign that nonetheless reports `click_to_call_native_call_placed` — so it counts
> as a call campaign here.

> **Structural change on 9 Oct.** At 3:33 pm a new campaign,
> `Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each`
> (`120255979446760348`), was created; at 3:56 pm it was activated and **all four
> per-number campaigns were switched off in the same minute**. Two days in it is at
> **₹32.85 a call** across 120 calls — less than half the account rate.

| | August (1–31) | September (1–30) | October (1–10) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹96,144.73 |
| Calls placed | 5,144 | 4,539 | 1,078 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.12** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 272 (25.2%) · ₹273.94 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 112 (10.4%) · ₹665.29 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹62,771.77 / 984 / ₹63.79 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 |
| Website-lead spend | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹21,631.88 / 103 |

(Both months' account rows are **call spend only**; website-lead spend sits outside
them. August's Pallavi Halcyon row is total spend, its cost per call call-only —
that inconsistency is in the August figures as published and has not been touched.)

Previous cuts: 1–22 Sep ₹2,34,692.62 · 3,284 calls · ₹70.21 (published 28 Sep);
1–28 Sep ₹3,04,514.33 · 4,256 calls · ₹69.65 (published 29 Sep).

All figures are **ex-GST** (Meta bills 18% GST on top in India). Unlike
`o2-reports`, this page does not show a GST-inclusive billed total — if the
client asks for one, add it, don't silently change the per-call numbers.

De-duplicated reach for each window (account pull *without* `time_increment`,
quoted in the footer only): September 8,00,412 (Pallavi Halcyon, frequency 2.44)
and 8,37,451 (Pallavi Kiran, 3.09); October 1–10 5,31,512 (2.12) and 90,931 (1.46).

### Residual rounding at this snapshot

Everything reconciles except two sub-rupee residuals, recorded so the next refresh
does not chase them:

- **10 October, Pallavi Halcyon:** campaign rows sum to ₹5,862.62 / 57,394
  impressions against the account's own ₹5,862.60 / 57,393. Every other day of
  October and all thirty days of September match to the rupee and the impression.
- **`MONTHS.oct.impressions` is 1,259,411**, the sum of the `DAILY_OCT` rows, against
  1,259,417 from the two account-level period pulls — the same 6 impressions. The
  daily sum is used deliberately, so the tile can never disagree with the chart
  under it (September follows the same convention and there the two agree exactly).

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across 1–28 Sep.

**September (1–30), complete.** ₹69.07 a call, 15% above the August average,
tracking August's second half (₹72.36). The last three days changed the shape of the
month: Pallavi Kiran went dark on the 28th and stayed dark, and Pallavi Halcyon's
budget moved into four per-number call campaigns that took ₹21,529 over 28–30 Sep for
**347 calls at ₹62.04** — better than the month and better than the lines they
replaced. The spread across the four is wide: **₹46.62** on 094906 31010 (117 calls)
against **₹104.71** on 7788091092 (51). Watch 7788091092.

For the month as a whole the gap is still one account: Pallavi Halcyon ₹58.81 a call,
Pallavi Kiran ₹76.94 on 1.7× the spend. `ad set level 3 camp` remains the standout at
**₹45.77** across 1,102 calls; the archived `4 Numbers` campaign did 469 calls at
₹67.68, cheaper than `Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two dearest
lines, `New Leads Campaign` (₹95.69) and its copy (₹94.47), both stopped by the 23rd.

**October (1–10), still running.** ₹69.12 a call — five paise above September. On the
headline nothing has changed; underneath it, two things have.

1. **The new `Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each` is buying calls
   at half the account rate**: ₹3,942.55 for **120 calls at ₹32.85** in two days, the
   cheapest call on either account since `Halcyon | Calls — Age 35+ | FB only | CBO`
   did ₹19.60 in early August. It also leads on duration (₹171 a 20-second call,
   ₹438 a minute). Two days is not a verdict — but this is the one line on the page
   worth watching, and it is the campaign that replaced the four per-number ones.
2. **The accounts have swapped places.** Pallavi Kiran is now the expensive one at
   **₹124.91** a call (September: ₹76.94) on only ₹11,741 over five days, almost all
   of it `Calls | ABO | Hyderabad` at ₹126.34. Pallavi Halcyon is at ₹63.79 — worse
   than its own September (₹58.81) but still the better half.

**Website-lead spend has reversed direction.** `Halcyon | Enquiry LP | Contact-good
lead` alone has taken **₹21,631.88 in ten days** — more than 2.5× its whole September
— for 103 of its custom `offsite_conversion.custom.1564834054962652` conversions,
₹210 each. That is **22% of everything the two accounts spent in October**, and it is
a fourth distinct lead event, so it stays out of every per-call figure.

**October has inverted September's age pattern.** 18–24 is now the *dearest* band at
₹100.43 a call (September: the cheapest, ₹55.56) and 65+ the cheapest at ₹49.71. The
18–24 figure rests on 22 calls from one campaign, so do not read much into it yet.

**The minute-long call keeps getting dearer:** ₹497 → ₹503 → ₹512 → ₹526 →
₹543 → ₹546 → ₹565 → **₹572.08** across eight cuts of September, against August's
₹507.57 — and October is running at **₹665.29**. It has risen at every single
refresh recorded here; it is the one figure on this page with a steady direction. The Kiran
lines hold callers best (4 Numbers ₹460, New Leads ₹480, 3 Numbers ₹484 per
60s call); Pallavi Halcyon's cheap calls are short (`ad set level 3 camp` ₹664,
`7788- call ads-new` ₹1,825). The earlier claim that 22 Sep was "the best day of
the month on duration" was removed — it rested on a five-day comparison.

**The four per-number campaigns ran 28 Sep – 9 Oct and are now off.** Over their
whole life they took ₹80,357.91 for 1,211 calls (**₹66.36 each**) — the 28 Sep reading of
₹65.41 across 68 calls was one day and was indeed too early to judge. 094906 31010
(formerly 8585072072) finished cheapest at ₹46.62 in September and ₹49.55 in October;
7788091092 stayed dearest at ₹104.71 and ₹105.03. All four were switched off at
3:56 pm on 9 Oct when the ABO campaign took over.


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

- **Check `Campaign name updated` in the activity log every refresh.** On the 11 Oct
  pull `Halcyon | Call 8585072072 | TS only | All days` had become
  `Halcyon | Call 094906 31010 | TS only | All days` on the same campaign id. A
  renamed campaign looks like a new campaign plus a vanished one, and carrying it
  forward under both names would double-count the month. Pull
  `ads_account_get_activity_logs` with `event_category: "campaign"` and read
  `extra_data.old_value` / `new_value`.
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
- **`MONTHS.impressions` and `MONTHS.clicks` are the sums of that month's own
  `DAILY_*` rows**, not the account period pull, so the tiles can never disagree with
  the chart under them. For September the two agree exactly; for October 1–10 they
  differ by 6 impressions (Meta's own rounding). August was built differently and its
  `MONTHS.impressions` does *not* equal its daily sum — that is as published; leave it.
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
