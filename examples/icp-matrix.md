# ICP Matrix: Examplia food producers

*Made-up example. See [README.md](README.md).*

## 0. About this matrix
- Version: food-producers-v1
- Evidence path: A
- Company list scored: Examplia market map, food manufacturing, pulled 2026-10-12, 1,412 in-market companies
- Customers used as evidence: 24 best, 2 other, 4 worst (6 best customers held out)
- "Best" means: in the top half of customers by yearly revenue, and a customer for 2 years or more

## 1. Disqualifiers
| Disqualifier | Rule in recorded fields | Kind | Reason |
|---|---|---|---|
| `fewer_than_5_staff` | `employees` below 5 | hard limit | No production planner on staff; the user can't serve them |
| `sole_trader` | `legal_form` = sole trader | hard limit | The user only contracts with companies |

## 2. Dimensions
| Dimension | Field | Max | Bands → points | Reason (lift, counts) |
|---|---|---|---|---|
| Size | `employees` | 40 | 1–9: 0 · 10–19: 15 · 20–49: 35 · 50–99: 40 · 100+: 30 | Lift 3.5 (20–49) and 6.7 (50–99), 18 of 24 best customers. 100+ has 2 customers: middle-high value |
| Activity | `industry_code` | 30 | bakery or dairy: 30 · other food: 15 | Lift 2.4 (bakery) and 2.9 (dairy), 15 of 24 |
| Age | `registered_date` | 15 | under 3: 0 · 3–7: 8 · 8+: 15 | Lift 1.8 within the 20–99 staff band, so not just size again |
| Revenue | `revenue` | 15 | below €2m: 0 · €2m–30m: 15 · above: 10 | Moves together with size. Lift 1.6 within the 20–99 staff band, so a small maximum |

## 3. Left out on purpose
| Attribute | Why it's not in the matrix |
|---|---|
| Region | Lift between 0.8 and 1.2 in every region: customers are spread like the market |
| Legal form | 23 of 24 best customers are limited companies, but so is 91% of the market (lift 1.05) |

## 4. Untested bands
- Meat processing: no customers, because the user has never sold there. Scored as "other food" (15 points); a candidate for a small experiment.

## 5. Where the matrix differs from the user's belief
| Belief | Matrix | Kept as user's call? |
|---|---|---|
| "Mainly the capital region" | Region left out: no evidence | No: user agreed |
| "Dairy is our best segment" | Dairy and bakery score the same | No: user agreed |

## 6. Sign-off
- Signed off by user: yes, 2026-10-20
- Review: end of the quarter, against meetings booked per tier
