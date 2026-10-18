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

**Scope: three tabs.** August 2026 (1–31), September 2026 (1–30) — both now
complete — and October 2026 (1–17). Each month stops at the last complete day:
Meta keeps revising the most recent ~48h, and a live part-day moves between calls
minutes apart. Showing it would read as a collapse in spend that is not real. The
range under each tab name is read off that month's own `DAILY_*` rows at load, so
it cannot drift from them.

## What it shows

- Amount spent, phone calls placed, blended cost per call, reach.
- A three-panel day-wise chart on one shared calendar: daily spend stacked by
  account (with the website-lead spend split out), calls placed stacked by
  account, and cost per call against that period's average. One hover reads all three.
- A two-up comparison card carrying each tab's headline finding (August's
  1–9 vs 10–31 split; September against the August average; October's
  1–9 vs 10–17 split).
- A **call-quality funnel**: placed → 20s+ → 60s+, with each step's share of
  placed calls and its true cost.
- Per-campaign totals for the call campaigns and, separately, the website-lead
  campaigns.
- Calls and cost per call by age band, both accounts combined.
- The full day-by-day table for the selected month.

## Snapshot

Frozen **18 Oct 2026, 9:00 am IST**. **September is now complete (1–30) and an
October tab has been added (1–17).** Both accounts reconcile to the paisa against
their own `level: "ad_account"` daily totals on spend **and** impressions for every
one of the 47 days — no mismatch anywhere in this refresh.

> ### Delivery has stopped on both accounts
>
> The 16th took **₹849.07 across both accounts**, the 17th took **nothing at all**
> (no spend, no impressions, no reach), and 18 October is ₹0 so far too. For the
> first time this report has **no part-day to exclude**. Whether that is a paused
> account, an exhausted budget or a billing problem is not something the API says —
> **somebody needs to look at it in Ads Manager.** The page says so in the October
> part-note.
>
> ### A campaign was renamed under us
>
> The campaign published last refresh as `Halcyon | Call 8585072072 | TS only |
> All days` now reads **`Halcyon | Call 094906 31010 | TS only | All days`** on the
> same id `120255796887700348`. It is a pure rename, not a creative swap: the 28 Sep
> day row still carries 27 calls, and the spend only moved ₹1,168.72 → ₹1,172.70
> with Meta's settling. The consequences are real, though — **nothing on the
> account targets 8585072072 any more, and two campaigns now name 9490631010**
> (`Halcyon | Call 9490631010 | TS+AP` and this one). Worth confirming with the
> clinic that 8585072072 was meant to come off the ads.
>
> ### A campaign with zero spend can still carry leads
>
> `Halcyon | LP 8585 | Website Leads` spent ₹0 in September and still booked
> **4 HContacted conversions on 1 September** — a lagging pixel event from its
> August run. A campaign listing filtered on `amount_spent > 0` drops it, and the
> day-row total then disagrees with the month total by those 4 leads. **List
> campaigns without the spend filter and keep any row that carries a result**, then
> place its leads on the right day with a ranged daily pull. October has no such row.

| | August (1–31) | September (1–30) | October (1–17) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,24,016.93 |
| Calls placed | 5,144 | 4,539 | 1,477 |
| Cost per call | **₹59.99** | **₹69.07** | **₹60.73** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 360 (24.4%) · ₹249.17 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹564.60 → **₹572.08** | 131 (8.9%) · **₹684.75** |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹77,961.48 / 1,383 / ₹56.37 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / **₹124.91** |

(Both accounts' September and October rows are **call spend only**. Website-lead
spend sits outside them: ₹13,712.53 for 67 conversions in September, and
**₹34,314.37 for 189 in October** — more than a quarter of the month's money.
August's Pallavi Halcyon row is total spend, its cost per call call-only — that
inconsistency is in the August figures as published.)

**What moved in September since the 1–28 cut.** Three days of Pallavi Halcyon
delivery were added (28–30 Sep; Pallavi Kiran was dark from the 28th) and Meta
settled the 28th up by ₹21.14 — ₹18.45 across the four per-number campaigns,
₹2.69 on Enquiry LP — with no call or lead count moving. The month's cost per call
went ₹69.65 → **₹69.07**, because 28–30 Sep ran at ₹61.34 against ₹69.72 over
1–27. Enquiry LP, which had one day of data last time, closed September at
₹9,589.18 for 52 conversions (₹184.41 each).

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
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across all of September
   and all of October.

**September (1–30), final.** ₹69.07 a call, **15% above the August average**, and
tracking August's second half (₹72.36) rather than its first nine days (₹44.82).
The gap is one account: Pallavi Halcyon ₹58.81 a call, Pallavi Kiran ₹76.94 on
₹1,97,583 against Halcyon's ₹1,15,915. `ad set level 3 camp` stayed the standout
at **₹45.77** across 1,102 calls; the archived `4 Numbers` campaign did 469 calls
at ₹67.68, cheaper than `Kiran | Calls — 3 Numbers | ABO` (₹72.90). Kiran's two
dearest lines, `New Leads Campaign` (₹95.69) and its copy (₹94.47), both stopped
by the 23rd. The whole 18–24 age band is Pallavi Kiran — **no Pallavi Halcyon
campaign targeted it at all**, which is why that band did not move when the last
three days were added.

**October (1–17): the cost per call fell 48% on the 10th, and the calls got
shorter.** The four per-number campaigns ran to the 9th at **₹68.09** a call
across 864 calls. On the 10th one campaign, `Halcyon | ABO | Calls | 7788 + 7272 +
9490 | 600 each` (`120255979446760348`), took the whole call budget and bought 519
calls at **₹36.86** — the cheapest line on either account since August's Age 35+
CBO, on roughly a third of the daily spend, and remarkably flat across age bands
(₹33–₹50 everywhere it reached).

**But read the duration before repeating that number.** Only 21.4% of its calls
passed 20 seconds against 24.3% for the set it replaced, and 5.4% passed a minute
against 9.6%. Per minute-long call the two are nearly level — **₹683.30 against
₹708.79** — so the headline halved while the cost of a real conversation barely
moved. The same trade runs the other way on Pallavi Kiran, which ran only 5–9 Oct:
₹124.91 a placed call, the dearest anywhere in this report, but 41.5% past 20
seconds and 21.3% past a minute — the best duration mix of the month.

`Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) is **still
₹0.00**, now across both September and October. That is the ₹19.60-a-call
campaign, dark for two and a half months. It is the single clearest thing to put
to the client, and it has been in this file since August.

## 20s and 60s calls are derived, not reported

There is **no count field** for call duration. Meta returns only an average cost
per connect, so each figure is:

    calls20s = spend / cost_per_action_type:click_to_call_native_20s_call_connect
    calls60s = spend / cost_per_action_type:click_to_call_native_60s_call_connect

**Every division must land on a whole number** — that is the check that the
derivation is sound. Assert it; if one does not, something is wrong. (Confirmed for
all 20 campaign-periods in the current data.) Same method as `o2-reports`.

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
one to watch: 132 calls, only 8 past 60 seconds, at ₹1,825 each. In October it is
the new `Halcyon | ABO | Calls` campaign for the opposite reason — the cheapest
placed call in the report and the weakest 60-second rate of any campaign in it
(5.4%).

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
age rows — lives in the `MONTHS` object keyed `aug` / `sep` / `oct`. **To add a month,
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
  this refresh they tie exactly on spend **and** on calls for both months. ₹3.55
  and 1 call (September) and ₹0.24 and no calls (October) land in an `Unknown`
  band and are omitted from the age table, which is why its total row reads a
  rupee or two under the call-campaign total.
- `reachSum` is the sum of each day's reach and double-counts people across days.
  Meta's de-duplicated August reach was 11,39,310 (Pallavi Halcyon, frequency
  2.68) and 6,12,279 (Pallavi Kiran, frequency 3.25); September 1–30 is 8,00,412
  (2.44) and 8,37,451 (3.09); October 1–17 is 6,42,176 (2.25) and 90,931 (1.46)
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
  `daysLive` is the **day range string** a month's own day rows imply
  (`"9&ndash;16"`, or `"&mdash;"` for a campaign that spent nothing), not a count.
- **A cost per call needs spend as well as calls.** 17 October has one
  late-attributed call against ₹0 of spend; the day table used to divide anyway
  and printed ₹0.00 a call. The cell now guards on both, as the campaign tables
  already did, and prints an em-dash instead.
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
