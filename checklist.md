# Definition of Done

Every item passes, or the summary explains why it doesn't.

## Intake
- [ ] The company list and the customer list are saved in `input/`, unedited
- [ ] "Best customer" is defined in measurable terms and signed off by the user
- [ ] The user's ICP belief was written down before any evidence was shown
- [ ] Capacity (people × accounts × period) and hard limits are written down
- [ ] The evidence path (A, B or C) is confirmed after matching

## Evidence
*Paths A and B only, except the last item. On path C, step 3 shows the market's shape instead.*
- [ ] Every customer is either matched to a row (with the match method) or listed with a reason
- [ ] No customer was matched by name when several rows fitted
- [ ] On path A, the hold-out was set aside before step 3, and how it was picked is recorded
- [ ] No hold-out customer was used in the lift tables or the matrix, and no two matrix versions were compared on the hold-out
- [ ] Every lift is shown with the customer count and the market share beside it
- [ ] Bands were set before looking at where customers fall
- [ ] Attributes that move together were checked, and only one of each pair carries full weight
- [ ] Every part of the user's belief has a verdict

## Matrix
- [ ] At most 6 dimensions (fewer only when the evidence supports fewer, with the reason recorded), maximums adding up to 100, written in recorded fields only
- [ ] Where two dimensions move together, the second one's points come from its lift within the first one's bands (on path C: a small maximum, with the reason)
- [ ] Every dimension and disqualifier has a reason (evidence or "belief")
- [ ] Every disqualifier is a hard limit or has strong evidence against, and the user agreed to it
- [ ] Each disqualifier says how it treats a recorded zero and an empty value
- [ ] Unknown values earn no points and aren't scored as a low band
- [ ] The matrix has a version name and was signed off by the user

## Rows
- [ ] `list-tiered-full.csv` holds every input row, and no more
- [ ] `list-tiered.csv` holds exactly the rows in tiers 1, 2 and 3
- [ ] Both files follow [schema.md](schema.md), with no renamed or missing columns
- [ ] Every row has a `tier`; every scored row has `icp_score`, `icp_reasons`, `icp_confidence` and `icp_matrix_version`
- [ ] Every excluded row has `icp_disqualified_by` set, or a score below a minimum the user chose
- [ ] No `low` confidence row is in tier 1
- [ ] Current customers are marked and not counted in the new-business tier 1
- [ ] No field was filled with a guess, and no website was researched

## Back-test and tiers
- [ ] Path A: the hold-out result is reported with counts, and the misses are named
- [ ] Path B: the in-sample check is reported and labelled as in-sample
- [ ] Path C: the review point is set, and the summary says "(unvalidated)" in its first line
- [ ] Tier 1 matches the agreed capacity, or the summary says why not
- [ ] The tier-1-by-score share of the market was checked
- [ ] Worst customers, lost deals and churned customers were checked where they exist
- [ ] If a large tied group straddles the tier 1 line, the tie-break is agreed and recorded
- [ ] Size figures older than the agreed limit were treated as unknown, not as current

## Summary
- [ ] Tier 1 size, the capacity it matches, and a plain-words verdict are in the first lines
- [ ] Belief vs evidence, the back-test, decisions and caveats are recorded
- [ ] A review date or outcome count is set, measured on what can be known by then
- [ ] The user's decision on working tier 1 is recorded
