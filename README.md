# Halcyon Pain Management — Meta Ads calls report

Client-facing report for **Halcyon Pain Management**, covering **both** ad accounts:

| Account | ID | What it runs |
|---|---|---|
| Pallavi Halcyon | `1999324147481098` | Call ads + website-lead campaigns + (from Nov) WhatsApp |
| Pallavi Kiran | `694358492762548` | Call ads only |

Live: https://lenkasacademy-pixel.github.io/halcyon-reports/

A single self-contained `index.html` with a **month tab bar** (August /
September / October / November). Figures are baked into the `DAILY_AUG` /
`DAILY_SEP` / `DAILY_OCT` / `DAILY_NOV` arrays and the `MONTHS` object near the
bottom of the file - nothing calls the network.

**Scope: four tabs.** August 2026 (1-31), September 2026 (1-30) and October 2026
(1-31) are complete months; November 2026 runs **1-13**, stopping at the last
complete day. Meta keeps revising the most recent ~48h and the live part-day moves
between calls minutes apart, so it is never shown. The range under each tab name is
read off that month's own `DAILY_*` rows at load, so it cannot drift from them.

**Both accounts have been dark since 6 November** - see the November tab.

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

Frozen **14 Nov 2026, 8:30 am IST**. Three months were added or closed on this
refresh: September completed (1-28 -> 1-30), October added whole, November added
to the 13th.

| | August (1-31) | September (1-30) | October (1-31) | November (1-13) |
|---|---|---|---|---|
| Spent (both accounts) | Rs 3,62,046.60 | Rs 3,27,210.50 | Rs 1,68,508.95 | Rs 10,594.70 |
| Call spend | Rs 3,08,602.82 | Rs 3,13,497.97 | Rs 1,27,364.09 | Rs 5,245.18 |
| Calls placed | 5,144 | 4,539 | 1,834 | 60 |
| **Cost per call** | **Rs 59.99** | **Rs 69.07** | **Rs 69.45** | **Rs 87.42** |
| Lasted 20s+ | 1,448 (28.1%) - Rs 213.12 | 1,328 (29.3%) - Rs 236.07 | 442 (24.1%) - Rs 288.15 | 17 (28.3%) - Rs 308.54 |
| Lasted 60s+ | 608 (11.8%) - Rs 507.57 | 548 (12.1%) - Rs 572.08 | 172 (9.4%) - Rs 740.49 | 6 (10.0%) - Rs 874.20 |
| Pallavi Halcyon | Rs 2,18,901.90 | Rs 1,15,914.55 / 1,971 / Rs 58.81 | Rs 1,15,623.01 / 1,740 / Rs 66.45 | Rs 5,245.18 / 60 / Rs 87.42 |
| Pallavi Kiran | Rs 1,43,144.70 / 2,081 / Rs 68.79 | Rs 1,97,583.42 / 2,568 / Rs 76.94 | Rs 11,741.08 / 94 / Rs 124.90 | Rs 0.00 |
| Non-call spend | Rs 53,443.78 / 332 | Rs 13,712.53 / 63 | Rs 41,144.86 / 226 | Rs 5,349.52 (incl. WhatsApp) |

(September, October and November account rows are **call spend only**. August's
Pallavi Halcyon row is total spend with a call-only cost per call - that
inconsistency is in the August figures as published and was left alone.)

All figures are **ex-GST** (Meta bills 18% GST on top in India).

### September closed

The previous cut stopped at the 28th. The 29th and 30th settled as two of the
month's biggest days on Pallavi Halcyon (Rs 11,858.31 and Rs 10,816.72), all of it
on the four per-number call campaigns opened on the 28th, at about Rs 60 a call.
That pulled the month from Rs 69.65 to **Rs 69.07**. Pallavi Kiran stopped on
27 September and never came back, so its September figures are final and unchanged.

### October held flat, and the money moved

Cost per call barely moved (Rs 69.07 -> **Rs 69.45**) but call volume fell 60%,
because **Pallavi Kiran effectively shut down**: Rs 11,741.08 over five days
(5-9 Oct) at Rs 124.90 a call, against Rs 1,97,583.42 in September. The account
also went dark twice inside the month (17-20 and 25-28 October) and stopped after
the 24th except a three-day restart on the 29th-31st.

**The month's find: `Halcyon | ABO | Calls | 7788 + 7272 + 9490 | 600 each`** -
525 calls at **Rs 37.11**, the cheapest line on either account since August's
Age 35+ campaign (Rs 19.60), on about Rs 19,500 across 9-24 October. It was **not
restarted in November**. Note the trade-off the funnel exposes: only 28 of its 525
calls passed a minute, so a minute-long call from it costs Rs 696.

### November: five days of delivery, then nothing

Rs 10,594.70 in total. Only three call campaigns ran, all "Daily 500" per-number,
buying 60 calls at **Rs 87.42** - 26% dearer than October, on a sample far too
small to call a trend. **Nothing has been served on either account since
5 November**, eight consecutive dark days to the 13th. That is the first thing to
ask the client about.

### The minute-long call keeps getting dearer

Rs 507.57 (Aug) -> Rs 572.08 (Sep) -> Rs 740.49 (Oct) -> Rs 874.20 (Nov). The
20-second call follows: Rs 213.12 -> Rs 236.07 -> Rs 288.15 -> Rs 308.54. This is
the one figure on the page with a steady direction across every cut ever recorded
here.

## A campaign was renamed and re-created underneath its own history

**This is the halcyon version of the trap `elixir-reports` documents.** On
**6 Oct 2026 at 10:13-10:14 am** (Power Editor, actor Abhijeet Lenka), campaign
`120255796887700348` was renamed

    Halcyon | Call 8585072072 | TS only | All days
    -> Halcyon | Call 094906 31010 | TS only | All days

and **all six of its ads had their creatives replaced in the same minute**
(`Ad updated`, old_value -> new_value on the creative id, each followed by
Active -> Pending Process -> Pending Review -> Active). Two days later its ad set
was renamed `8585 | Hyderabad 30km` -> `9490 | Kukatpally-Chandanagar-Moosapet`
and its targeting narrowed from one 30 km radius to three 3-4 km radii.

A pure rename never triggers Pending Review. **If a campaign name changed, pull
`ads_account_get_activity_logs` before carrying its history forward.**

It is **split into two `campCalls` rows** in October, because the two halves are
not the same campaign:

| identity | days | spend | calls | per call | 20s | 60s |
|---|---|---|---|---|---|---|
| `Call 8585072072` | 1-5 Oct | Rs 8,362.02 | 204 | **Rs 40.99** | 54 | 17 |
| `Call 094906 31010` | 6-24 Oct | Rs 17,216.73 | 167 | **Rs 103.09** | 35 | 19 |

The swap made it **two and a half times dearer per call**. The split is exact: the
two rows add back to the campaign's own month totals on spend (Rs 25,578.75), calls
(371), 20s (89) and 60s (36). September keeps the name the campaign actually ran
under that month (`Call 8585072072`).

## Three result types now - do not merge them

A **WhatsApp** campaign appeared on Pallavi Halcyon in November
(`Halcyon | ABO | WhatsApp | 6 numbers | 700 each | Telangana regions`,
`120256437300820348`), reporting `results` with indicator
`actions:onsite_conversion.messaging_conversation_started_7d`. It bought **56
conversations at Rs 74.30**, the cheapest result of any kind on the account that
month - and it is neither a phone call nor a site lead.

How it is carried, since `DAILY_*` has no messaging column:

- its **spend goes into the `a1WebSpend` column** (field 3), which is why that
  column is labelled **"Non-call spend"** in the day table and why `webLabel` for
  November reads "WhatsApp and website leads". Without this the day would not
  reconcile against the account total.
- its **conversations do NOT go into `a1WebLeads`** (field 4). That column is the
  pixel/custom-conversion lead count only, and is labelled "Site leads". Adding 56
  messaging conversations to 13 custom conversions would be exactly the blend this
  page exists to avoid.
- the conversation count appears in `campWeb`, where the event is named on the row.

`webLabel` is a new per-month `MONTHS` key, written in the case it should appear
inline ("website leads", "WhatsApp and website leads"). It drives the chart legend
and the non-call table's total row.

**The non-call total row no longer prints a blended cost per result when its rows
optimise for different events.** It shows `mixed`, a dash for the count and "not
comparable" instead. One cost per result across `HContacted`, `HEnquiry`,
`fb_pixel_lead`, a custom conversion and WhatsApp conversations is a number that
prices nothing. This changed what August and September display (they had been
showing a blend); October has a single event and still shows Rs 182.06 per lead.

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
- **Check `effective_status` AND the names, every refresh.** Filtering campaigns on
  `amount_spent > 0` over a long window is fine, but a campaign that was renamed
  will come back under its new name and silently replace a row you thought you knew.
  Diff this month's campaign names against last month's; anything that vanished is
  either archived, deleted or renamed, and the activity log says which.
- **Pull account-level dailies for both accounts and reconcile on spend,
  impressions AND link clicks.** On this refresh all six account-months matched
  exactly on all three, and every one of the 74 days matched on per-account spend
  and combined impressions. That check is what proves no campaign was missed.
- Age rows must sum to each campaign's own month total on **both** spend and calls.
  Use `results` index 7 of the period row when checking this - an earlier version of
  the build script read index 8 (`event`, always null for call campaigns), which made
  the call-count half of the assertion pass vacuously.
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
