# Step 1: Take in the List and the Customers

## Goal
Get the company list to be tiered and the customer evidence, agree what "best" means, find out how many accounts the team can work, and decide which evidence path this ICP will take.

## Why it matters
An ICP is only as good as the evidence behind it. If "best customer" isn't defined, the user will pick favourites, and the ICP will describe the customers they like rather than the ones that pay. If capacity isn't known, tier 1 becomes a long list nobody can work. Both have to be fixed before you look at a single number.

## The two inputs
**1. The company list to tier.** It should follow the [shared schema](../schema.md). In order of preference:
- **A market map** (`market-map.csv` from the [Market map](https://github.com/bruno-salna/gtm-market-map) guide): every company in the market, from official records. It's the best base for comparison, because it *is* the market.
- **A cleaned list** (`list-clean.csv` from the [List quality](https://github.com/bruno-salna/gtm-list-quality) guide). Fine to tier, but it's only part of the market, so comparisons in step 3 describe the list, not the market. Say so in the summary.
- **Any other list.** Suggest running it through List quality first. Duplicates and dead companies distort the comparison and waste tier 1 places. If the user declines, carry on and note it.

**2. The customers.** As many as the user has, split into groups:

| Group | Meaning | Needed? |
|---|---|---|
| `best_customer` | The customers the user would clone if they could | Yes, for paths A and B |
| `other_customer` | Customers who are neither best nor worst | Helpful |
| `worst_customer` | Customers the user wouldn't sign again | Helpful: they show what to avoid |
| `lost_deal` | Companies that seriously evaluated and didn't buy | Optional: used in the back-test |
| `churned` | Customers who left | Optional |

Ask for register IDs. Names alone match badly (see step 2).

## How
1. **Save both files** in `input/` exactly as received.
2. **Ask the questions** in [../AGENT.md](../AGENT.md). Write down the user's current ICP belief in their own words, before you show any data.
3. **Agree what "best" means.** Pick one or two measurable things: revenue per customer, margin, how long they stay, how quickly they bought. If the user can only say "the ones we like", ask what those customers have in common commercially. Write the definition down; step 3 depends on it.
4. **Check the list.** Confirm it follows the schema, count its rows, and note whether it's a market map, a cleaned list or something else. If it has `in_market`, tier only the in-market rows and keep the rest as excluded.
5. **Agree capacity.** How many accounts can the team work properly in a period, and over what period does the tiering apply? Example: "2 people, about 40 accounts a month each, for a quarter" = about 240 accounts. This sets the size of tier 1 in step 7.
6. **Agree the hard limits.** Companies the user can't serve at all (below a size, a legal form, a region). These become disqualifiers in step 4. Only take hard limits here, not preferences.
7. **Pick the evidence path**, from the number of customers the user can name:

| Path | Evidence | What the ICP is |
|---|---|---|
| **A: Evidence** | About 20 or more customers, with at least 10 marked best | Rules measured against the market; a back-test with held-out customers |
| **B: Thin evidence** | 5–19 customers | The user's beliefs, checked against the customers there are. The summary says the evidence is thin. |
| **C: No evidence** | Fewer than 5 customers, or a new market | A hypothesis ICP from the user's beliefs and the market's structure, labelled **"(unvalidated)"** until results come in |

   The thresholds are a rule of thumb. Count the customers *after* step 2's matching, not before: customers that don't match the list don't count.
   Path C is a proper result, not a failure. A new market has no customers yet; the tiering still tells the team where to start, and step 7 sets when to revisit it.
8. Write it all down and get the user's sign-off.

## Worksheet
```
ICP name:
What the user sells:
Company list: file, source (market map / cleaned list / other), rows, date
Customer list: file, rows per group
"Best" means:
User's ICP belief, in their words (written before any data was shown):
Capacity: people × accounts per period × period = tier 1 size
Hard limits (can't serve):
Evidence path: A / B / C (provisional until step 2)
Signed off by user: yes / no, date
```

## Pitfalls
- **"Best" defined as "biggest".** The biggest customers are often the hardest to win and serve. If the user picks by size alone, ask whether those customers are also the most profitable.
- **Recent customers only.** Customers signed in the last few months haven't proved they're good yet. Ask how long a customer needs before you can tell.
- **One customer group from one channel.** If every customer came through one partner or one event, the evidence describes that channel, not the market. Note it now; it matters in step 3.
- **Treating preferences as hard limits.** "We prefer bigger firms" belongs in the scoring, not in the disqualifiers. Disqualifiers remove companies for good.

## Done when
Both files are saved, "best" is defined, the user's belief is written down, capacity and hard limits are agreed, a provisional path is chosen, and the user has signed off.
