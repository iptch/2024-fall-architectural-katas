# ADR-016: Matches published as events
## Date:
2024-09-26

## Status:
Accepted

## Context:
Matches status changes are key events that influence many conponents of the system. Therefore we put them asynchronously into a topic allowing for loose coupling.
Also extensions for notification or other services is very easy to do.

## Decision:

## Consequences:
