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
(1–31) are complete and settled; November 2026 runs 1–22. November stops at the
last complete day — Meta keeps revising the most recent ~48h, and the live
part-day moves between calls minutes apart. Showing it would read as a collapse
in spend that is not real. The range under each tab name is read off that
month's own `DAILY_*` rows at load, so it cannot drift from them.

**The page opens on November**, the newest tab (`let M=MONTHS.nov` and the
`aria-selected="true"` button must stay in step). November is mostly zero rows
because delivery stopped on the 5th — that is the point, and its note card says
so; the earlier months are one click away.

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

Frozen **23 Nov 2026, 8:40 am IST**, data window **1 Aug – 22 Nov 2026**.
September and October are closed; November runs to the 22nd.

> **Delivery stopped on 5 November and has not restarted.** Neither account has
> spent a rupee or served an impression since 5 Nov — seventeen consecutive zero
> days to the 22nd. Every campaign on both accounts is paused or archived.
> Nothing in the reporting API says why; **check the billing/balance state and
> the activity log before the next refresh**, because if this was not deliberate
> the client is dark and does not know it.
>
> **Pallavi Kiran has been dark since 28 September** apart from 5–9 October
> (₹11,741.08, 94 calls).
>
> **A third result type arrived in November.** `Halcyon | ABO | WhatsApp |
> 6 numbers | 700 each | Telangana regions` (`120256437300820348`) optimises
> `onsite_conversion.messaging_conversation_started_7d` — not a call, not a
> pixel event. It took ₹4,160.90 over 4–5 Nov for **56 conversations at ₹74.30**.
> It sits in the website-lead (`campWeb`) table with its event named, exactly as
> the four pixel events already do, and is kept **out of every cost-per-call
> figure**. The `DAILY_*` row format was not changed to carry it — its spend goes
> in the `a1WebSpend` column and its count in `a1WebLeads`, which is what that
> column has always meant: "a result that is not a phone call".
>
> **Fixed a published error in the August tile.** `MONTHS.aug` carried
> `impressions: 2338227, clicks: 6921`. The account totals for August are
> **50,47,184 impressions and 27,226 link clicks** (Pallavi Halcyon 30,54,990 /
> 22,207 + Pallavi Kiran 19,92,194 / 5,019), which is exactly what `DAILY_AUG`
> already summed to. The August Reach tile had been understating impressions by
> 27 lakh since publication. Both values are now corrected. Spend, calls, cost
> per call and reach in that tab were always right.

> **The Pallavi Kiran "coverage gap" was an archived campaign.** From 23 Sep the
> Kiran campaign rows summed to only 33.8% of the account's spend. The missing
> ₹31,740.53 was in `Halcyon | Calls — 4 Numbers | ABO | 22 Sep`
> (`120251289083450425`), which ran 23–27 Sep and is now **ARCHIVED**. Archived
> (and deleted) campaigns are **not returned by an unfiltered campaign listing** —
> you must filter `effective_status IN [..., "ARCHIVED", "DELETED"]` to see them.
> With it included, campaign rows equal the account's daily spend and impressions
> on every day, both accounts, to the paisa.
>
> **Its calls are derived.** Meta labels it a lead campaign (`results` indicator
> `actions:lead`, "Not available"), though it is a call campaign. Calls =
> `spend / cost_per_action_type:click_to_call_native_call_placed` (request the
> plain `cost_per_action_type` field; the `:subtype` form is rejected). Every day
> divides to a whole number: 76, 111, 102, 93, 87 = **469 calls**. The same check
> reproduces `results` exactly on every other call campaign.
>
> **Structural change on 28 Sep.** Pallavi Kiran spent ₹0 — every campaign on it
> is paused or archived. On Pallavi Halcyon the old call campaigns are paused and
> four new per-number call campaigns started (`Halcyon | Call 8585072072 / 7788091092
> | TS only | All days`, `Halcyon | Call 7272897897 / 9490631010 | TS+AP | All days`),
> plus a new website-lead campaign `Halcyon | Enquiry LP | Contact-good lead |
> Mon–Sat 9–5` optimising a **custom conversion** (`offsite_conversion.custom.1564834054962652`)
> — a fourth distinct lead event, kept out of cost per call.
>
> **Meta revised 28 Sep after publication** by +₹21.14 (call spend +₹18.45,
> Enquiry LP +₹2.69); its call count did not move. Everything from 1 to 27 Sep
> is unchanged from the previous cut.

| | August (1–31) | September (1–30) | October (1–31) | November (1–22) |
|---|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,68,508.95 | ₹10,594.70 |
| Call spend | ₹3,08,602.82 | ₹3,13,497.97 | ₹1,27,364.09 | ₹5,245.18 |
| Calls placed | 5,144 | 4,539 | 1,834 | 60 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.45** | **₹87.42** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,326 (29.2%) · ₹236.42 | 442 (24.1%) · ₹288.15 | 17 (28.3%) · ₹308.54 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 172 (9.4%) · ₹740.49 | 6 (10.0%) · ₹874.20 |
| Non-call spend | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹41,144.86 / 226 | ₹5,349.52 / 69 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,56,767.87 / 1,740 / — | ₹10,594.70 / 60 / — |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.90 | ₹0.00 / 0 / — |

(September's and November's Pallavi Halcyon rows are **call spend only** where a
cost per call is quoted; October's Pallavi Halcyon figure is total account spend,
so no per-call rate is given for it — ₹41,144.86 of it was the landing page.
August's Pallavi Halcyon row is total spend with a call-only cost per call —
that inconsistency is in the August figures as published and is left alone.)

Previous cut (1–28 Sep, published 29 Sep): ₹3,04,514.33 · 4,256 calls · ₹69.65.

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

**September closed at ₹69.07** a call, 15% above the August average and tracking
August's second half (₹72.36). The last three days are the cheapest stretch —
₹61.34 over 28–30 Sep against ₹69.72 over 1–27 — and they are entirely the four
new per-number campaigns, which took ₹21,528.69 for 347 calls at ₹62.04 but
spread from ₹46.62 (094906 31010, 117 calls) to ₹104.71 (7788091092, 51 calls).
`ad set level 3 camp` stays the standout at **₹45.76** across 1,102 calls. The
account gap persisted to the end: Pallavi Halcyon ₹58.81, Pallavi Kiran ₹76.94.

**October held the price and bought half the calls.** ₹69.45 a call against
₹69.07, but **59 calls a day against 151** — the call budget was cut from
₹3,13,498 to ₹1,27,364 and a quarter of what was left went to the landing page.
The month is not smooth: **eight days with no spend and no impressions at all**
(17–20 and 25–28 Oct) and three more under ₹1,700.

- The winner is `Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each`
  (`120255979446760348`): **525 calls at ₹37.11** in nine days — 29% of the
  month's calls on 15% of its call budget, the cheapest call campaign on either
  account since August's 35+ FB-only line. **But it does not hold callers**:
  21.5% past 20s and 5.3% past a minute, the weakest rates in the table, so its
  20s call is ₹172.41 and its 60s call ₹695.81. Still best on both, by much less
  than the headline suggests.
- The three per-number `All days` campaigns it replaced cost two and a half times
  as much: ₹94.80 / ₹96.81 / ₹68.95, with `9490631010` at ₹59.68 before it
  stopped on the 9th.
- Kiran's five days are the dearest line of the month —
  `Calls | ABO | Hyderabad | Ara + Top Performers`, ₹10,486.48 for 83 calls at
  **₹126.34** — but the best on duration: 38.6% past 20s, 19.3% past a minute,
  ₹655 a minute-long call.

**November is five days and then nothing.** ₹10,594.70, 60 calls at ₹87.42 (too
few to read a rate from), and for the first time **calls were under half the
spend**: ₹5,245.18 on calls, ₹1,188.62 on the Enquiry LP landing page, ₹4,160.90
on the new WhatsApp campaign. Delivery stopped on the 5th.

**The minute-long call keeps getting dearer:** ₹507.57 (Aug) → ₹572.08 (Sep) →
₹740.49 (Oct) → ₹874.20 (Nov, 6 calls). The Oct–Nov steps are partly a smaller,
noisier sample, but the direction has not reversed once since August.

**`Halcyon | Calls — Age 35+ | FB only | CBO` (₹19.60 a call in early August)
has still spent ₹0.00** in September, October and November. It remains the
cheapest call campaign either account has ever run.


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

## Three result types — do not merge them

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

From 28 Sep a fifth event joined them: `Halcyon | Enquiry LP | Contact-good lead`
optimises the **custom conversion** `offsite_conversion.custom.1564834054962652`.

**Messaging campaigns** (November, Pallavi Halcyon) are the third type:
`Halcyon | ABO | WhatsApp | 6 numbers | 700 each | Telangana regions` reports
`results` with indicator
`actions:onsite_conversion.messaging_conversation_started_7d`. A WhatsApp
conversation is not a phone call and not a pixel event.

The page names the event on every row and keeps all of this spend **out of cost
per call**. Blending the August website-lead budget in reads ₹70.38 against the
true ₹59.99 and overstates what a call costs — don't. The same rule applies to
the WhatsApp spend: in November it is 39% of the month, and blending it would
read ₹176.58 a call instead of ₹87.42.

## Refreshing

`DAILY_AUG` / `DAILY_SEP` / `DAILY_OCT` / `DAILY_NOV` rows are
`[day, a1CallSpend, a1Calls, a1WebSpend, a1WebLeads, a2CallSpend, a2Calls, impressions, reachSum, linkClicks]`
where `a1` = Pallavi Halcyon, `a2` = Pallavi Kiran. `day` is the day of month.

Everything else a tab shows — headline totals, narrative copy, campaign tables,
age rows — lives in the `MONTHS` object keyed `aug` / `sep` / `oct` / `nov`.
**To add a month, add a `DAILY_*` array and a `MONTHS` entry, then add one
`<button class="tab">` with a matching `data-month`.** Nothing else is
month-specific. Each entry also carries `whole: true|false` — a complete calendar
month or a part window — which is all that decides whether the chart's reference
line reads "month average" or "period average".

**Keep zero rows.** A day the account served nothing (no spend, no impressions)
gets a row of zeros, not an omission: eight such days in October and seventeen in
November, and dropping them would turn a delivery stop into a shorter month. Some
of those rows still carry a late-attributed call or conversation earned by the
days before them (6 Nov: 3 WhatsApp conversations on ₹0.00) — keep those too.

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
  A few rupees and the odd call land in an `Unknown` band and are omitted from
  the age table.
- **`cost_per_action_type:click_to_call_native_*` is not reliably available with
  an `age` breakdown.** On the 23 Nov refresh Meta accepted it for Pallavi
  Halcyon on one call and rejected it as an unsupported field minutes later, and
  rejected it for Pallavi Kiran every time. Where `results` is populated the age
  split still works; where it is not — the archived `4 Numbers` campaign, whose
  `results` indicator is `actions:lead` / "Not available" — **there is no way to
  split its calls by age**. September's age table therefore holds that campaign
  out entirely, spend *and* calls (₹31,740.53 / 469), and `ageIntro` says so.
  Do not apportion its calls across bands: band spend without band calls makes
  every band read dearer than it was, which is the error that rule prevents.
- `reachSum` is the sum of each day's reach and double-counts people across days.
  The de-duplicated per-account figures in `MONTHS[].reach` come from an
  account-level call with `time_increment: "monthly"` (or none), never from
  summing days: Aug 11,39,310 (freq 2.68) / 6,12,279 (3.25); Sep 8,00,412 (2.44)
  / 8,37,451 (3.09); Oct 8,55,599 (2.34) / 90,931 (1.46); Nov 82,250 (1.40) / 0.
  When the second account did not spend, the Reach tile prints one figure instead
  of `… + 0.0L` — that is driven off `M.reach[1]` being zero, not off the month.
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
- Update the snapshot date in the masthead, in the `Baked figures` comment at the
  top of the `<script>` block, and in this README.
- **Check the headline tile values against the `DAILY_*` sums, not just the
  campaign rows.** `MONTHS[].impressions` and `.clicks` must equal the sums of
  columns 8 and 10 of that month's `DAILY_*` array, and `.spend` must equal
  `.callSpend + .webSpend`. August shipped with `impressions` and `clicks` that
  matched neither (fixed on 23 Nov) because nothing asserted it; the campaign
  reconciliation alone would not have caught it.
