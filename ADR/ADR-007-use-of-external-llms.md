# ADR-007: Use of external LLMs

## Date:
2024-09-26

## Status:
Accepted

## Context:
Our interview with the AI expert [](/Evidence/interview-ai-expert.md) led to new insight concerning
LLMs leading to assumptions A TODO

The following AI-use-cases need to be supported:
- A: Resume-Tips
- B: Automatic filling of employee data during registration
- C: Transformation of resume to story
- D: Extraction of features from stories and open role (TODO)

We discussed three propositions:
- A: Use external LLM services as offered for example by Azure, Google, OpenAI.
  - +: Little development cost
  - +: Easy adaptation to the latest trends and models.
  - +: Tendency to become cheaper
  - +: Very fast time to market
  - -: Expensive.
  - -: Many API limitations such as rate-limits, delays, quotas, short lifecycle of models 
  - -: Regulatory considerations due to data privacy need to be made
- B: Use self controlled open-source LLM in a container running on the cloud
  - +: Specialized hardware can be used as a service this way.
  - +: A lot of control over fine-tuning, rates, and the runtime.
  - +: Less regulatory considerations due to data privacy need to be made.
  - -: Current LLMs will be surpassed soon due to fast evolving market. (A20)
  - -: Requires more development, configuration, maintenance, know-how, therefore higher cost.
  - -: High infrastructure cost due to resource heavy computing
- C: Use self controlled open-source LLM on-prem
  - +: Data privacy
  - +: Full control over LLM
  - -: Specialized hardware needs to be procured and additional staff needed. Delay in project timeline.
  - -: High electricity cost
  - -: High procurement and additional staff cost

## Decision

- Proposition A: We use external LLMs
- We need additional fault-tolerance and interoperability: we us a event-driven design for every LLM client in the system:

## Consequences:

- AI development can start without delay, faster TTM.
- Need to somehow track rate to avoid surpassing rate-limit.
- Cost is more predictable.
- Need a good strategy for 



### Strengthened characteristics:

- Cost (especially due to tendency to become cheaper)
- Feasibility (less hardware, staff, talent required. Ability to use latest LLMs)
- Interoperability (due to the decided design)
- Fault-tolerance (due to the decided design)
- Availability (cloud providers are hard to beat)

### Weakened characteristics:

- Feasibility (Need to check privacy regulations)
- Responsiveness (User-facing AIs)
- Observability (Less metrics about external system)
- Deployability (Due to the risk of LLMs becoming EOL. High effort of testing and migrating to new LLMs)