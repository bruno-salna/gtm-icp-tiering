# Step 4: Build the Matrix

## Goal
Turn the differences from step 3 into a scoring matrix: a few dimensions, points for each band, and a short list of hard disqualifiers. All of it written in recorded fields, and signed off by the user.

## Why it matters
A matrix makes the ICP something you can apply to every company the same way, explain row by row, and change later in one place. Writing it in recorded fields means a machine can apply it to the whole market, not just a person reading websites.

## How
1. **Pick up to 6 dimensions.** Take the attributes with the strongest real differences from step 3. Fewer is better: each extra dimension adds noise and makes scores harder to explain. If the evidence supports only 2 or 3, use 2 or 3, and say why in the matrix. Don't add a dimension just to fill the matrix. Leave out any attribute marked "possibly channel" unless the user decides otherwise.
2. **Don't count the same thing twice.** If two attributes move together (size and revenue often do, and so do size and age), the stronger one becomes a dimension in full. The second one gets points only for the lift it shows *within* the first one's bands, from step 3. If, among companies of the same size, older firms are no more likely to be best customers, age gets no points. A small within-band lift means a small maximum.
3. **Give each dimension a maximum number of points.** The maximums add up to 100. Give more points to the dimensions with the clearer difference (higher lift, more customers behind it). On path C, use the user's ranking of their beliefs instead.
4. **Give each band points,** from 0 up to the dimension's maximum. Follow the lift: the band with the highest trusted lift gets the full points; bands near a lift of 1 get a little or none. Bands with too few customers to judge get a middle value, not zero. The **unknown** band gets no points, and it's handled through confidence in step 5, not as a low score.
5. **Set the disqualifiers.** Two kinds only:
   - The hard limits the user agreed in step 1 (can't serve them).
   - Bands with strong evidence against: a lift well below 0.5 with enough customers to judge, or a band dominated by worst customers. Ask the user before making these disqualifiers; they remove companies for good.

   For each disqualifier, write down how it treats a recorded zero and an empty value, and ask the user. They're not the same: a company that files 0 employees may be run by its owner with contract staff, while an empty field means the figure isn't known. By default, an empty value never disqualifies (see step 5).

   Everything else is points, not exclusion. A company can score low and still sit in tier 3.
6. **Mark untested bands.** Bands the user has never sold to (step 3) get a middle value and the label "untested". These are where the team can run an experiment later.
7. **Fill in [../icp-matrix-template.md](../icp-matrix-template.md).** Every dimension and every disqualifier gets its reason: the lift and counts behind it, or "belief" if there's no evidence.
8. **Show it to the user and get sign-off.** Point out every place where the matrix and their original belief differ.

## Illustrative example
*An example only, to show the shape. It is not a recommended matrix.*

A user sells production-planning software to food producers. Step 3 showed strong lift at 20–99 staff, a modest lift for companies over 8 years old, and a clear lift in two sub-codes. Region showed nothing.

| Dimension | Max | Bands → points | Reason |
|---|---|---|---|
| Size (employees) | 40 | 1–9: 0 · 10–19: 15 · 20–49: 35 · 50–99: 40 · 100+: 30 | lift 3.5–6.7 at 20–99, 18 of 24 best customers |
| Activity (sub-code) | 30 | bakery or dairy: 30 · other food: 15 | lift 2.4 and 2.9, 15 of 24 |
| Age | 15 | under 3: 0 · 3–7: 8 · 8+: 15 | lift 1.8 within the 20–99 band |
| Revenue | 15 | below band: 0 · in band: 15 · above: 10 | moves with size; lift 1.6 within the 20–99 band, so a small maximum |
| **Disqualifiers** | | fewer than 5 staff (hard limit); sole traders (can't serve) | user's limits from step 1 |

Region is left out: lift close to 1 in every region.

## Pitfalls
- **A dimension for every attribute.** Ten dimensions with small weights give everyone a middling score, and the tiers can't separate.
- **Disqualifying on a preference.** "We don't love small firms" is points, not a disqualifier. Disqualified companies never come back unless someone changes the matrix.
- **Scoring unknown as zero.** It quietly punishes companies that don't file full accounts and pushes them down the list for a reason that has nothing to do with fit.
- **Points that ignore the evidence.** If size had the strongest lift, it can't get fewer points than region because the user likes regions. Changes against the evidence are allowed, but they're recorded as the user's call.

- **Choosing between matrices on the hold-out.** If the user is torn between two versions (with or without a regional bonus, say), don't score both and keep whichever finds more held-out customers. That uses the hold-out to build the matrix, and the back-test in step 6 then proves nothing. Settle it on the evidence from step 3, or as the user's recorded call. Only the signed-off version is back-tested.

## Checkpoint
The matrix is the ICP. Stop and get the user's sign-off before scoring anything.

## Done when
The matrix template is filled in, every dimension and disqualifier has a reason, maximums add up to 100, and the user has signed it off.
