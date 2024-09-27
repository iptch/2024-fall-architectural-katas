# ADR-017: Analytics & Reporting as its own service

## Date:
2024-09-26

## Status:
Accepted

## Context:
Analytics& Reporting is its own service. It collects data all over the system.
Analytics: backend-part of data collection
Reporting: Front-facing representation of data
Goal: Separation of concerns between operational and analytics processes. No operational process should depend on analytics
Conflicting goal: Analytics & Reporting in the same service, for cost and complexity reasons in the system.
We resolve this conflict by leveraging channels of communication independent from UI, i.e. Email, Google Forms, …
it in the future, requirements of reporting in our own UI arises, the Reporting part of this service needs to be split and enter the operational realm of our system.
To mitigate the risk of strong coupling inside Analytics & Reports service, we use Clean/hexagonal Architecture principles including encapsulation of Use-Cases, allowing for cheaper technological transitions and Domain split.
Concretely:
1, 2 from topic

## Decision:

## Consequences:
