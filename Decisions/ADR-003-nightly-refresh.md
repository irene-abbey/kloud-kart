# ADR-003: Refresh reports once a night, with no streaming, and keep stock live inside the shop

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Irene, external consultant (Nana Adjei approves)

## Context

Investors asked about real-time analytics, and a board member saw real-time dashboards at another portfolio company. The brief says stock counts can't go stale, because that is how the company oversells, and that everything else can refresh daily. Nobody has named a decision that needs faster data.

## Decision

Everything reported to Nana and the board refreshes once a night. Only stock needs to be current. Stock is read from the live database in the shop, never from the reporting copy, and the developer adds low-stock warnings in the shop by the end of month 8.

## Alternatives considered

### Alternative A: Real-time (streaming) dashboards

- **How it would work:** Every order and stock change is sent to the dashboards within seconds.
- **Why it is attractive:** It is what the investors asked for, and it would look impressive in front of the board. It would give Nana live figures when she is asked a question mid-meeting, and it would make the stock fix part of the same system.
- **Why rejected:** The brief itself says everything except stock can refresh daily. At 4,000 orders a day, a decision made at 10:03 is no different from one made the next morning, and nobody has named one that would be. At my assumptions, streaming adds about GHS 72,000–216,000 a year in running costs, plus about three months of a hire's time (about GHS 45,000), and it needs skills nobody at Kloud Kart has. It would use up the second hire's first year on a dashboard instead of on matching numbers.

## Consequences

- **What this buys:** A cheap, simple system that two people can run, with all numbers taken from the same moment. An honest no to the board on streaming, with a clear way to reopen it.
- **What this costs:** Reports are up to a day old. The stock fix needs work in the shop itself by the one developer, which adds to their load.
- **What it costs the client if I am wrong:** If a decision really does lose money when delayed by a day, it keeps losing money until I reopen this. At my assumptions, oversells cost about GHS 110,000–330,000 a year, which is why the stock fix is planned separately from reporting.
- **What would make me revisit this:** Oversells continuing after the stock fix, or a named decision that loses money when delayed by a day. The month 10 review answers both with evidence.

## What this survives

- **Orders triple:** a nightly refresh still finishes comfortably by morning.
- **Nigeria grows fast:** a second country adds rows, not a new design.
- **The budget is cut:** the nightly refresh is the cheapest part of the plan.
- **The open complaint escalates:** the deletion list is applied in every nightly refresh, so a deleted customer is out of the reports within a day.
- **Investors push harder for real-time:** the answer stays the same until someone names a decision that changes within a day, and the month 10 review is where that is tested.
