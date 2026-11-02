# Step 6: Back-Test

## Goal
Check that the matrix actually finds companies like the user's best customers, using customers it wasn't built from.

## Why it matters
Any matrix scores the customers it was built from well; that's how it was built. The real question is whether it finds *new* companies like them. The hold-out answers that. Without a back-test, the ICP is a theory with a spreadsheet attached.

## How
### Path A: test on the hold-out
1. **Rank the market by score** (scored rows only) and find where the top 20% begins.
2. **Count how many held-out best customers sit in that top 20%.** If the matrix were no better than chance, about 20% of them would. Compare:

```
Held-out best customers in the top 20% of the market: 5 of 6 (83%)
Expected by chance: 20%
Ratio: 4.2×
```

3. **Read the result:**
   - **About 2× chance or better:** the matrix finds new companies like the best customers. Go on.
   - **Between chance and 2×:** it works weakly. Look at the misses: which dimension let them down? Bring that to the user, and offer to go back to step 4.
   - **Around chance or worse:** the matrix doesn't generalise. Go back to step 3: the patterns may be noise, or "possibly channel".

   With only 5–8 held-out customers, one customer moves the result a lot. Report the count, not just the percentage, and don't over-read it.
4. **Check the other groups,** where they exist:
   - **Worst customers** should score clearly lower than best ones. If they score the same, the matrix can't tell good from bad fit; it only finds "companies like the ones who bought".
   - **Lost deals** that score high are useful news: those companies fit, and something else (price, timing, competitor) lost them. That's for the Signals guide and for sales, not a reason to change the matrix.
   - **Churned customers** that score high may mean the matrix rewards something that predicts buying, not staying. Point it out.
5. **Look at the shape of the market.** If the top 20% holds almost every company with a score above 90, or scores bunch in a narrow range, the matrix may not separate enough for tiering. Note it for step 7.

### Path B
There are too few customers for a hold-out. Check the scores of all customers in the same way and say plainly that the matrix was tested on the customers it was built from, so the result is flattering.

### Path C
There are no customers to test on. Skip the test and say so. Instead, set **the review point**: the number of outcomes (meetings, deals, or whatever the user tracks) after which the matrix is checked against real results, and the date by which to check. Put both in the summary.

## Pitfalls
- **Tuning on the hold-out.** If you change the matrix to catch a missed hold-out customer and then re-test on the same customers, the hold-out is spent. Say so, and treat the new result as in-sample.
- **Celebrating a perfect result.** 6 of 6 is encouraging, not proof. With small numbers, report it as "found all 6 held-out customers", not "100% accurate".
- **Ignoring the misses.** The hold-out customers the matrix missed show what the ICP doesn't capture. Name them in the summary.

## Done when
The back-test result is reported with counts (path A), or the in-sample check is reported and labelled (path B), or the review point is set (path C), and the other customer groups are checked where they exist.
