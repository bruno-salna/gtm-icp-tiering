# Step 3: Find What Separates Them

## Goal
For each recorded attribute, measure how much more (or less) common it is among the best customers than in the market. Compare the result with what the user believes.

## Why it matters
This is the step most ICP work skips. Describing your customers ("most of them have 20–99 staff") tells you nothing until you know how common 20–99 staff is in the market. If it's equally common, it isn't a pattern; it's just the market. The comparison is what turns a description into a rule.

## How
### 1. Choose the attributes and their bands
Use the fields the list holds for most rows. Typical ones:

| Attribute | Field | How to band it |
|---|---|---|
| Activity | `industry_code` | By code, or a level up if codes are too fine for the number of customers |
| Size | `employees` | Bands set from the market, e.g. 1–9, 10–19, 20–49, 50–99, 100+ |
| Revenue | `revenue` | Bands set from the market |
| Age | `registered_date` | e.g. under 3 years, 3–7, 8–15, over 15 |
| Legal form | `legal_form` | As recorded |
| Place | `region` | As recorded |
| Segment | `segment` | From the market map, if there is one |

Set the bands **before** looking at where customers fall, so you don't draw lines around them. Use exact figures where the list has them (`employees`, not `employees_range`): a band edge only means something if the number is real. Add an "unknown" band for every attribute.

### 2. Measure the lift
For each band, compare:
- **Share of best customers** in the band (hold-outs excluded)
- **Share of the market** in the band. Use the market the user can actually serve as the base: the in-market rows that pass the hard limits from step 1. A band the user can't sell to anyway would only dilute the comparison. Report the whole market's shares next to it, so the effect of the limits is visible.
- **Lift** = share of best customers ÷ share of the market

```
Size (employees)   Best customers   Market     Lift
1–9                 1 of 24   4%    61%        0.07
10–19               3 of 24  13%    20%        0.6
20–49              10 of 24  42%    12%        3.5
50–99               8 of 24  33%     5%        6.7
100+                2 of 24   8%     2%        4.0
unknown             0 of 24   0%    …          –
```

Lift above 1 means the band is more common among best customers than in the market. Below 1 means less. Then do the same for worst customers, if there are enough of them: a band common among worst customers is a warning, even if best customers sit there too.

### 3. Judge which differences are real
Small numbers produce big, meaningless lifts. Use these rules of thumb:
- **Count before ratio.** Show the customer count next to every lift. A lift of 5 from 2 customers is an anecdote.
- **Trust a band** only with about 5 or more best customers in it, and a lift above about 1.5 (or below about 0.5 for a band to avoid).
- **Watch attributes that move together.** Older companies are often bigger. If both age and size show lift, check whether age still matters within one size band. If it doesn't, keep size and drop age, or the same thing gets counted twice. Write down the within-band lift: step 4 sets the second attribute's points from it.
- **Watch the channel.** If most customers came from one source (one partner, one region, one event), their shared attributes may describe how you found them, not who buys. Mark those attributes "possibly channel".

### 4. Compare with what the user believes
Take the belief written down in step 1 and mark each part:

| Belief | Evidence | Verdict |
|---|---|---|
| "Mid-sized firms" | 20–99 staff: lift 3.5–6.7 | **Confirmed** |
| "Mainly the capital region" | Capital: lift 1.1 | **Not supported**: customers are spread like the market |
| "Dairy is our best segment" | Dairy: 2 best customers | **No evidence either way** |

Where the evidence contradicts the belief, say so plainly and show the numbers. The user decides, but the summary records both.

### Path B and path C
- **Path B:** run the same tables, but treat every lift as a hint. Mark beliefs "consistent" or "inconsistent" with the customers there are, never "confirmed".
- **Path C:** there's nothing to measure lift on. Show the market's own shape instead (how many companies sit in each band), so the user can see what each belief would include or leave out. Every rule in step 4 will be a belief.

## Pitfalls
- **Describing customers without the market.** The single most common ICP mistake. Every share needs its market share beside it.
- **Too many bands.** With 24 customers, 15 industry codes give 1–2 customers each. Group codes until bands hold enough customers to judge.
- **Reading absence as rejection.** No customers in a band can mean "doesn't buy" or "never tried". If the user has never sold there, call it **untested**, not a poor fit.
- **Showing the user the numbers before asking their belief.** Once they've seen the data, you can't recover what they thought before.

## Done when
There's a lift table for every attribute with customer counts, the judged-real differences are marked, attributes that move together are resolved, and each part of the user's belief has a verdict.
