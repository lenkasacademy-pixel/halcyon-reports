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

**Scope: four tabs.** August (1–31), September (1–30) and October (1–31) are
complete, settled months; November runs 1–24. **November opens by default** —
it is the live month, and it is the one that needs reading.

Normally the live part-day is held back, because Meta keeps revising the most
recent ~48h and it moves between calls minutes apart. **There is no part-day to
hold back this time:** neither account has spent anything since 5 November, so
every day on the page is settled and nothing is excluded. The range under each
tab name is read off that month's own `DAILY_*` rows at load, so it cannot drift
from them.

## What it shows

- Amount spent, phone calls placed, blended cost per call, reach.
- A three-panel day-wise chart on one shared calendar: daily spend stacked by
  account (with the website-lead spend split out), calls placed stacked by
  account, and cost per call against that period's average. One hover reads all three.
- A two-up comparison card carrying each tab's headline finding (August's
  1–9 vs 10–31 split; each later month against the one before it).
- A **call-quality funnel**: placed → 20s+ → 60s+, with each step's share of
  placed calls and its true cost.
- Per-campaign totals for the call campaigns and, separately, the website-lead
  campaigns.
- Calls and cost per call by age band, both accounts combined.
- The full day-by-day table for the selected month.

## Snapshot

Frozen **24 Nov 2026, 8:15 am IST**. Data window **1 Aug – 24 Nov 2026**.
August, September and October are closed months; November is complete to the
24th. The 85 days from 1 Sep to 24 Nov were re-pulled in full this refresh and
campaign sums equal each account's own daily spend and impressions, to the
paisa, on every one of them; August is unchanged from when it was built, and
reconciled the same way then.

> ### Both accounts have been dark for 19 days
>
> **Nothing has delivered on either account since 5 November.** The month to the
> 24th contains five delivery days (1–5 Nov) and nineteen empty ones. Pallavi
> Kiran has not spent since **9 October** — 46 days. This is the finding of the
> refresh; everything else on the November tab is five days of data and should
> be read as such.
>
> `o2-reports` carries the same signature on a different account (31 days dark
> with a campaign still reading ACTIVE). Check Billing → Payment settings and
> the prepaid balance before concluding the campaigns are at fault.

> ### A third result type appeared: WhatsApp
>
> `Halcyon | ABO | WhatsApp | 6 numbers | 700 each | Telangana regions` ran on
> 4–5 November: **₹4,160.90 for 56 conversations, ₹74.30 each**. It is neither a
> phone call nor a website lead. The November tab renames its non-call section
> *Non-call campaigns* (`webEyebrow`), its totals row *All non-call campaigns*
> (`webTotalLabel`) and its chart legend band *WhatsApp + website leads*
> (`s3Label`) — three optional per-month overrides added for exactly this. The
> 56 conversations and the 13 Enquiry LP leads **are not 69 of anything**; the
> blended footer figure exists only because the page computes it, and the intro
> says so.
>
> Three conversations were attributed to **6 November**, after the campaign had
> stopped. They are carried on that day rather than dropped.

> ### One campaign was renamed at Meta
>
> On 6 Oct `Halcyon | Call 8585072072 | TS only | All days` became
> **`Halcyon | Call 094906 31010 | TS only | All days`** (Power Editor, no
> pending review). It is the same campaign id throughout: its September rows
> carry the old name, its October rows the new one. Spend, calls and day sums all
> still reconcile, which is the tell that it is a rename and not a new campaign.

| | August (1–31) | September (1–30) | October (1–31) | November (1–24) |
|---|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,68,508.95 | ₹10,594.70 |
| Calls placed | 5,144 | 4,539 | 1,834 | 60 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.45** | **₹87.42** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 442 (24.1%) · ₹288.15 | 17 (28.3%) · ₹308.54 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 172 (9.4%) · ₹740.49 | 6 (10.0%) · ₹874.20 |
| Call spend | ₹3,08,602.82 | ₹3,13,497.97 | ₹1,27,364.09 | ₹5,245.18 |
| Non-call spend | ₹53,443.78 | ₹13,712.53 | ₹41,144.86 | ₹5,349.52 |
| Pallavi Halcyon | ₹2,18,901.90 / 3,063 / ₹54.02 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,15,623.01 / 1,740 / ₹66.45 | ₹5,245.18 / 60 / ₹87.42 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.91 | ₹0 / 0 / — |
| Delivery days | 31 | 30 | 23 of 31 | 5 of 24 |

(Account rows from September on are **call spend only**. August's Pallavi
Halcyon row is total spend with a call-only cost per call — that inconsistency
is in the August figures as published and is left alone.)

Previous cut (1–28 Sep, published 29 Sep): ₹3,04,514.33 · 4,256 calls · ₹69.65.
The two settled days moved September to **₹69.07**; Meta also settled 28 Sep up
by ₹21.14 after publication, with no call counts moving on any settled day.

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
   margin, on ~₹1,000/day. Worth restarting — still ₹0.00 since.

**September closed at ₹69.07**, 15% above August and still tracking August's
second half. The gap is one account: Pallavi Halcyon ₹58.81, Pallavi Kiran
₹76.94 on 70% of the call budget. The last three days (28–30 Sep) are the ones
that carry forward: Kiran went dark, the whole call budget moved onto the four
new per-number campaigns, and they ran at **₹62.04** across 347 calls.

**October held the price and lost the quality.** ₹69.45 a call against
September's ₹69.07 — but call volume fell 60% (151 a day to 59), a quarter of
the month (₹41,145) went to the two Enquiry LP website-lead campaigns at ₹182.06
a lead, and the share of calls lasting 20 seconds fell from 29.3% to **24.1%**.
A 20-second call went ₹236.07 → ₹288.15 and a minute-long one ₹572.08 → ₹740.49.
The clinic paid about the same for a ring and distinctly more for a conversation.

**October's one standout:** `Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600
each` ran 9–16 Oct and bought **525 calls at ₹37.11** — 29% of the month's calls
on 15% of its call budget, the cheapest line on either account since August's
Age 35+ campaign. It was switched off on the 21st. Same caveat as Age 35+: only
5.3% of its calls reached a minute, so its minute-long call (₹695.81) is dearer
than `Call 9490631010`'s (₹630.54). **Ask why it was stopped.**

**November is five days and then silence.** ₹87.42 a call across 60 calls — the
dearest on record here — then nothing from the 6th. On 60 calls that rate is as
much noise as signal, but none of the three lines was cheap (₹68.11, ₹81.63,
₹129.61). Half the month's money was the WhatsApp campaign.

**The minute-long call by month:** ₹507.57 → ₹572.08 → ₹740.49 → ₹874.20. The
direction has not changed since this report started.

**Eight dark days inside October** (17–20 and 25–28) and nineteen in November.
The charts show them as the zeroes they are; the cost-per-call line breaks across
them rather than drawing through.

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

From 28 Sep both Enquiry LP campaigns optimise a **custom conversion**
(`offsite_conversion.custom.1564834054962652`, "Contact-good lead") — a fifth
distinct event.

**WhatsApp conversations** (4–5 Nov only) are a third kind again:
`onsite_conversion.messaging_conversation_started_7d`. 56 of them at ₹74.30.
Not a call, not a site lead.

The page names the event on every row and keeps all of this spend **out of cost
per call**. Blending it in reads ₹70.38 for August and overstates what a call
costs — don't.

## Refreshing

`DAILY_AUG` / `DAILY_SEP` rows are
`[day, a1CallSpend, a1Calls, a1WebSpend, a1WebLeads, a2CallSpend, a2Calls, impressions, reachSum, linkClicks]`
where `a1` = Pallavi Halcyon, `a2` = Pallavi Kiran. `day` is the day of month.

Everything else a tab shows — headline totals, narrative copy, campaign tables,
age rows — lives in the `MONTHS` object keyed `aug` / `sep` / `oct` / `nov`.
**To add a month, add a `DAILY_*` array and a `MONTHS` entry, then add one
`<button class="tab">` with a matching `data-month`.** Nothing else is
month-specific. Move `aria-selected="true"` (and `aria-labelledby` on `#report`,
and `let M=MONTHS.x`) to the new month so it opens first.

Optional per-month keys, all with sane defaults: `whole:true` (a complete month,
so the chart says "month average" not "period average"), `webEyebrow`,
`webTitle`, `webTotalLabel` and `s3Label` for when the non-call spend is not
only website leads — November sets all four because of WhatsApp.

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
  appending. The 28 Sep refresh settled up by ₹21.14 after publication.
- **Do not filter day rows on spend.** Late-attributed results land on days the
  campaign spent nothing: 1 call on 17 Oct, 1 on 25 Oct and 3 WhatsApp
  conversations on 6 Nov all arrived this way, and dropping those rows loses two
  calls against the campaign totals. Keep any row with a nonzero metric of any
  kind. A day with calls but **no call spend** has no cost per call — the chart
  treats it as a gap, not as ₹0.
- **Check the activity log for renames** (`ads_account_get_activity_logs`,
  `event_category` update). `Call 8585072072` became `Call 094906 31010` on
  6 Oct. The campaign id is what ties the months together, not the name.
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
- Update the snapshot date in **three** places: the masthead paragraph, the
  `Baked figures` comment above `DAILY_AUG`, and this README.
- Re-read the methodology bullets in the footer when the window moves. The one
  naming which month is complete and which is partial is hand-written prose and
  will go stale silently.
