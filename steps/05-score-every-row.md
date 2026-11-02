# Step 5: Score Every Row

## Goal
Apply the matrix to every in-market row: a score from 0 to 100, the reasons behind it, and a confidence level.

## Why it matters
A score without reasons can't be questioned or trusted. A score that treats missing data as a bad answer ranks companies by how much they disclose, not by how well they fit. This step makes each score explainable and honest about what it doesn't know.

## How
1. **Check how old the figures are.** Headcount and revenue come from filed accounts, and some companies stop filing. Agree with the user how old a figure may be (by default, two years before the newest `financials_year` in the list). Treat older figures as unknown, for the disqualifiers and the scoring alike, and note it in `icp_notes`. Never let an old figure disqualify a company.
2. **Apply the disqualifiers.** A row that hits one gets `icp_disqualified_by` set to the disqualifier's name, and no score. Rows outside the market (`in_market = false`) get `icp_disqualified_by = out_of_market`.
3. **Score the rest, dimension by dimension.** Look up each row's band and its points. If the value is unknown, the row earns nothing for that dimension, and the dimension's maximum is left out of the total available.
4. **Work out the score** as a share of what could be known:

   `icp_score` = points earned ÷ maximum points of the dimensions that were known × 100, rounded to a whole number.

   A row with every dimension known is scored out of 100. A row with no revenue figure is scored out of the other 85 points, and then scaled to 100.
5. **Set the confidence** from the share of matrix points that were known for the row:

| `icp_confidence` | Share of points known |
|---|---|
| `high` | 80% or more |
| `medium` | 50% to 79% |
| `low` | under 50% |

   Step 7 keeps `low` confidence rows out of tier 1: a score built on less than half the matrix isn't solid enough to spend the team's best time on.
6. **Write the reasons** in `icp_reasons`, one entry per dimension, in matrix order, separated by `;`:
   `size 50-99 +40; activity dairy +30; age 8+ +15; revenue unknown`
7. **Report the spread:** how many rows were scored, disqualified (by which disqualifier) and at each confidence level, and the score distribution (for example, rows per 10-point band). Look at the customers' scores too, but don't judge them yet; that's step 6.

## Pitfalls
- **Scaling hides how little is known.** A row with only size known can score 100. That's why confidence travels with every score, and why low-confidence rows can't reach tier 1.
- **Changing the matrix while scoring.** If a result looks wrong, note it and finish. Changes go back through step 4 and the user, not into the scoring code.
- **Points for being a customer.** Existing customers are scored by the same matrix as everyone else. Their status is a separate column, not extra points.

## Done when
Every in-market row has either a score, reasons and confidence, or a disqualifier, and the spread is reported.
