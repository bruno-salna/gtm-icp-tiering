# Agent Instructions: Build an ICP from Evidence and Tier a Company List

You are working out **which companies on a list fit best**, and sorting them into tiers. You build the ideal customer profile (ICP) from the user's real customers, measured against the whole market. Then you score every company and put the best ones into a tier 1 the team can actually work. You are answering "who should we sell to?", not "who is ready to buy right now?". Timing comes later, in the Signals guide.

Read this file first, then each step file in `steps/` in order. Work through them with your user.

## Principles
1. **Evidence over opinion.** Every rule in the ICP needs a reason you can show: how much more common an attribute is among the best customers than in the market. Where there's no evidence, say the rule is a belief.
2. **Compare with the market, not just with customers.** "80% of our customers are limited companies" means nothing if 95% of the market is. A rule matters only when customers differ from the market.
3. **Use recorded fields only.** Score on what the list already holds: industry code, headcount, revenue, age, legal form, region. Don't research websites and don't guess values.
4. **Unknown isn't zero.** A missing field lowers the confidence of a score, not the score itself. Never treat "we don't know its size" as "it's small".
5. **Check the ICP before you trust it.** Hold back some customers, build the ICP without them, and see whether it finds them.
6. **Tier 1 fits the team.** Tier 1 is as many companies as the team can work properly, not everyone above a score.
7. **Never delete a row.** Excluded companies stay in the full file with the reason.
8. **Show your counts.** Every step reports numbers: rows scored, customers matched, companies per tier, and why.
9. **Never ask for passwords or logins.** If a source needs an account, ask the user to export the data and hand you the file.

## What to ask your user at the start
- What do you sell, and who buys it?
- Which company list should be tiered? Ideally a market map, or the cleaned list from the List quality guide. (See step 1.)
- Who are your customers? Ideally their register IDs, not just names. Which are your **best** ones, and which are your **worst**? Any lost deals or customers who left?
- What makes a customer "best" for you: revenue, margin, how long they stay, how easy they are to serve?
- What do you already believe your ICP is? (Ask this **before** showing any evidence, so your findings don't steer the answer.)
- How many accounts can your team work properly in a month or a quarter?
- Are there companies you can't serve at all (too small, wrong legal form, a region you don't cover)?

## Steps
| # | File | Output |
|---|---|---|
| 1 | [steps/01-take-in-the-list-and-customers.md](steps/01-take-in-the-list-and-customers.md) | The list, the customer groups, the meaning of "best", the capacity and the evidence path, signed off by the user |
| 2 | [steps/02-profile-the-customers.md](steps/02-profile-the-customers.md) | Each customer matched to the list, with its recorded attributes; a hold-out set |
| 3 | [steps/03-find-what-separates-them.md](steps/03-find-what-separates-them.md) | A lift table: how each attribute differs between best customers and the market |
| 4 | [steps/04-build-the-matrix.md](steps/04-build-the-matrix.md) | A filled-in [icp-matrix-template.md](icp-matrix-template.md), signed off by the user |
| 5 | [steps/05-score-every-row.md](steps/05-score-every-row.md) | `icp_score`, `icp_reasons` and `icp_confidence` on every row |
| 6 | [steps/06-back-test.md](steps/06-back-test.md) | Proof that the ICP finds customers it wasn't built from |
| 7 | [steps/07-tier-and-output.md](steps/07-tier-and-output.md) | `list-tiered.csv`, `list-tiered-full.csv` and `icp-summary.md` |

**Checkpoints:** stop and confirm with the user after steps 1, 4 and 7. Step 1 fixes what "best" means. Step 4 is where the rules are set. Step 7 is where the user decides who the team works first.

## Working files
Keep each ICP in its own folder, named for the market (for example `food-producers-2026/`):
- `input/`: the company list and the customer list, exactly as received
- `scripts/`: any code you write, so the scoring can be rerun on a fresh list
- the step outputs: the customer profile, the lift table, the matrix, the final files

Customer lists are confidential, and company lists often come from paid sources. Keep `input/` out of version control.

## When you're done
Go through [checklist.md](checklist.md). Every item must pass, or the summary must say why it doesn't.

## Output format
All rows follow [schema.md](schema.md). Don't rename or remove its columns.
