# Step 7: Tier and Output

## Goal
Sort every scored company into a tier, with tier 1 sized to what the team can work. Deliver the tiered list, the full file and a one-page summary.

## Why it matters
Scores rank; tiers decide. A team can't work a ranking of 3,000 companies, but it can work 240 tier 1 accounts this quarter. Sizing tier 1 to capacity turns the ICP into a plan.

## The tiers
| `tier` | Meaning |
|---|---|
| `1` | Work these now: the best fit, as many as the team can work in the period |
| `2` | Next: good fit, worked when tier 1 is done or as capacity frees up |
| `3` | Later: some fit; worth a lighter touch or a later look |
| `excluded` | Not a fit: disqualified or out of the market (or below a minimum score, if the user chose one) |

Tiers are numbers, so they can't be confused with the List quality guide's A–D grade for a whole list.

## How
1. **Excluded means disqualified.** By default, only the disqualifiers from step 4 and rows outside the market make a company `excluded`. Every scored company sits in tier 1, 2 or 3, however low its score: step 4 promised that a low score is not an exclusion. If the user wants a minimum score as well, agree it now, show how many companies it removes and from which bands, and record it as their decision.
2. **Draw tier 1 from capacity.** Sort scored rows by score, highest first, skipping `low` confidence rows and current customers (see 5). Tier 1 is the top rows up to the capacity agreed in step 1.
   - **Move the line to a natural break.** If the capacity line falls in the middle of a group of equal scores, move it to the nearest break and say how many rows that adds or removes.
   - **If the tied group is large** (moving the line would change tier 1 by more than about a fifth), there's no natural break to move to. Agree a tie-break with the user, using a recorded field that's already in the matrix or was left out for a stated reason (for example, headcount within the band). Record it in the summary and in `icp_notes` for the tied rows. A large tie at the line also means the matrix can't separate those companies, so note it for the review.
   - **If the market is smaller than capacity:** put every high-scoring company in tier 1 and say the team has room for more; the problem then is the market size, not the tiering.
3. **Draw tiers 2 and 3.** By default, tier 2 is the next block of rows up to about twice tier 1's size, plus any `low` confidence rows that would otherwise have made tier 1. Tier 3 is everything else above the minimum score. Agree the lines with the user.
4. **Sense-check the shape.** If tier 1 by score (before the capacity cut) would hold a large share of the market (as a rule of thumb, more than a third), the matrix isn't selective enough: go back to step 4. If tier 1 holds companies that the user immediately says are wrong, find which dimension put them there. Look further down too: a strong bonus on one dimension can push a whole group the user wants (say, mid-sized firms outside a favoured region) into tier 3. Show the user any group like that before they sign off.
5. **Handle current customers.** Customers keep their score and tier, but stay out of the new-business tier 1 count. Mark them by `icp_customer_status`, so the team can use the tier for expansion work without mistaking them for prospects.
6. **Set the review date.** The matrix is a hypothesis about who fits. Agree when to check it against results: by default, after a quarter, or after the review point set in step 6 for path C. Review on what can be measured by then. After one quarter that's usually meetings and deals per tier, not whether customers stay. Check the matrix against "best" (step 1) once customers have had time to show it, and then rerun the guide on path A or B.

### Outputs
- **`list-tiered.csv`:** rows in tiers 1, 2 and 3, following [../schema.md](../schema.md), sorted by `tier`, then `icp_score` (highest first). This is the file the next guide picks up.
- **`list-tiered-full.csv`:** every input row, including excluded ones with the reason, sorted as the input was.
- **`icp-summary.md`:** in this structure:

```
# ICP summary: <ICP name>

Tier 1: <n> companies for <capacity and period>. <(unvalidated) on path C>
<one-sentence verdict: who the ICP is, in plain words>
List: <file, source, date>. Evidence: path <A/B/C>, <n> customers matched (<n> best).

## Who fits
<the matrix in plain words, then the matrix table with points and reasons>

## Tiers
<table: tier — companies — score range — confidence mix — current customers>

## Evidence
<the main lift tables, with counts>

## Belief vs evidence
<each part of the user's step 1 belief: confirmed / not supported / no evidence / consistent>

## Back-test
<path A: held-out customers in the top 20%, with counts; misses named. Path B: in-sample, labelled. Path C: review point.>

## Decisions made
- <"best" definition, capacity, disqualifiers, user changes against the evidence, tier lines>

## Caveats
- <list isn't the whole market; customers' attributes are as of today; possibly-channel attributes; untested bands>

## Review
<review date or outcome count, and what to check>
```

See [../examples/](../examples/) for a made-up filled-in version.

## Checkpoint
Show the user the summary and the top of tier 1. They decide whether the team starts working it, or the matrix goes back to step 4. Record the decision in the summary.

## Pitfalls
- **Tier 1 as a score threshold.** "Everyone above 70" might be 40 companies or 4,000. Start from capacity, then check the score at the line.
- **Low-confidence companies in tier 1.** Their high score rests on less than half the matrix. Tier 2 is the safe place, with a note to fill the gaps.
- **No review date.** An ICP nobody revisits quietly goes stale while the team keeps working it.

## Done when
Every row has a `tier`, all three files exist, the user has seen the summary and decided, and [../checklist.md](../checklist.md) passes.
