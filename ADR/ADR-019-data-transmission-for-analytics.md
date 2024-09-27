# ADR-019: Data transmission for analytics

## Date:
2024-09-26

## Status:
Proposed

## Context:
Transmitting data Point 5 tp Analkyticw & Reports
Opt 1: Analytics reads directly from candidate DB
fault tolerance | separation of concern. operational vs. analytics

Opt 2: Candidate sends to Analytics
stronger privacy of candidate db
Opt 3: Asynchronous delivery
Related: Should we only have asynchronous communication to the analytics service, to have better separation of concerns?

## Decision:

## Consequences:
