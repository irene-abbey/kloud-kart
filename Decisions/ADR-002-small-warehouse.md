# ADR-002: Build a small warehouse of tidy tables, not a data lake or lakehouse

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Irene, external consultant (Nana Adjei approves)

## Context

The wish list asks for a data warehouse, or maybe a lakehouse. The facts: about 40 GB of data, about 4,000 orders a day (about 1.5 million a year), growth of 15–20% a year, and one PHP/MySQL developer; nobody else has run a warehouse or written Python professionally. The board has budgeted two data hires, not three. All the data is orders, inventory and customer accounts, so it is already in tidy tables. The reporting copy (ADR-001) removes the load from the live box, but it only mirrors the shop's tables as they are now.

## Decision

I will build a small warehouse of tidy tables, with one agreed meaning for each number, refreshed overnight from the reporting copy. I will not build a lake or lakehouse.

## Alternatives considered

### Alternative A: A data lake or lakehouse

- **How it would work:** Raw data of every kind is stored cheaply in one large place, and structure is added later when needed.
- **Why it is attractive:** It is flexible. It can hold anything (website clicks, messages, files) if Kloud Kart later wants forecasting or Nigeria-specific data. It avoids deciding the shape of the tables too early. It is the safer choice if data volume explodes.
- **Why rejected:** Kloud Kart's data is tidy and small: 40 GB would fit on one laptop. Flexibility is worth most when data is messy and huge, and this data is neither. A lake needs skills nobody at Kloud Kart has, and two hires can't also run a lake. The real problem is that two spreadsheets disagree, and a lake doesn't fix that: it can store both versions. It would also make the deletion list harder, because raw copies of customer data spread through more places.

### Alternative B: Report straight from the reporting copy, with no warehouse

- **How it would work:** Nana's and Finance's reports run directly against the copy from ADR-001. No new tool and no new monthly bill.
- **Why it is attractive:** It is the cheapest option, the server is already approved, and it already solves the slowdown. For a quarter or two, it is enough to get Nana's Monday numbers off CSVs.
- **Why rejected:** The copy mirrors the shop's tables, not agreed numbers. Each team would still calculate revenue its own way, so Finance's figures and Nana's would keep disagreeing. The copy also holds only the shop's current state, so it can't keep the history the board dashboard, the Nigeria split and any later forecasting need. It remains the fallback if the budget is cut.

## Consequences

- **What this buys:** One place where Finance's figures and Nana's are settled, because both teams read the same table. It also replaces about GHS 31,000 a year of Nana's and Finance's time in the old manual process. It is the foundation for the board dashboard, the country split for Nigeria and any later forecasting.
- **What this costs:** About GHS 14,000–41,000 a year in running costs (USD 100–300 a month; my estimate, not yet checked against the provider's pricing). Build time for the data engineer and the analytics engineer. It is another copy of customer data, so it goes on the customer-data register, the deletion list is applied in every refresh, and its hosting location must be recorded for Act 843 and the Nigeria pilot.
- **What it costs the client if I am wrong:** If Kloud Kart later needs messy data (website clicks, say), the warehouse will need extending. That is about three weeks of a hire's time (about GHS 11,000), not a rebuild.
- **What would make me revisit this:** A real need to analyse data that isn't in tidy tables, or the data passing about 200 GB, far beyond the 15–20% growth the brief states.

## What this survives

- **Orders triple:** 40 GB becomes about 120 GB, which is still small.
- **Nigeria grows fast:** reports are split by country from day one.
- **The budget is cut:** fall back to Alternative B for a quarter.
- **A hire falls through:** the warehouse is simple enough for one person to run while the second is found.
- **The open complaint escalates:** the deletion list is applied in every refresh, so a deleted customer is out of the warehouse within a day.
