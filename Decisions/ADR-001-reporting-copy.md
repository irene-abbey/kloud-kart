# ADR-001: Run all reporting from a separate copy of the database, not from the live one

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Irene, external consultant (Nana Adjei approves)

## Context

MySQL and the live website must stay up, and they share one box. Twice last month, a Monday export slowed the live site to a crawl. At my assumptions (about 340 orders an hour on Monday morning, a one-hour slowdown that halves orders, and 30–60% of those sales lost for good), each incident costs about GHS 15,000–31,000 in revenue, or about GHS 360,000–740,000 a year if it keeps happening twice a month. A second server or read replica is already pre-approved.

## Decision

I will put a copy of the shop's database on the pre-approved second server, kept up to date continuously from the live database (a read replica), and run every report, export and refresh from that copy. Nothing reporting-related touches the live box. Stock is not read from the copy; it stays in the shop (ADR-003).

## Alternatives considered

### Alternative A: Keep reporting on the live box, but run exports at night or on Sunday evening

- **How it would work:** The Monday export is scheduled for a quiet hour, so it is ready when Nana arrives. No new server and no new build.
- **Why it is attractive:** It is free and quick. A Sunday-night export would be ready by Monday morning. It needs no new skills, and the one developer could set it up in a day.
- **Why rejected:** It still loads the shop's box, so any overrun or failure lands on customers. The export grows with the business (15–20% a year), so it runs longer each quarter and will eventually spill into trading hours. It also gives the definitions page, the overnight refresh and the deletion list no safe place to run. Because the second server is already approved, the saving from this option is small.

## Consequences

- **What this buys:** Reports stop affecting sales. Nana's Monday numbers come from a place that can't hurt customers. This is the base the later steps (definitions, overnight refresh, deletion list) run on.
- **What this costs:** The approved server's running cost, which is already budgeted but not stated in the brief. Setup and monitoring time for the data engineer. The copy can lag the shop by a short time, which is fine for everything except stock, and stock is not read from it. The copy is also one more place customer data lives: it goes on the customer-data register, and every deletion on the live database must be confirmed on the copy as well.
- **What it costs the client if I am wrong:** If the copy falls behind or breaks without anyone noticing, Nana takes wrong Monday numbers to the board, which is the same kind of wrong-decision cost as finding 3 (part of GHS 80,000–320,000 a year). Mitigation: a weekly check that the copy's order count matches the shop's.
- **What would make me revisit this:** Approval of the second server being withdrawn (then Alternative A becomes the fallback, with exports limited to Sunday night). Or the copy falling more than one hour behind the shop more than twice in a month.

## What this survives

- **Orders double or triple:** the copy grows with the business, and the live box is unaffected.
- **Nigeria grows fast:** there is no quiet hour to schedule around, and none is needed.
- **The open complaint escalates:** the copy gives a safe place to search for where a customer appears, without touching the live shop.
- **The budget is cut:** this is the cheapest fix with the biggest effect, so it is the last thing to cut.
- **Investors push for real-time:** the copy is already close to live, so a later decision on faster reporting doesn't need a redesign.
