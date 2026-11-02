# Step 2: Profile the Customers

## Goal
Find each customer in the company list, take its recorded attributes from there, confirm the evidence path, and set aside a hold-out group for the back-test.

## Why it matters
The comparison in step 3 only works if customers and market are described by the same fields from the same source. A customer's size from a sales rep's memory and the market's size from filed accounts can't be compared. Matching every customer to the list gives both sides the same ruler.

## How
1. **Match each customer** to a row in the company list:
   - **By register ID** first: same `country` and `register_id`. Treat it as text, so leading zeros survive.
   - **By name and place** if there's no ID: the cleaned name plus one more field (city or region), and only when exactly one row fits. If several fit, ask the user. Never pick one.
   - Record how each customer matched. Mark the matching row's `icp_customer_status` with the customer's group.
2. **Look at the customers that didn't match.** They tell you something:
   - **Outside the market:** the customer exists in the full map but not in the market (`in_market = false`). If several customers sit outside, the market definition may be too narrow. Tell the user; it may be worth revisiting the market definition in the Market map guide. Don't widen the market here.
   - **Not found at all:** a typo, a foreign company, or a company that closed. List them and ask.
   - Unmatched customers aren't used in step 3. Recount and confirm the evidence path from step 1.
3. **Check the dates.** The list shows companies as they are now, not as they were when they bought. A customer that had 15 staff when it signed and has 60 today will make the ICP look bigger than it was. If the list has financial figures by year, or the user knows when each customer signed, note the difference. Where many customers have grown a lot since they signed, say so.
4. **Set aside a hold-out (path A only).** Pick about a quarter of the best customers at random and mark them `icp_holdout = true`. They're **not** used in step 3 or 4. Step 6 checks whether the ICP finds them anyway. Record how you picked them (the random seed, or the rule).
5. **Write the customer profile:** a table of every matched customer with its group, how it matched, and the fields step 3 will compare.

```
Customer profile
Matched: <n> of <n>  (by ID <n>, by name and place <n>)
Not matched: <n>  (outside the market <n>, not found <n>)
Best customers matched: <n>, of which held out: <n>
Evidence path confirmed: A / B / C
```

## Pitfalls
- **Matching on name alone.** Common names repeat across a country. A wrong match puts a stranger's attributes into the evidence.
- **Group companies.** A customer may have signed through one entity of a group while the list holds several. Match the entity that signed and note the rest. Don't count the group several times.
- **Holding out after looking.** If you pick the hold-out after seeing the patterns, the back-test proves nothing. Pick it before step 3.
- **Quietly dropping awkward customers.** Every customer the user named is either matched or listed with the reason it isn't.

## Done when
Every customer is either matched (with the match method) or listed with a reason, the evidence path is confirmed, and on path A a hold-out has been set aside and recorded.
