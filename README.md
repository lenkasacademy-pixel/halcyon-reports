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

**Scope: three tabs, all complete months.** August 2026 (1–31), September 2026
(1–30) and October 2026 (1–31). Every one of them has closed and settled, so no
tab holds back a live part-day. When a month *is* still running, stop it at the
last complete day — Meta keeps revising the most recent ~48h, and the live
part-day moves between calls minutes apart; showing it reads as a collapse in
spend that is not real. The range under each tab name is read off that month's own
`DAILY_*` rows at load, so it cannot drift from them. **November is not a tab
yet** — see the section below; it is blocked on a structural decision, not on data.

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

Frozen **5 Nov 2026, 8:11 am IST**. **Three tabs, all complete months:** August
(1–31), September (1–30) and **October (1–31, new)**. No tab holds back a
part-day any more — August, September and October have all closed.

| | August (1–31) | September (1–30) | **October (1–31)** |
|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | **₹1,68,508.95** |
| Calls placed | 5,144 | 4,539 | **1,834** |
| Cost per call | ₹59.99 | ₹69.07 | **₹69.45** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | **442 (24.1%) · ₹288.15** |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | **172 (9.4%) · ₹740.49** |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | **₹1,15,623.01 / 1,740 / ₹66.45** |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | **₹11,741.08 / 94 / ₹124.91** |
| Website leads | ₹53,443.78 / 332 | ₹13,712.53 / 67 | **₹41,144.86 / 226 · ₹182.06** |

(September and October account rows are **call spend only**; website-lead spend
sits outside them, as it always has. August's Pallavi Halcyon row is total spend
with a call-only cost per call — that inconsistency is in the August figures as
published and has been left alone.)

### September closed cheaper than the 28th cut suggested

The previous cut stopped at 28 Sep (₹3,04,514.33 · 4,256 calls · ₹69.65). The
last three days were the **biggest of the month** on Pallavi Halcyon — ₹8,443 on
the 28th, ₹11,858 on the 29th, ₹10,817 on the 30th — because four new per-number
call campaigns and a new Enquiry LP campaign all opened on the 28th. Those days
added 283 calls at ₹61.09, pulling the month down to **₹69.07**.

**Pallavi Kiran stopped on 27 September** and spent nothing for the rest of the
month, so every day from the 28th is Pallavi Halcyon alone.

**`Halcyon | Call 8585072072 | TS only | All days` is the quality find of the
month** — 117 calls in three days at ₹46.62, and **₹147.43 per twenty-second
call**, better than `ad set level 3 camp` (₹198.56) and the best such figure in
either month. On nearly the same three-day budget the 7788091092 campaign managed
51 calls at ₹104.71. Same days, same account, same budget: the number being
dialled is doing the work.

**The 18–24 band is entirely Pallavi Kiran's.** No Pallavi Halcyon call campaign
delivered a single impression under 25 in September. Worth knowing before reading
the age table as an account-wide audience statement.

### October: the price of a call held, the quality of one did not

**This is the finding to lead with.** Cost per call moved 38 paise, ₹69.07 →
**₹69.45**. But the share of calls that lasted twenty seconds fell **29.3% →
24.1%** and past a minute **12.1% → 9.4%**, so the same ₹69 buys materially less:

| | Sep | Oct | change |
|---|---|---|---|
| Cost per call placed | ₹69.07 | ₹69.45 | +0.5% |
| Cost per 20-second call | ₹236.07 | **₹288.15** | **+22%** |
| Cost per 60-second call | ₹572.08 | **₹740.49** | **+29%** |

Both duration figures are the **highest on the whole page**, August included.

**One campaign explains most of it.** `Halcyon | ABO | Calls | 7788 + 7272 + 9490
| 600 each`, opened 9 Oct, bought **525 of the month's 1,834 calls at ₹37.11** —
the cheapest line in any month here — but only 28 of those 525 held a minute
(5.3%). Strip it out and the rest of October held 13.4% past a minute, in line
with September. It is the August `Age 35+ | FB only | CBO` trade-off again: the
cheapest placed call and among the worst 60-second rates. **Keep both numbers in
front of the client whenever this campaign is praised.**

**Pallavi Kiran has effectively stopped.** ₹11,741.08 all month against
₹1,97,583.42 in September, served on five days only (5–9 Oct), 94 calls at
**₹124.91** — the dearest line on either account in any month this report covers.

**Website leads took a quarter of the account and are priceable for the first
time.** Enquiry LP spend went ₹13,712.53 → ₹41,144.86 and produced 226 leads at
**₹182.06**. Both October rows are the same custom conversion, so unlike the
earlier months those two counts *are* comparable with each other — but still not
with HContacted, HEnquiry, or calls. **Blending it into cost per call would read
₹91.88 instead of ₹69.45.** Don't.

**Delivery stopped twice**, on both accounts: nothing at all on 17–20 October and
again on 25–28 October. Nothing in the activity log explains either gap; the page
shows them as flat stretches rather than hiding them.

**August's cheap `Halcyon | Calls — Age 35+ | FB only | CBO` is still at ₹0.00**
across September and October. It returned 410 calls at ₹19.60 in early August.
Two full months later nobody has restarted it.

## ⚠ A campaign changed the number it dials, and kept its history

**On 6 October 2026, 10:14 am** (activity log, Power Editor, actor Abhijeet
Lenka) campaign **`120255796887700348`** was renamed:

    Campaign name updated
      old_value  "Halcyon | Call 8585072072 | TS only | All days"
      new_value  "Halcyon | Call 094906 31010 | TS only | All days"

Three days later, on **9 October**, a new ad — `9490 | Proven | "1" video
(reused, 55/call, 3592 calls)` — started delivering inside it, alongside its
existing `8585 | …` ads. So:

- Its **September** figures (₹5,455.00, 117 calls, 28–30 Sep) were earned by
  **8585072072**. The September tab keeps the old name on that row on purpose.
  Relabelling it would quietly reassign September's best-quality line
  (₹147.43 per 20-second call) to a different clinic number.
- Its **October** figures (₹25,578.75, 371 calls) **mix two numbers**.
- There is now **no campaign dialling 8585072072 at all**, while *two* campaigns
  carry 9490631010 (`| TS only |` and `| TS+AP |`).

**Ask whether that rename was intended.** This is the same hazard
`elixir-reports` documents at ad level: a rename can hide a destination swap, and
every total still balances because the numbers are real — just attached to the
wrong label. The reconciliation did not catch it; the missing campaign name did.
**If a per-number campaign's name changes, pull the activity log before carrying
its history forward, and keep the old name on the months it ran under.**

## November is not a tab yet — and that is a decision, not an oversight

November is still running (₹8,803.23 on Pallavi Halcyon over 1–5 Nov; Pallavi
Kiran ₹0.00), so it would be shown without its live part-day as usual. That part
is routine. The blocker is different:

**On 4 November at 2:42 pm the account started
`Halcyon | ABO | WhatsApp | 6 numbers | 700 each | Telangana regions`** — and its
result is `onsite_conversion.messaging_conversation_started_7d`, a **WhatsApp
messaging conversation**. Over 1–4 Nov it took **₹1,943.45 for 26 conversations**
(₹74.75 each). At the same time the three `Daily 500` call campaigns and
`Enquiry LP | Daily 1000` were all switched off.

That is a **third result type**, alongside phone calls and website leads. The
`DAILY_*` row format has exactly two spend columns for Pallavi Halcyon —
`a1CallSpend` and `a1WebSpend` — and the spend chart stacks exactly three bands.
Messaging spend fits neither column:

- putting it in `a1WebSpend` would merge two incomparable result types, which the
  *Two result types* rule below forbids;
- dropping it would break the day-level reconciliation by exactly ₹1,943.45;
- keeping it out of cost per call is right, but it still has to appear somewhere.

So adding November needs **a fourth category** — a `DAILY_*` column pair, a fourth
chart band and legend entry, a day-table column, and a messaging campaign table —
plus a decision on how to present a conversation next to a call. That is a feature,
not a refresh. **August, September and October are complete and published; November
is waiting on that call.**

## The findings

Cost per call rose **61%** on 10 August: ₹44.82 (2,310 calls on ₹1,03,528) for
1–9 Aug, ₹72.36 (2,834 calls on ₹2,05,075) for 10–31 Aug. Two causes, both real:

1. ₹53,444 — 34% of the Pallavi Halcyon budget from the 10th — moved to
   website-lead campaigns, which do not produce calls.
2. `Halcyon | Calls — Age 35+ | FB only | CBO` (`120254451805720348`) stopped
   after 8 Aug. It returned **410 calls at ₹19.60**, the month's best by a wide
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 across 1–28 Sep.

**September (1–30, closed).** ₹69.07 a call, 15% above the August average,
tracking August's second half (₹72.36). The daily series is noisy throughout —
₹56.76 (23rd), ₹78.02 (26th), ₹68.74, ₹65.41 (28th) — so read month totals, not
days. **October then landed at ₹69.45, all but identical**, which makes the
duration collapse described in the Snapshot the only thing that actually moved.

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
- **Adding a month is three edits** — one `DAILY_*` array, one `MONTHS` entry, one
  `<button class="tab" data-month=...>`. October was added exactly that way and
  nothing else in the file is month-specific. The one thing that breaks the rule is
  a **new result type**, which needs a new `DAILY_*` column and a new chart band —
  that is what November is waiting on.
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
