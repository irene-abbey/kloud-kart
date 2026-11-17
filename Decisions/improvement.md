# Improvement beyond the brief: Oversell investigation log

## The problem it solves

The brief says stock counts can't go stale, because that is how Kloud Kart oversells. It does not say why the overselling happens. My diagnosis assumes two causes: the stock count running behind the real count (lag), and the system count not matching the shelf (mismatch), through returns, damage or stock not booked in. I could not verify this, and the stock fix in ADR-003 (low-stock warnings in the shop by the end of month 8) depends on it.

There is a third possible cause: two buyers taking the last unit at the same moment. If that is the real cause, low-stock warnings won't stop it, and the developer's time would go into the wrong fix.

Nobody at Kloud Kart currently records how an oversell happens, so there is no evidence to choose a fix with.

## What I built

A one-page log and a three-step checklist that the developer and warehouse staff fill in every time an order is sold that can't be fulfilled. After a few weeks, the log shows which cause is behind most oversells.

**The log (one row per oversell)**

| Date and time | Order number | Item | Count shown on the site | Count on the shelf | Buyers for the last unit (one or two) | Cause | Filled in by |
|---|---|---|---|---|---|---|---|
| | | | | | | | |

**The checklist (sorting each oversell into a cause)**

1. Did two orders for the same item arrive within a minute of each other, for the last unit in stock? If yes, the cause is **two buyers at once**.
2. If not, does the count on the shelf match the count the system holds now? If no, the cause is **mismatch** (returns, damage or stock not booked in).
3. If the counts match, the site showed an old number when the order was placed. The cause is **lag** (the count running behind).

**How it is used**

- Warehouse staff fill in a row as soon as an oversell is found. It takes about five minutes.
- Each Friday, the developer sorts the week's rows using the checklist.
- After four to six weeks, Nana reads one line: how many oversells came from each cause.

## What it is worth to Nana

At my assumptions, overselling costs Kloud Kart about GHS 110,000–330,000 a year in refunds, apologies and lost customers. The log tells Nana which fix actually stops it before any money or developer time is spent.

- If most oversells are **lag** or **mismatch**, the plan's low-stock warnings and regular shelf counts are the right fix, and she can approve them with evidence.
- If most are **two buyers at once**, the developer changes how the shop reserves the last unit, and the month 8 work is redirected before it is wasted.

It also turns the unverified assumption in my diagnosis into a fact within a few weeks, which strengthens the plan when the board asks why the shop oversells.

## What it cost

- **To build:** about one hour of my time. No new software and no money.
- **To run:** about five minutes of warehouse staff time per oversell, plus about 30 minutes of the developer's time each Friday to sort the week's rows.
- **Risk:** low. If staff forget to fill it in, the log is incomplete, and the decision on the fix is delayed by a few weeks, not made wrongly.
