# ADR-011: Deterministic matching

## Date:
2024-09-26

## Status:
Accepted

## Context:

The matching algorithm has a big influence on cost and architectural design.
Making a decision about the nature of scoring and matching helps to access
cost and performance.

Assumption: A match is always

We define:
- Resume: PDF as uploaded by user
- Story: Anonymized format of the resume as text, void of information that could lead to unfair discrimination.
- Features: Quantified distribution of personal skills, traits, experience across principal components. Not human comprehensible.
- Spyder: Quantified distribution of personal skills, traits, experience across predefined axes. Human comprehensible.
- Score: The result of comparing an open job with a representation of a resume.

We considered the following options:

TODO

A critical related requirement is Q14, which, due to the non-deterministic nature of AI training, we can
only solve through exhaustive testing. This decision also improved testing.

Also: the potential asymptotic complexity of update operations (needed for Q15) on a resume or open role is also significantly 
better for option TODO.

Also: The asymptotic complexity is only relevant, if a large amount of open roles should be considered for a resume. 
However, if the number of open roles to be considered are reduced beforehand, f.ex. by input of the candidate, 
utilization and cost may drop significantly.

## Decision:
- Option X has the best properties, with only linear 

## Consequences:
- Matching is more deterministic



### Strengthened characteristics:
- Testability (intermediate representation (spyder) allows for smaller, more precise tests)
- Feasibility (more comprehensible, verifiable process)
- Cost (significantly fewer AI-prompts)
- Deployability (due to testability)
- Data integrity (easier to verify, less AI)

### Weakened characteristics:
