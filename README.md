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
complete) and October 2026 (1–24). October stops at the last complete day — Meta
keeps revising the most recent ~48h, and the live part-day moves between calls
minutes apart. Showing it would read as a collapse in spend that is not real. The
range under each tab name is read off that month's own `DAILY_*` rows at load, so
it cannot drift from them. **The newest tab opens first** (`let M=MONTHS.oct`);
move that and the `aria-selected` attributes together when a month is added.

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

Frozen **25 Oct 2026, 8:30 am IST**. September is now closed at 1–30; October
has been added as a third tab, covering 1–24.

| | August (1–31) | September (1–30) | October (1–24) |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,62,154.48 |
| Calls placed | 5,144 | 4,539 | 1,778 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.52** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 429 (24.1%) · **₹288.12** |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 167 (9.4%) · **₹740.15** |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.93 | ₹1,11,863.43 / 1,684 / ₹66.43 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 |

(September and October account rows are **call spend only**; website-lead spend —
₹13,712.53 in September, ₹38,549.97 in October, all Pallavi Halcyon — sits
outside them. August's Pallavi Halcyon row is total spend, its cost per call
call-only; that inconsistency is in the August figures as published.)

> **The October headline: the price of a call held, the price of a conversation
> did not.** Blended cost per call is ₹69.52, within half a rupee of September.
> But the share of calls lasting twenty seconds fell from **29.3% to 24.1%** and
> past a minute from 12.1% to 9.4%, so a real conversation went from ₹236.07 to
> **₹288.12** and a minute-long call from ₹572.08 to **₹740.15**. Same price per
> ring, a fifth less likely to be worth answering. The 60-second call has now
> risen at every refresh this report has recorded: ₹497 → ₹503 → ₹512 → ₹526 →
> ₹543 → ₹546 → ₹565 → ₹572 → **₹740**, up 46% on August.
>
> **The one clear win is consolidation.** `Halcyon | ABO | Calls | 7788 + 7272 +
> 9490 | 600 each` opened 9 October and has produced **525 calls at ₹37.11** —
> cheaper than anything in September, cheaper than any Pallavi Kiran line, and
> the closest the account has come to August's ₹19.60 benchmark. Its 20-second
> calls cost ₹172.41, also the best of the month. Running three numbers in one
> campaign is beating running them separately: the surviving per-number
> campaigns cost ₹95.14 (7788091092), ₹96.81 (7272897897) and ₹68.95
> (094906 31010). **Worth putting the budget behind the consolidated campaign.**
>
> **A campaign was renamed mid-month — check this is intentional.** On
> **6 Oct 2026, 10:14 am** (Power Editor, actor Abhijeet Lenka) campaign
> `120255796887700348` went from `Halcyon | Call 8585072072 | TS only | All days`
> to `Halcyon | Call 094906 31010 | TS only | All days`. The activity log records
> a `Campaign name updated` event and **nothing else** — no ad-level events at
> all for that campaign, so unlike the `elixir-reports` case this is a pure
> rename, not a creative swap, and its history carries forward safely. But it
> leaves **two campaigns naming 9490631010 and none naming 8585072072**. The
> report shows it under its September name on the September tab and its current
> name on the October tab. Whether the campaign's ads actually dial a different
> number now is not visible through these tools — somebody should check.
>
> **Pallavi Kiran has effectively stopped.** It spent on five days only
> (5–9 Oct, ₹11,741) at ₹124.91 a call — the dearest line in either month —
> and nothing since. 97% of October's call budget is Pallavi Halcyon.
>
> **Four dark days, 17–20 October.** Both accounts spent ₹0. Delivery resumed on
> the 21st with the website-lead campaign alone, and the 22nd and 23rd are the
> two biggest spending days of the month. Nobody has explained the gap.
>
> **Website-lead spend has become a quarter of the budget**: ₹38,549.97 in
> October against ₹13,712.53 in September, all of it `Halcyon | Enquiry LP |
> Contact-good lead`, at ₹182.70 per contact-good lead. It is kept out of every
> per-call figure, but it is now the single largest line on the account and
> should be put to the client deliberately rather than as a footnote.

**September changes since the 1–28 cut.** The last two days were the biggest
call days of the month on Pallavi Halcyon: the four new per-number campaigns took
₹17,062.70 for **283 calls at ₹60.29**, which pulled the month's blended rate
from ₹69.65 down to **₹69.07**. Pallavi Kiran spent nothing from the 28th
onward. Two revisions: Meta settled **28 September up by ₹21.14** (call spend
+₹18.45, website +₹2.69) and moved that day's call count from 68 to 64, and it
revised **1 September's website leads from 9 down to 5**. Everything else on
days 1–27 is byte-identical to the previous snapshot.

**One September figure does not tie exactly, and the page says so.** Meta's
per-day call counts sum to **4,535**, four short of its own per-campaign period
total of **4,539**, across campaigns that closed earlier in the month. The day
table shows the daily figure; every priced table (campaigns, age, funnel) uses
the campaign figure, and both reconcile internally. Four calls in 4,539 is 0.09%.
August has the same one-call version of this. Do not "fix" it by editing a day —
these are two different Meta numbers, not an arithmetic error.

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

**September (1–28).** ₹69.65 a call, 16% above the August average, tracking
August's second half (₹72.36). 23–28 Sep ran slightly cheaper (₹67.63) than
1–22 (₹70.24), but the daily series is noisy — ₹56.76 (23rd), ₹63.06, ₹67.39,
₹78.02 (26th), ₹68.74, ₹65.41 (28th) — not a trend.

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

**The new per-number campaigns have one day of data** (28 Sep): ₹4,447.54,
68 calls, ₹65.41 — from ₹43.29 (8585072072, 27 calls) to ₹377.06 (7788091092,
3 calls). Too early to judge; watch 7788091092.


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
  A small `Unknown` band is omitted from the age table every month: ₹1.93 and
  1 call in August, ₹3.55 and 1 call in September, 74 paise and no calls in
  October. **The archived `4 Numbers` campaign has no age results either**, so
  its age calls are derived the same way its totals are, from
  `cost_per_action_type:click_to_call_native_call_placed` per band; every band
  divides to a whole number (138, 136, 82, 61, 33, 19 = 469).
- **A campaign can be renamed underneath you.** Pull
  `ads_account_get_activity_logs` with `event_category: "campaign"` every refresh
  and look for `Campaign name updated`. A rename keeps the campaign id, so the
  history is safe to carry forward — but the name on a past month's tab should
  stay the name it ran under then, which the per-month `campCalls` arrays make
  easy. Check `event_category: "ad"` on the renamed campaign too: if ads changed
  as well, it may be a creative swap rather than a rename (see `elixir-reports`),
  and the history must then be split.
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
