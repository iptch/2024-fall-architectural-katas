# Container Diagram (C2)

The container diagram offers an overview of the containers of the system and how they interact with each other.

![Container Diagram](/C4/images/C2-Container.png)

According to the service-based architecture [ADR-002](/ADR/ADR-002-architecture-style.md) we share the database between different containers to improve the simplicity and testability [ADR-014](/ADR/ADR-014-multiple-services-on-same-database.md). For the matches we use an event-based topic [ADR-016](/ADR/ADR-016-matches-published-as-events.md).

**Important**: The AI models will operate as external services, as outlined in [ADR-007](/ADR/ADR-007-flexibility-toward-ai-models.md), to enhance the system's adaptability and testability. These models will serve various purposes, including:

- **Autofilling company information** for employers,
- **Generating resume tips** for job candidates,
- **Generating S.M.A.R.T stories**
- **Developing features** for the matching algorithm.

### Story Container
- **Anonymize Resume**: Removes all personally identifiable information (PII) from the candidate's resume.
- **Generate S.M.A.R.T Stories**: Creates S.M.A.R.T (Specific, Measurable, Achievable, Relevant, Time-bound) stories from the anonymized resume.

This service is implemented as a separate microservice, as described in [ADR-009](/ADR/ADR-009-creation-of-story-as-own-microservice.md).

### Matching Container
- **Feature Extraction**: Generates quantitative, human-readable features ("spyders") from job positions and S.M.A.R.T stories ([ADR-010](/ADR/ADR-010-create-features-from-story-not-resumes.md)).
- **Match Scoring**: Creates a match with a score between job positions and S.M.A.R.T stories using these features ([ADR-011](/ADR/ADR-011-matching-based-on-ai-or-deterministic-methods.md), [ADR-012](/ADR/ADR-012-matching-algorithm-and-spyder.md)).

### HR Integration
- **Asynchronous Decoupling**: Integrates with external HR systems by asynchronously consuming the matches topic to enable interoperability.
- **Resume Upload**: Uploads a resume to the employer's HR system when a match is unlocked.

Since the interoperability with multiple HR systems is a main challenge of this system a [C3 HR Integration Components](C4/C3-components-hr-integration.md) was created.

### Analytics
- **Data Gathering**: Read-only access to databases and topics for:
  - Match statuses (unlocked, passed, hired)
  - Survey results
  - Demographic data of job candidates
- **Data Analysis**: Detects potential biases in the hiring process.
- **Report Generation**: Creates reports for employers and job candidates.

For more details, see [ADR-017](ADR/ADR-017-analytics-and-reporting-as-own-service.md).

## Persons
The persons are identical to the one used in the Context Diagram, for reference check the documentation [here](/C4/C1-context.md).

## Software Systems
The external software systems are identical as well, the full description can be found [here](/C4/C1-context.md).



