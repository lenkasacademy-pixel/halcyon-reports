# Halcyon Pain Management — Meta Ads calls report

Client-facing report for **Halcyon Pain Management**, covering **both** ad accounts:

| Account | ID | What it runs |
|---|---|---|
| Pallavi Halcyon | `1999324147481098` | Call ads + website-lead campaigns |
| Pallavi Kiran | `694358492762548` | Call ads only |

Live: https://lenkasacademy-pixel.github.io/halcyon-reports/

A single self-contained `index.html` with a **month tab bar** (August /
September). Figures are baked into the `DAILY_AUG` / `DAILY_SEP` arrays and the
`MONTHS` object near the bottom of the file — nothing calls the network.

**Scope: two tabs.** August 2026 (1–31, complete) and September 2026 (1–28).
September stops at the last complete day — Meta keeps revising the most recent
~48h, and the live part-day moves between calls minutes apart. Showing it would
read as a collapse in spend that is not real. The range under each tab name is
read off that month's own `DAILY_*` rows at load, so it cannot drift from them.

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

Frozen **25 Nov 2026, 8:15 am IST**. **Four tabs now: August, September, October,
November.** August, September and October are complete months; November stops at the
24th because 25 November is a live part-day.

> ## Both ad accounts are dark
>
> **The last rupee spent on this client anywhere was 5 November 2026.** Nineteen days
> have passed with no impressions and no spend on either account, and the 25th is
> showing nothing so far either.
>
> - **Pallavi Halcyon** last spent **5 Nov** (the WhatsApp campaign). Its call campaigns
>   stopped on the 4th and its website-lead campaign on the 2nd.
> - **Pallavi Kiran** last spent **9 Oct** — forty-six days ago. In the whole of October
>   it took only ₹11,741.08 across five days (5–9 Oct), and nothing in November.
>
> Nothing in the activity data explains it, and this report cannot tell a deliberate
> pause from a billing failure. **Check it before reading anything else on the page.**

| | Aug (1–31) | Sep (1–30) | Oct (1–31) | Nov (1–24) |
|---|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,68,508.95 | ₹10,594.70 |
| Calls placed | 5,144 | 4,539 | 1,834 | 60 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.45** | **₹87.42** |
| Lasted 20s+ | 1,448 (28.1%) | 1,328 (29.3%) | 442 (24.1%) | 17 (28.3%) |
| Lasted 60s+ | 608 (11.8%) | 548 (12.1%) | 172 (9.4%) | 6 (10.0%) |
| Call spend | ₹3,08,602.82 | ₹3,13,497.97 | ₹1,27,364.09 | ₹5,245.18 |
| Website-lead spend | ₹53,443.78 / 332 | ₹13,712.53 / 63 | ₹41,144.86 / 226 | ₹1,188.62 / 13 |
| WhatsApp spend | — | — | — | ₹4,160.90 / 56 |

All figures are **ex-GST** (Meta bills 18% GST on top in India). Per-call figures cover
**call campaigns only** — website-lead and WhatsApp spend sit outside every one of them.

### September is now the full month

The previous cut stopped at the 28th. The 29th and 30th have settled and added
**₹22,675.03 and 283 calls**; days 1–28 were revised up by ₹21.14. The month closes at
₹69.07 a call against the ₹69.65 published for 1–28.

**The 28 September rebuild made calls cheaper.** 1–27 Sep ran at ₹69.72 a call across
4,188 calls on the old structure; 28–30 Sep ran at **₹61.34** across 351 calls on the
four new per-number campaigns, with Pallavi Kiran already silent. Three days is not a
result, but it is the right direction.

### October: cheap, then stop-start and expensive

Spend halved to ₹1,68,509, almost entirely because Pallavi Kiran stopped.

**Calls cost 73% more after the 16th.** 1–16 Oct bought 1,476 calls at **₹60.77** — the
best call buying anywhere in this report. The account then went dark 17–20, came back on
the 21st, spent ₹36,515 in a three-day burst on 22–24 at **₹112.63 a call**, and stopped
again. 17–31 Oct averages ₹105.20. Stop-start delivery is expensive; every restart
re-enters the learning phase.

**The best line in months is `Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each`**:
9–24 Oct, ₹19,482.72, **525 calls at ₹37.11**. Watch the duration though — only 5.3% of
its calls reached sixty seconds, the weakest rate of the month, the same flattery the
August `Age 35+` line showed.

**Website-lead spend rose to ₹41,144.86 — a quarter of the month** and 26% of the Pallavi
Halcyon budget, for 226 custom-conversion leads at ₹182.06 each.

**Calls got shorter in October**: 24.1% past twenty seconds against September's 29.3%, and
9.4% past a minute against 12.1%.

### November: five days, a new channel, then nothing

Three per-number call campaigns ran 1–4 Nov and bought 60 calls at **₹87.42** — the
dearest call in the report, pointing the same way as late October.

**A WhatsApp campaign started on 4 November**, the first on either account:
`Halcyon | ABO | WhatsApp | 6 numbers | 700 each | Telangana regions`, two days,
**₹4,160.90 for 56 conversations started at ₹74.30 each**. See the next section — it is a
third result type and the page had to grow a column for it.

## A third result type: messaging

The page used to have exactly two buckets per account-day: call spend and website-lead
spend. November's WhatsApp campaign is neither, and dropping it would have left
₹4,160.90 of real spend off the page or, worse, mislabelled as a website lead.

`DAILY_*` rows are now **twelve** fields, not ten:

`[day, a1CallSpend, a1Calls, a1WebSpend, a1WebLeads, a2CallSpend, a2Calls, impressions, reachSum, linkClicks, a1MsgSpend, a1MsgConvos]`

`DAILY_AUG` is left at ten fields on purpose — the reader uses `(r[10]||0)`, so older
months need no edit. Four places consume the new fields: the stacked spend panel, the
hover tooltip, the day table (two new columns, em-dashed for months without messaging)
and its footer. A month with `campMsg` also renders a messaging-campaigns section;
without it the section stays `hidden`.

`msgSpend` and `msgConvos` are **never** added into cost per call or into the website-lead
table. A WhatsApp conversation is not a phone call.

### Adding a month, updated

One `DAILY_*` array + one entry in the `MONTHS` object + one `<button class="tab">` with a
matching `data-month`. That is still true. If the month has messaging, also give its
`MONTHS` entry `msgSpend`, `msgConvos`, `msgTitle`, `msgIntro` and `campMsg`; if it does
not, omit all five and the section hides itself.

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
  campaign listing silently omits them. **This bit again on 25 Nov**: a listing filtered
  on `amount_spent > 0` instead of `effective_status` dropped the same archived
  `4 Numbers` campaign and left Pallavi Kiran ₹31,740.53 short. The account
  reconciliation caught it immediately. Filter on `effective_status`, not on spend. On 28 Sep this made ₹31,740.53 of Pallavi
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
- Re-pull whole months, not just the new one. The 29th and 30th of September only
  appeared on this refresh, and days 1-28 moved by ₹21.14 while they were at it.
