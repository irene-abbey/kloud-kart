# ADR-004: Hire a data engineer first and an analytics engineer second

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Irene, external consultant (Nana Adjei approves)

## Context

The board has budgeted two data hires this financial year, not three. The brief asks which two roles to hire first, in what order, and what each does in their first 90 days. The problems are the shared box (finding 2), no agreed definitions (finding 3) and no owner of customer data (finding 1).

In plain terms: the data engineer makes the data safe and available. The analytics engineer turns raw shop data into numbers everyone trusts, and owns what each number means.

## Decision

I will hire a data engineer first, starting in month 1, and an analytics engineer second, starting early in Q2. Until the analytics engineer arrives, Nana and Finance agree the definitions page themselves, because it needs a decision, not a hire.

- **Data engineer, first 90 days:** set up the reporting copy and the overnight refresh, build the deletion list into every refresh, take the Monday report off Nana's desk, and write down how it all works.
- **Analytics engineer, first 90 days:** turn the signed-off definitions into the actual numbers, own the board dashboard, and run a weekly check that Operations' and Finance's totals match, explaining any gap.

## Alternatives considered

### Alternative A: Data engineer first, then a data analyst

- **How it would work:** The second hire reads the numbers and tells the board what they mean.
- **Why it is attractive:** Analysts are easier to find in Accra and likely cheaper. They speak to Nana and the board directly and can show insight quickly.
- **Why rejected:** Kloud Kart's problem isn't a lack of analysis. Two people calculate the same number differently, by hand, every week. An analyst would be a third person with a spreadsheet. The analytics engineer fixes it once, so it stays fixed.

### Alternative B: Analytics engineer first

- **How it would work:** Start with the person who builds the definitions and the numbers.
- **Why it is attractive:** The definitions problem is the biggest quiet drain, at about GHS 111,000–351,000 a year at my assumptions. Nana would see matching numbers sooner.
- **Why rejected:** There is nothing reliable to build on while reports still run on the live box and nothing controls the customer lists. The data engineer's work is the base, and it also covers the finding whose downside isn't capped. The definitions page itself doesn't need a hire, so it starts in Q1 anyway.

## Consequences

- **What this buys:** The right job in the right order. Two roles that cover moving the data and the reporting, with no third hire.
- **What this costs:** About GHS 360,000 a year in salaries (about GHS 180,000 each; my assumption, not verified). The analytics engineer arrives about a quarter later. The data engineer carries the first quarter alone.
- **What it costs the client if I am wrong:** If the analytics engineer was really needed first, matching numbers arrive a quarter late, which costs about a quarter of finding 3's yearly cost: about GHS 28,000–88,000. Two hires also don't remove the key-person risk of one developer, which I will say in the deck.
- **What would make me revisit this:** Nana says the definitions are already agreed and the real gap is interpreting the numbers (then an analyst is the better second hire). Or the data engineer role takes more than two months longer to fill than the analytics engineer role.

## What this survives

- **The budget is cut:** a hire is delayed by a quarter, and the data engineer still comes first.
- **A hire falls through:** the data engineer's written notes mean the plan doesn't live in one person's head.
- **Orders triple:** the same two roles can handle it without a third.
- **Nigeria grows fast:** the analytics engineer owns the country split.
- **The open complaint escalates:** the data engineer's first 90 days include the deletion list, so the month 3 deadline has an owner.
