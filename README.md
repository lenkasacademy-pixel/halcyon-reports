# Halcyon Pain Management — Meta Ads calls report

Client-facing report for **Halcyon Pain Management**, covering **both** ad accounts:

| Account | ID | What it runs | Last spent |
|---|---|---|---|
| Pallavi Halcyon | `1999324147481098` | Call ads, website-lead and (from Nov) WhatsApp campaigns | 5 Nov 2026 |
| Pallavi Kiran | `694358492762548` | Call ads only | 9 Oct 2026 |

Live: https://lenkasacademy-pixel.github.io/halcyon-reports/

A single self-contained `index.html` with a **month tab bar** (August /
September / October / November). Figures are baked into the `DAILY_AUG` /
`DAILY_SEP` / `DAILY_OCT` / `DAILY_NOV` arrays and the `MONTHS` object near the
bottom of the file — nothing calls the network.

**Scope: four tabs.** August 2026 (1–31), September 2026 (1–30), October 2026
(1–31) and November 2026 (1–5). **Every month is now complete and final** — both
accounts stopped delivering after 5 November, so there is no live part-day
anywhere in this cut. The range under each tab name is read off that month's own
`DAILY_*` rows at load, so it cannot drift from them.

## Snapshot

Frozen **27 Nov 2026, 8:10 am IST**.

> **Both ad accounts are dark.** Pallavi Halcyon last spent on **5 November**;
> Pallavi Kiran last spent on **9 October**. Every campaign on both accounts now
> reads PAUSED or ARCHIVED — a listing filtered to ACTIVE returns nothing at all —
> so this is a deliberate stop rather than a delivery fault. Worth confirming
> somebody meant it, because the client is paying for nothing right now.
>
> **September is complete and moved.** The cut published on 29 September covered
> 1–28 and read ₹3,04,514.33 · 4,256 calls · ₹69.65. The two days that have
> settled since took the month to **₹3,27,210.50 · 4,539 calls · ₹69.07**.
> Meta also revised **28 September** after publication: spend +₹21.14
> (call +₹18.45, web +₹2.69), impressions +293, clicks +4, and **calls on that
> day fell 68 → 64** on the four per-number campaigns while four late-attributed
> calls landed on campaigns that spent nothing. The day total stayed 68.
>
> **A third result type appeared in November.** `Halcyon | ABO | WhatsApp |
> 6 numbers | 700 each | Telangana regions` took ₹4,160.90 for **56 messaging
> conversations** at ₹74.30 each. A WhatsApp conversation is neither a phone call
> nor a website lead, so it sits on its own row in the non-call table with its
> event named, is kept out of every cost-per-call figure, and **does not feed the
> leads KPI**. Its spend *is* carried in the `a1WebSpend` column so the daily bars
> still add up to the account total — the same treatment `o2-reports` gives its
> WhatsApp campaign.

| | August (1–31) | September (1–30) | October (1–31) | November (1–5) |
|---|---|---|---|---|
| Spent | ₹3,62,046.60 | ₹3,27,210.50 | ₹1,68,508.95 | ₹10,594.70 |
| Call spend | ₹3,08,602.82 | ₹3,13,497.97 | ₹1,27,364.09 | ₹5,245.18 |
| Calls placed | 5,144 | 4,539 | 1,834 | 60 |
| Cost per call | **₹59.99** | **₹69.07** | **₹69.45** | **₹87.42** |
| Lasted 20s+ | 1,448 (28.1%) · ₹213.12 | 1,328 (29.3%) · ₹236.07 | 442 (24.1%) · ₹288.15 | 17 (28.3%) · ₹308.54 |
| Lasted 60s+ | 608 (11.8%) · ₹507.57 | 548 (12.1%) · ₹572.08 | 172 (9.4%) · ₹740.49 | 6 (10.0%) · ₹874.20 |
| Non-call spend | ₹53,443.78 / 332 | ₹13,712.53 / 67 | ₹41,144.86 / 226 | ₹5,349.52 / 13 + 56 conv |
| Pallavi Halcyon | ₹2,18,901.90 | ₹1,15,914.55 / 1,971 / ₹58.81 | ₹1,15,623.01 / 1,740 / ₹66.45 | ₹5,245.18 / 60 / ₹87.42 |
| Pallavi Kiran | ₹1,43,144.70 / 2,081 / ₹68.79 | ₹1,97,583.42 / 2,568 / ₹76.94 | ₹11,741.08 / 94 / ₹124.90 | ₹0.00 |

(Account rows from September onward are **call spend only**; the non-call spend
sits outside them. August's Pallavi Halcyon row is total spend, its cost per call
call-only — that inconsistency is in the August figures as published.)

All figures are **ex-GST** (Meta bills 18% GST on top in India).

## The findings

**Cost per call has risen every month since August:** ₹59.99 → ₹69.07 → ₹69.45
→ ₹87.42. The step from August to September was 15%; September to October was
flat; October to November was another 26% on a tiny base.

**The minute-long call keeps getting dearer:** ₹507.57 (Aug) → ₹572.08 (Sep) →
₹740.49 (Oct) → ₹874.20 (Nov). October is where it broke: the 60-second rate
fell from 12.1% of calls to 9.4% while cost per placed call held steady, so the
account was buying the same number of rings and fewer conversations.

**October's best line is the best call price since August.** `Halcyon | ABO |
Calls | 7788 + 7272 + 9490 | 600 each` did **525 calls at ₹37.11** and
₹172.41 per 20-second call — the cheapest on either account since the Age 35+
campaign that stopped on 8 August (₹19.60). It ran 9–24 October. Nothing that
followed it is close: the three per-number `Daily 500` campaigns that started on
29 October are the dearest call lines in the report (₹66.08–₹97.37 in October,
₹68.11–₹129.61 in November).

**`ad set level 3 camp` remains the September standout** at ₹45.76 across 1,102
calls. `Halcyon | Calls — Age 35+ | FB only | CBO` — August's ₹19.60 line — has
still spent **₹0.00 since 8 August**. It is three and a half months now.

**A quarter of October's budget bought no calls.** ₹41,144.86 went to the two
`Enquiry LP` website-lead campaigns for 226 custom-conversion leads (₹182.06
each). That is a real result, priced in its own currency, and it is the reason
the call line falls away in the middle chart panel.

**Pallavi Kiran effectively ended in October.** ₹11,741.08 over five days
(5–9 Oct) for 94 calls at ₹124.90 — the worst month-level call price on either
account — and nothing since.

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

## Three result types now, not two

**Never merge them.** As of November this account reports three different kinds
of result and they are priced in three different currencies:

| Kind | Indicator | Where it shows |
|---|---|---|
| Phone calls | `actions:click_to_call_native_call_placed` | calls KPI, cost per call, funnel, age table |
| Website leads | `actions:offsite_conversion.custom.1564834054962652` (and, earlier, `HContacted` / `HEnquiry` / `fb_pixel_lead`) | non-call table, leads KPI |
| WhatsApp conversations | `actions:onsite_conversion.messaging_conversation_started_7d` | non-call table only — **never the leads KPI** |

The row format has no column for messaging results, exactly as in `o2-reports`.
The rule applied here: **count the spend, never the result.** WhatsApp spend goes
into `a1WebSpend` so the daily bars still sum to the account total, its
conversation count goes only on its own `campWeb` row with the event named, and
`webLeads` counts website leads alone.

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

- **Re-pull the published tail every refresh, not just the new days.** On this
  refresh Meta had revised **28 September** — the newest day in the previous cut —
  by +₹21.14 and −4 calls, two months after the fact. September only balanced
  once that day was re-pulled. The check that found it was comparing the
  published `DAILY_SEP` day column against a fresh `level: "ad_account"` daily
  pull, day by day.
- **A month's `days` is the span its `range` claims, not the calendar month.**
  November is `days:5` because delivery stopped on the 5th; leaving it at 30 made
  the per-day figures read ₹353 instead of ₹2,119 and understated the month by
  six times.
- **Keep the file pure ASCII.** Campaign names coming back from Meta contain real
  en and em dashes (`Kiran | Calls — 3 Numbers`, `New Leads Campaign – Copy`,
  `Mon–Sat 9–5`). They must be converted to `&mdash;` / `&ndash;` before they go
  into the file, or the page stops being ASCII-safe. The build asserts a zero
  non-ASCII count before writing.
