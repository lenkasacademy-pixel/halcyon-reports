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
(1–31) are complete months; November 2026 runs **1–27**. The live month always
stops at the last complete day — Meta keeps revising the most recent ~48h, and
the part-day moves between calls minutes apart. Showing it would read as a
collapse in spend that is not real. The range under each tab name is read off
that month's own `DAILY_*` rows at load, so it cannot drift from them.

> **November is almost entirely empty, and that is the report's headline.**
> Both accounts stopped delivering after **5 November** and have shown zero
> spend and zero impressions on every day since — 22 consecutive days to the
> 27th. Pallavi Kiran has been dark even longer: its last delivery was
> **9 October**. Nothing in Meta's data says why; no campaign is serving. The
> November tab carries this in its `partNote` rather than reading as a
> performance collapse, because it is not one.

## What it shows

- Amount spent, phone calls placed, blended cost per call, reach.
- A three-panel day-wise chart on one shared calendar: daily spend stacked by
  account (with the website-lead spend split out), calls placed stacked by
  account, and cost per call against that period's average. One hover reads all three.
- A two-up comparison card carrying each tab's headline finding (August's
  1–9 vs 10–31 split; September against the August average; October against
  September; November against October).
- A **call-quality funnel**: placed → 20s+ → 60s+, with each step's share of
  placed calls and its true cost.
- Per-campaign totals for the call campaigns and, separately, the non-call
  campaigns. That second table's footer label is per-month (`webFoot`, falling
  back to "All website-lead campaigns") because from November it holds a
  WhatsApp campaign too, which is not a website lead.
- Calls and cost per call by age band, both accounts combined.
- The full day-by-day table for the selected month.

## Snapshot

Frozen **28 Nov 2026, 8:25 am IST**. Data windows: August 1–31, September 1–30,
October 1–31, November 1–27. September was previously published as 1–28 and is
now complete.

| | August (1–31) | September (1–30) | October (1–31) | November (1–27) |
|---|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,68,508.95 | **₹10,594.70** |
| Calls placed | 5,144 | 4,539 | 1,834 | **60** |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.45** | ₹87.42 (noise) |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 442 (24.1%) · ₹288.15 | 17 · ₹308.54 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 172 (9.4%) · **₹740.49** | 6 · ₹874.20 |
| Call spend | ₹3,08,602.82 | ₹3,13,497.97 | ₹1,27,364.09 | ₹5,245.18 |
| Non-call spend | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹41,144.86 / 226 | ₹5,349.52 / 69 |
| Pallavi Halcyon (call) | ₹2,18,901.90 | ₹1,15,914.55 | ₹1,15,623.01 | ₹5,245.18 |
| Pallavi Kiran (call) | ₹1,43,144.70 | ₹1,97,583.42 | ₹11,741.08 | **₹0** |

All figures are **ex-GST** (Meta bills 18% GST on top in India). Unlike
`o2-reports`, this page does not show a GST-inclusive billed total — if the
client asks for one, add it, don't silently change the per-call numbers.

## The findings

**Cost per call is flat across three months and then unreadable.**
₹59.99 in August, **₹69.07** in September, **₹69.45** in October — September and
October are the same number within half a rupee. November's ₹87.42 rests on 60
calls and should not be read at all; a single campaign's noise moves it by more
than ten rupees.

**Completing September moved it the right way.** The 1–28 cut read ₹69.65; the
whole month reads **₹69.07**, because the 29th and 30th were the first full days
of the restructured account and they delivered cheaply. The four new per-number
campaigns bought **347 calls at ₹62.04 over 28–30 September**, against ₹70.24
across the first twenty-two days.

**A campaign was renamed at Meta.** The line published last time as
`Halcyon | Call 8585072072 | TS only | All days` is the same campaign object —
id `120255796887700348`, created 28 September — now called
`Halcyon | Call 094906 31010 | TS only | All days`. The phone number in its name
changed, not the campaign; its history carries forward. Campaign names are plain
labels in `campCalls` (there is no index array as in `elixir-reports`), so a
rename cannot corrupt a historical row here — but check for one anyway, because
the September table's row names change between cuts without the figures moving.

**October's finding is one campaign, and it is the best result since August.**
`Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each` opened on the 9th and
bought **525 calls at ₹37.11** — the cheapest call on this account since
August's `Age 35+ | FB only | CBO` line (₹19.60), and at scale: more calls than
any other campaign in the month. It is also the best on connected calls at
**₹172.41 per 20-second call**. One ABO campaign carrying three numbers beat all
four single-number campaigns, which ran ₹68.95 to ₹96.81. **That is the
structure worth repeating.**

**7788091092 is consistently the clinic's weakest number.** Dearest of the four
per-number campaigns in September (₹104.71) and the worst 20-second rate in
October (₹437.64). It was also the one flagged in the September cut at ₹377.06
on three calls. Three cuts, same answer.

**The minute-long call keeps getting dearer.** ₹507.57 (August) → ₹572.08
(September) → **₹740.49 (October)**, the dearest anywhere in this report.
October bought calls at September's price but kept fewer of them on the line:
24.1% past twenty seconds against 29.3%.

**Pallavi Kiran has effectively stopped.** ₹1,97,583 in September, ₹11,741 across
five days in October (5–9), nothing since. Its October spend was the dearest of
the month — `Calls | ABO | Hyderabad | Ara + Top Performers` took ₹10,486.48 for
83 calls, **₹126.34 each** — so on the evidence stopping it was right.

**Delivery gaps are real, not missing data.** October ran 22 of 31 days: nothing
at all on 17–20 and 25–28 October, website-lead spend only on the 21st.
November ran 5 of 27. Campaign rows equal each account's own daily total on
spend *and* impressions on every day of all four months, including the empty
ones — which is what proves the gaps are genuine zero-delivery days.

**Still unresolved from August:** `Halcyon | Calls — Age 35+ | FB only | CBO`
returned 410 calls at ₹19.60 on ~₹1,000/day and stopped after 8 August. It has
spent **₹0.00 in September, October and November**. October's ABO campaign is
the closest anything has come to it since.

## Three result types — do not merge them

**Call campaigns** report `results` with indicator
`actions:click_to_call_native_call_placed` ("Phone calls placed"). There is no
queryable `calls` field — `ads_get_field_context` returns `calls`,
`call_confirm` and `click_to_call_*` as unknown. Same trap as `o2-reports`.

**Website-lead campaigns** (Pallavi Halcyon only) each optimise for a
*different* pixel event, so their counts are **not one comparable number**:

| Campaign | Event |
|---|---|
| `Halcyon \| LP 8585 \| Website Leads` | `HContacted` |
| `Halcyon \| LP 7788 \| Website Leads` | `HContacted` |
| `Halcyon \| LP 8585 \| Website Leads \| 7788` | `HEnquiry` |
| `Halcyon \| LP 8585 \| Website Leads \| TEST - Copy` | `offsite_conversion.fb_pixel_lead` |
| `Halcyon \| Enquiry LP \| Contact-good lead \| ...` | `offsite_conversion.custom.1564834054962652` |

**WhatsApp campaigns are new as of November and are a third kind again.**
`Halcyon | ABO | WhatsApp | 6 numbers | 700 each | Telangana regions` ran on 4–5
November and reports `results` with indicator
`actions:onsite_conversion.messaging_conversation_started_7d` — 56 conversations
on ₹4,160.90, **₹74.30 each**. It is neither a phone call nor a website lead.

The page names the event on every row and keeps **all** non-call spend out of
cost per call. Blending it in reads ₹70.38 for August instead of the true
₹59.99 and overstates what a call costs — don't.

> **A judgement call to review.** The non-call table's footer sums spend and
> counts across *different* events and labels the event column "mixed" — that
> was already true in August (HContacted + HEnquiry + fb_pixel_lead). November's
> WhatsApp conversations are now folded into the same mixed total, so that
> month's footer reads ₹5,349.52 / 69 / ₹77.53 across two incomparable events.
> The per-row figures stay honest; only the footer blends. If that is not wanted,
> the fix is to split the non-call table by event type rather than to drop the
> WhatsApp row, which would leave its spend unaccounted for.

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
age rows — lives in the `MONTHS` object keyed `aug` / `sep` / `oct` / `nov`.
**To add a month, add a `DAILY_*` array and a `MONTHS` entry, then add one
`<button class="tab">` with a matching `data-month`.** Nothing else is
month-specific. `webFoot` is optional and only needed when the non-call table
holds something other than website leads; it falls back to "All website-lead
campaigns".

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
  appending. Completing September on this refresh moved its cost per call from
  ₹69.65 to ₹69.07 and its 20-second call from ₹234.69 to ₹236.07 — the part-day
  rule earned its keep again.
- **Campaign-daily pulls with `cost_per_action_type` are large and spill to a
  file.** That is the cheap way to do this: let them spill, then aggregate the
  files with a script rather than reading rows inline. Keep each call under 200
  campaign-days (split the month in half, or pass only the `object_ids` that
  actually spent).
- **Watch for renamed campaigns.** Match on campaign id and `created_time`, not
  on name; see the 8585072072 → 094906 31010 rename above.
- **Zero-spend campaigns can still carry results.** `Halcyon | LP 8585 |
  Website Leads` reports 4 `HContacted` conversions in September on ₹0 spend — a
  lagging pixel event from its August run. A campaign listing filtered to
  `amount_spent > 0` drops it; it is carried here deliberately, with a note on
  the row.
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
