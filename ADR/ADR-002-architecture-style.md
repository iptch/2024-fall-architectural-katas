# ADR-002: Architecture style

## Date:
2024-09-23

## Status:
Proposed

## Context:
The style of the architecture is the cornerstone of a succesfull software project. Depending on the style, additional decisions like databases, communication patterns, ... can be derived. 

## Decision:
According to the requirements and the [Architecture Characteristics](/ArchitectureCharacteristics/) we decided to use the Service Based Architecture. Where needed for better inteoperability and deployability we want to use Eventdriven Architecture.

## Consequences:
- Service-Based Architecture is comparatively easier to maintain
- Evenstreaming adds complexity, but enabled additional decoupling of capabilities
