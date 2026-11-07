# ICP + Tiering

**An agent-ready guide to building your ideal customer profile from evidence, and sorting a company list into tiers your team can actually work, in any EU country.**

Most ideal customer profiles are written from opinion: "mid-sized, growth-minded companies". They can't be checked, and they can't be applied to a list of 3,000 companies the same way twice. And when they are built from customers, they usually describe the customers without asking how common the same traits are in the market as a whole.

This guide makes an agent build the ICP from your real customers, measured against the whole market. Each rule gets a reason you can show: "companies with 20–99 staff are 4× more common among our best customers than in the market". Then it scores every company on the list, checks the scoring against customers it wasn't built from, and puts the best fits into a tier 1 the size of your team's capacity.

## How to use it
This repo contains no code and no data. It's a set of instructions for an AI agent.

1. Fork or clone this repo.
2. Give it to your agent (Claude, ChatGPT, Cursor or any other) and point it to [AGENT.md](AGENT.md).
3. Hand the agent a company list and your customer list. The agent asks what "best customer" means for you and how many accounts your team can work, then goes through the seven steps with you.

You supply the list, your customers and your capacity. The agent works out the patterns and checks with you at the points that matter.

**The best list to tier is a market map.** The output of the [Market map](https://github.com/bruno-salna/gtm-market-map) guide holds every company in the market, from official records, so "more common than in the market" really means the market. A list cleaned by the [List quality](https://github.com/bruno-salna/gtm-list-quality) guide works too; the summary then says the comparison covers the list, not the whole market.

**No customers yet?** The guide still works. In a new market, it builds the ICP from your beliefs and the market's shape, tiers the list, and labels the result "unvalidated" until real results come in.

## In, middle, out
- **In:** a company list in the [shared schema](schema.md), your customers (best and worst, ideally with register IDs), what "best" means to you, and how many accounts your team can work.
- **Middle:** the agent matches your customers to the list, measures which recorded traits set your best customers apart from the market, builds a scoring matrix with you, scores every company, and tests the matrix on customers it held back.
- **Out:** every company with a score, the reasons behind it and a tier; tier 1 sized to your capacity; and a one-page summary of who fits and why.

## The seven steps
| # | Step | What happens |
|---|---|---|
| 1 | [Take in the list and the customers](steps/01-take-in-the-list-and-customers.md) | Agree what "best" means, the team's capacity and how much evidence there is |
| 2 | [Profile the customers](steps/02-profile-the-customers.md) | Find each customer in the list; hold some back for the test |
| 3 | [Find what separates them](steps/03-find-what-separates-them.md) | Measure which traits are more common among best customers than in the market |
| 4 | [Build the matrix](steps/04-build-the-matrix.md) | Turn the differences into points and a few hard disqualifiers |
| 5 | [Score every row](steps/05-score-every-row.md) | A score, its reasons and a confidence level for every company |
| 6 | [Back-test](steps/06-back-test.md) | Check the matrix finds customers it wasn't built from |
| 7 | [Tier and output](steps/07-tier-and-output.md) | Tier 1 sized to capacity, tiers 2 and 3, and the summary |

## Why build the ICP this way
- **Customers alone mislead.** "80% of our customers are limited companies" means nothing if 95% of the market is. Only the comparison with the market shows what really sets your customers apart.
- **Exact figures beat ranges.** Filed accounts give real headcount and revenue. A 27-person firm isn't tiered as a 50–249 company because a data provider put it in the wrong range.
- **A test, not a belief.** Holding back some customers and checking the matrix finds them is the difference between an ICP that works and one that just describes the past.
- **Tiers that fit the team.** Tier 1 is as many companies as your team can work properly this quarter, not everyone above an arbitrary score.

## Part of a series
This is the third of five guides that chain together through a [shared row schema](schema.md):

[Market map](https://github.com/bruno-salna/gtm-market-map) → [List quality](https://github.com/bruno-salna/gtm-list-quality) → **ICP + tiering** → [Signals](https://github.com/bruno-salna/gtm-signals) → Orchestrator

Each guide works on its own. Used together, each one picks up the previous one's output. This guide answers *who fits*. The [Signals](https://github.com/bruno-salna/gtm-signals) guide answers *who is ready now*, and never changes a company's fit tier.

## What's in the repo
```
AGENT.md                  start here (for the agent)
steps/                    one file per step
icp-matrix-template.md    filled in by the agent in step 4
schema.md                 output columns, shared across the series
checklist.md              definition of done
examples/                 made-up sample matrix, rows and summary
LICENSE                   MIT
```

## Influences
The guide is written from scratch. It draws mainly on my own work building ICPs and tiering markets for companies selling into European markets, and it also learned from public work:

- **Amos Bar-Joseph and Maja Voje, [swan-gtm/gtm-skills](https://github.com/swan-gtm/gtm-skills)** (MIT). `account-tier-scoring` puts accounts on a tier ladder with hard gates, and points out that bucketed headcount ranges put small firms in the wrong tier. The tiers and disqualifiers in steps 4 and 7 follow that shape.
- **[ColdIQ](https://coldiq.com/skills), `icp-matrix-builder`.** Builds the scoring matrix from your best and worst customers rather than from opinion, and reviews it regularly. Steps 3, 4 and 7 take the same view.

Where this guide goes its own way: it measures every customer trait against the whole market, holds customers back to test the matrix, and sizes tier 1 to the team's capacity.

## Licence
[MIT](LICENSE). Use it, fork it, adapt it, including commercially; keep the copyright notice.
